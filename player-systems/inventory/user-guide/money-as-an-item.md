# Money as an item

{% hint style="success" %}
Remember that the use of this system is automatic and mandatory in esx, but the use of qbcore can be completely optional by following all the corresponding steps.
{% endhint %}

Quasar Inventory integrates an advanced money as item system in which you can use money in item format, the system varies depending on qbcore and esx, but here we will focus on the information for qbcore.

***

## How to use in qbcore <a href="#how-to-use-in-qbcore" id="how-to-use-in-qbcore"></a>

This optional system for qbcore can be enabled by running it from server/custom/framework/qb.lua. To do this we will use the configuration that we will see below:

```lua
UseCashAsItem = false -- Choose whether to use money as an item
CashItem = 'cash' -- Choose the money item, it only works if I enable the configurable above
```

In this configuration we will place whether or not we want to use this system and below the name of the item that will be the money, in this case it is cash. This item must be added in your qb-core/shared/items.lua.
