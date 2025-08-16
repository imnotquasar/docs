# How to change notifications

## **Change Notifications**

Configuring notifications in Quasar Store assets is simple and straightforward. Notifications are used to display information, successes, and errors in-game. All Quasar Store assets share the same notification system, ensuring consistency across different scripts.

{% stepper %}
{% step %}
### Delete notifications

Delete the current notification logic inside the SendTextMessage function.
{% endstep %}

{% step %}
### Add the new ones

Manually add your desired notification export or method.
{% endstep %}

{% step %}
### Always test with backup

Test thoroughly to ensure compatibility with the rest of the asset.
{% endstep %}
{% endstepper %}

***

## **Editing Notifications**

All configurable notifications are located in client/custom/framework/\*.lua in this file, you’ll find the SendTextMessage function, which controls how notifications are displayed.

If you want to customize the notification system or integrate a new one, you can do so by editing the SendTextMessage function. Below is an example of how to modify it for a new system:

```lua
function SendTextMessage(msg, type)
    if type == 'inform' then
        exports['qs-notify']:Alert(msg, 1500, 'info')
    end
    if type == 'error' then
        exports['qs-notify']:Alert(msg, 1500, 'error')
    end
    if type == 'success' then
        exports['qs-notify']:Alert(msg, 1500, 'success')
    end
end
```
