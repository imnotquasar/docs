# Bleeding system

The **Bleeding System** controls how quickly a player loses blood depending on the type of injury they’ve received. This adds a realistic layer of urgency to medical roleplay, as some wounds are far more dangerous than others.

***

## How It Works

{% hint style="warning" %}
Setting a multiplier too high will make players die extremely fast. Use balanced values (e.g., `2`) to keep the system realistic but not frustrating.
{% endhint %}

Each injury type has a **multiplier** that affects blood loss speed:

```lua
Config.BleedMultiplier = {
    shot = 2,    -- Blood loss rate multiplier when shot (2x faster)
    stabbed = 2, -- Blood loss rate multiplier when stabbed (2x faster)
    beat = 0,    -- No blood loss for beat wounds
    burned = 0,  -- No blood loss for burn wounds
}
```

* **Shot (Gunshot wounds)** → Players bleed out **twice as fast**.
* **Stabbed (Knife wounds)** → Players also bleed out **twice as fast**.
* **Beat (Blunt trauma)** → No blood loss.
* **Burned (Burn injuries)** → No blood loss.
