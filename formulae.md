# Formulae

## I. Pool Minimum Balance

Ref: [Minimum balance requirement for a smart contract](https://developer.algorand.org/docs/get-details/dapps/smart-contracts/apps/#minimum-balance-requirement-for-a-smart-contract)

Local state uint count: 12

Local state byte slice count: 2

### A. ASA-ASA Pool

100000 (Accounts on Algorand require a minimum balance of 100,000 micro Algo)\
\+ 100000 ASA 1 (Asset Optin)\
\+ 100000 ASA 2 (Asset Optin)\
\+ 100000 Pool Token (Asset Optin)\
\+ 542000 App Optin (100000 + (25000+3500)\*12 + (25000+25000)\*2)\
\= 942000 micro Algo

### B. ASA-ALGO Pool

100000 (Accounts on Algorand require a minimum balance of 100,000 micro Algo)\
\+ 100000 ASA 1 (Asset Optin)\
\+ 100,000 ASA 2 (Asset Optin)\
\+ 100000 Pool Token (Asset Optin)\
\+ 542000 App Optin (100000 + (25000+3500)\*12 + (25000+25000)\*2)\
\= 842000 micro Algo

## II. Adding Liquidity

### **A. Adding Initial Liquidity**

Issued Pool Tokens = floor(sqrt(Asset1 Amount \* Asset2 Amount))\
Locked Pool Tokens= 1000\
Pool Token Output = Issued Pool Tokens - Locked Pool Tokens

### **B. Adding Subsequent Liquidity**

The same formula applies to single and flexible modes.

Old K = Asset1 Reserves \* Asset2 Reserves\
New K = (Asset1 Reserves + Asset1 Amount) \* (Asset2 Reserves + Asset2 Amount)\
R = sqrt(Old K) / Issued Pool Tokens\
New Issued Pool Tokens = sqrt(New K) / R\
New Issued Pool Tokens = sqrt(New K) / ( sqrt(Old K) / Issued Pool Tokens)\
New Issued Pool Tokens = sqrt((New K \* Issued Pool Tokens\* Issued Pool Tokens) / Old K)

Pool Tokens Out = New Issued Pool Tokens - Old Issued Pool Tokens\
New Asset1 Reserves = Old Asset1 Reserves + Asset1 Amount\
New Asset2 Reserves = Old Asset1 Reserves + Asset2 Amount

Calculated Asset1 Amount = floor((Pool Tokens Out \* New Asset1 Reserves) / New Issued Pool Tokens)\
Calculated Asset2 Amount =floor((Pool Tokens Out \*New  Asset2 Reserves) / New Issued Pool Tokens)\
Asset1 Swap Amount = Asset1 Amount - Calculated Asset1 Amount\
Asset2 Swap Amount = Asset2 Amount - Calculated Asset2 Amount\
Swap Amount = Max(Asset1 Swap Amount, Asset2 Swap Amount)

Total Fee Amount = (Swap Amount \* Total Fee Share) / (10000 - Total Fee Share)\
Protocol Fee Amount = Total Fee Amount / Protocol Fee Ratio\
Poolers Fee Amount = Total Fee Amount - Protocol Fee Amount

Asset1 Swap Amount > Asset2 Swap Amount:\
Fee As Pool Tokens = (Total Fee Amount \* New Issued Pool Tokens) / (New Asset1 Reserves \* 2)\
New Asset1 Reserves = New Asset1 Reserves - Protocol Fee Amount\
Pool Tokens Out = Pool Tokens Out - Fee As Pool Tokens

Asset2 Swap Amount > Asset1 Swap Amount:\
Fee As Pool Tokens = (Total Fee Amount \* New Issued Pool Tokens) / (New Asset2 Reserves \* 2)\
New Asset2 Reserves = New Asset2 Reserves - Protocol Fee Amount\
Pool Tokens Out = Pool Tokens Out - Fee As Pool Tokens

## III. Removing Liquidity

### **A. Multiple Asset Out**

#### a. Remove all circulating pool tokens

Issued Pool Tokens == Locked Pool Tokens + Removed Pool Tokens\
Asset1 Output = Asset1 Reserves\
Asset2 Output = Asset2 Reserves

#### b. Otherwise

Issued Pool Tokens > Locked Pool Tokens + Removed Pool Tokens\
Asset1 Output= floor(Removed Pool Token Amount \* Asset1 Reserves / Issued Pool Tokens)\
Asset2 Output= floor(Removed Pool Token Amount \* Asset2 Reserves / Issued Pool Tokens)

### **B. Single Asset Out**

Calculate the Asset1 Output and Asset2 Output as multiple assets out and convert an asset to desired output by doing an internal swap (fixed-input swap).

#### a. Asset 1 Out

Input Amount = Asset2 Output\
Swap Output = FixedInputSwap(Input Amount)\
Asset1 Output=Asset1 Output + Swap Output\
Asset2 Output=0

#### b. Asset 2 Out

Input Amount = Asset1 Output\
Swap Output = FixedInputSwap(Input Amount)\
Asset2 Output=Asset2 Output + Swap Output\
Asset1 Output=0

## IV. Swapping

### **A. Fixed Input**&#x20;

Total Fee = floor((Input Amount \* Total Fee Share) / 10000)\
Protocol Fee = floor(Total Fee / Protocol Fee Ratio)\
Poolers Fee = Total Fee - Protocol Fee\
Swap Amount = Input Amount - Total Fee\
K = Input Supply \* Output Supply\
Swap Output = Output Supply - (floor(K / (Input Supply + Swap Amount)) + 1)

### **B. Fixed Output**

Swap Amount = (floor(K / (Output Supply - Output Amount)) + 1) - Input Supply\
Input Amount = floor((Swap Amount \* 10000) / (10000 - Total Fee Share))\
Total Fee = Input Amount - Swap Amount\
Protocol Fee = floor(Total Fee / Protocol Fee Ratio)\
Poolers Fee = Total Fee - Protocol Fee\
Change = Input Transfer Amount - Input Amount

## V. Flash Loan

Applies to both assets.

Total Fee = floor((Loan Amount \* Total Fee Share) / 10000)\
Protocol Fee = floor(Total Fee / Protocol Fee Ratio)\
Poolers Fee = Total Fee - Protocol Fee\
Expected Repayment Amount = Loan Amount + Total Fee\
Donation Amount = Repayment Transfer Amount - Expected Repayment Amount

## VI. Flash Swap

Applies to both assets.

Input Amount= Transfer Amount (Final Balance - Initial Balance)

**Note:** The rest is the same with fixed input swap.

Total Fee = floor((Input Amount \* Total Fee Share) / 10000)\
Protocol Fee = floor(Total Fee / Protocol Fee Ratio)\
Poolers Fee = Total Fee - Protocol Fee
