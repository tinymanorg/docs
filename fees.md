---
description: Current Tinyman and Algorand fees incurred for each function
---

# Fees

## Swapping

A fee of 0.3% is added to all swaps.&#x20;

* 5/6ths of this fee (0.25%) is paid to Poolers
* 1/6th of this fee (0.05%) is paid to the protocol (Tinyman Treasury)

**Fixed input swap:**\
Algorand transaction fees: 4 \* min fee = 0.004 Algo

**Fixed output swap:**\
Algorand transaction fees: 5 \* min fee = 0.005 Algo

## Adding & Removing Liquidity

There are no extra fees charged by Tinyman for Minting or Burning.

**Adding Initial liquidity:**\
****Algorand transaction fees: 4 \* min fee = 0.004 Algo

**Adding subsequent liquidity for flexible:**\
****Algorand transaction fees: 5 \* min fee = 0.005 Algo

**Adding subsequent liquidity for single asset:**\
****Algorand transaction fees: 4 \* min fee = 0.004 Algo

**Removing liquidity for both multiple assets and single asset:**\
****Algorand transaction fees: 4 \* min fee = 0.004 Algo

## Pool Creation (Bootstrap)

There are no extra fees charged by Tinyman for Pool Creation.

There are additional Algo costs to cover the minimum balance required for the Pool account:\
ASA-ASA Pool: 1.043 Algo\
ASA-Algo Pool: 0.943 Algo

Algorand transaction fees: \
ASA-ASA Pool: 7 \* min fee = 0.007 Algo\
ASA-Algo Pool: 6 \* min fee = 0.006 Algo

**Total costs for Pool Creation:**\
ASA-ASA Pool: 1.05 Algo\
ASA-Algo Pool: 0.949 Algo

## Flash Loan

A fee of 0.3% is added to flash loans.&#x20;

* 5/6ths of this fee (0.25%) is paid to Poolers
* 1/6th of this fee (0.05%) is paid to the protocol (Tinyman Treasury)

Algorand transaction fees: 4 \* min fee = 0.004 Algo

## Flash Swaps

A fee of 0.3% is added to flash loans.&#x20;

* 5/6ths of this fee (0.25%) is paid to Poolers
* 1/6th of this fee (0.05%) is paid to the protocol (Tinyman Treasury)

Algorand transaction fees: 4 \* min fee = 0.004 Algo

## Variable Fees

Tinyman V2 is introducing new governance functionality that will allow liquidity providers (LPs) to set the percentage of fees they want to collect for their pool up to a maximum of 5%. The current fee structure will remain unchanged until the governance feature is activated and put up for a vote. At that point, LPs will be able to propose changes to the fee structure through the governance process. Until then, the fee structure will continue as is.&#x20;
