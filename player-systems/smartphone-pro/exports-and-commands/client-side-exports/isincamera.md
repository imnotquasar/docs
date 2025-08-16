# IsInCamera

The **IsInCamera** export allows you to check if the player is currently using the phone's camera. This can be used to manage HUD elements, such as disabling the map when the camera is active.

***

## How to Use

To check if the player is in the camera, use the following code:

```lua
local inCamera = exports['qs-smartphone-pro']:IsInCamera()

if inCamera then
    -- Disable map rendering or other HUD elements
    print("Player is using the camera.")
else
    -- Enable map rendering or restore HUD elements
    print("Player is not using the camera.")
end
```

This export returns `true` if the camera is active and `false` if it is not. Use it to dynamically adjust gameplay elements based on camera usage.
