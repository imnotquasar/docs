# No-signal system

The telephone signal system is managed using PolyZone or ox\_lib, depending on the version of the Smartphone you are using. Dead zones are configured in **config.lua**.

Quasar Smartphone includes an advanced signal system that blocks certain applications when the user is in a no-signal area.

***

## **Export to check the signal**

You can use the following export to check the signal on the client side.

```lua
-- Check the signal from the client-side
exports['qs-smartphone']:CheckSignal()
```
