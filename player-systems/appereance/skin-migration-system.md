# Skin Migration System

{% hint style="success" %}
If you are already using `illenium-appearance`, no migration is necessary — `qs-appearance` is **automatically compatible** with it and will take over without any extra steps.
{% endhint %}

If your server previously used clothing systems like `qb-clothing`, `esx_skin`, or `fivem-appearance`, you can easily migrate existing player skins to work with `qs-appearance` using the built-in `/migrateskins` command. This ensures your player base retains their character look without needing to recreate it from scratch.

***

## **How to Use the Migration Command** <a href="#generic-vending-machines-code" id="generic-vending-machines-code"></a>

{% hint style="warning" %}
This command should be executed only once after switching systems. After migration, make sure to remove or disable the old clothing scripts to prevent data conflicts.
{% endhint %}

To convert existing skin data from older systems, simply use the following command in-game:

```lua
/migrateskins
```

This will scan your player database and convert all stored appearance data from the following supported systems:

{% stepper %}
{% step %}
### qb-clothing
{% endstep %}

{% step %}
### esx\_skin
{% endstep %}

{% step %}
### fivem-appearance
{% endstep %}
{% endstepper %}

All migrated skins will then be stored in the format used by `qs-appearance`, allowing a seamless transition for your players.

***

## How to Use the Outfit Migration Command

{% hint style="info" %}
**Important:** The `/migrateoutfits` command is only compatible with servers that previously used **illenium-appearance**. If you were using other systems, this command will not apply.
{% endhint %}

If you are switching from **illenium-appearance** and previously used its outfit system (saved presets), you can transfer all outfits seamlessly using the built-in `/migrateoutfits` command.

This migration is optional and intended for those who wish to retain previously saved outfits under the new qs-appearance system.

To migrate, simply execute the following command in-game:

```lua
/migrateoutfits
```

This will detect and convert all outfits saved under the illenium-appearance format into the qs-appearance compatible structure. Once complete, players will be able to access their old outfits from the wardrobe menu as usual.
