---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Compact Inventory

The **Compact Inventory** is a configuration that allows the inventory to appear on the **side of the screen**, giving full visibility of the environment and allowing **player movement** while using it — without losing any of the system’s original features.

This is ideal for immersive servers or players who prefer minimal UI distractions.

***

## How to Enable It

{% stepper %}
{% step %}
## Open your config.lua file.
{% endstep %}

{% step %}
## Look for the line:

```lua
Config.CompactInventory = false
```
{% endstep %}

{% step %}
## Set it to true:

```lua
Config.CompactInventory = true
```
{% endstep %}
{% endstepper %}

***

## Styling (Optional)

If you wish to customize the look of the compact inventory:

* Navigate to the `compact.css` file.
* Make any visual adjustments as needed.

> ⚠️ **Edit at your own risk.** Make sure you back up the file before making changes.
