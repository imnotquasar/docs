# getPedProps

The `getPedProps` export allows you to retrieve all prop accessories currently applied to a given ped. This includes elements like hats, glasses, watches, and more. It is useful for saving or analyzing player props when managing appearance systems.

***

## How to Use

To get the props of a ped, use the following code:

```lua
local ped = PlayerPedId()
local props = exports['qs-appearance']:getPedProps(ped)

for i, prop in pairs(props) do
    print("Prop ID:", prop.prop_id)
    print("Drawable:", prop.drawable)
    print("Texture:", prop.texture)
end
```

This function returns a table where each entry includes:

* `prop_id`: The identifier for the prop slot (e.g., hat, glasses)
* `drawable`: The model variation index for that prop
* `texture`: The texture variation for that prop

It loops through all predefined prop slots, ensuring accurate and complete data for character customization or syncing purposes.
