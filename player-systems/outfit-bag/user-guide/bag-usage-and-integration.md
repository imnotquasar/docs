# Bag Usage & Integration

This guide explains how players can use outfit bags and how server admins can integrate them into shops or create default bags at specific locations.

***

## For Players

### Getting Started

{% stepper %}
{% step %}
### **Obtain an outfit bag**

You can get it from in-game shops, trades, or directly from admins.
{% endstep %}

{% step %}
### **Equip your desired outfit**

Visit a clothing store and customize your character.
{% endstep %}

{% step %}
### **Use the outfit bag**

&#x20;Open your inventory and use the item.
{% endstep %}

{% step %}
### **Save your current outfit**

Assign a custom name and store the outfit inside the bag.
{% endstep %}
{% endstepper %}

***

### Managing Outfits

* **Save Multiple Outfits** – Keep several styles in a single bag.
* **Load Outfits Instantly** – Change your appearance in seconds.
* **Rename Outfits** – Keep your collection organized with proper labels.
* **Delete Outfits** – Clean up old or unused styles easily.

***

### Using Default Bags

{% stepper %}
{% step %}
### **Locate default bags** placed at fixed map locations.
{% endstep %}

{% step %}
### **Walk up to the bag** and interact with it.
{% endstep %}

{% step %}
### **View available outfits** – Filtered by your job or public access.
{% endstep %}

{% step %}
### **Equip the outfit** – Instantly apply the pre-configured look.
{% endstep %}
{% endstepper %}

***

## For Server Administrators

### Adding Outfit Bags to Shops

To make outfit bags available for purchase in shops, you can add them as items.\
**Example for `qb-shops`:**

```lua
{
    name = 'outfitbag',
    price = 750,
    amount = 50,
    info = {},
    type = 'item',
    slot = 15,
}
```
