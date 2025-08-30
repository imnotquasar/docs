# Bandage healing system

The **Bandage system** lets players use bandages to heal themselves and optionally stop bleeding without EMS intervention. This gives roleplay flexibility for minor injuries while keeping serious trauma under medical control.

***

## How It Works

Bandages are configured as follows:

```lua
Config.BandageItem = {
    enable = true,          -- Enable bandage usage
    item = 'bandage',       -- The item name in your inventory
    regeneration = 50,      -- % of health restored
    healBleed = false,      -- Stop bleeding? (true = yes, false = no)
    duration = 7 * 1000     -- Time required to apply bandage (7 seconds)
}
```

* **Enable** → Activates or deactivates the bandage system.
* **Item** → Defines which inventory item will act as a bandage.
* **Regeneration** → Amount of health restored (percentage).
* **HealBleed** → Determines if a bandage can **stop bleeding**. If `false`, only EMS can treat bleeding wounds.
* **Duration** → How long the player must wait while applying the bandage.

***

## Example Use Case

* A player lightly injured in a fight can use a **bandage** to restore up to **50% health**.
* If **HealBleed = true**, it will also stop bleeding (for example, from a gunshot wound).
* If **HealBleed = false**, the bandage restores health but does not stop bleeding — the player must still see a medic.

{% hint style="warning" %}
For balance, it’s recommended to keep **HealBleed = false**, so EMS still plays a critical role in treating serious injuries.
{% endhint %}
