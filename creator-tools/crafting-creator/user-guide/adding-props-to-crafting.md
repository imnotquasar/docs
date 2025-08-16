# Adding Props To Crafting

To display 3D models of your crafted items directly on the table, **Quasar Crafting Creator** requires each item to have a defined prop (object model). These props are shown during the crafting process to enhance immersion and provide visual feedback.

{% hint style="success" %}
Recommendation: For full automation, proper icons, and prop handling, we **highly recommend using `qs-inventory`**. It's fully supported and works out of the box with Quasar Crafting Creator.
{% endhint %}

***

## Automatic Integration With qs-inventory

If you're using **qs-inventory** (standard, compact, or advanced), you're covered — item props are automatically retrieved from `items.lua`.

> No extra setup needed if you're on ESX or QBCore with `qs-inventory`.

***

## Manual Setup With Config.ObjectModels

If your inventory doesn't define props (or you want to override them), you can manually assign 3D models using this configuration section:

```lua
Config.ObjectModels = {
    ['pistol_ammo'] = joaat('prop_ld_ammo_pack_01'),
    ['rifle_ammo'] = joaat('prop_ld_ammo_pack_02'),
    ['id_card'] = joaat('p_ld_id_card_01'),
    ['black_weapontint'] = joaat('prop_cs_spray_can'),
    ['digital_weapontint'] = joaat('prop_paint_spray01b'),
    -- Add more items here as needed
}
```

Each key is the item name, and the value is the object’s `joaat` hash.

***

## Adjusting Prop Position

If a prop appears misaligned (e.g., floating or clipping), you can adjust its position using `Config.CustomObjectModelOffsets`.

```lua
Config.CustomObjectModelOffsets = {
    [joaat('prop_tool_jackham')] = vec3(0.0, 0.0, 1.0),
    [joaat('prop_cs_petrol_can')] = vec3(0.0, 0.0, 1.3),
    [joaat('prop_tool_box_04')] = vec3(0.0, 0.0, 1.35)
}
```

This allows you to lift, lower, or shift the object precisely on the table.
