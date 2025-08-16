# Logout System

Quasar Multicharacter includes a seamless **logout system** that allows players to return to the character selection screen without restarting the game. This feature enhances user experience, making Quasar Multicharacter one of the most advanced systems available.

To provide flexibility, this functionality can be disabled or modified by adjusting the Config.BackCharCommand setting in the configuration file.

***

## Integration and Usage

The logout system is simple to integrate and leverages the server-side event multicharacter:backToCharacterSelect. For example, a command like the following can trigger the logout event:

```lua
RegisterCommand('qs:logout', function()
    TriggerServerEvent('multicharacter:backToCharacterSelect')
end, false)
```

By default, this command is already configured in **config.lua** for easy implementation. Adjust it as needed to suit your server's requirements.
