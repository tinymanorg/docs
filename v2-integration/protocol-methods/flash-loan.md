# Flash Loan

### **Transactions**

**1. AppCall:**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“flash\_loan”, index\_diff, asset\_1\_amount, asset\_2\_amount]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
Accounts: \[pool\_address]\
Fee: (3 \* min\_fee)

**2. AppCall** _(Group Index: index of flash loan call + index diff specified in the arguments):_

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“verifiy\_flash\_loan”, index\_diff]\
Foreign Assets: \[]\
Accounts: \[pool\_address]\
Fee: min\_fee

### **Side Effects**

1\. Flash Loan

#### **Local State Changes**

1. asset\_1\_cumulative\_price
2. asset\_2\_cumulative\_price
3. cumulative\_price\_update\_timestamp

**Inner Transactions**

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

2\. Verify Flash Loan

#### **Local State Changes**

1. asset\_1\_reserves
2. asset\_2\_reserves
3. asset\_1\_protocol\_fees
4. asset\_2\_protocol\_fees

#### **Logs**

1. asset\_1\_output\_amount
2. asset\_1\_input\_amount
3. asset\_1\_donation\_amount
4. asset\_1\_poolers\_fee\_amount
5. asset\_1\_protocol\_fee\_amount
6. asset\_1\_total\_fee\_amount
7. asset\_2\_output\_amount
8. asset\_2\_input\_amount
9. asset\_2\_donation\_amount
10. asset\_2\_poolers\_fee\_amount
11. asset\_2\_protocol\_fee\_amount
12. asset\_2\_total\_fee\_amount
