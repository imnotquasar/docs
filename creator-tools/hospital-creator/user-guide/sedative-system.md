# Sedative system

The Sedative System allows medics to temporarily sedate a player using the **Sedate** option from the ambulance menu. This feature is designed to simulate real emergency scenarios where a patient must be calmed or immobilized for treatment.

***

## How It Works

When the medic uses the **Sedate** option, the target player is sedated for a period of time defined in the configuration. The sedation effect can be removed early by using the **Sedate** option again on the same player.

* Setting the duration too high may frustrate players, so choose balanced values (e.g., 5–10 minutes) to maintain realism without breaking gameplay.
* Sedation consumes the configured item (e.g., `sedative`) if `remove = true`.

***

## Configuration Example

```lua
Config.AmbulanceItems = {
    revive = {
        item = 'defib',
        label = 'Defibrillator',
        remove = false -- remove item after use
    },
    heal = {
        item = 'medikit',
        label = 'Medikit',
        duration = 1000,
        healBleed = true,
        remove = true
    },
    sedate = {
        item = 'sedative',
        label = 'Sedative',
        duration = 8 * 60000,
        remove = true
    },
    medbag = {
        enable = true,
        item = 'medbag',
        label = 'Med Bag',
        remove = true
    }
}
```

***

## Effects

* **Sedated Player** → The player cannot act normally until the sedation timer ends.
* **Re-using Sedate** → If the medic applies sedation again while the player is sedated, it will remove the effect instead of stacking.
* **Item Consumption** → The configured sedative item will be removed if `remove = true`.
