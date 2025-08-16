# Contacts with the jobs

The job contact system in Smartphone PRO is simpler and more advanced compared to previous versions. Instead of using commands, workers now have specific phone numbers and a new **Duty** section in the Settings app to manage their availability.

{% stepper %}
{% step %}
### **Contact workers via call**

In the Contact app, you can call a job, and a random worker on duty will answer.
{% endstep %}

{% step %}
### **Contact via Message app**

You can send a message to a specific job by finding its contact in the Contacts app.
{% endstep %}

{% step %}
### **Contact via Marketplace app**

You can also communicate with workers in the best way by using the Marketplace app, which sends them a chat.
{% endstep %}
{% endstepper %}

***

## Entering and Exiting Duty

Workers are unavailable for contact by default. To enable communication through apps like Contacts, Messages, or State, they must activate the **Duty** option in the Settings app. Once enabled, they can receive calls or messages from players.

{% stepper %}
{% step %}
### Enter service in any app

For any app except Marketplace, you need to go to Settings app and enter service from there.
{% endstep %}

{% step %}
### Entering into service in the Marketplace app

In the Marketplace app, when you open the app you get a button to log into your specific store.
{% endstep %}
{% endstepper %}

***

## **W**orker Configuration

Each job is assigned a unique phone number, and calls to this number will randomly connect to a worker on duty. Workers must enable their duty status in the Settings app to be reachable.

```lua
Config.Jobs = {
    'police',
    'ambulance',
    'mechanic',
    'taxi'
}

Config.jobNumbers = {
    ['police'] = '911',
    ['ambulance'] = '912',
    ['mechanic'] = '913',
}

Config.JobLabels = {
    ['police'] = 'Police',
    ['ambulance'] = 'Ambulance',
    ['mechanic'] = 'Mechanic',
    ['taxi'] = 'Taxi',
}
```

This system streamlines communication by integrating job roles directly into the smartphone's functionality.
