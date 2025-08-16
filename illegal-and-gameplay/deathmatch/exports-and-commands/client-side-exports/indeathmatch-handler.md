# inDeathmatch Handler

The `deathmatch:inDeathmatch` event is used to track a player's current state in a Deathmatch session. This allows you to update and manage a local variable (`inDeathmatch`) to reflect whether the player is currently participating in a Deathmatch.

***

## How to Use

To track the player's Deathmatch state, use the following code:

```lua
local inDeathmatch = false
AddEventHandler('deathmatch:inDeathmatch', function(state)
    inDeathmatch = state
end)
```

## Explanation

* `inDeathmatch`: A local boolean variable initialized as `false`.
* `AddEventHandler`: Listens for the `deathmatch:inDeathmatch` event.
* `state`: The parameter passed with the event, indicating the player's current Deathmatch status (`true` if in Deathmatch, `false` otherwise).
* When the event is triggered, the `state` value updates the `inDeathmatch` variable, allowing you to track the player's status in real-time.

You can then use the `inDeathmatch` variable in your code to control or restrict actions based on whether the player is actively in a Deathmatch session. For example:

```lua
if inDeathmatch then
    print("Player is in a Deathmatch session.")
else
    print("Player is not in a Deathmatch session.")
end
```
