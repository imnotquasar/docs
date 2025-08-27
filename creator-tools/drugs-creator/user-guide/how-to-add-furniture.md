# How to add furniture

{% hint style="info" %}
If you edit this, do so at your own risk, it is long and very advanced code, do not touch it without a developer.
{% endhint %}

To add new furniture items to Quasar Drugs Creator, you will configure them in the **furniture configuration** in shared/furniture.lua section of your asset. This allows for customization of furniture pieces, including functionality as wardrobes, stashes, or purely decorative items. Here's a step-by-step explanation.

***

## Basic Structure

Each furniture entry includes the following:

<table><thead><tr><th width="279">Value</th><th>Description</th></tr></thead><tbody><tr><td><strong>Label</strong></td><td>Name displayed in the UI.</td></tr><tr><td><strong>Image</strong></td><td>Icon used in the UI.</td></tr><tr><td><strong>Object</strong></td><td>In-game prop model for the furniture.</td></tr><tr><td><strong>Type</strong></td><td>Determines functionality (e.g., stash or wardrobe).</td></tr><tr><td><strong>Offset</strong></td><td>Position offset for interactions.</td></tr><tr><td><strong>Stash Settings</strong> (if applicable)</td><td>Maximum weight and slots for storage.</td></tr></tbody></table>

***

## **Example: Adding a Washing Machine**

Below is an example of adding a washing machine with multiple variants.

```lua
['washingmachine'] = {
    label = 'Washing Machine',
    img = './assets/img/decorate/categories/rooms/bathroom/bathroom-washingmachine-blue.svg',
    navigation = 2,
    dynamic = true,
    dynamicIcon = './assets/img/decorate/categories/rooms/bathroom/bathroom-washingmachine-blue.svg',
    css = {
        width = 4.5,
        top = 7.7,
        left = 2.5,
    },
    items = {
        [1] = {
            ['img'] = './assets/img/decorate/categories/rooms/bathroom/items/washing/prop_rub_washer_01.png',
            ['object'] = 'prop_rub_washer_01',
            ['price'] = 250,
            ['label'] = 'Broken Washing Machine',
            ['description'] = 'Old and dirty washing machine, its cheap at least.',
            ['colorlabel'] = 'Gray',
            ['colors'] = {},
            type = 'stash',
            offset = {
                x = 0.0,
                y = 0.0,
                z = 0.0,
            },
            stash = {
                maxweight = 50000,
                slots = 3,
            }
        },
        [2] = {
            ['img'] = './assets/img/decorate/categories/rooms/bathroom/items/washing/prop_washer_02.png',
            ['object'] = 'prop_washer_02',
            ['price'] = 400,
            ['label'] = 'Clear Washing Machine',
            ['description'] = 'A beautiful washing machine, at a good price and completely new.',
            ['colorlabel'] = 'White',
            ['colors'] = {},
            type = 'stash',
            offset = {
                x = 0.0,
                y = 0.0,
                z = 0.0,
            },
            stash = {
                maxweight = 50000,
                slots = 3,
            }
        }
    }
}
```

***

## Steps to Add a New Furniture Item

{% stepper %}
{% step %}
### **Choose an Object**

Use a valid GTA V prop model.
{% endstep %}

{% step %}
### Define Functionality

* For storage: Use `type = 'stash'` with `stash` settings.
* For wardrobe: Use `type = 'wardrobe'`.
{% endstep %}

{% step %}
### Set Visuals

Include an image path and optional CSS for UI customization.
{% endstep %}

{% step %}
### Add to Config

Place your new entry in the furniture configuration file.
{% endstep %}
{% endstepper %}
