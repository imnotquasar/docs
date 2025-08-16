# Gang Menu and Actions

Quasar Gangs & Territories offers an optional add-on, **qs-gangmenu**, which enhances the aesthetic and functionality of the system. This menu provides intuitive Gang role-based interactions and is fully customizable to work with external asset events.

***

## Default Menu Features

The default configuration includes the following role-based actions:

* **Steal from a player:** Allows members to rob another player's inventory.
* **Escort a player:** Enables dragging an individual.
* **Handcuff a player:** Restricts player movement by applying handcuffs.
* **Vehicle interactions:** Place or remove players from vehicles.
* **Sales in territories:** Manage drug sales within Gang territories.

***

## Customization Options

The menu is fully configurable, letting you:

{% stepper %}
{% step %}
### Add or remove actions.
{% endstep %}

{% step %}
### Set grade restrictions for specific options.
{% endstep %}

{% step %}
### Create submenus for better organization.
{% endstep %}
{% endstepper %}

Example configuration for a vehicle menu:

```lua
['vehicle'] = {
    name = 'vehicle',
    label = 'Vehicle Options',
    submenu = {
        ['putvehicle'] = {
            name = 'putvehicle',
            label = 'Put in vehicle',
            action = 'event:client:putvehicle',
            grade = { 'soldier', 'underboss', 'boss' }
        },
        ['getvehicle'] = {
            name = 'getvehicle',
            label = 'Get out vehicle',
            action = 'event:client:getvehicle',
            grade = { 'soldier', 'underboss', 'boss' }
        }
    },
}
```

This menu can be tailored to your server’s needs by:

{% stepper %}
{% step %}
### Modifying events triggered by actions.
{% endstep %}

{% step %}
### Adjusting access grades.
{% endstep %}

{% step %}
### Expanding functionality with additional options or submenus.
{% endstep %}
{% endstepper %}

By leveraging **qs-gangmenu**, your Gang system will gain a polished, user-friendly interface that enhances gameplay immersion.
