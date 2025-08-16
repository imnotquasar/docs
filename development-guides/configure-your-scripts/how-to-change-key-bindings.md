# How to change key bindings

## **Register Key Mapping**

{% hint style="info" %}
The new keybinds will apply only to new players or those who reset their keybinds manually.
{% endhint %}

To properly organize your keybinds and optimize your resource, we’ve adopted the FiveM native RegisterKeyMapping. This eliminates the need for constant checks (while loops) for key presses, significantly improving performance. This native works by triggering the associated chat command whenever the keybind is pressed.

{% stepper %}
{% step %}
### **Optimized performance**

Reduces resource usage by removing frame-by-frame checks.
{% endstep %}

{% step %}
### **Client customization**

Players can now change their own keybinds directly in-game.
{% endstep %}
{% endstepper %}

***

## How to Change Keys **In-Game**

This allows players to customize controls for specific FiveM actions directly in-game.

{% stepper %}
{% step %}
### Open the Settings Menu

Navigate to the **Settings** menu in GTA V.
{% endstep %}

{% step %}
### Go to Key Bindings

Under **Settings**, find and select the **Key Bindings** section.
{% endstep %}

{% step %}
### Select FiveM Key Bindings

Scroll to the **FiveM** section where all FiveM-related keybinds are listed.
{% endstep %}

{% step %}
### Adjust Key Bindings

Modify the keybinds as needed to suit your preferences.
{% endstep %}
{% endstepper %}

***

## How to Reset Keybinds

If you need to reset your keybinds, there are two options:

{% stepper %}
{% step %}
### Using Console

Open the F8 console and type this, example: unbind keyboard f10.

```lua
unbind keyboard [key]
```
{% endstep %}

{% step %}
### Editing Configuration File

* Go to C:\Users\\\[USERNAME]\AppData\Roaming\CitizenFX.
* Open fivem.cfg.
* Remove the lines related to the resource.
* Restart FiveM.
{% endstep %}
{% endstepper %}
