# Interface Customization

**Quasar Interface** allows players to customize their interface settings before they start playing. This process only happens the first time a player enters the world, ensuring that each user has the opportunity to set up their preferred visual experience right from the start.

***

## **Change the Default Color**

The customization process is fully automated and simple. If you want to change the main color of the interface, you can do so by editing the **root.css** file. Simply search for the `--motive` variable, where you can adjust the color to your preference.

<figure><img src="../../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

***

## **Edit Configurations in config.lua**

Many of these settings can also be adjusted directly in the **config.lua** file. This file allows you to make changes to the interface and other features without the need to modify individual files.

***

## **Player Default Settings (Config.Shared.PlayerSettings)**

It's important to note that `Config.Shared.PlayerSettings` does not refer to the customization settings of this menu. Instead, it represents the default settings for each player in case no customization has been applied yet.

***

## **Editing Loadscreen Title**

The title of the loadscreen can be customized in the **Config.ServerName** option or within the _locales/ files_\*. This allows you to modify the server name that appears during the loading process.
