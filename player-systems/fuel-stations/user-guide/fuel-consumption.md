# Fuel Consumption

Quasar Fuel Stations provides a flexible system for managing fuel consumption across different vehicle types and fuel categories. This guide explains how to adjust fuel consumption rates to suit your server's needs.

***

## **Fuel Types and Consumption Rates**

The system supports multiple fuel types (`petrol`, `diesel`, `electric`) with customizable consumption rates. These rates are defined in the `Config.FuelConsumption` section.

### **Key Parameters**

* **`petrol`**: Standard gasoline fuel.
* **`diesel`**: Used for diesel-powered vehicles with reduced consumption.
* **`electric`**: Used for electric vehicles with specific charging logic.

### **Example Configuration**

```lua
Config.FuelConsumption = {
    ['petrol'] = 1.0,    -- Standard consumption rate
    ['diesel'] = 0.1,    -- Reduced consumption for diesel
    ['electric'] = 5.0   -- Increased consumption for electric vehicles
}
```

* **Higher Values**: Faster fuel consumption.
* **Lower Values**: Slower fuel consumption.

***

## **Throttle-Based Consumption**

Fuel consumption can vary based on the vehicle's throttle level. This is managed through `Config.VehiclesFuelUsage`.

### **How It Works**

* The throttle intensity determines how much fuel is consumed.
* For example, at full throttle (`1.0`), the consumption rate is higher than at 50% throttle (`0.5`).

### **Example Configuration**

```lua
Config.VehiclesFuelUsage = {
    [1.0] = 0.6, -- Full throttle
    [0.9] = 0.5, -- 90% throttle
    [0.8] = 0.4, -- 80% throttle
    [0.7] = 0.45,
    [0.6] = 0.40,
    [0.5] = 0.35,
    [0.4] = 0.3,
    [0.3] = 0.25,
    [0.2] = 0.2,
    [0.1] = 0.1,
    [0.0] = 0.0  -- Idle (no fuel consumption)
}
```

***

## **Class-Based Consumption**

Vehicles are grouped into classes, each with its own fuel consumption multiplier. Adjust these rates in the `Config.VehiclesClasses` section.

### **Key Parameters**

* `1.0`: Standard consumption rate.
* `0.0`: Disables fuel consumption for that class (e.g., cycles).

### **Example Configuration**

```lua
Config.VehiclesClasses = {
    [0] = 1.0,  -- Compacts
    [1] = 1.0,  -- Sedans
    [2] = 1.0,  -- SUVs
    [3] = 1.0,  -- Coupes
    [4] = 1.0,  -- Muscle
    [5] = 1.0,  -- Sports Classics
    [6] = 1.0,  -- Sports
    [7] = 1.0,  -- Super
    [8] = 1.0,  -- Motorcycles
    [9] = 1.0,  -- Off-road
    [10] = 1.0, -- Industrial
    [11] = 1.0, -- Utility
    [12] = 1.0, -- Vans
    [13] = 0.0, -- Cycles (No fuel consumption)
    [14] = 1.0, -- Boats
    [15] = 1.0, -- Helicopters
    [16] = 1.0, -- Planes
    [17] = 1.0, -- Service
    [18] = 1.0, -- Emergency
    [19] = 1.0, -- Military
    [20] = 1.0, -- Commercial
    [21] = 1.0, -- Trains
}
```

***

## **Custom Vehicle Consumption**

For specific vehicle models, you can define unique fuel types and consumption rates in the `model_fuel_types.json` file.

### **Steps to Configure**

{% stepper %}
{% step %}
#### Open `model_fuel_types.json`.
{% endstep %}

{% step %}
#### Add or modify entries for specific vehicle models.&#x20;
{% endstep %}
{% endstepper %}

### **Example**

```json
[
    {
        "model": "t20",
        "fuel_type": "petrol"
    },
    {
        "model": "guardian",
        "fuel_type": "diesel"
    }
]
```

***

## **Excluding Vehicles from Fuel Consumption**

To exclude certain vehicles from fuel consumption, list them in `Config.VehiclesBlacklist`.

### **Example Configuration**

```lua
Config.VehiclesBlacklist = {
    'bmx',    -- No fuel consumption for this model
    'airtug',
    'caddy'
}
```

***

## **Real-Time Adjustments**

If you make changes to fuel consumption settings:

{% stepper %}
{% step %}
#### Restart the script for the changes to apply.
{% endstep %}

{% step %}
#### Vehicles already spawned will require respawning to reflect the updated settings.
{% endstep %}
{% endstepper %}

This flexible system ensures you can fine-tune fuel consumption for your server's unique gameplay dynamics.
