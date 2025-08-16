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

To ensure proper functionality, \[advancedracing] must be started directly below your framework and inventory folders. This guarantees smooth initialization and prevents potential conflicts.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

It is essential to execute the SQL file completely for this asset to function correctly.

```sql
CREATE TABLE IF NOT EXISTS `racing_competitions` (
	`id` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`track_id` INT(11) NOT NULL DEFAULT '0',
	`creator_id` INT(11) NOT NULL DEFAULT '0',
	`laps` SMALLINT(6) NOT NULL DEFAULT '1',
	`type` SMALLINT(6) NOT NULL DEFAULT '0',
	`vehicle_class` SMALLINT(6) NOT NULL DEFAULT '0',
	`prize` INT(11) NOT NULL DEFAULT '0',
	`timestamp` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
	`start_time` TIMESTAMP NULL DEFAULT NULL,
	`automated_id` INT(11) NULL DEFAULT NULL,
	INDEX `id` (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
;

CREATE TABLE IF NOT EXISTS `racing_favorite_tracks` (
	`track_id` INT(11) NOT NULL,
	`user_id` INT(11) NOT NULL,
	`favorite` TINYINT(1) NULL DEFAULT NULL,
	UNIQUE INDEX `track_id_user_id` (`track_id`, `user_id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
;

CREATE TABLE IF NOT EXISTS `racing_race_finishers` (
	`race_id` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`user_id` INT(11) NOT NULL,
	`track_id` INT(11) NULL DEFAULT NULL,
	`vehicle_name` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`vehicle_class` MEDIUMINT(9) NOT NULL DEFAULT '0',
	`lap_time` INT(11) NOT NULL DEFAULT '0',
	`finish_time` INT(11) NOT NULL DEFAULT '0',
	`rating` INT(11) NOT NULL DEFAULT '0',
	`money_earned` INT(11) NOT NULL DEFAULT '0',
	`elo_change` INT(11) NULL DEFAULT '0',
	`position` INT(11) NOT NULL,
	`timestamp` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
	INDEX `race_id` (`race_id`) USING BTREE,
	INDEX `user_id` (`user_id`) USING BTREE,
	INDEX `track_id` (`track_id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
;

CREATE TABLE IF NOT EXISTS `racing_recent_events` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`title` VARCHAR(50) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`user_id` INT(11) NOT NULL DEFAULT '0',
	`timestamp` TIMESTAMP NOT NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

CREATE TABLE IF NOT EXISTS `racing_tracks` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`title` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`description` TINYTEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`image` TEXT NULL DEFAULT NULL,
	`creator_id` INT(11) NULL DEFAULT NULL,
	`type` SMALLINT(6) NULL DEFAULT NULL,
	`duration` MEDIUMINT(9) NULL DEFAULT NULL,
	`points` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`objects` TEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`verified` TINYINT(1) NULL DEFAULT '0',
	`timestamp` TIMESTAMP NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=8
;

CREATE TABLE IF NOT EXISTS `racing_users` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`identifier` VARCHAR(90) NOT NULL DEFAULT '' COLLATE 'latin1_swedish_ci',
	`avatar` LONGTEXT NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`name` VARCHAR(20) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`elo` MEDIUMINT(9) NULL DEFAULT '0',
	`ranking` MEDIUMINT(9) NULL DEFAULT '0',
	`tag` VARCHAR(50) NULL DEFAULT NULL COLLATE 'latin1_swedish_ci',
	`timestamp` TIMESTAMP NULL DEFAULT current_timestamp(),
	`checkpoint_color` SMALLINT(6) NULL DEFAULT NULL,
	`gps_color` SMALLINT(5) UNSIGNED NULL DEFAULT NULL,
	`races` INT(11) NULL DEFAULT '0',
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `identifier` (`identifier`) USING BTREE
)
COLLATE='latin1_swedish_ci'
ENGINE=InnoDB
AUTO_INCREMENT=983
;
```

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>

***

## Key bind manipulation

All Quasar Store assets use the same process for modifying Key Binds to ensure consistency and optimized performance across all resources.&#x20;

Below is a clear and detailed guide on how to adjust them to your preferences.

{% content-ref url="../../development-guides/configure-your-scripts/how-to-change-key-bindings.md" %}
[how-to-change-key-bindings.md](../../development-guides/configure-your-scripts/how-to-change-key-bindings.md)
{% endcontent-ref %}
