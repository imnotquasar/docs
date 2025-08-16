# RegisterStash

The **RegisterStash** export allows you to create stashes dynamically with a simple and flexible configuration.

***

## How to Use

To register a stash, use the following code:

```lua
local playerSource = 1 -- Replace with the player's source ID
local stashID = "police_armory" -- Unique identifier for the stash
local stashSlots = 50 -- Total number of slots available
local stashWeight = 1000 -- Maximum weight capacity of the stash

exports['qs-inventory']:RegisterStash(playerSource, stashID, stashSlots, stashWeight)
print("Stash registered: " .. stashID)
```

This creates a stash with the specified identifier, number of slots, and weight capacity for the specified player. Stashes can be used for custom storage solutions like personal lockers or organizational armories.
