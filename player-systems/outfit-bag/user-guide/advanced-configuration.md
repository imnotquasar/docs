# Advanced Configuration

Customize the appearance and item settings of outfit bags to better match your server’s theme or roleplay needs.

***

## Custom Bag Models

{% hint style="success" %}
💡 Use only one model at a time. Replace the value with the desired prop.
{% endhint %}

Choose from various prop models to change how the default bags appear in the world.

```lua
Config.BagModel = 'prop_cs_heist_bag_02'      -- Heist bag
Config.BagModel = 'prop_money_bag_01'         -- Money bag
Config.BagModel = 'prop_plastic_bag_04'       -- Plastic bag
Config.BagModel = 'prop_rub_binbag_01'        -- Bin bag
Config.BagModel = 'prop_cs_shopping_bag'      -- Shopping bag
```

***

## Custom Item Names

{% hint style="warning" %}
Make sure your inventory system defines the item with this exact name. Otherwise, the bag won't function.
{% endhint %}

Rename the outfit bag item to match your server’s naming conventions:

```lua
Config.ItemName = 'clothing_bag' -- Custom item name
```
