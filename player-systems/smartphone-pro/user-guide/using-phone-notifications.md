# Using phone notifications

This system includes two types of notifications, simple notification and notification from the Dynamic Island, with this you can create a multitude of unique systems.

***

## **Pop-up notifications integration**

The notification system in this version of Smartphone is more complex and configurable, since now we will have the new disableBadge value, this will serve to enable or disable the red notification on the application icon. In the case of the server side, we will have to detail the phone number using the GetPhoneNumberFromIdentifier export, unfold the sections and we will teach you the basic use of this system.

<details>

<summary>Client-side integration</summary>

```lua
-- Its same as the old one
RegisterCommand('notifiOld', function(source)
    exports['qs-smartphone-pro']:SendTempNotificationOld({
        title = 'Test',
        text = 'This is a test notification.',
        app = 'settings',
        timeout = 5000,
        disableBadge = true, -- Disables the badge on the app icon.
    })
end, false)
```

</details>

<details>

<summary>Server-side integration</summary>

This integration is more advanced and we will use the phone number to send it.

```lua
-- This export sends a basic notification to a phone number.
RegisterCommand('sendNewNotification', function(source, args)
    local phone = exports['qs-smartphone-pro']:GetPhoneNumberFromIdentifier(GetPlayerIdentifier(source), false)
    local disableTempNotification = false -- Disables the temporary notification. (Pop up notification)
    exports['qs-smartphone-pro']:sendNotificationOld(phone, {
        app = 'twitter',
        msg = 'Hello world!',
        head = 'Quasar'
    }, disableTempNotification)
end, false)
```

</details>

***

## Pop-up notification on Dynamic Island <a href="#pop-up-notification-on-dynamic-island" id="pop-up-notification-on-dynamic-island"></a>

{% hint style="success" %}
This system will work in the same way as the basic notification but we will leave a mini user guide so you know how to export it correctly.
{% endhint %}

In this case it will be as in the previous one, you can use the example to understand the function.

<details>

<summary>Client-side integration</summary>

```lua
-- Example of how to use the notification function.
RegisterCommand('notifi', function(source)
    exports['qs-smartphone-pro']:SendTempNotification({
        title = 'Test',
        text = 'This is a test notification.',
        app = 'settings',
        timeout = 5000,
        disableBadge = true, -- Disables the badge on the app icon.
    })
end, false)
```

</details>

<details>

<summary>Server-side integration</summary>

This integration is more advanced and we will use the phone number to send it.

```lua
-- This export sends a new notification to a phone number.
RegisterCommand('sendNewNotification', function(source, args)
    local phone = exports['qs-smartphone-pro']:GetPhoneNumberFromIdentifier(GetPlayerIdentifier(source), false)
    local disableTempNotification = false -- Disables the temporary notification. (Pop up notification)
    exports['qs-smartphone-pro']:sendNotification(phone, {
        app = 'twitter',
        msg = 'Hello world!',
        head = 'Quasar'
    }, disableTempNotification)
end, false)
```

</details>
