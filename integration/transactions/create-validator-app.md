---
description: Create/deploy the Validator App.
---

# Create Validator App

{% hint style="info" %}
This transaction is sent once to create the Tinyman Validator App. No user should ever send this.
{% endhint %}

### Transaction

1. App Call - Create Validator App
   * signed by Creator

```
{
  "txn": {
    "type": "appl",
    "snd": "{CREATOR_ADDRESS}",
    "apid": 0,
    "apan": 0, // OnComplete: NoOp
    "apaa": ['Y3JlYXRl'] // ['create']
    "apls": {"nui": 16}, // Local State Schema: num_uints=16
    "apap": {APPROVAL_PROGRAM_BYTES},
    "apsu": {CLEAR_STATE_PROGRAM_BYTES},
    ...
  },
}
```

### Validator App State Changes

**Global State**

None

**Creator Account Local State**

None
