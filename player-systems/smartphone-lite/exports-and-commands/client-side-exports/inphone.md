# InPhone

The **InPhone** export checks if the phone is currently open. This is useful to prevent interactions with other menus or actions while the phone is being used.

***

## How to Use

To check if the phone is open, use the following code:

```lua
local isPhoneOpen = exports['qs-smartphone']:InPhone()
if isPhoneOpen then
    print("The phone is currently open.")
else
    print("The phone is not open.")
end
```

This helps ensure that other UI elements or commands do not interfere with the phone's functionality.
