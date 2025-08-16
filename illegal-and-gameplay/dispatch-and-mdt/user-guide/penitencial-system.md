---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Penitencial System

The **Penitentiary System** introduces a **GTA V-style chase system with wanted stars**, activated when criminal charges are assigned to a player and they manage to escape. This system works independently and integrates seamlessly with your police workflow.

***

## Key Features

{% stepper %}
{% step %}
### Chase System

Players assigned criminal charges who escape will trigger a chase system with visual search stars. (Currently manual, automatic assignment is coming soon.)
{% endstep %}

{% step %}
### Standalone Jail System

This system does not require any external jail scripts, making it fully functional on its own.
{% endstep %}

{% step %}
### Customizable Settings

The configuration allows you to:

* Specify jobs permitted to send players to jail.
* Set jail locations and prisoner spawn/exit points.
* Manage illegal items confiscated upon arrest.
* Adjust how long search stars persist out of camera view.
{% endstep %}

{% step %}
### Default Compatibility

This feature is only active if `Config.MDT.newMdt` is set to `false`.
{% endstep %}
{% endstepper %}

***

## Default Configuration

{% stepper %}
{% step %}
### keyForSendToJail

Keybind for sending a player to jail (default: **E**).
{% endstep %}

{% step %}
### JobsAllowedToSendToJail

List of jobs authorized to use the jail system.
{% endstep %}

{% step %}
### TimeToRemoveCodes

Timed removal of search stars when the player is out of camera view.
{% endstep %}

{% step %}
### IlegalItems

Items automatically confiscated upon arrest.
{% endstep %}

{% step %}
### CanSendToJailIfNotInPoint

If set to `true`, allows sending players to jail even if they’re not at the designated point.
{% endstep %}
{% endstepper %}

***

## **Jail Points**

You can configure multiple jail locations:

```lua
SendToJailPoints = {
    { title = 'Mission Row PD', coords = vector3(460.0216, -1001.5779, 24.9149) },
    { title = 'Mission Row PD', coords = vector3(459.1117, -997.9485, 24.9149) },
    { title = 'Mission Row PD', coords = vector3(460.0694, -994.2761, 24.9149) }
}
```

Prison Configuration:

{% stepper %}
{% step %}
### **Jail Name**

Name of the penitentiary (e.g., _Jail of Paleto_).
{% endstep %}

{% step %}
### **Spawn Points**

Coordinates where players appear in jail.
{% endstep %}

{% step %}
### **Exit Points**

Coordinates where players exit jail after serving time.
{% endstep %}
{% endstepper %}

```lua
Jail = {
    name = 'Jail of Paleto',
    radius = 50,
    spawnPoints = { vector4(1678.5844, 2541.4470, 45.5645, 267.97) },
    exitPoints = { vector4(1850.7671, 2586.0156, 45.6720, 274.4039) }
}
```
