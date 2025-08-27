---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# How to create new drugs

Adding new drugs to the Quasar Drugs Creator system is simple and fully customizable. Follow these steps to set it up:

***

## **Initial Setup in `config/config.lua`**

In the `config/config.lua` file, add a new entry to `Config.CollectItems` for the new drug. For example, to add **Heroine**:

```lua
['heroine'] = {
    prop = 'prop_sink_06',         -- Prop used for the drug collection zone
    name = 'Heroine',              -- Display name of the drug
    item = 'heroine',              -- Item name (must match the item in your database)
    time = 4000,                   -- Time required for the collection process (in ms)
    quantityMin = 1,               -- Minimum amount players will collect
    quantityMax = 5,               -- Maximum amount players will collect
    requiredCops = false,          -- Whether police presence is required
    requiredCopsQuantity = 0,      -- Minimum number of police required online
    collect_label = 'Collecting Heroine...' -- Progress bar label
}
```

***

## **Define Drug Animations in `Config.DrugAnimations`**

Next, add the new drug to `Config.DrugAnimations`. This defines the animations used during drug processing and packaging. For example:

```lua
['heroine'] = {
    package = {
        dict = 'mp_player_intdrink',
        anim = 'loop_bottle',
        progressBarLabel = 'Packaging Heroine...',
        progressBarTime = 5000,
        prop = { -- Optional, if you want to include a model
            model = `prop_ld_flow_bottle`,
            pos = vec3(0.03, 0.03, 0.02),
            rot = vec3(0.0, 0.0, -1.5)
        }
    },
    process = {
        dict = 'mp_player_intdrink',
        anim = 'loop_bottle',
        progressBarLabel = 'Processing Heroine...',
        progressBarTime = 5000,
        prop = {
            model = `prop_ld_flow_bottle`,
            pos = vec3(0.03, 0.03, 0.02),
            rot = vec3(0.0, 0.0, -1.5)
        }
    }
}
```

***

## **Add Processing Objects in `config/furniture.lua`**

To assign objects for processing and packaging the new drug, add entries to `Config.DynamicFurnitures`. For example, for **Heroine**:

```lua
-- Heroine Processing Table
['prop_sink_06'] = {
    drugType = 'heroine',           -- Drug type identifier
    fn = processDrug('heroine', 'process'), -- Function to process the drug
    offset = {                      -- Optional text offset
        x = 0.0,
        y = 0.0,
        z = 0.0,
    }
},
```

***

## **Add the Drug to Your Inventory Database**

{% hint style="warning" %}
If you use an inventory other than esx\_inventory, adapt it to your inventory.
{% endhint %}

Finally, ensure the new drug is added to your inventory system. For example, in your SQL database:

```sql
INSERT INTO `items` (`name`, `label`, `weight`) VALUES
    ('heroine', 'Heroine', 10);
```

***

## **Testing and Verification**

{% stepper %}
{% step %}
#### Restart your server to load the new configuration.
{% endstep %}

{% step %}
#### Test collecting, processing, and packaging the new drug to ensure everything works as expected.
{% endstep %}

{% step %}
#### Make any adjustments to timers, quantities, or animations based on feedback or server needs.
{% endstep %}
{% endstepper %}
