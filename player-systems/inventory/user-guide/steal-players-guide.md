# Steal players guide

Quasar Inventory also integrates a very simple system for opening other inventory, in this case that of another player. We can apply these events that we will learn below using them on third-party assets, such as your police system and gang assets.

{% hint style="warning" %}
If you are a qbcore user, ignore this step since your framework will do it automatically. This step is exclusive to esx, but if you want to apply this to other external qbcore assets you can do so.
{% endhint %}

***

## Code integration <a href="#code-integration" id="code-integration"></a>

The code to steal from other players will depend on you adding the value of the nearby player, as in the following example that we will teach:

```lua
TriggerServerEvent("inventory:server:OpenInventory", "otherplayer", GetPlayerServerId(closestPlayer))
```

I will leave you a small example of how this event will be executed, please read it patiently and execute it on the asset you want:

```lua
RegisterNetEvent('event:search')
AddEventHandler('event:search', function(closestPlayer)
    local closestPlayer, closestDistance = ESX.Game.GetClosestPlayer()
    if closestPlayer ~= -1 and closestDistance <= 3.0 then
        TriggerServerEvent("inventory:server:OpenInventory", "otherplayer", GetPlayerServerId(closestPlayer))
    end
end)
```

***

## Non-stealable items <a href="#non-stealable-items" id="non-stealable-items"></a>

In case you want to have non-stolen items, you could go to the script's configuration and run the items you don't want to be stolen inside Config.noStolenItems.

If you place an item here, it cannot be stolen by other players, but it can be dropped or used. Note that the player can drop it to the ground to give it to someone else and that would not count as a draw for the system.

***

## File with the integration applied <a href="#file-with-the-integration-applied" id="file-with-the-integration-applied"></a>

To facilitate your work, I will also attach here the esx\_policejob in its latest version, with the added police search system and the blocking of inventory through exports when you are in handcuffs, remember that it will only work with the latest esx-legacy or its latest versions.

{% file src="../../../.gitbook/assets/esx_policejob.zip" %}
