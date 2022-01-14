---
description: Transfer collected protocol fees to the CREATOR account.
---

# Redeem Protocol Fees

{% hint style="info" %}
Note: The CREATOR must opt-in to the liquidity assets separately before receiving them.
{% endhint %}

### Transaction Group:

0\. Pay - pay fees in Algo from User to Pool

* fees to cover Tx 1,2
* Signed by User

```
{
  "txn": {
    "type": "pay",
    "rcv": "{POOL_ADDRESS}",
    "snd": "{USER_ADDRESS",
    "amt": 2000,
    ...
  },
  "sig": "{USER_SIG}",
}
```

1. App Call - NoOp call to Validator App with args \['fees']

* Signed by Pool LogicSig

```
{
  "txn": {
    "type": "appl",
    "snd": "{POOL_ADDRESS}",
    "apid": {VALIDATOR_APP_ID},
    "apan": 0, // OnComplete: NoOp
    "apaa": ['ZmVlcw=='] // ['fees']
    ...
  },
  "lsig": "{POOL_LOGICSIG}",
}
```

2\. AssetTransfer - Transfer of liquidity asset from Pool to CREATOR account

* Signed by Pool LogicSig

```
{
  "txn": {
    "type": "axfer",
    "arcv": "{CREATOR_ADDRESS}",
    "snd": "{POOL_ADDRESS}",
    "xaid": {LIQUIDITY_ASSET_ID},
    "aamt": {ASSET_AMOUNT},
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
* `p: {int}` // unclaimed protocol fee liquidity asset amount

**Creator Local State**

None
