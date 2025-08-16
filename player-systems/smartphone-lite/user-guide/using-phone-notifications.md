# Using phone notifications

Quasar Smartphone features a single notification system, unlike its PRO version, which includes two types. This notification system uses a dynamic island to provide useful information, which can be sent from external assets. Keep in mind that this system is limited and cannot display long texts.

***

## **Pop-up notifications integration**

To use pop-up notifications, ensure the image you reference exists in **smartphone/html/img/** and provide its correct path. Notifications can be triggered from both client-side and server-side, allowing customization of the title, description, image, and display time.

<details>

<summary>Client-side integration</summary>

```lua
TriggerEvent('qs-smartphone:client:notify', {
    title = 'Title',
    text = 'Description',
    icon = './img/apps/whatsapp.png',
    timeout = 1500
})
```

</details>

<details>

<summary>Server-side integration</summary>

```lua
TriggerClientEvent('qs-smartphone:client:notify', source, {
    title = 'Title',
    text = 'Description',
    icon = './img/apps/whatsapp.png',
    timeout = 1500
})
```

</details>

***

## L**ockscreen notification integration** <a href="#lockscreen-notification-integration" id="lockscreen-notification-integration"></a>

This type of notification works exclusively on the client-side and should not be used on the server-side. It provides a notification on the lockscreen, complementing the pop-up notification to create a more complete event.

```lua
TriggerServerEvent('qs-smartphone:server:AddNotifies', {
    head = 'Title',
    msg = 'Description',
    app = './img/apps/whatsapp.png',
})
```
