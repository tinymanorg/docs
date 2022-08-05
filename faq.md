# FAQ

_Tinyman is in ongoing development and the following FAQs will continue to be updated as the Tinyman protocol continues to be defined._

## **What service does Tinyman offer?**

Tinyman enables users to trade/swap Assets (Tokens/Currencies) at market rates.

## Who are the users of Tinyman?

There are two classes of users of Tinyman: Swappers who trade assets and Poolers who provide asset liquidity for the trading Pools.&#x20;

Poolers are individuals/organisations who hold reasonably large amounts of assets.&#x20;

Swappers are individuals/organizations who wish to exchange tokens. They may be interested in doing this in an automated way with bots or they may use an app interface.

## What are Pools?

Pools are Accounts holding two different Assets contributed by Poolers. Swappers transfer assets to and from pools.

## Who sets the exchange rates?

The exchange rate for a swap is determined from the ratio of the pair of Assets in the Pool and the amount to be swapped. The precise rate will be different for every transaction but will always ensure the total product of the Pool stays constant (+ fees). This type of exchange is known as a Constant Product Market Maker, a type of Automated Market Maker.

## How is the exchange rate enforced?

The smart contracts of the Pool ensure that only a group of transactions for the correct amounts succeed.

## Why do Poolers provide assets?

In return for providing assets, they receive a share of transaction fees.

## How are Poolers fee shares calculated?

A Pooler is issued an amount of Pool Token proportional to their Pool contribution. This can be cashed in at any time in return for a portion of the Pools assets.

## How often does the Pooler receive fees?

Poolers only receive fees when they withdraw liquidity (assets) from the Pool by exchanging their Pool Tokens.

## Who controls withdrawals from the Pools?

The assets are held in a contract account that only allows withdrawals in two cases:

1. As one transaction of a swap where an equal value of the other asset is deposited
2. As one transaction of a withdrawal where an equal value of Pool Tokens are deposited

## Who owns the assets in a Pool?

Only the Pool Token holders have the right to withdraw assets and only in proportion to their contribution so they collectively own the Pool assets.

## Can a Pooler withdraw one asset from a Pool?

No, the Pool’s balance must be maintained so an equal value of both currencies must be withdrawn in exchange for Pool Tokens.

## How does a Swapper interact with Tinyman?

A Swapper may swap assets with the Tinyman pools using either of three methods:

1. Manually/programatically creating, signing and submitting a set of transactions that satisfy the smart contracts
2. Signing and submitting the transactions created by the helper functions of the Tinyman JS library
3. Using the web app interface to do the swap, signing the transactions with a wallet browser extension

## How does a Pooler interact with Tinyman?

Using any of the 3 methods described above for Swappers.

## How can I connect to Tinyman with my Ledger account?&#x20;

Wallets that support atomic transactions for Ledger accounts can operate flawlessly with the Tinyman platform. At the moment only My Algo Wallet supports this. Hopefully other wallets will support this in the near future.

## How will the exchange rate track the general market rate?

Certain Swappers will monitor discrepancies between Tinyman rates and rates on other exchanges and trade these to their profit until the rates are equalized. This is known as arbitrage trading.

## How are Pools created?

Pools are created by submitting a specific set of transactions. The logic of the contracts ensures that only one Tinyman Pool can exist for a pair of assets.

## Who can create Pools?

Anyone can create a Pool by issuing the correct set of transactions.

## Can Pools be created for any pair of Algorand Standard Assets?

Yes, the protocol is fully permissionless so no restrictions are in place. However it is not at all advisable to create pools with assets that have a low total supply. Pools should not be created with assets that represent collectables, NFTs or similar.\
The system is designed with the expectation that the minimum input and output amount of a swap is 1000 microunits. Swapping smaller amounts than this may lead to rounding errors that negatively affect users.

## Can Pools be created with Algo as one of the ‘assets’?

Yes. Algo is not an ASA but it may be used as one of the assets in a Pool.

## Can Tinyman be used to swap NFTs?

No, AMM protocols like Tinyman are not suitable for swapping assets like NFTs.

## How is the exchange rate set at the time of Pool creation?

The Pool creation contracts do not enforce an exchange rate as they have no knowledge of the current market rates. However, it is in the Pooler's interest to ensure the ratio of assets deposits matches the market rates. Pools can always be traded against from both sides so Swappers will take advantage of any rates that don't match the overall market.

## What currency/asset is the swap fee paid in?

The fee is paid in the currency of input/sell asset. The fee amount is added to the liquidity in the pool.

## Does the platform/protocol earn fees?

The platform earns fees at %0.05 of the input amount. Pool tokens are allocated to the protocol representing the platform's share of each swap.

## Who will control the protocol fee account?

The protocol fee account will eventually be controlled by a governance process encoded in smart contracts. Holders of a governance token will be able to participate in this process and control how the fee account’s assets are used. The details of this governance system are TBD. It will not be in place at the time of the initial product launch.&#x20;

The protocol fees are claimable only by the creator of the Tinyman Validator app, a MultiSig account controlled by team members.

## Can Pool tokens be traded?

Yes they are standard assets and can be traded freely. Only the pool token is necessary to redeem liquidity from the associated Pool.

## Can't the Tinyman team change the rules of contracts and take all the assets?

No. The contracts will be published with rules that forbid anyone to change them. The team will have no way of taking assets from Pool accounts or modifying any of the contract code.

## Does that mean the Tinyman product will never change or improve?

No. The contracts themselves cannot be updated but the interface may be improved and may even interact with new contracts. If the team persuades the community that the new contracts offer advantages, the Poolers will want to move their assets to the new accounts. The old contracts will still exist and Swappers and Poolers will still be free to use them as they wish.

## What transactions are needed for a Swap?

A Swap is made by transferring some of "Asset A" to a Pool and transferring some of "Asset B" from the Pool. Algorand smart contracts only allow or reject transactions but do not initiate any transfers themselves. The Tinyman SDK/Web App will prepare a group of transactions that will be approved by the Tinyman smart contracts.

The specific group of transactions needed for a Swap are as follows:

&#x20;   0: Pay - pay fees in Algo from Swapper to Pool

&#x20;   1: App Call - NoOp call to Pair App with args 'swap'

&#x20;   2: AssetTransfer - transfer sell asset from Swapper to Pool

&#x20;   3: AssetTransfer - transfer buy asset from Pool to Swapper

The app call transaction (1) verifies that the amounts of transactions 2 and 3 satisfy the constraint of the Pool.&#x20;

The Pay transaction (0) is required to transfer enough Algos to the Pool to cover the fees of transactions 1 and 3.

Transactions 0 and 2 must be signed by the Swapper.

## What happens if the Pool exchange rate changes between the time of preparing the transactions and execution (slippage)?

This will be a common occurrence in Pools with high volume. Tinyman handles this by including slippage tolerance in the preparation of the transactions to reduce the possibility of asking for more of an asset than allowed by the rate. If the initial set of swap transactions succeed, the minimum amount will be received. The Pool will likely hold some excess that can be reclaimed with a subsequent transaction. The excess is redeemed with a Redeem transaction group.\


## What transactions are needed to Redeem excess?

The specific group of transactions needed for a Redeem is as follows:

&#x20;   0: Pay - pay fees in Algo from Swapper to Pool

&#x20;   1: App Call - NoOp call to Pair App with args 'redeem'&#x20;

&#x20;   2: AssetTransfer - transfer asset from Pool to Swapper

The app call transaction (1) verifies that the amount in transaction 2 is the same as the amount of excess stored in the Pool for the Swapper.

The Pay transaction (0) is required to transfer enough Algos to the Pool to cover the fees of transactions 1 and 2.

Transaction 0 must be signed by the Swapper.

## Is Excess a type of reward or profit?

No, excess is simply an IOU or change from some operations with the pool due to slippage tolerance. Read more about it [here](tinyman-amm-basics/slippage-and-excess.md).

## Are any additional transactions required to Swap on Tinyman?

The Swapper must Opt-In to the Tinyman Validation app once. They must also Opt-In to receive Assets that they have not previously received.

As with all Apps and Assets on Algorand, each Opt-In increases the minimum balance of Algos required. This is not a fee but a minimum balance that must be held.

## How does the Swapper know the correct amounts to include in their Swap transactions?

The Tinyman SDK/Web App will calculate these based on the Swapper input amounts using information retrieved from the network on the current asset amounts held by the Pool account. The formula to determine the swap amounts including fees is publicly known and encoded in the SDK/Web App.&#x20;

## How does Tinyman mark Assets as Verified?

Tinyman does not "Verify" any Asset and does not play any role in the verification process. This process is carried out by Pera Wallet. Tinyman pulls all verification information from Pera Wallet. Check out Pera Wallet's verification program [here](https://explorer.perawallet.app/asa-verification/).

Note that there is another verification program by Algoexplorer.io and it is not connected to Pera Wallet's verification system or the information that appears on Tinyman.

## **What is impermanent loss?**

CoinMarketCap defines impermanent loss as “the temporary loss of funds occasionally experienced by liquidity providers because of volatility in a trading pair.” To put this into perspective, if you are holding an LP token, and one of the assets depreciates in value in the short term, but gradually returns to the original price, then you would have lost value "impermanently." Alternatively, if the same asset appreciated in value before reverting to the mean, you would have had "impermanent gains." These metrics can help liquidity providers balance their portfolios for optimal ratios. For instance, if you think a token will appreciate, and then revert to the mean, you might provide liquidity before it appreciates, just to accumulate the fees for that duration.\
\
If you'd like to learn more about impermanent loss, the following articles may be useful:\
[https://pintail.medium.com/understanding-uniswap-returns-cc593f3499ef](https://pintail.medium.com/understanding-uniswap-returns-cc593f3499ef)\
[https://blog.bancor.network/beginners-guide-to-getting-rekt-by-impermanent-loss-7c9510cb2f22](https://blog.bancor.network/beginners-guide-to-getting-rekt-by-impermanent-loss-7c9510cb2f22) \
****

## Does Tinyman earn commission when I add Algo with Moonpay?

No, Tinyman has setup an integration with Moonpay with 0 fees/commission for Tinyman. This integration is provided purely as a convience for Tinyman users.

## **How can I get help with buying Algo with Moonpay ?**

For any issues related to Moonpay please checkout their support page here: [https://support.moonpay.com/hc/en-gb/categories/360001595097-Customer-Support-Help-Centre](https://support.moonpay.com/hc/en-gb/categories/360001595097-Customer-Support-Help-Centre)
