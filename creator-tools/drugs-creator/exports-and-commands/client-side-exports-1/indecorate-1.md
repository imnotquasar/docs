# revivePlayer

The `ambulance:revivePlayer` event allows you to instantly revive a player. This is useful for scripts that need to bring a player back to life after death without using the standard hospital or respawn flow.

***

## How to Use

To revive a player from the server side, use:

```lua
TriggerClientEvent('ambulance:revivePlayer', source)
```

This will revive the player referenced by `source`.

***

## The healPlayer export

The `ambulance:healPlayer` event allows you to heal a player. It includes two configurable parameters for more control:

* **First parameter (boolean – full heal)**:
  * `true` → The player will be fully healed, their treatment will be cleared, and they will also be revived if dead.
  * `false` → Only partial healing will be applied.
* **Second parameter (boolean – disable notification)**:
  * `true` → The healing process will not show a notification to the player.
  * `false` → A healing notification will be shown.

***

## **How to Use**

To fully heal and revive a player without showing notifications:

```lua
TriggerClientEvent('ambulance:healPlayer', source, true, true)
```

To heal a player but still show a notification:

```lua
TriggerClientEvent('ambulance:healPlayer', source, true, false)
```
