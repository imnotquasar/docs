# Installation

## Script Download

Before starting, you must log in to the CFX portal to download the asset. You will be able to download it as many times as you want on the official CFX page. Just as you download it the first time, you will also download it multiple times in the future to get updates.

{% stepper %}
{% step %}
### Logging in to the CFX Portal

First, log in to the official CFX portal by [clicking here](https://portal.cfx.re/assets/granted-assets).
{% endstep %}

{% step %}
### Finding Your Assets

Once logged in, navigate to the **Granted Assets** section to access your purchased assets. You can download them by clicking the **"Download"** button.
{% endstep %}
{% endstepper %}

Remember, if you encounter any issues or errors when starting the asset, you can check here to see if the problem is related.

{% content-ref url="../../getting-started/what-is-cfx-auth.md" %}
[what-is-cfx-auth.md](../../getting-started/what-is-cfx-auth.md)
{% endcontent-ref %}

<div data-full-width="false"><figure><img src="../../.gitbook/assets/ezgif-5-f03822751d.gif" alt=""><figcaption></figcaption></figure></div>

***

## Downloading Dependencies

The dependencies for this asset are mandatory, so please follow the dependency guide completely and use all required files.

When downloading a dependency, ensure the file is properly unzipped and does not include **"-main"** at the end of its name. If it does, please remove it.

{% stepper %}
{% step %}
### progressbar

{% embed url="https://github.com/quasar-store-organizations/progressbar" %}
{% endstep %}

{% step %}
### meta\_libs

{% embed url="https://github.com/meta-hub/meta_libs/releases/tag/v1.31" %}
{% endstep %}

{% step %}
### bob74\_ipl

{% embed url="https://github.com/Bob74/bob74_ipl" %}
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/ezgif-5-ee6f842765 (1).gif" alt=""><figcaption></figcaption></figure>

***

## Update artifacts and gamebuild

Updating to the latest **artifacts** and **gamebuild** is essential to avoid common server issues. Here's how to do it properly:

{% stepper %}
{% step %}
### Update Artifacts

> To find the best FiveM artifact, visit [artifacts.jgscripts.com](https://artifacts.jgscripts.com). Thanks to JG Scripts.

Completely replace your current artifacts with the latest version. Download the appropriate artifacts for your operating system from the official links:

* **Windows**: [Windows Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/).
* **Linux**: [Linux Artifacts](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/).
{% endstep %}

{% step %}
### Update Gamebuild

Using gamebuild 3095 is recommended as it is the most stable version, ensuring optimal performance and avoiding compatibility issues.

Edit the `server.cfg` file and add the following line:

```plaintext
sv_enforceGameBuild 3095
```
{% endstep %}
{% endstepper %}

You can see the complete guide to update your server here:

{% content-ref url="../../development-guides/before-you-start/how-to-update-my-server.md" %}
[how-to-update-my-server.md](../../development-guides/before-you-start/how-to-update-my-server.md)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/ezgif-2-2221374386.gif" alt=""><figcaption></figcaption></figure>

***

## Server.cfg Positioning

This asset must always be started below your framework and inventory. Failure to do so may result in functionality issues or critical errors. To ensure smooth operation and proper initialization, it is recommended to start the entire download folder using "ensure \[drugs]" in your server configuration.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## Dispatch Configuration

The **notifyCops.lua** file in the configuration folder allows you to notify law enforcement when suspicious activities, such as drug sales, occur. The dispatch system can be configured to use either **client-side** or **server-side** logic depending on your preferences.

Set the desired dispatch method in the **notifyCops.lua** file using the `Config.Dispatch` variable. Two options are available:

{% stepper %}
{% step %}
### Client-side Dispatch

Enables notifications to be handled directly on the player's client.
{% endstep %}

{% step %}
### Server-side Dispatch

Handles notifications centrally on the server.
{% endstep %}
{% endstepper %}

You can configure it via client or server with the following examples:

{% stepper %}
{% step %}
### Client-Side Configuration

When Config.Dispatch = 'client', use the following setup:

```lua
Config.Dispatch = 'client'

function DispatchNotify(coords)
    local playerData = exports['qs-dispatch']:GetPlayerInfo()

    TriggerServerEvent('qs-dispatch:server:CreateDispatchCall', {
        job = { 'police', 'sheriff', 'traffic', 'patrol' },
        callLocation = playerData.coords,
        callCode = { code = '10-15', snippet = 'Drug sell' },
        message = "A ".. playerData.sex.. " is selling drug in ".. playerData.street_1.. "",
        flashes = false,
        image = image or nil,
        blip = {
            sprite = 488,
            scale = 1.5,
            colour = 1,
            flashes = true,
            text = 'High Speed',
            time = (20 * 1000), -- 20 seconds
        }
    })
end
```

This configuration retrieves player information using **qs-dispatch** and sends a dispatch call with details such as the location, street name, and other relevant data.
{% endstep %}

{% step %}
### Server-Side Configuration

When Config.Dispatch = 'server', notifications are processed server-side. Use the following example:

```lua
Config.Dispatch = 'server'

RegisterNetEvent('drugs:server:NotifyCops')
AddEventHandler('drugs:server:NotifyCops', function(coords)
    local street = GetStreetNameAtCoord(coords.x, coords.y, coords.z)
    local street2 = GetStreetNameFromHashKey(street)
    TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
        job = { 'police', 'sheriff', 'traffic', 'patrol' },
        callLocation = street,
        callCode = { code = '<CALL CODE>', snippet = '<CALL SNIPPET EX: 10-10>' },
        message = "Call Message",
        flashes = false,
        image = "URL", -- Optional image URL
        blip = {
            sprite = 488,
            scale = 1.5,
            colour = 1,
            flashes = true,
            text = 'High Speed',
            time = (20 * 1000), -- 20 seconds
        },
        otherData = {
            {
                text = 'Red Obscure', -- Additional data text
                icon = 'fas fa-user-secret', -- Font Awesome icon
            }
        }
    })
end)
```
{% endstep %}
{% endstepper %}
