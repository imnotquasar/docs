# Job Garages

**Job garages** are specialized garages designed for specific jobs like police, ambulance, or mechanics. These garages allow vehicles to be customized with specific liveries, tuning, or extras based on the job requirements. Vehicles stored in these garages are job-specific and cannot be accessed from other garages or impounds.

***

## **Creating Job Garages**

You can configure job garages directly in the `config.lua` file under `Config.JobGarages`. The basic structure includes the job type, garage name, accessible grades, spawn coordinates, and a list of vehicles with optional tuning, liveries, and extras. For example:

{% stepper %}
{% step %}
### **Job-Specific Vehicles**

Assign vehicles to the garage based on the job.
{% endstep %}

{% step %}
### **Custom Tuning**

Apply pre-configured modifications like engine upgrades, brakes, or window tints.
{% endstep %}

{% step %}
### **Exclusive Extras**

Define which extras (lights, sirens, etc.) are enabled for each vehicle.
{% endstep %}

{% step %}
### **Garage Cameras**

Add cinematic cameras for a polished experience.
{% endstep %}
{% endstepper %}

***

## **Job Garages with Stock**

Job garages can include a **vehicle stock system**, where the number of available vehicles is limited. This feature is particularly useful for jobs with multiple workers. Here’s how it works:

{% stepper %}
{% step %}
### **Stock Limits**

Vehicles are limited to the stock defined in the job garage. Workers need to coordinate to ensure availability.
{% endstep %}

{% step %}
### **Garage-Specific Storage**

Vehicles must be stored in the specific job garage they belong to. They cannot be stored in public garages or impounds.
{% endstep %}

{% step %}
### **Impound Exemption**

If a vehicle is removed using `/mdv` or `/mdvall`, it will automatically return to the assigned job garage.
{% endstep %}
{% endstepper %}

***

## **Managing Job Garage Stock**

A **boss** or **authorized role** can manage the stock of vehicles for the job garage.

{% stepper %}
{% step %}
### **Steps to Add Vehicles**

1. Spawn the desired vehicle.
2. Use the `/addJobVehicle` command to add it to the job garage as stock.
{% endstep %}

{% step %}
### **Steps to Remove Vehicles**

1. Go to the job garage.
2. Use the `/deleteJobVehicle` command to access a menu and remove specific vehicles from the stock.
{% endstep %}
{% endstepper %}

***

## **Commands Overview**

<table><thead><tr><th width="242">Command</th><th>Description</th></tr></thead><tbody><tr><td>/addJobVehicle</td><td>Adds the current vehicle to the job garage as stock.</td></tr><tr><td>/deleteJobVehicle</td><td>Removes a selected vehicle from the job garage.</td></tr></tbody></table>
