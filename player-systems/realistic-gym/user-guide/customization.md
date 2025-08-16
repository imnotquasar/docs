# Customization

This section covers basic customization options that allow you to fine-tune the gym experience to fit your server’s style, difficulty, and player expectations.

All values are located in:

```lua
shared/config.lua
```

***

## Membership Pricing

You can adjust how much players must pay to access the gym:

```lua
Config.MembershipPrice = 5000 -- Increase membership cost
```

This value can be changed to reflect your server’s economy or to encourage long-term commitment.

***

### Stats HUD Key

Modify which key opens the player's fitness stats display:

```lua
Config.StatsHUDKey = "F9" -- Change from default F10 to F9
```

Make sure this key doesn't conflict with other systems on your server.

***

### Exercise UI Position

Adjust where the on-screen exercise interface appears:

```lua
Config.ExerciseUIPosition = "right" -- Moves UI to right side of the screen
```

Options: `"left"` or `"right"` — ideal for preventing overlaps with other HUD elements.

***

### Stat Decay System

Change when and how much fitness stats decrease automatically:

```lua
Config.StatDecay = {
    enabled = true,
    hour = 6, -- Switch to 6:00 AM daily reset
    minute = 30, -- Run stat decay at 6:30 AM
    amount = 3 -- Reduce stat loss to 3 points
}
```

This system encourages regular gym visits while maintaining balance. You can disable it completely by setting `enabled = false`.
