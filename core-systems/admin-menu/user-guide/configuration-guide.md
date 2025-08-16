# Configuration Guide

Quasar Admin Menu includes a wide range of customization options. Below are the **most important configuration entries** to ensure proper functionality:

***

## Discord Integration

{% stepper %}
{% step %}
## **guildId**

Set this to the **Discord Guild ID** of your server. It is required for role-based admin access.
{% endstep %}

{% step %}
## **GodId**

This must be the **Discord Role ID** (not user ID) of the role that has full administrative access. Without this, the admin panel will be restricted.
{% endstep %}

{% step %}
## **BotToken**

Your Discord bot token, used to retrieve role data. The bot must be a member of your Discord server, even if it's offline.
{% endstep %}
{% endstepper %}

{% embed url="https://discord.com/developers/applications" %}

***

## General Configuration

```lua
Config.Command = "qadmin" -- Change to your desired admin command
AdminConfig.Discord = "discord.gg/quasarstore" -- Discord link shown in the panel
AdminConfig.ServerLogo = "URL_TO_YOUR_IMAGE" -- Header image for your admin dashboard
AdminConfig.Inventory = "qs" -- Options: qs, qb, codem, ox
AdminConfig.AmbulanceScript = "" -- Register your custom script in server/custom/ambulance.lua
```

***

## Entity & Environment Controls

```lua
AdminConfig.PedRate = 0.99
AdminConfig.VehicleRate = 0.99
AdminConfig.ClearPedRadius = 50.0
AdminConfig.ClearNearbyVehiclesRadius = 50.0
AdminConfig.ResetWorldRadius = 50.0
```

***

## Weather System Compatibility

```lua
Config.WeatherManager = "qb-weathersync" -- Supports qb-weathersync, cd_easytime, vSync, weathersync

AdminConfig.WeatherList = {
  "HALLOWEEN", "EXTRASUNNY", "CLEAR", "NEUTRAL", "SMOG", "FOGGY",
  "OVERCAST", "CLOUDY", "CLEARING", "RAINY", "THUNDER",
  "SNOW", "BLIZZARD", "SNOWLIGHT", "XMAS"
}
```

***

## Framework Detection

Quasar Admin Menu automatically detects your framework — QBCore or ESX — and configures itself accordingly.

```lua
Config.AdminFramework = {
  qb = "qb-core",
  esx = "es_extended"
}

AdminConfig.FrameworkName = "other" -- Default, auto-updated at runtime
```

On runtime:

* If `qb-core` is running and exports `GetCoreObject`, the system initializes for **QBCore**
* If `es_extended` is detected via import or `getSharedObject`, it initializes for **ESX**
* If none is detected, the asset will fall back to `'other'` mode with limited features

The detection log will confirm the selected framework during startup.
