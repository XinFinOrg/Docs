# API Reference

Complete API documentation for interacting with XDC Network.

## Overview

XDC Network provides multiple APIs for developers to interact with the blockchain:

| API Type | Use Case | Documentation |
|----------|----------|---------------|
| **JSON-RPC** | Standard blockchain queries | [JSON-RPC Reference](json-rpc.md) |
| **WebSocket** | Real-time subscriptions | [WebSocket API](./#websocket-endpoints) |
| **GraphQL** | Complex queries (via indexers) | Coming Soon |

## Quick Start

### Connect to XDC Network

=== "JavaScript (Web3.js)"
    ```javascript
    const Web3 = require('web3');
    
    // Mainnet
    const web3 = new Web3('https://rpc.xinfin.network');
    
    // Testnet (Apothem)
    const web3Testnet = new Web3('https://rpc.apothem.network');
    ```

=== "JavaScript (Ethers.js)"
    ```javascript
    const { ethers } = require('ethers');
    
    // Mainnet
    const provider = new ethers.JsonRpcProvider('https://rpc.xinfin.network');
    
    // Testnet
    const testnetProvider = new ethers.JsonRpcProvider('https://rpc.apothem.network');
    ```

=== "Python"
    ```python
    from web3 import Web3
    
    # Mainnet
    w3 = Web3(Web3.HTTPProvider('https://rpc.xinfin.network'))
    
    # Testnet
    w3_testnet = Web3(Web3.HTTPProvider('https://rpc.apothem.network'))
    ```

=== "cURL"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
    ```

## RPC Endpoints

### Mainnet

| Provider | Endpoint | Rate Limit |
|----------|----------|------------|
| XDC Official | `https://rpc.xinfin.network` | Public |
| XDC Official | `https://rpc1.xinfin.network` | Public |
| Ankr | `https://rpc.ankr.com/xdc` | Tiered |
| BlocksScan | `https://rpc.xdc.blocksscan.io` | Public |

### Apothem Testnet

| Provider | Endpoint | Rate Limit |
|----------|----------|------------|
| XDC Official | `https://rpc.apothem.network` | Public |
| BlocksScan | `https://rpc.apothem.blocksscan.io` | Public |

### WebSocket Endpoints

| Network | Endpoint |
|---------|----------|
| Mainnet | `wss://ws.xinfin.network` |
| Apothem | `wss://ws.apothem.network` |

## Common Queries

### Get Block Number

```javascript
const blockNumber = await web3.eth.getBlockNumber();
console.log('Current block:', blockNumber);
```

### Get Balance

```javascript
const balance = await web3.eth.getBalance('xdc71C765...');
console.log('Balance:', web3.utils.fromWei(balance, 'ether'), 'XDC');
```

### Get Transaction

```javascript
const tx = await web3.eth.getTransaction('0x123...');
console.log('Transaction:', tx);
```

### Send Transaction

```javascript
const tx = await web3.eth.sendTransaction({
    from: '0x...',
    to: '0x...',
    value: web3.utils.toWei('1', 'ether'),
    gas: 21000,
    gasPrice: web3.utils.toWei('0.25', 'gwei')
});
```

## Address Format

XDC Network supports two address formats:

| Format | Example | Use Case |
|--------|---------|----------|
| **0x format** | `0x71C7656EC7ab88b098defB751B7401B5f6d8976F` | Standard EVM format |
| **xdc format** | `xdc71C7656EC7ab88b098defB751B7401B5f6d8976F` | XDC-specific display |

Both formats represent the same address. Convert between them:

```javascript
// xdc to 0x
const ethFormat = xdcAddress.replace('xdc', '0x');

// 0x to xdc
const xdcFormat = ethAddress.replace('0x', 'xdc');
```

## Error Handling

Common error codes and their meanings:

| Code | Message | Description |
|------|---------|-------------|
| -32700 | Parse error | Invalid JSON |
| -32600 | Invalid request | Malformed request |
| -32601 | Method not found | Unknown method |
| -32602 | Invalid params | Invalid parameters |
| -32603 | Internal error | Server error |
| -32000 | Server error | Generic server error |

## Rate Limiting

Public RPC endpoints have rate limits to ensure fair usage:

| Endpoint Type | Limit |
|--------------|-------|
| Public | ~100 requests/second |
| Paid/Premium | Custom |

For high-volume applications:
- Run your own node
- Use premium RPC providers (Ankr, etc.)
- Implement request batching

## SDKs & Libraries

| Language | Library | Install |
|----------|---------|---------|
| JavaScript | xdc3.js | `npm install xdc3` |
| JavaScript | web3.js | `npm install web3` |
| JavaScript | ethers.js | `npm install ethers` |
| Python | web3.py | `pip install web3` |
| Go | go-ethereum | Native support |
| Rust | ethers-rs | `cargo add ethers` |

## Next Steps

- [JSON-RPC Reference](json-rpc.md) - Complete method documentation
- [WebSocket API](./#websocket-endpoints) - Real-time subscriptions
- [Error Codes](./#error-handling) - Error handling guide
