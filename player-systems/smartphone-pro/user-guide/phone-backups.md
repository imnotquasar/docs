# Phone Backups

The backup system in **Smartphone PRO** is designed for servers using the Unique Phones feature, providing an automatic and manual way to safeguard player data. It functions similarly to a cloud backup, allowing players to recover data from lost phones seamlessly.

***

## Creating a Backup

Players can create backups by accessing the **Settings** app and navigating to their profile in the first panel. From there, they can create a backup for their phone number. It’s recommended to periodically update the backup by deleting the old one and creating a new one to ensure the latest data is saved.

***

## Deleting a Backup

To delete a backup, right-click on the existing backup in the **Settings** app. This action permanently removes the selected backup but does not affect the phone or its data. Players can create a new backup after deletion.

***

## Automatic Backup System

The asset includes an **automatic backup** feature configured via `Config.Autobackup` in **config.lua**. This feature creates a backup every time the phone is closed, ensuring player data is always up-to-date. The backups can be recovered anytime through the **Settings** app under the player's profile.

```lua
Config.Autobackup = true -- Enable automatic backups when the phone is closed
```

This system ensures player data remains secure and easily recoverable, enhancing gameplay and reducing the risk of data loss.
