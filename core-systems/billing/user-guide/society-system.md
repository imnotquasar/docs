# Society System

The **Society System** allows you to configure multiple companies, granting them access to view, manage, and update invoices based on their job grade. This feature is useful for organizing company finances and assigning permissions within the society.

{% stepper %}
{% step %}
### **Multi-Society Support**

Configure as many societies as required for your server, each with unique settings.
{% endstep %}

{% step %}
### **Custom Grade Access**

Define which job grades (in **QBCore**) or grade names (in **ESX**) have access to society invoices.
{% endstep %}

{% step %}
### **Comprehensive Invoice Management**

Authorized grades can view all society invoices, delete them, or mark them as paid.
{% endstep %}
{% endstepper %}

***

## **Configuration Example**

Below is a configuration snippet for setting up societies with access control:

```lua
Config.Societys = {
    ['police'] = { -- Example of a society (e.g., Police Department)
        canAccessGrade = {
            [4] = true,        -- QBCore: Job grade 4 has access
            ['boss'] = true,   -- ESX: Job grade name 'boss' has access
        }
    },
    ['mechanic'] = { -- Example of another society (e.g., Mechanics)
        canAccessGrade = {
            [2] = true,        -- QBCore: Job grade 2 has access
            ['manager'] = true -- ESX: Job grade name 'manager' has access
        }
    }
}
```

***

## **How It Works**

{% stepper %}
{% step %}
## **Grade Access Configuration**

* **For QBCore**: Use numeric job grades (e.g., `[4] = true`) to specify access levels.
* **For ESX**: Use grade names (e.g., `['boss'] = true`) to define permissions.
{% endstep %}

{% step %}
## **Invoice Permissions**

* Authorized grades can:
  * View all society invoices.
  * Delete invoices as needed.
  * Mark invoices as paid.
{% endstep %}

{% step %}
## **Flexibility**

* Configure multiple societies independently with unique access controls for each.
{% endstep %}
{% endstepper %}
