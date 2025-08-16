# Petrol Can system

This step is not completely mandatory, but we will teach you how to apply metadata to the weapon\_petrolcan of assets like LegacyFuel or similar so that they break when you finish filling a certain amount of gasoline in a car.

{% hint style="success" %}
Quasar Store has an exclusive fuel system called Fuel Stations, which you will find at an exclusive price in our official store. This asset integrates the entire system automatically and has completely impressive functions.
{% endhint %}

***

## Integration as an example in LegacyFuel <a href="#integration-as-an-example-in-legacyfuel" id="integration-as-an-example-in-legacyfuel"></a>

{% hint style="warning" %}
It depends on the version of LegacyFuel you will have to add an event so that it gives you the item since some versions do not bring that natively, use our resource and it will be more functional and faster for you.
{% endhint %}

The integration is very simple, we will search on the client side for the following code:

```lua
SetPedAmmo(ped, 883325847, math.floor(GetAmmoInPedWeapon(ped, 883325847) - fuelToAdd * 100))
```

This event will point us to the point where we should add our custom event, which will be just below it, make sure not to replace the previous event, simply use it as a guide to place the advanced inventory event.

```lua
TriggerEvent('inventory:client:LegacyFuel', math.floor(GetAmmoInPedWeapon(ped, 883325847) - fuelToAdd * 100))
```

***

## File with the integration applied <a href="#file-with-the-integration-applied" id="file-with-the-integration-applied"></a>

Once we know the modification that was applied, you can simply make use of the file already modified by our support, which will simply download and use without problems. This file is LegacyFuel for esx, if you want to use it in qbcore, you will have to apply some changes to it for qbcore or modify the version of your framework yourself.

{% file src="../../../.gitbook/assets/LegacyFuel.zip" %}
