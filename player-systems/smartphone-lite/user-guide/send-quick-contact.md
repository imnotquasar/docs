# Send quick contact

Unlike other phones on the FiveM market, Quasar Smartphone makes it easy to share contact details with other players. Here are the different methods to give a contact.

{% stepper %}
{% step %}
### **Radial menu integration**

You can integrate it into a radial menu using the example from **qb-radialmenu**.
{% endstep %}

{% step %}
### **Classic AirDrop**

Swipe down on your phone screen to access the options menu, where you'll find the AirDrop feature.
{% endstep %}

{% step %}
### **Contact via command**

Use the **/givecontact** command to share your contact with a nearby player.
{% endstep %}

{% step %}
### **Executable event**

You can use an event in your other scripts to give your contact to a nearby player.
{% endstep %}
{% endstepper %}

***

## **Integration with qb-radialmenu**

You can integrate contact sharing directly into **qb-radialmenu**, similar to the integration available for **qb-phone**. Use the following snippet to add this feature to your radial menu:

```lua
{
    id = 'givenum',
    title = 'Give Contact Details',
    icon = 'address-book',
    type = 'client',
    event = 'qs-smartphone:client:GiveContactDetails',
    shouldClose = true
}
```

***

## **Give contact via AirDrop**

By swiping down on the phone, you can access the sliding menu, which includes a button for sharing contacts via AirDrop. This feature sends the contact to the nearest player, who will receive a notification and the contact in their Contacts app.

<div data-full-width="true"><figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure></div>

***

## **Give contact by command**

You can also share a contact using the **/givecontact** command, which sends the contact to the nearest player in the same way as AirDrop.

***

## **Integration event to give contact**

The event **qs-smartphone:client:GiveContactDetails** allows external assets to trigger contact sharing. This is especially useful for custom menus or radial systems. When executed, it sends the contact to the nearest player.
