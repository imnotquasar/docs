# Factions and Sales

The **Quasar Drugs** system integrates laboratories, farming, and a dynamic drug-selling mechanism, configurable for specific factions or open sales. Using the file config/seller.lua, you can customize sales options, faction exclusivity, and NPC interactions to fit your server's needs.

***

## Faction-Exclusive Sales

The system supports restricting sales to specific factions or jobs by enabling the appropriate configuration:

```lua
Config.SellOnlyJob = false -- Enable this to restrict sales to specific jobs
Config.SellJobs = { 
    ['ballas'] = true, -- Add jobs or factions allowed to sell
}
```

If enabled, only the jobs or factions listed under Config.SellJobs will be able to interact with sellers.

***

## Configuring Drugs for Sale

Drugs can be configured with wholesale and retail prices, providing flexibility in how items are sold:

```lua
Config.Drugs = {
    Weed = {
        ItemName = 'weed_packaged',
        ItemWholesalePrice = 35, -- Price for bulk sales
        ItemSinglyPrice = 80, -- Price for individual sales
    },
    Meth = {
        ItemName = 'meth_packaged',
        ItemWholesalePrice = 45,
        ItemSinglyPrice = 90,
    },
    Coke = {
        ItemName = 'cocaine_packaged',
        ItemWholesalePrice = 85,
        ItemSinglyPrice = 170,
    },
}
```

***

## Retail Drug Sales

Retail sales allow interaction with NPCs who buy drugs individually. This process involves:

{% stepper %}
{% step %}
### Mission-Based Interaction

Players are assigned a location where an NPC awaits.
{% endstep %}

{% step %}
### Randomized Outcomes

The NPC may pay the price, provide a tip, or attempt to rob the player.
{% endstep %}

{% step %}
### Configuration

All retail settings can be edited in config/seller.lua.
{% endstep %}
{% endstepper %}

***

## Wholesale Drug Sales

For bulk sales, players can:

{% stepper %}
{% step %}
### Rent a Vehicle

The system spawns a vehicle behind the player, ready for deliveries.
{% endstep %}

{% step %}
### **Deliver to Wholesaler**

Marked locations on the map guide players to sell large bags of drugs.
{% endstep %}

{% step %}
### **Customization**

Wholesale settings are also managed in config/seller.lua.
{% endstep %}
{% endstepper %}

***

## Dealer NPC Menu

Players interact with a **Dealer NPC**, which provides options for:

{% stepper %}
{% step %}
### Retail Sales

Individual drug sales with varied outcomes.
{% endstep %}

{% step %}
### Wholesale Sales

Bulk drug deliveries for larger profits.
{% endstep %}
{% endstepper %}

This system ensures a rich, faction-oriented roleplay experience, allowing server administrators to tweak every detail, from faction restrictions to pricing and outcomes.
