# In-Game Crafting Setup

This method allows you to **create and manage crafting tables directly in-game**, using an interactive UI designed for ease of use. No need to edit code or search item names — everything is integrated visually with item images, blip positioning, and live placement.

***

## Job Access Configuration

To restrict who can create tables, configure the following option in your `config.lua`:

```lua
Config.CreatorJobs = { -- Jobs allowed to create crafting tables
    'realestate',
    'police',
}
```

{% hint style="warning" %}
Only players with these jobs and admins will be able to access the crafting creator menu.
{% endhint %}

If you want the system to be **open to all admins regardless of job**, simply **clear the table**:

```lua
Config.CreatorJobs = {}
```

***

## Accessing the Creator Menu

Once you meet the job or admin requirement, open the crafting creator menu using:

```
/crafting_creator
```

Or by pressing the **keybind** you’ve configured in `config.lua`.

***

## What You Can Do In-Game

Inside the menu, you'll find a **fully interactive UI** that allows you to:

* Select the crafting table object with live preview.
* Position it precisely in the world with blip placement.
* Add item recipes by simply clicking on images.
* View materials required for each recipe with auto-complete support.
* Assign job and grade restrictions (optional).
* Save everything to config with a single click.

You **don’t need to search for item names or coordinates manually** — the system handles everything for you visually.

{% hint style="success" %}
This method is ideal for staff members or developers who want fast, intuitive control without touching code.
{% endhint %}
