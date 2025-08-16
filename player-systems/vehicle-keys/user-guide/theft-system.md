# Theft System

The **Theft System** in `qs-vehiclekeys` enables immersive vehicle hotwiring and theft mechanics, allowing players to engage in mini-games to break into vehicles. The system is fully customizable, letting you control difficulty levels, timings, and even interactions with NPC vehicles.

***

## Hotwire Mini-Game

The theft mechanic uses a skill-based mini-game to simulate hotwiring. You can adjust the difficulty and parameters for more engaging gameplay:

{% stepper %}
{% step %}
### **Config.MiniGameHotWireStyle**

Choose between `'easy'` or `'hard'` mini-game styles.

* `'easy'`: A simple series of skill checks with low challenge.
* `'hard'`: A more advanced skill check with smaller areas and faster speeds for greater difficulty.
{% endstep %}

{% step %}
### **Config.TimeMin** and **Config.TimeMax**

Define the minimum and maximum time (in milliseconds) required to complete the hotwiring process.
{% endstep %}

{% step %}
### **Config.ChanceToHotwire**

Sets the success chance for the hotwire action (e.g., `99` for 99%).
{% endstep %}
{% endstepper %}

***

## NPC Vehicle Theft

The system supports stealing NPC-driven vehicles, adding realism and roleplay opportunities:

{% stepper %}
{% step %}
### **Config.StealVehiclesPeds**

Enable (`true`) or disable (`false`) NPC vehicle theft. Players can target NPC drivers to receive their keys.
{% endstep %}

{% step %}
### **Config.StealVehiclesPedsPolice**

Adjust the percentage chance that the NPC will call the police after being targeted.
{% endstep %}
{% endstepper %}

***

## Additional Options

{% stepper %}
{% step %}
### **Config.WhitelistVehicles**

Exclude specific vehicles from hotwiring by listing them (e.g., `'bmx'`).
{% endstep %}
{% endstepper %}

This system is ideal for adding depth to vehicle theft mechanics while maintaining control over gameplay balance. Use the configuration options to tailor the experience to your server's needs.
