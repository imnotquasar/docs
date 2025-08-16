# Automatic Payment

The **Auto Pay System** simplifies the process of handling unpaid invoices by introducing an automated mechanism that ensures invoices are managed efficiently. This system is ideal for situations where a payment deadline is required, automatically handling overdue invoices after the specified time.

{% stepper %}
{% step %}
### **Automatic Payment Handling**

Automatically processes overdue invoices after a defined time limit, ensuring no invoices are left unpaid indefinitely.
{% endstep %}

{% step %}
### **Configurable Payment Deadlines**

Define the maximum number of days a user has to pay an invoice before the system intervenes.
{% endstep %}

{% step %}
### **Regular Invoice Checks**

Periodically reviews unpaid invoices at set intervals, ensuring the system operates smoothly and efficiently.
{% endstep %}
{% endstepper %}

***

## **Configuration Options**

{% stepper %}
{% step %}
### **Config.AutoPayInterval**

This value determines the interval, in minutes, at which the system checks for unpaid invoices.\
Example:

```lua
Config.AutoPayInterval = 10 -- System checks every 10 minutes
```
{% endstep %}

{% step %}
### **Config.LimitToPayInvoice**

Specifies the maximum number of days allowed to pay an invoice before it is automatically handled.

```lua
Config.LimitToPayInvoice = 7 -- Invoices must be paid within 7 days
```
{% endstep %}
{% endstepper %}

***

## **How It Works**

{% stepper %}
{% step %}
### **Invoice Creation**&#x20;

When an invoice is issued, it is added to the system with a timestamp.
{% endstep %}

{% step %}
### **Regular Checks**

The system reviews all unpaid invoices at intervals specified by `Config.AutoPayInterval`.
{% endstep %}

{% step %}
### **Overdue Handling**

If the `Config.LimitToPayInvoice` threshold is exceeded, the system takes predefined actions, such as marking the invoice as unpaid or processing it automatically.
{% endstep %}
{% endstepper %}

This configuration ensures a streamlined approach to managing invoices, reducing manual oversight while maintaining accountability.
