# Copy Keys System

The **Copy Keys System** allows players to duplicate their vehicle keys at specified locations for a configurable price. This system supports integration with `esx_menu_default` and `qtarget`, offering flexibility for different server setups.

***

## Configuration Options

{% stepper %}
{% step %}
### **Menu Settings**

* `Config.CopyKeysMenu`: Enables the key copy menu using `esx_menu_default`. If set to `false`, you can integrate it with `qtarget`.
* `Config.OpenCopyKeys`: Specifies the key to open the key copy menu (default: `E`).
* `Config.MenuPlacement`: Defines the position of the `esx_menu_default` menu (default: `top-left`).
{% endstep %}

{% step %}
### **Cost and Location**

* `Config.CopyKeysCost`: Set the price for duplicating keys. You can set it to `0` for free key duplication.
* `Config.CopyKeysLocations`: A list of locations where players can duplicate keys, defined using `vector3` coordinates.
{% endstep %}

{% step %}
### **Blip Configuration**

* `Config.Blip`: Enables or disables the blip on the map for the key duplication store.
* `Config.CopyKeysBlip`: Customize the blip, including:
  * **BlipName**: The name displayed on the map (default: `Copy keys`).
  * **BlipSprite**: Icon representing the location (default: `186`).
  * **BlipColour**: Color of the blip (default: `3`).
  * **BlipScale**: Size of the blip on the map (default: `0.8`).
{% endstep %}
{% endstepper %}

```lua
Config.CopyKeysMenu = true --- If you want to use the esx getdistancebetweencoords menu, otherwhise you can make it work with qtarget, the function to open menu is OpenCopyKeys()
Config.OpenCopyKeys = 'E' -- Key to open the key copy menu.
Config.MenuPlacement = 'top-left' -- Position of `esx_menu_default`.
Config.CopyKeysCost = 500 -- Price of the copies of the keys, you can use 0 and it will be free.
Config.CopyKeysLocations = { -- List of stores to copy keys.
	vector3(-31.402076721191, -1647.4393310547, 29.282875061035)
}

Config.Blip = true -- True or false for disable the blip.
Config.CopyKeysBlip = { -- Blip of the key copy spot.
	BlipName = 'Copy keys',
	BlipSprite = 186,
	BlipColour = 3,
	BlipScale = 0.8,
}
```

***

## Example Use Case

Imagine a player loses their vehicle keys and needs a duplicate. They navigate to a **Copy Keys** location marked by a blip on the map, press the interaction key (`E` by default), and use the menu to create a duplicate for a set price. The system ensures accessibility while maintaining configurable pricing and visual customization to suit your server's theme.
