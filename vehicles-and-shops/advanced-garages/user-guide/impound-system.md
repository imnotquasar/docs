---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Impound System

Quasar Advanced Garages features a robust impound system that can be used via commands or integrated into third-party systems through exports. This system is ideal for police or administrative roles, enabling the organized management of vehicles sent to impounds.

***

## **Using Impound Commands**

Police and other configured roles (defined in `Config.AllowedJobs`) can use the `/impound` command. This opens a NUI interface that provides detailed options for handling impounds, including:

{% stepper %}
{% step %}
### **Impound Location**

Choose where to send the vehicle.
{% endstep %}

{% step %}
### **Duration**

Set how long the vehicle will remain impounded.
{% endstep %}

{% step %}
### **Waiting Time**

Add any required delay before release.
{% endstep %}

{% step %}
### **Fines**

Set a fine to be paid by the vehicle owner.
{% endstep %}
{% endstepper %}

<table><thead><tr><th width="240">Command</th><th>Description</th></tr></thead><tbody><tr><td>/impound</td><td>Opens the interface to impound a vehicle. Access requires a specific job.</td></tr></tbody></table>

***

## **Using Impound via Internal Code**

For developers or advanced users, impounding vehicles can be managed programmatically through exports. These allow for integration with other systems or automated processes.

{% stepper %}
{% step %}
### **Client-Side Export**

This export impounds the nearest vehicle from the player.

```lua
-- Impound the nearest vehicle
exports['qs-advancedgarages']:ImpoundVehicle()
```
{% endstep %}

{% step %}
### **Server-Side Export**

This export impounds a specific vehicle using its plate number.

```lua
-- Impound a vehicle by its plate
exports['qs-advancedgarages']:impound(plate)
```
{% endstep %}
{% endstepper %}
