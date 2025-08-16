# Vending machines

In this section we present the vending machines, where you can enjoy a complete system by categories. You can create categories by entering the prop model, the name of the category and a title for the category. In this way, the elements you want are added for each category of vending machines. You can do this configuration in vending.lua.

{% hint style="success" %}
The system does not include floating text or any external visual indicators. Simply open your inventory while standing in front of a vending machine, and you're ready to interact with it.
{% endhint %}

***

## Generic Vending Machines code <a href="#generic-vending-machines-code" id="generic-vending-machines-code"></a>

Here we will leave a brief code as an example of using vending machines, which we can edit as we wish, editing does not require much effort.

```lua
Config.VendingMachines = {
    ['drinks'] = {
        ['Label'] = 'Drinks',
        ['Items'] = {
            [1] = {
                ['name'] = 'kurkakola',
                ['price'] = 4,
                ['amount'] = 50,
                ['info'] = {},
                ['type'] = 'item',
                ['slot'] = 1,
            },
            [2] = {
                ['name'] = 'water_bottle',
                ['price'] = 4,
                ['amount'] = 50,
                ['info'] = {},
                ['type'] = 'item',
                ['slot'] = 2,
            },
        }
    },
    ['candy'] = {
        ['Label'] = 'Candy',
        ['Items'] = {
            [1] = {
                ['name'] = 'chocolate',
                ['price'] = 4,
                ['amount'] = 50,
                ['info'] = {},
                ['type'] = 'item',
                ['slot'] = 1,
            },
        }
    },
    ['coffee'] = {
        ['Label'] = 'Coffee',
        ['Items'] = {
            [1] = {
                ['name'] = 'coffee',
                ['price'] = 4,
                ['amount'] = 50,
                ['info'] = {},
                ['type'] = 'item',
                ['slot'] = 1,
            },
        }
    },
    ['water'] = {
        ['Label'] = 'Water',
        ['Items'] = {
            [1] = {
                ['name'] = 'water_bottle',
                ['price'] = 4,
                ['amount'] = 50,
                ['info'] = {},
                ['type'] = 'item',
                ['slot'] = 1,
            },
        }
    },
}

Config.Vendings = {
    [1] = {
        ['Model'] = 'prop_vend_coffe_01', -- Model name of prop
        ['Category'] = 'coffee', -- Category from list above
        ['Label'] = 'Coffee', -- Name of vending
    },
    [2] = {
        ['Model'] = 'prop_vend_water_01',
        ['Category'] = 'water',
        ['Label'] = 'Water Dispenser',
    },
    [3] = {
        ['Model'] = 'prop_watercooler',
        ['Category'] = 'water',
        ['Label'] = 'Water Dispenser',
    },
    [4] = {
        ['Model'] = 'prop_watercooler_Dark',
        ['Category'] = 'water',
        ['Label'] = 'Water Dispenser',
    },
    [5] = {
        ['Model'] = 'prop_vend_snak_01',
        ['Category'] = 'candy',
        ['Label'] = 'Candy Vending',
    },
    [6] = {
        ['Model'] = 'prop_vend_snak_01_tu',
        ['Category'] = 'candy',
        ['Label'] = 'Candy Vending',
    },
    [7] = {
        ['Model'] = 'prop_vend_fridge01',
        ['Category'] = 'drinks',
        ['Label'] = 'Drinks Vending',
    },
    [8] = {
        ['Model'] = 'prop_vend_soda_01',
        ['Category'] = 'drinks',
        ['Label'] = 'Drinks Vending',
    },
    [9] = {
        ['Model'] = 'prop_vend_soda_02',
        ['Category'] = 'drinks',
        ['Label'] = 'Drinks Vending',
    },
}
```
