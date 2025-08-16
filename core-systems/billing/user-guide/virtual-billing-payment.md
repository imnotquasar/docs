# Virtual Billing Payment

The **Virtual Billing Payment** system allows for invoice payments via virtual bank transfer. This system provides a convenient way for players to pay invoices while incorporating a configurable tax percentage for electronic transactions, enhancing the realism of the system.

{% stepper %}
{% step %}
### **Electronic Transfers**

Invoices can be paid through a virtual transfer system directly linked to the society bank account.
{% endstep %}

{% step %}
### **Configurable Transaction Fee**

A percentage-based tax is applied to the invoice amount for electronic payments.
{% endstep %}

{% step %}
### **Custom Prefix for Societies**

Societies can be identified using a configurable prefix, simplifying integration with other systems.
{% endstep %}
{% endstepper %}

***

## **Configuration Example**

Below is an example of how to configure the virtual billing payment system in your `config.lua` file:

```lua
Config.SocietyPrefix = 'society_' -- Prefix used for society accounts
Config.PercentageOfElectronicTransaction = 3 -- Percentage of the invoice amount as a tax for electronic transactions
```

***

## **How It Works**

{% stepper %}
{% step %}
### **Invoice Payment**

* Players can pay invoices electronically.
* A 3% tax (or your configured percentage) is added to the total invoice amount.
{% endstep %}

{% step %}
### **Society Prefix**

* The system uses `Config.SocietyPrefix` to identify the bank accounts for each society.
* For example, a payment to the "police" society would reference `society_police`.
{% endstep %}

{% step %}
### **Configurable Tax**

* Adjust `Config.PercentageOfElectronicTransaction` to change the tax percentage.
* Example:
  * Invoice Amount: $1,000
  * Tax: 3%
  * Total Payment: $1,030
{% endstep %}
{% endstepper %}
