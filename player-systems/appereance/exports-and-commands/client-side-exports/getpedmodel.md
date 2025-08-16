# getPedModel

The `getPedModel` export allows you to retrieve the internal model identifier of a given ped entity. This is useful when you need to identify the ped’s base model (such as male, female, or any custom ped) in order to apply logic, customization, or compatibility checks.

***

## How to Use

To get the model name of any ped entity, use the following code:

```lua
local ped = PlayerPedId()
local model = exports['qs-appearance']:getPedModel(ped)

print("Ped model:", model)
```

This export returns a string representing the model name associated with the given ped, such as `"mp_m_freemode_01"`. The function automatically initializes internal mappings if they haven't been computed yet, ensuring consistent results across uses.
