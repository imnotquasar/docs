# General Configuration

All configuration for **Quasar Realistic Gym** is handled in `shared/config.lua`. The script uses intelligent auto-detection to ensure fast, seamless integration across ESX, QBCore, QBox, or standalone setups.

***

## Basic Settings

These options control the core behavior of the system:

```lua
Config.Debug = false -- Enable debug messages for troubleshooting
Config.Language = 'en' -- Set your preferred language
Config.Framework = 'auto' -- Auto-detected or set manually
Config.UseTarget = true -- Enable targeting system integration
Config.Target = 'auto' -- Auto-detected targeting system
```

***

## Job Center NPC Configuration

Define the NPC model, position, and interaction text for opening the job center:

```lua
Config.JobCenterPed = {
    model = "a_f_y_business_01", -- Ped model to spawn
    coords = vector4(-268.9539, -956.1339, 31.2231, 204.3517), -- Location and heading
    label = "Open Job Center" -- Text displayed when near NPC
}
```

***

## **B**lip Configuration

Customize the map marker for the Job Center:

```lua
Config.JobCenterBlip = {
    enabled = true, -- Enable/disable the blip
    coords = vector3(-268.9539, -956.1339, 31.2231), -- Blip coordinates
    sprite = 407, -- Blip sprite ID (briefcase icon)
    color = 3, -- Blip color (green)
    scale = 0.8, -- Blip size
    name = "Job Center", -- Blip name on map
    shortRange = true -- Only show when close to the blip
}
```

***

## **Boss Management Configuration**

Configure how managers access the boss panel:

```lua
Config.UseBossItem = true -- Enable boss tablet item
Config.UseBossCommand = true -- Enable boss command
Config.BossItem = "boss_tablet" -- Item name for boss management
Config.BossCommand = "jobchats" -- Command for accessing boss panel
```

***

## **Auto-Detection System**

The resource automatically detects your framework and targeting system for optimal compatibility:

```lua
-- Framework Detection (Automatic)
local frameworks = {
    ['es_extended'] = 'esx',    -- ESX Framework
    ['qb-core'] = 'qbcore',     -- QBCore Framework  
    ['qbx_core'] = 'qbox'       -- QBox Framework
}

-- Targeting System Detection (Automatic)
local targets = {
    ['ox_target'] = 'ox_target',     -- OX Target
    ['qb-target'] = 'qb-target',     -- QB Target
    ['qs-textui'] = 'qs-textui'      -- QS TextUI
}
```
