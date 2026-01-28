---
description: >-
  This document focuses exclusively on the server-side screenshot function in
  the qs-police-creator resource for FiveM, using Lua.
---

# GetScreenshotUrl

It explains how to capture a screenshot from a specific player's client directly from server scripts and obtain a shareable URL (typically for use in dispatch calls or logs).

### What is GetScreenshotUrl(source) on server?

```lua
local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(source)
```

This server-side export:

* Requests the specified player's client (`source` = server player ID) to capture their current screen view
* Uploads the screenshot via the resource's configured service (Discord webhook, Imgur, custom, etc.)
* Returns a public/temporary URL to the uploaded image

The function is **asynchronous from the server's perspective** but blocks the calling thread until the client responds or times out.

### Function details

| Aspect                     | Details                                                                                                                                                                                                   |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Side**                   | **Server-side only** (called from server.lua or server scripts)                                                                                                                                           |
| **Parameter**              | `source` – The server ID of the player whose screen you want to capture (integer)                                                                                                                         |
| **Returns**                | <p><code>string</code> → valid https URL to the screenshot<br><code>nil</code> → if capture/upload failed or timed out</p>                                                                                |
| **Execution time**         | Usually 2–6 seconds (client capture + upload + network round-trip)                                                                                                                                        |
| **Blocking?**              | Yes – blocks the server thread that calls it until completion or failure                                                                                                                                  |
| **Requirements**           | <p>- Resource <code>qs-police-creator</code> started<br>- Screenshot service configured in the resource<br>- The target player must be connected and the client script loaded</p>                         |
| **Common failure reasons** | <p>- Invalid <code>source</code> (player not online)<br>- Client not responding (crashed, bad connection)<br>- No screenshot webhook configured<br>- Resource timeout<br>- Player blocked screenshots</p> |

### Basic usage example (server command)

```lua
-- server.lua

RegisterCommand('servershot', function(source, args, rawCommand)
    -- By default use the command executor as target
    local target = source

    -- Optional: use first argument as target player ID
    if args[1] then
        target = tonumber(args[1])
        if not target or target <= 0 then
            print("Invalid player ID")
            return
        end
    end

    -- Verify player exists
    if not GetPlayerName(target) then
        print("Player " .. target .. " not found/online")
        return
    end

    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(target)

    if screenshotUrl then
        print("Screenshot captured successfully for player " .. target)
        print("URL: " .. screenshotUrl)
        
        -- Optional: send URL to the admin who ran the command
        TriggerClientEvent('chat:addMessage', source, {
            color = {255, 200, 0},
            multiline = true,
            args = {"[Server Screenshot]", "Player " .. target .. ": " .. screenshotUrl}
        })
    else
        print("Failed to capture screenshot for player " .. target)
        
        TriggerClientEvent('chat:addMessage', source, {
            color = {255, 50, 50},
            args = {"[Error]", "Screenshot capture failed for player " .. target}
        })
    end
end, true)  -- true = admin/restricted command
```

### Recommended safe usage (with fallback and logging)

```lua
-- server.lua – Helper function

local function CapturePlayerScreenshot(targetSource, callback)
    if not targetSource or not GetPlayerName(targetSource) then
        callback(nil, "Invalid or offline player")
        return
    end

    local startTime = GetGameTimer()
    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(targetSource)

    local elapsed = GetGameTimer() - startTime

    if screenshotUrl then
        callback(screenshotUrl, nil)
        print(string.format("[Screenshot] Success for player %d in %d ms", targetSource, elapsed))
    else
        callback(nil, "Capture failed")
        print(string.format("[Screenshot] Failed for player %d after %d ms", targetSource, elapsed))
    end
end

-- Usage example in an event
RegisterNetEvent('my-resource:requestPlayerScreenshot')
AddEventHandler('my-resource:requestPlayerScreenshot', function(targetId)
    local src = source  -- admin/source who requested it

    CapturePlayerScreenshot(targetId, function(url, err)
        if url then
            TriggerClientEvent('chat:addMessage', src, {
                args = {"[Screenshot]", url}
            })
        else
            TriggerClientEvent('chat:addMessage', src, {
                color = {255, 50, 50},
                args = {"[Error]", err or "Unknown error"}
            })
        end
    end)
end)
```

### Most common real usage: With Dispatch Call

```lua
-- server.lua – Example: Send dispatch with player screenshot

RegisterCommand('dispatchwithshot', function(source, args, rawCommand)
    local target = source  -- or tonumber(args[1])

    if not GetPlayerName(target) then
        print("Player not found")
        return
    end

    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl(target)

    local playerName = GetPlayerName(target) or 'Unknown'

    local callData = {
        title = 'Server Reported Incident',
        description = 'Incident detected - attached player screenshot',
        location = { coords = { x = 123.4, y = 567.8, z = 21.0 } },  -- replace with real coords if available
        jobNames = { 'police' },
        image = screenshotUrl,  -- will be nil if failed (safe to include)
        priority = 2,
        caller = {
            playerId = target,
            name = playerName,
            phone = '555-UNKNOWN',
        },
        blip = { sprite = 280, color = 1, scale = 1.0, label = 'Incident' },
    }

    exports['qs-police-creator']:CreateDispatchCall(callData, source)  -- or target, depending on your needs

    print("Dispatch sent " .. (screenshotUrl and "with screenshot" or "without screenshot"))
end, true)
```

### Best practices & tips

* **Always validate `source`** — check `GetPlayerName(source)` or use framework helpers
* **Expect delays** — 2–8 seconds is normal; never call in tight loops
* **Use in threads if needed** — wrap in `Citizen.CreateThread` for non-blocking behavior in complex scripts
* **Log failures** — always log when it returns `nil` for debugging
* **Config check** — ensure qs-police-creator has a valid screenshot upload service set up
* **Permission** — restrict commands/events that use this function (anticheat abuse risk)
* **No spam** — implement cooldowns per player or globally
