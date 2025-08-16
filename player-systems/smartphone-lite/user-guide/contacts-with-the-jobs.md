# Contacts with the jobs

The Quasar Smartphone includes a mandatory duty system for jobs and workers. Workers need to be on duty to receive and use their job-related features within the phone. Without this, they cannot access their job powers. We have the following types of contact per job:

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
### **Contact via Business app**

You can also communicate with workers in the best way by using the Business app, which sends them a dispatch.
{% endstep %}
{% endstepper %}

***

## **How the Duty System works**

The duty system prevents excessive spam by ensuring that only workers on duty can receive job-related messages and calls. To go on duty, workers need to activate the function using a specific command. For example, police officers can use the **/911** command to go on duty and start receiving calls.

***

## **Worker commands configuration**

Commands for each job are set up in **config.lua**, where you assign a number for each job that will appear when they are called.

```lua
Config.jobCommands = { 
    ['police'] = '112',
    ['ambulance'] = '113',
    ['mechanic'] = '114',
}
```

***

## **Worker Calls and Messages**

Workers can receive calls and messages but cannot respond directly via chat. Instead, they can double-click the received message to view the sender's phone number and call or message them back.

The **config.lua** file allows you to set up job-specific contacts that will automatically appear in the phone’s call application. These contacts cannot be deleted unless modified in the configuration file.

```lua
Config.Jobs = {
    { job = 'police',    name = 'Policia',  img = './img/apps/police.png' },
    { job = 'ambulance', name = 'Ems',      img = './img/apps/ambulance.png' },
    { job = 'mechanic',  name = 'Mechanic', img = './img/apps/mechanic.png' },
}
```

***

## Messaging system

Players can send text messages to job contacts added in **config.lua**, but workers cannot reply directly. To respond, workers double-click the received message, which shows the sender’s phone number for direct communication.
