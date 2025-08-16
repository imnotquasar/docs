# Default Exports

The **Quasar Dispatch** asset provides a variety of exports to trigger predefined dispatch calls for specific scenarios. These exports allow you to integrate key events into your server, enhancing roleplay and emergency response dynamics. Below is a comprehensive list of default exports included in the asset:

**Commonly Used Exports:**

* **VehicleShooting**: Trigger a dispatch for shooting from a vehicle.
* **Shooting**: Notify law enforcement of a reported shooting.
* **OfficerDown**: Alert for an officer in distress or injured.

**Robbery-Related Exports:**

* **StoreRobbery**: Trigger dispatch for store robberies.
* **FleecaBankRobbery**, **PaletoBankRobbery**, **PacificBankRobbery**: Specific bank robbery dispatches.
* **VangelicoRobbery**: Dispatch for jewelry store robberies.
* **HouseRobbery**: Notify law enforcement of residential burglaries.
* **ArtGalleryRobbery**, **HumaneRobbery**, **TrainRobbery**, **VanRobbery**, **UndergroundRobbery**, **DrugBoatRobbery**, **UnionRobbery**, **YachtHeist**: Specialized heist and robbery alerts.

**Crime & Suspicious Activity:**

* **DrugSale**: Dispatch for illegal drug sales.
* **SuspiciousActivity**: Report of unusual or potentially illegal actions.
* **CarJacking**, **VehicleTheft**, **CarBoosting**: Vehicle-related crimes.
* **IllegalRacing**: Notify of street racing activity.
* **Kidnapping**: Dispatch for reported abductions.

**Miscellaneous Exports:**

* **PrisonBreak**: Alert for a prison escape.
* **IllegalFishing**: Notify law enforcement of unlawful fishing activities.
* **ArmsDeal**: Dispatch for illegal weapons trading.
* **CyberAttack**: Alerts for a reported cybercrime or hack.

***

## How to Use

To trigger any of these events, use the export in your code like this:

```lua
exports['qs-dispatch']:Shooting()
```

Replace Shooting() with the desired export to trigger a specific event. These exports allow seamless integration of dynamic scenarios into your server for better roleplay and gameplay experiences.
