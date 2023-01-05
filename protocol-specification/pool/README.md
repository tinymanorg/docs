# Pool

An AMM based decentralized exchange is made up of a number of ‘Pools’, with one pool per asset pair. Users can swap assets through these pools by sending some of one asset and receiving the equivalent value of the other asset.

The funds in the pools are owned by ‘Liquidity Providers’. Each liquidity provider contributes and retains ownership of a share of the pool’s funds. The liquidity provider receives ‘Pool Tokens’ to represent their share of the pool. They can reclaim their assets at any time by returning the pool tokens.&#x20;

Each Pool is an Algorand Account. The accounts hold the assets and state related to the pool. A single stateful Algorand Application contains all the logic that controls the asset transfers and state management of the pools.

Each Pool has a number of local state variables which are updated during every operation. The asset reserves (liquidity) of the pool are tracked in the local state and not determined dynamically from the account balances. This means that ‘donations’ to the pool or Algo making up the minimum balance do not contribute to the asset reserves.

If assets are transferred to the pool account with transactions that are not part of a documented group the assets will be lost. These assets are called “extra” and are only transferable to the fee collector. They will not affect the liquidity of the pool or the shares of the liquidity providers.

{% content-ref url="pool-creation.md" %}
[pool-creation.md](pool-creation.md)
{% endcontent-ref %}

{% content-ref url="adding-liquidity.md" %}
[adding-liquidity.md](adding-liquidity.md)
{% endcontent-ref %}

{% content-ref url="removing-liquidity.md" %}
[removing-liquidity.md](removing-liquidity.md)
{% endcontent-ref %}
