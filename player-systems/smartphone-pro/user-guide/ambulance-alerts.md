# Ambulance alerts

This system is not exclusive to ESX, but we provide an example using it since QBcore includes its own integrated system, making this modification unnecessary.

The example uses **esx\_ambulancejob**; if you use another asset, you’ll need to adapt it. Quasar Smartphone includes a convenient messaging system for workers, like in this example where a dispatch is triggered when a player dies, notifying the ambulance with their location.

{% stepper %}
{% step %}
### Locate the File

First, navigate to **esx\_ambulancejob/client/main.lua** and find the function **SendDistressSignal()**.
{% endstep %}

{% step %}
### **Replace the Function**

Once located, replace it with the event provided below. If you use QBcore, this step is unnecessary.
{% endstep %}
{% endstepper %}

***

## Ambulance Dispatch using Messages app <a href="#ambulance-dispatch-using-messages-app" id="ambulance-dispatch-using-messages-app"></a>

This snippet will be for esx\_ambulancejob but you can integrate it wherever you want since it is standalone, in this example we will edit esx\_ambulancejob/client/main.lua and replace the following function.

```lua
function SendDistressSignal()
  local coords = GetEntityCoords(PlayerPedId())
  local street = GetStreetNameAtCoord(coords.x, coords.y, coords.z)
  local streetName = GetStreetNameFromHashKey(street)
  local message = json.encode(coords)
  TriggerServerEvent('phone:sendSOSMessage', 'ambulance', message, 'location')
  Citizen.Wait(100)
  message = ([[
      I need help! I'm at %s. Please fast come here!
  ]]):format(streetName)
  TriggerServerEvent('phone:sendSOSMessage', 'ambulance', message, 'message')
end
```
