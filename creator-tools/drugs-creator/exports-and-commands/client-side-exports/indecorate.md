# isDead (dead state)

The `LocalPlayer.state.dead` property allows you to check if the local player is currently dead. This is useful for restricting actions, disabling menus, or triggering custom logic when the player has died.

***

## How to Use

To check whether the player is dead, use the following code:

```lua
local isDead = LocalPlayer.state.dead
print("Is the player dead? " .. tostring(isDead))
```

This will return one of the following values:

* `"dead"` → The player is dead.
* `"lastStand"` → The player is in last stand mode (downed, not fully dead).
* `nil` → The player is alive.

You can then use this information to implement conditions.

***

## **Example**

```lua
if LocalPlayer.state.dead == "dead" then
    print("The player is completely dead, block actions here.")
elseif LocalPlayer.state.dead == "lastStand" then
    print("The player is in last stand mode, maybe allow help.")
else
    print("The player is alive and can interact normally.")
end
```
