# Overview

#### Overview <a href="#docs-internal-guid-cc253a8b-7fff-e763-4b36-c841dab7a1c0" id="docs-internal-guid-cc253a8b-7fff-e763-4b36-c841dab7a1c0"></a>

* The concept of the staking program is one of the core elements of DeFi, especially AMM platforms.
* Staking is pretty similar to Liquidity Provision, but also it allows Poolers to get “extra” rewards by a staking process.
* Poolers that agree to keep their liquidity in pre-determined Tinyman pools for a “certain amount of time”, will be eligible to earn rewards in addition to fees.&#x20;
* Tinyman will support this functionality by listing staking opportunities for those certain pools, enabling Poolers to commit to a staking program, track commitment activities, and distribute rewards on behalf of the program manager.
* The first Staking Program on the Tinyman belongs to Algorand Foundation. Therefore, all the components of the program, such as the start and end dates of the program, participation conditions, reward distribution rules, cycle durations etc. are determined by the Algorand Foundation.

#### How to Participate?&#x20;

* Users need to apply for the Staking Program in order to participate, whether they are already in the pool or not.
* Applying for a staking program is simply a commitment from a Pooler to keep a minimum balance of Pool Tokens during the whole staking period.
* Applying for a staking program requires signing an app call transaction that doesn’t transfer any assets elsewhere or alters their pool positions. By doing that, users only declare their intention to be part of the program.&#x20;
* Users can apply and participate in the program anytime as long as the program is available.&#x20;
* There will be some conditions for participation eligibility such as committing a minimum specific amount of pool tokens or its USD equivalent. Details to these specifications will be announced with each staking program.
* When users apply for a program, all available pool tokens will be recognized and utilized for the staking program by Tinyman.&#x20;

#### What are cycles?

* Cycles are the duration of staking commitment that must be completed to be eligible for the rewards.
* The cycle duration is 24-hours – it starts and ends at a specific time (UTC 00:00) every day. When one cycle ends, the other cycle starts automatically.
* Users are only able to earn rewards when they complete an entire cycle.&#x20;
* Rewards will be allocated per cycle. So, after completing a cycle successfully, users will be eligible to receive rewards per cycle based on their staked liquidity.
* The total reward amount is open to changes between cycles by the program owner.

#### How to Earn Rewards?

* Users can earn rewards only if they have applied for the program and completed the entire cycle successfully.
* Users must maintain a balance of at least the committed amount of Pool Tokens at all times throughout the cycle to remain eligible.
* As a specific amount of rewards is set for each cycle, rewards are distributed to the eligible stakers proportionally to their share of the total eligible staked amounts.
* Pooler commitments are accepted before the cycle starts. When the new cycle starts, rewards will be allocated as “Accumulated Rewards” per user according to their pool shares. They won’t be able to earn these rewards until the cycle ends. &#x20;
* The earned rewards will be credited from “Accumulated Rewards” to “Rewards to be Distributed” as users complete cycles.
* Users will receive rewards based on the number of cycles they complete successfully.&#x20;
* Users can add pool tokens to the Tinyman pools at any time. When they do so, they need to update their position in the staking program manually. That way, they will start earning rewards in the upcoming cycles according to their new commitment.

#### Leaving a Program and Ineligibility&#x20;

* Users can “leave the program” or “unstake” any time. If they do so, they won’t be eligible to earn rewards for the ongoing cycle. This does not affect the rewards previously earned by the user.
* Users have to keep the committed amount of Pool Tokens at all times during an ongoing cycle. If the Pool Token amount in the wallet goes below the committed amount, the user loses eligibility for the cycle. In case of multiple transactions of the Pool Tokens, users will only be eligible if the minimum amount stays above the committed amount at all times.
* In order to participate again, you will have to commit your pool tokens once more.
* Users can stake pool tokens any time, but earning rewards only applies to complete cycles. Therefore, users cannot qualify for rewards until the next cycle starts.&#x20;

#### How will the rewards be distributed?

* When users successfully complete cycles, their rewards will gradually accumulate in the “Rewards to be Distributed” section. Here, users will see the rewards they earned but not yet transferred to their accounts.
* Rewards to be Distributed will be (automatically) sent by the program manager to the stakers within 7-days, then it will be shown as Paid Rewards. Users do not need to claim them.

\
\
