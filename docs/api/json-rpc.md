# JSON-RPC API Reference

Complete reference for XDC Network JSON-RPC methods. XDC is fully compatible with Ethereum JSON-RPC API.

## Making Requests

All requests follow the JSON-RPC 2.0 specification:

```json
{
    "jsonrpc": "2.0",
    "method": "method_name",
    "params": [],
    "id": 1
}
```

## Ethereum Namespace (`eth_`)

### eth_blockNumber

Returns the current block number.

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x5e4b8c3"
    }
    ```

---

### eth_getBalance

Returns the balance of an address.

**Parameters:**
1. `address` - Address to check
2. `block` - Block number or "latest", "earliest", "pending"

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_getBalance",
        "params":["0x71C7656EC7ab88b098defB751B7401B5f6d8976F", "latest"],
        "id":1
      }'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x8ac7230489e80000"
    }
    ```

---

### eth_getTransactionCount

Returns the number of transactions sent from an address (nonce).

**Parameters:**
1. `address` - Address
2. `block` - Block number or tag

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_getTransactionCount",
        "params":["0x71C7656EC7ab88b098defB751B7401B5f6d8976F", "latest"],
        "id":1
      }'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x29"
    }
    ```

---

### eth_sendRawTransaction

Submits a signed transaction to the network.

**Parameters:**
1. `data` - Signed transaction data

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_sendRawTransaction",
        "params":["0xf86c0a8502540be400825208..."],
        "id":1
      }'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"
    }
    ```

---

### eth_call

Executes a call without creating a transaction.

**Parameters:**
1. `object` - Transaction call object
2. `block` - Block number or tag

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_call",
        "params":[{
          "to": "0xContractAddress",
          "data": "0x70a08231000000000000000000000000..."
        }, "latest"],
        "id":1
      }'
    ```

---

### eth_estimateGas

Estimates gas needed for a transaction.

**Parameters:**
1. `object` - Transaction object

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_estimateGas",
        "params":[{
          "from": "0x...",
          "to": "0x...",
          "value": "0xde0b6b3a7640000"
        }],
        "id":1
      }'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x5208"
    }
    ```

---

### eth_gasPrice

Returns the current gas price in wei.

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":1}'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x3b9aca00"
    }
    ```

---

### eth_getBlockByNumber

Returns block information by number.

**Parameters:**
1. `block` - Block number (hex) or tag
2. `full` - If true, returns full transaction objects

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_getBlockByNumber",
        "params":["latest", false],
        "id":1
      }'
    ```

---

### eth_getBlockByHash

Returns block information by hash.

**Parameters:**
1. `hash` - Block hash
2. `full` - If true, returns full transaction objects

---

### eth_getTransactionByHash

Returns transaction information by hash.

**Parameters:**
1. `hash` - Transaction hash

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_getTransactionByHash",
        "params":["0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b"],
        "id":1
      }'
    ```

---

### eth_getTransactionReceipt

Returns the receipt of a mined transaction.

**Parameters:**
1. `hash` - Transaction hash

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": {
            "transactionHash": "0x...",
            "blockHash": "0x...",
            "blockNumber": "0x5e4b8c3",
            "contractAddress": null,
            "cumulativeGasUsed": "0x5208",
            "gasUsed": "0x5208",
            "logs": [],
            "status": "0x1"
        }
    }
    ```

---

### eth_getLogs

Returns logs matching filter criteria.

**Parameters:**
1. `object` - Filter object with:
    - `fromBlock` - Start block
    - `toBlock` - End block
    - `address` - Contract address
    - `topics` - Array of topics

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{
        "jsonrpc":"2.0",
        "method":"eth_getLogs",
        "params":[{
          "fromBlock": "0x5e4b8c0",
          "toBlock": "latest",
          "address": "0xContractAddress",
          "topics": ["0xddf252ad..."]
        }],
        "id":1
      }'
    ```

---

### eth_chainId

Returns the chain ID.

=== "Request"
    ```bash
    curl -X POST https://rpc.xinfin.network \
      -H "Content-Type: application/json" \
      -d '{"jsonrpc":"2.0","method":"eth_chainId","params":[],"id":1}'
    ```

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "0x32"
    }
    ```

| Network | Chain ID (Hex) | Chain ID (Dec) |
|---------|----------------|----------------|
| Mainnet | 0x32 | 50 |
| Apothem | 0x33 | 51 |

---

### eth_getCode

Returns code at a given address.

**Parameters:**
1. `address` - Contract address
2. `block` - Block number or tag

---

### eth_getStorageAt

Returns storage at a specific position.

**Parameters:**
1. `address` - Contract address
2. `position` - Storage slot
3. `block` - Block number or tag

## Net Namespace (`net_`)

### net_version

Returns network ID.

=== "Response"
    ```json
    {
        "jsonrpc": "2.0",
        "id": 1,
        "result": "50"
    }
    ```

### net_listening

Returns true if client is listening for connections.

### net_peerCount

Returns number of connected peers.

## Web3 Namespace (`web3_`)

### web3_clientVersion

Returns the client version.

### web3_sha3

Returns Keccak-256 hash of the given data.

## Method Summary

| Method | Description |
|--------|-------------|
| `eth_blockNumber` | Current block number |
| `eth_getBalance` | Account balance |
| `eth_getTransactionCount` | Account nonce |
| `eth_sendRawTransaction` | Submit signed tx |
| `eth_call` | Execute call |
| `eth_estimateGas` | Estimate gas |
| `eth_gasPrice` | Current gas price |
| `eth_getBlockByNumber` | Block by number |
| `eth_getBlockByHash` | Block by hash |
| `eth_getTransactionByHash` | Transaction details |
| `eth_getTransactionReceipt` | Transaction receipt |
| `eth_getLogs` | Filter logs |
| `eth_chainId` | Chain ID |
| `eth_getCode` | Contract code |
| `eth_getStorageAt` | Storage value |
| `net_version` | Network ID |
| `web3_clientVersion` | Client version |

## Batch Requests

Send multiple requests in one call:

```bash
curl -X POST https://rpc.xinfin.network \
  -H "Content-Type: application/json" \
  -d '[
    {"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1},
    {"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":2}
  ]'
```
