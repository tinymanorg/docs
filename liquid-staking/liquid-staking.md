# Liquid Staking

### Overview of Liquid Staking

The liquid staking solution enables users to stake ALGO directly into the Tinyman Stake Pool through the Tinyman UI. By participating in staking, users contribute to the security and decentralization of the Algorand blockchain while earning staking rewards.

### Staking Rewards

Staking rewards are distributed in ALGO. The total rewards earned per ALGO decrease as more ALGO are staked, resulting in a lower Annual Percentage Rate (APR). Rewards for tALGO are derived from two primary sources:

1. ﻿﻿Block fees - 50% of transaction fees will be paid out as block reward
2. ﻿﻿Algorand Foundation-funded supplementary bonus - Starting at 10 Algo per block, this bonus will decay by 1% every 1 million blocks. The Foundation has committed to providing bonus rewards for a period of 24 months.

### Fee Structure

Tinyman employs a fee structure that automatically deducts a portion of the staking rewards to support the protocol's sustainability. A fee of 8% is applied to the total block rewards before distribution to users. The remaining rewards are added to the tALGO value.&#x20;

### Liquid Staking Process

Upon staking ALGO, users receive tALGO in return. tALGO is a liquid token that can be traded or transferred and can be utilized for additional yield opportunities, such as re-staking, liquidity provision, and farming. Importantly, tALGO automatically accrues Algorand staking rewards without requiring active management.

### Unstaking tALGO

tALGO can be redeemed for ALGO at any time, with no lock-up periods or penalties. Upon redemption, users receive the initial ALGO amount along with any accrued staking rewards.

### Re-Staking tALGO

Users have the option to re-stake tALGO. Upon re-staking, stALGO is issued at a 1:1 ratio. stALGO represents the re-staked tALGO and allows for the earning of additional TINY rewards. While stALGO remains in the user's wallet, it cannot be transferred or traded. Holding stALGO enables continuous accumulation of TINY rewards, which can be claimed at any time from the re-staking page—unstaking is not required to access these rewards. Re-staking provides an opportunity to generate extra yield without active management.

### Re-Staking Requirements

To re-stake tALGO, a minimum of 5000 TINY power is required, which can be earned by locking TINY tokens in governance. Locking TINY qualifies users as Tinyman governors and provides various benefits, including additional TINY rewards and voting rights. For further details, please refer to this [link](https://docs.tinyman.org/token-and-governance/governance-details/governance-vault).

### Unstaking stALGO

stALGO can be unstaked at any time and redeemed for tALGO on a 1:1 basis. Any accrued TINY rewards can be claimed at any time. A minimum of 5000 TINY power is required in order to claim TINY rewards. &#x20;

### Swapping ALGO

When a user swaps ALGO to tALGO, the "stake ALGO" process is applied, staking the ALGO and issuing tALGO.

When a user swaps tALGO back to ALGO, the "unstake tALGO" process is applied, unstaking the tALGO and returning the original ALGO.





### Implementation Details & Contracts

The contract sources are available to view in the Github repo.

The repo also contains [audit reports](https://github.com/tinymanorg/tinyman-consensus-staking/tree/main/audits) and the [protocol specification](https://github.com/tinymanorg/tinyman-consensus-staking/blob/main/docs/Tinyman_Liquid_Staking_Protocol_Specification.pdf).

Github repo: [https://github.com/tinymanorg/tinyman-consensus-staking](https://github.com/tinymanorg/tinyman-consensus-staking)

### On-Chain Details

tAlgo ASA:  [2537013734](https://lora.algokit.io/mainnet/asset/2537013734)\
tAlgo App ID: [2537013674](https://lora.algokit.io/mainnet/application/2537013674)

Re-Staking App: [2537022861](https://lora.algokit.io/mainnet/application/2537022861)\
stAlgo ASA: [2537023208](https://lora.algokit.io/mainnet/asset/2537023208)
