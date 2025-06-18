---
title: Deployment & Verification 
---

## Deployment & Verification on the XDC Network

Deploying and verifying smart contracts on the XDC Network is streamlined and developer-friendly, thanks to its EVM compatibility. Developers can use familiar tools such as Remix, Hardhat, Truffle, and Foundry to write and deploy smart contracts. After deployment, contracts can be verified on XDCScan (the network’s block explorer), enhancing transparency and trust. Verification allows users and developers to review the contract’s source code, ensuring authenticity and alignment with the deployed bytecode. The XDC Network’s low gas fees and fast finality (2-second block time) make it an efficient and cost-effective environment for smart contract deployment and execution.

## Using Remix
Remix is an integrated development environment (IDE) that allows you to deploy smart contracts directly to a blockchain. It supports Solidity, the most popular language for smart contract development.

**Steps to Deploy a Token on XDC Network using Remix:**

**Step 1: Access Remix IDE** 

Visit Remix IDE in your web browser.

**Step 2: Create and Write the Token Smart Contract**

In the Remix IDE, create a new Solidity file (e.g., MyToken.sol).

Write your ERC20 token contract or use the following basic example for an ERC20 token:
solidity

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}
```

**Step 3: Select the Compiler Version**

In Remix, under the Solidity Compiler tab, select the correct version of Solidity (the version you used in the contract).

**Note:** XDC Network supports up to 0.8.23 compiler version only.

**Step4: Compile the Smart Contract**

Click the Compile button to compile the contract.

**Step 5: Configure the XDC Network on Remix**

Under the Deploy & Run Transactions tab, choose Injected Web3 as the environment. This will connect Remix to your MetaMask wallet (ensure MetaMask is set to the XDC Network).

**Add the XDC Network to MetaMask if not already added:**

- **Network Name:** XDC Network
- **RPC URL:** https://rpc.xinfin.network
- **Chain ID:** 50
- **Currency Symbol:** XDC
- **Explorer URL:** https://xdcscan.com/ or https://xdcscan.io/
- **Check out the Endpoint URLs:** https://docs.xdcscan.com/getting-started/endpoint-urls

**Step 6: Deploy the Token**

- Select your compiled contract (MyToken) in Remix and input the constructor parameters (e.g., initial supply) in the Deploy section.
- Click Deploy, and your token will be deployed to the XDC Network.

**Step 7: Verify the Token**

Verify the deployed token on [XDCScan.com](https://xdcscan.com/) or [XDCScan.io](https://xdcscan.io/)  Explorer. Using below methods:

- [How to Verify Your Smart Contract Built on the XDC Network via Standard Input JSON on XDCScan](https://www.xdc.dev/openscan/how-to-verify-your-smart-contract-built-on-the-xdc-network-via-standard-input-json-on-xdcscan-powered-by-blocksscanopenscan-2j93)
- [How to Verify Multi-Part Smart Contracts on XDCScan Explorer: A Complete Guide.](https://www.xdc.dev/openscan/how-to-verify-multi-part-smart-contracts-on-xdcscan-explorer-a-complete-guide-1pfe)

## Using Hardhat
Refer the guide on [Hardhat Smart Contract Verification](https://www.xdc.dev/openscan/streamline-hardhat-smart-contract-verification-a-guide-to-automated-verification-on-blocksscan-with-xdc-network-30kc)

**After deployment, verify the contract using:**

```
npx hardhat verify - -network network-name contract-address constructor-arguments
```

- **network-name:** The blockchain network where the contract was deployed.
- **contract-address:** The address of the deployed contract.
- **constructor-arguments:** (Optional) If your contract's constructor takes parameters, provide them as space-separated values.

**Example (Without Constructor Arguments):**

```
npx hardhat verify - -network xdc 0x1234567890abcdef1234567890abcdef12345678
```

**Example (With Constructor Arguments):**

```
npx hardhat verify - -network xdc 0x1234567890abcdef1234567890abcdef12345678 "arg1" "arg2"
```

Check out the Endpoint URLs: https://docs.xdcscan.com/getting-started/endpoint-urls

## Using Brownie
**Brownie** is a Python-based development framework for Ethereum-compatible blockchains, including the **XDC Network**. It allows developers to write, test, and deploy smart contracts efficiently using **Python**. Brownie supports both **Solidity** and **Vyper** contracts, making it a versatile tool for developing decentralized applications (dApps) on the XDC Network.

For a step-by-step guide on deploying Vyper contracts on the XDC Network using Brownie, refer to [this guide](https://www.xdc.dev/openscan/a-step-by-step-guide-to-deploying-vyper-contracts-on-the-xdc-network-with-brownie-2m0e).

