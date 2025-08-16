# handleRentPayment

The `housing:handleRentPayment` event is triggered each time a rent payment is processed for a property.\
This allows external scripts to track rent-related activity or perform custom actions such as logging, rewards, or penalties.

#### Event Parameters

* **`house`**: The name or ID of the house being rented.
* **`identifier`**: The identifier (usually Steam or Rockstar ID) of the player making the payment.
* **`payed`**: A boolean indicating if the rent was successfully paid (`true`) or not (`false`).

***

## **How to Use**

To listen for rent payment events in your script, use the following pattern:

```lua
AddEventHandler('housing:handleRentPayment', function(house, identifier, payed)
    if payed then
        print(('[Rent Paid] Player %s has paid rent for house %s.'):format(identifier, house))
    else
        print(('[Rent Failed] Player %s failed to pay rent for house %s.'):format(identifier, house))
    end
end)
```

Here’s an example of how you could log all successful rent payments to a file:

```etlua
AddEventHandler('housing:handleRentPayment', function(house, identifier, payed)
    if payed then
        local logMessage = os.date('[%Y-%m-%d %H:%M:%S]') ..
            (' Rent paid for %s by %s\n'):format(house, identifier)

        SaveResourceFile('my-logger', 'rent_logs.txt', logMessage, -1)
    end
end)
```

This code listens for rent payments and writes successful transactions to a text file for later review.
