---
title: XDC Subnet 
---

# XDC Subnet 

![xdc-subnet-ui](./img/xdc-subnet-ui.png)

XDC Subnet is a technology that allows you to create a secure, scalable, and decentralized network within the XDC Ecosystem. It enables various use cases, including creating private subnets, deploying decentralized applications (dApps), and more.
Are you ready to embark on a journey into the world of secure, scalable, and decentralized networks? Look no further than XDC Subnet, the cutting-edge technology that empowers you to create a digital realm tailored to your needs within the thriving XDC Ecosystem.


## Motivation & Design Rationale

As a leading Layer-1 (L1) public blockchain, XinFin's XDC network has attrated many enterprise and institutional customers. Besides the high performance and high security that XDC already offers, these customers also demand privacy, meaning that their transactions and ledger should not be disclosed to the public. This requirement prohibits them from directly submitting transactions to XDC. Instead, they should only checkpoint snapshots of their ledger to XDC in order to extract XDC's security.

From a system perspective, "security via checkpointing" is achieved via Layer-2 (L2) techniques, such as rollups and subnets. The most popular rollup technique, namely optimistic rollup, is not suitable for our use case. This is because while transaction execution is offloaded to L2, all these L2 transactions are still submitted to L1 as a record. Another popular rollup called zero-knowledge (ZK) rollup solves this problem. But ZK computation is slow, and the type of use cases it can currently support is very limited (such as token transfers), which cannot fulfill the diverse business needs of XDC's enterprise and institutional customers.

On the other hand, subnet is a perfect solution. By subnet, the customer runs a blockchain and checkpoints its critical consensus data to the parent chain. This way, not only is privacy preserved, the subnet can have its own security and resiliency besides those provided by the parent chain. This is particularly useful to enterprise and institutional customers who may collaborate with untrusted partners. A common criticism against subnet solutions is the high entry bar and operational cost of running a blockchain. However, in XDC's case, this is indeed welcomed becomes enterprise and institutional customers prefer owning the infrastructure in a private and isolated domain.


Motivated by this opportunity, XDC's core protocol team has tailor-designed a subnet solution for XDC's enterprise and institutional customers. It has the following main features:
1.	the subnet will be a sovereign, permissioned, and high-performing blockchain wholly owned by the customer.
2.	the subnet will be driven by XDC2.0, the most advanced and secure consensus engine originally-built for XDC in-house, and will be deployed to the XDC mainnet, too.
3.	a security level equivalent to the sum security of the subnet AND XDC mainnet.
4.	native EVM smart contract support.
5.	total privacy (i.e., no visibility) of the subset transactions on the XDC mainnet.
6.	full access and compatibility to XDC's abundant SDK and tools, such as the explorer and forensic monitoring system.

## Architecture
The architecture consists of the following key components owned by the customer:

- A subnet driven by the XDC2.0 consensus engine, with system configurations tailored for the customer
- A relayer program that checkpoint critical consensus data of the subnet to the XDC Mainnet
- A smart contract in the XDC Mainnet that verifies and records the checkpoints
- Wallet APIs that enable additional protection of subnet transaction from the XDC Mainnet
- The subnet will also natively support XDC's abundant utility tools such as blockchain explorer and forensic monitor

![subnet-image](./img/xdc-subnet-architecture.svg)

