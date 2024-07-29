# Governance Vault

## Overview

Tinyman Governance Vault is a smart contract that holds and manages the TINY tokens being staked for governance. When a user stakes their TINY tokens, they are transferred to the governance vault contract. The governance vault is responsible for managing the lockup period, participating in governance proposals, and continuous stake rewards. The longer a user stakes their tokens, the more voting power they accumulate. However, there is also a time decay factor. As the unlock period gets closer, the voting power diminishes.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Governance Vault</p></figcaption></figure>

Locking Mechanism\



### Locking Duration:&#x20;

* Users will have pre-defined time period options to lock their tokens to the governance vault.
  * 1 Month = 4 Weeks (Minimum commitment)
  * 3 Months = 12 Weeks&#x20;
  * 6 Months = 24 Weeks
  * 1 Year = 52 Weeks
  * 2 Years = 104 Weeks
  * 3 Years = 156 Weeks
  * 4 Years = 208 Weeks (Maximum commitment)
* There is no withdrawal during the active lock period. When a user stakes their TINY tokens, they are locked up for the period of their choosing, which can range from 1 month to 4 years. During this time, the user's tokens cannot be transferred or sold, and they are not available for trading.
* The governance vault contract tracks the lockup period and prevents users from withdrawing their tokens before it ends.&#x20;
* Once the lockup period has ended, users can withdraw their staked TINY tokens, and they become available for trading.
* When users lock TINY tokens, they will be able to see their voting power and estimated governance rewards over time.&#x20;

### Locking Amount:

* There is a minimum limit for locking tokens to the governance vault: 10 TINY&#x20;
* There is no maximum token limit to having a commitment; it is unlimited.
* The same rule applies to updating/extending an existing commitment. Users should update their commitment with at least 10 TINY tokens.



### Extending the governance commitment:

* When users stake their TINY tokens, they are locked up for a period of time. However, they can update their commits to increase their voting power.
* There will be 3 forms of extending the commitment: (Amount x Duration)
  * Case1: Increasing the amount for the same duration
  * Case2: The same amount for a longer duration
  * Case3: Increasing the amount for a longer duration
  * E.g. Existing Commitment: 1000 TINY x 1-year
    * Case1 – Updated Amount: 2000 TINY x 1-year
    * Case2 – Updated Duration: 1000 TINY x 2-year
    * Case3 – Updated the two: 2000 TINY x 2-year
* The minimum limit for locking tokens is also valid for extending the commitment.&#x20;
* Updating the commitment is a unidirectional action, with a positive impact:
  * There is no withdrawal during the active lock period.
  * There is no decrease in the locked amount.&#x20;
  * There is no shortening of the time duration of the commitment.
* When users extend their commitment, the governance system grants them a new level of Tiny Power, increasing their share of the governance rewards and voting power in the governance process.
  * Updated Power will be valid for the upcoming governance reward cycle.
  * Additionally, the updated voting power will apply only to future governance proposals, not to any existing or active proposals.



## Tiny Power

* TINY Power, is a concept within the Tinyman Governance system. &#x20;
* It is a measure of a user's commitment to the governance process and is determined by the number of tokens committed and the duration of the commitment. (TINY Power = Committed Amount x Commitment Duration)
* The TINY Power affects the portion of governance rewards that users receive, as well as increasing their voting power in the governance process.&#x20;
* This incentivizes users to make longer commitments to the governance system, as it allows them to have a greater say in the decision-making process and receive greater rewards.
* **Formula**: TINY Power = “Committed Amount / 208 x Remaining Weeks”
  * The number of tokens to be locked directly increases TINY Power.
  * The locking duration also directly increases TINY Power.
  * As the unlock period gets closer, the TINY Power diminishes gradually.

<figure><img src="broken-reference" alt=""><figcaption><p>Tiny Power (over time)</p></figcaption></figure>

TINY Power directly affects the following:

* Voting Power in Tinyman Governance Proposal – Categories
  * Tinyman Protocol — Pools and Fee Structure
  * Tinyman Protocol — Roadmap & Features
  * $TINY Token – Rewards (Governance, Farming, etc.)
  * $TINY Token – Grants
* Voting Power in Liquidity Mining Rewards – TINY Token Farms. Governors will vote on governance proposals monthly and determine which pools will receive an allocation of $TINY rewards.
  * “ALGO/USDC”, “TINY/USDC”, “TINY/ALGO” – by default farms
  * Governors will be able to choose other pools of their choice in the ecosystem, such as Stable Pools, Lending Pools, Meme Tokens, etc.
* Rewards Multiplier in Tinyman Governance Rewards
  * Commit more TINY = More TINY Rewards (Weekly)
  * Commit with longer periods = More TINY Rewards (Weekly)

This token and governance structure aims to make Tinyman a sustainable protocol and gradually transfer ownership to the community. We believe that users and other projects will commit to the Tinyman Governance Vault for the long term, benefiting from participating in governance and shaping the protocol's future.

\
\


\
\
