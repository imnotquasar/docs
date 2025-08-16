# Washing System

The laundering system allows players to clean black money obtained from drug sales. For **QBCore**, this system uses `markedbills` with the original metadata system, making it seamless and functional. Players must complete three stages—cutting, packaging, and washing—to convert black money into clean currency.

{% stepper %}
{% step %}
### Customizable Item Names

You can rename the markedbills system using Config.Markedbills in the file server/custom/framework/\*.lua.
{% endstep %}

{% step %}
### Entry and Exit Points

A hidden location on the map serves as the entry point for laundering. Players can move between defined interior and exterior spots for the process.
{% endstep %}

{% step %}
### Three-Step Process

* **Cut Money**: Converts black\_money into sorted\_money.
* **Package Money**: Turns sorted\_money into package\_money.
* **Wash Money**: Cleans package\_money into usable in-game cash.
{% endstep %}
{% endstepper %}

***

## Configuration Example

Below is an example setup for configuring the laundering system:

```lua
luaCopiarEditarConfig.CustomPorcentaje = false -- Set to false or a percentage (e.g., 25 for 25%)

Config.Laundry = {
    -- Entry configuration
    ['entry'] = {
        coord = vector3(887.38409, -953.7551, 39.213134), -- Exterior entry point
        intcoord = vector3(1138.0, -3198.96, -39.68), -- Interior entry point
        intheading = 11.64, -- Interior entry heading
        text = '[E] - Enter', -- Interaction text
    },

    -- Exit configuration
    ['exit'] = {
        intcoord = vector3(1138.0, -3198.96, -39.68), -- Interior exit point
        coord = vector3(887.38409, -953.7551, 39.213134), -- Exterior exit point
        heading = 46.85, -- Exterior exit heading
        text = '[E] - Exit', -- Interaction text
    },

    -- Cutting Zone
    ['cuttingZone'] = {
        coords = vector3(1122.24, -3197.88, -40.4), -- Cutting zone location
        heading = 179.46,
        text = '[E] - Cut money', -- Interaction text
        progText = 'Cutting stolen money...', -- Progress text
        count = 100, -- Amount of black money required
        requireItem = 'black_money', -- Input item
        rewardItem = 'sorted_money', -- Output item
    },

    -- Packaging Zone
    ['packageZone'] = {
        coord = vector3(1120.12, -3197.88, -39.92), -- Packaging zone location
        heading = 180.93,
        text = '[E] - Packaged money', -- Interaction text
        progText = 'Packaging stolen money...', -- Progress text
        requireItem = 'sorted_money', -- Input item
        rewardItem = 'package_money', -- Output item
    },

    -- Washing Zone
    ['washingZone'] = {
        coord = vector3(1122.32, -3194.6, -40.4), -- Washing zone location
        heading = 346.76,
        text = '[E] - Wash money', -- Interaction text
        progText = 'Washing stolen money...', -- Progress text
        requireItem = 'package_money', -- Input item
        rewardItem = 'money', -- Output item
    }
}
```

***

## How It Works

This system ensures an immersive and interactive money-laundering experience, adding depth and realism to the drug operations within your server.

{% stepper %}
{% step %}
### Enter the Laundering Location

Use the designated entry point to access the laundering area.
{% endstep %}

{% step %}
### Perform the Steps

Follow the sequential steps—cut, package, and wash money—to complete the laundering process.
{% endstep %}

{% step %}
### Exit the Location

Leave through the designated exit once the process is complete.
{% endstep %}
{% endstepper %}
