# Add Subsequent Liquidity

## A. **Flexible**

### **Transactions**

**1. AssetTransfer:**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_1\_id\
Amount: asset\_1\_amount

**2. AssetTransfer/Pay:**

Sender: user\_address;\
Receiver: pool\_address\
Index: asset\_2\_id\
Amount: asset\_2\_amount

**3. AppCall:**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp\
App Args: \[“add\_liquidity”, “flexible”, min\_output]\
Foreign Assets: \[pool\_token\_asset\_id]\
Accounts: \[pool\_address]\
Fee: (3 \* min\_fee)

### **Side Effects**

#### **Local State Changes**

1. asset\_1\_reserves
2. asset\_2\_reserves
3. issued\_pool\_tokens
4. asset\_1\_protocol\_fees
5. asset\_2\_protocol\_fees
6. asset\_1\_cumulative\_price
7. asset\_2\_cumulative\_price
8. cumulative\_price\_update\_timestamp

#### **Logs**

1. input\_asset\_id
2. output\_asset\_id
3. swap\_amount
4. poolers\_fee\_amount
5. protocol\_fee\_amount
6. total\_fee\_amount

#### **Inner Transactions**

**1. App Call (to increase op code budget):**

It is for increasing the opcode (computational) [budget](https://developer.algorand.org/docs/get-details/dapps/avm/teal/?from\_query=opcode%20budged#dynamic-operational-cost-of-teal-opcodes) which is required for internal swap calculations.

**2. AssetTransfer:**

Sender: pool\_address\
Receiver: user\_address\
Index: pool\_token\_asset\_id\
Amount: (See formula [II.B](../../formulae.md#b.-adding-subsequent-liquidity) for pool token calculation)

## B. Single Asset

### **Transactions**

**1. AssetTransfer/Pay:**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_id\
Amount: asset\_amount

**2.AppCall:**

Sender: user\_address\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: NoOp

### **Side Effects**

#### **Local State Changes**

1. asset\_1\_reserves
2. asset\_2\_reserves
3. issued\_pool\_tokens
4. asset\_1\_protocol\_fees
5. asset\_2\_protocol\_fees
6. asset\_1\_cumulative\_price
7. asset\_2\_cumulative\_price
8. cumulative\_price\_update\_timestamp

#### **Logs**

1. input\_asset\_id
2. output\_asset\_id
3. swap\_amount
4. poolers\_fee\_amount
5. protocol\_fee\_amount
6. total\_fee\_amount

#### **Inner Transactions**

**1. App Call (to increase op code budget):**

It is for increasing the opcode (computational) [budget](https://developer.algorand.org/docs/get-details/dapps/avm/teal/?from\_query=opcode%20budged#dynamic-operational-cost-of-teal-opcodes) which is required for internal swap calculations.

**2. AssetTransfer:**

Sender: pool\_address\
Receiver: user\_address\
Index: pool\_token\_asset\_id\
Amount: (See formula [II.B](../../formulae.md#b.-adding-subsequent-liquidity) for pool token calculation)
