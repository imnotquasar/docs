# qs-inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
['morphine_30mg'] = {
    ['name'] = 'morphine_30mg',
    ['label'] = 'Morphine 30MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'morphine_30mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Strong opioid injection providing high pain relief for severe injuries'
},

['morphine_15mg'] = {
    ['name'] = 'morphine_15mg',
    ['label'] = 'Morphine 15MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'morphine_15mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Moderate dose of morphine for controlled pain management'
},

['percocet_30mg'] = {
    ['name'] = 'percocet_30mg',
    ['label'] = 'Percocet 30MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'percocet_30mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'High dose of Percocet for treating severe pain with combined effect'
},

['percocet_15mg'] = {
    ['name'] = 'percocet_15mg',
    ['label'] = 'Percocet 15MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'percocet_15mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Medium Percocet pill to reduce pain and discomfort'
},

['percocet_5mg'] = {
    ['name'] = 'percocet_5mg',
    ['label'] = 'Percocet 5MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'percocet_5mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Low dose of Percocet used for mild pain relief'
},

['vicodin_10mg'] = {
    ['name'] = 'vicodin_10mg',
    ['label'] = 'Vicodin 10MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'vicodin_10mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Vicodin tablet used for moderate pain treatment'
},

['vicodin_5mg'] = {
    ['name'] = 'vicodin_5mg',
    ['label'] = 'Vicodin 5MG',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'vicodin_5mg.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Small Vicodin dose for light pain relief'
},

['sedative'] = {
    ['name'] = 'sedative',
    ['label'] = 'Sedative',
    ['weight'] = 5,
    ['type'] = 'item',
    ['image'] = 'sedative.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'A sedative dose used to calm patients or prepare for procedures'
},

['medikit'] = {
    ['name'] = 'medikit',
    ['label'] = 'Medical Kit',
    ['weight'] = 800,
    ['type'] = 'item',
    ['image'] = 'medikit.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'A full medical kit containing basic supplies for emergency care'
},

['medbag'] = {
    ['name'] = 'medbag',
    ['label'] = 'Medical Bag',
    ['weight'] = 1200,
    ['type'] = 'item',
    ['image'] = 'medbag.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Portable bag filled with essential medical tools and medicines'
},

['tweezers'] = {
    ['name'] = 'tweezers',
    ['label'] = 'Tweezers',
    ['weight'] = 100,
    ['type'] = 'item',
    ['image'] = 'tweezers.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Small precision tool used for removing debris or bullets from wounds'
},

['suturekit'] = {
    ['name'] = 'suturekit',
    ['label'] = 'Suture Kit',
    ['weight'] = 300,
    ['type'] = 'item',
    ['image'] = 'suturekit.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Kit used for stitching and closing open wounds'
},

['icepack'] = {
    ['name'] = 'icepack',
    ['label'] = 'Ice Pack',
    ['weight'] = 200,
    ['type'] = 'item',
    ['image'] = 'icepack.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Cold pack used to reduce swelling and pain from injuries'
},

['burncream'] = {
    ['name'] = 'burncream',
    ['label'] = 'Burn Cream',
    ['weight'] = 150,
    ['type'] = 'item',
    ['image'] = 'burncream.png',
    ['unique'] = false,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'Special cream to treat burns and protect the skin'
},

['defib'] = {
    ['name'] = 'defib',
    ['label'] = 'Defibrillator',
    ['weight'] = 2500,
    ['type'] = 'item',
    ['image'] = 'defib.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'A defibrillator used to revive unconscious patients'
},

['stretcher'] = {
    ['name'] = 'stretcher',
    ['label'] = 'Stretcher',
    ['weight'] = 1500,
    ['type'] = 'item',
    ['image'] = 'stretcher.png',
    ['unique'] = true,
    ['useable'] = true,
    ['shouldClose'] = true,
    ['combinable'] = nil,
    ['description'] = 'A medical stretcher to transport injured patients safely'
},

```
