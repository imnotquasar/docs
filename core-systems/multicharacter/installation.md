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

## Modifications and Dependencies

{% hint style="warning" %}
For any other clothing systems, compatibility can be achieved manually by editing the open-source files provided within the asset or by contacting the system creator.
{% endhint %}

Quasar Multicharacter has minimal dependencies, requiring only a compatible clothing system or manual compatibility adjustments.

{% stepper %}
{% step %}
### Removing Conflicting Assets

#### **ESX Version**

Remove esx\_multicharacter.

#### **QBCore Version:**&#x20;

Remove qb-multicharacter and optionally qb-spawn if you plan to use Quasar's integrated spawn selector. The asset supports qb-apartments if enabled in the fxmanifest.lua.

**IMPORTANT: If you use qbx\_core, you must go to qbx\_core/config/client.lua and edit this useExternalCharacters to false.**
{% endstep %}

{% step %}
### Clothing System Compatibility

Quasar Multicharacter is pre-configured to work with the following systems:

* **qb-clothing**
* **esx\_skin**
* **illenium-appearance**

If your clothing system replaces esx\_skin and skinchanger, it may work out of the box by declaring esx\_skin or qb-clothing in the config.
{% endstep %}
{% endstepper %}

***

## Issues in illenium-appearance

{% hint style="info" %}
If you do not use illenium-appearance, skip this step.
{% endhint %}

If your character does not spawn with the correct clothing or appearance, follow these steps for illenium-appearance:

{% stepper %}
{% step %}
### Open the manifest file in your illenium-appearance folder
{% endstep %}

{% step %}
### Remove the lines

```lua
provides {esx_skin, skin_changer}
```
{% endstep %}

{% step %}
### Check other scripts

Remove this line if it exists.

```lua
dependencies {esx_skin, skin_changer}
```
{% endstep %}

{% step %}
### Clear the server cache

Once you have completed these steps, clear your server cache and restart it.
{% endstep %}
{% endstepper %}

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

{% hint style="warning" %}
For some reason, spawnmanager doesn't always start, so make sure you have `ensure spawnmanager` at the top of your server.cfg, or you'll get an infinite loadscreen.
{% endhint %}

For optimal functionality, ensure that this asset is started directly below your framework and inventory folders. Proper initialization depends on this order, as starting it elsewhere could lead to errors or conflicts. Always prioritize framework and inventory loading before this asset.

We recommend starting this asset within its own folder using `ensure [multicharacter]` in your server configuration. This approach ensures a clean and organized initialization, minimizing potential conflicts and maintaining proper asset functionality.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

Quasar Multicharacter features an intelligent system that automatically creates the necessary database table for you upon first launch. This means there’s no need for manual database installation or modifications. The table used for managing character slots is named **multichar\_slots**, and it will be generated seamlessly by the system, ensuring a hassle-free setup process.

***

## Blocking slots using Tebex

Quasar Multicharacter provides a flexible slot management system, offering two main methods for administrators to control character slots: Tebex integration and manual management.

{% stepper %}
{% step %}
### Tebex Integration

Quasar Multicharacter is fully compatible with the **Tebex Store**, allowing you to sell character slots directly through your server's Tebex store. This system enables players to purchase additional character slots seamlessly, which can then be unlocked and managed automatically. The configuration for these locked slots can be adjusted in **config.lua** under the `"tebex"` setting, giving you full control over how these slots are managed and displayed.
{% endstep %}

{% step %}
### Manual Slot Management

If you prefer not to use Tebex for slot management—for reasons such as payment flexibility or direct control—you can use the **/addslot id** command. This command allows administrators to manually assign additional slots to a player using their server ID. This method is ideal for those who want to manage slots independently of the Tebex platform.
{% endstep %}

{% step %}
### Why This Step is Important

Skipping this configuration step may lead to confusion or misuse of the slot system. It is crucial to understand how the Tebex integration or manual management works to ensure a smooth experience for both administrators and players.

For a detailed guide on using and integrating this system, refer to the official documentation. Properly understanding this system is essential for its effective implementation.
{% endstep %}
{% endstepper %}

In the following link you will learn how to get the Tebex token and how to execute in this script:

{% content-ref url="user-guide/char-slots-integration.md" %}
[char-slots-integration.md](user-guide/char-slots-integration.md)
{% endcontent-ref %}
