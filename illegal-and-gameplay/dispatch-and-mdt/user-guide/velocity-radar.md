# Velocity Radar

The Velocity Radar system provides a dynamic speed monitoring tool for your server, allowing you to enforce speed limits, issue fines, and send alerts to police or MDT systems. Below is a simplified explanation of its configuration.

***

## Key Parameters

{% stepper %}
{% step %}
### General Settings

* `enabled`: Turns the Velocity Radar on or off.
* `activateFXFlash`: Enables flashing visual effects when a speed violation occurs.
* `account`: Defines the account from which fines are deducted (`money`, `bank`, etc.).
* `amount`: Sets the default fine for exceeding speed limits.
* `useMph`: Switches speed units between km/h and mph.
{% endstep %}

{% step %}
### Functions

* **`onDispatchCall`**: Executes when a radar sends a dispatch signal to the police. Customize this function to define how alerts are sent.
* **`onHistoryToMDT`**: Logs speed infractions to the MDT system. This is used to store violators' data, including speed, zone, and fines.
{% endstep %}

{% step %}
### Ignored Jobs

* `ignoredjobs`: Specify jobs (e.g., police, ambulance) that are exempt from speed checks.
{% endstep %}

{% step %}
### Zones

* Each radar zone has a label, coordinates, speed limits, and penalties:
  * `label`: Name of the radar zone.
  * `coords`: Radar's location on the map.
  * `velocityRanges`: Defines speed limits and corresponding fines.
  * `width`: Radius of the radar zone.
  * `beforeEnterInZoneAlert`: Enables warnings before entering a radar zone.
  * `autoBill`: Automatically charges fines to violators.
  * `notifyInfractor`: Notifies the offender of the fine.
  * `sendAlertToPolice`: Sends alerts to police for violations.
  * `sendHistoryToMDT`: Logs violations to the MDT system.
{% endstep %}

{% step %}
### Blip Configuration

* `enabled`: Activates blip visibility on the map.
* `color`: Defines the blip color.
* `sprite`: Specifies the blip icon.
* `scale`: Adjusts blip size.
* `text`: Blip label displayed on the map.
{% endstep %}
{% endstepper %}

***

## Example Zone Configuration

A single radar zone setup might look like this:

```lua
[1] = {
    label = "Zone 1",
    velocityRanges = {
        { limitFrom = 105, price = 8500 },
        { limitFrom = 200, price = 11000 }
    },
    coords = vector3(365.81, 134.43, 103.09),
    width = 30,
    beforeEnterInZoneAlert = true,
    beforeEnterInZoneAlertMargin = 40,
    autoBill = true,
    notifyInfractor = true,
    sendAlertToPolice = true,
    sendHistoryToMDT = true,
    blip = {
        enabled = true,
        color = 3,
        sprite = 184,
        scale = 0.8,
        text = "Velocity Radar"
    }
}
```
