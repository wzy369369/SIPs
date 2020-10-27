---
sip: 2
title: Change Rewards Ratio
status: WIP
author: Ken Nguyen <@hungypoo>
discussions-to: https://t.me/SymbloxSIP
created: 2020-10-21
---

<!--You can leave these HTML comments in your merged SIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. This is the suggested template for new SIPs. Note that an SIP number will be assigned by an editor. When opening a pull request to submit your SIP, please use an abbreviated title in the filename, `sip-draft_title_abbrev.md`. The title should be 44 characters or less.-->

## Simple Summary
<!--"If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the SIP.-->
This SIP proposes to change the current rewards ratio of 80% Swap Pool/20% Seed Pool to 90% Swap Pool/10% Seed Pool.
## Abstract
<!--A short (~200 word) description of the technical issue being addressed.-->
The current rewards ratio is 80% Swap Pool/20% Seed Pool. Because of the limited amount of SYX at launch, the Seed Pool was created to give users an incentive to participate on the platform and earn rewards. Now that there are atleast 175,000 SYX in circulation, users can use the AMM (Swap Pool) to get SYX directly. Therefore, the need to give rewards to the Seed Pool can be reduced from 20% to 10%.
## Motivation
<!--The motivation is critical for SIPs that want to change Symlox. It should clearly explain why the existing protocol specification is inadequate to address the problem that the SIP solves. SIP submissions without sufficient motivation may be rejected outright.-->
This will incentives more users to participate into the liquidity pool (Swap Pool) by giving them an extra 10%. Currently, the liquidity in the Seed Pool is not utilized to create yield. By reducing the Seed Pool rewards, users might take a leap of faith and join the Swap Pool and earn higher APR's.

## Specification
<!--The technical specification should describe the syntax and semantics of any new feature.-->

### Solidity

## Rationale
<!--The rationale fleshes out the specification by describing what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work, e.g. how the feature is supported in other languages. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

## Test Cases
<!--Test cases for an implementation are mandatory for SIPs but can be included with the implementation..-->

## Implementation
<!--The implementations must be completed before any SIP is given status "Implemented", but it need not be completed before the SIP is "Approved". While there is merit to the approach of reaching consensus on the specification and rationale before writing code, the principle of "rough consensus and running code" is still useful when it comes to resolving many discussions of API details.-->

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
