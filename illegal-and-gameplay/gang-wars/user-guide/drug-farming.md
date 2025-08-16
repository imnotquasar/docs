# Drug Farming

Set here the drug, the object, the accessory or even the amount it gives you. if you own the zone or not, don't add more as it won't work and you might break the resource.

***

## Basic collection configuration <a href="#basic-collection-configuration" id="basic-collection-configuration"></a>

This is the collection configuration which is extremely simple.

```lua
Config.Items = { -- These are the items, prop and quantity that you can farm
    weed = {
        itemname = 'cannabis',
        prop = 'prop_weed_01',
        amount = 1,
        masteramount = 2, -- If your gang dominates the area, you will get more
    },

    cocaine = {
        itemname = 'cocaine',
        prop = 'prop_plant_cane_02b',
        amount = 1,
        masteramount = 2, -- If your gang dominates the area, you will get more
    },

    meth = {
        itemname = 'meth',
        prop = 'prop_barrel_exp_01a',
        amount = 1,
        masteramount = 2, -- If your gang dominates the area, you will get more
    },
}
```
