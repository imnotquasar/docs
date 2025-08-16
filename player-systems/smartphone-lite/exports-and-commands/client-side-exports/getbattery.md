# getBattery

The **getBattery** export allows you to retrieve the current battery level of the phone. This is useful for checking the battery status programmatically within your scripts.

***

## How to Use

To get the battery value on the client side, you can use the following code:

```lua
local batteryLevel = exports['qs-smartphone']:getBattery()
print("Current battery level: " .. batteryLevel)
```

This will return a numeric value representing the phone's current battery percentage. You can then use this value for custom logic, such as triggering low battery warnings or managing app behavior.
