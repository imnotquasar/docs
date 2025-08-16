# Selling items system

Just like we have stores in qs-shops, we also have a small item selling system in qs-inventory/config/selling.lua, which will allow us to do the reverse logic of a store and make buyers of items, this can be Useful for dealers or specific roles and works by simply dragging and dropping the item into said seller's store.

This system does not contain an external integration for other assets, but we can use it easily by following the steps that we will find in the same configuration.

***

## Basic use of crafting <a href="#basic-use-of-crafting" id="basic-use-of-crafting"></a>

The selling system has nothing complicated, you can edit it however you like using the following example as a guide.

```
Config.SellItems = {
    ['Seller item'] = {
        coords = vec3(2682.7588, 3284.8857, 55.2103),
        blip = {
            active = true,
            name = 'Seller',
            sprite = 89,
            color = 1,
            scale = 0.5,
            account = 'money' -- Account associated with the seller's blip
        },
        items = {
            {
                name = 'sandwich',
                price = 3,
                amount = 1,
                info = {},
                type = 'item',
                slot = 1
            },
            {
                name = 'tosti',
                price = 2,
                amount = 1,
                info = {},
                type = 'item',
                slot = 2
            },
        }
    },
    ['24/7'] = {
        coords = vec3(2679.9326, 3276.6897, 54.4058),
        blip = {
            active = true,
            name = 'Seller',
            sprite = 89,
            color = 1,
            scale = 0.5,
            account = 'money' -- Account associated with the seller's blip
        },
        items = {
            {
                name = 'tosti',
                price = 1,
                amount = 1,
                info = {},
                type = 'item',
                slot = 1
            },
        }
    }
}
```
