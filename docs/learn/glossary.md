# Glossary

A comprehensive glossary of terms used in XDC Network documentation.

## A

### Address
A unique identifier on the blockchain, derived from a public key. XDC addresses can be displayed in two formats:
- **0x format**: `0x71C7656EC7ab88b098defB751B7401B5f6d8976F`
- **xdc format**: `xdc71C7656EC7ab88b098defB751B7401B5f6d8976F`

### ABI (Application Binary Interface)
A JSON specification that defines how to interact with a smart contract's functions and data structures.

### Apothem
The primary testnet for XDC Network. Used for development and testing before mainnet deployment.

### Archive Node
A full node that stores all historical blockchain states, not just the latest state.

## B

### Block
A collection of transactions that are bundled together and added to the blockchain.

### Block Explorer
A web application that allows users to view blockchain data including transactions, addresses, and blocks. Examples: BlocksScan, XDCScan.

### Block Height
The number of blocks in the chain from the genesis block to the current block.

### Block Time
The average time between new blocks. XDC has a ~2 second block time.

### BFT (Byzantine Fault Tolerant)
A consensus property ensuring the network functions correctly even if some nodes are malicious or faulty.

## C

### Chain ID
A unique identifier for a blockchain network. XDC Mainnet is 50, Apothem is 51.

### Checkpoint
A snapshot of subnet state that is anchored to the XDC mainnet for security.

### Consensus
The mechanism by which nodes agree on the current state of the blockchain.

### Contract Address
The address where a smart contract is deployed on the blockchain.

## D

### DApp (Decentralized Application)
An application that runs on a decentralized blockchain network rather than centralized servers.

### DeFi (Decentralized Finance)
Financial services built on blockchain technology without traditional intermediaries.

### Delegated Proof of Stake (DPoS)
A consensus mechanism where token holders vote for validators to secure the network.

## E

### Epoch
A fixed period of blocks (900 blocks on XDC) after which validator sets may change.

### EVM (Ethereum Virtual Machine)
The runtime environment for smart contracts. XDC is EVM-compatible.

## F

### Finality
The guarantee that a transaction cannot be reversed. XDC achieves instant finality through BFT consensus.

### Fork
A change in blockchain protocol or a split in the chain history.

### Full Node
A node that stores the complete blockchain and validates all transactions.

## G

### Gas
A unit measuring computational effort required to execute operations on the blockchain.

### Gas Limit
The maximum amount of gas a user is willing to spend on a transaction.

### Gas Price
The amount of XDC (in Gwei) paid per unit of gas. Determines transaction priority.

### Genesis Block
The first block in a blockchain (block 0).

### Gwei
A denomination of XDC. 1 XDC = 1,000,000,000 Gwei.

## H

### Hash
A fixed-length cryptographic fingerprint of data. Used extensively in blockchain for security.

### Hot Wallet
A wallet connected to the internet, used for frequent transactions.

## I

### ISO 20022
An international standard for financial messaging that XDC Network supports.

## K

### KYC (Know Your Customer)
Identity verification process required for regulatory compliance.

## L

### Layer 1 (L1)
The base blockchain network. XDC Mainnet is a Layer 1.

### Layer 2 (L2)
Solutions built on top of L1 to improve scalability. XDC Subnets can function as L2.

### Liquidity
The ease with which an asset can be bought or sold without affecting its price.

## M

### Mainnet
The primary public XDC blockchain network where real transactions occur.

### Masternode
A validator node on XDC Network that requires 10M XDC stake and participates in consensus.

### Mempool
A waiting area for unconfirmed transactions before they're included in a block.

### Mnemonic / Seed Phrase
A series of words (usually 12 or 24) that can recover a wallet's private keys.

## N

### Node
A computer running blockchain software that maintains a copy of the ledger.

### Nonce
A number used once in transaction ordering to prevent replay attacks.

## O

### Oracle
A service that provides external data to smart contracts.

## P

### Private Key
A secret cryptographic key that proves ownership of an address. Never share this!

### Proof of Stake (PoS)
A consensus mechanism where validators are chosen based on their token stake.

### Protocol
The rules governing how the blockchain operates.

### Public Key
A cryptographic key derived from the private key, used to generate addresses.

## R

### RPC (Remote Procedure Call)
An API protocol for interacting with blockchain nodes.

### RWA (Real-World Assets)
Physical or financial assets tokenized on the blockchain.

## S

### Slashing
Penalty mechanism that reduces a validator's stake for misbehavior.

### Smart Contract
Self-executing code deployed on the blockchain that runs when conditions are met.

### Solidity
The primary programming language for EVM smart contracts.

### Staking
Locking tokens to participate in network security and earn rewards.

### Standby Node
A node ready to become a Masternode if an active one fails.

### Subnet
A separate blockchain network connected to XDC mainnet.

## T

### Testnet
A blockchain network for testing, using valueless tokens.

### Token
A digital asset created on a blockchain using smart contracts (e.g., XRC20 tokens).

### Transaction
A signed message that transfers value or interacts with a smart contract.

### Transaction Fee
The cost paid in XDC to execute a transaction.

### TVL (Total Value Locked)
The total value of assets deposited in DeFi protocols.

### TPS (Transactions Per Second)
A measure of blockchain throughput. XDC supports 2,000+ TPS.

## V

### Validator
A node that participates in consensus by proposing and validating blocks.

## W

### Wallet
Software or hardware that stores private keys and allows interaction with the blockchain.

### Web3
The concept of a decentralized internet built on blockchain technology.

### Wei
The smallest denomination of XDC. 1 XDC = 10^18 Wei.

## X

### XDC
The native token of XDC Network, used for transactions, staking, and governance.

### XDPoS
XinFin Delegated Proof of Stake - XDC Network's consensus mechanism.

### XRC20
XDC's fungible token standard, equivalent to Ethereum's ERC20.

### XRC721
XDC's non-fungible token (NFT) standard, equivalent to Ethereum's ERC721.

### XDC Zero
Cross-chain bridge technology connecting XDC mainnet with subnets.

---

!!! note "Missing a term?"
    Suggest additions by editing this page on [GitHub](https://github.com/XinFinOrg/Docs/edit/main/docs/learn/glossary.md).
