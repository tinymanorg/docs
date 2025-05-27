# Trigger Orders & Recurring Orders&#x20;

### Overview

Tinyman is introducing two powerful trading features on its decentralized exchange: Trigger Orders (Limit Orders) and Recurring Orders (DCA). These tools allow users to trade more strategically, automate purchases, and stay fully in control — all with the speed, security, and transparency of the Algorand blockchain.

### 1. Trigger Orders

#### Description

A Trigger Order (also known as Limit Order) lets users buy or sell a token at a specific price. The trade will only execute if the market reaches the price set by the user, within a timeframe they choose.

#### Benefits

* Set your preferred price for buy/sell orders
* Trade passively and strategically
* Avoid constant price monitoring
* Maintain full custody of funds at all times

#### Expiration Options

Users can choose when the order should expire:

* Never
* After 10 minutes
* After 1 hour
* After 1 day
* After 3 days
* After 7 days
* After 30 days

If the price condition is not met before the expiration, the order is canceled and the funds are returned to the user’s wallet.

#### Minimum Trade Amount

* $5 USD equivalent per order

#### Fees

* A 0.15% fee is charged when a Trigger Order is successfully executed.
* TINY governors enjoy a discounted fee of 0,1%. In order to be eligible, TINY governors need to hold a TINY power of at least 2000

#### Execution Flow

* When a user places a Trigger Order, the funds are locked into a dedicated smart contract.
* If the price target is reached, the order is executed and tokens are sent directly to the user’s wallet.
* If canceled or expired, the original funds are returned.
* Partial fills: If only part of the order is filled, the user will be able to claim the completed portion at a later stage (feature coming soon).
* Users can cancel the order at any time and funds will be returned to their wallet.

#### Example Use Case

A user places a Trigger Order to buy ALGO at $0.16, set to expire in 1 day.\
They commit $25 to the order, meeting the $5 minimum.\
If ALGO reaches $0.16 within 24 hours, the order executes automatically.\
If not, it expires and the $25 is returned.

### 2. Recurring Orders (DCA)

#### Description

A Recurring Order (also known as Dollar Cost Averaging) allows users to automate regular purchases of a token at predefined intervals. This strategy is especially useful for long-term accumulation and reducing exposure to short-term volatility.

#### Benefits

* Automate recurring token buys
* Reduce impact of market volatility
* Ideal for long-term investors
* Fully non-custodial and on-chain

#### Configuration Options

Users can define:

* Interval between orders:
  * Every minute
  * Every hour
  * Every day
  * Every week
  * Every month
* Number of executions (e.g., 5 purchases over 5 days)
* Price range (optional):
  * Users can specify a price range within which the recurring orders are allowed to execute.
  * This ensures that purchases are only made when the asset price is within a target zone, adding an extra layer of strategy.

#### Minimum Order Amount

* Each recurring execution must be at least $10 USD
* The total recurring order value must be at least $20 USD
* Example: If a user wants to schedule 5 recurring orders, they must commit at least $50 (5 x $10)

#### Fees

* A 0.15% fee is charged when a Recurring Order is successfully executed.
* TINY governors enjoy a discounted fee of 0,1%. In order to be eligible, TINY governors need to hold a TINY power of at least 2000

#### Execution Flow

* Full order value is deposited into a smart contract at creation
* The contract executes trades at the defined intervals and within the allowed price range
* After each execution, tokens are delivered directly to the user's wallet
* Orders can be canceled at any time, and unused funds will be returned

#### Example Use Case

A user sets up a Recurring Order to buy $10 of ALGO every day for 5 days, only if ALGO trades between $0.15 and $0.18.\
They commit $50 total, satisfying the $10 minimum per execution.\
Each day, if ALGO's price is within range, $10 is used to purchase tokens.\
After 5 days or 5 successful executions, the order completes automatically.

### 3. Security

Security is a top priority at Tinyman. Both Limit Orders and Recurring Orders are built on secure, transparent smart contracts.

* All contracts are internally reviewed and tested
* The contracts are open source
* The contracts are upgradable with user consent only
* Isolated smart contracts: each user has their own contract account, holding only the associated funds — no pooled risks
* Users retain full control over their assets at all times
* Transactions and states are fully on-chain and auditable
* All orders are executed atomically, ensuring there can be no loss of funds to partial execution
* Recurring Orders use the existing Tinyman Swap Router to ensure trades are made at the market price.&#x20;
* The contracts ensure Recurring Order executions are not at risk of sandwich attacks

### 4. Early Access for TINY Governors

Tinyman prioritizes community governance. TINY Governors — users who lock TINY in governance — will get early access to both Trigger Orders and Recurring Orders.

#### Eligibility

* Locking at least 2,000 TINY Power is required for early access

#### Additional Governance Benefits

* Weekly TINY rewards for participation
* Voting rights on farming rewards and protocol upgrades
* Early access to future feature rollouts
* Boosted staking: stake ALGO in the Stakepool, restake tALGO as a Governor, and earn additional TINY rewards on top of your ALGO staking returns

### 5. Additional Considerations&#x20;



* Trigger Orders & Recurring Orders are executed on a best effort basis. Off-chain components are required for triggering execution and despite redundancy these may fail to execute.
* Trigger Orders might not execute even when the trigger price is reached. This can be due to a number of factors including the trigger price falling again within a short timespan, the price impact of the order and the volume of orders.
* Note this is not an orderbook system. The orders are executed on the Tinyman AMM where the price moves independently of the trigger orders.
* Smaller order amounts have higher probability of successful execution than larger ones.
