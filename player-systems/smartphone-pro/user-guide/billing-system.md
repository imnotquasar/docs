# Billing System

The **Smartphone PRO** includes an internal Billing system designed for optimal performance and independence from third-party assets. This system ensures seamless integration with the phone's exclusive Banking app, avoiding potential issues with external billing systems.

***

## Why Use Internal Billing?

The internal system is optimized for the Smartphone PRO, allowing full control without relying on third-party dependencies. If there’s enough demand, support for external assets may be added in the future.

***

## Sending a Bill

Bills can be sent using the **/sendbill id price reason** command. This functionality is available only to workers specified in the configuration file.

```lua
-- Define which jobs can use the /sendbill command
Config.BillJobs = {
    'police',
    'ambulance'
}
```

***

## Viewing Bills

Recipients can view their received bills directly in the **Banking** app on their phone.

This system provides a streamlined and reliable billing process, tailored specifically for Smartphone PRO users.
