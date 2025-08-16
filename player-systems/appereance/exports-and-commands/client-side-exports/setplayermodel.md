# setPlayerModel

The `setPlayerModel` export allows you to dynamically change a player’s ped model by providing either a string (e.g., `"mp_m_freemode_01"`) or a numeric hash. It also ensures the model is properly loaded, assigned, and, if applicable, initialized with default appearance settings for freemode characters.

***

## How to Use

To change a player's model to freemode male or female, use:

```lua
exports['qs-appearance']:setPlayerModel("mp_m_freemode_01")
```

You can also pass a custom model hash:

```lua
exports['qs-appearance']:setPlayerModel(joaat("a_m_m_bevhills_01"))
```

This export performs the following:

* Converts the model string to a hash if needed
* Requests and waits for the model to load
* Sets the player model with `SetPlayerModel`
* Applies default component variations for freemode models
* Sets default face blend data depending on gender
* Resets any tattoos (`PED_TATTOOS = {}`)

Returns the updated `ped` entity if the model was successfully applied, or the `playerId` if the model was invalid. This function is ideal for character creation, identity change mechanics, or any system requiring model switching with proper initialization.
