# Steal players guide

**Quasar Advanced Inventory** includes a simple system that allows you to open another player’s inventory — useful for actions like searching a suspect, checking a gang member, or inspecting a teammate. This feature can be used in **third-party assets**, such as police systems, gang scripts, or custom commands.

***

## Code integration <a href="#code-integration" id="code-integration"></a>

Here is an example of how to trigger another player’s inventory using the event manually.

You must provide the server ID of the nearby player you want to search, along with an optional config indicating **which inventory types** can be accessed:

```lua
RegisterCommand('search', function(source, args, raw)
    -- Replace '1' with the player ID you want to search (e.g., from your logic)
    TriggerServerEvent('inventory:server:OpenInventory', 'otherplayer', 1, {
        type = 'hotbar' -- Options: 'hotbar', 'wallet', or 'all'
    })
end)
```

* **'hotbar'**: only the hotbar items will be visible.
* **'wallet'**: opens wallet-type items (e.g., ID, cards, cash).
* **'all'**: full access to the target’s inventory.

You can implement this inside any asset or create your own logic to determine the target player’s ID dynamically.

***

## Non-stealable items <a href="#non-stealable-items" id="non-stealable-items"></a>

If you want certain items to **never be stealable**, go to your `config.lua` and add them under:

```lua
Config.noStolenItems = {
    'police_badge',
    'passport',
    'black_card'
}
```

These items **cannot be taken from another player's inventory**, but they can still be **used or dropped manually**. That means a player can still drop the item on the ground and give it away, which will **not be blocked** by the system.
