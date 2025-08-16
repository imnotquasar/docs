# GetPlayerPhone

The **GetPlayerPhone** export retrieves the phone number of a specified player using their source ID. This is useful for scripts that need to access or display a player's phone number programmatically.

***

## How to Use

To get a player's phone number, pass their source ID to the export:

```lua
-- Replace 'playerSource' with the target player's source ID
local phoneNumber = exports['qs-base']:GetPlayerPhone(playerSource)
print("Player's phone number: " .. phoneNumber)
```

This export is ideal for creating features like contact-sharing systems or admin tools that require a player's phone number.
