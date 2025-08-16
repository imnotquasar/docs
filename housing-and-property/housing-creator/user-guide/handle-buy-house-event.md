---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Handle Buy House Event

The `housing:handleBuyHouse` event is designed to trigger when a player purchases a house in the **Housing** system. This event allows developers to listen to the transaction and implement custom logic such as logging, external integrations, or additional processes.

***

## Event syntax <a href="#event-syntax" id="event-syntax"></a>

```lua
AddEventHandler('housing:handleBuyHouse', function(playerSrc, house, housePrice, isCredit)
    -- Your custom logic here
end)
```

***

### Parameters Explained <a href="#parameters-explained" id="parameters-explained"></a>

<table><thead><tr><th width="279">Value</th><th>Description</th></tr></thead><tbody><tr><td><strong><code>playerSrc</code></strong></td><td>The server ID of the player who is purchasing the house.</td></tr><tr><td><strong><code>house</code></strong></td><td>The unique identifier of the house being purchased.</td></tr><tr><td><strong><code>housePrice</code></strong></td><td>The price of the house.</td></tr><tr><td><strong><code>isCredit</code></strong></td><td>A boolean value indicating if the house is being purchased with credit (<code>true</code>) or with direct payment (<code>false</code>).</td></tr></tbody></table>

***

## Example use case <a href="#example-use-case" id="example-use-case"></a>

Log the details of the house purchase to the console or a file for administrative purposes.

```lua
AddEventHandler('housing:handleBuyHouse', function(playerSrc, house, housePrice, isCredit)
    print(("[Housing] Player %d purchased house %s for $%d. Payment method: %s"):format(
        playerSrc, house, housePrice, isCredit and "Credit" or "Cash"
    ))
end)
```
