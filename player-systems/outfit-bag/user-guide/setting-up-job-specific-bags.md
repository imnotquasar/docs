# Setting Up Job-Specific Bags

Create default outfit bags that are only accessible to specific jobs or roles. Ideal for police departments, medical staff, gangs, or any whitelisted faction.

***

## Job-Restricted Configuration

Define a default bag limited to one or more jobs:

```lua
{
    pos = vector3(x, y, z), -- World location of the bag
    jobs = { "police", "sheriff" }, -- List of allowed job names
    public = false, -- Must be false to restrict to jobs
    outfits = {
        {
            name = "Sheriff Uniform",
            data = {
                ['arms'] = {item = 30, texture = 0},
                ['t-shirt'] = {item = 15, texture = 0},
                ['torso2'] = {item = 55, texture = 0},
                ['pants'] = {item = 35, texture = 0},
                ['shoes'] = {item = 25, texture = 0},
                ['hat'] = {item = 46, texture = 0}
            }
        }
        -- Add more outfits if needed
    }
}
```

***

## Notes

* Set `public = false` to ensure only the listed jobs can access the bag.
* You can define multiple jobs per bag using the `jobs` array.
* This setup is useful for creating immersive faction outfit systems.
