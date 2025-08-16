# Room Key Sharing

This section explains how room key sharing works, allowing players to grant access to their motel rooms to others under specific conditions. The system is flexible, with customizable settings to suit different server requirements.

***

## How Room Sharing Works <a href="#how-room-sharing-works" id="how-room-sharing-works"></a>

{% stepper %}
{% step %}
### **Inventory Sharing Limitations**

When sharing a room key, only inventories without metadata can be accessed by others. If the inventory includes metadata, the owner must share a separate "meta key" for access.
{% endstep %}

{% step %}
### **Sharing the Key with Nearby Players**

Players can share their room key with nearby players using the command `"shareMotelKey"`, which can be configured to a different command if desired.
{% endstep %}

{% step %}
### **Configurable Sharing Limits**

The maximum number of people a key can be shared with is configurable. This setting can be adjusted in the `config.lua` file under `qs-motels-creator > shared`, with the default maximum set to 3 people:

```lua
roomSharingMaximum = 3, -- Maximum room sharing
```
{% endstep %}
{% endstepper %}
