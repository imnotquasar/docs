# core\_inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
["uniqueItem"] = {
    color = "#87ceeb",
    takeSound = 'take',
    putSound = 'put',
},
```

```lua
INSERT INTO `items` (`name`, `label`, `weight`, `category`) VALUES
    ('cryptostick', 'Crypto Stick', 50, 'uniqueItem'),
    ('phone_dongle', 'Phone Dongle', 50, 'uniqueItem'),
    ('powerbank', 'Power Bank', 50, 'uniqueItem'),
    ('phone', 'Classic Phone', 150, 'uniqueItem'),
    ('black_phone', 'Black Phone', 150, 'uniqueItem'),
    ('yellow_phone', 'Yellow Phone', 150, 'uniqueItem'),
    ('red_phone', 'Red Light Phone', 150, 'uniqueItem'),
    ('green_phone', 'Green Phone', 150, 'uniqueItem'),
    ('white_phone', 'White Phone', 150, 'uniqueItem');
```
