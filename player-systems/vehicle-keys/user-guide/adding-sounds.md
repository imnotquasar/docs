# Adding Sounds

In `qs-vehiclekeys`, you can configure custom sounds for key-related interactions to enhance immersion. This requires using a sound management resource such as [interact-sound](https://github.com/plunkettscott/interact-sound). Follow the steps below to set up and customize sounds for your server.

***

## **Install and Add Custom Sound**

{% stepper %}
{% step %}
### **Download and Install interact-sound**

* Install the resource from the provided GitHub link and ensure it is properly set up in your server.
{% endstep %}

{% step %}
### **Add the Sound File**

*   Place your custom sound file (e.g., `carkeys.ogg`) in the following directory:

    ```bash
    interact-sound/client/html/sounds/carkeys.ogg
    ```
{% endstep %}

{% step %}
### **Update fxmanifest.lua**

*   Add your sound file to the files section of fxmanifest.lua for the interact-sound resource:

    ```lua
    files {
        'client/html/index.html',
        'client/html/sounds/demo.ogg',
        'client/html/sounds/carkeys.ogg',
    }
    ```
{% endstep %}
{% endstepper %}

***

## **Configure Custom Sounds**

Once the sound is added, update the following configuration values in qs-vehiclekeys:

```lua
Config.Sounds = true -- Enable custom sounds through InteractSound
Config.SoundsDisableDefault = false -- Disable default FiveM sounds
Config.SoundsVolume = 0.3 -- Adjust volume (recommended range: 0.1 to 1.0)
Config.SoundsFileName = 'carkeys' -- Name of the custom sound file
Config.SoundsDistance = 2 -- Set the sound range in-game (in meters)
```
