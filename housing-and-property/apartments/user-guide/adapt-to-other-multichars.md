# Adapt to other Multichars

To integrate **Quasar Apartments** into another multicharacter system, you need to ensure that the apartment system is started **before** the multicharacter script in your `server.cfg`. This guarantees that apartments are properly registered before character selection occurs.

***

## Apartment Spawn Event

Once your multicharacter system is loaded, you can teleport a player directly to a specific apartment using the following event:

```lua
TriggerServerEvent('apartments:server:CreateApartment', 'apartment1', 'South Rockford Drive', true)
```

By executing this event, the player will be assigned and teleported to the specified apartment (`apartment1` at `South Rockford Drive`). This allows seamless integration with character selection, ensuring that players spawn in their designated apartments when joining the server.
