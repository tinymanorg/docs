# Slippage & Excess

**Slippage** refers to the slip or movement in price between the time a transaction was prepared and the transaction was executed.&#x20;

When you sign a swap transaction you agree to receive an exact amount of one asset in exchange for an exact amount of the other. If the price slips your transaction would fail because the ratio of the input and output is no longer valid. Even if it slips by a miniscule amount your transaction would fail. To handle this situation the concept of **slippage tolerance** is used.

With **slippage tolerance** you agree to accept a slightly less amount (a slightly poorer price) in the _worst case_. The default is a tolerance of 0.5%. This swap is more likely to succeed because it has some tolerance included. You will immediately receive the exact amounts you sign for. However the contract calculates the exact amount you should receive, which is usually better than the worst case you agreed to, and stores the difference for you as **excess**.

**Excess** is simply an IOU (I owe you) from the Pool. The amount is stored in the Pool account rather than your account but you and only you can **redeem** it at any time to move it to your account. You can let the excess amounts accumulate over multiple swaps or redeem after each swap if you wish.

The same concepts of slippage and excess apply to **adding/removing liquidity** operations also.

### Examples

#### Swapping

Bob wishes to swap 100 USDC for Algo. He is quoted 50.00 Algo at a rate of 2.0. With 0.5% slippage tolerance he agrees to receive 49.75 Algo at minimum. The swap executes and he receives exactly 49.75 Algo. He is then informed that he has 0.24 Algo in _excess_ which he decides to _redeem_ later. The total received was 49.75 + 0.24 = 49.99. With a no slippage tolerance this swap would have failed but with 0.05% tolerance Bob was very satisfied.&#x20;

Alice wishes to swap 50 Algo for USDC. She is quoted 100.00 USDC at a rate of 0.5. With 0.5% slippage tolerance she agrees to receive 99.50 USDC at minimum. The swap executes and she receives exactly 99.50 USDC. She is then informed that he has 1.00 USDC in _excess._ The total received was 100.50 USDC because the price shifted to 2.01 just before her swap executed. Alice was delighted with this result as the amount received is even better than she expected when she first got her quote.

Carol wishes to swap 100 USDC for Algo. She is quoted 50.00 Algo at a rate of 2.0. With 0.5% slippage tolerance she agrees to receive 49.75 Algo at minimum. The swap fails to execute. A large swap before hers made the price jump to 2.1. If her swap was exectuted at this rate she would have received 47.61 Algo which she wouldn't have been happy with. Carol was glad her slippage tolerance was not too high. She waited a bit for the rate to return and did her swap again.&#x20;

#### Adding Liquidity

Dan wishes to add liquidity to the Algo-USDC pool. For adding 100 USDC and 50 Algo he is quoted 70 Pool Tokens to represent his share of the pool. With 0.5 slippage tolerance he agrees to receive 69.55 Pool Tokens at minimum. The mint operation executes and he receives exactly 69.65 Pool Tokens. He is then informed he as 0.30 Pool tokens in _excess._ The total received was 69.95 Pool Tokens due to a slight change in the pools liquidity. Dan chooses not to redeem the excess right now. He will still earn profits from swap fees proportional to his _total_ Pool Tokens, including the amount in excess. However, he will need to redeem the excess before being able to withdraw his entire liquidity share.

