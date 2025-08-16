# getPedHair

The `getPedHair` export allows you to retrieve detailed information about a ped’s hairstyle, including the selected style, base color, highlight color, and texture variation. It’s ideal for storing or replicating custom hairstyles in character creation systems.

***

## How to Use

To get the hair data of a ped, use the following code:

```lua
local ped = PlayerPedId()
local hairData = exports['qs-appearance']:getPedHair(ped)

print("Hair Style:", hairData.style)
print("Hair Texture:", hairData.texture)
print("Hair Color:", hairData.color)
print("Highlight Color:", hairData.highlight)
```

This export returns a table with:

* `style`: Hair model index (drawable ID for slot 2)
* `texture`: Texture variation for the selected hair
* `color`: Primary hair color ID
* `highlight`: Secondary highlight color ID

This function ensures you can track and reapply exact hairstyles with full visual fidelity in any freemode ped customization workflow.
