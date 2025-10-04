# Create manual hospitals

Create or edit hospitals directly in `config`. Use this when you want to replace the default hospital, add multiple centers, or set up medical outposts with specific features.

***

## How it works (quick)

* Each hospital is one entry in `Config.Hospitals` (array).
* You define: zone, respawn point, blip, duty/stash/boss/wardrobe, check-in, shop, and garages.
* You can delete the default hospital and add yours. If you prefer placing them in-game, use the separate guide **“How to create hospitals.”**
* Standalone check-ins (without a full hospital) go in `Config.StandaloneHospitals`.

***

## Full commented example

Drop this in your config. Every line is commented so you know exactly what each field does.

```lua
---@type ConfigHospital[]
Config.Hospitals = {
    {
        id = 'pillbox',
        zone = {
            coords = vec3(320.04052734375, -591.7145385742188, 43.29180526733398),
            size = vec3(120.0),
        },
        coords = vec3(320.04052734375, -591.7145385742188, 43.29180526733398), -- General hospital coords. Using for zone.
        respawnPoint = {
            coords = vec4(315.4651489257813, -583.1113891601562, 43.28171920776367, 246.7841949462891),
            useCheckInInstead = true
        },
        blip = {
            enable = true,
            coords = vec3(320.04052734375, -591.7145385742188, 43.29180526733398),
            sprite = 61,
            color = 2,
            scale = 1.0,
            label = 'Pillbox Hospital'
        },
        duty = {
            enable = true,
            coords = vec3(305.3186340332031, -597.4736328125, 43.29183959960937),
            distance = 3.0
        },
        stash = {
            enable = true,
            coords = vec3(310.1644287109375, -599.5597534179688, 43.29182434082031),
            distance = 2.0
        },
        boss = {
            enable = true,
            coords = vec3(309.921142578125, -602.950927734375, 43.29182434082031),
            distance = 3.0
        },
        checkIn = {
            enable = true,
            ped = 's_m_m_doctor_01',
            coords = vec4(307.9654846191406, -588.1099853515625, 43.2918472290039 - 1.0, 155.0590362548828),
            distance = 50.0,
            cost = 3000,
            duration = 15 * 1000,
            maxOnDuty = 3,
            disableHospitalBeds = false,
            respawnNoBedCoords = vec4(316.66, -581.3, 43.28, 339.02),
            beds = {
                vec4(333.98287963867, -578.43774414062, 42.864631652832, 70.000022888184),
                vec4(326.90502929688, -576.34295654297, 42.877216339111 + 0.3, 340.00003051758),
                vec4(344.70373535156, -581.04907226562, 42.871894836426, 70.000022888184),
                vec4(349.42709350586, -583.51416015625, 42.871894836426, 340.00003051758)
            }
        },
        wardrobe = {
            enable = true,
            coords = vec4(298.780029296875, -599.7715454101562, 43.29206085205078, 341.15),
            distance = 3.0,
        },
        -- Shop only supporting in qs, qb and ps-inventory. For other inventories you can add them to the stores inside them. Each inventory has its own store.
        shop = {
            enable = true,
            ped = 's_m_m_doctor_01',
            animationDict = 'mini@strip_club@idles@bouncer@base',
            animationName = 'base',
            coords = vec4(316.68939208984375, -588.1437377929688, 43.29182434082031 - 1.0, 185.07872009277344),
            distance = 3.0,
            items = Config.CreatorDefaultItems
        },
        garage = {
            {
                menuCoords = vec3(295.0177917480469, -600.4273071289062, 43.3034439086914),
                distance = 5.0,
                spawnCoords = vec4(287.3741760253906, -611.8311157226562, 43.38404083251953, 70.00999450683594),
                vehicles = {
                    {
                        model = 'ambulance',
                        label = 'Ambulance',
                        grades = { 1, 2, 3 },
                    }
                }
            },
            {
                menuCoords = vec3(339.72088623046875, -588.82763671875, 74.16568756103516),
                distance = 5.0,
                spawnCoords = vec4(350.1439208984375, -587.94775390625, 74.16577911376953, 274.9385070800781),
                vehicles = {
                    {
                        model = 'polmav',
                        label = 'Maverick',
                        grades = { 1, 2, 3 },
                    }
                }
            }
        }
    }
}
```

***

## Standalone check-ins (no full hospital)

Turn on `EnableStandaloneHospitals` and add your outpost(s). Good for prisons, remote clinics, or temp triage points.

```lua
-- Enable standalone check-in points globally.
Config.EnableStandaloneHospitals = true

---@type HospitalInteractionCheckIn[]
Config.StandaloneHospitals = {
    {
        id = 'sandy',
        ped = 's_m_m_scientist_01',
        animationDict = 'mini@strip_club@idles@bouncer@base',
        animationName = 'base',
        coords = vec4(-1600.72265625, 5204.52587890625, 3.3, 23.65213012695312),
        distance = 5.0,
        cost = 5000,
        duration = 5000,            -- 5 second
        disableHospitalBeds = true, -- force respawn in respawnNoBedCoords. If you enable this, player will respawn in respawnNoBedCoords.
        respawnNoBedCoords = vec4(-1598.0526123046875, 5206.6220703125, 4.3100938796997, 295.98626708984375),
        beds = {}
    },
}
```

***

## Common pitfalls (read this)

* **Zone size**: If `size` is too small, UI texts/targets may not appear; if too large, prompts show outside the building. Test it.
* **Z offsets**: Peds sometimes float/sink. Adjust Z by ±0.3–1.0 until feet touch the floor.
* **Blip position**: Put it at the main entrance for player clarity.
* **Inventory support**: `shop` supports **qs/qb/ps** out of the box. Other inventories must add items in their own store system.
* **Removing default**: You can clear it with `Config.Hospitals = {}` and keep only your custom entries (or build them in-game via “How to create hospitals”).

***

## Quick checklist

* Set **id**, **coords**, **size**.
* Configure **respawnPoint** (or rely on **checkIn** if `useCheckInInstead = true`).
* Add **blip**, **duty**, **stash**, **boss**, **wardrobe** as needed.
* Configure **checkIn** (ped, cost/duration, beds).
* Configure **shop** (NPC + items) if you want an internal pharmacy.
* Add **garage** entries (ground/roof) with correct **spawnCoords**.
* _(Optional)_ Turn on **EnableStandaloneHospitals** and add outposts.
