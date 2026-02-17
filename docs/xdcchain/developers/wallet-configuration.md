---
title: Wallet Configuration - XDC Network
---

# Wallet Configuration

XDC Network is fully EVM-compatible, so you can use any Ethereum wallet. This guide covers setup for popular wallets including MetaMask, Trust Wallet, and others.

## MetaMask

### Option 1: Native Support (Recommended)

MetaMask now supports XDC Network natively! You can add it directly:

1. Open MetaMask and click the network dropdown
2. Click **"Add Network"**
3. Search for **"XDC"** in the network list
4. Select **XDC Mainnet** and approve

### Option 2: Manual Configuration

If you prefer manual setup or need testnet access:

#### XDC Mainnet

| Parameter | Value |
|-----------|-------|
| Network Name | XDC Mainnet |
| RPC URL | `https://erpc.xinfin.network` |
| Chain ID | 50 |
| Symbol | XDC |
| Block Explorer | `https://xdcscan.com` |
|| `https://xdc.blocksscan.io` |

**Alternative RPC URLs:**
- `https://rpc.xdc.org`
- `https://earpc.xinfin.network`

#### Apothem Testnet

| Parameter | Value |
|-----------|-------|
| Network Name | XDC Apothem Testnet |
| RPC URL | `https://rpc.apothem.network` |
| Chain ID | 51 |
| Symbol | TXDC |
| Block Explorer | `https://testnet.xdcscan.com` | 
| | `https://apothem.blocksscan.io` |

## Trust Wallet

Trust Wallet supports XDC Network. To configure:

1. Open Trust Wallet settings
2. Navigate to **Network** settings
3. Add a custom network with the parameters above

## Other EVM Wallets

Any EVM-compatible wallet (Rabby, Coinbase Wallet, etc.) can connect to XDC using the RPC parameters listed above.

## Finding the Best RPC Endpoint

For optimal performance based on your location, you can:

1. Visit [Chainlist.org](https://chainlist.org/?search=xdc) | [XDC RPC](https://xdcrpc.com/) to test RPC latency
2. Choose the endpoint with the lowest latency for your region

## Troubleshooting

**Address Format:** XDC uses `xdc` prefix instead of `0x`. Most wallets handle this automatically, but if you encounter issues:
- Replace `xdc` with `0x` when pasting addresses into MetaMask
- Replace `0x` with `xdc` when sharing addresses externally

**Transaction Stuck?** XDC has very low gas fees (0.25 Gwei). If a transaction is pending, ensure you're using at least this gas price.
