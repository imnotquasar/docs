# How to add more shells

Quasar Drugs Creator supports adding additional shells to expand your property options. While the package includes basic k4mb1 shells, you can enhance your collection by acquiring new shells from the [K4MB1 Shells Store. ](https://www.k4mb1maps.com)Follow this guide to integrate new shells properly.

{% stepper %}
{% step %}
### Acquire Shells

Purchase or obtain shells from a trusted source like k4mb1.
{% endstep %}

{% step %}
### **Configure Shells**:

Use the `Config.Shells` table in the configuration file to define the properties, and storage settings of each shell.
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
    [1] = {
        model = 'shell_coke1',
        limits = {
            weed = 10,
            meth = 10,
            cocaine = 10,
            money = 10
        },
        stash = {
            maxweight = 1000000,
            slots = 5,
        }

    },
    [2] = {
        model = 'shell_weed',
        limits = {
            weed = 10,
            meth = 10,
            cocaine = 10,
            money = 10
        },
        stash = {
            maxweight = 1000000,
            slots = 5,
        }

    }
    -- Other shells
}
```
