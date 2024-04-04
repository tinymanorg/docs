# Migration FAQ

### How does Migration work?

Tinyman Migration allows users to transfer their liquidity and redeemables from a V1 pool to a corresponding V2 pool. It streamlines the process of migrating assets by handling all necessary steps under a single flow. When you initiate a pool migration with Tinyman, it will provide a list of all the steps it will complete.

### Is there a difference between migrating to an already existing pool and creating a new pool in V2?

Yes, there is a difference between creating a new pool in V2 and migrating to an already existing pool.&#x20;

When creating a new pool, a user must pay an additional Algo for the creation of the pool account, lock the initial 1 LP token, and set the price.&#x20;

Migrating to an existing V2 pool, on the other hand, does not require these actions and users follow the current price of the V2 pool when adding liquidity. It is also possible that flexible liquidity adding, with internal swaps to match the proportions of the pool and user funds, may be required when moving to an existing pool.

### During migration, why do I see different amounts of V1 and V2 LP tokens?

The amounts of V1 and V2 LP tokens may differ during migration due to the mathematical assessments of the protocol. The difference in LP token amounts does not necessarily imply any specific meaning or difference in value.

### Will the dollar value of my LP tokens stay the same after migrating V2 pools?

The dollar value of LP tokens may not remain the same after migrating to V2 pools.&#x20;

If a user is creating a new pool, pool creation fees and locked LP tokens will decrease the funds being added.&#x20;

If the user is adding liquidity to an existing V2 pool, a price difference between V1 and V2 pools is expected. The process of adding liquidity to an existing V2 pool while adjusting the liquidity to match the ratio of assets in the pool, known as flexible liquidity adding, will incur a swap fee and may cause a fluctuation in funds.

### I see a different APR or no APR for v2 pools, why?

APR and APY values for V1 and V2 pools may differ because Tinyman calculates these values based on 1-day and 7-day trade volumes for each individual pool. Additionally, APR/APY values for newly created V2 pools, in particular, may be low or nonexistent in the early days of Tinyman V2.
