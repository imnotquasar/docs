# core\_inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

Add the item creditcard in database. In category column, set the category uniqueItem In core\_inventory/config.lua find ItemCategories and add in it:

```lua
["uniqueItem"] = {
    color = "#87ceeb",
    takeSound = 'take',
    putSound = 'put',
},
```

In core\_inventory/config.lua find ShownMetadatatable and add in it:

```lua
['cardNumber'] = 'Card Number',
['ownerName'] = 'Owner name',
['cardtype'] = 'Card Type',
```
