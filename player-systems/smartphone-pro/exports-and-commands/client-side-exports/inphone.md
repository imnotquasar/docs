# InPhone

The **InPhone** export allows you to check whether the player currently has their phone open. This is particularly useful for preventing conflicts with other menus or actions while the phone is in use.

***

## How to Use

To check if the phone is open, you can use the following code:

```lua
local isUsingPhone = exports['qs-smartphone-pro']:InPhone()
if isUsingPhone then
    print("The phone is currently open.")
else
    print("The phone is not open.")
end
```

This will return `true` if the phone is open and `false` if it is not. You can use this to manage logic for menus or actions that should not overlap with phone usage.
