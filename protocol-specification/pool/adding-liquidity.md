# Adding Liquidity

Funds are added to the pool with Asset Transfer transactions together with an Application Call. Pool tokens are sent to the user by the pool using an inner transaction. There are two methods for adding liquidity.

## **Adding Initial Liquidity**

If the pool has no liquidity then the first user to add liquidity is free to set the ratio between the two assets. If the pool has any liquidity this transaction fails and the user should use the Adding Subsequent Liquidity method. The formula to determine the number of pool tokens for initial liquidity is [Formula II.A](../../formulae.md#a.-adding-initial-liquidity).

[Transaction Details for add\_initial\_liquidity](../../v2-integration/protocol-methods/add-initial-liquidity.md)

## **Adding Subsequent Liquidity**

The formula to determine the number of pool tokens for subsequent liquidity is [Formula II.B](../../formulae.md#b.-adding-subsequent-liquidity).

The protocol supports adding liquidity in a flexible way so that the user does not have to provide amounts of assets at exactly the current pool ratio. Instead, it supports a continuum between liquidity at exactly the current ratio and all liquidity in a single asset. This is achieved by internal implicit swaps where necessary. A swap fee is charged on the amount that must be swapped. The value of this fee is reduced from the pool tokens output.

If the user does provide liquidity at exactly the current ratio then there will be no swap fee and pool tokens will be output for the entirety of the liquidity provided.

A special case of providing liquidity in a flexible way is providing liquidity in only one single asset. In this case the user does not need to transfer a zero amount but can instead omit the transfer transaction entirely.

When providing liquidity at a ratio different from the current pool ratio the user must be aware of the loss of value due to both price impact and fees of the implicit swap. The user can pre-calculate the expected value of pool tokens accounting for these and provide the min\_output parameter to ensure the amount of pool tokens output matches their expectations. This can protect the user from sudden price changes between the time of signing and executing the transaction.

### **Adding liquidity with two assets**

When adding liquidity with two assets two transfer transactions are required in addition to the application call transaction. The 2nd application arg must be the byte string “flexible” in this case.

### **Adding liquidity with a single asset**

When adding liquidity with one asset one transfer transaction is required in addition to the application call transaction. The 2nd application arg must be the byte string “single” in this case.

[Transaction Details for add\_liquidity](../../v2-integration/protocol-methods/add-subsequent-liquidity.md)
