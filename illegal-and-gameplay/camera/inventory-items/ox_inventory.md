# ox\_inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
["photo"] = {
    label = "Photo",
    weight = 1,
    stack = false,
    close = false,
    consume = 0,
    client = {
        export = 'qs-camera.usePhoto',
    },
},

["camera"] = {
    label = "Camera",
    weight = 1,
    stack = false,
    close = true,
    description = nil
},

["broken_camera"] = {
    label = "Broken Camera",
    weight = 1,
    stack = false,
    close = true,
    description = nil
},

["camera_module"] = {
    label = "Camera module",
    weight = 1,
    stack = false,
    close = true,
    description = nil
},
```
