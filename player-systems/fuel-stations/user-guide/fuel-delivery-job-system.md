# Fuel Delivery Job System

Quasar Fuel Stations includes a dynamic **Fuel Delivery Job System**, allowing players to manage gas station supplies by refueling stations. This system adds an engaging gameplay mechanic while requiring players to maintain operational gas stations.

***

## **How to Enable the Fuel Delivery Job System**

The job system is disabled by default. To enable it:

{% stepper %}
{% step %}
### Locate the following line in your configuration file

```lua
Config.EnableJob = false
```
{% endstep %}

{% step %}
### Change the value to `true`

```lua
Config.EnableJob = true
```
{% endstep %}
{% endstepper %}

***

## **Key Features**

{% stepper %}
{% step %}
### **Station Fuel Levels**

Each gas station has its own fuel level, and players must refill stations to keep them operational.

* Enable fuel level tracking by setting:

```lua
Config.EveryStationHasFuelLevel = true
```

* If the job system is disabled, this feature will automatically be turned off.
{% endstep %}

{% step %}
### **Fuel Level Depletion**

* Each time a jerrycan is purchased or a vehicle is refueled, the station's fuel level decreases.
* Configure depletion rates:

```lua
Config.JerryCanStationLevel = 20 -- Reduction per jerrycan purchase
Config.DivideStationLevel = 2    -- Higher values = slower depletion
```
{% endstep %}
{% endstepper %}

***

## **Job Workflow**

Players take on the role of fuel delivery personnel. Here's how the system works:

{% stepper %}
{% step %}
### **Start the Job**

* Players can begin the job by interacting with the designated NPC.
* Configure the NPC's location and appearance:

```lua
Config.PedType = 'a_m_m_ktown_01' -- Ped model
Config.PedCoords = vector4(1721.87, -1557.67, 111.65, 243.12) -- Ped location
```

* The job NPC will appear as a blip on the map:

```lua
Config.JobBlip = {
    title = 'Fuel Delivery',
    color = 12,
    coords = vec3(1721.87, -1557.67, 111.65),
    id = 477
}
```
{% endstep %}

{% step %}
### **Acquire the Truck and Tanker**

* Players must rent or spawn the delivery vehicles:
  *   **Truck**:

      ```lua
      Config.TruckToSpawn = 'packer' -- Model of the truck
      Config.TruckPrice = 5000       -- Rental cost
      ```
  *   **Tanker**:

      ```lua
      Config.TrailerToSpawn = 'tanker2' -- Model of the tanker
      Config.TankPrice = 2000          -- Rental cost
      ```
  *   Spawn locations:

      ```lua
      Config.TruckSpawnLocation = vec4(1733.08, -1556.68, 112.66, 252.0)
      Config.TankerSpawnLocation = vec4(1738.34, -1530.89, 112.65, 252.0)
      ```
{% endstep %}

{% step %}
### **Refuel the Tanker**

* The player must refill the tanker before delivering fuel to stations:

```lua
Config.RefuelLocation = vec4(1688.59, -1460.29, 111.65, 254.5) -- Refuel point
Config.RefuelDuration = 15000 -- Time to refuel in milliseconds
```


{% endstep %}

{% step %}
### **Deliver Fuel**

* Players drive the tanker to gas stations to refill their supplies.
*   Each delivery increases the station's fuel level by a random value:

    ```lua
    Config.AddStationFuelLevel = { 10, 20 } -- Min and max fuel level increase
    ```
*   After completing a delivery, players earn money:

    ```lua
    Config.PayPerFueling = math.random(1200, 2500) -- Random payout per station
    Config.PayType = 'bank' -- Payment method ('money' or 'bank')
    ```
{% endstep %}
{% endstepper %}

***

## **Managing the Job System**

{% stepper %}
{% step %}
### **Maximum Deliveries**

Define how many deliveries a player can complete before refueling their tanker:

```lua
Config.MaxFuelDeliveries = 5
```
{% endstep %}

{% step %}
### **Adjusting Payment**

Modify the amount players earn per delivery:

```lua
Config.PayPerFueling = math.random(1200, 2500) -- Payment range
```
{% endstep %}

{% step %}
### **Debugging**&#x20;

Enable debug mode to monitor job-related mechanics:

```lua
Config.Debug = true -- General debug information
Config.ZoneDebug = true -- Zone-specific debug info
```
{% endstep %}
{% endstepper %}

***

## **Important Notes**

* Players cannot begin deliveries if all gas stations are full.
* Ensure the truck and tanker models are compatible with trailers and fuel delivery mechanics.
* If Config.EnableJob is disabled, the fuel levels for stations will not decrease.

By following this guide, you can create an immersive and engaging fuel delivery experience for your players.
