---
title: XDC Node Architecture
---

# XDC Node Architecture

The XDC Network is a hybrid blockchain platform designed to support both public and private states, offering enterprises the ability to conduct secure, scalable, and fast transactions. At the core of this network is its node architecture, which plays a crucial role in maintaining the network's integrity, security, and efficiency. This document provides a comprehensive overview of the XDC Node Architecture, detailing the various components and their functions.

The XDC Network operates on a Delegated Proof of Stake (XDPoS) consensus mechanism, which ensures low energy consumption and high transaction throughput. The network is EVM-compatible, allowing it to support smart contracts and decentralized applications (dApps).

## Node Types in XDC Network

The XDC Network comprises several types of nodes, each serving a unique function within the ecosystem. These nodes are essential for network operations, including transaction validation, block creation, and consensus.

**Masternodes (Validator Nodes):**

- **Role:** Masternodes are responsible for validating transactions, proposing and finalizing blocks, and maintaining consensus within the network.
Requirements: To run a Masternode, operators must stake a 10 Million XDC, ensuring they have a vested interest in the network's security and performance.
Functionality: These nodes participate in the consensus mechanism, verifying transactions and adding them to the blockchain. They also play a role in voting on protocol upgrades and governance decisions.

## Full Nodes:
- **Role:** Full Nodes store the entire blockchain ledger, validating blocks and transactions independently.
- **Requirements:** Operators of Full Nodes do not need to stake XDC but must maintain a certain level of computing resources to store and process the entire blockchain.
- **Functionality:** These nodes propagate transactions across the network, ensuring that all participants have access to the same data. Full Nodes contribute to network security by verifying the integrity of the blockchain.

## Node Communication and Network Topology

The XDC Network employs a peer-to-peer (P2P) communication model where nodes interact directly with each other to share information and propagate transactions.

* **Gossip Protocol:** 
    - Nodes in the XDC Network use a gossip protocol to disseminate information about transactions and blocks. This protocol ensures that all nodes are kept up-to-date with the latest state of the blockchain, maintaining network consistency and reducing the likelihood of forks.

* **Networking Layers:**
    - **Overlay Network:** The XDC Network uses an overlay network to facilitate communication between nodes. This layer abstracts the underlying physical network, providing a virtual topology that is more manageable and secure.
    - **Transport Layer:** The transport layer is responsible for ensuring reliable communication between nodes. It handles data transmission, error checking, and retransmission in case of data loss.





