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
### MugShotBase64

{% embed url="https://github.com/BaziForYou/MugShotBase64" %}
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

To ensure **Quasar Crafting Creator** works properly, it must always be started **after your framework** (e.g., `qb-core`, `es_extended`) and **after your inventory system** (e.g., `qs-inventory`, `ox_inventory`). This ensures all dependencies are properly loaded before the script is initialized.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

Since this script supports both **ESX** and **QBCore**, the SQL file includes entries for both frameworks. Simply select the SQL section that matches your framework — either **ESX** or **QBCore** — and execute it accordingly.

<details>

<summary>Database for esx</summary>

```sql
DROP TABLE IF EXISTS `crafting_queue`;
DROP TABLE IF EXISTS `crafting_tables`;

CREATE TABLE IF NOT EXISTS `crafting_queue` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`owner` VARCHAR(80) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`tableId` VARCHAR(30) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`item` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`amount` INT(11) NOT NULL DEFAULT '1',
	`startDate` TIMESTAMP NULL DEFAULT NULL,
	`duration` INT(11) NULL DEFAULT NULL,
	`earn` INT(11) NULL DEFAULT '0',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `owner_tableId` (`owner`, `tableId`) USING BTREE
)
COLLATE='utf8mb3_general_ci';

CREATE TABLE IF NOT EXISTS `crafting_tables` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(80) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`label` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`size` SMALLINT(6) NOT NULL DEFAULT '0',
	`job` VARCHAR(30) NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`grades` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`gang` VARCHAR(30) NULL DEFAULT NULL,
	`gangGrades` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`object` VARCHAR(50) NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`recipes` LONGTEXT NOT NULL COLLATE 'utf8mb4_bin',
	`blip` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`global` TINYINT(1) NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='utf8mb3_general_ci';

ALTER TABLE `users` ADD IF NOT EXISTS `crafting_skill` LONGTEXT NULL DEFAULT NULL;

DELIMITER $$

CREATE PROCEDURE migrate_crafting_tables()
BEGIN
    IF EXISTS (
        SELECT * FROM INFORMATION_SCHEMA.COLUMNS 
        WHERE TABLE_NAME = 'crafting_tables' 
        AND COLUMN_NAME = 'job'
        AND TABLE_SCHEMA = DATABASE()
    ) THEN
        ALTER TABLE `crafting_tables` 
            DROP COLUMN `job`,
            DROP COLUMN `grades`,
            DROP COLUMN `gang`,
            DROP COLUMN `gangGrades`;
        
        ALTER TABLE `crafting_tables`
            ADD COLUMN `jobs` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
            ADD COLUMN `gangs` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci';
    END IF;
END$$

DELIMITER ;

CALL migrate_crafting_tables();
DROP PROCEDURE IF EXISTS migrate_crafting_tables;

```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
DROP TABLE IF EXISTS `crafting_queue`;
DROP TABLE IF EXISTS `crafting_tables`;

CREATE TABLE IF NOT EXISTS `crafting_queue` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`owner` VARCHAR(80) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`tableId` VARCHAR(30) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`item` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`amount` INT(11) NOT NULL DEFAULT '1',
	`startDate` TIMESTAMP NULL DEFAULT NULL,
	`duration` INT(11) NULL DEFAULT NULL,
	`earn` INT(11) NULL DEFAULT '0',
	PRIMARY KEY (`id`) USING BTREE,
	INDEX `owner_tableId` (`owner`, `tableId`) USING BTREE
)
COLLATE='utf8mb3_general_ci';

CREATE TABLE IF NOT EXISTS `crafting_tables` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`creator` VARCHAR(80) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`label` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`size` SMALLINT(6) NOT NULL DEFAULT '0',
	`job` VARCHAR(30) NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`grades` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`gang` VARCHAR(30) NULL DEFAULT NULL,
	`gangGrades` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`object` VARCHAR(50) NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`coords` LONGTEXT NOT NULL COLLATE 'utf8mb3_general_ci',
	`recipes` LONGTEXT NOT NULL COLLATE 'utf8mb4_bin',
	`blip` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	`global` TINYINT(1) NULL DEFAULT NULL,
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='utf8mb3_general_ci';


ALTER TABLE `players` ADD IF NOT EXISTS `crafting_skill` LONGTEXT NULL DEFAULT NULL;

DELIMITER $$

CREATE PROCEDURE migrate_crafting_tables()
BEGIN
    IF EXISTS (
        SELECT * FROM INFORMATION_SCHEMA.COLUMNS 
        WHERE TABLE_NAME = 'crafting_tables' 
        AND COLUMN_NAME = 'job'
        AND TABLE_SCHEMA = DATABASE()
    ) THEN
        ALTER TABLE `crafting_tables` 
            DROP COLUMN `job`,
            DROP COLUMN `grades`,
            DROP COLUMN `gang`,
            DROP COLUMN `gangGrades`;
        
        ALTER TABLE `crafting_tables`
            ADD COLUMN `jobs` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
            ADD COLUMN `gangs` LONGTEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci';
    END IF;
END$$

DELIMITER ;

CALL migrate_crafting_tables();
DROP PROCEDURE IF EXISTS migrate_crafting_tables;

```

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc (1).gif" alt=""><figcaption></figcaption></figure>

***

## Key bind manipulation

All Quasar Store assets use the same process for modifying Key Binds to ensure consistency and optimized performance across all resources.&#x20;

Below is a clear and detailed guide on how to adjust them to your preferences.

{% content-ref url="../../development-guides/configure-your-scripts/how-to-change-key-bindings.md" %}
[how-to-change-key-bindings.md](../../development-guides/configure-your-scripts/how-to-change-key-bindings.md)
{% endcontent-ref %}
