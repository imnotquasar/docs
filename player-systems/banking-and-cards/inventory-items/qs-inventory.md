# qs-inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
['creditcard'] = {
    ['name'] = 'creditcard',
    ['label'] = 'Credit Card',
    ['weight'] = 0,
    ['type'] = 'item',
    ['image'] = 'creditcard.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = false,
    ['combinable'] = nil,
    ['description'] = 'Visa card, can be used via ATM',
    client = { export = 'qs-banking.CreateCard' }
},
```

In case of qs-inventory, we can add the following item inside config/metadata.js:

```lua
} else if (itemData.name == "visa" || itemData.name == "creditcard") {
    $(".item-info-title").html('<p>' + label + '</p>')
        var str = "" + itemData.info.cardNumber + "";
        var res = str.slice(12);
        var cardNumber = "************" + res;
        $(".item-info-description").html('<p><strong>Card Owner: </strong><span>' + itemData.info.ownerName + '</span></p><p><strong>Card Type: </strong><span>' + itemData.info.cardType + '</span></p><p><strong>Card Number: </strong><span>' + cardNumber + '</span></p>'
);
```
