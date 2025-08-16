# Client-side invoice

The CreateInvoice server-side export allows you to generate invoices programmatically within the Quasar Billing system. This is particularly useful for creating customized billing scenarios for various jobs, businesses, or gameplay mechanics.

***

## How to Use

To create an invoice, trigger the following server event:

```lua
TriggerServerEvent('qs-billing:server:CreateInvoice', receiverId, 'title', 'description', amount, isSociety, isAlreadyPaid, giveItem, questToGiveItem, customSocietyName or nil)
```

### Parameters Explained

* **`receiverId`**: The player ID receiving the invoice.
* **`title`**: A short title for the invoice.
* **`description`**: A detailed description of the invoice.
* **`amount`**: The invoice amount to be paid.
* **`isSociety`**: Always set to `true` to ensure compatibility. Using `false` may result in unexpected behavior.
* **`isAlreadyPaid`**: If `true`, the invoice is marked as paid and logged as payment history. If `false`, the player must pay the invoice.
* **`giveItem`**: If `true`, the player will receive the invoice as an item. If `false`, the invoice remains virtual.
* **`questToGiveItem`**: If `true`, the player is prompted to accept the invoice item. If `false`, the invoice is automatically given or not, depending on `giveItem`.
* **`customSocietyName`** _(optional)_: Allows setting a custom name for the company issuing the invoice. Use `nil` to default to the standard society name.

***

## Example Usage

Here’s an example of how to use this export to create an invoice via a custom command:

```lua
RegisterCommand('testinvoice', function()
    TriggerServerEvent('qs-billing:server:CreateInvoice', 1, 'Car Repair', 'Repair services for vehicle damage', 5000, true, false, true, true, nil)
end, false)
```

### Additional Notes

{% stepper %}
{% step %}
#### Ensure that `customSocietyName` is included server-side; otherwise, the event may not function correctly.
{% endstep %}

{% step %}
#### Always verify the `receiverId` to avoid targeting non-existent players.
{% endstep %}

{% step %}
#### Use this export cautiously, as improper parameter handling can disrupt gameplay.
{% endstep %}
{% endstepper %}
