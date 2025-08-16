# interface:notification

{% hint style="info" %}
If icons don't render with `fa-solid`, try using `fas` instead, depending on your FontAwesome version.
{% endhint %}

The `interface:notification` event allows you to send styled notifications to a specific player client-side. This is especially useful for displaying alerts, messages, or system feedback in a consistent and customizable way across your server.

***

## How to Use

To trigger a notification, use the following syntax:

```lua
TriggerClientEvent('interface:notification', source, text, header, duration, icon)
```

* `source`: The player’s source ID.
* `text`: The main content of the notification.
* `header`: The notification title/header.
* `duration`: How long the notification stays on screen (in milliseconds).
* `icon`: FontAwesome icon class (e.g., `"fas fa-bell"`).

### Example:

Here’s a working example using a simple test command:

```lua
RegisterCommand("quasar_notify", function(source, args, rawCommand)
    TriggerClientEvent('interface:notification', source, "This is a test notification.", "Quasar Alert", 5000, "fas fa-file")
end, false)
```

Running `/quasar_notify` in-game will display a sample notification to the player who executes it.

