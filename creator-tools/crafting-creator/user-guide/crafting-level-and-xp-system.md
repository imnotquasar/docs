---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Crafting Level & XP System

The **Quasar Crafting Creator** includes a built-in progression system that allows players to gain experience (XP) every time they successfully craft an item. This XP system determines the player's crafting level, which can be used to unlock access to more advanced recipes as they progress.

***

## How Leveling Works

The leveling system is based on a **progressive multiplier**, meaning that each new level requires more XP than the previous one. By default, the system uses a 1.5x multiplier:

* Level 1 requires 100 XP
* Level 2 requires 150 XP
* Level 3 requires 225 XP
* And so on...

You can adjust the difficulty of progression with the following setting:

```lua
Config.LevelingDifficulty = 1.5
```

Raising this value will make each new level require significantly more XP.

***

## Player Starting Stats

When a player first joins the server, they will begin with a default level and zero XP:

```lua
Config.DefaultSkill = {
    level = 1,
    xp = 0
}
```

This defines the **baseline** for all players, unless you choose to sync levels with another system.

***

## Advanced Integration With Quasar Inventory

{% hint style="success" %}
This integration improves immersion and simplifies the player experience, avoiding multiple, confusing level systems.
{% endhint %}

If your server uses **Quasar Advanced Inventory**, you can **merge both systems into one shared level**. That means players will use a single leveling system across both crafting and inventory-related mechanics.

To enable this integration, simply set:

```lua
Config.UseAdvancedInventorySkill = true
```

When enabled, crafting XP and levels will be tracked through the inventory system, maintaining one consistent progression path for players.
