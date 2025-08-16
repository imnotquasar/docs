# createCall

The `createCall` export allows you to start a phone call from your script. This can be used for custom systems like automated dispatch calls, job-based communication, or scripted events.

***

## How to Use

To start a call, use the following code:

```lua
-- Example: Create an outgoing call
-- @param name (string): Display name of the contact being called
-- @param number (string): Phone number to dial
-- @param image (string, optional): URL for the contact's avatar/image
-- @param anonymous (boolean, optional): If true, call is anonymous

exports['qs-smartphone-pro']:createCall('Police Department', '911', 'imageLink', true)
```

This export will initiate a call to the given number. You can pass an image and set it as anonymous if needed. Useful for job roles like EMS or Police.
