# List of commands

Each command has its explanation on the right side, if any command does not work, you can check if you used its syntax correctly, you can later claim it in a ticket.

<table><thead><tr><th width="342">Command</th><th>Description</th></tr></thead><tbody><tr><td>/closeinv</td><td>Closes the player's inventory instantly.</td></tr><tr><td>/inventory</td><td>Opens the player's inventory instantly.</td></tr><tr><td>/hotbar</td><td>Opens the player's hotbar instantly.</td></tr><tr><td>/handsup</td><td>Raise your hands and enable the button to draw from said player if you open the inventory in a close range of the player.</td></tr><tr><td>/searchplayer</td><td>Search the nearest player to steal or check their items.</td></tr><tr><td>/randomitems</td><td>Test command that will give you a random amount of items, used for general testing of the asset.</td></tr><tr><td>/resetinv [id]</td><td>Resets the selected player's inventory.</td></tr><tr><td>/clearinv [id]</td><td>Clears the selected player's inventory and leaves it completely empty.</td></tr><tr><td>/giveitem [id] [item] [count]</td><td>Deliver items to a specific player, selecting his id, item name and quantity, he sends items and also sends weapons.</td></tr><tr><td>/giveweapon [id] [weapon] [ammo]</td><td>Deliver only weapons, you must select the id, weapon and number of ammo.</td></tr><tr><td>/repairweapon [id]</td><td>Repairs the weapons of the selected player through his id, all weapons go to 100% durability.</td></tr><tr><td>/openinventorytarget [id]</td><td>Administrative command to check the inventory of a target player.</td></tr></tbody></table>

***

## How to execute commands using code

This step is very simple, you can use ExecuteCommand('command') anywhere in your code, but for this you should read the ExecuteCommand usage guide at the following link.

{% content-ref url="../../../development-guides/configure-your-scripts/how-to-execute-commands.md" %}
[how-to-execute-commands.md](../../../development-guides/configure-your-scripts/how-to-execute-commands.md)
{% endcontent-ref %}
