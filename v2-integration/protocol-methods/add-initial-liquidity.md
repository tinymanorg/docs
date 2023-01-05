# Add Initial Liquidity

### **Transactions**

**1. AssetTransfer:**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_1\_id\
Amount: asset\_1\_amount

**2. AssetTransfer/Pay:**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_2\_id\
Amount: asset\_2\_amount

**3. AppCall:**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“add\_initial\_liquidity”]\
Foreign Assets: \[pool\_token\_asset\_id]\
Accounts: \[pool\_address]\
Fee: (2 \* min\_fee)

### **Side Effects**

#### **Local State Changes**

1. asset\_1\_reserves
2. asset\_2\_reserves
3. issued\_pool\_tokens

#### **Inner Transactions**

**1. AssetTransfer:**

Sender: pool\_address\
Receiver: user\_address\
Index: pool\_token\_asset\_id\
Amount: (See formula [II.A](../../formulae.md#a.-adding-initial-liquidity) for pool token calculation)
