# Drug Sales System

Quasar Gangs & Territories includes an advanced drug sales system that integrates with gang territories. Players can engage in two types of drug sales: **dealer missions** and **street sales** within conquered territories. Each system offers unique gameplay opportunities and challenges.

***

## Territory Dealer System

Within each territory, a **dealer** provides missions to deliver drug packages. Completing these missions on time builds **reputation**, unlocking new purchasable items from the dealer. Each dealer's reputation system is independent, allowing players to develop unique relationships with each one. Dealers can be configured in the `Config.Territories` file under their respective territories.

```lua
dealers = { 
    ['zone-1'] = {
        name = 'Abel Pintos',
        coords = vector3(267.665955, -1979.446167, 21.461548),
        time = { min = 01, max = 12 },
        products = Config.Products
    }
}
```

Alternatively, you can create dealers in-game using the command `/createdealer name open close`, specifying the dealer's name, opening time, and closing time for added flexibility.

***

## Street Drug Sales

Street sales are exclusive to the dominant gang within a territory. Gang members can sell drugs to NPCs in the area, simulating neighborhood-level dealing. NPCs may tip, haggle, or even attempt to rob the player, adding dynamic challenges. The sales system can be initiated with the `/selldrugs` command or through the Gang menu.

{% stepper %}
{% step %}
### Drug sales are limited to your gang’s territory.
{% endstep %}

{% step %}
### Prices and interactions can be configured for balanced gameplay.
{% endstep %}
{% endstepper %}

This dual-layered sales system adds depth to gang dynamics, encouraging players to conquer and maintain territories while managing relationships with dealers.
