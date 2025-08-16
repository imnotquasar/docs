# Change default number

Changing the default phone number depends on your framework and requires careful attention to avoid breaking internal files, as ESX and QBCore have entirely different approaches.

***

## **Change the default phone number in ESX**

In ESX, the process is straightforward. Navigate to **qs-base/config.lua**, where you can modify the prefix and the number of digits assigned to the player:

```lua
Config.NumberPrefix = '553' -- Prefix of the number
Config.NumberDigits = 6 -- Amount of digits after the prefix
```

***

## **Change the default phone number in QBCore**

In QBCore, the process is more advanced. Access **qb-core/server/player.lua** and locate the **CreatePhoneNumber()** function:

```lua
function QBCore.Functions.CreatePhoneNumber()
    local UniqueFound = false
    local PhoneNumber = nil
    while not UniqueFound do
        PhoneNumber = math.random(100, 999) .. math.random(1000000, 9999999)
        local query = '%' .. PhoneNumber .. '%'
        local result = MySQL.prepare.await('SELECT COUNT(*) as count FROM players WHERE charinfo LIKE ?', { query })
        if result == 0 then
            UniqueFound = true
        end
    end
    return PhoneNumber
end
```

To change the prefix or number length, you can edit the first **math.random** value to set a fixed prefix or a dynamic one using **math.random**, while the second value determines the number of digits.&#x20;

Example of a custom number:

```lua
PhoneNumber = '376' .. math.random(100000, 999999)
```

This creates a phone number with the prefix **376** followed by six random digits. Adjust the values as needed to suit your server's configuration.
