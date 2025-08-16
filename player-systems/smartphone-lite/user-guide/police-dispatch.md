---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Police dispatch

The Quasar Smartphone includes a police app with a simple yet functional MDT for receiving alerts and dispatches. Officers can get notifications with locations for various incidents.

***

## How to use the event

To send a police dispatch, you use a server-side script since client-side exports are unavailable. Here’s an example of how to trigger a police alert:

```lua
local alertData = {
    title = "Store Robbery",
    coords = {x = GetEntityCoords(GetPlayerPed(1)).x, y = GetEntityCoords(GetPlayerPed(1)).y, z = GetEntityCoords(GetPlayerPed(1)).z},
    description = "A robbery started at the store!"
}
TriggerClientEvent("qs-smartphone:client:addPoliceAlert", -1, alertData)
```

This will send an alert titled **"Store Robbery"** with the coordinates of the incident to all players. Customize the **title**, **description**, and other details as needed.
