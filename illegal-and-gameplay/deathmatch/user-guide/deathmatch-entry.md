# Deathmatch entry

Quasar Deathmatch Creator offers flexible options for accessing deathmatch lobbies. By default, a physical spot on the map serves as the entry point, but you can disable it to allow players to open the Deathmatch menu via commands or events from anywhere on the map.

***

## Disabling the Map Spot

To remove the fixed location for Deathmatch access:

{% stepper %}
{% step %}
Open the configuration file
{% endstep %}

{% step %}
Set Config.SpotEnable to false

```lua
Config.SpotEnable = false
```
{% endstep %}
{% endstepper %}

This disables the static entry point on the map.

***

## Using Commands to Access the Menu

You can replace the static spot with a command to open the Deathmatch menu.&#x20;

Define the command as follows:

```lua
RegisterCommand("openDeathmatch", function()
    ExecuteCommand("dmopen")
end, false)
```

Players can now type /openDeathmatch to access the Deathmatch menu.
