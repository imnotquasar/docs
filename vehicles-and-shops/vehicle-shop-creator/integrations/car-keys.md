# Car Keys

The car keys feature allows you to grant a player ownership of a vehicle's keys dynamically. This can be customized by replacing the default event with your own car key script. The configuration function is simple and can be adapted to different frameworks or scripts as needed.

***

## How to Use

To use this feature, call the Config.Carkeys function, passing the player's source ID and the vehicle's plate number as arguments. Update the event name within the function to match the event used by your car key system.

```lua
Config.Carkeys = function(source, plate)
    print("Sending Keys")
    TriggerClientEvent('vehiclekeys:client:SetOwner', source, plate) -- THIS EVENT IS QBCORE CAR KEYS!, replace the event name to your carkeys event
end
```
