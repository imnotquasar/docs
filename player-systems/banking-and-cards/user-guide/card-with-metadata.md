# Card With Metadata

The metadata system allows for advanced functionality, such as using credit cards to access ATMs, creating cards at designated spots, and adding security features like passwords. This system requires an inventory system compatible with metadata to function properly.

***

## How to Enable Metadata Functionality

To activate the metadata system, locate the `Config.Metadata` section in your `config.lua` and set it to `true`:

```lua
Config.Metadata = true
```

#### **Features When Metadata is Enabled:**

* Access ATMs using credit cards with metadata.
* If a card is stolen and the password is known, other players can access the bank account tied to the card.
* Option to add card creation spots outside banks for more flexibility.

***

## How to Disable Metadata Functionality

If you prefer not to use metadata, set the configuration to `false`:

```lua
Config.Metadata = false
```

#### **Limitations Without Metadata:**

* ATMs and credit cards cannot be used.
* Only personal bank accounts will be accessible.

***

## Configuring Card Creation Spots (Optional)

If the metadata system is active, you can configure additional spots for card creation outside of banks. This is optional, as cards can also be created directly at banks.

#### **Example Configuration:**

```lua
Config.CreateCardEverywhere = false -- Restrict card creation to specific spots
Config.CreateCard = {
    {
        coords = vec3(143.266, -1042.591, 29.368) -- Example spot for card creation
    },
    -- Add more spots as needed
    -- {
    --     coords = vec3(150.0, -1040.0, 29.0)
    -- }
}
```

If `Config.CreateCardEverywhere` is set to `true`, cards can be created at all banks without needing to configure specific spots.
