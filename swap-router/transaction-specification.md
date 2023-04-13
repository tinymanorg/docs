# Transaction Specification

### Asset Opt-in **Transactions**

**1. AppCall:** \
Sender: user\_address\
Index: router\_app\_id\
OnComplete: NoOp\
App Args: \[“asset\_opt\_in”]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id, ….., asset\_n\_id]\
Fee: min\_fee \* (1 + number of assets)

### **Swap Transactions**

**1. AssetTransfer/Pay (Input):**

Sender: user\_address\
Receiver: pool\_address\
Index: asset\_1\_id or asset\_2\_id\
Amount: input\_amount

**2. AppCall:**

**a. Mode: Fixed Input**

Sender: user\_address\
Index: router\_app\_id\
OnComplete: NoOp\
App Args: \[“swap”, “fixed-input”, min\_output\_amount]\
Foreign Assets: \[asset\_in\_id, asset\_intermediary\_id, asset\_out\_id]\
Accounts: \[pool\_1\_address, pool\_2\_address]\
Foreign Apps: \[amm\_app\_id]\
Fee: (8 \* min\_fee)

**b. Mode: Fixed Output**

Sender: user\_address\
Index: router\_app\_id On\
Complete: NoOp\
App Args: \[“swap”, “fixed-output”, output\_amount]\
Foreign Assets: \[asset\_in\_id, asset\_intermediary\_id, asset\_out\_id]\
Accounts: \[pool\_1\_address, pool\_2\_address]\
Foreign Apps: \[amm\_app\_id]\
Fee: (9 \* min\_fee)
