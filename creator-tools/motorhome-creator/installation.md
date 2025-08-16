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

For best results, place dependencies and **qs-motorhome** in the same `[`**motorhome**`]` folder. If not, ensure dependencies are started before **qs-motorhome** to guarantee proper functionality. This script should always be started under your inventory system.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

Select the framework you are using and then execute the SQL in your HeidiSQL. If you encounter errors, ensure you are using the most current version of MariaDB. You can refer to our guide above or search online.

<details>

<summary>Database for esx</summary>

```sql
ALTER TABLE
    `users`
ADD
    IF NOT EXISTS `motorhome_inside` TEXT NULL DEFAULT NULL;

CREATE TABLE IF NOT EXISTS `motorhome_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`plate` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`created` TIMESTAMP NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `plate`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=5
;

CREATE TABLE IF NOT EXISTS `motorhome` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`plate` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`charge` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `plate` (`plate`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=13
;
```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
ALTER TABLE
    `players`
ADD
    IF NOT EXISTS `motorhome_inside` TEXT NULL DEFAULT NULL;

CREATE TABLE IF NOT EXISTS `motorhome_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`plate` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`created` TIMESTAMP NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `plate`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=5
;

CREATE TABLE IF NOT EXISTS `motorhome` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`plate` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`charge` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `plate` (`plate`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=13
;
```

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>
