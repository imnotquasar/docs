# setPedHair

The `setPedHair` export allows you to apply a complete hairstyle configuration to a ped, including the style index, texture variation, color, and highlight. If the ped is a freemode model, it also re-applies tattoos to ensure compatibility with hair variations that may hide or affect them.

***

## How to Use

To apply a hairstyle to a ped, use the following code:

```lua
local ped = PlayerPedId()
local hair = {
    style = 5,
    texture = 1,
    color = 2,
    highlight = 3
}

exports['qs-appearance']:setPedHair(ped, hair)
```

You may optionally provide tattoo data as a third argument:

```lua
exports['qs-appearance']:setPedHair(ped, hair, savedTattoos)
```

This export takes:

* `ped`: The ped entity to modify
* `hair`: A table with hairstyle settings:
  * `style`: Hair drawable index (component 2)
  * `texture`: Texture variation
  * `color`: Hair color ID
  * `highlight`: Highlight color ID
* `tattoos` (optional): Tattoo data to reapply after hair change

If the ped model is a freemode character, the function also calls `setTattoos`, preserving tattoo appearance across hairstyle changes.
