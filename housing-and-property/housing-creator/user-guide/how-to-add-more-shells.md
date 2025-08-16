# How to add more shells

Quasar Housing supports adding additional shells to expand your property options. While the package includes basic k4mb1 shells, you can enhance your collection by acquiring new shells from the [K4MB1 Shells Store. ](https://www.k4mb1maps.com)Follow this guide to integrate new shells properly.

{% stepper %}
{% step %}
### Acquire Shells

Purchase or obtain shells from a trusted source like k4mb1.
{% endstep %}

{% step %}
### **Configure Shells**:

Use the `Config.Shells` table in the configuration file to define the properties, images, and storage settings of each shell.
{% endstep %}

{% step %}
### Images for Realtors

Ensure you include relevant preview images to enhance the realtor UI (for future DLC)
{% endstep %}
{% endstepper %}

***

## Example Configuration

Here’s how to configure new shells in `Config.Shells`:

```lua
Config.Shells = {
    [1] = { -- Tier 1
        model = 'standardmotel_shell', -- Shell model
        stash = {                     -- Storage configuration
            maxweight = 1000000,      -- Max weight the stash can hold
            slots = 5,                -- Number of stash slots
        },
        imgs = {                      -- Images for realtor previews
            {
                url = 'https://cdn.discordapp.com/attachments/1101313033684394084/1101712181017460736/motel.webp',
                label = 'Motel',
            },
        }
    },
    [2] = { -- Tier 2
        model = 'modernhotel_shell', -- Shell model
        stash = {                    -- Storage configuration
            maxweight = 1000000,     -- Max weight the stash can hold
            slots = 5,               -- Number of stash slots
        },
        imgs = {                     -- Images for realtor previews
            {
                url = 'https://cdn.discordapp.com/attachments/1101313033684394084/1101712459691208704/angle_1.webp',
                label = 'Angle 1',
            },
            {
                url = 'https://cdn.discordapp.com/attachments/1101313033684394084/1101712460110643210/angle_2.webp',
                label = 'Angle 2',
            },
        }
    },
    
    -- Other shells
}
```
