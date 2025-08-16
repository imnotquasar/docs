# How to execute commands

The ExecuteCommand() function lets you run any FiveM command directly from a script. It’s useful for automating tasks or triggering commands programmatically.

***

## How It Works

Simply call the function with the command you want to execute as a string:

{% stepper %}
{% step %}
### **Run a Chat Command**

This sends "Hello, world!" to the chat.

```lua
ExecuteCommand("say Hello, world!")
```


{% endstep %}

{% step %}
### **Trigger a Custom Command**

This runs a custom /heal command for player ID 1.

```lua
ExecuteCommand("heal 1")
```
{% endstep %}

{% step %}
### **Create a Shortcut Command**

This makes a /healMe command that heals the player who uses it.

```lua
RegisterCommand("healMe", function()
    ExecuteCommand("heal " .. GetPlayerServerId(PlayerId()))
end, false)
```
{% endstep %}
{% endstepper %}

That’s it! ExecuteCommand is a simple and powerful way to run commands directly from your scripts.
