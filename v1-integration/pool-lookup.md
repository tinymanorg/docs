# Pool Lookup

Tinyman pools are discovered by generating a Pool LogicSig contract from the published template and computing the address associated with that LogicSig. The following variables must be replaced in the template to generate the LogicSig for a pool; Asset 1 ID, Asset 2 ID and Validator App ID.

See the Python SDK for the [reference implementation](https://github.com/tinymanorg/tinyman-py-sdk/blob/main/tinyman/v1/pools.py#L19) of this lookup.

{% hint style="danger" %}
All clients interacting with Tinyman pools MUST generate pool addresses in this way. It is not safe to assume any address is a Pool if it is not verified with this method.
{% endhint %}

