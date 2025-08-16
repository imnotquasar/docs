# Presential Billing Payment

The **Presential Billing Payment** system introduces a physical, tax-free method for players to pay their invoices at designated locations. This alternative provides a realistic and engaging experience by requiring players to visit specific branches to settle their bills.

{% stepper %}
{% step %}
### **Tax-Free Payments**

Unlike virtual transfers, no transaction fee is applied when paying invoices at physical branches.
{% endstep %}

{% step %}
### **Configurable Branch Locations**

Add multiple payment points across the map with specific coordinates and labels.
{% endstep %}

{% step %}
### **Customizable Interaction**

Configure the interaction distance, marker appearance, and blip visibility.
{% endstep %}

{% step %}
### **Blip Support**

Display payment branch locations on the map using customizable blip settings.
{% endstep %}
{% endstepper %}

***

## **Configuration Example**

Below is the configurable section for presential billing payment found in `config.lua`:

```lua
Config.PresentialBillingPayment = {
    ['Enabled'] = true, -- Enable or disable the presential billing payment system
    ['Distance'] = 1.5, -- Interaction distance for payment points
    ['Blips'] = {
        enabled = true,      -- Enable or disable blips on the map
        sprite = 207,        -- Blip icon
        display = 4,         -- Display setting for the blip
        scale = 0.8,         -- Size of the blip
        colour = 2,          -- Blip color (green)
        shortRange = true,   -- Show only when nearby
    },
    ['Points'] = {          -- List of branch locations
        {
            label = 'Pay Invoice', -- Label displayed in the interaction
            coords = vector3(241.8698, 224.2415, 106.2868), -- Coordinates of the branch
            markerId = 21,        -- Marker ID for the interaction point
            distance = 3          -- Interaction distance for this point
        },
        {
            label = 'Pay Invoice',
            coords = vector3(246.7510, 222.9073, 106.2868),
            markerId = 21,
            distance = 3
        },
        {
            label = 'Pay Invoice',
            coords = vector3(-1270.0256, -3048.5208, 13.9807),
            markerId = 21,
            distance = 3
        }
    }
}
```

***

## **How It Works**

{% stepper %}
{% step %}
### **Tax-Free Payment**

* Players visit one of the configured payment branches to settle their invoices.
* Payments made at these locations are exempt from transaction fees.
{% endstep %}

{% step %}
### **Branch Locations**

* Define payment points using the `coords` property.
* Use the same `label` for multiple points to stack their blips on the map.
{% endstep %}

{% step %}
### **Blip Customization**

* Modify the `sprite`, `scale`, `colour`, and other properties to personalize the map markers for these branches.
{% endstep %}

{% step %}
### **Markers and Interaction**

* Set `markerId` and `distance` for a visual marker and interaction range.
* Adjust `Distance` globally for all interaction points.
{% endstep %}
{% endstepper %}
