---
description: Claim back 'change' due to slippage in Mint/Burn/Swap process.
---

# Redeem

### Transaction Group

0\. Pay - pay fees in Algo from PoolerSwapper to Pool

* fees to cover Tx 1,2
* Signed by Pooler

```
{
  "txn": {
   "type": "pay",
   "rcv": "{POOL_ADDRESS}",
   "snd": "{POOLER/SWAPPER_ADDRESS",
   "amt": 2000,
   "fee": 1000,
   ...
  },
  "sig": "{POOLER/SWAPPER_SIG}",
}
```

1. App Call - NoOp call to Validator App with args \['redeem'], with Pooler/Swapper account
   * Signed by Pool LogicSig

```
{
  "txn": {
    "type": "appl",
    "snd": "{POOL_ADDRESS}",
    "apid": {VALIDATOR_APP_ID},
    "apan": 0, // OnComplete: NoOp
    "apaa": ['cmVkZWVt'] // ['redeem']
    "apat": [{POOLER/SWAPPER_ADDRESS}],
    "fee": 1000,
    ...
  },
  "lsig": "{POOL_LOGICSIG}",
}
```

2\. (a) AssetTransfer - Transfer of asset from Pool to Pooler/Swapper

* If asset is an ASA
* Signed by Pool LogicSig

```
{
  "txn": {
    "type": "axfer",
    "arcv": "{POOLER/SWAPPER_ADDRESS}",
    "snd": "{POOL_ADDRESS}",
    "xaid": {ASSET_ID},
    "aamt": {ASSET_AMOUNT},
    "fee": 1000,
    ...
  },
  "lsig": "{POOL_LOGICSIG}",
}
```

2\. (b) Pay - Transfer of Algo from Pool to Pooler/Swapper

* If asset is Algo
* Signed by Pool LogicSig

```
{
  "txn": {
    "type": "pay",
    "rcv": "{POOLER/SWAPPER_ADDRESS}",
    "snd": "{POOL_ADDRESS"},
    "amt": {ASSET_AMOUNT},
    "fee": 1000,
    ...
  },
  "lsig": "{POOL_LOGICSIG}",
}
```

### Validator App State Changes

**Global State**

None

**Pool Account Local State**

* `o{LIQUIDITY_ASSET_ID}: {int}` // total outstanding unredeemed liquidity asset amount
* `o{ASSET1_ID}: {int}` // total outstanding unredeemed asset 1 amount
* `o{ASSET2_ID}: {int}` // total outstanding unredeemed asset 2 amount

**Pooler/Swapper Account Local State**

* `{POOL_ADDRESS}e{LIQUIDITY_ASSET_ID}: {int}` // excess liquidity asset amount available for redemption
* `{POOL_ADDRESS}e{ASSET1_ID}: {int}` // excess asset 1 amount available for redemption
* `{POOL_ADDRESS}e{ASSET2_ID}: {int}` // excess asset 2 amount available for redemption
