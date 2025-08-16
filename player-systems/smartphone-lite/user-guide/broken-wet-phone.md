# Broken wet phone

This feature is exclusive to Smartphones and is not available on the PRO Smartphone, as it is water-resistant and doesn't require it. When phones fall into water, they will become wet and break, replacing your phone item with a **wet\_phone**. This can be repaired either by using the **phone\_module** item or by visiting a Telephone Technician on the map.

{% stepper %}
{% step %}
### **Enable the wet system**

To enable the wet system, go to **config.lua** and look for **Config.WetPhone**.
{% endstep %}

{% step %}
### **When does the phone break?**

The phone will break when it falls into the sea, turning into an unusable wet phone.
{% endstep %}

{% step %}
### **Repair using a module**

You can repair the phone using a repair module, as mentioned below, without losing previous data.
{% endstep %}

{% step %}
### **Repair using an NPC**

The NPC from the previous step can also repair the phone without losing previous data.
{% endstep %}
{% endstepper %}

***

## **Basic wet phone system configuration**

The configuration is straightforward and includes the following options:

```lua
Config.WetPhone = false -- Phones will break when in water and be replaced with the item "wet_" prefix.
Config.RepairWetPhone = 'phone_module' -- This item can repair a wet phone.
Config.RepairWetPhoneNpc = true -- Allow repairing wet phones with the NPC Telephone Technician.
Config.RepairWetPhoneNpcPrice = 100 -- Price to repair a wet phone at the Technician.
Config.RepairWetPhoneNpcAccount = 'bank' -- Account used to pay the technician for repairs.
```

This simple system ensures a realistic experience while keeping flexibility for customization.
