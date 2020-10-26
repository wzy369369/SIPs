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

We will create a new Smart Contract called pVault, which will be used to pool all VLX tokens together. Once a user sends VLX tokens to the pVault, she gets the same amount of pVLX, meaning pooled VLX, in return. The token pVLX will always be 1:1 pegged to VLX, and can be converted back to VLX anytime when a user sends pVLX back to pVault.

Once pVault receives VLX tokens, it sends all VLX tokens on its balance to VLX masternodes to earn the staking rewards. When pVault gets the rewards, it converts VLX to pVLX, and stakes pVLX to Symblox swap pair SYX/pVLX, which is created separately, to earn SYX rewards.

Everyday, pVault randomly selects a winner from all the stakeholders of pVault, and sends all SYX rewards to the winner.

### Solidity

## Rationale

<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

## Test Cases

<!--Test cases for an implementation are mandatory for SIPs but can be included with the implementation..-->

## Implementation

<!--The implementations must be completed before any SIP is given status "Implemented", but it need not be completed before the SIP is "Approved". While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
