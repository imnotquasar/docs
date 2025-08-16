# Trunk and glovebox

The trunk and glovebox system is completely automatic, requiring no modifications or specifications for basic use. But there are certain configurations that we can adapt to our server to make it more comfortable and complete.

***

## **Trunk weight and position**

In config/vehicles.lua you can configure the trunk of your vehicles, you can customize in BackEngineVehicles the vehicles that have the stash in front of them, in addition to configuring the weight and slots allowed in each category of vehicles.

{% hint style="warning" %}
This configuration is very specific and is called Config.VehicleClass.
{% endhint %}

***

## Permissions and jobs configuration <a href="#permissions-and-jobs-configuration" id="permissions-and-jobs-configuration"></a>

We can completely configure the trunk and glovebox system from config/vehicles.lua, where we will find some basic configurations with permissions for police or private use of these systems, edit it to your liking to achieve a single server.

```lua
Config.OpenTrunkAll = false -- Set to true to allow all players to open the trunk of the vehicles / Set false to allow only the owner of the vehicle to open the trunk
Config.OpenTrunkPolice = true -- If the option above its set to false, set if the police can open the trunk or not anyways
Config.OpenTrunkPoliceGrade = 0 -- Grade from the police will be able to open the trunks

Config.OpenGloveboxesAll = false -- Set to true to allow all players to open the glovebox of the vehicles / Set false to allow only the owner of the vehicle to open the glovebox
Config.OpenGloveboxesPolice = true -- If the option above its set to false, set if the police can open the trunk or not anyways
Config.OpenGloveboxesPoliceGrade = 0 -- Grade from the police will be able to open the gloveboxs
```
