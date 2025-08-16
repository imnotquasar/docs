# Security system

The **Smartphone PRO** includes a Unique Phones system that adds significant depth to phone security and data protection. Without this feature, the system is purely aesthetic, but enabling it makes this document essential for safeguarding player data.

***

## **P**assword Security

To secure your phone and its applications, it’s crucial to set a password. Without one, your apps and social networks are vulnerable.

In the **Settings** app, you can add a password to lock your phone. This password ensures no one can access your data unless you share it with them.

***

## FaceID Security

FaceID allows you to unlock your phone using facial recognition. However, it requires a backup password for situations where your face is covered, such as wearing a mask.

This feature, also found in the **Settings** app, ensures your phone remains secure even if it’s stolen, as FaceID will not function for anyone else.

***

## Forgotten Passwords

If you forget your password, you can visit the **Technician**, who is marked on the map by default. The technician can reset your password for a fee.

To configure the technician system, edit the **config.lua** file:

```lua
Config.ResetPassword = {
    coords = vec3(1000.32, -103.89, 73.95),
    ped = {
        coords = vec3(1000.32, -103.89, 73.95),
        h = 121.65,
        model = `a_m_m_afriamer_01`
    },
    blip = {
        coords = vec3(1000.32, -103.89, 73.95),
        name = 'Technical',
        sprite = 89,
        color = 1,
        scale = 0.5
    },
    money = 500
}
```
