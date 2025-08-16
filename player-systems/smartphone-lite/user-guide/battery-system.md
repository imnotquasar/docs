# Battery system

The Quasar Smartphone features an advanced battery system managed through intelligent JSON storage, which tracks each player's battery status. Here's a simple explanation of its functionalities and usage.

***

## **Battery usage settings**

Ensure **Config.EnableBattery** is enabled in your **config.lua**, or the battery system won't work. You can customize the battery usage for each app and adjust overall consumption using **Config.Battery**. This allows you to control how quickly the battery drains for different applications.

```lua
Config.Battery = {
    default = 0.01, -- This is the rate at which the battery drains by default.
    apps = { -- The following applications will make your battery go down faster.
        ['phone'] = 0.02,
        ['photos'] = 0.02,
        ['messages'] = 0.02,
        ['settings'] = 0.02,
        ['clock'] = 0.02,
        -- Other apps
    }
}
```

***

## **Recharging options**

{% stepper %}
{% step %}
### Powerbank

Players can use a powerbank item to recharge their phone to 100%. Ensure this item is added to your database or item base.
{% endstep %}

{% step %}
### Charging Spots

Configurable spots on the map allow players to recharge their phones. The phone will be taken away during charging, and the charge level will display until it reaches 100%. Add these spots in **Config.ChargerSpots** within the configuration file.
{% endstep %}
{% endstepper %}

***

## **Administrator battery command**

Admins can recharge players' batteries using a dedicated command. Enable **Config.AdminCommand** in **config.lua** to manage permissions and commands. The default command is **/adminbattery id amount** to set a player's battery level.

***

## **Checking battery level**

Use the export **getBattery** to check a player's battery level from the client side. This is a simple and efficient way to create custom events that rely on battery status.

```lua
exports['qs-smartphone']:getBattery()
```

This system is flexible, allowing full customization of battery usage, charging methods, and administrative controls.
