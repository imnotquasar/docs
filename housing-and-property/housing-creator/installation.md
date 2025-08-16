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

{% hint style="warning" %}
If you are a qbcore user, remove qb-interior or use only qb-interior, not the k4mb1 package, not use both.
{% endhint %}

{% stepper %}
{% step %}
### ox\_lib

{% embed url="https://github.com/overextended/ox_lib/releases" %}
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

{% hint style="info" %}
**K4MB1 Maps (shells)** are now in the "Housing \[props]" asset in your keymaster.
{% endhint %}

For best results, place dependencies and **qs-housing** in the same `[housing]` folder. If not, ensure dependencies are started before **qs-housing** to guarantee proper functionality. This script should always be started under your inventory system.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

As there are multiple housing systems in the market, and frameworks like QBCore include systems like **qb-houses** with similar database columns to **qs-housing**, we will begin by cleaning the database before executing the SQL. Start by using the first dropdown labeled **"First we clean the database"**, then select the dropdown for the framework you are using.

{% stepper %}
{% step %}
### First important step

Before running the ESX or QBCore sql, we are going to clean our database, this step is essential and you cannot skip it if it is your first installation of Housing 4.0 or higher.
{% endstep %}

{% step %}
### Execute the corresponding sql

Once the database is cleaned, we look for the drop-down menu of the framework we use and execute it.
{% endstep %}
{% endstepper %}

<details>

<summary>First we clean the database</summary>

```sql
-- IF YOU ARE NOT UPDATING YOUR OLD QS-HOUSING, MAKE SURE YOU READ THIS SQL!

DROP TABLE IF EXISTS `houselocations`;
DROP TABLE IF EXISTS `player_houses`;
DROP TABLE IF EXISTS `house_rents`;
DROP TABLE IF EXISTS `house_objects`;
DROP TABLE IF EXISTS `house_plants`;
```

</details>

<details>

<summary>Database for esx</summary>

```sql
ALTER TABLE
    `users`
ADD
    IF NOT EXISTS `inside` VARCHAR(50) NULL DEFAULT '';

INSERT IGNORE INTO
    `addon_inventory` (name, label, shared)
VALUES
    ('propery', 'Property', 0);

INSERT IGNORE INTO
    `datastore` (name, label, shared)
VALUES
    ('propery', 'Property', 0);

CREATE TABLE IF NOT EXISTS `houselocations` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(255) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`label` VARCHAR(255) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`owned` TINYINT(2) NULL DEFAULT NULL,
	`price` INT(11) NULL DEFAULT NULL,
	`defaultPrice` INT(11) NULL DEFAULT NULL,
	`tier` TINYINT(2) NULL DEFAULT NULL,
	`garage` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`garageShell` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`creator` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`mlo` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`ipl` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`console` INT(11) NULL DEFAULT NULL,
	`board` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`for_sale` INT(11) NULL DEFAULT '1',
	`extra_imgs` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`description` TEXT NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`creatorJob` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`upgrades` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`apartmentCount` INT(11) NULL DEFAULT NULL,
	PRIMARY KEY (`name`) USING BTREE,
	INDEX `name` (`name`) USING BTREE,
	INDEX `id` (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

CREATE TABLE IF NOT EXISTS `player_houses` (
	`id` INT(255) NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`citizenid` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`owner` VARCHAR(46) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`keyholders` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`outfit` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`logout` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`decorateStash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`charge` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`credit` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`creditPrice` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`console` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`decorateCoords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`rented` INT(11) NULL DEFAULT NULL,
	`rentPrice` INT(11) NULL DEFAULT NULL,
	`rentable` INT(11) NULL DEFAULT NULL,
	`purchasable` INT(11) NULL DEFAULT NULL,
	`vaultCodes` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `house` (`house`) USING BTREE,
	INDEX `owner` (`owner`) USING BTREE,
	INDEX `citizenid` (`citizenid`) USING BTREE
)
COLLATE='utf8mb4_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=3
;



CREATE TABLE IF NOT EXISTS `house_rents` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
	`identifier` VARCHAR(80) NOT NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
	`payed` INT(11) NOT NULL DEFAULT '0',
	`date` TIMESTAMP NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

CREATE TABLE IF NOT EXISTS `house_objects` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'latin1_swedish_ci',
	`model` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'latin1_swedish_ci',
	`coords` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	`house` VARCHAR(80) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`construction` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`created` TIMESTAMP NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;


ALTER TABLE `house_objects`
	ADD IF NOT EXISTS `construction` VARCHAR(50) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `created` TIMESTAMP NULL DEFAULT current_timestamp()
;

DROP TABLE IF EXISTS `house_plants`;

CREATE TABLE IF NOT EXISTS `house_plants` (
	`id` int(11) NOT NULL AUTO_INCREMENT,
	`building` varchar(50) DEFAULT NULL,
	`stage` varchar(50) DEFAULT 'stage-a',
	`sort` varchar(50) DEFAULT NULL,
	`gender` varchar(50) DEFAULT NULL,
	`food` int(11) DEFAULT 100,
	`health` int(11) DEFAULT 100,
	`progress` int(11) DEFAULT 0,
	`coords` text DEFAULT NULL,
	`plantid` varchar(50) DEFAULT NULL,
	PRIMARY KEY (`id`),
	KEY `building` (`building`),
	KEY `plantid` (`plantid`)
) ENGINE = InnoDB AUTO_INCREMENT = 7123 DEFAULT CHARSET = utf8mb4;

ALTER TABLE `player_houses`
    CHANGE COLUMN IF EXISTS `identifier`  `owner` VARCHAR(46) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci';

ALTER TABLE `houselocations`
	ADD IF NOT EXISTS `blip` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `upgrades` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `apartmentCount` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `creatorGotMoney` TINYINT(1) NOT NULL DEFAULT '0'
;

ALTER TABLE `player_houses`
	ADD IF NOT EXISTS `rented` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `rentPrice` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `rentable` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `purchasable` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `console` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `decorateCoords` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `vaultCodes` TEXT NULL DEFAULT NULL
;

ALTER TABLE `houselocations`
	DROP IF EXISTS `houseID`
;
	

ALTER TABLE `player_houses`
	DROP IF EXISTS `houseID`,
	DROP IF EXISTS `timer`,
	DROP IF EXISTS `insideId`
;

ALTER TABLE `houselocations`
	CHANGE COLUMN `tier` `tier` SMALLINT NULL DEFAULT NULL;

CREATE TABLE IF NOT EXISTS `house_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`inHouse` TINYINT(1) UNSIGNED NOT NULL DEFAULT '0',
	`uniq` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`created` TIMESTAMP NULL DEFAULT NULL,
	`lightData` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `house`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
ALTER TABLE
    `players`
ADD
    IF NOT EXISTS `inside` VARCHAR(50) NULL DEFAULT '';

CREATE TABLE IF NOT EXISTS `houselocations` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(255) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`label` VARCHAR(255) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`owned` TINYINT(2) NULL DEFAULT NULL,
	`price` INT(11) NULL DEFAULT NULL,
	`defaultPrice` INT(11) NULL DEFAULT NULL,
	`tier` TINYINT(2) NULL DEFAULT NULL,
	`garage` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`garageShell` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`creator` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`mlo` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`ipl` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`console` INT(11) NULL DEFAULT NULL,
	`board` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`for_sale` INT(11) NULL DEFAULT '1',
	`extra_imgs` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`description` TEXT NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`creatorJob` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`blip` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`upgrades` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`apartmentCount` INT(11) NULL DEFAULT NULL,
	PRIMARY KEY (`name`) USING BTREE,
	INDEX `name` (`name`) USING BTREE,
	INDEX `id` (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

CREATE TABLE IF NOT EXISTS `player_houses` (
	`id` INT(255) NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`citizenid` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`owner` VARCHAR(46) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`keyholders` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`stash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`outfit` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`logout` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`decorateStash` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`charge` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`credit` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`creditPrice` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`console` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`decorateCoords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	`rented` INT(11) NULL DEFAULT NULL,
	`rentPrice` INT(11) NULL DEFAULT NULL,
	`rentable` INT(11) NULL DEFAULT NULL,
	`purchasable` INT(11) NULL DEFAULT NULL,
	`vaultCodes` TEXT NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `house` (`house`) USING BTREE,
	INDEX `owner` (`owner`) USING BTREE,
	INDEX `citizenid` (`citizenid`) USING BTREE
)
COLLATE='utf8mb4_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=3
;



CREATE TABLE IF NOT EXISTS `house_rents` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
	`identifier` VARCHAR(80) NOT NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
	`payed` INT(11) NOT NULL DEFAULT '0',
	`date` TIMESTAMP NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

CREATE TABLE IF NOT EXISTS `house_objects` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'latin1_swedish_ci',
	`model` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'latin1_swedish_ci',
	`coords` TEXT NOT NULL COLLATE 'latin1_swedish_ci',
	`house` VARCHAR(80) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`construction` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`created` TIMESTAMP NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;


ALTER TABLE `house_objects`
	ADD IF NOT EXISTS `construction` VARCHAR(50) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `created` TIMESTAMP NULL DEFAULT current_timestamp()
;

DROP TABLE IF EXISTS `house_plants`;

CREATE TABLE IF NOT EXISTS `house_plants` (
	`id` int(11) NOT NULL AUTO_INCREMENT,
	`building` varchar(50) DEFAULT NULL,
	`stage` varchar(50) DEFAULT 'stage-a',
	`sort` varchar(50) DEFAULT NULL,
	`gender` varchar(50) DEFAULT NULL,
	`food` int(11) DEFAULT 100,
	`health` int(11) DEFAULT 100,
	`progress` int(11) DEFAULT 0,
	`coords` text DEFAULT NULL,
	`plantid` varchar(50) DEFAULT NULL,
	PRIMARY KEY (`id`),
	KEY `building` (`building`),
	KEY `plantid` (`plantid`)
) ENGINE = InnoDB AUTO_INCREMENT = 7123 DEFAULT CHARSET = utf8mb4;

ALTER TABLE `player_houses`
    CHANGE COLUMN IF EXISTS `identifier`  `owner` VARCHAR(46) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci';

ALTER TABLE `houselocations`
	ADD IF NOT EXISTS `blip` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `upgrades` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `apartmentCount` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `creatorGotMoney` TINYINT(1) NOT NULL DEFAULT '0'
;

ALTER TABLE `player_houses`
	ADD IF NOT EXISTS `rented` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `rentPrice` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `rentable` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `purchasable` INT(11) NULL DEFAULT NULL,
	ADD IF NOT EXISTS `console` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `decorateCoords` TEXT NULL DEFAULT NULL,
	ADD IF NOT EXISTS `vaultCodes` TEXT NULL DEFAULT NULL
;

ALTER TABLE `houselocations`
	DROP IF EXISTS `houseID`
;
	

ALTER TABLE `player_houses`
	DROP IF EXISTS `houseID`,
	DROP IF EXISTS `timer`,
	DROP IF EXISTS `insideId`
;

ALTER TABLE `houselocations`
	CHANGE COLUMN `tier` `tier` SMALLINT NULL DEFAULT NULL;
	
CREATE TABLE IF NOT EXISTS `house_decorations` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`house` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`creator` VARCHAR(70) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`modelName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`rotation` TEXT NOT NULL DEFAULT '' COLLATE 'utf8mb3_general_ci',
	`inStash` TINYINT(1) NOT NULL DEFAULT '0',
	`inHouse` TINYINT(1) UNSIGNED NOT NULL DEFAULT '0',
	`uniq` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`created` TIMESTAMP NULL DEFAULT NULL,
	`lightData` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `id` (`id`, `house`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

```

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

## Garage Systems

{% hint style="info" %}
If your garage system is not listed, contact its creator for compatibility, as tickets for unsupported systems will not be handled.
{% endhint %}

Quasar Housing supports the following garage systems:

| Garage                                                            | Framework support                  |
| ----------------------------------------------------------------- | ---------------------------------- |
| [qs-advancedgarages](https://www.youtube.com/watch?v=Y1i8_Hxpq5I) | Exclusive for ESX, easy to use.    |
| [qb-garages](https://github.com/qbcore-framework/qb-garages)      | Exclusive for QBCore, easy to use. |

Quasar Store offers one of the most popular FiveM garage systems with features like interiors, slots, impounds, and in-game creation tools. Quasar Housing also includes an editable garage system located in **client/custom/garage/** and **server/custom/garage/**, automatically detecting compatible garages with the correct asset name.

Quasar Housing also supports garage systems such as **jg-advancedgarages**, **cd\_garage**, **okokGarage**, **loaf\_garage**, **rcore\_garage**, **zerio-garage**, **codem-garages**, **ak47\_garage**, or **vms\_garagesv2**.

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
