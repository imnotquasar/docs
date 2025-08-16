# Public Garages

Quasar Advanced Garages supports the creation of **public garages**, which are accessible to all players. You can add these garages either via in-game tools or by editing the `config.lua` file directly for more complex setups. Below, we'll guide you through the process and highlight the key components.

***

## **Creating Public Garages**

{% stepper %}
{% step %}
**In-Game Creator**

Use the in-game creation menu, as detailed in the previous documentation. This is a straightforward way to set up public garages with minimal configuration. Simply open the menu, select "Create Garage," and follow the prompts to set up the name, type, and location.
{% endstep %}

{% step %}
**Manual Configuration**

For more control and customization, you can add public garages directly to `config.lua`. This approach is ideal for developers comfortable with editing server files and allows for features like cinematic cameras, polyzones, and job restrictions.
{% endstep %}
{% endstepper %}

***

## **Example Configuration**

The following configuration demonstrates how to define a public garage in config.lua. Use this as a reference when adding new garages:

* **Garage Name**: Set a unique name (e.g., Pinkie Pie Garage) for internal use in SQL and blips.
* **Ownership**: Set owner = false for public garages.
* **Availability**: Ensure available = true so all players can access it.
* **Job Restriction**: Leave job = false for unrestricted access or specify a job (e.g., 'police') for exclusive garages.
* **Type**: Choose from vehicle, boat, or plane depending on the garage's purpose.
* **Coordinates**: Define menu and spawn locations, and use Config.ZoneDebug for polyzone setup.
* **Camera Settings**: Optionally configure vehicle cameras and cinematic effects for added immersion.

***

## **Tips for Configuration**

{% stepper %}
{% step %}
### **Reuse Existing Examples**

Start by duplicating and modifying existing garage configurations in `config.lua`. This ensures compatibility and consistency.
{% endstep %}

{% step %}
### **Debugging**

Use `Config.Debug` and `Config.ZoneDebug` to verify your garage setup visually in-game.
{% endstep %}

{% step %}
### **Polyzone Setup**

Carefully define the `points` to outline the garage area. Ensure the Z-coordinate matches the intended height for the zone.
{% endstep %}
{% endstepper %}
