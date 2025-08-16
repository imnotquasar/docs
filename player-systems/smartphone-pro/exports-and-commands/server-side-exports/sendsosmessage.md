# sendSOSMessage

The **sendSOSMessage** export allows you to send an SOS message to a specified job. This message can include the sender's location or other relevant details, making it ideal for emergency systems.

***

## How to Use

To send an SOS message, use the following code:

```lua
local phoneNumber = "123456" -- Replace with the sender's phone number
local job = "ambulance" -- The job to receive the SOS message
local coords = { x = 100.0, y = 200.0, z = 300.0 } -- Coordinates to send
local messageType = "location" -- Use 'location' to send a location-based SOS

exports['qs-smartphone-pro']:sendSOSMessage(phoneNumber, job, json.encode(coords), messageType)
```

## Parameters

* **phoneNumber**: The sender's phone number.
* **job**: The job that will receive the SOS message (e.g., `'ambulance'`, `'police'`).
* **coords**: The coordinates to include in the message, encoded as JSON.
* **type**: The type of message. Use `'location'` to send a location-based message.

This export is useful for creating emergency features, allowing players to quickly notify specific jobs with critical information. Ensure the phone number and job values are correctly defined for optimal functionality.
