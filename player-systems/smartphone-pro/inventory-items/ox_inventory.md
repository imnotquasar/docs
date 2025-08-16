# ox\_inventory

{% hint style="warning" %}
Before placing items, please remove items with the same name as ox\_inventory by default.
{% endhint %}

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
["cryptostick"] = {
    label = "Crypto Stick",
    weight = 50,
    stack = false,
},

["phone_dongle"] = {
    label = "Phone Dongle",
    weight = 50,
    stack = false,
},

["powerbank"] = {
    label = "Power Bank",
    weight = 50,
    stack = false,
},

['phone'] = {
    label = 'Classic Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},

['black_phone'] = {
    label = 'Black Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},

['yellow_phone'] = {
    label = 'Yellow Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},

['red_phone'] = {
    label = 'Red Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},

['green_phone'] = {
    label = 'Green Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},

['white_phone'] = {
    label = 'White Phone',
    weight = 150,
    stack = false,
    consume = 0,
    client = {
        export = "qs-smartphone-pro.UsePhoneItem",
        add = function(total)
            TriggerServerEvent('phone:itemAdd')
        end,

        remove = function(total)
            TriggerServerEvent('phone:itemDelete')
        end
    }
},
```
