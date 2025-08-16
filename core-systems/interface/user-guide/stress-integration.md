# Stress Integration

**Quasar Interface** includes an advanced stress system that works automatically with both **QBCore** and **ESX** frameworks. No additional configuration is required, ensuring a seamless experience.

***

## Automatic Integration

The stress system is fully automated and does not require manual triggers or configurations when used with **QBCore** or **ESX**. Players will naturally gain stress based on in-game events.

***

## Custom Stress Events

If you wish to add stress manually from other scripts, you can easily do so using the following example:

```lua
TriggerServerEvent('interface:updateStress', math.random(1, 3))
```

This command allows you to increase a player's stress by a random value between **1** and **3**, which you can customize as needed. With this flexible system, you can enhance the realism of your server while maintaining full control over custom stress triggers.

<figure><img src="../../../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>
