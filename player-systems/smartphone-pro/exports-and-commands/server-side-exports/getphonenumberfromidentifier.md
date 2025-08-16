# GetPhoneNumberFromIdentifier

The **GetPhoneNumberFromIdentifier** export allows you to retrieve a player's phone number based on their identifier. It prioritizes the phone the player has used most recently, or if unused, retrieves any phone from their inventory.

***

## How to Use

To get a player's phone number, use the following code:

```lua
local identifier = "player-identifier" -- Replace with a valid player identifier
local mustBePhoneOwner = true -- Ensures the phone belongs to the identifier (e.g., prevents using stolen phones)

local phoneNumber = exports['qs-smartphone-pro']:GetPhoneNumberFromIdentifier(identifier, mustBePhoneOwner)

if phoneNumber then
    print("Player's phone number: " .. phoneNumber)
else
    print("No phone number found for this identifier.")
end
```

## Parameters

* **identifier**: The player's unique identifier, such as `ESX.GetPlayerFromId(source).identifier`.
* **owner**: A boolean (`true` or `false`). If `true`, it ensures the phone number belongs to the identifier (useful for handling stolen phones).

This export is particularly useful for verifying ownership or retrieving contact details dynamically. It returns the phone number as a string or `false` if no phone number is found.
