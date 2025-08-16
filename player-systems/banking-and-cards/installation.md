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

{% hint style="info" %}
Dependencies vary depending on whether you use QBCore or ESX, and are completely optional as you can disable the partnership system.
{% endhint %}

The dependencies for this asset are mandatory, so please follow the dependency guide completely and use all required files.

When downloading a dependency, ensure the file is properly unzipped and does not include **"-main"** at the end of its name. If it does, please remove it.

{% stepper %}
{% step %}
### ESX

{% embed url="https://github.com/esx-framework/esx_society" %}
{% endstep %}

{% step %}
### QBCore

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

This asset must always be started below your framework and inventory. Failure to do so may result in functionality issues or critical errors. To ensure smooth operation and proper initialization, it is recommended to start the entire download folder using "ensure \[banking]" in your server.cfg.

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
DROP TABLE IF EXISTS `bank_process`;
CREATE TABLE `bank_process` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `owner` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `type` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `icon` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `text` TEXT NOT NULL COLLATE 'utf8mb4_unicode_ci',
    `created` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_unicode_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

DROP TABLE IF EXISTS `bank_cards`;
CREATE TABLE `bank_cards` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `identifier` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `cardNumber` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `ownerName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `valid` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `cardType` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `active` INT(11) NOT NULL DEFAULT '0',
    `passCode` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

DROP TABLE IF EXISTS `bank_history`;
CREATE TABLE `bank_history` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `identifier` VARCHAR(50) NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
    `amount` INT(11) NOT NULL DEFAULT '0',
    `type` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
    `date` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB;
```

</details>

<details>

<summary>Database for qbcore</summary>

```sql
DROP TABLE IF EXISTS `bank_process`;
CREATE TABLE `bank_process` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `owner` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `type` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `icon` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    `text` TEXT NOT NULL COLLATE 'utf8mb4_unicode_ci',
    `created` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'utf8mb4_unicode_ci',
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_unicode_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

DROP TABLE IF EXISTS `bank_cards`;
CREATE TABLE `bank_cards` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `identifier` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `cardNumber` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `ownerName` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `valid` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `cardType` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    `active` INT(11) NOT NULL DEFAULT '0',
    `passCode` VARCHAR(50) NOT NULL DEFAULT '0' COLLATE 'utf8mb4_general_ci',
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB AUTO_INCREMENT = 1;

DROP TABLE IF EXISTS `bank_history`;
CREATE TABLE `bank_history` (
    `id` INT(11) NOT NULL AUTO_INCREMENT,
    `identifier` VARCHAR(50) NULL DEFAULT '' COLLATE 'utf8mb4_general_ci',
    `amount` INT(11) NOT NULL DEFAULT '0',
    `type` VARCHAR(50) NULL DEFAULT NULL COLLATE 'utf8mb4_general_ci',
    `date` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
    PRIMARY KEY (`id`) USING BTREE
) COLLATE = 'utf8mb4_general_ci' ENGINE = InnoDB;

DROP TABLE IF EXISTS `bank_accounts`;
CREATE TABLE IF NOT EXISTS `bank_accounts` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(11) DEFAULT NULL,
  `account_name` varchar(50) DEFAULT NULL,
  `account_balance` int(11) NOT NULL DEFAULT 0,
  `account_type` enum('shared','job','gang') NOT NULL,
  `users` longtext DEFAULT '[]',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE KEY `account_name` (`account_name`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

DROP TABLE IF EXISTS `bank_statements`;
CREATE TABLE IF NOT EXISTS `bank_statements` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(11) DEFAULT NULL,
  `account_name` varchar(50) DEFAULT 'checking',
  `amount` int(11) DEFAULT NULL,
  `reason` varchar(50) DEFAULT NULL,
  `statement_type` enum('deposit','withdraw') DEFAULT NULL,
  `date` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`id`) USING BTREE,
  KEY `citizenid` (`citizenid`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

</details>

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>

***

## Society Configuration

Quasar Banking includes a Society system to manage jobs and organizations, compatible with both **ESX** and **QBCore** frameworks. Follow these steps to configure and use it effectively:

{% stepper %}
{% step %}
### Enabling the Society System

* To enable societies, set `Config.EnableSociety` to `true` in the configuration file.
{% endstep %}

{% step %}
### ESX Framework

* If you are using **ESX**, the asset will integrate directly with **esx\_society**. No additional configuration is required, as societies will function seamlessly with the default ESX society system.
{% endstep %}

{% step %}
### QBCore Framewor**k**

* If you are using **QBCore**, you must **remove `qb-management`** from your server, as **qs-banking** replaces its functionality.
* **Quasar Banking** provides all necessary events and exports that were originally handled by `qb-management`, ensuring a smooth transition.
{% endstep %}

{% step %}
### Key Notes

* Make sure to only enable the society system for the framework you are using.
* Properly test the integration to avoid conflicts with leftover resources or configurations from removed assets like `qb-management`.
{% endstep %}
{% endstepper %}

This setup ensures a seamless and optimized experience for managing societies across your server.
