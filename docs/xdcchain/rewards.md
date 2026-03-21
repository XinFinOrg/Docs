---
title: Rewards Mechanism
---

# Rewards Mechanism

The XDC Network operates on a Delegated Proof of Stake (XDPoS) consensus mechanism, which allows for high transaction throughput, energy efficiency, and security. The network’s rewards mechanism is designed to incentivize Masternode operators and participants who contribute to the stability, security, and growth of the network. This document outlines how the XDC rewards mechanism works, who is eligible for rewards, and how rewards are distributed.

## Overview of XDC Rewards System
In the XDC Network, rewards are primarily distributed to Masternode operators who validate transactions, secure the network, and propose new blocks. Additionally, XDC token holders who delegate their tokens to Masternodes also earn a share of the rewards. The rewards mechanism is structured to:

Incentivize decentralization by encouraging more participants to run Masternodes or delegate their tokens.
Reward active participation in the network, such as block validation and staking.
Ensure the economic sustainability of the XDC Network over time.

## Masternode Operator Rewards
The reward mechanism on the XDC Network is designed to incentivize both Masternodes (active validators) and Standby Nodes (backup validators) for maintaining network security, uptime, and performance.
**Rewards are distributed based on:**
- Staking 10 M XDC
- Node activity (block validation / signatures)
- Participation within each epoch

To improve efficiency and transparency, the proposed system introduces:
- Smart contract-based reward automation
- Activity-based reward validation
- Flexible distribution cycles (daily / weekly / monthly)

### Staking Requirements								

| Node Type          | Minimum Stake  |
|------------------|------------------------------------------------------------------------|
| Masternode   | 10,000,000 XDC  | 
| Standby Node | 10,000,000 XDC 

**All participating nodes must lock the required stake to:**
- Become eligible for rewards
- Participate in consensus or standby operations

### Annual Reward Rates (APR Model)
The reward system follows a fixed annual percentage return model:

| Node Type          | Annual Reward Rate  | Yearly ROI |
|------------------|-------------------|------------------------------------------------------------------------|
| Masternode   | 10% |   1,000,000 XDC  | 
| Standby Node | 8%  |   1,000,000 XDC 

**Monthly Reward Breakdown**

| Node Type          | Monthly Reward  |
|------------------|------------------------------------------------------------------------|
| Masternode   | 83,333.33 XDC  | 
| Standby Node | 66,666.67 XDC

**These values are derived as:**

- Masternode → 1000,000 / 12
- Standby Node → 800,000 / 12

### Epoch-Based Reward Distribution

The XDC Network operates on an epoch-based reward system, ensuring continuous and fair distribution.

**Epoch Configuration**

- 1 Epoch = 900 blocks (~30 minutes)
- Epochs per day = 48

**Total Reward per Epoch**

| Component          | Amount  |
|------------------|------------------------------------------------------------------------|
| Total Epoch Reward   | 5,000 XDC  | 
| Foundation Share (10%) | 500 XDC  |
| Remaining for Nodes  | 4,500 XDC  |

**Distribution Logic**

After deducting the foundation share:

- The remaining 4,500 XDC is distributed among eligible nodes
- Rewards are allocated based on:
    - Block validation (masternodes)
    - Signature participation (standby nodes)

### Per Node Reward (Masternodes)

| Metric          | Value  |
|------------------|------------------------------------------------------------------------|
| Reward per Epoch   | 2,000 XDC  | 
| Daily Reward | 96,000 XDC (2,000 × 48) |
| Monthly Reward  | ~60,000 XDC  |

**Actual rewards may vary slightly based on:**
- Participation rate
- Network conditions
- Validator set size

### Standby Node Reward Logic

**Standby nodes:**

- Do not produce blocks actively
- Earn rewards based on:
    - Uptime
    - Block signature verification
    - Availability for failover
- They receive:
    - Lower APR (8%) compared to masternodes (10%)
    - Rewards proportional to verified participation
