# Starter Items

{% hint style="info" %}
Remember that if there are problems or incompatibilities with your inventory, you will need to disable this configuration, since the plan is not to have it as a mandatory but optional feature.
{% endhint %}

This system includes a configuration for starter items, which will allow several different items to be added to the player's spawn. Read the following comments if you have questions.

This setting is completely basic, but if you want to remove it you can simply change it to the following `Config.StarterItems = {}` or comment inside. Below we will leave the default configuration to better understand your configuration.

```lua
Config.StarterItems = {
    { item = 'phone', amount = 1 },
}
```
