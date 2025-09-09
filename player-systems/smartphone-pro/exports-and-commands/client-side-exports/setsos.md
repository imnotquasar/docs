# setSOS

The **setSOS** export allows you to enable or disable the SOS emergency mode of the phone. This is useful for managing situations where you want to control whether players can send emergency calls, such as during events, minigames, or restricted areas.

***

## How to Use

To change the SOS status, you can use the following code:

```lua
exports['qs-smartphone-pro']:setSOS(bool) -- true or false
```

This example disables the SOS system while the player is in a deathmatch.

***

#### Example with integration

<pre class="language-lua"><code class="lang-lua"><strong>-- In deathmatch event
</strong><strong>TriggerEvent('deathmatch:inDeathmatch', true)
</strong>if GetResourceState('qs-smartphone-pro'):find('started') then
    exports['qs-smartphone-pro']:setSOS(false)
end
</code></pre>

In this case:

* The deathmatch event is triggered.
* If the **qs-smartphone-pro** resource is running, the SOS feature is disabled.
* Finally, a server event is triggered to set the player requirements.
