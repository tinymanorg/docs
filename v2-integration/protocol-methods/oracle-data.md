# Oracle Data

The protocol computes and stores some data which can be consumed by external contracts to create TWAP price oracles for pools.  The oracle related data of the pool is updated with any operation which may change the price. It is updated at most once in a block. The first operation of the pool in that block updates the oracle data before any changes are made to the pool ratio.

Pools have 3 oracle related fields in their local state:

1. asset\_1\_cumulative\_price (bytes)
2. asset\_2\_cumulative\_price (bytes)
3. cumulative\_price\_update\_timestamp (uint)

Cumulative price fields are scaled by 2^64 to provide more precision. In the bootstrap operation \`asset\_1\_cumulative\_price\` and \`asset\_2\_cumulative\_price\` are set to zero and \`cumulative\_price\_update\_timestamp\` is set to the latest block timestamp.

time\_delta = (latest block timestamp) - (cumulative price update timestamp)

asset\_1\_cumulative\_price = asset\_1\_cumulative\_price + ((asset\_2\_reserves \* 2^64) \* time\_delta) / (asset\_1\_reserves)

asset\_2\_cumulative\_price =asset\_2\_cumulative\_price + ((asset\_1\_reserves \* 2^64) \* time\_delta) / (asset\_2\_reserves)

cumulative\_price\_update\_timestamp = latest block timestamp

The cumulative price fields accumulate uint128 values represented as bytes. Even if these values accumulate until the final possible block (max uint64 value) then the total cumulative price will never exceed a uint192 or 24 bytes. For this reason, these values do not overflow or wrap around.
