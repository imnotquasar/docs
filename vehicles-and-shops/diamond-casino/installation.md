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
### ox\_lib (use the latest version)

{% embed url="https://github.com/overextended/ox_lib/releases" %}
{% endstep %}

{% step %}
### xsound

{% embed url="https://github.com/Xogy/xsound" %}
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

{% hint style="warning" %}
However, it’s important that **bob74\_ipl** always stays above this line to avoid conflicts.
{% endhint %}

To ensure **Quasar Diamond Casino** works correctly, you must add `ensure [casino]` in your **server.cfg** below your framework and inventory.&#x20;

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## **Database Installation**

For this step, we highly recommend using **HeidiSQL** to avoid issues, as it provides an updated version of MariaDB. We have a guide that explains step-by-step how to use HeidiSQL. If you choose to use phpMyAdmin, we will not be responsible for any errors that may occur in your database.

{% content-ref url="../../development-guides/before-you-start/how-to-install-heidisql.md" %}
[how-to-install-heidisql.md](../../development-guides/before-you-start/how-to-install-heidisql.md)
{% endcontent-ref %}

It is essential to execute the SQL file completely for this asset to function correctly.

<details>

<summary>Add only for companies in esx</summary>

```sql
INSERT INTO
    `addon_inventory` (name, label, shared)
VALUES
    ('casino', 'Casino', 0);

INSERT INTO
    `datastore` (name, label, shared)
VALUES
    ('casino', 'Casino', 0);
```

</details>

```sql
DROP TABLE IF EXISTS `casino_memberships`;

CREATE TABLE `casino_memberships` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`identifier` VARCHAR(90) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`chips` INT(11) NOT NULL DEFAULT '0',
	`vip` TINYINT(1) NULL DEFAULT '0',
	`luckywheel_date` TIMESTAMP NULL DEFAULT current_timestamp(),
	`chip_buy_date` TIMESTAMP NULL DEFAULT current_timestamp(),
	PRIMARY KEY (`id`) USING BTREE,
	UNIQUE INDEX `identifier` (`identifier`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
AUTO_INCREMENT=1
;

DROP TABLE IF EXISTS `casino_blocked_players`;

CREATE TABLE `casino_blocked_players` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`identifier` VARCHAR(90) NOT NULL DEFAULT '0' COLLATE 'utf8mb3_general_ci',
	`reason` TEXT NULL DEFAULT NULL COLLATE 'utf8mb3_general_ci',
	PRIMARY KEY (`id`) USING BTREE
)
COLLATE='utf8mb3_general_ci'
ENGINE=InnoDB
;
```

<figure><img src="../../.gitbook/assets/ezgif-7-08fed20fdc.gif" alt=""><figcaption></figcaption></figure>
