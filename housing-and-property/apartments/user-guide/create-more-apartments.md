# Create more Apartments

In **Quasar Apartments**, new apartments can be easily added by modifying the Apartments.Locations table. Each apartment includes its **name, price, tier, entry coordinates, and polyzone settings**. The **spawn coordinates** inside the apartment are **automatically generated** the first time a player enters.

***

## Steps to Add a New Apartment

{% stepper %}
{% step %}
### Open the Configuration File

Locate and open your **apartment configuration file** where Apartments.Locations is defined.
{% endstep %}

{% step %}
### Add a New Entry

Copy and paste an existing apartment structure, then modify the values:

```lua
['apartment6'] = { 
    name = 'apartment6', 
    label = 'Downtown Loft', -- Display name
    price = 6000, -- Moving price
    tier = 2, -- Apartment tier (affects shell model)
    coords = { 
        enter = vector4(350.15, -1002.42, 29.28, 180.0), -- Entry coordinates
    }, 
    polyzoneBoxData = { 
        heading = 180, 
        minZ = 28.5, 
        maxZ = 32.0, 
        debug = false, 
        length = 1, 
        width = 2, 
        distance = 2.0, 
        created = false 
    } 
}
```
{% endstep %}

{% step %}
### Define the Interior Model

* Each apartment **tier** corresponds to a **shell model** in `Config.Shells`.
* Modify the `tier` value to match a **valid shell model** from `Config.Shells`:

```lua
Config.Shells = {
    [1] = { model = 'shell_v16low', stash = { maxweight = 1000000, slots = 5 } },
    [2] = { model = 'shell_office1', stash = { maxweight = 1000000, slots = 5 } },
    [3] = { model = 'shell_v16mid', stash = { maxweight = 1000000, slots = 5 } },
}
```
{% endstep %}

{% step %}
### Save & Restart

Once the apartment is added, save the file and **restart your server**.
{% endstep %}
{% endstepper %}

### **Automatic Interior Spawn Generation**

* When a player **enters the apartment for the first time**, the **spawn coordinates inside will be automatically set**.
* No manual interior positioning is required.

With this setup, you can **expand your housing system effortlessly** and provide a diverse range of apartments for players.&#x20;
