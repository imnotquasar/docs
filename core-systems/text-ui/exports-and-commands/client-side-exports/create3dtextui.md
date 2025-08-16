# create3DTextUI

Quasar Text UI allows you to create floating text at specific locations in the world. This is useful for **roleplay interactions, markers, or guiding players** without using outdated DrawText3D systems.

***

## **How to Use**

To use **classic coordinate-based text UI**, simply place this code at the **top of your client-side script**:

```lua
-- Put this on top of your client-side script, no additional setup needed!
exports['qs-textui']:create3DTextUI("test", {
    coords = vector3(-1461.18, -31.48, 54.63),
    displayDist = 6.0,
    interactDist = 2.0,
    enableKeyClick = true, -- Enables key interaction
    keyNum = 38, -- Key code for interaction (E)
    key = "E",
    text = "Test",
    triggerData = {
        triggerName = "",
        args = {}
    }
})

```

***

## Example:

Imagine a **shop NPC** where players can press "E" to interact:

```lua
exports['qs-textui']:create3DTextUI("shop", {
    coords = vector3(25.7, -1346.58, 29.49),
    displayDist = 5.0,
    interactDist = 1.5,
    enableKeyClick = true,
    keyNum = 38,
    key = "E",
    text = "Press E to open the shop",
    triggerData = {
        triggerName = "qb-shops:client:openShop",
        args = {}
    }
})
```

This will **display floating text** and allow players to **press "E"** to open the shop!
