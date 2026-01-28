# CreateDispatchCall

This document explains how to create police / emergency dispatch calls from server-side scripts (Lua) using the `qs-police-creator` resource in FiveM.

### What you can do from the server side

* Create a dispatch call with minimal data
* Add a screenshot from a specific player (using their server `source` ID)
* Use `GetPlayerInfo(source)` to get detailed player/vehicle/location data
* Put street names, vehicle plate, speed, etc. directly into the **description** field

### Main server-side functions

| Export / Function                                                   | Description                                                             | Returns                  |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------- | ------------------------ |
| `exports['qs-police-creator']:GetScreenshotUrl(source)`             | Requests screenshot from the specified player's client and returns URL  | `string` or `nil`        |
| `exports['qs-police-creator']:CreateDispatchCall(callData, source)` | Creates and sends dispatch to the specified jobs                        | `result` (boolean/table) |
| `GetPlayerInfo(source)`                                             | Returns detailed info about the player (coords, streets, vehicle, etc.) | `table` or `nil`         |

### GetPlayerInfo(source) – Returned fields

```lua
{
    ped             = ped handle,
    coords          = vector3,
    street_1        = string,
    street_2        = string,
    sex             = string,
    vehicle         = entity or nil,
    vehicle_label   = string or 'VehLabel Unknown',
    vehicle_colour  = string or 'VehColor Unknown',
    vehicle_plate   = string or 'VehPlate Unknown',
    speed           = number,           -- km/h
    doorCount       = number,
    networkEntityId = number or 0
}
```

### Full callData structure

```lua
local callData = {
    title       = string,               -- required
    description = string,               -- required – include data from GetPlayerInfo()
    location    = {                     -- required
        coords = { x = number, y = number, z = number }
    },
    jobNames    = { "police", "sheriff" },   -- required
    priority    = number,               -- optional
    image       = string,               -- optional – screenshot URL
    caller      = {                     -- optional – basic reporter info
        playerId = number,
        name     = string,
        phone    = string,
    },
    blip        = {                     -- optional
        sprite = number,
        color  = number,
        scale  = number,
        label  = string
    }
}
```

### 1. Minimal Dispatch (no screenshot, no extra info)

```lua
-- server.lua

RegisterCommand('serverdispatchmin', function(source, args, rawCommand)
    local callData = {
        title       = 'Suspicious Activity',
        description = 'Unknown person loitering (server detected)',
        location    = { coords = { x = 123.4, y = 567.8, z = 21.0 } },
        jobNames    = { 'police' },
        priority    = 2,
        blip        = { sprite = 280, color = 1, scale = 1.0, label = 'Suspicious' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, source)
end, true)
```

### 2. Dispatch with Screenshot

```lua
-- server.lua

RegisterCommand('serverdispatchscreenshot', function(source, args, rawCommand)
    local target = tonumber(args[1]) or source

    if not GetPlayerName(target) then
        print("Player not found")
        return
    end

    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(target)

    local callData = {
        title       = 'Robbery in Progress',
        description = 'Armed suspects inside store (server alert)',
        location    = { coords = { x = 123.4, y = 567.8, z = 21.0 } },
        jobNames    = { 'police', 'sheriff' },
        image       = screenshotUrl,
        priority    = 1,
        blip        = { sprite = 280, color = 49, scale = 1.0, label = 'Robbery' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, source)
end, true)
```

### 3. Dispatch using GetPlayerInfo() in description

```lua
-- server.lua

RegisterCommand('serverdispatchinfo', function(source, args, rawCommand)
    local playerInfo = GetPlayerInfo(source) or {}

    local street = playerInfo.street_1 or 'Unknown'
    if playerInfo.street_2 and playerInfo.street_2 ~= '' then
        street = street .. ' / ' .. playerInfo.street_2
    end

    local description = ('Shots fired reported at %s.'):format(street)

    if playerInfo.vehicle_label then
        description = description .. (' Possible suspect vehicle: %s [%s] @ %d km/h.'):format(
            playerInfo.vehicle_label,
            playerInfo.vehicle_plate or '???',
            playerInfo.speed or 0
        )
    end

    local callData = {
        title       = 'Shots Fired',
        description = description,
        location    = { coords = playerInfo.coords and { x = playerInfo.coords.x, y = playerInfo.coords.y, z = playerInfo.coords.z } or { x = 123.4, y = 567.8, z = 21.0 } },
        jobNames    = { 'police' },
        caller      = {
            playerId = source,
            name     = GetPlayerName(source) or 'Unknown',
            phone    = '555-UNKNOWN',
        },
        priority    = 1,
        blip        = { sprite = 280, color = 1, scale = 1.0, label = 'Shots Fired' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, source)
end, true)
```

### 4. Full example – Screenshot + GetPlayerInfo() in message

```lua
-- server.lua

RegisterCommand('serverdispatchfull', function(source, args, rawCommand)
    local playerInfo = GetPlayerInfo(source) or {}

    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(source)

    local street = playerInfo.street_1 or 'Unknown location'
    if playerInfo.street_2 and playerInfo.street_2 ~= '' then
        street = street .. ' / ' .. playerInfo.street_2
    end

    local desc = ('Traffic accident reported at %s.'):format(street)

    if playerInfo.vehicle_label then
        desc = desc .. (' Involved: %s [%s] - %d km/h'):format(
            playerInfo.vehicle_label,
            playerInfo.vehicle_plate or '???',
            playerInfo.speed or 0
        )
    end

    local callData = {
        title       = 'Traffic Accident',
        description = desc,
        location    = { coords = playerInfo.coords and { x = playerInfo.coords.x, y = playerInfo.coords.y, z = playerInfo.coords.z } or { x = 123.4, y = 567.8, z = 21.0 } },
        jobNames    = { 'police', 'ems' },
        caller      = {
            playerId = source,
            name     = GetPlayerName(source) or 'Unknown',
            phone    = '555-UNKNOWN',
        },
        image       = screenshotUrl,
        priority    = 1,
        blip        = { sprite = 280, color = 3, scale = 1.2, label = 'Accident' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, source)
end, true)
```

### 5. Dynamic location from client event + GetPlayerInfo()

```lua
-- server.lua

RegisterNetEvent('my-resource:reportAccident')
AddEventHandler('my-resource:reportAccident', function(coords)
    local src = source

    local playerInfo = GetPlayerInfo(src) or {}

    local street = playerInfo.street_1 or 'Unknown'
    if playerInfo.street_2 and playerInfo.street_2 ~= '' then
        street = street .. ' / ' .. playerInfo.street_2
    end

    local description = ('Accident reported at %s.'):format(street)

    local callData = {
        title       = 'Player Reported Accident',
        description = description,
        location    = { coords = coords },
        jobNames    = { 'police', 'ambulance' },
        caller      = {
            playerId = src,
            name     = GetPlayerName(src) or 'Unknown',
            phone    = '555-UNKNOWN',
        },
        priority    = 1,
        blip        = { sprite = 280, color = 3, scale = 1.2, label = 'Accident' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, src)
end)
```

### Quick tips

* Use `playerInfo.coords` when available — more reliable than manual coords
* Put street, vehicle plate, speed directly in `description` — officers see it right away
* Keep `caller` simple (id, name, phone)
* Always handle `GetPlayerInfo()` returning `nil` with fallback
* Combine screenshot + detailed description for best results
