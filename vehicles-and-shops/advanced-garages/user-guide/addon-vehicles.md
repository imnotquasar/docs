---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Addon Vehicles

Many addon vehicles include names in their `vehicles.meta` file that differ from their spawn names. This guide explains how to locate and resolve name discrepancies to ensure smooth integration with the Quasar Advanced Garages system.

***

## **Understanding Addon Vehicle Names**

Addon vehicles, often custom-branded cars, may display "NULL" as their name in the garage menu. This issue arises from mismatched metadata in the `vehicles.meta` file, specifically the `gameName` field. The garage system references this field to display vehicle names.

**Example Issue:**

* Spawn name: `golfgti7`
* Meta `gameName`: `Golf GTI`

If no configuration is provided, the system cannot match the two, resulting in a "NULL" display in the menu.

***

## **How to Identify the Vehicle Name**

{% stepper %}
{% step %}
### **Enable Debug Mode**

Use `Config.Debug = true` to view the vehicle's metadata name in the client console. This will help you identify the model name and resolve discrepancies.
{% endstep %}

{% step %}
### **Check `vehicles.meta`**

Open the `vehicles.meta` file for the specific car and locate the `gameName` value. This is the name the garage system needs for accurate display.
{% endstep %}
{% endstepper %}

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

***

## **How to Configure Addon Vehicles**

Add the correct name mapping to `Config.AddonVehiclesLabelList` in the `config.lua` file. Match the `gameName` value to a readable label.

**Example Configuration:**

```lua
Config.AddonVehiclesLabelList = {
    ['Golf GTI'] = 'Volkswagen Golf 8 GTI', -- gameName : Display Label
}
```

***

## **Why This Happens**

This issue stems from custom vehicle creators using inconsistent naming practices in their metadata files. Correcting this is a simple step in ensuring addon vehicles integrate seamlessly with the garage system.

By following these steps, you can resolve the "NULL" display issue and enjoy a polished experience for your players using addon vehicles.
