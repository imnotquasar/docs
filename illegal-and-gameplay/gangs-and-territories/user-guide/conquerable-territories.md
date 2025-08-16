# Conquerable Territories

The **Conquerable Territories** system in Quasar Gangs & Territories provides fully customizable zones where gangs can claim dominance. Each territory offers strategic benefits, such as control over drug sales, access to exclusive dealers, and enhanced map visibility for the conquering gang.

{% stepper %}
{% step %}
### **Conquest System**

Territories start as neutral zones and can be claimed by gangs. Once claimed, the territory changes to the gang’s color on the map.
{% endstep %}

{% step %}
### **Dealer System**

Each territory includes a dealer who is only accessible to the dominant gang. The dealer provides missions, drug transportation, and a limited store that expands as reputation increases.
{% endstep %}

{% step %}
### **Drug Sales**

Gang members can sell drugs within their territories. NPCs in the zone will interact dynamically, including bargaining, buying, or even attempting theft.
{% endstep %}
{% endstepper %}

***

## Basic Configuration

The **Territories** are defined in the `config.lua` file, where you can specify:

{% stepper %}
{% step %}
### **Area Dimensions**

Map squares or ox\_lib zones to define the territory.
{% endstep %}

{% step %}
### **Points**

Boundaries of the territory using ox\_lib.
{% endstep %}

{% step %}
### **Conquest Timer**

Time (in seconds) needed to claim a zone.
{% endstep %}

{% step %}
### **Dealers**

Add dealers with active hours and products.
{% endstep %}
{% endstepper %}

***

## Example Configuration

The configuration for each territory includes map squares for visualization, boundary points, dealers, and conquest parameters. Ensure that the `Config.ZoneDebug` is enabled for setting up zones accurately. Territories must be numbered consecutively (`[1]`, `[2]`, `[3]`).

```lua
Config.Territories = {
    [1] = {
        area = {
            { coords = vec3(254.610992, -1972.153809, 21.562622), width = 170.0, height = 85.0, blipRotation = 6.0 },
        },
        points = {
            vec3(342.580231, -1937.947266, 17.8),
            vec3(317.063751, -1970.162598, 17.8),
        },
        minScore = 10,
        winner = 'neutral',
        occupants = {
            ['neutral'] = { label = 'Neutral', score = 60 },
        },
        dealers = {
            ['zone-1'] = {
                name = 'Abel Pintos',
                coords = vector3(267.665955, -1979.446167, 21.461548),
                time = { min = 01, max = 12 },
                products = Config.Products
            }
        }
    },
}
```

***

## Territory Management

{% stepper %}
{% step %}
### **Neutral Zones**

Territories start as neutral, indicated by a white color.
{% endstep %}

{% step %}
### **Conquered Zones**

A gang’s color takes over once the zone is claimed. Conquering a rival’s territory alerts them, initiating a war.
{% endstep %}

{% step %}
### **Dealer Benefits**

Dominant gangs gain exclusive dealer access, which expands with completed missions.
{% endstep %}

{% step %}
### **Dynamic Drug Sales**

NPC interactions vary based on gang ownership and territory boundaries.
{% endstep %}
{% endstepper %}

By configuring and managing territories effectively, your gangs can dominate the server, offering exciting gameplay opportunities for both competition and cooperation.
