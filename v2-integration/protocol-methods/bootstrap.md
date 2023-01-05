# Bootstrap

### **Transactions**

**Pay:**

Sender: any\_address\
Receiver: pool\_address\
Amount:\
Pool minimum balance ([Formula I](../../formulae.md#i.-pool-minimum-balance))\
\+ Transaction fee of the app call\
\+ 100000 (min transaction fee for asset creation)

**AppCall:**

Sender: pool\_address (Logic Sig)\
Index: tinyman\_amm\_v2\_app\_id\
OnComplete: OptIn\
App Args: \[“bootstrap”]\
Foreign Assets: \[asset\_1\_id, asset\_2\_id]\
RekeyTo: tinyman\_amm\_v2\_app\_address\
Fee: (7 \* min\_fee) (Note: 6 \* min\_fee if asset 2 is Algo)

### **Side Effects**

#### **Local State Changes**

1. pool\_token\_asset\_id
2. asset\_1\_id
3. asset\_2\_id
4. total\_fee\_share
5. protocol\_fee\_ratio
6. asset\_1\_reserves
7. asset\_2\_reserves
8. issued\_pool\_tokens
9. asset\_1\_protocol\_fees
10. asset\_2\_protocol\_fees
11. lock
12. asset\_1\_cumulative\_price
13. asset\_2\_cumulative\_price
14. cumulative\_price\_update\_timestamp

#### **Inner Transactions**

**1. Pay:**

Sender: pool\_address\
Receiver: tinyman\_amm\_v2\_app\_address\
Amount: 100\_000\
Fee: 0

**2. AssetConfig:**

Sender: tinyman\_amm\_v2\_app\_address\
UnitName: “TMPOOL2”\
Name: “TinymanPool2.0 {asset\_1\_unit\_name}-{asset\_2\_unit\_name}”\
MetadataHash: “{asset\_1\_id}{asset\_2\_id}{trailing zeros}”\
uint64 (8 bytes) + uint64 (8 bytes) + zeros (16 bytes)\
Total: 18446744073709551615\
Reserve: pool\_address\
Decimals: 6\
URL: “[https://tinyman.org](https://tinyman.org)”\
Fee: 0

**3. AssetTransfer (Opt-In):**

Sender: pool\_address\
Receiver: pool\_address\
Index: asset\_1\_id\
Amount: 0

**4. AssetTransfer (Opt-In) (If Asset 2 is not Algo):**

Sender: pool\_address\
Receiver: pool\_address\
Index: asset\_2\_id\
Amount: 0

**5. AssetTransfer (Opt-In):**

Sender: pool\_address\
Receiver: pool\_address\
Index: created\_asset\_id\
Amount: 0

**6. AssetTransfer:**

Sender: tinyman\_amm\_v2\_app\_address\
Receiver: pool\_address\
Index: created\_asset\_id\
Amount: 18446744073709551615
