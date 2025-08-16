# openInteractMenu

The `openInteractMenu` export allows you to create an interaction menu for NPCs programmatically. This is useful for adding roleplay elements, custom dialogues, and other gameplay interactions with NPCs.

***

## **How to Use**

To open an interaction menu for an NPC, use the following code:

```lua
-- Open an interaction menu for an NPC
exports['qs-interact']:openInteractMenu({
    coords = coords,
    title = 'Interact with NPC',
    name = 'NPC',
    options = {
        {
            label = 'Hello',
            onPress = function()
                -- 'npc' or 'player' for the type of message
                interact:addMessage('Hello, how are you?', 'npc')
            end
        },
        {
            label = 'Goodbye',
            onPress = function()
                -- 'npc' or 'player' for the type of message
                interact:addMessage('Goodbye!', 'npc')
                Wait(1500)
                interact:closeMenu()
            end
        }
    }
})
```

***

## Example:

```lua
RegisterCommand('interact', function()
    local ped = PlayerPedId()
    local pos = GetEntityCoords(ped)
    -- -180 for the camera to face the player
    local heading = GetEntityHeading(ped) - 180
    local coords = vec4(pos.x, pos.y, pos.z, heading)

    exports['qs-interact']:openInteractMenu({
        coords = coords,
        title = 'Interact with NPC',
        name = 'NPC',
        options = {
            {
                label = 'Hello',
                onPress = function()
                    -- 'npc' or 'player' for the type of message
                    interact:addMessage('Hello, how are you?', 'npc')
                end
            },
            {
                label = 'Goodbye',
                onPress = function()
                    -- 'npc' or 'player' for the type of message
                    interact:addMessage('Goodbye!', 'npc')
                    Wait(1500)
                    interact:closeMenu()
                end
            }
        }
    })
end)
```

This export takes the following parameters:

* **coords**: The `vec4` position where the interaction will take place.
* **title**: The title displayed on the interaction menu.
* **name**: The name of the NPC.
* **options**: A table of interaction choices available to the player.

This function allows seamless NPC interactions, enhancing gameplay customization and immersion.
