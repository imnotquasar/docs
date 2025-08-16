# No-signal system

The **Smartphone PRO** includes an advanced signal system, similar to the lite version, which restricts access to certain applications when the player is in a no-signal area.

***

## Configuration Example

You can create no-signal zones by using **ox\_lib** zones. The configuration is straightforward and highly customizable. Use **Config.ZoneDebug** during setup to visualize and fine-tune the zones.

```lua
Config.Mountains = {
    {
        coords = vec3(1849.0, 362.0, 113.0),
        size = vec3(1081.0, 1994.0, 2023.0),
        rotation = 0.0,
        name = 'Mount Chiliad 1',
    },
    {
        coords = vec3(1954.219727, -1600.285767, 380.278320),
        size = vec3(581.0, 1394.0, 2023.0),
        rotation = 0.0,
        name = 'Mount Chiliad 2',
    },
    -- Add more zones as needed
}
```

***

## Usage

When a player enters one of these configured zones, their phone's signal will drop, and access to specific applications will be restricted. This adds realism and enhances gameplay in remote areas.

Feel free to add or modify zones to match your server's needs.
