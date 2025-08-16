# Clothing Price Customization

You can assign specific prices to each clothing item based on its category and variation using the configuration in `config/prices.lua`. This gives you full control over the cost of props (like hats and glasses) and components (like shirts or pants) directly in-game.

***

## How to Modify Prices <a href="#basic-item-declaration" id="basic-item-declaration"></a>

Here’s an example of how the pricing system is structured:

```lua
Config.Prices = {
    props = {
        [0] = { -- hats
            [1] = 1250,
            [2] = 2500,
            [3] = 3750,
            [4] = 5000,
            [5] = 6250,
            [6] = 7500,
            [7] = 8750,
            [8] = 10000
        }
    },
    components = {
        [11] = { -- tops
            [1] = 1000,
            [2] = 2000,
            [3] = 3000,
            [4] = 4000,
            [5] = 5000,
            [6] = 6000,
            [7] = 7000,
            [8] = 8000
        }
    }
}
```

In this configuration you can see:

* `props` handles accessories like hats, glasses, watches, etc.
  * `[0]` corresponds to **hats**.
  * The inner indices (`[1]`, `[2]`, etc.) represent **drawable variations**, each with its own defined price.

{% embed url="https://docs.fivem.net/natives/?_0x829F2E2" %}

* `components` handles clothing items like shirts, pants, shoes, etc.
  * `[11]` corresponds to **tops**.
  * Each variation has a separate cost based on its index.

{% embed url="https://docs.fivem.net/natives/?_0xD4F7B05C" %}
