# sendNewMessageFromApp

The **sendNewMessageFromApp** export allows you to send a new message from an app to a player's phone. This is commonly used for app-related notifications, such as verification messages or alerts.

***

## How to Use

To send a message from an app, use the following code:

```lua
local source = playerSource -- Replace with the player's source ID
local phoneNumber = "123456" -- Phone number of the recipient
local message = "Welcome to our app! Here's your verification code: 12345" -- Message content
local appName = "twitter" -- The name of the app sending the message

exports['qs-smartphone-pro']:sendNewMessageFromApp(source, phoneNumber, message, appName)
```

## Parameters

* **source**: The player's source ID.
* **phoneNumber**: The phone number of the person receiving the message.
* **message**: The content of the message to send.
* **appName**: The name of the app sending the message.

This export is ideal for sending app-generated notifications, such as account verifications or system alerts, directly to a player's phone in a realistic and immersive way.
