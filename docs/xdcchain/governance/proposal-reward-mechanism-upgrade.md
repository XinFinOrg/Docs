---
title: XDC Network Protocol Upgrade Proposal - Reward Mechanism & Node Tiers
description: Proposal for XDC 2.0 Network Reward Mechanism Upgrade including Protector & Observer nodes, unlimited staking, and fee burning
---

# XDC Network Protocol Upgrade Proposal

## Reward Mechanism Upgrade & Node Tier System

**Author:** Community Proposal  
**Date:** February 2026  
**Status:** Draft

---

## Executive Summary

This proposal outlines a comprehensive upgrade to the XDC Network's reward mechanism, introducing a multi-tiered node system and enhanced economic model. The upgrade includes:

- **Three-tier node system**: Master Nodes, Protector Nodes, and Observer Nodes
- **Unlimited staking** with fixed per-node rewards
- **Enhanced fee burning mechanism**
- **Gas fee redistribution**

---

## 1. Background: How Rewards Work Today

In the current XDC Network's consensus model:

- Rewards are distributed every epoch (900 blocks)
- Total reward per epoch: 5000 XDC (defined by `XDPoSConfig.Reward`)
- 90% to block signers (Master Nodes)
- 10% to Foundation Wallet (`xdc92a289fe95a85c53b8d0d113cbaef0c1ec98ac65`)

### Current Reward Flow (3 Steps)

1. **Count Contributions**: Only block signers who were Master Nodes are counted
2. **Calculate Reward**: Fixed reward per epoch (5000 XDC)
3. **Distribute Rewards**:
   - 90% to the owner of each contributing signer
   - 10% to the Foundation Wallet

---

## 2. Proposed Changes

### 2.1 Three-Tier Node System

| Role | Rank | Total Nodes | Min Stake |
|------|------|-------------|-----------|
| Master Nodes | 1 – 108 | 108 | 10,000,000 XDC |
| Protector Nodes | 109 – 324 | 216 | 10,000,000 XDC |
| Observer Nodes | 325 – 1324 | 1000 | 10,000,000 XDC |

### 2.2 Proposed Per-Epoch Rewards

| Role | XDC Contribution | Annual Rewards | Per Epoch Reward |
|------|------------------|----------------|------------------|
| Master Node | 10,000,000 XDC | 1,000,000 XDC | ≈ 57 XDC |
| Protector Node | 10,000,000 XDC | 800,000 XDC | ≈ 45 XDC |
| Observer Node | 10,000,000 XDC | 400,000 XDC | ≈ 23 XDC |

> **Note:** Higher stake increases probability of being selected as Master Node. New selection criteria includes:
> - XDC Contribution amount
> - Node longevity (timestamp)
> - Hardware/Network resources allocated

### 2.3 Unlimited Staking

- No maximum stake limit
- Per-epoch rewards remain fixed regardless of stake amount
- Higher stake = higher probability of being selected as validator
- Voting mechanism allows community delegation

### 2.4 Fee Burning & Gas Enhancement

#### Base Fee Burning (EIP-1559 Style)

- A portion of gas fees is burned from each transaction
- Base fee varies based on network congestion
- Burn rate: 30% of base fee

#### Priority Fee Redistribution

- 70% of priority fees go to the block proposer
- 30% distributed to Protector and Observer nodes

---

## 3. Technical Implementation

### 3.1 V2Config Structure

```go
type V2Config struct {
    MasternodeReward   float64 `json:"masternodeReward"`
    ProtectorReward   float64 `json:"protectorReward"`
    ObserverReward    float64 `json:"observerReward"`
    MaxProtectorNodes int     `json:"maxProtectorNodes"`
    MaxObserverNodes  int     `json:"maxObserverNodes"`
    FeeBurnRate      float64 `json:"feeBurnRate"`
    MinStakeAmount   uint64  `json:"minStakeAmount"`
}
```

### 3.2 Implementation Steps

1. Pull candidates from parent state of epoch switch block
2. Rank by Candidate Cap (stake from owner + voters)
3. Assign roles (Master, Protector, Observer)
4. Calculate fixed rewards per contributing node
5. Distribute rewards to node owners
6. Apply 90/10 split with Foundation Wallet

### 3.3 Penalty & Inactivity

- Inactive nodes (no contribution during epoch) receive no rewards
- Penalty provision: Serve few epochs before starting rewards
- Slashing mechanism for malicious behavior

---

## 4. Gas Fee Structure

### 4.1 New Fee Model

| Component | Description |
|-----------|-------------|
| Base Fee | Dynamic, burned (30%) |
| Priority Fee | Goes to validator (70%) |
| Network Fee | Distributed to Protector/Observer nodes (30%) |

### 4.2 Gas Limit Changes

- Current gas limit: Dynamic
- Proposed increase: 2x for smart contract execution
- Special provisions for XDPoS system transactions (free)

---

## 5. Security & Activation

### Requirements

- Full security audit
- Rigorous testnet simulations
- Clearly defined activation block (`TIPUpgradeReward = big.NewInt(XXXX)`)
- Community approval via governance process

### Risk Assessment

| Risk | Mitigation |
|------|------------|
| Unprecedented model | Extensive testing |
| Edge case behaviors | Monitoring & emergency response |
| Network congestion | Dynamic fee mechanism |

---

## 6. Timeline

| Phase | Timeline | Milestone |
|-------|----------|-----------|
| Testnet | Month 1-2 | Protocol simulation |
| Security Audit | Month 3 | Audit completion |
| Community Vote | Month 4 | Governance approval |
| Mainnet Upgrade | Month 5 | Hard fork activation |

---

## 7. Conclusion

This proposal represents a major step forward for the XDC Network:

- ✅ Recognizes contribution from all node tiers
- ✅ Encourages decentralization
- ✅ Provides sustainable reward model
- ✅ Implements fee burning for deflationary mechanics
- ✅ Positions XDC for long-term growth

---

## References

- [Original Proposal](https://www.xdc.dev/gary/proposal-xdc-network-reward-mechanism-upgrade-3kkc)
- [XDC Whitepaper](../whitepaper.md)
- [XDPoS Documentation](xdpos.md)
- [XDC Architecture](../learn/xdc-architecture.md)

---

*This is a community-driven proposal. Questions and feedback are welcome.*
