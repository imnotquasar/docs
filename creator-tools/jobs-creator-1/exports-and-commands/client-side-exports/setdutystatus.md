---
description: >-
  This document explains how to force a player on or off duty from the client
  side using the SetDutyStatus export provided by qs-police-creator.
---

# SetDutyStatus

### What SetDutyStatus does

`SetDutyStatus(status)` allows any **client-side script** to:

* Force the player **on duty or off duty**
* Instantly update the dispatch UI duty state
* Synchronize duty status with the internal qs-police-creator system

***

### Export signature

```lua
exports['qs-police-creator']:SetDutyStatus(status)
```

#### Parameters

| Name     | Type    | Description                          |
| -------- | ------- | ------------------------------------ |
| `status` | boolean | `true` = On Duty, `false` = Off Duty |

***

### Basic usage

#### Force player ON duty

```lua
exports['qs-police-creator']:SetDutyStatus(true)
```

***

#### Force player OFF duty

```lua
exports['qs-police-creator']:SetDutyStatus(false)
```

***

### Behavior

When called, `SetDutyStatus` will:

* Set the internal duty state
* Notify the dispatch UI of the change
* Apply the duty state immediately (no toggle, no checks)

It **does not**:

* Validate job type
* Check permissions
* Toggle automatically

The caller is responsible for ensuring correct usage.

***

### Example use cases

#### Auto-duty when player spawns

```lua
AddEventHandler('playerSpawned', function()
    exports['qs-police-creator']:SetDutyStatus(true)
end)
```

***

#### Job-based duty control

```lua
if PlayerJob == 'police' then
    exports['qs-police-creator']:SetDutyStatus(true)
else
    exports['qs-police-creator']:SetDutyStatus(false)
end
```

***

#### Admin or command usage

```lua
RegisterCommand('forceduty', function()
    exports['qs-police-creator']:SetDutyStatus(true)
end)
```

***

### Important notes

* This export is **client-side only**
* It affects **only the local player**
* Always pass a boolean (`true` / `false`)
* Use responsibly — this bypasses UI interaction

***

### Quick tips

* Do not call repeatedly in loops
* Best used for explicit state changes
