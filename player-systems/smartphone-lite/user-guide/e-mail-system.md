# E-mail system

Using the Quest system for Mail requires general programming knowledge or assistance from a programmer to set it up properly. The email system includes the following features:

{% stepper %}
{% step %}
### Emails for external systems

This feature allows you to add email notifications to your other scripts, such as when purchasing an item or withdrawing money.
{% endstep %}

{% step %}
### **Emails for missions**

This option lets you send an email with an activation button that can trigger events.
{% endstep %}

{% step %}
### **Administrative email**

You can use a command to send emails to all online players, such as for server shutdown notices or important alerts.
{% endstep %}
{% endstepper %}

***

## **Mail integration into other assets**

The Quasar Smartphone features an advanced Mail system that supports integration with other assets, including optional Quest functionality. For simplicity, all Mail integrations are executed client-side. Server-side execution is not supported and may cause errors. To send Mail from the server, pass the required data to the client and use the following event:

```lua
TriggerServerEvent('qs-smartphone:server:sendNewMail', {
    sender = 'Robby Williams',
    subject = 'Hey bro, how are you?',
    message = 'Soon we will launch more versions and this will be more complete, what are you waiting for to get this great phone brother?',
    button = {}
})
```

***

## Quest integration in Mail

The Quest system allows for additional functionality when interacting with Mail. Buttons can be included in the Mail to accept or reject tasks. The following example shows how to enable a button and assign it an event:

```lua
TriggerServerEvent('qs-smartphone:server:sendNewMail', {
    sender = 'Robby Williams',
    subject = 'Hey bro, how are you?',
    message = 'Soon we will launch more versions and this will be more complete, what are you waiting for to get this great phone brother?',
    -- Execution example for the button
    button = {
        enabled = true,
        buttonEvent = 'gangs:client:setLocation',
    }
})
```

***

## **Administrative mail command (ads)**

The Mail system includes a simple command for sending announcements to the entire server. This command supports quotes for long texts and can be used as follows:

```lua
/sendmail "Important" "Players please disconnect from the server for brief maintenance."
```

This allows administrators to broadcast messages efficiently via the Mail system.
