# ox\_inventory

The images for these items can always be found in a folder named **\[images]** within the previously downloaded package. Make sure to use these images to ensure consistency and a seamless experience for players on your server.

```lua
["vehiclekeys"] = {
	label = "Keys",
	weight = 1,
	stack = false,
	close = false,
	consume = 0,
	client = {
		export = 'qs-vehiclekeys.useKey',
	},
},

['plate'] = {
	label = 'Plate',
	weight = 100,
	stack = true,
	close = false,
	consume = 0,
	client = {
		export = 'qs-vehiclekeys.usePlate',
	},
},

['carlockpick'] = {
	label = 'Car Lockpick',
	weight = 100,
	stack = true,
	close = false,
	description = "Plate for vehicle",
	client = {
		export = 'qs-vehiclekeys.useCarlockpick',
	},
},

['caradvancedlockpick'] = {
	label = 'Advanced Lockpick',
	weight = 100,
	stack = true,
	close = false,
	description = "Plate for vehicle",
	client = {
		export = 'qs-vehiclekeys.useAdvancedCarlockpick',
	},
},

['vehiclegps'] = {
    label = 'Vehicle GPS',
    weight = 100,
    stack = true,
    close = false,
    description = "GPS device for what...?",
    client = {
        export = 'qs-vehiclekeys.useVehiclegps',
    },
},

['vehicletracker'] = {
    label = 'Vehicle Tracker',
    weight = 100,
    stack = true,
    close = false,
    description = "It seems to stream probes",
    client = {
        export = 'qs-vehiclekeys.useVehicletracker',
    },
},
```
