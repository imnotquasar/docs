# How to create hospitals

In **Quasar Hospital Creator**, administrators have the ability to create and manage hospitals directly in-game. This feature provides flexibility for server staff to design and place hospitals without manual database edits. Follow this guide to learn how to open the creation menu and start building hospitals.

Before creating a hospital, ensure you know:

{% stepper %}
{% step %}
**Only administrators** can open the hospital creation menu.
{% endstep %}

{% step %}
The **default hospital** included with the script is **only editable via `config.lua`** and cannot be modified in-game.
{% endstep %}
{% endstepper %}

***

## Creating a Hospital

To create a hospital in-game, follow these steps:

{% stepper %}
{% step %}
### Access the Hospital Creator Menu

* Use the `/hospital_creator` command as an administrator or Config.CreatorJobs.
* This will open the creation interface where you can add new hospitals.
{% endstep %}

{% step %}
### Customize the Hospital

* Inside the menu, you can define the hospital’s name, location, and layout.
* Place interaction points such as **healing areas, beds, or NPCs**.
{% endstep %}

{% step %}
### Save the Hospital

* Once finished, save your hospital to make it available to players.
* The new hospital will be added dynamically and does not require a restart.
{% endstep %}
{% endstepper %}

***

## Important Notes

⚠️ The **default hospital** that comes with the script cannot be edited in-game. If you need to modify it, changes must be made directly in **`config.lua`**.

***

## Who Can Create Hospitals?

Only **administrators** with access to the `/hospital_creator` command can create and edit hospitals in-game. Regular players cannot use this feature unless permissions are explicitly granted.
