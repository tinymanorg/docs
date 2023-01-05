# Removing Liquidity

Liquidity providers can remove funds from the pool with an Asset Transfer of pool tokens and an Application Call.&#x20;

Amounts of each asset are sent to the user by the pool using two inner transactions. The amount of each asset received is proportional to the pool tokens returned and dependent on the current ratio of the pool. See [Formula III.A](../../formulae.md#a.-multiple-asset-out).

## **Removing liquidity as a single asset**

The protocol supports removing liquidity as a single asset from pools by combining removing liquidity with an internal swap calculation. The entirety of one side of the liquidity will be swapped into the other asset. A swap fee is charged on this amount and deducted from the output.

See [Formula III.B](../../formulae.md#b.-single-asset-out).

When using this convenience method the user must be aware of the loss of value due to both price impact and fees of the implicit swap. The user can pre-calculate the expected output accounting for these and provide the min\_output parameter to ensure the amount of output matches their expectations. This can protect the user from sudden price changes between the time of signing and executing the transaction.
