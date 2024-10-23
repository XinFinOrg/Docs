---
title: XDC Network - Slashing Mechanism
---

# XDC Network - Slashing Mechanism

The XDC Network, utilizing the XDPoS (Delegated Proof of Stake) consensus mechanism, ensures that its validators, known as masternodes, maintain optimal performance to keep the network stable and secure. One of the key features designed to ensure this reliability is the slashing mechanism, which acts as a corrective measure for underperforming masternodes.

## Objective of the Slashing Mechanism

The primary goal of the slashing mechanism is not to penalize or blame masternodes but to maintain a stable and high-performing network. It serves to mitigate issues arising from underperforming masternodes by holding them accountable while ensuring the overall system remains efficient.

## How the XDC Network Slashing Mechanism Works
The slashing mechanism operates with a clear set of rules to manage masternode performance:

### 1. Non-Participation in Block Signing:

* If a masternode fails to sign any block during an entire epoch (a defined period within the consensus process), it will be slashed.
* The penalty for not participating in block creation during the epoch is exclusion from block production for the next four epochs. This temporary exclusion incentivizes masternodes to maintain uptime and perform their duties diligently.

### 2. Handling Multiple Underperforming Masternodes:

* If multiple masternodes are underperforming within the same epoch, they face similar slashing penalties. Masternodes that have been underperforming for the past four epochs will be kicked out of the active masternode list and are not eligible to create blocks.
* Consequently, the number of active masternodes responsible for block creation in the following epoch could drop below the full 108, which is the maximum number of validators. In such cases, the system dynamically adjusts, allowing active masternodes to proceed with block creation without waiting for the underperforming ones.

### 3. Role After Being Slashed:

* A slashed masternode can still participate in block verification and signing. This enables it to demonstrate liveness to the network by submitting signatures for new blocks.
* However, the slashed masternode is ineligible for rewards during the slashed period. It can continue verifying and signing blocks, but this participation only serves as a signal of its recovery and does not result in earning block rewards.

## Properties of the XDC Network Slashing Mechanism**
### 1. Accountability:

* The XDPoS consensus protocol ensures accountability by detecting masternodes that remain inactive for an entire epoch. A smart contract known as the Block Signer tracks the activity of each masternode.
* The Block Signer stores the signatures from all masternodes, making it easy to determine whether a masternode has been performing its duties. If a masternode has failed to provide the required number of signatures during an epoch, the slashing mechanism is triggered.

### 2. Liveness:

* A core feature of the slashing mechanism is to allow slashed masternodes to regain their status. After being excluded from the active masternode list for four epochs, the masternode can return to normal operations if it resumes block verification and signing during the slashed period.
* This property ensures that temporarily underperforming masternodes, which may have experienced technical issues such as power outages, can rejoin the network without permanent penalties.

## Comparison to Other Slashing Mechanisms
The concept of slashing is not unique to the XDC Network and has been implemented in various other blockchain networks, such as Ethereum’s Casper FFG (Friendly Finality Gadget). Casper’s slashing mechanism is designed to prevent the "nothing-at-stake" problem, where validators can choose to support multiple forks of the blockchain. In Casper, if a validator is found to have validated conflicting forks, they are severely penalized by losing a significant portion, or even all, of their staked tokens.

Unlike Casper’s more punitive approach aimed at preventing malicious behavior, the XDC Network’s slashing mechanism is designed to handle unintentional underperformance. Rather than harshly punishing validators for outages or system failures, XDC’s system focuses on ensuring network performance without creating fear of excessive penalties. The design philosophy behind XDC’s slashing mechanism is to avoid deterring participation by maintaining a fair yet firm system.

## Benefits of the XDC Slashing Mechanism
* Network Stability: By detecting and penalizing underperforming masternodes, the XDC Network ensures that the overall system remains stable and efficient.
* Encouraging Performance: Masternodes are incentivized to maintain their performance to avoid being slashed and losing rewards.
* Reduced Risk for Validators: Validators are not permanently penalized for minor lapses, such as technical issues, which encourages wider participation in the network without fear of catastrophic loss.




