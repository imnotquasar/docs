# Dispatch Call in Client

The event `qs-dispatch:server:CreateDispatchCall` allows you to create dispatch calls in the system, targeting specific jobs and providing detailed call information. Below is a guide to using this event effectively.

***

## Basic Dispatch Call

The event qs-dispatch:server:CreateDispatchCall is used to create a dispatch call in a dispatch management system. You must pass an object as an argument to the event with the following data.

* `job` (array): A list of jobs related to the dispatch call. You can include values such as 'police', 'sheriff', 'traffic', 'patrol' and any others you wish to receive the dispatch call.
* `callLocation` (vector3): The coordinates of the location of the dispatch call. You must provide the coordinates in the form of a vector3 object.
* `callCode` (table): An object containing a call code and an associated code fragment. For example, you can have a call code 'Hight Speed' with a code fragment 'Vehicle'.
* `message` (string): A message describing the dispatch call. It may include relevant information such as vehicle model, license plate, color and speed.
* `flashes` (boolean): A Boolean value indicating whether the dispatch call icon should flash.
* `image` (string o nil): An image attached to the dispatch call. This can be an image URL or nil if there is no image attached.
* `blip` (table): An object describing the blip associated with the dispatch call. It may contain properties such as the blip's sprite, scale, color, whether it blinks, the associated text, and the blip's duration time in milliseconds.

Be sure to provide the proper data in the correct format when calling this event to create a dispatch:

```lua
TriggerServerEvent('qs-dispatch:server:CreateDispatchCall', {
    job = { 'police', 'sheriff', 'traffic', 'patrol' },
    callLocation = vector3(0, 0, 0),
    callCode = { code = '10-10', snippet = 'Vehicle Pursuit' },
    message = "A vehicle speeding at 120 km/h with license plate ABC123 was spotted.",
    flashes = true,
    image = "https://cdn.example.com/image.png", -- Use getSSURL if needed
    blip = {
        sprite = 488,
        scale = 1.5,
        colour = 1,
        flashes = true,
        text = 'High-Speed Pursuit',
        time = 60000, -- 1 minute
    },
    otherData = {
        {
            text = 'Suspect Wearing Red',
            icon = 'fas fa-user-secret'
        }
    }
})
```

***

## Dispatch Call With Player Data

The combination of `CreateDispatchCall` and `GetPlayerInfo` allows you to dynamically generate dispatch calls based on real-time player information. This is useful for creating personalized and precise alerts for jobs like police or emergency services.

To create a dispatch call using real-time player data, use the following code:

```lua
local playerData = exports['qs-dispatch']:GetPlayerInfo()

TriggerServerEvent('qs-dispatch:server:CreateDispatchCall', {
    job = { 'police', 'sheriff', 'traffic', 'patrol' }, -- Targeted jobs
    callLocation = playerData.coords, -- Player's current location
    callCode = { code = 'High Speed', snippet = 'Vehicle' }, -- Dispatch code
    message = "street_1: ".. playerData.street_1.. " street_2: ".. playerData.street_2.. 
              " sex: ".. playerData.sex.. " vehicle_label: ".. playerData.vehicle_label.. 
              " vehicle_colour: ".. playerData.vehicle_colour.. " vehicle_plate: ".. playerData.vehicle_plate.. 
              " speed: ".. playerData.speed, -- Detailed call message
    flashes = false, -- No flashing icon
    image = image or nil, -- Optional image URL for dispatch
    blip = {
        sprite = 488, -- Blip icon
        scale = 1.5,  -- Blip size
        colour = 1,   -- Blip color
        flashes = true, -- Blip flashes
        text = 'High Speed', -- Blip label
        time = (20 * 1000), -- Blip duration in milliseconds
    }
})
```

***

## Dispatch Call With Player Data and Image

This example demonstrates how to create a dispatch call that includes real-time player data and a screenshot URL. This is useful for creating detailed and visual alerts for dispatch jobs like police or emergency services.

To dynamically generate a dispatch call with player data and a screenshot, use the following code:

```lua
local playerData = exports['qs-dispatch']:GetPlayerInfo()

-- Check if player data is successfully retrieved
if (not playerData) then
    ErrorPrint("Error getting player data")
    return
end

-- Get the screenshot URL and create a dispatch call
exports['qs-dispatch']:getSSURL(function(image)
    TriggerServerEvent('qs-dispatch:server:CreateDispatchCall', {
        job = { 'police', 'sheriff', 'traffic', 'patrol' }, -- Targeted jobs
        callLocation = playerData.coords, -- Player's current location
        callCode = { code = 'High Speed', snippet = 'Vehicle' }, -- Dispatch code
        message = "street_1: ".. playerData.street_1.. " street_2: ".. playerData.street_2.. 
                  " sex: ".. playerData.sex.. " vehicle_label: ".. playerData.vehicle_label.. 
                  " vehicle_colour: ".. playerData.vehicle_colour.. " vehicle_plate: ".. playerData.vehicle_plate.. 
                  " speed: ".. playerData.speed, -- Detailed call message
        flashes = false, -- No flashing icon
        image = image or nil, -- Screenshot URL for dispatch
        blip = {
            sprite = 488, -- Blip icon
            scale = 1.5,  -- Blip size
            colour = 1,   -- Blip color
            flashes = true, -- Blip flashes
            text = 'High Speed', -- Blip label
            time = (20 * 1000), -- Blip duration in milliseconds
        }
    })
end)

```

***

## Client Command for Dispatch

Add the following code to your `client.lua` file. Running the `/testclient` command in-game will send a dispatch alert to the configured jobs (`police`, `sheriff`, `traffic`, `patrol`) with the player's details who executed the command.

```lua
RegisterCommand('testclient', function(source, args, rawCommand)
    local playerData = exports['qs-dispatch']:GetPlayerInfo()

    if (not playerData) then
        ErrorPrint("Error getting player data")
        return
    end

    exports['qs-dispatch']:getSSURL(function(image)
        TriggerServerEvent('qs-dispatch:server:CreateDispatchCall', {
            job = { 'police', 'sheriff', 'traffic', 'patrol' },
            callLocation = playerData.coords,
            callCode = { code = 'High Speed', snippet = 'Vehicle' },
            message = "Street 1: ".. playerData.street_1 ..", Street 2: ".. playerData.street_2 ..
                      ", Gender: ".. playerData.sex ..", Vehicle: ".. playerData.vehicle_label ..
                      ", Color: ".. playerData.vehicle_colour ..", Plate: ".. playerData.vehicle_plate ..
                      ", Speed: ".. playerData.speed,
            flashes = false,
            image = image or nil,
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
end, false)
```

{% stepper %}
{% step %}
### **Command Execution**

Use `/testclient` in the game chat.
{% endstep %}

{% step %}
### **Player Data Fetching**

The script gathers player details like location, vehicle, and speed.
{% endstep %}

{% step %}
### **Dispatch Alert Creation**

Sends the gathered information to the configured jobs as a dispatch call.
{% endstep %}
{% endstepper %}

This example demonstrates how to integrate `qs-dispatch` to trigger dispatch events dynamically based on player data.
