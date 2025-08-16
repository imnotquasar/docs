# CheckSignal

The **CheckSignal** export lets you determine whether the phone currently has a signal. It returns a boolean value: `true` if there is signal and `false` if there isn't.

***

## How to Use

To check the phone's signal status on the client side, use the following code:

```lua
local hasSignal = exports['qs-smartphone']:CheckSignal()
if hasSignal then
    print("Phone has signal.")
else
    print("No signal on the phone.")
end
```

This can be used to control features like app access or message sending based on signal availability.
