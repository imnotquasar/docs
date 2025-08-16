# Char Creator Integration

This section explains how the script is fully compatible with multicharacter systems that use `illenium-appearance`, integrating automatically without requiring additional setup. It also shows how to easily retrieve a player’s appearance from a ped.

***

This script has been designed to fully override and manage all default events from `illenium-appearance`, ensuring native compatibility without requiring any additional configuration. Thanks to this integration approach, any multicharacter system that relies on `illenium-appearance`—such as `qs-multicharacter`, `qb-multicharacter`, or any other similar implementation—will automatically work with this script as if it were using the original. You don't need to make manual changes, patch event handlers, or rewrite compatibility logic; everything is handled transparently by the system.

This means that as long as your multichar system is set to use `illenium-appearance` for character styling and appearance control, our script will intercept those calls and respond appropriately, preserving full functionality while using our own internal logic.

Moreover, extracting a player's appearance for custom implementations is extremely straightforward. You can get the current visual data of any ped using a simple helper like this:

```lua
function Appearance:GetAppearanceFromPed(ped)
    if not DoesEntityExist(ped) then
        Error('Ped does not exist', ped)
        return nil
    end
    local appearance = exports['qs-appearance']:getPedAppearance(ped)
    if not appearance then
        Error('Failed to get appearance from ped', ped)
        return nil
    end
    Debug('Got appearance from ped', appearance)
    return appearance
end
```

This function safely checks the ped entity, fetches the current appearance using the `qs-appearance` export, and returns the structured data. This can be used in custom spawns, player saving systems, NPC customization, or anything else where you need to capture or replicate a character's current look.
