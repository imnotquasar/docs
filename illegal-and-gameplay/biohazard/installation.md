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

This asset must always be started below your framework, inventory, and ambulance job scripts. Failing to maintain this order can lead to functionality issues or critical errors. To ensure proper initialization and smooth operation, it is recommended to start the entire download folder using "ensure \[backrooms]" in your server.cfg, respecting the specified hierarchy.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## Reloadskin Configuration

{% hint style="info" %}
For **QBCore users** using qb-ambulancejob, no additional modifications are necessary as it works automatically.
{% endhint %}

To configure the reloadskin, go to `client/custom` and edit the `ExecuteCommand` as you prefer. By default, we have set it to **"reloadskin"** since most clothing systems use this command. However, you can change it to whatever suits your needs.

```lua
function ReloadSkin()
    ExecuteCommand('reloadskin')
end
```

***

## Ambience Recommendation

For the best immersive experience, we strongly recommend adding an ambience map to your server. A great option is the **Total Apocalypse** map, which completely transforms the world of GTA V into a ruined, devastated environment filled with destruction. This setting fits perfectly with any zombie survival scenario, making players feel like they are truly living through an outbreak.

The atmosphere created by this map enhances roleplay, increases tension, and makes every encounter more realistic. If you want your server to stand out and provide a unique post-apocalyptic vibe, this map is the ideal choice.

{% embed url="https://github.com/SparksScripts/Total-Apocalypse" %}

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>
