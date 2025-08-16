# WeaponWheel

The **WeaponWheel** export allows you to enable or disable the Weapon Wheel temporarily. This is intended for specific use cases, such as mini-games like battle royale, and is not meant for permanent use. Quasar Inventory will not register weapons when this system is enabled, so it should only be used for short-term scenarios.

***

## How to Use

To enable or disable the Weapon Wheel, use the following code:

```lua
-- Enable the Weapon Wheel
exports['qs-inventory']:WeaponWheel(true)

-- Disable the Weapon Wheel
exports['qs-inventory']:WeaponWheel(false)
```

This export is designed specifically for enabling the Weapon Wheel in controlled environments, such as mini-games, and should not be used as a replacement for the standard inventory weapon system.
