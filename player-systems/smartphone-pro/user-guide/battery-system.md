# Battery system

The **Smartphone PRO** introduces a significantly enhanced battery system compared to previous versions. It now utilizes metadata for dynamic and precise battery tracking, interacting with the phone's dynamic island at 20% and 10% charge levels.

***

## General Battery Configuration

The battery system allows customization of power consumption for default and app-specific usage. You can enable the interval system, adjust default consumption rates, and assign higher or lower drain rates for specific applications.

```lua
Config.Battery = {
    enabled = true,
    interval = 1000,
    default = 0.001,
    apps = {
        ['phone'] = 0.002,
        ['whatsapp'] = 0.002,
        ['twitter'] = 0.002,
        -- Add or modify apps as needed
    }
}
```

***

## Battery Recharging Options

{% stepper %}
{% step %}
### Powerbank

Use the powerbank item (set up during installation) to recharge your phone. If multiple phones are in the inventory, you can choose which one to recharge. The powerbank charges the battery to 100%.
{% endstep %}

{% step %}
### Charging Spots

Place charger spots on the map using `Config.ChargeCoords` in the configuration. Players can drop off their phones to charge, with the progress displayed until the battery is fully recharged.
{% endstep %}
{% endstepper %}

Example Spot Configuration:

```lua
Config.ChargeCoords = {
    {
        coords = vec3(1431.4039, -2009.6640, 61.3492),
        isAvailable = true,
        chargeSpeed = 3.0 -- +3 charge every 3 seconds
    }
}
```

***

## **Administrator battery command**

Admins can fully recharge a player's phone battery using the command `/chargePhone id`

This advanced battery system ensures seamless and realistic management of phone power, offering multiple ways to recharge and track usage.
