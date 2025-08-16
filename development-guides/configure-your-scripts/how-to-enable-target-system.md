# How to enable target system

## **Target System**

All Quasar Store assets use the same target system for consistency and ease of use. To prevent errors, we have standardized the configuration and provided clear options for supported systems.

***

## **Supported Target Systems**

We are compatible with the following target systems:

{% stepper %}
{% step %}
### ox\_target

The most stable and reliable target system currently available.

{% embed url="https://github.com/overextended/ox_target" %}
{% endstep %}

{% step %}
### qb-target

Another widely used and supported system.

{% embed url="https://github.com/qbcore-framework/qb-target" %}
{% endstep %}
{% endstepper %}

Please always keep your targets updated to the latest available version.

***

## **How To Enable The Target System**

All Quasar Store assets come with built-in support for target systems, allowing for seamless interaction with entities, objects, and more within your server. This configuration provides flexibility by supporting the two most popular target systems in FiveM: **ox\_target** and **qb-target**.

{% stepper %}
{% step %}
### Locate the Config File

Open the config.lua file for the asset you want to configure. This file contains all the adjustable settings for that specific resource.
{% endstep %}

{% step %}
### Enable the Target System

Look for the following configuration line in config.lua:

```lua
Config.UseTarget = false
```

Change the value from false to either 'ox\_target' or 'qb-target', depending on the target system you are using. For example:

```lua
Config.UseTarget = 'ox_target'
```
{% endstep %}

{% step %}
### Choose Your Target System

After selecting your preferred target system, save the changes to the config.lua file.
{% endstep %}

{% step %}
### Restart the Resource

Restart the asset or your entire server to apply the updated configuration.
{% endstep %}
{% endstepper %}

***

## **Editing Or Customizing Your Target System**

Quasar Store assets provide flexibility for advanced users who wish to modify or create custom target systems. All configurations for the target system are located in the directory client/custom/target/\*.

These files are **open source**, allowing you to:

{% stepper %}
{% step %}
### Edit Existing Configurations

You can adjust or refine the default target configurations to better suit your server’s requirements. For example:

* Modify interaction ranges or options.
* Adjust the target zones for objects, entities, or vehicles.

Make changes directly within the files located in the `client/custom/target/` folder.
{% endstep %}

{% step %}
### Create New Target Systems

If you use a target system not supported by default (e.g., custom-built or less common systems), you can create entirely new configurations within the same folder. Use the provided files as examples or templates to build your custom target system.
{% endstep %}

{% step %}
### Important Warnings

* **Edit At Your Own Risk**: While customization is encouraged, making changes can cause unexpected issues. Only experienced developers should modify these files.
* **No Support for Custom Changes**: Quasar Store cannot provide support for problems arising from edits or customizations to these files.
* **Backup Files**: Always create backups of the original files before making any modifications. This ensures you can revert to a functional state if something goes wrong.
{% endstep %}
{% endstepper %}
