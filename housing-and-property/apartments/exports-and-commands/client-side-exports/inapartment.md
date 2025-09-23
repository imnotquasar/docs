# inApartment

The **InApartment** export allows you to check if a player is currently inside an apartment. This is useful for managing or restricting specific actions while the player is inside their apartment.

***

## How to Use

To check whether the player is inside an apartment, use the following code:

```lua
local inApartment = exports['qs-housing']:InApartment()
print("Is the player inside an apartment? " .. tostring(inApartment))
```

This will return a boolean value (**true** or **false**) indicating whether the player is currently inside an apartment.\
You can then use this information to implement custom logic, such as restricting jobs, disabling certain actions, or triggering events only when the player is in their apartment.
