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

{% step %}
### oxmysql

{% embed url="https://github.com/overextended/oxmysql/releases" %}
{% endstep %}

{% step %}
### hospital\_map (default hospital)

{% embed url="https://github.com/qbcore-framework/hospital_map" %}
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

To ensure \[hospital] works properly, always start your framework (e.g., ESX, QBCore) first, followed by your inventory system (e.g., qs-inventory, ox\_inventory) and your shops system (e.g., qs-advancedshops, ox\_inventory).&#x20;

Finally, start \[hospital], making sure all dependencies are already running beforehand.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

As there are multiple housing systems in the market, and frameworks like QBCore include systems like **qb-houses** with similar database columns to **qs-housing**, we will begin by cleaning the database before executing the SQL. Start by using the first dropdown labeled **"First we clean the database"**, then select the dropdown for the framework you are using.

<details>

<summary>Database for esx</summary>

```sql
ALTER TABLE `users` ADD IF NOT EXISTS `ems_duty` LONGTEXT NULL DEFAULT NULL;
ALTER TABLE `users` ADD IF NOT EXISTS `is_dead` TINYINT(1) NULL DEFAULT '0';

CREATE TABLE IF NOT EXISTS `hospitals` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`zone` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`respawnPoint` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`blip` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`duty` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`stash` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`boss` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`checkIn` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`shop` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`garage` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
;
```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
CREATE TABLE IF NOT EXISTS `hospitals` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`zone` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`respawnPoint` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`blip` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`duty` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`stash` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`boss` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`checkIn` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`shop` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`garage` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
;
```

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc (1).gif" alt=""><figcaption></figcaption></figure>

***

## Automatic System Detection

{% hint style="success" %}
This system automatically adapts to your dependencies, please do not touch files.
{% endhint %}

One of the strengths of **Quasar Medical Creator** is that it automatically detects the systems your server is running, so you don’t need to manually configure most integrations. When the script starts, it scans your active resources and links itself with the correct dependencies.&#x20;

For example:

* **Frameworks** → Detects if you use **ESX**, **QBCore**, or **QBX**, and configures itself accordingly.
* **Inventories** → Works with popular systems such as **qs-inventory** or others without requiring edits.
* **Wardrobes** → Compatible with **qs-appearance**, **qb-clothing**, **codem-appearance**, and many more.
* **Vehicle Keys** → Supports different car key systems automatically, from **qs-vehiclekeys** or others.
* **Fuel Systems** → Recognizes resources like **qs-fuelstations**, **LegacyFuel**, **ox\_fuel**, etc.
* **Society/Job Management** → Adapts to **esx\_society** or **qb-management**.
* **Phones** → Works seamlessly with **qs-smartphone-pro or others** for distress calls.

***

## Key bind manipulation

All Quasar Store assets use the same process for modifying Key Binds to ensure consistency and optimized performance across all resources.&#x20;

Below is a clear and detailed guide on how to adjust them to your preferences.

{% content-ref url="../../development-guides/configure-your-scripts/how-to-change-key-bindings.md" %}
[how-to-change-key-bindings.md](../../development-guides/configure-your-scripts/how-to-change-key-bindings.md)
{% endcontent-ref %}
