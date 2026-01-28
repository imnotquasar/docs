---
description: >-
  This document focuses exclusively on the GetScreenshotUrl() function in the
  client-side (Lua) of the qs-police-creator resource for FiveM.
---

# GetScreenshotUrl

It explains everything you need to know about taking screenshots from the player's game and getting a shareable URL to use in dispatch calls or other features.

### What is GetScreenshotUrl()?

`exports['qs-police-creator']:GetScreenshotUrl()`\
Is a client-side export that:

* Captures the current view of the player's screen (what the player sees in-game at that moment)
* Uploads the screenshot to a configured image hosting service (usually Discord webhook, Imgur, or custom server configured in qs-police-creator)
* Returns a public/temporary URL to the uploaded image

This URL can then be used in dispatch calls (as the `image` field) to attach visual evidence to police alerts.

### Function details

```lua
local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()
```

| Aspect                     | Details                                                                                                                                |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Side**                   | Client-side only (must be called from client.lua or client script)                                                                     |
| **Returns**                | <p><code>string</code> → valid https URL to the screenshot<br><code>nil</code> → if capture/upload failed</p>                          |
| **Execution time**         | Usually 1–4 seconds (depends on network, screenshot quality, upload speed)                                                             |
| **Blocking?**              | Yes – it blocks until the screenshot is taken and uploaded (or fails)                                                                  |
| **Requirements**           | <p>- Resource <code>qs-police-creator</code> must be started<br>- Screenshot system must be configured (check resource config.lua)</p> |
| **Common failure reasons** | <p>- No screenshot service configured<br>- Network issues<br>- Player too fast (spamming)<br>- Resource not fully loaded</p>           |

### Basic usage example

```lua
-- client.lua

RegisterCommand('takeshot', function()
    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()

    if screenshotUrl then
        print("Screenshot taken successfully!")
        print("URL: " .. screenshotUrl)
        
        -- Example: show notification to player
        BeginTextCommandThefeedPost('STRING')
        AddTextComponentSubstringPlayerName("Screenshot URL: ~y~" .. screenshotUrl)
        EndTextCommandThefeedPostTicker(true, false)
    else
        print("Failed to take screenshot")
        
        -- Optional: notify player
        BeginTextCommandThefeedPost('STRING')
        AddTextComponentSubstringPlayerName("~r~Failed to capture screenshot")
        EndTextCommandThefeedPostTicker(true, false)
    end
end, false)
```

### Recommended safe usage (with timeout protection)

Because the function can take several seconds and block the thread, it's best to wrap it and add a timeout/fallback:

```lua
-- client.lua – Safe wrapper example

local function GetSafeScreenshot(callback)
    Citizen.CreateThread(function()
        local startTime = GetGameTimer()
        local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()
        
        if screenshotUrl then
            callback(screenshotUrl)
        else
            local elapsed = GetGameTimer() - startTime
            print("Screenshot failed after " .. elapsed .. "ms")
            callback(nil)
        end
    end)
end

-- Usage example
RegisterCommand('safeshot', function()
    GetSafeScreenshot(function(url)
        if url then
            TriggerEvent('chat:addMessage', {
                color = {255, 200, 0},
                multiline = true,
                args = {"[Screenshot]", "URL: " .. url}
            })
        else
            TriggerEvent('chat:addMessage', {
                color = {255, 50, 50},
                args = {"[Error]", "Could not capture screenshot"}
            })
        end
    end)
end, false)
```

### Using GetScreenshotUrl() with Dispatch Call (most common use)

```lua
-- client.lua – Typical real usage in a dispatch script

RegisterCommand('reportrobbery', function()
    local screenshotUrl = exports['qs-police-creator']:GetScreenshotUrl()

    local callData = {
        title = 'Robbery in Progress',
        description = 'Suspects with weapons inside the store - see attached photo',
        location = { coords = vector3(GetEntityCoords(PlayerPedId())) },
        jobNames = { 'police', 'sheriff' },
        image = screenshotUrl,           -- this is where the URL goes
        priority = 1,
        blip = { sprite = 280, color = 49, scale = 1.0, label = 'Robbery' },
    }

    if screenshotUrl then
        print("Dispatch with photo evidence sent")
    else
        print("Dispatch sent without photo (capture failed)")
        -- You can still send → just omit 'image' or leave as nil
    end

    exports['qs-police-creator']:CreateDispatchCall(callData)
end, false)
```

### Best practices & tips

* **Always check for nil** — never assume the URL exists
* **Don't spam it** — add cooldowns (e.g. 10–30 seconds) to prevent abuse
* **Inform the player** — use notifications/chat when capture starts/fails/succeeds
* **Use in threads** — if you call it in a long script, wrap in `Citizen.CreateThread` to avoid freezing other code
* **Test upload config** — make sure qs-police-creator has a valid screenshot webhook/service configured
* **Quality vs speed** — higher quality screenshots take longer to upload
