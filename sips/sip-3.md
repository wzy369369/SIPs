---
sip: 3
title: Add a No-loss Prize Game
status: WIP
author: Symblox Dev (@symblox)
discussions-to: https://t.me/SymbloxSIP
created: 2020-10-26
---

<!--You can leave these HTML comments in your merged SIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new SIPs. Note that an SIP number will be assigned by an editor. When opening a pull request to submit your SIP, please use an abbreviated title in the filename, `sip-draft_title_abbrev.md`. The title should be 44 characters or less.-->

## Simple Summary

<!--"If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the SIP.-->

This proposal suggests to add a no-loss prize game on Symblox so that small VLX token holders can also have the chance to get decent amount of SYX by pooling their VLX together.

## Abstract

<!--A short (~200 word) description of the technical issue being addressed.-->

Currently, there's no steady revenue stream for Symblox, and all VLX tokens staked on Symblox are not earning any VLX staking rewards. We can solve those issues altogether by first pooling VLX tokens together on a Smart Contract, called Vault, and the Vault sends VLX tokens to earn the staking rewards. Once received staking rewards, Vault sends those rewards to Symblox swap pools and get SYX rewards in return. Finally, the Vault periodically, e.g., everday, randomly selects a winner from all stakeholders of the pool to receive all SYX rewards during that period.

## Motivation

<!--The motivation is critical for SIPs that want to change Symlox. It should clearly explain why the existing protocol specification is inadequate to address the problem that the SIP solves. SIP submissions without sufficient motivation may be rejected outright.-->

Right now, there are 2 issues with the current design of Symblox. Firstly, there are over 90 million VLX parked on Symblox, but not earning any VLX rewards, which is not ideal in terms of capital efficiency. Secondly, there are no ways for small VLX token holders to earn more SYX tokens. That means the majority of SYX tokens will be allocated to VLX whales, and that is not ideal either because Symblox needs to be as distributed as possible rather than being controlled by a handful of people. By adding a no-loss prize game, it incentivizes VLX token holders to pool their tokens together to earn a SYX reward larger than the one that they can get by staking directly to Symblox. Meanwhile, all VLX staking rewards from the tokens pooled toghether are sent to SYX/VLX swap pool that effectively brings more revenue to Symblox protocol.

## Specification

<!--The technical specification should describe the syntax and semantics of any new feature.-->

### pVault

We create a new Smart Contract called `pVault`, which is used to pool all VLX tokens together. There are 4 major functionalities for pVault.

-   Accept users' deposit and withdrawal of VLX tokens;

-   Stake users' deposited VLX to Velas Masternodes to earn VLX rewards;

-   Stake VLX rewards to Symblox to earn SYX rewards;

-   Randomly select a winning account from all stakeholders of pVault every certain period of time (e.g., every 24 hours), and send all SYX rewards generated during that period to that account.

### pVLX Token

The `pVLX` is a standard ERC20/VRC20 token, which is 1-to-1 pegged x to VLX.

#### Token Minting

When a user deposits VLX tokens to pVault, pVault mints the equivilant amount of pVLX token (as its 1:1 pegged to VLX) and sends them back to the user. It in turn, leaves the pre-defined `reserve_ratio` percent of VLX tokens in the vault, and sends the rest to Velas masternodes to earn VLX staking rewards.

When pVault gets the staking rewards, it mints the equivilant amount pVLX tokens, and stakes them to Symblox swap pool SYX/pVLX, which is created separately, to earn SYX rewards.

#### Token Burning

pVLX tokens can be converted back to VLXs anytime when a user withdraws VLX by sending pVLX tokens back to pVault. Then they will be burnt and the equivilant amount of VLX will be sent the back to the user. The pVault may act accordingly based on if it has enough VLX on the current balance. More details on this later.

### Awarding the Winner

For certain period of time, e.g., everday, pVault randomly selects a winner from all the pVLX holders. The random seed number is generated from RANDAO, which is the random number generator provided by VELAS blockchain. Then, pVault sends all SYX rewards generated during that period to the winner.

### pVLX and VLX exchange

VLX token holders can get pVLX simply by depositing VLX to the pVault.

The pVLX token holder has two options to convert pVLX back to VLX.

-   One way is that he can send pVLX to pVault directly to exchange back to VLX. pVault reserves a pre-defined `reserve_ratio` percent of VLXs for the exchange. If there are enough VLX in the vault, the user can get them backs immediately. Or, the user either has to wait for more VLX be deposited to the vault, or he can resort to the second option.

-   Another way to exchange pVLX back to VLX is thru pVLX/VLX swap on Symblox.

### Solidity

## Rationale

<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

The idea of no-loss prize game was inspired by premium bonds; the idea is that it encourages savers to deposit money into their accounts by giving them the ability to win prizes. In the UK, the government-run savings program has attracted \$100 billion in savings from one third of the population.

There's another project, called [PoolTogether](https://pooltogether.com/), also implemented the similar idea on Ethereum.

## Test Cases

<!--Test cases for an implementation are mandatory for SIPs but can be included with the implementation..-->

## Implementation

<!--The implementations must be completed before any SIP is given status "Implemented", but it need not be completed before the SIP is "Approved". While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
