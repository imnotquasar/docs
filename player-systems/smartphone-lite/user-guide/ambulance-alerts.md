# Ambulance alerts

This system is not exclusive to ESX, but we provide an example using it since QBcore includes its own integrated system, making this modification unnecessary. However, you can adapt it creatively for either ESX or QBcore.

The example uses **esx\_ambulancejob**; if you use another asset, you’ll need to adapt it. Quasar Smartphone includes a convenient messaging system for workers, like in this example where a dispatch is triggered when a player dies, notifying the ambulance with their location.

{% stepper %}
{% step %}
### Locate the File

First, navigate to **esx\_ambulancejob/client/main.lua** and find the function **SendDistressSignal()**.
{% endstep %}

{% step %}
### **Replace the Function**

Once located, replace it with the event provided below. You can use either the Business version or the Messages version, but do not use both. If you use QBcore, this step is unnecessary.
{% endstep %}
{% endstepper %}

***

## Ambulance Dispatch through Business app <a href="#ambulance-dispatch-through-business-app" id="ambulance-dispatch-through-business-app"></a>

We can use the dispatch system through the business app using the following code. Remember that we will give all the examples using esx\_ambulancejob, you can use another asset and adapt it your way, customizing it and leaving it ready for your server.

```lua
function SendDistressSignal()
  local playerPed = PlayerPedId()
  local coords = GetEntityCoords(playerPed)
  local message = "Injured person" -- The message that will be received.
  local alert = {
      message = message,
      -- img = "img url", -- You can add image here (OPTIONAL).
      location = coords,
  }

  TriggerServerEvent('qs-smartphone:server:sendJobAlert', alert, "ambulance") -- "Your ambulance job"
  TriggerServerEvent('qs-smartphone:server:AddNotifies', {
      head = "Google My Business", -- Message name.
      msg = message,
      app = 'business'
  })
end 
```

***

## Ambulance Dispatch using Messages app <a href="#ambulance-dispatch-using-messages-app" id="ambulance-dispatch-using-messages-app"></a>

The option via Messages is not a bad option but we will prefer to use the superior Business option, in any case we will leave the snippet and its use below.

```lua
function SendDistressSignal()
    local playerPed = PlayerPedId()
    local coords = GetEntityCoords(playerPed)

    TriggerEvent('qs-smartphone:sendJobMessage', {
        phone = 'ambulance', 
        type = 'message', 
        message = 'Injured person'
    })
    Wait(300)
    TriggerEvent('qs-smartphone:sendJobMessage', {
        phone = 'ambulance', 
        type = 'location'
    })
end
```
