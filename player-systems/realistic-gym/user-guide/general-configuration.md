# General Configuration

All configuration for **Quasar Realistic Gym** is handled in `shared/config.lua`. The script uses intelligent auto-detection to ensure fast, seamless integration across ESX, QBCore, QBox, or standalone setups.

***

## Basic Settings

These core options define how the gym system behaves:

```lua
Config.Debug = false -- Enable debug messages for troubleshooting
Config.Language = 'en' -- Set your preferred language
Config.MembershipPrice = 2500 -- Price players pay for gym membership
Config.StatsHUDKey = "F10" -- Keybind to open the stats HUD
Config.ExerciseUIPosition = "left" -- Position of exercise UI: "left" or "right"
```

***

## Target Detection

Automatically detects and configures your targeting system, or allows manual override:

```lua
Config.UseTarget = false -- Enable/disable targeting integration
Config.Target = checkDependencies(targets) or 'standalone'
```

Compatible with:

* `ox_target`
* `qb-target`
* `qs-textui`
* or no targeting system at all

***

## Stat Decay System

Customize the map marker for the Job Center:

```lua
Config.StatDecay = {
    enabled = true,         -- Enable or disable daily stat reduction
    hour = 22,              -- Hour of decay execution (24h format)
    minute = 0,             -- Minute of decay execution
    amount = 5              -- Amount of stat loss (in percentage points)
}
```

***

## Gym Blip Configuration

Customizes the in-game map marker for the gym location:

```lua
Config.GymBlip = {
    enabled = true, -- Show/hide the gym blip
    coords = vector3(-1201.14, -1565.23, 4.61), -- Location of the gym
    sprite = 311, -- Dumbbell icon
    color = 3, -- Green blip color
    scale = 0.8, -- Size of the blip
    name = "Quasar Gym", -- Blip label on map
    shortRange = true -- Only visible when nearby
}
```

***

## Reception NPC Configuration

Configure the NPC who handles gym membership purchases:

```lua
Config.ReceptionNPC = {
    model = "a_f_y_fitness_01", -- Female gym trainer model
    coords = vector4(-1195.32, -1577.64, 4.61, 119.6949), -- NPC location and heading
    label = "LABEL_PURCHASE_MEMBERSHIP" -- Text shown when interacting (localized)
}
```

You can easily change the model, coordinates, or interaction label to match your preferred gym style.
