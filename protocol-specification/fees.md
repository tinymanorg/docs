# Fees

Tinyman charges fees on swaps, loans and internal swap operations. A portion of this fee is allocated to the protocol (Tinyman) and the remainder is allocated to the liquidity providers by adding to the pool reserves.

The fee rate and the protocol fee fraction portion are configurable parameters on each pool. The total fee rate can be set in the range from 0.01% to 1% (1 to 100 basis points), the protocol fee fraction can be set as 1/n in the range from 1/3 to 1/10. The default fee rate is %0.3 and protocol fee fraction is 1/6 (0.05% of total input). These defaults are the same as the Tinyman V1.

Pools have a single fee setting and the same rate is applied to all swap, loan and internal swap operations.

The protocol fees accumulate in both assets. They can be claimed in full at any time by any user that issues an appropriate Application Call. The accumulated amounts of both assets are transferred by inner transactions to the fee collector. The fee collector is specified by a global state variable of the App (fee\_collector). The  fee\_collector can be set by the global fee\_manager address.

Fee parameters can be set by the global fee\_setter address. The fee\_setter address can be set by the global fee\_manager address. The fee\_manager address can be set by the current fee\_manager address.

## **Swap Fees**

Swap fees are collected from the input assets.

**Examples:**

**A. Fixed Input**

If the input amount is 5000A, fee is 5000\*fee rate AssetA. If the fee rate is 0.3%, total fee is 15 AssetA, pooler fee is 13 AssetA and protocol fee is 2 AssetA.

If the input amount is 20000A, fee is 20000A\*fee rate AssetA. If the fee rate is 0.3%, total fee is 60 AssetA and protocol fee is 10 AssetA.

\
**B. Fixed Output**

In this method, the extra amount added because of the slippage is returned back to the users with an inner transaction. The input amount is calculated by subtracting the extra amount from the transferred amount and the fee is applied to this amount.

If the transferred amount is 1005A, and extra amount is 5, the fee is applied to 1000 AssetA.



## **Flash Loan Fees**

The fee rate is the same with the swap fee rate of the pool. It is applied to the loan amounts. The repayment must be equal or greater than the total of loan amount and fee.

**Examples:**

**A. Loan single asset**

If the loan is 3000 AssetA, fee is 3000\*fee rate AssetA. It is 9 AssetA if the fee rate is 0.3%, so minimum repayment amount is 3009 AssetA.

**B. Loan multiple assets**

If the loan is 3000 AssetA and 5000 AssetB, fee is 3000\*fee rate AssetA and 5000\*fee rate AssetB. The minimum repayment amounts are 3009 AssetA and 5015 AssetB, if the fee rate is 0.3%.

## **Flash Swap Fees**

The fee calculation is the same as swap. The same swap fee rate is applied to input amounts.

**Examples:**

**A. Pay in single asset**

If the payment is 3000 AssetA, the fee is 3000\*fee rate AssetA.

**B. Pay in multiple assets**

If the payment is 1000 AssetA and 2000 AssetB, the fees are 1000\*fee rate AssetA and 2000\*fee rate AssetB.

## **Swap Router Fees**

The swap router doesn’t charge additional fees. Tinyman AMM V2 fee policy applies to swaps.

Using the swap router requires 3 more transactions than 2 swaps and 6 more transactions than a single swap. API is aware of this difference and makes suggestions accordingly. The total transaction fee is converted from Algo to input asset amount using the price information, calculated by pool reserves. However, if this conversion is impossible, the transaction fee isn’t included in the calculation.

All transaction fees must be paid by the sender of any of the outer transactions. The inner transaction fees are not paid by the swap router app account.
