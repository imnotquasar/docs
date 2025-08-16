# Shop integration

The package that you have obtained from your keymaster includes both qs-inventory and qs-shops, the latter is an exclusive stores addon for qs-inventory. Here we can create stores with different dependencies on licenses or items and even with customizable jobs and degrees.

{% hint style="success" %}
Follow the thousands of examples within qs-shops/config/config.lua to fully understand the system. There you will find examples and general guides.
{% endhint %}

***

## Basic use of shops <a href="#basic-use-of-shops" id="basic-use-of-shops"></a>

The simple use is through the qs-shops asset, which has multiple stores. We can also use other stores as long as they do not search for items in your SQL. If this is the case, we will have to ask the creator for certain modifications.

{% hint style="info" %}
If you were using Quasar Inventory, we recommend using qs-shops or qb-shops to run the stores. If you use a third party one, we cannot take care of such situation.
{% endhint %}

***

## Integration of shops in other assets <a href="#integration-of-shops-in-other-assets" id="integration-of-shops-in-other-assets"></a>

You can also make use of the integration of stores in other assets in a simple way, we will leave an example using command of its basic use, then you yourself can easily integrate it as portable stores or static stores using loops on the client side.

```lua
RegisterCommand('openshop', function()
    local shop = 'shop'
    local Items = {
        label = 'Simple Shop',
        items = {
            {
                name = "water_bottle",
                amount = 99,
                price = 15,
                slot = 1
            },
            {
                name = "tosti",
                amount = 99,
                price = 25,
                slot = 2
            },
        },
    }
    TriggerServerEvent("inventory:server:OpenInventory", "shop", "Itemshop_" .. shop, Items)
end)
```
