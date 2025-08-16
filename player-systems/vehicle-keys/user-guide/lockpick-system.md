# Lockpick System

The **Lockpick System** in `qs-vehiclekeys` provides immersive mechanics for vehicle theft, allowing players to use lockpicks or advanced tools to break into vehicles. It includes options to integrate police presence, alarms, and item-based requirements for lockpicking.

***

## Police Integration

The system can require a minimum number of police officers on duty before robberies are allowed. Configure these options to enable or disable police integration:

{% stepper %}
{% step %}
### **Config.ReqPolice**

Enable or disable the requirement for police to allow vehicle robberies.
{% endstep %}

{% step %}
### **Config.ReqPoliceCount**

Set the minimum number of police officers required.
{% endstep %}

{% step %}
### **Config.ReqJobPolice**

Specify the police job name (e.g., `'police'`).
{% endstep %}

{% step %}
### **Config.RefreshPolice**

Determine how often the police count is checked (in milliseconds).
{% endstep %}
{% endstepper %}

***

## Lockpick Mechanics

Players can use basic or advanced lockpicks to perform vehicle break-ins. Customize the chances of success, item usage, and alarm triggers:

{% stepper %}
{% step %}
### **Config.LockpickItem**

Define the required item for basic lockpicking.
{% endstep %}

{% step %}
### **Config.LockpickKeepChance**

Set the percentage chance that the lockpick remains intact after use.
{% endstep %}

{% step %}
### **Config.AdvancedLockpickItem**

Enable advanced lockpicks, which bypass the police requirement for robberies.
{% endstep %}
{% endstepper %}

***

## Alarm System

Vehicle alarms add an extra layer of risk, with a configurable chance to alert the police during a robbery:

{% stepper %}
{% step %}
### **Config.LockpickAlarm**

Enable or disable vehicle alarms for theft attempts.
{% endstep %}

{% step %}
### **Config.StartAlarmChance**

Set the percentage chance for the alarm to trigger, sending a dispatch alert to police.
{% endstep %}
{% endstepper %}

***

## Whitelist Exclusions

You can exempt specific vehicles from the lockpick system, ensuring they cannot be broken into:

{% stepper %}
{% step %}
### **Config.LockpickWhitelist**

List vehicles (e.g., `'bmx'`) that are excluded from lockpicking.
{% endstep %}
{% endstepper %}
