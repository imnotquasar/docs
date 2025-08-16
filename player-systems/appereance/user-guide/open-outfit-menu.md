# Open Outfit Menu

{% hint style="warning" %}
If you need assistance, please reach out to a developer, as the setup for "Basic Item Declaration" is designed to be straightforward. However, if any difficulties arise, it’s best to consult a trusted developer to ensure a smooth integration.
{% endhint %}

The **Outfit Menu** system in `qs-appearance` can be triggered externally from other scripts or systems using predefined events. This allows you to open the clothing menu for outfit selection or management from any custom interaction such as NPCs, commands, stores, jobs, and more.

***

## Supported Events <a href="#basic-item-declaration" id="basic-item-declaration"></a>

You can trigger the outfit menu with the following events:

{% stepper %}
{% step %}
## Native Event (qs-appearance)

This is the standard event provided by `qs-appearance`. It opens the outfit menu for the current player, allowing them to **view, equip, rename or delete** their saved outfits.

```lua
TriggerEvent('clothing:openOutfitMenu')
```
{% endstep %}

{% step %}
## Compatibility: Illenium Appearance

If you're using systems that were originally built for `illenium-appearance`, you don't need to change anything. `qs-appearance` is fully compatible with:

```lua
TriggerEvent('illenium-appearance:client:openOutfitMenu')
```

This means you can use `qs-appearance` as a drop-in replacement without breaking compatibility in your existing server scripts or third-party resources.
{% endstep %}
{% endstepper %}

***

## Example Usage <a href="#decay-wear-and-tear" id="decay-wear-and-tear"></a>

{% stepper %}
{% step %}
## From an NPC interaction:

```lua
exports['qb-target']:AddBoxZone("outfit_npc", vector3(123.4, 456.7, 78.9), 1.5, 1.5, {
    name = "outfit_npc",
    heading = 90.0,
}, {
    options = {
        {
            label = "Open Outfit Menu",
            icon = "fas fa-tshirt",
            action = function()
                TriggerEvent('clothing:openOutfitMenu')
            end
        }
    },
    distance = 2.0
})

```
{% endstep %}

{% step %}
## From a command:

```lua
RegisterCommand("outfits", function()
    TriggerEvent('clothing:openOutfitMenu')
end)
```
{% endstep %}

{% step %}
## From legacy Illenium integrations:

```lua
TriggerEvent('illenium-appearance:client:openOutfitMenu') -- Works identically with qs-appearance
```
{% endstep %}
{% endstepper %}

***

## Notes

* You do **not** need to pass any parameters; the system will detect the player and context automatically.
* Ensure the player is using a **freemode ped model**, or the menu may be limited.
* This menu includes options to **equip**, **rename**, **delete**, and **view** saved outfits.
