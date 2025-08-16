# Process System

After collecting raw materials, the next step is processing them into finished products ready for sale. This system is fully configurable in `config/processes.lua`, allowing for detailed customization of processing spots and their associated behaviors.

{% stepper %}
{% step %}
### Complex Configuration

Modifying this configuration is not recommended unless necessary, as improper changes can disrupt animations or other critical functionalities. Ensure you have a trusted developer if adjustments are needed.
{% endstep %}

{% step %}
### Processing Locations

Each processing spot has an `inside` zone (where processing happens) and an `outside` zone (entry/exit). You can adjust these to control the number of players who can process simultaneously.
{% endstep %}

{% step %}
### Customizable Settings

Adjust entry/exit zones, processing times, required and reward items, animations, and more. Proceed cautiously to avoid breaking the system.
{% endstep %}
{% endstepper %}

***

## Example Configuration: Meth Processing

Below is a simplified example of the meth processing spot configuration:

```lua
Config.Progress = {
    ['Meth'] = {
        -- Inside the processing area
        inside = {
            coords = vec3(996.81, -3200.64, -36.39) -- Interior location
        },
        -- Outside the processing area
        outside = {
            coords = vec3(1561.46, -1693.57, 89.21) -- Exterior entry/exit
        },
        -- Cooking Meth
        ['cook_meth'] = {
            mainText = '[E] - Process meth',       -- Interaction prompt
            progText = 'Processing methamphetamine...', -- Progress bar text
            requireRate = 5,                      -- Quantity of required item
            requireItem = 'chemicals',            -- Required input item
            notifyname = 'Chemicals',             -- Notify name for item
            rewardItem = 'meth',                  -- Output item
            rewardRate = 30,                      -- Quantity of output item
            locations = {                         -- Processing locations
                [1] = {
                    location = vector3(1005.80, -3200.40, -38.90),
                    offset = vector3(-4.88, -1.95, 0.0),
                    rotation = vector3(0.0, 0.0, 0.0),
                    active = true
                }
            },
            time = 73000,                         -- Processing time (ms)
            act = 'Meth',
            scene = 1,
            active = true
        },
        -- Packaging Meth
        ['package_meth'] = {
            mainText = '[E] - Package meth',
            progText = 'Packing methamphetamine...',
            requireRate = 10,
            requireItem = 'meth',
            notifyname = 'Methamphetamine',
            rewardItem = 'meth_packaged',
            rewardRate = 10,
            locations = {
                [1] = {
                    location = vector3(1011.80, -3194.90, -38.99),
                    offset = vector3(4.48, 1.7, 1.0),
                    rotation = vector3(0.0, 0.0, 0.0),
                    active = true
                },
                [2] = {
                    location = vector3(1014.19, -3195.02, -38.99),
                    offset = vector3(4.48, 1.7, 1.0),
                    rotation = vector3(0.0, 0.0, 0.0),
                    active = true
                },
                [3] = {
                    location = vector3(1016.49, -3194.9, -38.99),
                    offset = vector3(4.48, 1.7, 1.0),
                    rotation = vector3(0.0, 0.0, 0.0),
                    active = true
                }
            },
            time = 50000,
            act = 'Meth',
            scene = 2,
            active = true
        }
    }
}
```

***

## How It Works

This system adds a dynamic layer of interactivity and immersion, making the drug production process feel realistic and engaging.

{% stepper %}
{% step %}
### Entry and Exit

Players enter the processing area via the designated `outside` zone and interact with processing stations in the `inside` zone.
{% endstep %}

{% step %}
### Processing Steps

Each process requires specific items (`requireItem`) and rewards players with finished products (`rewardItem`).
{% endstep %}

{% step %}
### Customizable Locations

Define multiple spots for simultaneous processing by multiple players. Each station is configured individually with coordinates and properties.
{% endstep %}

{% step %}
### Timers and Notifications

Use timers to simulate processing and display messages to keep players informed.
{% endstep %}
{% endstepper %}
