# E-mail system

Quasar Smartphone PRO has an even more advanced Mail system than its previous version. In this application we must register and we will have a real account, where we can send Mails, media files and more epic functions that we could not do before.

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

The Mails system has integration of both the client and the server. Expand the tab according to your needs.

<details>

<summary>Client side integration</summary>

```lua
-- Example of how to use the sendNewMail event.
RegisterCommand('mailTest', function(source)
    TriggerServerEvent('phone:sendNewMail', {
        sender = 'Movistar Plus',
        subject = 'Family telephone balance promotion',
        message = 'Enjoy the family balance at only $8.50 per month, what are you waiting for?'
    })
end, false)
```

</details>

<details>

<summary>Server side integration</summary>

```lua
-- Example of how to use the sendNewMail export.
RegisterCommand('mailTest', function(source)
    exports['qs-smartphone-pro']:sendNewMail(source, {
        sender = 'Quasar',
        subject = 'Es tu culpa',
        message = 'Es tu culpa que no haya un ejemplo de como usar esto...'
    })
end, false)
```

</details>

***

## Quest integration in Mail

The Mails system includes a completely optional option to integrate a button that responds with a specific event, which will operate through the next button value. Expand the tab according to your needs.

<details>

<summary>Client side integration</summary>

```lua
-- Example of how to use the sendNewMail event and Quest button!
RegisterCommand('mailTest', function(source)
    TriggerServerEvent('phone:sendNewMail', {
        sender = 'Movistar Plus',
        subject = 'Family telephone balance promotion',
        message = 'Enjoy the family balance at only $8.50 per month, what are you waiting for?'
        -- Execution example for the button
        button = {
            enabled = true,
            buttonEvent = 'phone:client:movistarEvent',
        }
    })
end, false)
```

</details>

<details>

<summary>Server side integration</summary>

```lua
-- Example of how to use the sendNewMail event and Quest button!
RegisterCommand('mailTestSv', function(source)
    exports['qs-smartphone-pro']:sendNewMail(source, {
        sender = 'Quasar',
        subject = 'Es tu culpa',
        message = 'Es tu culpa que no haya un ejemplo de como usar esto...',
        -- Execution example for the button
        button = {
            enabled = true,
            buttonEvent = 'phone:client:movistarEvent',
        }
    })
end, false)
```

</details>

***

## Administrative Mail Command (ads) <a href="#administrative-mail-command-a-ds" id="administrative-mail-command-a-ds"></a>

This command can be sent using quotes to be able to send long texts.

The Mail system does not end here, we also have a brief command to give community announcements, this command will send an Mail to the entire server giving it a general message.

The way the command is used can be done with quotes to send long texts. The command is very simple, we can use it in the following way /sendmail subject message.

```lua
/sendmail "Important" "Players please disconnect from the server for brief maintenance."
```
