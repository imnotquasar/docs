# Starting Biohazard

The Biohazard event can be controlled in two different ways: **manual execution** through a command or **automatic scheduling** using the configuration file.

***

## Manual Start and Stop <a href="#basic-configuration-of-blips-and-factions" id="basic-configuration-of-blips-and-factions"></a>

Administrators can launch or stop the event at any time using the `/biohazard` command. To set a specific duration, simply type `/biohazard [time]` where **\[time]** is the number of seconds the event should last. For example:

* `/biohazard 200` → starts the event and runs it for 200 seconds.
* `/biohazard stop` → immediately ends the ongoing event.

This manual option gives staff full control over when and how the zombie outbreak occurs, allowing them to run it during live events, community activities, or special roleplay sessions.

***

## Automatic Start

If you prefer the event to trigger on its own, you can enable the automatic system in the configuration file:

```lua
Config.AutoStart = {
    Enabled        = true,   -- true = event auto-starts every X hours (randomized)
    MinHours       = 2,      -- Minimum hours between auto-starts
    MaxHours       = 5,      -- Maximum hours between auto-starts
    AnnounceInChat = true    -- true = announce in chat when an auto-start triggers
}
```

With this setup, the Biohazard event will automatically begin at random intervals between **2 and 5 hours**, creating unexpected outbreaks that keep players alert. When enabled, a message can also appear in the chat to warn everyone that the apocalypse is starting.

This dual system gives you flexibility: either run Biohazard manually when you want to create a unique event, or let the server handle it automatically to surprise players at random times.
