# ox\_inventory

This guide explains how to register a new **throwable item** in `ox_inventory`, such as a custom newspaper weapon called `WEAPON_ACIDPACKAGE`.

{% stepper %}
{% step %}
## Register The Item

**File:** Usually located in `data/items.lua` or your custom items definition file.

Add the following entry to the items list:

```lua
luaCopiarEditar['WEAPON_ACIDPACKAGE'] = {
    label = 'Newspaper',
    weight = 0,
    throwable = true,
}
```

> 🔁 You can adjust the `weight` value if needed. Setting it to `0` makes it weightless in the inventory.
{% endstep %}

{% step %}
## Add Icon To Inventory UI

Place your icon in the appropriate folder (commonly `web/images/` or `html/images/`) and make sure the file is named:

```
WEAPON_ACIDPACKAGE.png
```

> 🖼️ The filename must **exactly match** the item name, including capitalization.
{% endstep %}
{% endstepper %}
