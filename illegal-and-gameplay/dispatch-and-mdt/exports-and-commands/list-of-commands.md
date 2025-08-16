# List of commands

Each command has its explanation on the right side, if any command does not work, you can check if you used its syntax correctly, you can later claim it in a ticket.

***

## Default configuration

Default (unchangeable) commands can be configured in the config.lua file.

```lua
Config.Commands = {
     ["OpenLargue"] = "toggleopendispatch", -- Prefer not to change this
     ["OpenSmall"] = "togglesmalldispatch", -- Prefer not to change this
     ["MoveSmall"] = "movesmalldispatch", -- Command to move the small dispatch
     ["DisableSpeedRadar"] = 'disablespeedradar', -- Command to disable speed radar
     ["OpenMdt"] = 'openmdt' -- Command to open the police MDT
}
```

In the commands.lua file located in the client/custom/misc/ folder, you will find a list of commands that you can edit according to your needs.

<table><thead><tr><th width="342">Command</th><th>Description</th></tr></thead><tbody><tr><td>/police [message]</td><td>Sends a dispatch call to the police (similar to /enterno)</td></tr><tr><td>/ambulance [message]</td><td>Same thing but for medics.</td></tr><tr><td>/mechanic [message]</td><td>Same thing but for mechanics.</td></tr><tr><td>/panic [message]</td><td>Panic call sent by a police officer to all other police officers.</td></tr></tbody></table>

***

## How to execute commands using code

This step is very simple, you can use ExecuteCommand('command') anywhere in your code, but for this you should read the ExecuteCommand usage guide at the following link.

{% content-ref url="../../../development-guides/configure-your-scripts/how-to-execute-commands.md" %}
[how-to-execute-commands.md](../../../development-guides/configure-your-scripts/how-to-execute-commands.md)
{% endcontent-ref %}
