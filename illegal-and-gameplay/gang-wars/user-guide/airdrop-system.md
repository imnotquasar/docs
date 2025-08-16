# Airdrop System

Here you will find all the configuration of the drop, remember that if you use Items instead of Weapons, you must set the Config.Weapons to false. In case of using an inventory without Items as weapons, you should use true.

{% stepper %}
{% step %}
### How to use the flare?

The revenge is an item that you can put in a store or drop system, when using said item the airdrop will occur.
{% endstep %}
{% endstepper %}

***

## Airdrop basic configuration <a href="#airdrop-basic-configuration" id="airdrop-basic-configuration"></a>

To use this system we must go to config.lua and we can add the item that we want in Config.FlareItem and with it we can call the plane that will bring a drop.

Just as we can configure the usable item, we can also configure the drop items.

```lua
Config.CooldownMinutes = 5         -- After requesting an Airdrop, this will be the cooldown minutes to request another for any player.
Config.PlaneArrivalTimeSecons = 10 -- Time it will take for the plane to arrive in seconds.
Config.FlareItem = 'tosti'         -- With this object you will call the plane.

Config.ItemCount = 1               -- Quantity of objects that the airdrop box will bring.
Config.ItemsDrop = {               -- Items that will fall in the airdrop.
    { Item = 'tosti',        count = 1 },
    { Item = 'water_bottle', count = 1 },
    -- { Item = 'example', count = 1 },
}

Config.Weapons      = false -- If you activate this, you will be able to choose weapons for the drops. If you use Quasar Inventory, leave this false, since weapons are objects.
Config.WeaponChance = 100   -- Chance of a weapon being airdropped.
Config.WeaponsDrop  = {     -- Weapons that will airdrop.
    { weapon = 'weapon_pistol',   ammo_count = 10 },
    { weapon = 'weapon_revolver', ammo_count = 20 },
    { weapon = 'weapon_microsmg', ammo_count = 50 },
    -- { weapon = 'example', ammo_count = 120 },
}
```
