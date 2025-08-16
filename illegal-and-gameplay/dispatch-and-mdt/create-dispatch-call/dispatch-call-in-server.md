# Dispatch Call in Server

The event `qs-dispatch:server:CreateDispatchCall` is used to generate dispatch calls for specific jobs in the dispatch management system. This event should be triggered server-side, passing an object with the required parameters.

***

## Basic Dispatch Call

The event qs-dispatch:server:CreateDispatchCall is used to create a dispatch call in a dispatch management system. You must pass an object as an argument to the event with the following data:

* `job` (array): A list of jobs related to the dispatch call. You can include values such as 'police', 'sheriff', 'traffic', 'patrol' and any others you wish to receive the dispatch call.
* `callLocation` (vector3): The coordinates of the location of the dispatch call. You must provide the coordinates in the form of a vector3 object.
* `callCode` (table): An object containing a call code and an associated code fragment. For example, you can have a call code 'Hight Speed' with a code fragment 'Vehicle'.
* `message` (string): A message describing the dispatch call. It may include relevant information such as vehicle model, license plate, color and speed.
* `flashes` (boolean): A Boolean value indicating whether the dispatch call icon should flash.
* `image` (string o nil): An image attached to the dispatch call. This can be an image URL or nil if there is no image attached.
* `blip` (table): An object describing the blip associated with the dispatch call. It may contain properties such as the blip's sprite, scale, color, whether it blinks, the associated text, and the blip's duration time in milliseconds.

Be sure to provide the proper data in the correct format when calling this event to create a dispatch:

```lua
TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
    job = { 'police', 'sheriff', 'traffic', 'patrol' }, -- List of jobs to receive the dispatch
    callLocation = vector3(0, 0, 0), -- Coordinates of the call
    callCode = { code = '10-10', snippet = 'Vehicle Pursuit' }, -- Call code and description
    message = "A high-speed vehicle was spotted traveling at 120 km/h.", -- Dispatch call message
    flashes = true, -- Should the blip on the map flash?
    image = "URL", -- Optional: URL for an image attachment (use `getSSURL` if needed)
    blip = { -- Blip details for the map
        sprite = 488, -- Blip icon type
        scale = 1.5, -- Blip size
        colour = 1, -- Blip color
        flashes = true, -- Blip flashes
        text = 'High-Speed Pursuit', -- Blip label
        time = (60 * 1000), -- Duration of the blip (milliseconds)
    },
    otherData = { -- Additional optional information
        {
            text = 'Suspect wearing red', -- Additional detail
            icon = 'fas fa-user-secret' -- Font Awesome icon
        }
    }
})

```

***

## Dispatch Call With Player Data

This example demonstrates how to use the `GetPlayerInfo` export and `CreateDispatchCall` to generate a dispatch call using player information.

The GetPlayerInfo export retrieves detailed player data, which can then be used in the CreateDispatchCall event to send a dispatch alert to specified jobs.

```lua
exports['qs-dispatch']:GetPlayerInfo(PlayerID, function(playerData)
    if (not playerData) then
        ErrorPrint("Error getting player data")
        return
    end
    TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
        job = { 'police', 'sheriff', 'traffic', 'patrol' },
        callLocation = playerData.coords,
        callCode = { code = 'High Speed', snippet = 'Vehicle' },
        message = "Street 1: ".. playerData.street_1 ..", Street 2: ".. playerData.street_2 ..
                  ", Gender: ".. playerData.sex ..", Vehicle: ".. playerData.vehicle_label ..
                  ", Color: ".. playerData.vehicle_colour ..", Plate: ".. playerData.vehicle_plate ..
                  ", Speed: ".. playerData.speed,
        flashes = false,
        image = nil,
        blip = {
            sprite = 488,
            scale = 1.5,
            colour = 1,
            flashes = true,
            text = 'High Speed',
            time = (20 * 1000), -- 20 seconds
        }
    })
end)
```

For static data, you can create a dispatch call without player-specific information using the following:

```lua
TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
    job = { 'police', 'sheriff', 'traffic', 'patrol' },
    callLocation = vector3(0, 0, 0),
    callCode = { code = '<CALL CODE>', snippet = '<CALL SNIPPED EX: 10-10>' },
    message = "Call Message",
    flashes = false, -- Enable flashing lights if needed
    image = "URL", -- Attach an image URL (optional)
    blip = {
        sprite = 488, -- Blip icon
        scale = 1.5, -- Blip size
        colour = 1, -- Blip color
        flashes = true, -- Blip flashes
        text = 'High Speed', -- Blip label
        time = (20 * 1000), -- Duration in milliseconds
    }
})
```

***

## Dispatch Call With Player Data and Image

This example demonstrates how to use the `CreateDispatchCall`, `GetPlayerInfo`, and `GetSSURL` exports to create a dispatch call enriched with player data and a screenshot.

This implementation fetches player-specific details (e.g., location, vehicle information) and optionally attaches a screenshot for enhanced dispatch call details.

```lua
exports['qs-dispatch']:GetPlayerInfo(PlayerID, function(playerData)
    if (not playerData) then
        ErrorPrint("Error getting player data")
        return
    end
    exports['qs-dispatch']:GetSSURL(PlayerID, function(screenshot)
        TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
            job = { 'police', 'sheriff', 'traffic', 'patrol' },
            callLocation = playerData.coords,
            callCode = { code = 'High Speed', snippet = 'Vehicle' },
            message = "Street 1: ".. playerData.street_1 ..
                      ", Street 2: ".. playerData.street_2 ..
                      ", Gender: ".. playerData.sex ..
                      ", Vehicle: ".. playerData.vehicle_label ..
                      ", Color: ".. playerData.vehicle_colour ..
                      ", Plate: ".. playerData.vehicle_plate ..
                      ", Speed: ".. playerData.speed,
            flashes = false,
            image = screenshot or nil, -- Attach screenshot if available
            blip = {
                sprite = 488,
                scale = 1.5,
                colour = 1,
                flashes = true,
                text = 'High Speed',
                time = (20 * 1000), -- 20 seconds
            }
        })
    end)
end)
```

***

## Server Command for Dispatch

This example demonstrates how to create a server command that triggers a dispatch alert with player-specific data. By using this command, you can send a dispatch notification to configured jobs like `police`, `sheriff`, `traffic`, and `patrol`.

Add the following code to your `server.lua` file. When you run the `test` command in the TxAdmin console or game chat (with a valid player ID), it will fetch player data and send a dispatch alert.

```lua
RegisterCommand('test', function(source, args, rawCommand)
    -- Ensure the player ID is provided
    local PlayerID = tonumber(args[1])
    if not PlayerID then
        ErrorPrint("No player ID provided")
        return
    end

    -- Fetch player data
    exports['qs-dispatch']:GetPlayerInfo(PlayerID, function(playerData)
        if not playerData then
            ErrorPrint("Error getting player data")
            return
        end

        -- Fetch screenshot
        exports['qs-dispatch']:GetSSURL(PlayerID, function(screenshot)
            TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
                job = { 'police', 'sheriff', 'traffic', 'patrol' },
                callLocation = playerData.coords,
                callCode = { code = 'Test Command', snippet = 'TEST' },
                message = "Street 1: " .. playerData.street_1 ..
                          ", Street 2: " .. playerData.street_2 ..
                          ", Gender: " .. playerData.sex ..
                          ", Vehicle: " .. playerData.vehicle_label ..
                          ", Color: " .. playerData.vehicle_colour ..
                          ", Plate: " .. playerData.vehicle_plate ..
                          ", Speed: " .. playerData.speed,
                flashes = false,
                image = screenshot or nil, -- Attach screenshot if available
                blip = {
                    sprite = 488,
                    scale = 1.5,
                    colour = 1,
                    flashes = true,
                    text = 'Test Command',
                    time = (20 * 1000), -- 20 seconds
                }
            })
        end)
    end)
end, false)
```

{% stepper %}
{% step %}
### Command Execution

Use `/test [PlayerID]` in the TxAdmin console or game chat to trigger the dispatch.
{% endstep %}

{% step %}
### Dynamic Data Retrieval

The command fetches real-time player data, including location, vehicle details, and speed.
{% endstep %}

{% step %}
### Screenshot Attachment

Automatically captures and attaches a player screenshot (if available) to the dispatch alert.
{% endstep %}

{% step %}
### Dispatch Customization

Configure jobs, messages, blips, and other details within the `CreateDispatchCall` event.
{% endstep %}
{% endstepper %}

This setup ensures a dynamic and interactive way to create dispatch alerts for specific players.
