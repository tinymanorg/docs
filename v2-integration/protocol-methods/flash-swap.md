# Flash Swap

### **Transactions**

**1. AppCall:**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“flash\_swap”, index\_diff, asset\_1\_amount, asset\_2\_amount]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
Accounts: \[pool\_address]\
Fee: (3 \* min\_fee)

**2. AppCall** _(Group Index: index of flash swap call + index diff specified in the arguments):_

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“verifiy\_flash\_swap”, index\_diff]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
Accounts: \[pool\_address]\
Fee: min\_fee

#### **Side Effects**

1. Flash Swap

#### **Local State Changes**

1. lock
2. asset\_1\_cumulative\_price
3. asset\_2\_cumulative\_price
4. cumulative\_price\_update\_timestamp

**Logs**

To able to share data between app calls, these logs are added:

1. asset\_1\_balance\_after\_transfer
2. asset\_2\_balance\_after\_transfer

#### **Inner Transactions**

**1. AssetTransfer (If asset 1 amount is not 0):**

Sender: pool\_address\
Receiver: user\_address\
Index: asset\_1\_id\
Amount: asset\_1\_amount

**2. AssetTransfer/Pay (If asset 2 amount is not 0):**

Sender: pool\_address\
Receiver: user\_address\
Index: asset\_2\_id\
Amount: asset\_2\_amount

2\. Verify Flash Swap

**Local State Changes**

1. lock
2. asset\_1\_reserves
3. asset\_2\_reserves
4. asset\_1\_protocol\_fees
5. asset\_2\_protocol\_fees

**Logs**

1. asset\_1\_output\_amount
2. asset\_1\_input\_amount
3. asset\_1\_poolers\_fee\_amount
4. asset\_1\_protocol\_fee\_amount
5. asset\_1\_total\_fee\_amount
6. asset\_2\_output\_amount
7. asset\_2\_input\_amount
8. asset\_2\_poolers\_fee\_amount
9. asset\_2\_protocol\_fee\_amount
10. asset\_2\_total\_fee\_amount
