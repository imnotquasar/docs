# Phone balance system

The **Phone Balance** feature in **Smartphone PRO** introduces a dynamic system for managing phone credit, enhancing realism. This system allows players to make calls only when their balance is positive and offers both daily and temporary balance options.

***

## Configuration Overview

{% stepper %}
{% step %}
### **Daily Balance**

&#x20;Credits are valid throughout the day.
{% endstep %}

{% step %}
### **Temporary Balance**

Credits are valid until spent.
{% endstep %}
{% endstepper %}

By default, the system is disabled. To enable it, modify **Config.EnableRecipe** in **config.lua**.

```lua
Config.EnableRecipe = false
Config.BuyRecipe = {
    coords = {
        vec3(324.93, -229.56, 54.22)
    },
    prices = {
        daily = 100000, -- Daily balance price
        moment = 1000,  -- Temporary balance price
    },
    blip = {
        sprite = 52,
        color = 2,
        scale = 0.8,
        name = 'Recipe Shop',
    }
}
```

***

## Checking Your Balance

Use the **/recipe** command to view your current balance and active plan. A notification will display the relevant information. This system adds depth and strategy to phone usage, encouraging players to manage their balance effectively.
