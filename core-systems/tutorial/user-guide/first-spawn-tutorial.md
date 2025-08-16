# First Spawn Tutorial

{% hint style="success" %}
On the first spawn, the tutorial will appear automatically if you are using **qs-multicharacter** (latest version).
{% endhint %}

If you want to trigger the tutorial manually, you can use this event in any client-side script:

```lua
exports['qs-tutorial']:StartTutorial()
```

The tutorial will only appear **once** thanks to `localStorage`. If you need to reset it, there are commands available in the configuration.
