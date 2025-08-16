# Casino Job Actions

You can change or customize the casino job directly from the configuration file `config/main.lua`. In the configuration, you will find the following section:

```lua
Config.CasinoJobs = {
    'police' -- Change or add more jobs
}
```

This allows you to set which jobs have access to the casino. Simply replace `'police'` with the job you want to grant access to the casino. You can add multiple jobs by separating them with commas.

To use the casino job in the game, players can simply use the `/casino` command.

***

## Functions Available for Casino Job

Once you assign the casino job, the player will have access to several powerful functions that can manage the casino environment:

{% stepper %}
{% step %}
### Open/Close Casino Doors

The casino job can open or close the casino doors, automatically expelling visitors when closing the doors.
{% endstep %}

{% step %}
### Ban or Unban Players

Admins with the casino job can ban or unban players from entering the casino.
{% endstep %}

{% step %}
### Change Casino Background Music

You can change the background music of the casino to set the mood you prefer.
{% endstep %}

{% step %}
### Change the Presentation Car

You can modify the car used for the casino's presentation, adding a unique touch to the experience.
{% endstep %}

{% step %}
### Change LED Wall Color or Image

Customize the LED walls inside the casino by changing their color or uploading a new image.
{% endstep %}

{% step %}
### View Casino Cameras

Admins can access and view the casino's surveillance cameras to monitor activities and security.
{% endstep %}
{% endstepper %}
