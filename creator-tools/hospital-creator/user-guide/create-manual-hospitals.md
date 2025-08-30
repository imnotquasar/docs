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
        -- Unique identifier used internally (no spaces).
        id = 'pillbox',

        -- (Optional) Zone info used to detect you're inside hospital area.
        zone = {
            -- Center of the hospital zone (x, y, z).
            coords = vec3(320.0405, -591.7145, 43.2918),
        },

        -- General reference coords for this hospital (also used by zone helpers).
        coords = vec3(320.0405, -591.7145, 43.2918),

        -- Size of the zone box (x, y, z). Too small = drawtexts may not show; too big = shows too far.
        size = vec3(120.0),

        -- Main respawn configuration.
        respawnPoint = {
            -- Where players respawn when revived/processed (x, y, z, heading).
            coords = vec4(315.4651, -583.1114, 43.2817, 246.7842),

            -- true = use Check-In flow instead of hard respawn point when possible.
            useCheckInInstead = true
        },

        -- Map blip settings for the hospital.
        blip = {
            enable = true,                                -- Show a blip on the map.
            coords = vec3(320.0405, -591.7145, 43.2918), -- Blip position.
            sprite = 61,                                  -- Blip icon (GTA sprite ID).
            color  = 2,                                   -- Blip color ID.
            scale  = 1.0,                                 -- Blip size.
            label  = 'Pillbox Hospital'                   -- Blip name.
        },

        -- Duty point for EMS (toggle on/off duty).
        duty = {
            enable = true,                                -- Enable this duty point.
            coords = vec3(305.3186, -597.4736, 43.2918),  -- Interaction coords.
            distance = 3.0                                -- Max distance to interact.
        },

        -- Stash point (shared storage for EMS).
        stash = {
            enable = true,
            coords = vec3(310.1644, -599.5598, 43.2918),
            distance = 2.0
        },

        -- Boss menu (grades/management).
        boss = {
            enable = true,
            coords = vec3(309.9211, -602.9509, 43.2918),
            distance = 3.0
        },

        -- Check-In system (NPC + beds + costs + timers).
        checkIn = {
            enable = true,                                -- Turn the system on/off.
            ped = 's_m_m_doctor_01',                      -- Ped model for the receptionist.
            -- Z lowered by 1.0 to align ped with floor if needed; adjust to your map.
            coords = vec4(307.9655, -588.1100, 43.2918 - 1.0, 155.0590),

            distance = 50.0,                              -- 3D text / target visibility distance.
            cost = 3000,                                  -- Money cost to check in (set false for free).
            duration = 15 * 1000,                         -- Bed time in milliseconds (15s here).
            maxOnDuty = 3,                                -- If >0, check-in is allowed only when EMS on duty ≤ this.
            disableHospitalBeds = false,                  -- true = skip beds; respawn uses respawnNoBedCoords.
            respawnNoBedCoords = vec4(316.66, -581.30, 43.28, 339.02), -- Fallback respawn if beds disabled.

            -- Bed list: each bed has x, y, z, heading. Add as many as your interior needs.
            beds = {
                vec4(333.9829, -578.4377, 42.8646, 70.0),
                vec4(326.9050, -576.3430, 42.8772 + 0.3, 340.0), -- +0.3 raises Z slightly to avoid clipping.
                vec4(344.7037, -581.0491, 42.8719, 70.0),
                vec4(349.4271, -583.5142, 42.8719, 340.0)
            }
        },

        -- Wardrobe/locker room for uniforms.
        wardrobe = {
            enable = true,
            coords = vec4(298.7800, -599.7715, 43.2921, 341.15),
            distance = 3.0,
        },

        -- Shop: supported by qs-inventory, qb-inventory and ps-inventory.
        -- For other inventories, add/replicate items in their native store systems.
        shop = {
            enable = true,
            ped = 's_m_m_doctor_01',                      -- Shop NPC model.
            animationDict = 'mini@strip_club@idles@bouncer@base', -- Optional idle anim dict.
            animationName = 'base',                       -- Optional idle anim name.
            -- Z lowered by 1.0 for better ped placement; tweak if your floor is different.
            coords = vec4(316.6894, -588.1437, 43.2918 - 1.0, 185.0787),
            distance = 3.0,

            -- Items available for purchase (item name, label, price, description).
            items = {
                { name = 'medbag',     label = 'Medical Bag',   price = 1000, description = 'Portable medic kit' },
                { name = 'medikit',    label = 'First-Aid Kit', price = 250,  description = 'Basic healing kit' },
                { name = 'morphine30', label = 'Morphine 30MG', price = 100,  description = 'Strong pain relief' },
                { name = 'morphine10', label = 'Morphine 10MG', price = 45,   description = 'Light pain relief' },
                { name = 'perc30',     label = 'Percocet 30MG', price = 60,   description = 'High-dose pill' },
                { name = 'perc10',     label = 'Percocet 10MG', price = 40,   description = 'Medium-dose pill' },
                { name = 'perc5',      label = 'Percocet 5MG',  price = 30,   description = 'Low-dose pill' },
                { name = 'vic10',      label = 'Vicodin 10MG',  price = 30,   description = 'Strong painkiller' },
                { name = 'vic5',       label = 'Vicodin 5MG',   price = 15,   description = 'Mild painkiller' },
                { name = 'stretcher',  label = 'Stretcher',     price = 1500, description = 'Patient transport' },
            }
        },

        -- Garage list. You can have multiple garage entries (ground, roof, etc.).
        garage = {
            {
                -- Where players open the vehicle menu.
                menuCoords = vec3(295.0178, -600.4273, 43.3034),
                distance = 5.0,

                -- Where the vehicle actually spawns (x, y, z, heading).
                spawnCoords = vec4(287.3742, -611.8311, 43.3840, 70.01),

                -- Vehicles available here; restrict by grades if needed.
                vehicles = {
                    { model = 'ambulance', label = 'Ambulance', grades = { 1, 2, 3 } }
                }
            },
            {
                menuCoords = vec3(339.7209, -588.8276, 74.1657),
                distance = 5.0,
                spawnCoords = vec4(350.1439, -587.9478, 74.1658, 274.9385),
                vehicles = {
                    { model = 'polmav', label = 'Maverick', grades = { 1, 2, 3 } }
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
        id   = 'prison',                                   -- Unique ID.
        ped  = 's_m_m_scientist_01',                       -- Reception/medic NPC model.
        coords = vec4(1729.03, 2563.33, 45.56 - 0.9, 181.42), -- NPC position (Z adjusted down 0.9).
        distance = 5.0,                                    -- TextUI/target visibility range.

        cost = 5,          -- Bank cost to use check-in (set false for free).
        duration = 5 * 1000, -- Time in bed (ms) before you’re released.
        account = 'bank',  -- Which account to charge (depends on your economy).

        -- If true, players won’t be placed into beds; fallback respawn coords used instead.
        disableHospitalBeds = false,

        -- Fallback respawn if beds are disabled or not available.
        respawnNoBedCoords = vec4(1729.03, 2563.33, 45.56, 339.02),

        -- Bed list for this outpost (usually 1–2 for small clinics).
        beds = {
            vec4(1729.03, 2563.33, 45.56, 339.02),
        }
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
