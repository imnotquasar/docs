# getSSURL

The getSSURL export allows you to retrieve a screenshot of the local player (client) dynamically. This can be useful for creating visual evidence, sending images to a server, or for custom gameplay features.

***

## How to Use

To get the screenshot URL, use the following code:

```lua
exports['qs-dispatch']:getSSURL(function(image)
    print("Screenshot URL: " .. (image or "No image available"))
end)
```

This export runs asynchronously and returns a string containing the image URL, such as `cdn.discordapp.net/image.png`. If the screenshot cannot be taken, the `image` variable will return `nil`. You can use this export to integrate screenshots into your scripts dynamically.
