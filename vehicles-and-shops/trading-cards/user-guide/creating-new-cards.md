# Creating New Cards

Quasar Trading Cards allows you to create custom collectible cards with metadata like rarity, stats, and visual details. Follow this guide to add your own cards.

{% stepper %}
{% step %}
### **Do not edit rarity levels**

Modifying the rarity (`basic`, `rare`, `legendary`) may break the system.
{% endstep %}

{% step %}
### **Metadata requirement**

Card items without metadata (e.g., manually added to inventory) will not function. Cards must be obtained through the `tradingcard_booster_pack` for metadata to apply.
{% endstep %}

{% step %}
### **Image hosting**

Avoid hosting card images on Discord, as it is not compatible with FiveM. Use a reliable image-hosting service instead.
{% endstep %}
{% endstepper %}

***

## How to Create Cards

All card configurations are located in the `config.lua` file under the `Config.Cards` table. Each card has detailed properties, allowing you to customize its appearance and attributes.

***

## Example Card Configuration

Here’s an example of how to add a new card:

```lua
Config.Cards = {
    [1] = { -- Unique order number for the card
        color = 'rare', -- Rarity level: basic, rare, legendary
        rank = 'rare', -- Rank corresponding to rarity
        label = 'Corrado Cattani', -- Card title or name
        images = 'https://i.ibb.co/HVL3nYP/2021-05-02-30.webp', -- URL to the card image
        term = 'Corrado Cattani, son of a smuggler, candidate for general after a pandemic. Defender of his city against walkers.', -- Card backstory or tagline
        -- description = 'A secondary description?', -- Optional additional description
        health = 200, -- Health value of the character
        attack = 99, -- Attack power of the character
        height = '168', -- Character's height (cm)
        weight = '80', -- Character's weight (kg)
        quality = 100, -- Quality rating of the card (e.g., out of 100)
    },
    -- Add more cards following the same structure
}
```

***

## Key Attributes

* **`color`**: Defines card rarity (`basic`, `rare`, `legendary`).
* **`rank`**: Must match the rarity for consistency.
* **`label`**: The card's title or name.
* **`images`**: URL to the card's image; ensure compatibility with FiveM.
* **`term`**: A short backstory or tagline for the card.
* **`description`** (optional): Placeholder for an additional description.
* **`health`**: Character's health points.
* **`attack`**: Character's attack power.
* **`height` and `weight`**: Character's physical attributes.
* **`quality`**: The card's overall quality rating.

***

## Tips for Adding Cards

{% stepper %}
{% step %}
### **Unique Order Number**

Ensure each card has a unique index number (`[1]`, `[2]`, etc.).
{% endstep %}

{% step %}
### **Matching Rarity and Rank**

The `color` and `rank` values must correspond (`basic` for `basic`, `rare` for `rare`, etc.).
{% endstep %}

{% step %}
### **Optimize Images**

Use web-optimized image formats (e.g., `.webp`) to ensure fast loading and compatibility.
{% endstep %}
{% endstepper %}

By following this structure, you can expand your Quasar Trading Cards system with custom and engaging cards tailored to your server’s needs.
