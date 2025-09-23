# getClosestVan

The **getClosestVan** export allows you to check if a player is currently near a van (motorhome). This is useful for detecting proximity to specific vehicles and triggering related actions.

***

## **How to Use**

To check whether the player is near a van, use the following code:

```lua
local closestVan = exports['qs-housing']:getClosestVan()
print("Is the player near a van? " .. tostring(closestVan))
```

This will return a boolean value (**true** or **false**) indicating whether the player is currently near a van.\
You can then use this information to implement custom logic, such as opening an interaction menu, restricting actions, or triggering events when the player approaches a motorhome.
