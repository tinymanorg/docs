# Swapping

Swaps are made with an Asset Transfer transaction together with an Application Call.

An amount of the other asset is sent to the user by the pool using an inner transaction.

The type of swap may be either fixed-input or fixed-output. If the type is fixed-output an extra inner transaction is sent to return any change from the input amount to the user (see below). A fixed-output swap has a higher transaction fee because it requires one extra inner transaction.

A swap fee is charged on all swaps. The fee is set per pool as basis points. This fee is deducted from the input amount before applying the swap formula to calculate the output.

The formulae for fixed-input and fixed-output swaps are described in [Formula IV.A & IV.B](../formulae.md#iv.-swapping) respectively.

## **Slippage Tolerance**

Swaps have slippage tolerance to allow for changes to the exchange rate between the time the swap was prepared and the swap was executed. For a fixed-input swap, a minimum output amount is included in the Application Call arguments. If the calculated output amount is less than this amount the swap will fail.

For a fixed-output swap, the slippage tolerance is included in the input amount and the exact output amount is specified in the arguments. If the calculated input amount required to achieve the target output amount is less than the provided input amount the swap fails. If it is greater then the change is returned to the user by an inner transaction.

[Transaction Details for swap](../v2-integration/protocol-methods/swap.md)
