# getMetaFromSource

The **getMeta** export retrieves the metadata of the phone a player is currently using or the last phone they used. This metadata can include information such as the phone's unique attributes or data associated with it.

***

## How to Use

To retrieve a player's phone metadata, use the following code:

```lua
local playerSource = source -- Replace with the player's source ID

local phoneMeta = exports['qs-smartphone-pro']:getMetaFromSource(playerSource)

if phoneMeta then
    print("Phone Metadata: " .. json.encode(phoneMeta, { indent = true }))
else
    print("No phone metadata found for this player.")
end
```

## Parameter

* **source**: The player's source ID (e.g., the server-side identifier for the player).

This export returns a table containing the phone's metadata or `false` if no metadata is found. It is particularly useful for debugging, tracking phone usage, or managing custom features related to the phone.
