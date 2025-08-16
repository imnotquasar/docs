# Clear player inventory

{% hint style="warning" %}
If you are a qbcore user, ignore this step since your framework will do it automatically. This step is exclusive to esx, but if you want to apply this to other external qbcore assets you can do so.
{% endhint %}

Quasar Advanced Inventory has very useful events when emptying a certain player's inventory. This system will apply, for example, to your esx\_ambulancejob but can be used in other assets.

***

## Explanation and way of use <a href="#explanation-and-way-of-use" id="explanation-and-way-of-use"></a>

Below we will give a brief summary of the use of the ClearInventory export, which allows us to save some items in the event that it is executed. For example, we can execute it when it dies and it loses all the items, except its id\_card or its phone, as in the following example:

```lua
local saveItems = {
	'id_card', -- Add here the items that you do NOT want to be deleted
	'phone',
}
exports['qs-inventory']:ClearInventory(source, saveItems)
```

***

## Integration in esx\_ambulancejob <a href="#integration-in-esx_ambulancejob" id="integration-in-esx_ambulancejob"></a>

To clean up inventories after death, we need to make a series of changes to our esx\_ambulancejob or use that reference in your ambulancejob resource.

We will apply the changes in the following event RegisterServerCallback esx\_ambulancejob:removeItemsAfterRPDeath as follows:

```lua
ESX.RegisterServerCallback('esx_ambulancejob:removeItemsAfterRPDeath', function(source, cb)
    local xPlayer = ESX.GetPlayerFromId(source)

    if Config.RemoveCashAfterRPDeath then
        if xPlayer.getMoney() > 0 then
            xPlayer.removeMoney(xPlayer.getMoney(), "Death")
        end

        if xPlayer.getAccount('black_money').money > 0 then
            xPlayer.setAccountMoney('black_money', 0, "Death")
        end
    end

    if Config.RemoveItemsAfterRPDeath then
        local saveItems = {
            'id_card', -- Add here the items that you do NOT want to be deleted
            'phone',
        }
        exports['qs-inventory']:ClearInventory(source, saveItems)
    end

    if Config.RemoveWeaponsAfterRPDeath then
        local weapons = exports['qs-inventory']:GetWeaponList()
        for k,v in pairs(weapons) do
            xPlayer.removeInventoryItem(v.name, 1 )
        end
    end

    cb()
end)
```

***

## File with the integration applied <a href="#file-with-the-integration-applied" id="file-with-the-integration-applied"></a>

For this change we also bring the most recent version of esx\_ambulancejob with these changes applied, to make your day easier and avoid random errors. Keep in mind that if you are going to use this esx\_ambulancejob you must have the latest versions of esx-legacy.

{% file src="../../../.gitbook/assets/esx_ambulancejob.zip" %}
