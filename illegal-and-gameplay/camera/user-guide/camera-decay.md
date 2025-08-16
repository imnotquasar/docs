# Camera Decay

The camera system includes an optional durability feature that allows the item to degrade with use, adding realism and limiting the number of photos a camera can take before it breaks. This system uses metadata durability, which might not be available in all inventory systems. Currently, it is fully compatible with **qb-inventory** and **qs-inventory**, but if you use a different inventory, you should test this feature to ensure compatibility.

If your server supports metadata durability, you can configure this system using the following options:

{% stepper %}
{% step %}
### Config.DecayToUse

Enables the durability feature. Set it to `true` to activate the decay mechanic.
{% endstep %}

{% step %}
### Config.DecayToUseRate

Determines how much durability is consumed per use. For example, if the item starts with 100 durability and you set the rate to 1, the camera will last for 100 photos.
{% endstep %}
{% endstepper %}

```lua
Config.DecayToUse = true -- Only for qs-inventory or qb-inventory, read above!
Config.DecayToUseRate = 1 -- Decay level due to use, the item has 100 durability, therefore 1 = 100 shots
```

This configuration ensures the camera behaves realistically by introducing limited usage, which can enhance gameplay dynamics and resource management.
