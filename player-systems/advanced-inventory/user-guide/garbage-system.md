---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Garbage system

Quasar Advanced Inventory includes a straightforward garbage collection system that you can configure and modify in **config/garbage.lua**. This system allows players to collect items from any garbage can in the city or deposit items into them, adding immersive functionality to your server.

***

## Editing Garbage Cans

You can customize the system by editing or adding more garbage can props in **config/garbage.lua**. Use props available in GTA V or from a trusted source to ensure compatibility.

{% stepper %}
{% step %}
### Go to garbage file

We will look for the file inside qs-**inventory**/config/garbage.lua, open it and look for the following configurables.
{% endstep %}

{% step %}
### **Config.GarbageObjects**

Add or modify the props that will act as garbage cans. These props define where players can interact with the garbage collection system.
{% endstep %}

{% step %}
### **Config.GarbageItemsForProp**

Specify the items that players can collect or deposit for each garbage can prop. This allows different garbage cans to hold unique items, making the system more dynamic.
{% endstep %}
{% endstepper %}

By using these configurations, you can create a detailed and interactive garbage collection system tailored to your server’s needs. Players can interact with the environment in new ways, enhancing realism and gameplay variety.
