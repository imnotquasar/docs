# qb-inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
['creditcard'] 			 = {['name'] = 'creditcard', 					['label'] = 'Credit Card', 				['weight'] = 10, 		['type'] = 'item', 		['image'] = 'creditcard.png', 				['unique'] = false, 		['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'Visa card, can be used via ATM'},
```

In case we want to see the item information, we will add the following case in qb-inventory/html/js/apps.js within the generateDescription function.

```lua
case "creditcard":
   var str = "" + itemData.info.cardNumber + "";
   var res = str.slice(12);
   var cardNumber = "************" + res;
   return `<p><strong>Card Owner: </strong><span>${itemData.info.ownerName}</span></p>
      <p><strong>Card Type: </strong><span>${itemData.info.cardType}</span></p>
      <p><strong>Card Number: </strong><span>${cardNumber}</span></p>`;
```
