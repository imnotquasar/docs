# History Entrie for Vehicle

{% hint style="info" %}
You can only use these events on client-side, do not try any other way.
{% endhint %}

This feature allows you to create a report for a vehicle and is only compatible when `Config.MDT.newMdt = false`. You can use this functionality alongside exports like `GetPlayerInfo` and `getSSURL` to generate detailed vehicle records.

***

## Parameters

The server callback requires three parameters:

{% stepper %}
{% step %}
### **Callback Function**

Executes when the server responds. The `resp` argument indicates success (`true`) or failure (`false`).
{% endstep %}

{% step %}
### **Data Object**

Contains the vehicle data to be stored in the record:

* **type** (string): Type of violation or event (e.g., `infraction`). Do not modify this value.
* **plate** (string): The vehicle's license plate.
* **zone** (string): The name of the area or related official.
* **data** (table): Key-value pairs with additional information about the vehicle:
  * **key**: The label/title of the data.
  * **value**: The content/value of the data.
{% endstep %}
{% endstepper %}

***

## Example (Client-Side)

```lua
TriggerServerCallback("qs-dispatch:server:setVehicleDataRecord", function(resp)
    if resp then
        print("BOLO SUCCESS")
    else
        print("BOLO ERROR")
    end
end, {
    type = "infraction",
    plate = "ABC123",
    zone = "Downtown",
    data = {
        { key = "Model", value = "Sedan" },
        { key = "Plate", value = "ABC123" },
        { key = "Color", value = "Red" },
        { key = "Speed", value = "60 km/h" },
        { key = "Zone", value = "Downtown" },
        { key = "Limit", value = "50 km/h" },
        { key = "Fine", value = "100$" },
        { key = "Image", value = "https://example.com/image.jpg" }
    }
})
```

* This feature is intended for **client-side** usage.
* Ensure the data passed to the `data` table is relevant and correctly formatted.
* The `plate` and `zone` parameters should accurately represent the vehicle's details and location/event for better record-keeping.
