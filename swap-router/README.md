# Swap Router

Tinyman Swap Router is an application that relies on both on-chain and off-chain components to offer better prices for traders in the Tinyman protocol. It is developed by the Tinyman team and aims to maximize the amount of assets users will get when trading. In the normal swap function, a swap is always executed through a single pool in Tinyman. However, the Swap Router checks multiple pools and alternative routes to find the best exchange rate in order to provide better prices using a single transaction.&#x20;

E.g., The equivalent value of the output asset for a swap:

* Normal Swap: The exchange rate of the single pool minus a related transaction fee
* Swap by Swap Router: Exchange rates of multiple pools, subtracting all related transaction fees (swapping assets between multiple pools).

Using a Swap Router can result in higher transaction fees, as it must pay fees to multiple liquidity pools to execute the swap. Nevertheless, Swap Router aims to offer a better output amount using multi-hop swaps by taking those fees into account. The Swap Router is primarily useful when there is insufficient liquidity in a single pool to complete a swap at an optimal exchange rate. There is a common situation of deep liquidity ASA-Algo pools but low liquidity ASA-ASA pools on Tinyman. Using the route of ASA-ALGO-ASA can potentially provide a better exchange rate and lower price impacts compared to using a single pool, resulting in a better swap experience for the user.&#x20;

## Methodology

From a technical standpoint, using the Swap Router is essentially equivalent to executing the Normal Swap function multiple times. These swaps are being executed on the backend and on the chain without any additional steps required on the part of the user. So, the overall swap experience is vastly improved, and the user experience is still smooth. Since all of the resulting transactions are grouped by Swap Router into a single operation, it does not have any adverse effects or risks for the users. Additionally, the Swap Router feature is optional, and users can choose to enable or disable it.

Rather than trading on a single pool, the Swap router checks the single-hop routers for two assets and suggests a path that provides the best swap rate: higher output or lower input. If the swap amount is relatively high, the router tends to suggest a route with high liquidity and low price impact.&#x20;

E.g. Swap Asset-1 for Asset-2

* Option-1: Asset-1 / Asset-2 Tinyman v1 pool
* Option-2: Asset-1 / Asset-2 Tinyman v2 pool
* Option-3: Asset-1 / ASA-A and ASA-A / Asset-2 v2 pools (best output amount)
* Option-4: Asset-1 / ASA-B and ASA-B / Asset-2 v2 pools
* Option-5: ...

All these calculations and suggestions are powered by Tinyman API, and it always proposes the best option and benefits to the users. When users do not prefer to use the Swap Router, or it is not available for some reason, swaps will be executed in Tinyman v1 or v2 pools as Normal Swap.

These are the number of transactions for each swap type. Swap Router includes all these fees in the overall calculation and takes them into account when suggesting a route.&#x20;

* Normal Swap - Fixed Input: 3
* Normal Swap - Fixed Output: 4
* Swap Router - Fixed Input: 9&#x20;
* Swap Router - Fixed Output: 10



[Swap Router App Contract](https://github.com/tinymanorg/tinyman-periphery-contracts-v2)

[Tinyman Python SDK](https://github.com/tinymanorg/tinyman-py-sdk)
