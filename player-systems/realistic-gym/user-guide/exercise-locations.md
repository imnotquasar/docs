# Exercise Locations

Define and manage workout stations throughout your gym environment. Each exercise location corresponds to a specific activity and can be fully customized in position and orientation.

All locations are configured inside:

```lua
Config.ExerciseLocations
```

***

## Example Configuration

```lua
Config.ExerciseLocations = {
    -- Chin-up Bars
    {coords = vector3(-1200.08, -1571.15, 4.5), heading = 214.37, exercise = "chinups"},
    {coords = vector3(-1204.74, -1564.35, 4.5), heading = 38.83, exercise = "chinups"},
    
    -- Floor Exercises
    {coords = vector3(-1205.01, -1560.06, 4.5), heading = nil, exercise = "situps"},
    {coords = vector3(-1203.30, -1570.67, 4.5), heading = nil, exercise = "pushups"},
    
    -- Bench Press Stations (with activityCoord)
    {
        coords = vector3(-1201.55, -1562.81, 4.5), 
        heading = 125.29, 
        exercise = "bench", 
        activityCoord = vector4(-1200.64, -1562.11, 3.10, 125.29)
    },
    -- Additional benches...
    
    -- Barbell and Dumbbell Zones
    {coords = vector3(-1198.97, -1574.5, 4.5), heading = 215.48, exercise = "barbell"},
    {coords = vector3(-1202.6, -1572.78, 4.5), heading = 127.31, exercise = "dumbbells"}
}

```

These categories help users navigate job listings more easily.

***

## Location Structure

Each entry in the `ExerciseLocations` array represents a physical place where an exercise can be performed. You can place as many as you need, even across different interiors or MLOs.

### **🔹 Basic Properties**

<table><thead><tr><th width="185.3333740234375">Key</th><th>Description</th></tr></thead><tbody><tr><td><code>coords</code></td><td>The position where the player can start the exercise</td></tr><tr><td><code>heading</code></td><td>Direction the player faces while performing the action (can be <code>nil</code> for dynamic alignment)</td></tr><tr><td><code>exercise</code></td><td>The exercise type to trigger — must match a key from <code>Config.Exercises</code></td></tr></tbody></table>

### **🔸 Advanced Properties (Equipment-based)**

<table><thead><tr><th width="186">Key</th><th>Description</th></tr></thead><tbody><tr><td><code>activityCoord</code></td><td>Used for <strong>bench press</strong> or other exercises needing fine control of animation positioning</td></tr><tr><td><code>vector4</code></td><td>Includes <code>x, y, z, heading</code> to define the <strong>exact pose location</strong> for the animation and prop alignment</td></tr></tbody></table>

This is especially useful to prevent player clipping or misaligned equipment in tight gym environments.ts or interviews. With these tools, you can build a fully immersive and functional job market tailored to your server’s structure and RP depth.
