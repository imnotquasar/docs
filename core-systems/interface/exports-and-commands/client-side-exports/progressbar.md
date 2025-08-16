# ProgressBar

The `ProgressBar` export from **qs-interface** provides an easy way to display a progress bar during in-game actions, such as crafting, loading, or any other time-consuming tasks. It gives players visual feedback on the progress of an action and can be customized to fit your needs.

In this tutorial, we will explain how to use the `ProgressBar` export, with an example of integrating it into a custom command.

***

## **How to Use**

To use the `ProgressBar` export, follow these simple steps:

```lua
local success = exports['qs-interface']:ProgressBar({
    duration = duration,         -- Duration of the progress bar (in milliseconds)
    label = label,               -- Text that will appear on the progress bar
    position = 'bottom',         -- Position of the progress bar on the screen (e.g., 'top', 'bottom', 'center')
    useWhileDead = useWhileDead, -- Whether the progress bar shows when the player is dead (true/false)
    canCancel = canCancel,       -- Whether the player can cancel the progress (true/false)
    disable = disableControls,   -- Whether to disable player controls during the progress (true/false)
    anim = {                     -- Animation to be played while the progress is happening
        dict = animation.animDict,
        clip = animation.anim,
        flag = animation?.flags   -- Optional animation flags
    },
    prop = prop                  -- Optional prop to show alongside the progress bar (can be nil)
})
```

Here are the key parameters:

* **`duration`**: The time the progress bar will be shown (in milliseconds).
* **`label`**: The message displayed on the progress bar.
* **`position`**: The position of the progress bar on the screen (options like 'top', 'bottom', or 'center').
* **`useWhileDead`**: If set to `true`, the progress bar will be visible even when the player is dead.
* **`canCancel`**: If set to `true`, the player can cancel the progress bar.
* **`disable`**: If set to `true`, disables player controls (like walking, jumping, etc.) while the progress is active.
* **`anim`**: An optional animation to play during the progress. You need to specify the animation dictionary (`dict`), clip (`clip`), and optionally flags (`flag`).
* **`prop`**: You can specify a prop (like a tool or object) to show with the progress bar, though this is optional.

***

### Example: Using ProgressBar in a Command

Let’s integrate the `ProgressBar` export into a simple command. For this example, we’ll use a 5-second progress bar to simulate crafting.

```lua
RegisterCommand('startAction', function()
    local success = exports['qs-interface']:ProgressBar({
        duration = 5000,
        label = "Crafting...",
        position = 'bottom',
        canCancel = true
    })

    if success then
        print("Action completed!")
    else
        print("Action canceled!")
    end
end, false)
```

### **Explanation**

{% stepper %}
{% step %}
**Command**

This example registers the command `/startCrafting` that can be executed by the player in the game.
{% endstep %}

{% step %}
**Progress Bar**

* The `duration` is set to 5000 milliseconds (5 seconds).
* The `label` is set to "Crafting your item..." which will be shown on the progress bar.
* The `position` is set to `'bottom'`, which places the progress bar at the bottom of the screen.
* `canCancel` is set to `true`, allowing the player to cancel the action.
{% endstep %}

{% step %}
**Completion**

* If the progress completes, the message "Crafting completed!" is printed.
* If the player cancels the action, the message "Crafting was canceled!" is printed.
{% endstep %}
{% endstepper %}
