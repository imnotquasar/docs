# hasEmailAccount

The **hasEmailAccount** export checks if a player is logged into the Mail app and returns a boolean value (`true` or `false`). This can be used to verify if the player has an active email account in the app.

***

## How to Use

To check if a player is logged into the Mail app, use the following code:

```lua
local source = playerSource -- Replace with the player's source ID

local isLoggedIn = exports['qs-smartphone-pro']:hasEmailAccount(source)

if isLoggedIn then
    print("Player is logged into the Mail app.")
else
    print("Player is not logged into the Mail app.")
end
```

## Parameters

* **source**: The player's source ID.

This export is useful for implementing logic that requires players to be logged into their email account, such as receiving mail or sending messages. It ensures functionality is tied to the player's active email status.
