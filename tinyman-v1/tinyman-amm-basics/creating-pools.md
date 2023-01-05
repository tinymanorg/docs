# Creating Pools

For a user to be able to swap between two assets there must be a Pool for those two assets and that pool must have 'liquidity' (funds in both assets). A large amount of liquidity is required for users to be able to swap close to the mid price.

As a permissionless protocol any user can create a pool for an asset pair or provide liquidity for a pool.&#x20;

There are some important considerations when creating a pool:

* Assets in pools should only be currencies - assets with large total supply.
* Assets in pools should NOT be collectables, NFTs, or similar assets with low total supply.
* The system is designed with the expectation that the minimum input and output amount of a swap is 1000 microunits.
* A small quantity of each asset is permanently locked in the pool. This amount is displayed the first time liquidity is added.
* The initial liquidity must be provided at an appropriate ratio that matches the market rates to avoid losses to arbitrage.

