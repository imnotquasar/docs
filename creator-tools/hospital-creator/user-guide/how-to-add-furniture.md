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

{% hint style="warning" %}
For **compatibility**, the same items as _wasabi\_ambulance_ are used. If the **total level** exceeds **10**, it **can be fatal**.
{% endhint %}

| Item       | Name          | Duration (s) | Level |
| ---------- | ------------- | ------------ | ----- |
| morphine30 | Morphine 30MG | 120          | 9     |
| morphine15 | Morphine 15MG | 50           | 5     |
| perc30     | Percocet 30MG | 60           | 6     |
| perc10     | Percocet 10MG | 45           | 4     |
| perc5      | Percocet 5MG  | 30           | 2     |
| vic10      | Vicodin 10MG  | 40           | 3     |
| vic5       | Vicodin 5MG   | 20           | 2     |

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
