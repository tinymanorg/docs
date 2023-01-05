# Flash Loan

Flash loan allows users to borrow single or multiple assets with no collateral with the condition of paying it back within the same transaction group. It allows advanced users to create a custom transaction group to generate a profit without an initial capital.

Flash loan requires two application calls. The first one is for requesting a loan from the pool and the second one is for verifying the repayment.

The repayments must be made in the same asset. The repayment amount should cover the loan amount and fee. The swap fee rate applies to loan amounts.

With the first app call users specify the amount of loans in terms of asset 1 and asset 2 and group index difference between first and second application calls. Loan amounts cannot exceed the pool reserves. Requested assets are transferred to the user using inner transactions.

Verification calls check the repayment amounts. The transaction fails if they don’t cover the loan amount and fee. Repayments should be placed just before the verification app call and the contract checks the transfer amounts. Any extra payments are considered donations to pools.

Flash loan transactions can appear anywhere within a transaction group and a single group may contain multiple flash loans.

Users can use the same pool freely between the two application calls and do a swap. Unlike Flash Swap (below) usage of the pool is not restricted.
