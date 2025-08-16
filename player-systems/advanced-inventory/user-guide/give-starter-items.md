# Give starter items

Quasar Advanced Inventory integrates a small system of starter items which are an edition for esx, since qbcore has them in an automated way. To add starter items we will have to apply some changes to our esx\_identity, which we must already have one integrated into our server natively.

***

## Modifications to esx\_identify <a href="#modifications-to-esx_identify" id="modifications-to-esx_identify"></a>

To integrate the native inventory events on starter items, we will search within our esx\_identity/client/main.lua for the following callback, which we will use as a guide.

```lua
RegisterNUICallback('register', function(data, cb)
```

Once this callback is detected we will add our own event at the end of the personal registration, leaving something like the example below:

```lua
RegisterNUICallback('register', function(data, cb)
    if not guiEnabled then
        return
    end

    ESX.TriggerServerCallback('esx_identity:registerIdentity', function(callback)
        if not callback then
            return
        end

        ESX.ShowNotification(TranslateCap('thank_you_for_registering'))
        TriggerEvent('inventory:client:GiveStarterItems') -- Starter Items
        setGuiState(false)

        if not ESX.GetConfig().Multichar then
            TriggerEvent('esx_skin:playerRegistered')
        end
    end, data)
end)
```

Once all the steps are ready, we will apply the list of starting items within the inventory in qs-advancedinventory/server/custom/framework/esx.lua, where we will have the complete list as an example by default, remember to add items that you have in your qs- advancedinventory/shared/items.lua.
