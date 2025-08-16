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
### ox\_lib

{% embed url="https://github.com/overextended/ox_lib/releases" %}
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

This asset must always be started below your framework and inventory. Failure to do so may result in functionality issues or critical errors. To ensure smooth operation and proper initialization, it is recommended to start the entire download folder using "ensure \[textui]" in your server.cfg.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## Automatic Integration in all Quasar Scripts

Quasar Text UI seamlessly integrates with all **qs scripts** without additional configuration. Simply start it **before other scripts** in your `server.cfg`, and it will automatically adapt to your server's needs.

{% stepper %}
{% step %}
### Automatic Adaptation

The script will **automatically integrate** with other `qs` scripts without additional configuration.
{% endstep %}

{% step %}
### Optional Customization

If you need to modify any parameters, navigate to `client/custom/framework/*`
{% endstep %}
{% endstepper %}

That’s it! **Quasar Text UI** is now fully integrated and ready to use.

***

## Integration in qbcore and esx

We can seamlessly integrate this system by default in both QB and ESX frameworks using the following code snippets. If your framework does not include these events, you can refer to the **"User Guides"** section for detailed instructions on how to adapt this system to any other script.

<details>

<summary>Integration in qbcore</summary>

```lua
-- qb-core/client/drawtext.lua

exports['qb-core']:DrawText() => exports["qs-textui"]:displayTextUI(text, position)

exports['qb-core']:HideText() => exports["qs-textui"]:hideTextUI()

exports['qb-core']:KeyPressed() => Dont change it

exports['qb-core']:ChangeText() => exports['qs-textui']:changeText(text, position)
```

</details>

<details>

<summary>Integration in esx</summary>

```lua
-- es_extended/client/functions.lua

function ESX.TextUI(...)
    return IsResourceFound('esx_textui') and exports['esx_textui']:TextUI(...)
end

---@return nil
function ESX.HideUI()
    return IsResourceFound('esx_textui') and exports['esx_textui']:HideUI()
end

-- Set them to these:

function ESX.TextUI(...)
    return exports["qs-textui"]:displayTextUI(...)
end

---@return nil
function ESX.HideUI()
    return exports["qs-textui"]:hideTextUI()
end
```

</details>
