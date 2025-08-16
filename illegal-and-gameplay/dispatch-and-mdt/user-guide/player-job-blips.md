# Player Job Blips

{% hint style="info" %}
In the config.lua file you will find everything that has to do with the player and blips system. Make use of this configuration by reading all the comments.
{% endhint %}

With Quasar Dispatch & MDT we have an advanced blip system that you will see on your map where all the workers of your current job will be, here you will learn how to manage said system.

***

## Basic Job Blips Configuration

In this setting, you can enable or disable blips for players depending on their job. You can also adjust the color, sprite and scale of the blips for each job.

You can set different blips and change the sprite for each one.

```lua
Config.JobsBlips = {              -- Blips for players depending on their job
    ['police'] = {                --JOB
        show = true,              -- Enable or disable
        color = 38,               -- Color
        sprite = {
            ['walking'] = 1,      -- Sprite
            ['automobile'] = 225, -- sprite
            ['bike'] = 559,       -- sprite
            ['boat'] = 404,       -- sprite
            ['heli'] = 422,       -- sprite
            ['plane'] = 307,      -- sprite
        },
        showJobs = {
            'ambulance' -- need Exist Blip config in this section
        },
        scale = 1.0,    -- Scale
        showConeOfView = true,
    },
    ['ambulance'] = {             --JOB
        show = true,              -- Enable or disable
        color = 66,               -- Color
        sprite = {
            ['walking'] = 1,      -- Sprite
            ['automobile'] = 225, -- sprite
            ['bike'] = 559,       -- sprite
            ['boat'] = 404,       -- sprite
            ['heli'] = 422,       -- sprite
            ['plane'] = 307,      -- sprite
        },
        showJobs = {
            'police' -- need Exist Blip config in this section
        },
        scale = 1.0, -- Scale
        showConeOfView = false,
    },
    ['mechanic'] = {              --JOB
        show = true,              -- Enable or disable
        color = 43,               -- Color
        sprite = {
            ['walking'] = 1,      -- Sprite
            ['automobile'] = 225, -- sprite
            ['bike'] = 559,       -- sprite
            ['boat'] = 404,       -- sprite
            ['heli'] = 422,       -- sprite
            ['plane'] = 307,      -- sprite
        },
        showJobs = {
            -- 'police' -- cant view other job blips
        },
        scale = 1.0, -- Scale
        showConeOfView = false,
    },
}
```
