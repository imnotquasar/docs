# RegisterStash

The **RegisterStash** export allows you to create stashes directly from the client side. This is useful for setting up custom stash locations or containers dynamically. You can configure the stash identifier, number of slots, and total weight capacity.

***

## How to Use

To create a stash, use the following code:

```lua
-- Example stash configuration
local stashID = "example_stash" -- Unique identifier for the stash
local stashSlots = 50           -- Total number of slots
local stashWeight = 1000        -- Maximum weight capacity

exports['qs-inventory']:RegisterStash(stashID, stashSlots, stashWeight)
print("Stash registered: " .. stashID)
```

The export parameters are:

* **`stash`**: A unique identifier for the stash (e.g., "police\_armory").
* **`slots`**: The total number of item slots available in the stash.
* **`weight`**: The total weight capacity of the stash in your preferred unit.

This export allows for dynamic stash creation and is particularly useful for custom systems like private lockers, organization storage, or role-specific containers. For more advanced details, refer to the Feature Guides in this documentation.
