# Installation

Script Download

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

This script has dependencies depending on its framework, even if it says optional we recommend having them for correct use.

{% stepper %}
{% step %}
### ESX

{% embed url="https://github.com/esx-framework/esx_core" %}

Optional for ESX:

{% embed url="https://github.com/esx-framework/esx_addonaccount" %}
{% endstep %}
{% endstepper %}

{% stepper %}
{% step %}
### QBCore

{% embed url="https://github.com/qbcore-framework/qb-core" %}

Optional for QBCore:

{% embed url="https://github.com/qbcore-framework/qb-menu" %}

{% embed url="https://github.com/qbcore-framework/qb-management" %}
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

This asset must always be started below your framework and inventory. Failure to do so may result in functionality issues or critical errors. To ensure smooth operation and proper initialization, it is recommended to start the entire download folder using "ensure \[billing]" in your server.cfg.

```markdown
## First we will start the cores, never below
ensure es_extended or qb-core

## The inventory should be executed above
ensure [inventory]

## Run qs-billing here along with its dependencies
ensure [billing]
```

{% hint style="warning" %}
The gif is an example of how to do it, it does not mean that you have to put exactly what is in it, please read the text above to understand how to place the script's secure
{% endhint %}

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

It is essential to execute the SQL file completely for this asset to function correctly.

```sql
CREATE TABLE `qs_billing` (
  `id` int(50) NOT NULL PRIMARY KEY AUTO_INCREMENT,
  `receiver_identifier` varchar(255) NOT NULL,
  `receiver_name` varchar(255) NOT NULL,
  `author_identifier` varchar(255) NOT NULL,
  `author_name` varchar(255) NULL DEFAULT NULL,
  `society` varchar(255) NOT NULL,
  `society_name` varchar(255) NOT NULL,
  `item` varchar(255) NOT NULL,
  `invoice_value` int(50) NOT NULL,
  `status` varchar(50) NOT NULL,
  `notes` varchar(255) NULL DEFAULT ' ',
  `sent_date` varchar(255) NOT NULL,
  `limit_pay_date` varchar(255) NULL DEFAULT NULL,
  `fees_amount` int(50) NULL DEFAULT 0,
  `paid_date` varchar(255) NULL DEFAULT NULL
);
```

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>

***

## Items for inventories with metadata

{% hint style="info" %}
This item is optional and will only work with metadata-based inventories.
{% endhint %}

This system will only work with metadata items, don't worry, you can not use this system if you do not have a compatible inventory or you do not like this function.

<details>

<summary>Items for qs-inventory</summary>

<pre class="language-lua"><code class="lang-lua"><strong>['bill_paper'] = {
</strong>    ['name'] = 'bill_paper',
    ['label'] = 'Bill Paper',
    ['weight'] = 0,
<strong>    ['type'] = 'item',
</strong>    ['image'] = 'bill_paper.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'View your invoice'
},
</code></pre>

</details>

<details>

<summary>Items for qb-inventory</summary>

```lua
    ['bill_paper'] = {
        ['name'] = 'bill_paper',
        ['label'] = 'Bill Paper',
        ['weight'] = 10,
        ['type'] = 'item',
        ['image'] = 'bill_paper.png',
        ['unique'] = false,
        ['useable'] = true,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'Visa card, can be used via ATM'
    },
```

</details>

<details>

<summary>Items for ox_inventory</summary>

```lua
['bill_paper'] = {
    label = 'Bill paper',
    weight = 1,
    stack = false,
    close = false,
},
```

</details>

***

## Basic asset configuration

{% hint style="info" %}
We do not recommend editing frameworks unnecessarily, since almost all assets depend exclusively on your framework and exports on the name of your framework. Otherwise and if you edited your framework, read these steps carefully.
{% endhint %}

{% hint style="success" %}
If you still require more open codes for the configuration, you can check within client/custom and server/custom to adapt the asset to your personal taste.
{% endhint %}

Please expand each part to see information about the configuration of the asset, this way you will understand the general operation of the asset on the framework and editable files side.

<details>

<summary>Basic framework configuration</summary>

The asset will work automatically if your framework is called es\_extended or qb-core, it will automatically detect if any of them are started. In case your framework has been renamed, you can modify it in config.lua to edit the name of your framework.

</details>

<details>

<summary>Advanced framework configuration</summary>

If your framework is completely modified, both in events and name, you should access client/custom/framework or server/custom/framework to adapt the native events of your framework to the codes you have created. If this step doesn't work, we ask that you ask your framework modifier or trusted developer for help.

</details>

<details>

<summary>More general settings</summary>

This asset contains multiple configurations within the config folder. But you can also access more open source and configurations within client/custom or server/custom. We do not recommend using these configurations if you do not have the basics of programming.

</details>
