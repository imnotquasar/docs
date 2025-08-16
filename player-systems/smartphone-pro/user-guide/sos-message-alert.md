---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# SOS Message alert

The **Smartphone PRO** features an SOS system that allows players to send emergency messages in critical situations. This system can be configured for manual or automatic use and customized for specific jobs like ambulances.

***

## Manual SOS System

Players can manually activate the SOS system by holding the phone's **close button**. This action opens the SOS screen, where they can slide the red slider to call for help, such as contacting an ambulance.

***

## Automatic SOS System

The automatic SOS system triggers when a player’s health drops below a configured threshold. The SOS message will appear on the screen, allowing them to request help automatically.

To disable the automatic SOS, set **Config.SOSMessage** to `false` in the configuration file.

```lua
-- SOS message when life is under Config.SOSHealth
Config.SOSMessage = true
Config.SOSJob = 'ambulance'
Config.SOSHealth = 25
```

This system ensures rapid communication during emergencies and can be customized to suit your server's needs.
