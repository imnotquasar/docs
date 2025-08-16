# Installation

## Script Download

Before starting, you must log in to the CFX portal to download the asset. You will be able to download it as many times as you want on the official CFX page. Just as you download it the first time, you will also download it multiple times in the future to get updates.

{% stepper %}
{% step %}
### Logging in to the CFX Portal

First, log in to the official CFX portal by [clicking here](https://portal.cfx.re/assets/granted-assets).
{% endstep %}

{% step %}
### Finding Your Assets

Once logged in, navigate to the **Granted Assets** section to access your purchased assets. You can download them by clicking the **"Download"** button.
{% endstep %}
{% endstepper %}

Remember, if you encounter any issues or errors when starting the asset, you can check here to see if the problem is related.

{% content-ref url="../../getting-started/what-is-cfx-auth.md" %}
[what-is-cfx-auth.md](../../getting-started/what-is-cfx-auth.md)
{% endcontent-ref %}

<div data-full-width="false"><figure><img src="../../.gitbook/assets/ezgif-5-f03822751d.gif" alt=""><figcaption></figcaption></figure></div>

***

## Downloading Dependencies

The dependencies for this asset are mandatory, so please follow the dependency guide completely and use all required files.

When downloading a dependency, ensure the file is properly unzipped and does not include **"-main"** at the end of its name. If it does, please remove it.

{% stepper %}
{% step %}
### ox\_lib

{% embed url="https://github.com/overextended/ox_lib/releases" %}
{% endstep %}

{% step %}
### cfx-natives (baseevents)

{% embed url="https://github.com/citizenfx/cfx-server-data" %}
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/ezgif-5-ee6f842765 (1).gif" alt=""><figcaption></figcaption></figure>

***

## Update artifacts and gamebuild

Updating to the latest **artifacts** and **gamebuild** is essential to avoid common server issues. Here's how to do it properly:

{% stepper %}
{% step %}
### Update Artifacts

> To find the best FiveM artifact, visit [artifacts.jgscripts.com](https://artifacts.jgscripts.com). Thanks to JG Scripts.

Completely replace your current artifacts with the latest version. Download the appropriate artifacts for your operating system from the official links:

* **Windows**: [Windows Artifacts](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/).
* **Linux**: [Linux Artifacts](https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/).
{% endstep %}

{% step %}
### Update Gamebuild

Using gamebuild 3095 is recommended as it is the most stable version, ensuring optimal performance and avoiding compatibility issues.

Edit the `server.cfg` file and add the following line:

```plaintext
sv_enforceGameBuild 3095
```
{% endstep %}
{% endstepper %}

You can see the complete guide to update your server here:

{% content-ref url="../../development-guides/before-you-start/how-to-update-my-server.md" %}
[how-to-update-my-server.md](../../development-guides/before-you-start/how-to-update-my-server.md)
{% endcontent-ref %}

<figure><img src="../../.gitbook/assets/ezgif-2-2221374386.gif" alt=""><figcaption></figcaption></figure>

***

## Server.cfg Positioning

This asset must always be started below your framework and inventory but above any vehicle-related scripts. Failure to follow this order may result in functionality issues or critical errors. To ensure smooth operation and proper initialization, it is highly recommended to start the entire download folder using "ensure \[vehiclekeys]" in your server.cfg while maintaining the correct order.

<figure><img src="../../.gitbook/assets/ezgif-7-18d691812a.gif" alt=""><figcaption></figcaption></figure>

***

## Debugging and Helper Tips

Debugging is an essential part of creating and modifying scripts, especially when working with vehicle-related assets. Using tools like `print()` statements, you can inspect the values of variables, test logic, and identify errors in your code. Below are some practical tips and examples to help you debug and improve your scripts.

{% stepper %}
{% step %}
### Using print Statements for Debug

You can use print() statements to display the values of variables in the console. This is particularly useful when you’re unsure of the data being returned or when you need to verify the behavior of your code. Here are two examples:

```lua
-- Printing multiple values separated by commas
print(vehicleData.model, vehicleData.name, vehicleData.other)

-- Including descriptive labels for clarity
print('Model: ', vehicleData.model, 'Name: ', vehicleData.name)
```

This approach helps identify whether specific variables are returning the expected values.
{% endstep %}

{% step %}
### Example Debugging Scenario in a Callback

In complex scripts, such as when purchasing a vehicle, you might want to validate the data being processed. Using print() statements inside callbacks can reveal any unexpected issues.

```lua
ESX.TriggerServerCallback('esx_vehicleshop:buyVehicle', function(success)
    if success then
        IsInShopMenu = false
        menu2.close()
        menu.close()
        DeleteDisplayVehicleInsideShop()
        FreezeEntityPosition(playerPed, false)
        SetEntityVisible(playerPed, true)

        -- Debugging vehicle data
        print('Model: ', vehicleData.model, 'Name: ', vehicleData.name, 'Other: ', vehicleData.other)
    else
        ESX.ShowNotification(TranslateCap('not_enough_money'))
    end
end, vehicleData.model, generatedPlate)
```

By adding debugging prints, you can determine if the vehicle data (e.g., vehicleData.model, generatedPlate) is correct before proceeding with the rest of the logic.
{% endstep %}

{% step %}
### Retrieve Vehicle Model and Plate

If you need to get the model name or plate of a vehicle, you can use the following native functions. These are simple yet powerful tools for obtaining vehicle information directly:

```lua
local model = GetDisplayNameFromVehicleModel(GetEntityModel(veh)) -- Returns the vehicle model name
local plate = GetVehicleNumberPlateText(veh) -- Returns the vehicle's license plate
```

These functions can be integrated into your scripts to quickly fetch the necessary details about a vehicle.
{% endstep %}

{% step %}
### Best Practices for Debugging

1. **Place `print()` Strategically:** Add print() statements before and after key operations to understand the flow of your code.
2.  **Label Debug Outputs:** Use descriptive text in print() to make debugging outputs easier to read.

    ```lua
    print('Current Vehicle Model:', model)
    print('Current Vehicle Plate:', plate)
    ```
3. **Test Incrementally:** Test small portions of your script to isolate errors and verify logic step by step.

By following these practices, you’ll streamline your debugging process and ensure that your vehicle scripts operate as intended. Debugging effectively not only saves time but also enhances the reliability and performance of your code.
{% endstep %}
{% endstepper %}

***

## Integrating Key Management with Third-Party Assets

Vehicle Keys provides an export system to grant or revoke keys for vehicles in external assets. This guide demonstrates how to integrate the GiveKeys export with a third-party asset, such as esx\_vehicleshop, to seamlessly handle vehicle key assignments.

{% stepper %}
{% step %}
### **Export Overview**

The `GiveKeys` export assigns keys to a specified vehicle. It accepts the following parameters:

```lua
exports['qs-vehiclekeys']:GiveKeys(plate, model, true)
```

* **plate**: The vehicle's license plate.
* **model**: The vehicle's model name.
* **bypassKeyCheck**: _(optional, default `false`)_ If set to `true`, the export bypasses the key validation check.
{% endstep %}

{% step %}
### **Implementation Example**

Below is an example of integrating the GiveKeys export within esx\_vehicleshop. This code ensures that once a vehicle is purchased, keys are automatically assigned to the buyer:

```lua
ESX.TriggerServerCallback('esx_vehicleshop:buyVehicle', function(success)
    if success then
        IsInShopMenu = false
        menu2.close()
        menu.close()
        DeleteDisplayVehicleInsideShop()
        FreezeEntityPosition(playerPed, false)
        SetEntityVisible(playerPed, true)

        -- Retrieve the vehicle's model and plate using natives
        local model = GetDisplayNameFromVehicleModel(GetEntityModel(vehicleData))
        local plate = GetVehicleNumberPlateText(vehicleData)

        -- Grant keys to the buyer
        exports['qs-vehiclekeys']:GiveKeys(plate, model, true)
        
    else
        ESX.ShowNotification(TranslateCap('not_enough_money'))
    end
end, vehicleData.model, generatedPlate)
```
{% endstep %}

{% step %}
### **Key Points for Integration**

1. **Dynamic Plate and Model Retrieval**:
   * Use natives like `GetDisplayNameFromVehicleModel` and `GetVehicleNumberPlateText` to dynamically fetch the vehicle's model and plate.
2. **Export Usage**:
   * Call `GiveKeys` with the retrieved `plate` and `model` values, and set `bypassKeyCheck` as `true` if necessary.
3. **Custom Implementation**:
   * While this example uses `esx_vehicleshop`, the logic can be adapted for any third-party asset where key assignment is needed.

By integrating the `GiveKeys` export in your scripts, you can enhance the gameplay experience by automatically assigning keys upon vehicle purchase or spawn.
{% endstep %}
{% endstepper %}

Learn more about exports by viewing the following link:

{% content-ref url="exports-and-commands/" %}
[exports-and-commands](exports-and-commands/)
{% endcontent-ref %}

***

## Key bind manipulation

All Quasar Store assets use the same process for modifying Key Binds to ensure consistency and optimized performance across all resources.&#x20;

Below is a clear and detailed guide on how to adjust them to your preferences.

{% content-ref url="../../development-guides/configure-your-scripts/how-to-change-key-bindings.md" %}
[how-to-change-key-bindings.md](../../development-guides/configure-your-scripts/how-to-change-key-bindings.md)
{% endcontent-ref %}
