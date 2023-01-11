---
description: This section describes the transaction groups for each method of the protocol.
---

# Protocol Methods

Where more than one transaction is required they must appear in an atomic group. The exact indices within the group are not important unless specified. However, the relative positions of transactions for each method are important. The transaction order may not change and no other transactions may appear between the transactions of each method.

Where user\_address is specified the same address must be used for all instances within a method. any\_address can be any value.



{% content-ref url="bootstrap.md" %}
[bootstrap.md](bootstrap.md)
{% endcontent-ref %}

{% content-ref url="add-initial-liquidity.md" %}
[add-initial-liquidity.md](add-initial-liquidity.md)
{% endcontent-ref %}

{% content-ref url="add-subsequent-liquidity.md" %}
[add-subsequent-liquidity.md](add-subsequent-liquidity.md)
{% endcontent-ref %}

{% content-ref url="remove-liquidity.md" %}
[remove-liquidity.md](remove-liquidity.md)
{% endcontent-ref %}

{% content-ref url="swap.md" %}
[swap.md](swap.md)
{% endcontent-ref %}

{% content-ref url="flash-loan.md" %}
[flash-loan.md](flash-loan.md)
{% endcontent-ref %}

{% content-ref url="flash-swap.md" %}
[flash-swap.md](flash-swap.md)
{% endcontent-ref %}

{% content-ref url="../state-data.md" %}
[state-data.md](../state-data.md)
{% endcontent-ref %}

{% content-ref url="../oracle-data.md" %}
[oracle-data.md](../oracle-data.md)
{% endcontent-ref %}
