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

This asset must always be started below your framework and inventory in your server.cfg. Additionally, any robbery scripts that use dispatch exports must also be started after **"ensure \[dispatch]"**.&#x20;

Failure to follow this order may result in functionality issues or critical errors. It is highly recommended to maintain this sequence to ensure proper initialization and smooth operation.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

Select the framework you are using and then execute the SQL in your HeidiSQL. If you encounter errors, ensure you are using the most current version of MariaDB. You can refer to our guide above or search online.

```sql
DROP TABLE IF EXISTS `dispatch_callsigns`;
CREATE TABLE IF NOT EXISTS `dispatch_callsigns` (
  `identifier` varchar(46) NOT NULL,
  `callsign` varchar(50) NOT NULL,
  PRIMARY KEY (`identifier`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_cameras`;
CREATE TABLE IF NOT EXISTS `dispatch_cameras` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(25) DEFAULT NULL,
  `model` varchar(50) NOT NULL,
  `coords` varchar(255) NOT NULL,
  `type` varchar(50) DEFAULT NULL,
  `metadata` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin NOT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=23 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_jail_database`;
CREATE TABLE IF NOT EXISTS `dispatch_jail_database` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `player_identifier` varchar(255) NOT NULL,
  `jail_reason` varchar(255) NOT NULL,
  `jail_time` int(11) NOT NULL,
  `jail_start` timestamp NOT NULL DEFAULT current_timestamp(),
  `jail_end` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8 COLLATE=utf8_general_ci;

DROP TABLE IF EXISTS `dispatch_mdt_bolos`;
CREATE TABLE IF NOT EXISTS `dispatch_mdt_bolos` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `CreatorName` varchar(50) DEFAULT NULL,
  `jobtype` varchar(25) DEFAULT 'police',
  `title` varchar(50) DEFAULT NULL,
  `content` mediumtext DEFAULT NULL,
  `officers_involved` text DEFAULT NULL,
  `createdAt` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=22 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_mdt_convictions`;
CREATE TABLE IF NOT EXISTS `dispatch_mdt_convictions` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `identifier` varchar(46) DEFAULT NULL,
  `charges` text DEFAULT NULL,
  `warrant` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_mdt_data`;
CREATE TABLE IF NOT EXISTS `dispatch_mdt_data` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `identifier` varchar(46) DEFAULT NULL,
  `tags` text NOT NULL,
  `jobtype` varchar(25) DEFAULT 'police',
  `pfp` text DEFAULT NULL,
  `notes` mediumtext DEFAULT NULL,
  KEY `id` (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_mdt_incidents`;
CREATE TABLE IF NOT EXISTS `dispatch_mdt_incidents` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `CreatorName` varchar(50) DEFAULT NULL,
  `jobtype` varchar(25) DEFAULT 'police',
  `title` varchar(50) DEFAULT NULL,
  `content` mediumtext DEFAULT NULL,
  `citizens_involved` text DEFAULT NULL,
  `criminals_involved` text DEFAULT NULL,
  `officers_involved` text DEFAULT NULL,
  `createdAt` varchar(50) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=22 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_players_database`;
CREATE TABLE IF NOT EXISTS `dispatch_players_database` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `identifier` longtext NOT NULL,
  `datatype` varchar(1200) NOT NULL DEFAULT 'undefinedData',
  `dataobj` longtext NOT NULL,
  `createdAt` varchar(50) NOT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

DROP TABLE IF EXISTS `dispatch_vehicle_database`;
CREATE TABLE IF NOT EXISTS `dispatch_vehicle_database` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `datatype` varchar(50) DEFAULT NULL,
  `by` varchar(50) DEFAULT NULL,
  `plate` varchar(50) NOT NULL,
  `data` longtext DEFAULT NULL,
  `createdAt` varchar(150) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc (1).gif" alt=""><figcaption></figcaption></figure>
