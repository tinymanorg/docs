# Flash Swap

Flash swap has similarities to swap and flash loan. It is designed for advanced users. They can create a custom transaction group, borrow assets from the pool with an application call and make a profit (arbitrage, collateral swap etc.), pay it back within the same transaction group and make another application call to verify the payment. If the payment amount is insufficient all transactions in the atomic group fail. It allows users to generate profit without risk and collateral.

Unlike the flash loan, users are free to pay back in both assets as long as the final pool invariant increases and covers the fee. This can allow for more efficient transactions in some scenarios compared to the Flash Loan.

In the regular swap, the user transfers input assets to the pool first and then receives the output assets. Flash swap allows users to change this order. They can receive the output assets first, and use these assets to make a profit, and transfer input assets to the pool. In this scenario, the applied fee is exactly the same as the swap and the fee is applied to input assets and collected in terms of input assets. If users receive 500 AssetA and send 1000 AssetB, fee amount will be 3 AssetB with default fee rate 0.3% (1000\*0.003=3).

Additionally, similar to flash loan, flash swap allows users to borrow a single asset or both assets of the pool. Unlike the flash loan, users are free to pay back in both assets as long as the final pool invariant increases and covers the fee. Fees are applied to all input assets. If the repayment is made as 1000 AssetA and 2000 AssetB, the fee is collected in both assets as 3 AssetA and 6 AssetB. If the repayment is made in a single asset such as 3000 AssetB, the fee is 9 AssetB.

With the first app call, users specify the amount of loans in terms of asset 1 and asset 2 and group index difference between first and second (verification) application calls. Loan amounts cannot exceed the pool reserves. Requested assets are transferred to the user using inner transactions.

The verification calls check the initial and final invariant. Repayments must be made between two app calls. The app checks the final balance to determine the paid amounts and doesn’t check a particular transfer so users can make multiple inner and outer transactions. Any extra payments are considered as donations to the pools.

The pool is locked between the two application calls and no operation (swap, add & remove liquidity etc.) is allowed. These operations can be used before or after the flash swap in the same transaction group however.
