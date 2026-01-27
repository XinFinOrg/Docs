# Gas & Fees on XDC Network

Understanding how transaction fees work on XDC Network.

## Overview

XDC Network uses a **gas model** similar to Ethereum, but with significantly lower costs. Gas is a unit measuring the computational effort required to execute transactions.

## Key Concepts

### Gas vs Gas Price vs Transaction Fee

```
Transaction Fee = Gas Used × Gas Price
```

| Term | Description | Example |
|------|-------------|---------|
| **Gas** | Computational units required | 21,000 (simple transfer) |
| **Gas Price** | Cost per gas unit (in Gwei) | 0.25 Gwei |
| **Gas Limit** | Max gas you're willing to spend | 100,000 |
| **Transaction Fee** | Actual cost in XDC | 0.00000525 XDC |

## XDC Network Fee Advantages

| Metric | XDC Network | Ethereum | Savings |
|--------|-------------|----------|---------|
| Avg Gas Price | 0.25 Gwei | 20-100 Gwei | 80-400x cheaper |
| Simple Transfer | ~$0.00004 | $1-5 | 99%+ |
| Token Transfer | ~$0.0001 | $5-20 | 99%+ |
| Contract Deploy | ~$0.01-0.10 | $50-500 | 99%+ |

## Gas Costs by Operation

### Common Operations

| Operation | Gas Used | Cost (0.25 Gwei) |
|-----------|----------|------------------|
| XDC Transfer | 21,000 | ~$0.00004 |
| XRC20 Transfer | 65,000 | ~$0.00012 |
| XRC20 Approve | 45,000 | ~$0.00008 |
| NFT Transfer | 85,000 | ~$0.00015 |
| Contract Deploy | 500,000-3,000,000 | ~$0.001-0.05 |
| Swap (DEX) | 150,000-300,000 | ~$0.0003-0.0006 |

### EVM Opcode Costs

| Opcode | Gas | Description |
|--------|-----|-------------|
| ADD | 3 | Addition |
| MUL | 5 | Multiplication |
| SSTORE (new) | 20,000 | Store new value |
| SSTORE (update) | 5,000 | Update existing value |
| SLOAD | 800 | Load from storage |
| CALL | 700+ | External contract call |
| CREATE | 32,000 | Deploy contract |

## Setting Gas Price

### Recommended Gas Prices

| Speed | Gas Price | Confirmation |
|-------|-----------|--------------|
| 🐢 Low | 0.1 Gwei | ~30 seconds |
| 🚶 Standard | 0.25 Gwei | ~2-4 seconds |
| 🏃 Fast | 0.5 Gwei | ~2 seconds |

### In Code

=== "JavaScript (Web3.js)"
    ```javascript
    const Xdc3 = require('xdc3');
    const xdc3 = new Xdc3('https://rpc.xinfin.network');
    
    // Get current gas price
    const gasPrice = await xdc3.eth.getGasPrice();
    console.log('Current gas price:', xdc3.utils.fromWei(gasPrice, 'gwei'), 'Gwei');
    
    // Send transaction with custom gas price
    const tx = await xdc3.eth.sendTransaction({
        from: '0x...',
        to: '0x...',
        value: xdc3.utils.toWei('1', 'ether'),
        gasPrice: xdc3.utils.toWei('0.25', 'gwei'),
        gas: 21000
    });
    ```

=== "JavaScript (Ethers.js)"
    ```javascript
    const { ethers } = require('ethers');
    const provider = new ethers.JsonRpcProvider('https://rpc.xinfin.network');
    
    // Get fee data
    const feeData = await provider.getFeeData();
    console.log('Gas Price:', ethers.formatUnits(feeData.gasPrice, 'gwei'), 'Gwei');
    
    // Send transaction
    const tx = await wallet.sendTransaction({
        to: '0x...',
        value: ethers.parseEther('1'),
        gasPrice: ethers.parseUnits('0.25', 'gwei')
    });
    ```

## Estimating Gas

Always estimate gas before sending transactions:

```javascript
// Estimate gas for a transaction
const gasEstimate = await xdc3.eth.estimateGas({
    from: '0x...',
    to: contractAddress,
    data: contract.methods.transfer(recipient, amount).encodeABI()
});

// Add 20% buffer for safety
const gasLimit = Math.ceil(gasEstimate * 1.2);

console.log('Estimated gas:', gasEstimate);
console.log('Gas limit (with buffer):', gasLimit);
```

## Gas Optimization Tips

### For Users

1. **Set appropriate gas price**: 0.25 Gwei is usually sufficient
2. **Don't overpay**: XDC has consistent low fees
3. **Batch transactions**: Combine multiple operations when possible
4. **Off-peak times**: Fees are consistently low, but network is fastest during low activity

### For Developers

1. **Minimize storage writes**
   ```solidity
   // Bad: Multiple storage writes
   balances[user] = balances[user] + amount;
   totalSupply = totalSupply + amount;
   
   // Good: Batch operations
   function batchUpdate(address user, uint256 amount) internal {
       balances[user] += amount;
       totalSupply += amount;
   }
   ```

2. **Use events instead of storage for historical data**
   ```solidity
   // Instead of storing all historical values
   event Transfer(address indexed from, address indexed to, uint256 value);
   ```

3. **Pack storage variables**
   ```solidity
   // Bad: Uses 3 storage slots
   uint256 a;
   uint256 b;
   uint256 c;
   
   // Good: Pack into fewer slots
   uint128 a;
   uint128 b;
   uint256 c; // 2 slots total
   ```

4. **Use `calldata` for read-only function parameters**
   ```solidity
   // Bad
   function process(string memory data) public { }
   
   // Good
   function process(string calldata data) public { }
   ```

## Failed Transactions

If a transaction fails:

- Gas used up to the failure point is **still charged**
- Set appropriate gas limits to minimize losses
- Common failure reasons:
    - Out of gas
    - Contract revert
    - Invalid parameters

```javascript
try {
    const tx = await contract.methods.riskyOperation().send({
        from: account,
        gas: 500000,
        gasPrice: xdc3.utils.toWei('0.25', 'gwei')
    });
} catch (error) {
    console.log('Transaction failed:', error.message);
    // Gas is still consumed up to failure point
}
```

## Network Comparison

| Network | Avg Tx Fee | TPS | Block Time |
|---------|-----------|-----|------------|
| **XDC Network** | **~$0.00004** | **2,000+** | **2s** |
| Ethereum | $1-50+ | 15-30 | 12s |
| Polygon | ~$0.01 | 7,000 | 2s |
| BSC | ~$0.10 | 160 | 3s |
| Solana | ~$0.00025 | 65,000 | 0.4s |

## Summary

- XDC Network offers **99%+ cheaper** fees than Ethereum
- Standard gas price: **0.25 Gwei**
- Simple transfer: **~$0.00004**
- Always estimate gas before sending
- Optimize contracts to minimize gas usage

---

!!! tip "Calculate Your Costs"
    Use the [XDC Gas Station](https://xdc.blocksscan.io/gastracker) to check current network gas prices.
