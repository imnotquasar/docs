# Server-side invoice

The `ServerCreateInvoice` export allows you to create invoices directly from the server side. This is ideal for automated or scripted billing scenarios, where players or entities need to be invoiced without manual interaction.

***

## How to Use

To create an invoice from the server, use the following export:

```lua
exports['qs-billing']:ServerCreateInvoice(source, title, description, amount, isSociety, isAlreadyPaid, giveItem, questToGiveItem, customSocietyName or nil)
```

### Parameters Explained

* **`source`**: The source player ID receiving the invoice.
* **`title`**: A short, descriptive title for the invoice.
* **`description`**: A detailed explanation of the invoice's purpose or charges.
* **`amount`**: The total amount to be paid for the invoice.
* **`isSociety`**: Always set to `true` to ensure the invoice is linked to a society. Setting it to `false` may cause issues.
* **`isAlreadyPaid`**: If `true`, the invoice is marked as paid and logged as payment history. If `false`, the invoice requires payment.
* **`giveItem`**: If `true`, the player will receive the invoice as an item. If `false`, the invoice is virtual.
* **`questToGiveItem`**: If `true`, the player will be prompted to accept the invoice item. If `false`, the item is automatically handled based on the `giveItem` parameter.
* **`customSocietyName`** _(optional)_: Customizes the society name issuing the invoice. Use `nil` to default to the standard society name.

***

## Example Usage

The following example demonstrates creating an invoice through a command:

```lua
RegisterCommand('testInvoice', function(source, args, rawCommand)
    exports['qs-billing']:ServerCreateInvoice(source, 'Car Repair', 'Invoice for repairing vehicle damage', 5000, true, false, true, true, nil)
end, false)
```

### In this example

* The invoice is created for the player running the command.
* The title is "Car Repair," and the description is "Invoice for repairing vehicle damage."
* The invoice amount is `$5000`.
* The invoice is linked to a society and remains unpaid.
* The player is given the invoice as an item with a prompt to accept it.
