**By: Steve Henley, Rao Bhamidipati, Nutzipper**

SysOps runbook procedure for a breaking change release.

## History
Date          | Version
| :---        | :---        
May 14th 2020 | Initial Draft

## Introduction

Breaking change release is a release that is not backwards compatible. Should these procedures apply at the root shard level only or all shards? Protocol (data structures and/or API call parameters) breaking changes vs. specific implementation breaking change (scala vs java vs rust) ? Note that multiple language nodes can run in the same shard .. it might improve security and resilience.

## Validators:

All bonded node validators must participate in a breaking change release implementation to migrate from the old network to the new network at the block height announced by the Tech Governance team (with inputs from dev team).

1. Breaking change release can be submitted by
   1. RChain core developers??
   1. Proposers??
1. Editorial, approval & communication
   1. Editorial - review and edit submitted release request.
   1. Approval - review edited release request
   1. Communication
      1. Announcement procedure
         1. Atlassian release notes
         1. Social media
          1. developer.rchain.coop website
          1. Discord - development channel on RChain pub
          1. Telegram - RChain community
          1. Weekly community debrief
          1. RChain YouTube channel
1. List breaking change release in registry.
    1. Release number
    1. Change classification
        1. Soft update
        1. Breaking change
        1. Hard fork
    1. Implementation date
1. Validator identification - identify which validators are involved in the breaking change release implementation.
1.(Third item - help me here Tomislav, see log: tech governance is needed)
https://docs.google.com/document/d/1fvxMC6Bt5XwbVaLzYPy6ZPB8KzJvASO2sKRC6ZCPwpI/edit
1. Metrics
    1. **Block height start** - the block number at which validators must begin to implement a breaking change release.
        1. The recommendation is to treat validators that have not upgraded, as dead nodes until they upgrade
        1. How do we ensure that this doesn’t lead to a network security issue because most validators have not upgraded to the new release at the specified block height?
    1. Block grace period - the number of blocks within which validators must implement a breaking change release before being penalized (slashed?)
    1. Block height slash - the block number at which validators will be penalized for not completing a breaking change release implementation.
        1. (Incomplete implementation penalty - Slashing?)
1. Issue tree or stream??
1. New feature not being supported by existing validators will cause them to be slashed
    1. Have some block number where everyone has to update by a specific time
        1. Validators do not upgrade their block will be orphaned
        1. As a result validator will fork itself
    1. Possible resolution - is to have version number field in block. When a node receives a higher version block, it can simply pass on the block to other validators without doing anything with it.
        1. Incorporate into the version numbering scheme, semantics about whether the new version features break or cause slashing etc or not..
        1. Breaking/slashing causing changes should mostly be combined together into a single release, so validators have time to react and upgrade
        1. Have minimum feature set that should be support by validators for example Rholang 1.0.1
            1. Without upgrade say all features in Rholang will be breaking
            1. Example: 0.9.25.x / supports Rholang 1.0.1
  1. Casper -
