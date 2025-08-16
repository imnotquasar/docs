# qs-inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
    -- Coal Items
    ['coal_ore'] = {
        ['name'] = 'coal_ore',
        ['label'] = 'Coal Ore',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'coal_ore.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A piece of coal ore.'
    },

    ['flint'] = {
        ['name'] = 'flint',
        ['label'] = 'Flint',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'flint.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A sharp piece of flint.'
    },

    ['sulfur_chunk'] = {
        ['name'] = 'sulfur_chunk',
        ['label'] = 'Sulfur Chunk',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'sulfur_chunk.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A chunk of sulfur.'
    },

    -- Gold Items
    ['gold_nugget'] = {
        ['name'] = 'gold_nugget',
        ['label'] = 'Gold Nugget',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'gold_nugget.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A small nugget of gold.'
    },

    ['gold_dust'] = {
        ['name'] = 'gold_dust',
        ['label'] = 'Gold Dust',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'gold_dust.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A pinch of gold dust.'
    },

    ['quartz_crystal'] = {
        ['name'] = 'quartz_crystal',
        ['label'] = 'Quartz Crystal',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'quartz_crystal.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A clear quartz crystal.'
    },

    -- Emerald Items
    ['emerald_crystal'] = {
        ['name'] = 'emerald_crystal',
        ['label'] = 'Emerald Crystal',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'emerald_crystal.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A radiant emerald crystal.'
    },

    ['beryl_chunk'] = {
        ['name'] = 'beryl_chunk',
        ['label'] = 'Beryl Chunk',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'beryl_chunk.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A chunk of beryl.'
    },

    ['green_garnet'] = {
        ['name'] = 'green_garnet',
        ['label'] = 'Green Garnet',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'green_garnet.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A precious green garnet.'
    },

    -- Ruby Items
    ['ruby_crystal'] = {
        ['name'] = 'ruby_crystal',
        ['label'] = 'Ruby Crystal',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'ruby_crystal.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A brilliant ruby crystal.'
    },

    ['corundum_chunk'] = {
        ['name'] = 'corundum_chunk',
        ['label'] = 'Corundum Chunk',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'corundum_chunk.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A chunk of corundum.'
    },

    ['pink_sapphire'] = {
        ['name'] = 'pink_sapphire',
        ['label'] = 'Pink Sapphire',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'pink_sapphire.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A delicate pink sapphire.'
    },

    -- Amethyst Items
    ['amethyst_geode'] = {
        ['name'] = 'amethyst_geode',
        ['label'] = 'Amethyst Geode',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'amethyst_geode.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A beautiful amethyst geode.'
    },

    ['purple_quartz'] = {
        ['name'] = 'purple_quartz',
        ['label'] = 'Purple Quartz',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'purple_quartz.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A piece of purple quartz.'
    },

    ['clear_crystal'] = {
        ['name'] = 'clear_crystal',
        ['label'] = 'Clear Crystal',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'clear_crystal.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A clear and pristine crystal.'
    },

    -- Diamond Items
    ['diamond_crystal'] = {
        ['name'] = 'diamond_crystal',
        ['label'] = 'Diamond Crystal',
        ['weight'] = 250,
        ['type'] = 'item',
        ['image'] = 'diamond_crystal.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'An exquisite diamond crystal.'
    },

    ['graphite_chunk'] = {
        ['name'] = 'graphite_chunk',
        ['label'] = 'Graphite Chunk',
        ['weight'] = 200,
        ['type'] = 'item',
        ['image'] = 'graphite_chunk.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A chunk of graphite.'
    },

    ['blue_diamond'] = {
        ['name'] = 'blue_diamond',
        ['label'] = 'Blue Diamond',
        ['weight'] = 150,
        ['type'] = 'item',
        ['image'] = 'blue_diamond.png',
        ['unique'] = false,
        ['useable'] = false,
        ['shouldClose'] = true,
        ['combinable'] = nil,
        ['description'] = 'A rare and valuable blue diamond.'
    },
```
