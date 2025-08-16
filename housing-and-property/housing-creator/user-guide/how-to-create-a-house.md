# How to create a house

Quasar Housing is more than just a housing system; it’s a versatile creation system that allows you to dynamically create houses and objects anywhere on the map.

{% stepper %}
{% step %}
### Get the job first

You must first get the job with the command `/setjob [id] realestate 0`.
{% endstep %}

{% step %}
### Press F7 (by default)

Once we have the job, we press the F7 key and we will see the complete menu.
{% endstep %}
{% endstepper %}

***

## **Worker Configuration**

To enable housing creation, specific jobs must be assigned in the configuration. These jobs will be allowed to create homes using a default key mapping F7 or a custom key set in Config.OpenJobMenu.

Below is an example of assigning jobs allowed to create houses:

```lua
Config.CreatorJobs = { -- Jobs authorized for house creation
    'realestate',
    'police',
    'realestatejob'
}
```

By assigning these jobs, workers like real estate agents or police can access the housing creation menu seamlessly.
