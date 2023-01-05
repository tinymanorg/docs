# 2021-11-12 - Pool overflow errors

{% hint style="warning" %}
This issue applies only to a previous version of the contracts ([V1.0](../tinyman-v1/contracts.md#version-1.0))
{% endhint %}

### The Problem

We have discovered that some small pools in Tinyman have become stuck and unable to process swaps/mints/burns. This happens because of an overflow error in the calculations in the contracts when the price (asset ratio) is extremely high. This currently affects pools with a price ratio greater than 10,000,000:1, in the microunits of the assets.

Unfortunately the calculation occurs at the start of the swap/mint/burn code block and uses the previously stored price value so this error affects all swap/mint/burn operations on these pools and cannot be fixed by adding extra assets to the pool. Pools that currently give these errors are unfortunately unrecoverable and any assets in these pools are permanently stuck as burn (remove liquidity) operations no longer work.

Asset ratios of this magnitude are outside the design limits of the system but the system does not enforce limits to prevent a problem occurring.

There are currently 95 affected pools with a total value of approximately $4000, according to Tinyman's own price information. The majority of the value in the assets in the pools belong to the asset creators so the true value lost is significantly less than this.

#### Details

The [calculation in question](https://github.com/tinymanorg/tinyman-contracts-v1/blob/main/contracts/validator\_approval.teal#L390) involves a time component so the susceptibility of a pool to this issue is a function of price and time since the last swap/mint/burn. If `seconds_since_last_op * (price*10^6) >= 2**64` this problem occurs. A pool with a price of `100,000,000:1` must have an operation at least every 2 days to avoid this issue. For `10,000,000:1` it is 21 days, for `1,000,000:1` it is 213 days and for `100,000:1` it more than 2135 days (>5 years) days. For `USDC-Algo` at `1.98:1` it is 107332174 days (> 294,000 years).

The full list of all pools is it at the following link. The highlighted pools are currently stuck. The TTL columns indicate the time till becoming stuck for each pool:&#x20;

[https://docs.google.com/spreadsheets/d/e/2PACX-1vSItQ-wh5V57jV3o6sjB2nBmQ2VSqH\_yn3TVlcGN6twzsox4Cew2Yecgx4nNmzVYzQIxL8Ferh9wS\_U/pubhtml?gid=2124112322\&single=true](https://docs.google.com/spreadsheets/d/e/2PACX-1vSItQ-wh5V57jV3o6sjB2nBmQ2VSqH\_yn3TVlcGN6twzsox4Cew2Yecgx4nNmzVYzQIxL8Ferh9wS\_U/pubhtml?gid=2124112322\&single=true)

### FAQ

#### Can Tinyman recover these funds?

No, as a fully permissionless and trustless protocol the Tinyman developers have no special permissions on any pools. There is no way to recover the assets in these pools.

#### Can new pools be created with these assets?

The same asset pair cannot be used to create a new pool with the current contracts. This is because there is a unique deterministic pool address per asset pair.

#### Can Tinyman fix this issue?

The Tinyman developers cannot fix the current contracts but will aim to avoid this issue in future versions. There is no plan to migrate to new contracts immediately due to this issue.

#### What will Tinyman do to prevent this affecting more users?

* We will add more information to our documentation about the design limits of the system and the potential problems when those limits are exceeded.&#x20;
* We will update the web app UI to prevent the creation of pools with initial asset ratios that are likely to cause problems in short term.&#x20;
* We will update the UI to inform users when adding liquidity that their is a potential for liquidity to be lost of the price becomes greater than `1,000,000:1`

