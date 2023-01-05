# Pool Creation

Pools are created with two separate operations; Bootstrap & Add Initial Liquidity.

A pool is created as a [Smart Signature Contract Account](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/smartsigs/modes/#contract-account). The Smart Signature is derived from a standard template but it is unique per pool because it contains the ids of the pair of assets.

## Bootstrap

The account is turned into a pool by issuing an Application Call transaction to the AMM app. This transaction opts the account into the app and also rekeys the contract account to the App account. \
As a contract account, this transaction must be signed by the associated Smart Signature. After this transaction is confirmed the Smart Signature no longer has authority over the account as it has been rekeyed. Instead, the AMM App has full authority over the pool account.

During the Bootstrap operation, the app creates the Pool Token asset and transfers the total supply to the pool account. These are done with Inner Transactions. All pool token assets are created by the app account so that there is a single well-known creator address of Tinyman AMM V2 pool tokens. The Reserve address of the pool token asset is set to the pool address.\
\
The Bootstrap operation requires some Algo to cover the minimum balances for the pool account (Formula I), asset creation (100000 micro Algo), and transaction fees. This Algo must be supplied to the pool prior to the Bootstrap Application Call. It will usually be in the same group but this is not required.

[Transaction Details for bootstrap](../../v2-integration/protocol-methods/bootstrap.md)
