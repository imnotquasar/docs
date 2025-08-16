# getCurrentHouse

The `getCurrentHouse` export allows you to retrieve the identifier of the house the player is currently inside. This is useful for managing house-specific features, such as editing or interacting with the house's interior.

***

## How to Use

To get the current house the player is in, you can use the following code:

```lua
luaCopiarEditarlocal currentHouse = exports['qs-housing']:getCurrentHouse()
if currentHouse then
    print("Player is in house: " .. currentHouse)
else
    print("Player is not inside any house.")
end
```

This export will return the identifier of the current house if the player is inside one, or `nil` if the player is not in any house. You can utilize this for custom scripts or house-related actions.
