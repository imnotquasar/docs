# General Configuration

All configuration for **Quasar Outfit Bag** is managed from `shared/config.lua`. Thanks to its intelligent auto-detection system, only minimal adjustments are required to get started.

***

## Basic Settings

All core settings are found in `shared/config.lua`. You can adjust debug mode, language, item name, and the model used for the outfit bag. The system is designed to work out of the box, requiring only minimal changes.

```lua
Config.Debug = false -- Enable debug messages for troubleshooting
Config.Language = 'en' -- Set your preferred language
Config.ItemName = 'outfitbag' -- Name of the outfit bag item
Config.BagModel = 'reh_prop_reh_bag_outfit_01a' -- 3D model for the bag
```

Use `Config.Debug` for testing, select your preferred `Config.Language`, define the inventory item with `Config.ItemName`, and set the bag's 3D appearance using `Config.BagModel`.
