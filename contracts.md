# Contracts

Source code on Github: [https://github.com/tinymanorg/tinyman-contracts-v1](https://github.com/tinymanorg/tinyman-contracts-v1)

Audit Report by [Runtime Verification](http://runtimeverification.com): [https://github.com/runtimeverification/publications/blob/main/reports/smart-contracts/Tinyman.pdf](https://github.com/runtimeverification/publications/blob/main/reports/smart-contracts/Tinyman.pdf)

### Overview

The Tinyman contracts consist of a single stateful smart contract (the **Validator App**) and a template for a stateless smart contract for each Pool, the **Pool LogicSig**. The Validator app is created/deployed to the network by the Tinyman team. The Pool contract accounts are created from the Pool LogicSig template by the first Pooler who wishes to provide liquidity. Pool contract account addresses are discovered or verified by Swappers/Poolers using the Pool LogicSig template to generate a specific Pool LogicSig and retrieving the address.

#### Validator App <a href="#docs-internal-guid-b18fd459-7fff-aa47-087b-2bcfdededbc5" id="docs-internal-guid-b18fd459-7fff-aa47-087b-2bcfdededbc5"></a>

* Stateful smart contract
* Created by Tinyman core team
* Fully immutable
  * No updates allowed
  * No deletion allowed
* No global state
* Local state in Pool, Pooler, Swapper accounts (16 ints, 0 bytes)
* Contains validation and state manipulation logic for all operations

#### Pool Logic Signature Template

* A stateless smart contract template
* Template variables for asset 1 id, asset 2 id, and Validator App id
* Pool contract account address retrieved by hashing the completed template
* Contains logic to ensure only transactions part of expected transaction groups are signed
* Delegates most logic responsibility to the Validator app by ensuring the transaction group contains a call to the Validator App with appropriate arguments

### Version 1.1 (Release Candidate)

Source Code: [https://github.com/tinymanorg/tinyman-contracts-v1/tree/dc9ab40c58b85c15d58f63a1507e18be76720dbb](https://github.com/tinymanorg/tinyman-contracts-v1/tree/dc9ab40c58b85c15d58f63a1507e18be76720dbb)

Mainnet Validator App ID: Not yet deployed

Testnet Validator App ID: [62368684](https://testnet.algoexplorer.io/application/62368684)

### Version 1.0

Source Code: [https://github.com/tinymanorg/tinyman-contracts-v1/tree/d1090f16d755b3898d2b8e03a2efa86133c30346](https://github.com/tinymanorg/tinyman-contracts-v1/tree/d1090f16d755b3898d2b8e03a2efa86133c30346)

Mainnet Validator App ID: [350338509](https://algoexplorer.io/application/350338509)

Testnet Validator App ID: [21580889](https://testnet.algoexplorer.io/application/21580889)



