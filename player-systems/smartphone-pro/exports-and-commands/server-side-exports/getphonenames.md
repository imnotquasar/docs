# getPhoneNames

The **getPhoneNames** export allows you to retrieve a list of all available phone names in the system. This is useful for managing or displaying phone options dynamically.

***

## How to Use

To get a list of phone names, use the following code:

```lua
local phoneNames = exports['qs-smartphone-pro']:getPhoneNames()

for _, phone in pairs(phoneNames) do
    print("Phone Name: " .. phone)
end
```

This export returns a table containing all phone names. You can iterate through this table to display or manage the available phones as needed.
