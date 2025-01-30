---
title: XDC Subnet
---

# Subnet Chain
This section specifies the subnet itself, a sovereign, permissioned, and high-performing blockchain.

## Design

XDC subnet is a blockchain network tailored for private and consortium use cases. It is powered by XDC2.0, which is the core engine of XDC network and enables state-of-the-art security against Byzantine attacks with forensics, fast transaction confirmation, and low energy consumption. It is also designed to enable secure checkpointing to XDC mainnet, so that it can harness the security, finality, and accountability of mainnet.

### XDC2.0 Protocol
As the core engine of both XDC mainnet and subnet, XDC2.0 maintains the consistency of the blockchain with strong security and performance guarantees. The Delegated Proof-of-Stake subprotocol elects a committee of masternodes. The masternodes run the state-of-the-art HotStuff consensus subprotocol to settle block generation and verification and confirm transactions. Besides, XDC2.0 protocol enables its unique feature, namely forensic monitoring. When the adversary corrupts more than 1/3 masternodes and violates safety, forensic monitoring can detect those actions and report irrefutable evidence of the culprits.

The distinction between XDC2.0 for subnet and mainnet is that for subnet the masternodes are permissioned whereas for mainnet they are permissionless. 

### Your Own Blockchain Network
XDC subnet is completely owned by you. You, the owner of the subnet, are capable of controlling several aspects of the subnet.

First, the owner regulates the master node list. More specifically, the join/retire of mater nodes is done by smart contract calls that only the owner has access to. Also, underperforming or misbehaving masternodes could be expelled by the owner. This is in contrast with XDC mainnet, where masternodes join or leave willingly as long as they follow the rule enforced by the protocol.

Second, the blockchain genesis can be configured by the owner. The owner is able to distribute initial tokens and create accounts, as well as deploy system-level smart contracts on the blockchain.

Last, the owner can customize blockchain parameters, such as epoch length, max masternode number, the quorum certificate threshold, the reward per epoch, etc.

### Integrating with XDC mainnet
Integrating with XDC mainnet will enable subnet to harness the security, finality, and accountability of XDC mainnet. This requires the subnet owner to deploy a smart contract (XDC will provide) to XDC mainnet and report block headers and masternode changes to the smart contract.

As long as the mainnet is secure, the block header information of the subnet is securely stored on the mainnet. Users can also query the mainnet for finality to enhance the confidence that the subnet transaction is indeed finalized. The subnet can also report the culprits to the forensic server of XDC mainnet when its forensic monitor module detects safety violations. When the culprit report is validated, necessary measurements should be taken by the owner to reestablish the security of the subnet.

It is worth noting that the subnet can be deployed as a standalone, independent blockchain network without integrating with XDC mainnet. The choice is up to the owner whether to harness the advantages of XDC mainnet.

## API
Subnet-specific APIs