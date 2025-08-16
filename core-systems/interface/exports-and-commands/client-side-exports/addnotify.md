# AddNotify

The `AddNotify` export from **qs-interface** allows you to display notifications to the player in the game. These notifications can have various types, and you can customize the message, title, duration, and icon that appears with it.

***

## **How to Use**

The basic syntax for the `AddNotify` export is as follows:

```lua
exports['qs-interface']:AddNotify(message, title, duration, icon)
```

* **message**: The text you want to display in the notification.
* **title**: The type or category of the notification (e.g., 'Inform', 'Error', 'Success').
* **duration**: The length of time the notification will be shown, in milliseconds.
* **icon**: The icon to display with the notification (e.g., a Font Awesome icon). If no icon is provided, a default icon will be used.

### **Example**

```lua
exports['qs-interface']:AddNotify('Message', 'Title', 2500, 'fa-solid fa-file')
```

This displays an informational notification with a file icon. It will last for 2500 milliseconds (2.5 seconds).

***

### **Default Behavior**

If you don't provide an icon, the system will automatically use a default icon. You can customize the notification's look by changing the icon, title, or duration according to the context of your script.
