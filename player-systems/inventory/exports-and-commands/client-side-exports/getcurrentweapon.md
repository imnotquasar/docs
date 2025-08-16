# GetCurrentWeapon

The **GetCurrentWeapon** export allows you to check the weapon currently in your hands. This export provides useful information about the weapon, such as its durability or other attributes, and can be integrated into custom scripts.

***

## How to Use

To retrieve the current weapon, use the following code:

```lua
local weapon = exports['qs-inventory']:GetCurrentWeapon()
if weapon then
    print("Current Weapon: " .. json.encode(weapon))
else
    print("No weapon equipped.")
end
```

Here’s an example of using this export to check the durability of a weapon:

```lua
RegisterCommand('getdurability', function()
    local weapon = exports['qs-inventory']:GetCurrentWeapon()
    if not weapon then
        print("No weapon equipped.")
        return
    end

    print('Weapon info:', json.encode(weapon, { indent = true }))
    local durability = weapon.info.quality
    print('Weapon durability:', durability)
end, false)
```

This command retrieves the weapon currently in use, prints its information, and displays its durability. It’s a simple and flexible way to interact with weapon data during gameplay.
