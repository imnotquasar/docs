# Plate Style System

The **Plate Style System** provides the ability to customize vehicle license plates, including variations in letters, numbers, spaces, and how players can interact with the plate customization process. This feature adds realism and flexibility to your server's vehicle registration system.

***

## Plate Customization

{% stepper %}
{% step %}
### **Config.PlateLetters**

Determines the number of letters in the plate (e.g., 3 for "ABC").
{% endstep %}

{% step %}
### **Config.PlateNumbers**

Determines the number of digits in the plate (e.g., 3 for "123").
{% endstep %}

{% step %}
### **Config.PlateUseSpace**

Enables or disables spaces in the plate format (e.g., "ABC 123" vs. "ABC123").
{% endstep %}

{% step %}
### **Config.TimeToChange**

Specifies the time (in milliseconds) required to change a plate (default: 5000ms or 5 seconds).
{% endstep %}
{% endstepper %}

***

## Plate Management Shop or Menu

You can manage the plate customization system through either a **menu** or a shop integrated with `qs-shops`. Both systems allow players to purchase or modify their license plates using items or currency.

{% stepper %}
{% step %}
### **Config.PlateType**

Specifies the interaction type, either `'menu'` (predefined menu) or `'shop'` (uses `qs-shops`).
{% endstep %}
{% endstepper %}

***

## Item and Pricing Configuration

{% stepper %}
{% step %}
### **Config.PlateItem**

The item used to manage plates, named `'plate'` by default.
{% endstep %}

{% step %}
### **Config.PlatePrice**

The price and payment method for purchasing the plate item. Supported accounts include:

* `'money'` (ESX only)
* `'cash'` (QBCore only)
* `'bank'` (both frameworks)
{% endstep %}

{% step %}
### **Config.ChangePlateItem**

The item required for changing the plate, named `'screwdriver'` by default.
{% endstep %}

{% step %}
### **Config.ChangePlateItemPrice**

The price and payment method for obtaining the item.
{% endstep %}
{% endstepper %}

***

## Example Use Case

A player wishes to customize their vehicle's license plate. They visit a designated **Ped** that provides access to the plate management menu or shop. Using in-game currency, the player purchases a plate (`Config.PlateItem`) and the necessary tools (`Config.ChangePlateItem`). After selecting their preferred style (e.g., letters, numbers, with or without spaces), they apply the changes within the allotted time (`Config.TimeToChange`). This system ensures immersive customization while maintaining server-side control over plate formats and pricing.
