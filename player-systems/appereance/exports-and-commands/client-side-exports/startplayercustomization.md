# startPlayerCustomization

The `startPlayerCustomization` export opens the character customization menu so the player can change their appearance (clothes, face, hair, etc.). It sets up the camera, hides the HUD, and locks the player in place until they finish.

***

## How to Use

You can use this export in a command like this:

```lua
RegisterCommand('customize', function()
    local config = exports['qs-appearance']:GetDefaultConfig()
    -- you can see what options of the config in qs-appearance/types.lua `Config` type
    config.character = true               -- this will enable character creation and make all the prices 0
    config.enableExit = true              -- this will enable the exit button in the customization menu
    config.upper_body = true
    config.componentConfig.gloves = false -- this will disable gloves in the upper body section
    exports['qs-appearance']:startPlayerCustomization(function(appearance)
        if appearance then
            print('Player finished customizing.')
            -- You can save the appearance here
        else
            print('Player cancelled customization.')
        end
    end, config)
end)
```

#### What It Does

* Opens the customization menu
* Freezes the player and hides the HUD
* Lets the player change their appearance
* Calls your callback function when done or cancelled

{% hint style="success" %}
Use it in shops, spawn menus, or whenever you want players to customize their look.
{% endhint %}
