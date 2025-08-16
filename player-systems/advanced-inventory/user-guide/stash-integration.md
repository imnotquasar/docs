# Stash integration

The stashes in Quasar Advanced Inventory are really useful, smart and simple to integrate into other scripts. This system is completely standalone for both esx and qbcore, follow the following steps to integrate it into your other assets.

***

## Basic integrations <a href="#basic-integrations" id="basic-integrations"></a>

To integrate a stash, either through export or event, we must have an identification to give to said store, in the case of the examples mentioned it will be lockerID, do not forget to give it the specific value of this identification or use your own identifier for a private stash.

{% hint style="success" %}
If you want to make a completely personal stash, you can use your player's id as the stash id using client-side `ESX.GetPlayerData().identifier`.
{% endhint %}

To integrate stashes we have two methods, the basic event without the use of export which is the simplest to apply or the more complex export which can be used both on the client and on the server.

Don't forget to give the values corresponding to the lockerID example, in that case we must modify it for the identification that we will decide to give to the stash or simply delete it and give it a name.

```lua
local other = {}
other.maxweight = 10000 -- Custom weight statsh
other.slots = 50 -- Custom slots spaces
TriggerServerEvent("inventory:server:OpenInventory", "stash", "Stash_"..lockerID, other)
TriggerEvent("inventory:client:SetCurrentStash", "Stash_"..lockerID)
```

***

## Advanced exports <a href="#advanced-exports" id="advanced-exports"></a>

In the case of wanting to integrate it on the client or server side through a faster export, we can execute either of these two events, depending on your situation.

{% tabs %}
{% tab title="Client" %}
```
exports['qs-inventory']:RegisterStash("Stash_"..lockerID, 50, 10000) 
```
{% endtab %}

{% tab title="Server" %}
```
exports['qs-inventory']:RegisterStash(source, "Stash_"..lockerID, 50, 10000) 
```
{% endtab %}
{% endtabs %}

***

## Simple use within qs-shops <a href="#simple-use-within-qs-shops" id="simple-use-within-qs-shops"></a>

There is still another simpler option, you can run customizable stashes from your qs-shops, where you can add dependencies on licenses or items, such as jobs and degrees. This system is much simpler and you can find it in qs-shops/config/config.lua.

{% hint style="info" %}
You can use the esx licenses using Config.ESXLicense, since by default the license will be a required item, if you enable this option it will use the esx\_licenses licenses.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
