# ox\_inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
    ['tradingcard_basic'] = {
        label = 'Trading Card Basic',
        weight = 150,
        stack = false,
        consume = 0,
        server = {
            export = 'qs-tradingcards.OpenInterationMenu',
        }
    },

    ['tradingcard_rare'] = {
        label = 'Trading Card Rare',
        weight = 150,
        stack = false,
        consume = 0,
        server = {
            export = 'qs-tradingcards.OpenInterationMenu',
        }
    },

    ['tradingcard_legendary'] = {
        label = 'Trading Card Legendary',
        weight = 150,
        stack = false,
        consume = 0,
        server = {
            export = 'qs-tradingcards.OpenInterationMenu',
        }
    },

    ['tradingcard_booster_pack'] = {
        label = 'Trading Card Booster',
        weight = 150,
        stack = false,
        consume = 0,
        client = {
            export = 'qs-tradingcards.OpenBoosterPack',
        }
    },
    
    ['tradingcard_booster_legends'] = {
        label = 'Trading Card Booster Legends',
        weight = 150,
        stack = false,
        consume = 0,
        client = {
            export = 'qs-tradingcards.OpenBoosterPack',
        }
    },

    ['tradingcard_psa'] = {
        label = 'Trading Card Psa',
        weight = 150,
        stack = false,
        consume = 0,
        client = {
            export = 'qs-tradingcards.openPsa'
        },
    },

    ['tradingcard_stash'] = {
        label = 'Trading Card Stash',
        weight = 150,
        stack = false,
        consume = 0,
        server = {
            export = 'qs-tradingcards.openAlbum',
        },
    },
```
