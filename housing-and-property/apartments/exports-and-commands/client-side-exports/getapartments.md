# GetApartments

The `GetApartments` export allows you to **retrieve the full list of configured apartments** programmatically. This can be useful for **displaying available apartments, handling property data, or integrating with other systems**.

***

## How to Use

To get the list of all apartments, use the following code:

```lua
local apartments = exports['qs-apartments']:GetApartments()
if apartments then
    print("Apartments retrieved successfully!")
    for name, data in pairs(apartments) do
        print("Apartment Name: " .. name)
        print("Location: " .. data.label)
        print("Price: $" .. data.price)
    end
else
    print("No apartments found.")
end
```

### **Explanation**

* exports\['qs-apartments']:GetApartments() → Returns the Apartments table containing all configured apartments.
* If apartments exist, it loops through them to print name, location, and price.
* If no apartments are found, it returns nil.

This function is ideal for **custom menus, listings, or integration with other scripts** to manage housing dynamically.
