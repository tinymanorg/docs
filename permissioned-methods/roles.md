# Roles

The fee\_manager, fee\_setter and fee\_collector are distinct roles in the protocol. Each of these are mutable.&#x20;

## **Fee Collector**

The fee\_collector is expected to be a single signature account used by an off-chain system to actively manage the accumulated protocol fees and extras. There is a not insignificant chance that this account could become compromised so in order to protect future earnings of the protocol this account must be replaceable by a higher authority - the fee\_manager.

## **Fee Setter**

The fee\_setter is expected to initially be a multisig account but over time it may transition to a system account for an automated process or a contract account governed by voting. To facilitate these changes of use and to protect against compromised keys the fee\_setter is configurable only by the fee\_manager.

## **Fee Manager**

The fee\_manager is expected to be a multisig account initially, and potentially a contract account governed by voting in the future. It is assumed that this account is never compromised. The protocol requires that the role can be transferred between accounts.

The fee\_manager, fee\_setter and fee\_collector roles are all initialized to the creator address of the application. This is assumed to be a multisig.

These roles are global - they cannot be defined separately for different pools.

There are no other roles or management capabilities defined in the protocol. There is no capability to pause/lock/close/empty any pool and there is no capability to upgrade the application.\
