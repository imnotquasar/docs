# Exercise Configuration

This section details how each exercise is structured and how you can customize animations, props, stat gains, and more to match your server's fitness system.

***

## Available Exercises

The gym includes six fully animated and configurable workout types, split into two categories:

### **🏃‍♂️ Bodyweight Exercises**

These do not require props and are based on character animations:

* **Push-ups** (`pushups`) – Improves upper body strength and stamina
* **Sit-ups** (`situps`) – Focuses on core strength and stamina
* **Chin-ups** (`chinups`) – Targets upper body and grip strength

### **🏋️‍♀️ Weight Training**

These exercises include props and are based on heavy training:

* **Bench Press** (`bench`) – Uses a bench with barbell prop
* **Barbell Curls** (`barbell`) – Standing weightlifting using a curl bar
* **Dumbbells** (`dumbbells`) – Dual-hand lifting for isolated strength training

***

## Exercise Structure

Each exercise follows a modular structure for configuration. Here's a full example for a **bodyweight exercise**:

```lua
["pushups"] = {
    label = "LABEL_PUSHUPS", -- Localized display name
    stamina = {min = 1, max = 3}, -- Stamina gain per repetition
    strength = {min = 2, max = 4}, -- Strength gain per repetition

    -- Animation Sequences
    idleDict = "amb@world_human_push_ups@male@idle_a",
    idleAnim = "idle_c",
    actionDict = "amb@world_human_push_ups@male@base",
    actionAnim = "base",
    actionTime = 1100, -- Duration per action (ms)

    -- Entry/Exit Animations
    enterDict = "amb@world_human_push_ups@male@enter",
    enterAnim = "enter",
    enterTime = 3050,
    exitDict = "amb@world_human_push_ups@male@exit",
    exitAnim = "exit",
    exitTime = 3400,

    -- Progression Configuration
    actionProcent = 1, -- Progress bar gain per action
    actionProcentTimes = 20, -- Total actions to complete the exercise
    frozen = false -- Should the player be frozen during the animation?
}
```

***

## Prop-Based Exercises

For exercises that require a **single prop**, like the bench press:

```lua
["bench"] = {
    label = "LABEL_BENCH",
    stamina = {min = 2, max = 4},
    strength = {min = 3, max = 5},
    
    -- Prop Configuration
    prop = "prop_barbell_60kg", -- Barbell model
    propAttachment = {
        bone = 28422, -- Right hand
        x = 0.0, y = 0.0, z = 0.0,
        xRot = 0.0, yRot = 0.0, zRot = 0.0
    },

    frozen = false
}
```

***

## Dual-Prop Exercises

For exercises using **two props**, like dumbbells:

```lua
["dumbbells"] = {
    label = "LABEL_DUMBBELLS",
    stamina = {min = 1, max = 2},
    strength = {min = 1, max = 2},
    
    -- Main Prop (Right Hand)
    prop = "prop_barbell_01",
    propAttachment = {
        bone = 28422,
        x = -0.24, y = 0.0, z = -0.03,
        xRot = 0.0, yRot = -50.0, zRot = 0.0
    },

    -- Secondary Prop (Left Hand)
    prop2 = {
        name = "prop_barbell_01",
        attachBone = 60309, -- Left hand
        placement = {0.05, 0.0, 0.0, 0.0, -90.0, 120.0}
    },

    frozen = false
}
```

***

## Stat Gains Overview

Each exercise increases stamina and strength within defined ranges:

| Exercise    | Stamina Gain | Strength Gain | Focus Area       |
| ----------- | ------------ | ------------- | ---------------- |
| Push-ups    | 1–3          | 2–4           | Upper Body       |
| Sit-ups     | 2–4          | 1–2           | Core / Endurance |
| Chin-ups    | 1–2          | 3–5           | Grip / Arms      |
| Bench Press | 2–4          | 3–5           | Chest / Arms     |
| Barbell     | 2–3          | 2–3           | Full Body        |
| Dumbbells   | 1–2          | 1–2           | Isolation / Arms |

These values are fully editable, letting you rebalance exercises for realism, progression, or custom RPG systems.
