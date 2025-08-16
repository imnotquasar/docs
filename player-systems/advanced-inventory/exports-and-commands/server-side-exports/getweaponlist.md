# GetWeaponList

The **GetWeaponList** export allows you to retrieve the complete list of weapons defined in your **shared/weapons.lua** file. This is useful for accessing and managing all weapon data programmatically within your scripts.

***

## How to Use

To get the full list of weapons, use the following code:

```lua
rlocal weaponList = exports['qs-inventory']:GetWeaponList()

for weaponName, weaponData in pairs(weaponList) do
    print("Weapon Name: " .. weaponName)
    print("Label: " .. weaponData.label)
end
```

This will return a table containing all the weapons and their properties, such as name, label, damage, and more. You can use this to interact with or display weapon details dynamically in your scripts.
