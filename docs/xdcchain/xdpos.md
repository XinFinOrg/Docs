---
title: Overview - XDC Chain
---

# XDPoS - XDC's Consensus Mechanism

XinFin Delegated Proof of Stake(XDPoS) is another form of Proof of Stake(PoS) consensus mechanism to scale up to Thousands of transactions per second. XDPOS concentrates block production in the hands of few semi-trusted entities in order to achieve more scalability than Proof of Work(PoW) or other Proof of Stake blockchains. XDPOS leverages the power of stakeholder to resolve consensus issues in a fair and democratic way. The Self KYC feature added in XinFin XDPoS is more enterprise and regulator friendly.

## Common Terms
* **Nominator:** A coin holder who stakes or delegates their coin to one or more validator. 
* **Validator:** A semi-trusted entity responsible for validating and producing blocks. 
* **Epoch:** A cycle of few blocks in which validator nodes create blocks in turn.

## Transition from PoW to XDPoS
The traditional PoW mechanism, while effective in securing networks, is highly energy-intensive due to its reliance on solving complex cryptographic puzzles across all nodes in the network. This results in significant electricity consumption and poses environmental concerns. Recognizing these drawbacks, XinFin transitioned away from PoW and adopted Proof of Stake (PoS), a more energy-efficient consensus methodology. Eventually, XinFin advanced to XinFin Delegated Proof of Stake (XDPoS), which further enhances the efficiency and security of the network.

To understand XDC Network's decision to adopt XDPoS, it's essential to explore the various consensus mechanisms.

## Understanding Consensus: PoW vs. PoS vs. XDPoS
In blockchain technology, consensus refers to a general agreement among nodes in the network, which is crucial for maintaining the integrity and accuracy of the distributed ledger. Unlike centralized systems like banks, where a central authority maintains records, blockchain relies on distributed ledgers to record information. Consensus ensures that all nodes agree on the state of the blockchain, including account balances, transactions, and more.

**Proof of Work (PoW)**
PoW relies on nodes solving cryptographic puzzles to validate transactions and create new blocks. This process requires significant computational power and consumes vast amounts of electricity, making it environmentally unsustainable and costly.

**Proof of Stake (PoS)**
PoS eliminates the need for energy-intensive computations. Instead of miners, PoS relies on validators who lock a portion of their cryptocurrency as a stake. Validators are chosen to propose the next block based on their stake and uptime. When a validator discovers a block that can be added to the blockchain, they validate it by placing a bet on it. The validators receive rewards proportional to their bets.

**XinFin Delegated Proof of Stake (XDPoS)**
XDPoS is an evolution of PoS and offers greater efficiency. It uses a reputation-based system to achieve consensus, where master nodes create blocks in a round-robin manner. The network elects block producers (also known as witnesses) who are responsible for validating transactions and creating the next block. The key features of XDPoS include:

* **Random Election of Block Producers:** Block producers are elected randomly and are limited in number. They are responsible for signing and creating blocks.
* **Block Validators:** These full nodes verify that the blocks created by block producers adhere to consensus rules.
* **Community Governance:** Unlike PoS, XDPoS provides the community with more governance rights, allowing them to have a greater say in the network's operations.

## Pros and Cons of XinFin Delegated Proof of Stake
## Advantages

* **Speed:** XDPoS enables faster transaction processing due to the limited number of witnesses involved.
* **Cost Efficiency:** The reduction in the number of participants in block creation lowers transaction costs.
* **Scalability:** XDPoS improves the network's scalability by ensuring efficient block creation and validation.
* **Security:** The reputation system and regular monitoring of witnesses help maintain the integrity of the network. Malicious actors can be penalized or removed by other master nodes.

## Disadvantages
* **Centralization Risk:** Since only master nodes can create blocks, there is a risk of centralization if these nodes collude.
* **Limited Participation:** The limited number of block producers may reduce the inclusiveness of the consensus process.

## Why XDC Network Prefers XDPoS
XDC Network chose XDPoS for its network due to its superior speed, cost efficiency, and scalability. XDPoS offers a more democratic, faster, and effective way to scale the network, making it the ideal consensus mechanism for XDC's hybrid blockchain platform.