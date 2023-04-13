# Swap

### **Transactions**

**1. AssetTransfer/Pay (Input):**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_1\_id or asset\_2\_id\
Amount: input\_amount

**2. AppCall:**

**a. Mode: Fixed Input**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“swap”,  “fixed-input”, min\_output\_amount]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
Accounts: \[pool\_address]\
Fee: (2 \* min\_fee)

**b. Mode: Fixed Output**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“swap”, “fixed-output”, output\_amount]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
Accounts: \[pool\_address]\
Fee: (3 \* min\_fee)

### **Side Effects**

#### **Local State Changes**

1. asset\_1\_reserves
2. asset\_2\_reserves
3. asset\_1\_protocol\_fees
4. asset\_2\_protocol\_fees
5. asset\_1\_cumulative\_price
6. asset\_2\_cumulative\_price
7. cumulative\_price\_update\_timestamp

#### **Logs**

1. input\_asset\_id
2. input\_amount
3. swap\_amount
4. change
5. output\_asset\_id
6. output\_amount
7. poolers\_fee\_amount
8. protocol\_fee\_amount
9. total\_fee\_amount

#### **Inner Transactions**

**1. AssetTransfer/Pay (Change):**\
_**Change is possible, if the swap mode is fixed-output.**_\
_**This transaction is issued, If there is a change.**_

Sender: pool\_address\
Receiver: user\_address\
Index: input\_asset\_id\
Amount: (See formula [IV.B](../../formulae.md#b.-fixed-output))

**2. AssetTransfer/Pay (Output)**

Sender: pool\_address\
Receiver: user\_address\
Index: output\_asset\_id\
Amount: (See formula [IV](../../formulae.md#iv.-swapping))
