# ToggleHud

The `ToggleHud` export from **qs-interface** allows you to toggle the visibility of the HUD (Heads-Up Display) for a player. This can be useful for hiding or showing interface elements depending on the situation or context in the game.

***

## **How to Use**

To toggle the HUD visibility, use the following code:

```lua
local hudVisible = true -- Set to true to show, false to hide
exports['qs-interface']:ToggleHud(hudVisible)
```

In this example, setting `hudVisible` to **true** will display the HUD, while setting it to **false** will hide it. You can change the `hudVisible` value dynamically depending on the context or player actions.

This export allows you to control when the HUD is visible or not, giving you flexibility in managing the player's interface experience in your scripts.
