# Pain pills system

The **Pain Pills system** provides a way to temporarily reduce pain and the effects of severe injuries. When a pill is taken, a **stackable effect** is applied with a defined **duration** and **level** of strength. It does not heal wounds: it only reduces pain, allowing the player to move and function while awaiting proper treatment or evacuation.

***

## How It Works

{% stepper %}
{% step %}
### Intake

When using a valid pill item, an animation plays and a dose is registered with its `label`, `duration` (in seconds), and `level` (strength).
{% endstep %}

{% step %}
### Stacking

Multiple pills can **combine their levels and durations**. The system recalculates the **total level** and applies the corresponding effect.
{% endstep %}

{% step %}
### Fading

Every second, all active doses lose duration. When a dose reaches 0, it is removed. If no doses remain, the effects are cleared.
{% endstep %}

{% step %}
### Internal State

While any doses are active, the player is marked as **under painkillers**; once they expire, the state and effects are automatically removed.
{% endstep %}
{% endstepper %}

***

## What It Does and Doesn’t Do

* ✅ **Reduces pain** and allows more normal movement and interaction.
* ✅ **Can be stacked**: multiple pills add up to increase total level and extend duration.
* ❌ **Does not heal injuries**: you must still use _Diagnose_ and treat each body part with the correct medical item.

***

## Default Pills

```lua
Config.MedicalSystem = {
    enable = true,
    items = {
        -- Pain Relief Medications
        {
            item = 'painkiller',
            label = 'Painkiller',
            duration = 20000,        -- 20 seconds
            effects = {
                reduce_bruising = 2, -- Reduces bruising level by 2
                reduce_burning = 1,  -- Reduces burning level by 1
                screen_blur = true,  -- Adds slight blur effect
                movement_slow = 0.9  -- 90% movement speed
            }
        },
        {
            item = 'morphine',
            label = 'Morphine',
            duration = 60000,        -- 60 seconds
            effects = {
                reduce_bruising = 4, -- Removes all bruising
                reduce_burning = 3,  -- Reduces burning significantly
                reduce_bleeding = 1, -- Slightly reduces bleeding
                screen_blur = true,
                screen_distortion = true,
                movement_slow = 0.7,  -- 70% movement speed
                weapon_accuracy = 0.5 -- 50% weapon accuracy
            }
        },

        {
            item = 'hemostatic_agent',
            label = 'Hemostatic Agent',
            duration = 12000,             -- 12 seconds
            effects = {
                reduce_bleeding = 3,      -- Reduces bleeding by 3 levels
                stop_bleeding_chance = 80 -- 80% chance to stop bleeding completely
            }
        },

        -- Burn Treatment
        {
            item = 'burn_gel',
            label = 'Burn Treatment Gel',
            duration = 24000,          -- 24 seconds
            effects = {
                reduce_burning = 2,    -- Reduces burning by 2 levels
                cooling_effect = true, -- Visual cooling effect
                pain_reduction = 0.5   -- 50% less burn pain
            }
        },

        -- Stimulants
        {
            item = 'adrenaline',
            label = 'Adrenaline Shot',
            duration = 18000,          -- 18 seconds
            effects = {
                movement_boost = 1.3,  -- 130% movement speed
                weapon_accuracy = 1.2, -- 120% weapon accuracy
                health_regen = true,   -- Gradual health regeneration
                screen_shake = true,   -- Adrenaline shake effect
                heart_rate_increase = true
            }
        },

        -- Antibiotics
        {
            item = 'antibiotic',
            label = 'Antibiotic',
            duration = 90000, -- 90 seconds
            effects = {
                prevent_infection = true,
                slow_healing = true,
                immunity_boost = 0.2 -- 20% damage resistance
            }
        },

        -- Emergency Medications
        {
            item = 'epinephrine',
            label = 'Epinephrine Auto-Injector',
            duration = 30000,           -- 30 seconds
            effects = {
                instant_health = 50,    -- Instant health boost
                reduce_all_effects = 1, -- Reduces all damage types by 1
                movement_boost = 1.1,
                weapon_accuracy = 1.1,
                screen_flash = true -- Emergency injection flash
            }
        },

        -- Sedatives
        {
            item = 'self_sedative',
            label = 'Self Sedative',
            duration = 45000, -- 45 seconds
            effects = {
                reduce_bruising = 3,
                reduce_burning = 2,
                movement_slow = 0.6,   -- 60% movement speed
                weapon_accuracy = 0.3, -- 30% weapon accuracy
                screen_blur = true,
                drowsiness = true
            }
        }
    }
}
```

***

## Usage Tips

* Start with **lower doses** (e.g., `perc5` or `vic5`) and **evaluate** if a stronger dose is required.
* Avoid combining multiple strong pills in a short period (e.g., `morphine30` + `perc30`) unless absolutely necessary.
* Remember: pain pills are a **temporary support** to stabilize the patient — they do not replace proper body-part treatments.

***

## Configuration

* Enable/disable the system with `Config.EnablePainPills`.
* Adjust durations and strength levels inside `Config.PainPills`.
* Keep the **practical cap** below 10 to avoid accidental overdoses on your server.
