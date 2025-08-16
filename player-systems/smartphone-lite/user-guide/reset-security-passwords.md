# Reset security passwords

If your phone is broken or you've forgotten your password, you can use the Telephone Technician service. This feature allows for one or more map points where you can pay to repair a damaged phone or reset your password.

Issues may arise if your **esx\_menu\_default** or **qb-menu** version is incorrect or modified. Ensure you're using the original version from your framework.

***

## **Basic technician configuration**

You can configure multiple technician spots or integrate **okokTextUI** for a better user interface. Below is an example of the basic configuration for a telephone technician:

```lua
Config.ResetPassword = {
    spawnNPC = true,
    spots = {
        {
            coords = vec3(-1524.32, -409.3, 35.6),
            money = 500,
            text = '[E] - Telephone Technician',
            ped = {
                h = 230.65,
                model = `hc_hacker`
            },
            blip = {
                name = 'Telephone technician',
                sprite = 89,
                color = 1,
                scale = 0.7
            }
        },

        -- Add more spots here
    },
    okokTextUI = {
        enable = true, -- Enable text UI system
        colour = { r = 255, g = 255, b = 255, a = 255 }, -- Text UI color
        position = 'center' -- Text UI position
    }
}
```

You can expand the configuration by adding more spots or customizing the **okokTextUI** settings.
