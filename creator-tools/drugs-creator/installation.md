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

To ensure Quasar Drugs Creator works properly, start your framework (e.g., ESX, QBCore) first, followed by your inventory system (e.g., qs-inventory, ox\_inventory). Finally, start Quasar Drugs Creator, ensuring all dependencies are running beforehand.

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
ALTER TABLE
    `users`
ADD
    IF NOT EXISTS `inside_lab` VARCHAR(50) NULL DEFAULT NULL;

DROP TABLE IF EXISTS `drug_farm`;

CREATE TABLE `drug_farm` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(80) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`type` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`zone` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`maxCollectionCount` INT(11) NOT NULL DEFAULT '5',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

DROP TABLE IF EXISTS `drug_labs`;

CREATE TABLE `drug_labs` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`owner` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`shell` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`price` INT(11) NULL DEFAULT '500',
	`holders` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`locked` TINYINT(2) NULL DEFAULT '0',
	`level` INT(11) NULL DEFAULT '1',
	`progress` INT(11) NULL DEFAULT '0',
	`public` TINYINT(1) NULL DEFAULT '0',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;



DROP TABLE IF EXISTS `drug_lab_decorations`;

CREATE TABLE `drug_lab_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`lab` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`created` TIMESTAMP NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `lab`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

DROP TABLE IF EXISTS `drug_seller`;

CREATE TABLE `drug_seller` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`entry` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`model` VARCHAR(50) NOT NULL COLLATE 'utf8mb3_general_ci',
	`time` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`knock` TINYINT(1) NOT NULL DEFAULT '0',
	`itemListId` VARCHAR(50) NOT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;
```

</details>

<details>

<summary>Database for qbcore</summary>

<pre class="language-sql"><code class="lang-sql"><strong>ALTER TABLE
</strong>    `players`
ADD
    IF NOT EXISTS `inside_lab` VARCHAR(50) NULL DEFAULT NULL;

DROP TABLE IF EXISTS `drug_farm`;

CREATE TABLE `drug_farm` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(80) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`type` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`zone` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`maxCollectionCount` INT(11) NOT NULL DEFAULT '5',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

DROP TABLE IF EXISTS `drug_labs`;

CREATE TABLE `drug_labs` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`owner` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`wardrobe` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`shell` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`price` INT(11) NULL DEFAULT '500',
	`holders` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`locked` TINYINT(2) NULL DEFAULT '0',
	`level` INT(11) NULL DEFAULT '1',
	`progress` INT(11) NULL DEFAULT '0',
	`public` TINYINT(1) NULL DEFAULT '0',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;


DROP TABLE IF EXISTS `drug_lab_decorations`;

CREATE TABLE `drug_lab_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`lab` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`created` TIMESTAMP NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `lab`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

DROP TABLE IF EXISTS `drug_seller`;

CREATE TABLE `drug_seller` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`entry` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`model` VARCHAR(50) NOT NULL COLLATE 'utf8mb3_general_ci',
	`time` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`knock` TINYINT(1) NOT NULL DEFAULT '0',
	`itemListId` VARCHAR(50) NOT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `name` (`name`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;
</code></pre>

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc (1).gif" alt=""><figcaption></figcaption></figure>

***

## Weather Sync

{% hint style="success" %}
You can add or edit the weather systems directly in **client/custom/weather/weather.lua** to customize it according to your server's needs.
{% endhint %}

For seamless synchronization of weather and time, specific dependencies are required for **ESX** and **QBCore**. Make sure to select and install the appropriate dependency based on the framework your server uses to ensure everything functions correctly.

| Weather                                                              | Framework support                            |
| -------------------------------------------------------------------- | -------------------------------------------- |
| [cd\_easytime](https://github.com/dsheedes/cd_easytime)              | Exclusive for ESX, easy to use.              |
| [qb-weathersync](https://github.com/qbcore-framework/qb-weathersync) | Exclusive for QBCore, easy to use.           |
| [av\_weather](https://av-scripts.tebex.io/package/5618745)           | Paid, runs on ESX and QBCore, very advanced. |

***

## Stash and Wardrobe&#x20;

{% hint style="success" %}
This system automatically adapts to your dependencies, please do not touch files.
{% endhint %}

The **stash** and **wardrobe** systems in Quasar Housing are configured automatically, so no additional adjustments are needed. However, if your system is not compatible, you can fully customize these features using the files located in `client/custom/` and `server/custom/`.&#x20;

***

## Key bind manipulation

All Quasar Store assets use the same process for modifying Key Binds to ensure consistency and optimized performance across all resources.&#x20;

Below is a clear and detailed guide on how to adjust them to your preferences.

{% content-ref url="../../development-guides/configure-your-scripts/how-to-change-key-bindings.md" %}
[how-to-change-key-bindings.md](../../development-guides/configure-your-scripts/how-to-change-key-bindings.md)
{% endcontent-ref %}
