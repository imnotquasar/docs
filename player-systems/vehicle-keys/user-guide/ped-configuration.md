# Ped Configuration

In `qs-vehiclekeys`, you can customize the NPCs used for key copying and plate sales. This includes modifying their models, locations, and rendering distance. These settings allow server owners to adapt the asset to fit their roleplay environments and enhance immersion.

***

## **Key Copying NPC**

Set the NPC that manages the key duplication process. Customize the character model and its location on the map:

{% stepper %}
{% step %}
### **Model**

The NPC model is defined by `Config.CopyKeysNpcName`.
{% endstep %}

{% step %}
### **Location**

Set the NPC's position using `Config.CopyKeysPedLocation` (coordinates and heading).
{% endstep %}

{% step %}
### **Render Distance**

Control how far away the NPCs will be visible to players by adjusting `Config.PedRenderDistance`.
{% endstep %}
{% endstepper %}

***

## **Plate Sale NPC**

Configure the NPC responsible for selling plate items. You can adjust the model and placement:

{% stepper %}
{% step %}
### **Model**

Use `Config.PlateNpcName` to specify the NPC model.
{% endstep %}

{% step %}
### **Location**

Define the NPC's placement with `Config.PlateNPCLocation`.
{% endstep %}

{% step %}
### **Render Distance**

Control how far away the NPCs will be visible to players by adjusting `Config.PedRenderDistance`.
{% endstep %}
{% endstepper %}

This configuration ensures that your NPCs are positioned and styled appropriately for your server's environment, providing a seamless experience for key and plate-related interactions.
