# Additional Notes

## **Donations**

Any assets that are in the pool accounts but not part of the reserves, protocol fees or minimum Algo balance are claimable to the fee\_collector address.

Algorand Participation Rewards that accumulate in accounts holding Algo are considered donations to the pool and do not contribute to the pool reserves in AMM V2 (unlike V1). As of [2022/05/14 the Participation Rewards program is finished](https://algorand.foundation/faq#participation-rewards-) and no further rewards are planned to be distributed by this mechanism. In the event that this mechanism is re-enabled in the future the pool accounts would accumulate rewards that would be claimable by the fee\_collector address. It would be up to the protocols managers (development team or DAO) to decide how those rewards should be used.

## **Algo Pools**

The AMM V2 protocol supports ASA-Algo pools just like V1. All references to ‘Assets’ in this document equally apply to Algo. The transaction details differ slightly whenever Algo is involved as Payment transactions are used instead of Asset Transfer.

## **Transaction Fees**

All transaction fees must be paid by the sender of any of the outer transactions of an operation. The inner transaction fees cannot be paid by the pool account and app account.

## **Users**

This document refers to ‘Users’ as the senders of assets and transactions to the pool and receivers of assets from the pool. The protocol does not place any restriction on the type of account that initiates a pool operation and therefore supports operations made by application accounts in the same way as regular accounts. Additionally there is no requirement that the sender of all transactions in an operation group is the same account.

The receiver of assets (Pool Tokens, swapped assets, removed assets, change, etc) is always the sender of the Application Call.

## **Transaction Groups & Composability**

Each operation requires multiple transactions that must be part of the same atomic group. The exact indices of the transactions within the group or the size of the group is not specified by the protocol however so it is possible to create groups containing additional transactions before or after a swap for example. However relative indexing is used so the relative location of transactions within the group is specified and must be adhered to.

Operation transaction groups may also be created as inner transactions from within another Application. The only exception to this is the Bootstrap operation for creating pools, which requires a Smart Signature that cannot be used from an inner transaction.

## **Pool Discovery**

Clients can discover the existence of pools in either of two ways;

1. Every pool account is opted into the Tinyman App. Any account opted into this app is a valid pool. A list of pool accounts can therefore be retrieved from an Algorand Indexer or other block follower. The [local state](../v2-integration/state-data.md#local-state-pool) of these accounts gives the details of the pool.
2. The pool account address can be computed from the LogicSig template.
