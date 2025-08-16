# GetSSURL

The **GetSSURL** export allows you to capture a screenshot of a specific player. This screenshot can be used in dispatch systems or other features where visual context is required.

***

## How to Use

To use this export, pass the player's ID and a callback function to process the result:

```lua
exports['qs-dispatch']:GetSSURL(playerID, function(image)
    if image then
        print("Screenshot URL: " .. image)
    else
        print("Failed to retrieve screenshot.")
    end
end)
```

The export returns:

* **A URL string** pointing to the screenshot (e.g., `cdn.discordapp.net/image.png`).
* **`nil`** if the screenshot cannot be captured.

Use this export to enhance dispatch systems or other gameplay elements by providing visual evidence tied to player activities.
