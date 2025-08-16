# Control Configuration

This section explains how to customize the control configuration for enabling or disabling specific features, such as hotkeys for vehicle actions, as well as assigning new keybindings for better compatibility and roleplay.

***

## Customizing Hotkeys

The system provides flexibility to enable or disable hotkeys and assign custom keys for specific actions:

{% stepper %}
{% step %}
### **Enable or Disable Hotkeys**

Use `Config.HotKeys` to globally enable or disable the hotkey system. Set it to `true` to allow the use of hotkeys or `false` to disable them.
{% endstep %}

{% step %}
### **Key Bindings**

* **Engine Control**: Default keybinding is set to `IOM_WHEEL_UP` (Mouse wheel up) to start or stop the engine. This ensures better compatibility with systems like `qs-dispatch` and enhances roleplay by avoiding conflicts with commonly used keys.
* **Lock/Unlock Vehicle**: The default key for locking or unlocking the vehicle is `U`. You can replace it with a key of your choice.
{% endstep %}

{% step %}
### **Hotwiring Configuration**

* **Enable Hotwire**: Use `Config.Hotwire` to toggle the hotwiring feature. Set it to `true` to allow players to hotwire vehicles or `false` to disable this functionality.
* **Hotwire Key**: The default keybinding for starting the hotwiring process is `H`. You can modify it based on your preference.
{% endstep %}
{% endstepper %}

```lua
Config.HotKeys = true -- Enable or disable the engine on/off system
Config.Controls = {
    EngineControl = 'IOM_WHEEL_UP', -- Key to start or stop the engine. (Mouse wheel up) for better compatibility with the qs-dispatch already using the G keybind. And also better roleplay
    UseKey = 'U', -- Key to lock / unlock the car
}

Config.Hotwire = true -- True or false for enable / disable the hotwire functions
Config.UseHotwire = 'H' -- Key to start hotwiring the car
```

***

## Example Use Case

For immersive roleplay, using the mouse wheel (`IOM_WHEEL_UP`) for engine control and keeping the `U` key for lock/unlock actions maintains a natural flow. The `H` key for hotwiring adds a layer of realism and interaction, allowing players to perform vehicle-related tasks seamlessly.

These configurations ensure flexibility while maintaining compatibility with other scripts and enhancing player experience.
