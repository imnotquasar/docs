# getHouseRoutingId

The `getHouseRoutingId` export allows you to retrieve the _Routing Bucket ID_ of a house instance.\
This is useful for checking if a specific house is currently active (someone is inside) or to manage instance-based logic inside houses.

***

## **How to Use**

To get the routing ID of a house, use the following code:

```lua
local routingId = exports['qs-housing']:getHouseRoutingId('house')
if not routingId then
    print('Nobody is home!')
end

print('Routing ID:', routingId)
```

Here’s an example of a command that checks if a specific house is occupied:

```etlua
RegisterCommand('checkhouserouting', function()
    local routingId = exports['qs-housing']:getHouseRoutingId('house')

    if not routingId then
        print('Result: Nobody is currently inside the house.')
    else
        print('Result: House is occupied. Routing ID:', routingId)
    end
end)
```

This example checks if the house identified by `'house'` has an active routing bucket.\
If no one is inside (`routingId` is `nil`), it prints that nobody is home.\
If there is an active routing bucket, it prints the `routingId`, indicating the house is currently being used.
