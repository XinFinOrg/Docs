---
title: USDC on XDC QuickStart Guide
---

# USDC on XDC QuickStart Guide

## Overview

USDC is a digital dollar issued by Circle, also known as a stablecoin, and is available on many of the world’s leading blockchains. Designed to represent US dollars on the internet, USDC is backed 100% by highly liquid cash and cash-equivalent assets, making it redeemable 1:1 for USD.

On the XDC Network, USDC behaves like any standard ERC-20 token — enabling fast, secure, and programmable digital dollar transactions.

This guide walks you through building a standalone `index.js` script using **Viem** and **Node.js** to check your USDC balance and send a test transfer to another address on the **XDC Apothem Testnet**.

---

## Prerequisites

- Node.js v18+ with `"type": "module"` in `package.json`
- `viem` and `dotenv` packages installed
- An XDC Apothem testnet wallet funded with testnet USDC and XDC (for gas fees)
- A `.env` file with:
  - `PRIVATE_KEY`
  - `RECIPIENT_ADDRESS`

> To get testnet USDC, use Circle’s CCTP v2 Sample App to transfer USDC cross-chain to your XDC wallet.

---

## Project Setup

### 1. Initialize Project & Install Dependencies

```bash
npm init -y
npm install viem dotenv
````

### 2. Create Environment File

In your project root, create a `.env` file and add:

```env
PRIVATE_KEY=<YOUR_PRIVATE_KEY>         # Must be 0x-prefixed 64-character hex
RECIPIENT_ADDRESS=0x<RECIPIENT_ADDRESS>
```

### 3. Create Your Script File

In the same directory, create a file named `index.js`.

Ensure `"type": "module"` is set in your `package.json`.

---

## Script Breakdown

### 1. Import Modules & Define USDC Constants

```js
import 'dotenv/config';
import { createPublicClient, createWalletClient, http, formatUnits, parseUnits } from 'viem';
import { privateKeyToAccount } from 'viem/accounts';
import { xdcTestnet } from 'viem/chains';

const USDC_ADDRESS = '0xb5AB69F7bBada22B28e79C8FFAECe55eF1c771D4';
const USDC_DECIMALS = 6;
const USDC_ABI = [
  {
    name: 'balanceOf',
    type: 'function',
    stateMutability: 'view',
    inputs: [{ name: 'account', type: 'address' }],
    outputs: [{ name: '', type: 'uint256' }],
  },
  {
    name: 'transfer',
    type: 'function',
    stateMutability: 'nonpayable',
    inputs: [
      { name: 'to', type: 'address' },
      { name: 'amount', type: 'uint256' },
    ],
    outputs: [{ name: '', type: 'bool' }],
  },
];
```

---

### 2. Load & Validate Environment Variables

```js
const PRIVATE_KEY_RAW = process.env.PRIVATE_KEY;
const RECIPIENT = process.env.RECIPIENT_ADDRESS || process.env.RECIPIENT;

if (!PRIVATE_KEY_RAW) {
  console.error('Error: Set PRIVATE_KEY in your .env file');
  process.exit(1);
}
if (!RECIPIENT) {
  console.error('Error: Set RECIPIENT_ADDRESS or RECIPIENT in your .env file');
  process.exit(1);
}
if (!/^0x[a-fA-F0-9]{40}$/.test(RECIPIENT)) {
  console.error('Error: Recipient address is not a valid Ethereum address');
  process.exit(1);
}

const PRIVATE_KEY = PRIVATE_KEY_RAW.startsWith('0x') ? PRIVATE_KEY_RAW : '0x' + PRIVATE_KEY_RAW;
```

---

### 3. Initialize Viem Clients

```js
const account = privateKeyToAccount(PRIVATE_KEY);
const publicClient = createPublicClient({ chain: xdcTestnet, transport: http() });
const walletClient = createWalletClient({ account, chain: xdcTestnet, transport: http() });
```

---

### 4. Main Transfer Logic

```js
(async () => {
  try {
    const balance = await publicClient.readContract({
      address: USDC_ADDRESS,
      abi: USDC_ABI,
      functionName: 'balanceOf',
      args: [account.address],
    });

    const balanceFormatted = Number(formatUnits(balance, USDC_DECIMALS));
    const amount = 10;

    console.log('Sender:', account.address);
    console.log('Recipient:', RECIPIENT);
    console.log('USDC balance:', balanceFormatted);

    if (amount > balanceFormatted) {
      console.error('Error: Insufficient USDC balance');
      process.exit(1);
    }

    const amountInDecimals = parseUnits(amount.toString(), USDC_DECIMALS);

    const hash = await walletClient.writeContract({
      address: USDC_ADDRESS,
      abi: USDC_ABI,
      functionName: 'transfer',
      args: [RECIPIENT, amountInDecimals],
    });

    console.log('Transfer successful!');
    console.log('Tx hash:', hash);
    console.log('Explorer:', `https://testnet.xdcscan.com/tx/${hash}`);
  } catch (err) {
    console.error('Transfer failed:', err.message || err);
    process.exit(1);
  }

  process.exit(0);
})();
```

---

## Run the Script

Use the following command:

```bash
node index.js
```

If successful, you’ll see output like:

```
Sender: 0x1A2b...7890
Recipient: 0x9F8f...1234
USDC balance: 250.0
Transfer successful!
Tx hash: 0xabc123...def456
Explorer: https://testnet.xdcscan.com/tx/0xabc123...def456
```

---

## Important Notes

* **Testnet Only**: USDC on Apothem has no real value.
* **Security**: Never commit your `.env` file. Treat private keys as sensitive.
* **Gas Fees**: Get free XDC from the [XDC Faucet](https://faucet.apothem.network/).
* **Lightweight ABI**: Only the necessary functions (`balanceOf`, `transfer`) are used.
* **Viem Behavior**: Viem auto-handles RPC interaction, account signing, and encoding/decoding.

---

## Learn More

Explore the full Circle USDC integration guide in the [Circle Developer Docs](https://developers.circle.com/docs/usdc).

```

---
