# Electric Vehicles

Quasar Fuel Stations supports electric vehicles with a customizable charging system. This system includes predefined charging stations, specific charging rates, and vehicle offsets for accurate charging point placement. Below is a guide to configuring the electric vehicle system in your server.

***

## **Configuring Electric Charging Stations**

Electric charging stations are defined in `Config.ChargeStations`. Each station has specific coordinates and a model that acts as the charging point.

### **Adding a New Charging Station**

To add a new electric charging station:

{% stepper %}
{% step %}
#### Locate the `Config.ChargeStations` section.
{% endstep %}

{% step %}
#### Add a new entry with the following details:

* `coords`: Location of the charging station in `vector4(x, y, z, heading)` format.
* `model`: The model of the electric charger (e.g., `electric_charger`).
{% endstep %}
{% endstepper %}

```lua
Config.ChargeStations = {
    {
        coords = vector4(175.9, -1546.65, 28.26, 224.29),
        model = `electric_charger`
    },
    {
        coords = vector4(-51.09, -1767.02, 28.26, 47.16),
        model = `electric_charger`
    }
    -- Add more stations here
}
```

***

## **Charging Rate**

The charging rate determines how quickly electric vehicles regain energy. Adjust this value in `Config.ChargeRate` to set the desired speed of charging.

### **Key Parameter**

{% stepper %}
{% step %}
### Config.ChargeRate

Defines the charge rate per second. For example, a value of `1.8` charges the vehicle from 0% to 100% in approximately 56 seconds.
{% endstep %}
{% endstepper %}

```lua
Config.ChargeRate = 1.8 -- Charging rate per second
```

***

## **Custom Offsets for Electric Vehicles**

Electric vehicles may have unique designs requiring precise nozzle placement. Use `Config.CustomOffsets` to configure offsets for specific vehicles.

### **Adding Custom Offsets**

To add offsets for a specific vehicle:

{% stepper %}
{% step %}
#### Locate the `Config.CustomOffsets` section.
{% endstep %}

{% step %}
#### Add an entry with the vehicle model as the key and offsets as `vec3(x, y, z)`.
{% endstep %}
{% endstepper %}

```lua
Config.CustomOffsets = {
    ['tesla_model3'] = {
        vec3(-0.9, -1.3, 0.5), -- First nozzle position
        vec3(0.9, -1.3, 0.5)   -- Second nozzle position
    },
    ['voltic'] = {
        vec3(-0.8, -0.5, 0.6),
        vec3(0.8, -0.5, 0.6)
    }
}
```

***

## **Fuel Type Configuration**

Electric vehicles use the `electric` fuel type. By default, this is automatically assigned based on the model. The configuration for fuel types is managed through `model_fuel_types.json`.

### **Key Information**

{% stepper %}
{% step %}
### **Fuel Consumption**

Defined in `Config.FuelConsumption['electric']`. Example: `5.0` for faster consumption.
{% endstep %}

{% step %}
### **Dynamic Assignment**

Models and their fuel types are mapped in `model_fuel_types.json`.
{% endstep %}
{% endstepper %}

***

## **Integrating Electric Chargers**

To fully integrate the electric charging system:

{% stepper %}
{% step %}
#### Ensure the `electric_charger` model is installed and accessible.
{% endstep %}

{% step %}
#### Add `electric_charger` stations to `Config.ChargeStations`.
{% endstep %}

{% step %}
#### Verify vehicle models are correctly mapped to the `electric` fuel type in `model_fuel_types.json`.
{% endstep %}
{% endstepper %}
