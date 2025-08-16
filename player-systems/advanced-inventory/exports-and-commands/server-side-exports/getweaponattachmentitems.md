# GetWeaponAttachmentItems

**The `GetWeaponAttachmentItems` export** allows you to retrieve the full list of weapon attachments configured in your `config.lua`, including suppressors, scopes, magazines, flashlights, tints, and more. This is useful for managing compatible attachments dynamically within your scripts or inventory systems.

***

## How to Use

To get the full list of weapon attachments, use the following code:

```lua
local attachmentList = exports['qs-inventory']:GetWeaponAttachmentItems()

for _, attachment in pairs(attachmentList) do
    print("Item: " .. attachment.item)
    print("Attachment Type: " .. attachment.type)
    print("Attachment ID: " .. attachment.attachment)
end
```

This will return a table with all available attachment entries. Each attachment contains properties such as:

* `item`: The inventory item name.
* `attachment`: The internal attachment ID used by the weapon system.
* `type`: The category (e.g., `suppressor`, `clip`, `scope`, `tint`, `flash`).
* Optional: `tint`, `label`, `forEveryWeapon`, `isUrlTint`.

You can use this export to build custom weapon customization UIs, validate items, or extend the functionality of your weapon systems with ease.
