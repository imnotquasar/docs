# How is it used?

**Quasar Backrooms** is an immersive horror asset designed to surprise players by teleporting them to the Backrooms, a perilous dimension where they must escape a deadly entity. Players can either survive and escape or perish, in which case their body will automatically return to the location where they originally died.

***

## Automatic Fall to Backrooms <a href="#basic-configuration-of-blips-and-factions" id="basic-configuration-of-blips-and-factions"></a>

This feature triggers automatically upon a player's death, with a configurable chance for them to be sent to the Backrooms. You can adjust this probability or disable it entirely using the configuration:

```lua
Config.BackroomsToDead = {
    enable = true, -- Enables or disables Backrooms on death
    chance = 10,   -- Percentage chance to be sent to Backrooms on death
}
```

***

## Manual Fall to Backrooms

Administrators have the option to send players to the Backrooms manually using the `/sendbackrooms id` command. This will teleport the specified player to the Backrooms without any prior notification, allowing for custom gameplay or events.

<table><thead><tr><th width="269">Command</th><th>Description</th></tr></thead><tbody><tr><td>/sendbackrooms [id]</td><td>Command to train the player to go to backrooms.</td></tr></tbody></table>
