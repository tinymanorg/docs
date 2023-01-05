# Calculating Quotes

Calculating quotes for swaps and other operations requires knowledge of the current pool state including fee parameters, reserves, issued protocol tokens, etc. This information can be retrieved from the local state of the Tinyman app in the pool account. It is important to use fresh state data when calculating quotes as pool ratios and prices can change quickly.

## Swap

### **Fixed Input**

See [Formula IV.A](../../formulae.md#a.-fixed-input)

Fixed Input Swap from asset 1 to asset 2

total\_fee = (input\_amount \* state\["total\_fee\_share"]) / 10000\
swap\_amount = input\_amount - total\_fee\
k = state\["asset\_1\_reserves"] \* state\["asset\_2\_reserves"]\
swap\_output = state\["asset\_2\_reserves"] - (floor(k / (state\["asset\_1\_reserves"] + swap\_amount)) + 1)

Allowing for a slippage of 1%, min\_output\_amount should be set as swap\_output \* 0.99

### **Fixed Output**

See[ Formula IV.B](../../formulae.md#b.-fixed-output)

Fixed Output Swap from asset 1 to asset 2

k = state\["asset\_1\_reserves"] \* state\["asset\_2\_reserves"]\
swap\_amount = (floor(k / (state\["asset\_2\_reserves"] - output\_amount)) + 1) - state\["asset\_1\_reserves"]\
input\_amount = floor((swap\_amount \* 10000) / (10000 - state\["total\_fee\_share"]))

Allowing for a slippage of 1%, input\_amount should be set as input\_amount \* 1.01
