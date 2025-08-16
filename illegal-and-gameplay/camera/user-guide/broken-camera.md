# Broken Camera

The Quasar Camera includes a dynamic broken camera system, adding a layer of unpredictability and challenge to photography. This system introduces a chance for the camera to break while taking photos, creating a spark effect. You can customize the breakage mechanics to suit your gameplay preferences.

In the configuration, you can enable or disable the broken camera feature and adjust the percentage chance for the camera to break. Additionally, you can decide whether the camera breaking will cause damage to the player.

{% stepper %}
{% step %}
### Config.CameraBroken

Enables the camera breakage feature.
{% endstep %}

{% step %}
### Config.CameraBrokenChance

Sets the probability of breakage, from 1 to 100%. The default is 10%, meaning a 10% chance of breaking per photo.
{% endstep %}

{% step %}
### Config.CameraBrokenDamage

If enabled, the player will take 20 HP damage when the camera breaks, accompanied by a spark effect.
{% endstep %}
{% endstepper %}

```lua
Config.CameraBroken = true -- If you want the camera to break, use this
Config.CameraBrokenChance = 10 -- Percentage of camera breakage, from 1 to 100% (default 10 = 10%)
Config.CameraBrokenDamage = false -- When the chamber breaks, it makes a spark that removes 20 HP
```

This system introduces a new level of immersion and realism, encouraging players to use their cameras carefully to avoid breakage.
