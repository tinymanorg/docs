# FAQ

{% content-ref url="migration-faq.md" %}
[migration-faq.md](migration-faq.md)
{% endcontent-ref %}

## Introduction

### What is Tinyman?

Tinyman is a decentralized protocol on the Algorand blockchain that enables users to trade or swap Assets at market rates. The web app ([app.tinyman.org](http://app.tinyman.org)) is a visual interface for interacting with a set of smart contracts deployed to the Algorand blockchain.

### What are Tinyman’s design principles?

Tinyman protocol is open-source, decentralized, permissionless, persistent, non-custodian, and immutable (non-upgradable).&#x20;

### What is Algorand and ALGO?

Algorand is a blockchain launched in 2018 to solve the “blockchain-trilemma” with a fast, secure, decentralized and scalable framework built with PPoS (Pure Proof of Stake) consensus mechanism. Tinyman V2 smart contracts are deployed on Algorand blockhain.\
ALGO is the native currency of the Algorand blockchain.

### What is Algorand Standard Asset?

Algorand Standard Assets (ASA) provide a standardized, Layer-1 mechanism to represent any type of Asset on the Algorand blockchain. Only ASAs and ALGO are tradable assets on Tinyman.&#x20;

### How does Tinyman work?

Tinyman protocol works with smart contracts that allow users to swap assets, provide liquidity and borrow/pay flash loans. Tinyman smart contracts are built with the Automated Market Maker(AMM) mechanism, specifically the Constant Product Formula.

### What is an AMM - Automated Market Maker?

Automated market makers (AMM) are a type of decentralized exchange (DEX) that pool liquidity from users and allow digital assets to be traded automatically and without permission. AMMs use smart contracts to provide deep liquidity, low transaction fees, and uninterrupted access for all users. They offer a highly efficient and reliable way to trade digital assets on the blockchain.

### Who can use Tinyman?

Any individual or organization interested in trading or supplying liquidity on DeFi can use Tinyman.&#x20;

### How can users interact with Tinyman?

Users can interact with Tinyman pools using either of three methods:

1. Manually/programmatically creating, signing and submitting a set of transactions that satisfy the smart contracts
2. Signing and submitting the transactions created by the helper functions of the Tinyman Python SDK and Tinyman JS SDK.
3. Using the web app to do the swap, signing the transactions with a wallet browser extension.

### How can a user connect to Tinyman? Which wallets are available currently?

Users can access Tinyman using their Algorand wallet accounts. Currently:

* [Pera Wallet,](https://perawallet.app/)
* [MyAlgoWallet,](https://wallet.myalgo.com/access)
* [Exodus Wallet,](https://www.exodus.com/)
* [Defly,](https://defly.app/)
* [Fireblocks](https://www.fireblocks.com/)

are supported on the Tinyman web app. In addition, Tinyman supports the&#x20;

* Pera Connect,
* Wallet Connect,
* AlgoSigner connection modals.

For the latest wallet list, you may check the “Connect to a wallet” button on app.tinyman.org

Tinyman protocol and platform can operate with Ledger Wallets too. These users are encouraged to follow the latest updates to their ledgers as older versions can frequently experience issues with Tinyman. You may follow Ledger’s page for the latest updates:

[https://support.ledger.com/hc/en-us/articles/360012341980-Algorand-ALGO-?docs=true](https://support.ledger.com/hc/en-us/articles/360012341980-Algorand-ALGO-?docs=true)

### What are the core Tinyman operations users can perform?

Users can:

1. Swap (exchange) assets. Those who swap on Tinyman are referred to as Traders or Swappers
2. Add/Remove Liquidity to Tinyman Pools, referred to Poolers or Liquidity Providers (LPs)
3. Earn farming rewards, referred to as Farmers

## Swap

### What is a Swap?&#x20;

Swap function allows users to exchange different assets using the liquidity provided by Tinyman pools. To initiate a swap on the web app, users may select the assets they want to exchange (input asset), specify the amount, and authorize the swap after confirming its details. If the conditions are met, then the swap will be successfully completed, and users will receive the output asset. If the transaction fails, the user will receive their input asset amount back.&#x20;

### Is there a fee when doing swaps? How much are the fees?

Yes, there is an industry-standard fee of 0.3% for all swaps on Tinyman, paid in the currency of input/sell asset. The V2 contracts for Tinyman allow for customization of swap fees, which is expected to increase flexibility and functionality in the future.

### What are slippage and slippage tolerance?

Slippage refers to the difference(slip) in price between the time a transaction is initiated and the time it is executed.&#x20;

Slippage tolerance is a user's preferred level of tolerance for slippage, expressed as a percentage. It determines the minimum output amount for a swap. For example, a slippage tolerance of "0%" means that the user does not tolerate any unfavorable change in the output amount of the swap, while a tolerance of "100%" means that the user is willing to accept any output amount.&#x20;

Tinyman's default slippage tolerance is set at 1%, which can be adjusted in the settings modal and on the swap form.&#x20;

### What is a Price Impact?

The price of a swap may change due to the depth of the liquidity pool and the size of the transaction. This change in price is known as Price Impact, which is expressed as a percentage. If the price impact of a proposed swap is greater than 5%, the Tinyman platform will display a warning and disable the swap button for a period of time. This precaution is in place to ensure that users are aware of the fair price levels, helping them to make informed decisions about their trades.

### What should Traders need to pay attention to when swapping?

It is recommended that Tinyman users compare the prices of the pool for a fair exchange, as well as consider the expected price impact and their current slippage rates during a swap. Having this information can assist users in making informed decisions about their trades. To support its users, Tinyman will also indicate on the swap form if a swap price seems ‘’fair’’, "normal" or ‘’too expensive’’

## Pool

### What is a Pool?

A pool is a collection of digital assets in a smart contract account contributed by Poolers. Pools provide liquidity for trading. Currently, each Tinyman pool contains only two assets. There is only one pool for every asset pair and currently, all pools are run by the same protocol rules.

### What is Total Value Locked (TVL)?

The total value (in $USD) of assets in the pool(s) is called Total Value Locked (TVL).

### How to add liquidity to a Pool?

Each Tinyman pool is designed to hold two specific assets and once created, only accepts those assets as liquidity. When users add liquidity to the pool, the protocol attempts to mathematically ensure that the requirements for adding assets to the pool are met.&#x20;

Tinyman V2 allows users to provide liquidity with different proportions of assets, including single-asset liquidity adding.&#x20;

### What are the Proportional Style and Flexible (FLEX) Styles?

Please read the previous answer first.

**Proportional Style Liquidity Adding** is the fundamental process for adding funds to a Tinyman pool, where the liquidity provider (LP) adds assets in the same proportion as that already present in the pool.&#x20;

**Flexible Style (FLEX) Liquidity Adding** is an alternative method that allows LPs to add any proportion of the two assets to the pool. In this case, Tinyman will perform an implicit swap to match the desired asset proportions, charging the LP a swap fee for this service and subsequently adding the assets to the Pool. **Single-asset liquidity adding** can also be done with Flexible Style on the web app.

### How much do LPs earn from swaps?

A fee of 0.3% is taken for all swaps on Tinyman. Out of this fee, the Tinyman protocol earns 0.05% and LPs earn 0.25%. The fee is paid in the currency of input/sell asset and added to the liquidity in the pool. LPs will earn a share of these fees based on their share of the pool. They can track their earnings for each pool on the "Your Positions" page.

### What is an LP token?

When liquidity providers (LPs) add assets to a Tinyman pool, they receive LP tokens that represent their share of the pool. The total value of all LP tokens represents the total value of assets in the pool, also known as the locked value. This ensures that the value of LP tokens accurately reflects the value of the assets in the pool and allows LPs to track their share of the pool.

### How do I withdraw my earnings from LP tokens?

Earnings from the swap fees accumulate within the LP tokens. To access these earnings, liquidity providers (LPs) can withdraw their liquidity from the pool. The earnings will be included in the LP tokens and can be claimed at that time.

### What is an Impermanent Loss (IL)?

We must revisit the mathematical formula of The Constant Product Model (CPM) used in AMMs to understand the Impermanent Loss. CPM’s formula is "Asset1 x Asset2 = k" where k is a constant that remains unchanged after trades and can only be adjusted when LPs add or remove funds from the pool. The "Asset 1 / Asset 2" ratio is the most current relative price.

Impermanent Loss: During trading, if the asset is traded against (sold), its amount in the pool grows and its price decreases. As a result, LPs will have more of the assets that decreased in value and less of the assets that increased in value. The difference in values between their original positions and their current positions, calculated with the most current asset prices, would yield a loss for the Liquidity Provider. This is a temporary - “impermanent” -  loss because if the market changes direction and the price returns to its original state, the loss will disappear. Similarly, any future price movements may cause this loss to appear and disappear again.

## Farm

### What is a farm?

Farms on Tinyman are programs that reward users for holding and committing specific LP tokens. Farms are a way for Tinyman to incentivize users to provide liquidity to selected pools. The farms are launched and managed by the Tinyman team, and they are funded by third-party organizations looking to offer additional incentives.

### Are LP tokens transferred or removed from users' wallets during farming?

No, LP tokens do not need to be transferred out of the user's wallet during Tinyman farming. When a user signs up for a Tinyman farming program, Tinyman simply tracks the amount of LP tokens in the user's wallet. There is no locking or movement of these tokens required. As long as the user maintains the agreed-upon amount of LP tokens in their wallet throughout the farming cycle, they will earn the corresponding rewards.

### How do I claim my farming earnings on Tinyman?

Tinyman farmers can claim their rewards at any time. These rewards can be collected after each cycle or accumulated until the farmer wishes to collect them.

## Other Services

### What are a flash loan and a flash swap?

Flash loans and flash swaps are advanced features that are currently only available on the Tinyman protocol and are not included in the web app.

A flash loan is a special transaction that allows users to borrow single or multiple assets from a pool with no collateral, provided that the borrowed assets are paid back within the same transaction group, along with a loan fee.

Flash swaps are similar to flash loans, but allow users to pay back the loan with either of the two assets in the pool, rather than just the borrowed asset.

### What other services does Tinyman offer?

Other Tinyman services and tools include:

* Analytics,
* Account Page,
* Bridge,
* Fiat on-ramp application,
* Python SDK,
* JavaScript SDK,
* Icon list for ASAs (asa-list.tinyman.org)

### What is Tinyman Analytics?

Tinyman Analytics is a feature of Tinyman that allows users to access real-time, detailed statistics, graphs, and other information about pools, assets, and transactions. By analyzing these statistics, users can make informed decisions about what to trade or which pools to provide liquidity to.

### Where can users see their wallet data?

The Tinyman Account page shows each wallet address's historical and current position data on a single page.&#x20;

### What is Bridge?&#x20;

A blockchain bridge is a tool that allows to port assets from one blockchain to another. It is used to overcome interoperability problems between different blockchains. Using bridges, users can access tokens or currencies on other chains. Tinyman has non-referral links to the following bridge applications:

* Wormhole,
* Algomint,
* pNetwork

### What is a Fiat On-ramp?&#x20;

A fiat on-ramp on Tinyman is a solution that allows users to access digital assets using their fiat holdings. Moonpay has been integrated into Tinyman, allowing users to purchase a variety of assets with their fiat currency. Tinyman does not currently charge an additional fee for its Moonpay referrals.

## Community Developers

### Where can I find Tinyman's contracts and other materials for developers?

Here is Tinyman’s GitHub: [https://github.com/tinymanorg](https://github.com/tinymanorg)

### What is Tealish?

Tealish is an easy-to-read programming language designed for the Algorand Virtual Machine (AVM), the decentralized, open-source virtual machine that is built on top of the Algorand blockchain. Tealish is designed to enable developers to build and deploy smart contracts on the Algorand blockchain.

Tealish GitHub: [https://github.com/tinymanorg/tealish](https://github.com/tinymanorg/tealish)

### What are the Tinyman protocol SDKs?

There are two SDKs for Tinyman protocol:\
Python SDK: [https://github.com/tinymanorg/tinyman-py-sdk](https://github.com/tinymanorg/tinyman-py-sdk)\
JavaScript SDK: [https://github.com/tinymanorg/tinyman-js-sdk/tree/main](https://github.com/tinymanorg/tinyman-js-sdk/tree/main)

### Were Tinyman V2 smart contracts audited?

Yes the V2 smart contracts were audited by Runtime Verification. Here is their audit report and blog:

Audit Report: [https://github.com/runtimeverification/publications/blob/main/reports/smart-contracts/Tinyman-amm-v2-audit/tinyman-amm-v2-audit-report.pdf](https://github.com/runtimeverification/publications/blob/main/reports/smart-contracts/Tinyman-amm-v2-audit/tinyman-amm-v2-audit-report.pdf)\
Blog: [https://runtimeverification.com/blog/runtime-verification-audits-tinyman-amm-v2](https://runtimeverification.com/blog/runtime-verification-audits-tinyman-amm-v2)

### Is there an ongoing community audit of Tinyman V2 smart contracts? Is there a bounty?

Tinyman encourages community developers to review and test the V2 smart contracts. There is a bug bounty of up to 200,000 USD available to incentivize these efforts. If you are interested in participating in the community audit, please visit [Bug Bounty Campaign on Immunefi](https://immunefi.com/bounty/tinymanv2/) to read more about the scope of the bug bounty and follow the guidelines for participation.

You can also reach out to us at [security@tinyman.org](mailto:security@tinyman.org) to report your findings. Please be sure to follow caution and our guidelines when submitting a vulnerability.

## Tinyman Community

### What are the official Tinyman channels?

[Discord](https://discord.gg/xJRKueQdrG)

[Telegram](https://t.me/tinymanofficial)

[Twitter](https://twitter.com/tinymanorg)

[Reddit](https://www.reddit.com/r/Tinyman/)

[Website](https://tinyman.org/)

[Youtube](https://www.youtube.com/c/tinymanorg)

### How can a user contribute to Tinyman?

Users can participate in Tinyman's social channels to share their ideas, feedback, and comments. The team values the input of all community members and appreciates their contributions. Additionally, Tinyman has community roles available for various types of volunteer work. For the most up-to-date information, you can visit the Tinyman Discord channel.

### What is Tinyman Token, and when will it be released?

Tinyman Token is an item on Tinyman's roadmap that is planned to play a significant role in the future of the project. There is no set date for the release of the token at this time, and updates will be provided as more information becomes available.

## ASA guide for Tinyman

### How can I launch my ASA on Tinyman?

To launch your Algorand Standard Asset (ASA) on Tinyman, you can create a pool by pairing it with another asset. For example, you can create an "ASA-ALGO" pool by combining your ASA with Algo.

### What are the requirements for launching a new ASA Tinyman?

Tinyman is built on the Algorand blockchain, so it relies on Algorand Standard Assets (ASAs) to function. In order to be traded on Tinyman, an asset must be minted on the Algorand blockchain.

ASAs without decimal points, often used as NFTs in the Algorand ecosystem, are not compatible with the Tinyman protocol and may cause calculations to fail or result in funds becoming stuck in pools. While it may be possible to create pools with non-decimal ASAs, it is recommended to avoid using these types of assets with the Tinyman protocol.

Tinyman system is designed with the expectation that the minimum input and output amount of a swap is 1000 microunits. Swapping smaller amounts than this may lead to rounding errors that negatively affect users. Therefore, it is not at all advisable to create pools with assets that have a low total supply.

### How can I sell my NFT on Tinyman?

Tinyman is not designed to support the sale or exchange of NFTs (non-fungible tokens), which are often ASAs with no decimals. It is not recommended to offer and trade NFTs on Tinyman.

### How can I set the initial price of my ASA?

The ratio of assets in a Tinyman pool determines its relative price. When an ASA is first introduced on the platform, the initial asset ratio establishes its price. ASA owners can set their desired price by considering the ratio of assets they are adding to the pool.

### How can I control who can swap in my pool and who can add additional liquidity?

Tinyman is completely decentralized and permissionless. Swapping, adding liquidity, and removing liquidity can be carried out by any Algorand wallet engaging with Tinyman smart contracts. Therefore, nobody can limit access to a pool, whether it be the pool creator or the protocol.

### How can I pause/stop trading on my pool?

Regardless of who creates the pool or who issues an ASA, Tinyman functionalities cannot be obstructed.

### Where can I upload my logo?

To upload your logo to the Tinyman GitHub repository, follow the steps outlined on [asa-list.tinyman.org](https://asa-list.tinyman.org/). Once you have submitted your merge request, it will be reviewed by the Tinyman team. Please be aware that this process may take a few days, and we appreciate your patience as we review and process your request.

### How can I get verification on Tinyman?

Tinyman does not verify any assets and does not play a role in the verification process. This is handled by Pera Wallet, from which Tinyman obtains all verification information. Check out Pera Wallet's verification program [here](https://explorer.perawallet.app/asa-verification/).

Please note that Algoexplorer.io also has a separate verification program that is not connected to Pera Wallet or the information displayed on Tinyman.

### What does clawback mean in Algorand?

Assets on Algorand can optionally have “clawback” functionality enabled. This option can be enabled only when creating the asset. Once enabled/disabled, it becomes a feature of the asset and cannot be changed back. This allows the creator (or another delegated address) to remove assets from a holder’s account without their permission. This feature has genuine use cases but it may also be exploited by bad actors. Tinyman does not prevent creating or listing pools with clawback-enabled assets because some of the most commonly used assets have this feature enabled (e.g. USDt).&#x20;

Tinyman informs users if clawback is enabled with a badge on the asset. Users of the platform should use this information and consider the additional trust requirements in this situation. Users should be especially wary of providing liquidity to pools with these assets if they do not trust the asset creators. Tinyman Pools, as Algorand Accounts, can be subjected to clawback of their assets. If this happens the pool no longer maintains the correct ratio of assets and the internal accounting of pool reserves and pool price is out of sync with the account. This can cause transactions on the pool to fail. Transactions will continue to fail until the pool asset balances are returned to their correct levels. There is nothing the Tinyman team can do in this scenario and there is a real risk of loss of funds.&#x20;

The clawback usage warning will remain on a pool even if the pool has been returned to its correct levels and functions correctly. This serves as an additional warning to the user that the pool is at risk of malicious actions by the asset creator.

## Tinyman

### Does Tinyman store individual user information?

No, it doesn’t. Tinyman platforms do not require users to log in with personal accounts and do not track individual visitor data.

### Is there any legal restriction to becoming a Tinyman user?

The Tinyman protocol is open to participation from individuals and entities of all regions and nationalities, subject to compliance with local regulations.
