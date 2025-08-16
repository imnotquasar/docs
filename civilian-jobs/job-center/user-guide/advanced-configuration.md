# Advanced Configuration

This section covers optional yet powerful features you can use to further enhance your job system within **Quasar Job Center**. These tools allow for greater flexibility, dynamic content, and immersive roleplay experiences.

***

## Custom Status Badges

You can display **custom status labels** on job cards to grab players' attention or convey special conditions.

```lua
status = "🔥 Hot Jobs"       -- Use emojis for high-visibility roles
status = "NEW HIRING"        -- Highlight newly added positions
status = "URGENT"            -- Indicate critical staffing needs
status = "PART TIME"         -- Clarify job type or schedule
```

These badges appear on the top-right corner of job cards in the UI.

***

## Multi-Location Jobs

If a job role is associated with more than one location (e.g., a delivery company with several depots), you can define **multiple GPS waypoints**:

```lua
locations = {
    {
        name = "Main Office",
        coords = vector3(100.0, -100.0, 30.0)
    },
    {
        name = "Branch Office", 
        coords = vector3(150.0, -150.0, 30.0)
    }
}
```

Each location will be selectable by the player when they click **"Get Location"** on the job card.

***

## Job Requirements Templates

To avoid repeating the same requirements in multiple jobs, you can define reusable templates in your configuration:

```lua
local basicRequirements = {
    "Valid ID",
    "Clean background check",
    "Reliable transportation"
}

local professionalRequirements = {
    "College degree",
    "Professional references",
    "Industry certification",
    "5+ years experience"
}
```

You can then inject these into jobs like so:

```lua
requirements = professionalRequirements
```

This approach keeps your config clean and consistent, especially for large servers with dozens of job listings.
