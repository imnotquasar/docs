# Telephone booth system

Quasar Smartphone includes a free, integrated phone booth system that allows you to call workers on duty or a custom number.

***

## **Modification of phone booths**

This system is very simple to use. Place the booth props in your world, and everything will execute automatically without requiring complex configurations. You can add more props by finding GTA V props from an external resource and adding their hashes to the configuration file.

```lua
Config.EnableBooth = true -- Do you want to enable the phone booths?

-- Configure here the props that will be phone booths.
Config.Booth = {
    [1158960338] = true, -- Hash of booths
    [1511539537] = true,
    [1281992692] = true,
    [-429560270] = true,
    [-1559354806] = true,
    [-78626473] = true,
    [295857659] = true,
    [-2103798695] = true,
    -- You can add more!
}
```
