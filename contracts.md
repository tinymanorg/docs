# Contracts

Source code on Github: [https://github.com/tinymanorg/tinyman-amm-contracts-v2](https://github.com/tinymanorg/tinyman-amm-contracts-v2)

Mainnet Validator App ID: [1002541853](https://algoexplorer.io/application/1002541853)

Testnet Validator App ID: [148607000](https://testnet.algoexplorer.io/application/148607000)

### Overview

The Tinyman V2 contracts consist of a single stateful smart contract (the **Validator App**) and a template for a stateless smart contract for each Pool, the **Pool LogicSig**. The Validator app is created/deployed to the network by the Tinyman team. The Pool contract accounts are created from the Pool LogicSig template by the first Pooler who wishes to provide liquidity. Pool contract account addresses are discovered or verified by Swappers/Poolers using the Pool LogicSig template to generate a specific Pool LogicSig and retrieving the address.

#### Validator App <a href="#docs-internal-guid-b18fd459-7fff-aa47-087b-2bcfdededbc5" id="docs-internal-guid-b18fd459-7fff-aa47-087b-2bcfdededbc5"></a>

* Stateful smart contract
* Created by Tinyman core team
* Fully immutable
  * No updates allowed
  * No deletion allowed
* Local state in Pool  accounts&#x20;
* Contains validation and state manipulation logic for all operations

#### Pool Logic Signature Template

* A stateless smart contract template
* Template variables for asset 1 id, asset 2 id, and Validator App id
* Pool contract account address retrieved by hashing the completed template
* ONLY used during pool creation (bootstrap) where it is rekeyed to the Validator App









