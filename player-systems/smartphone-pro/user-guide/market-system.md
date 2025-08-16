# Market system

The **Market App** in **Smartphone PRO** is designed to provide a comprehensive system for connecting players with in-game businesses and services. Unlike the simpler version in the standard smartphone, the PRO version adds duty systems, chat, calls, and more, creating a more immersive experience.

{% stepper %}
{% step %}
Players can contact businesses, place orders, and get directions to store locations.
{% endstep %}

{% step %}
Workers in the listed jobs can handle orders and communicate with customers.
{% endstep %}

{% step %}
Each market has a unique configuration, including name, description, image, and coordinates.
{% endstep %}
{% endstepper %}

***

## Adding New Markets

The Market App enhances gameplay by bridging the gap between customers and businesses, offering a dynamic way to interact within the server. Proper management of IDs and configurations ensures a seamless experience.

### Important Notes:

{% stepper %}
{% step %}
### **Do Not Delete Randomly**

Market IDs are stored in players' phones. If you delete or modify a market, use the command `/deletemarket id` to prevent data conflicts.
{% endstep %}

{% step %}
### Configuration

All markets are defined in **config.lua**, where you can add new markets, customize descriptions, and assign jobs. If you edit a market ID, ensure you reset it using the aforementioned command.
{% endstep %}
{% endstepper %}

Here’s how you can define a market in **config.lua**:

```lua
Config.Markets = {
    {
        id = 1,
        name = 'Los Santos Police Department',
        image = 'https://static.wikia.nocookie.net/gtawiki/images/d/dc/MissionRowPoliceStation-GTAV.png',
        description = 'The city police, always willing to help you, let us know if you have any problems in Los Santos.',
        job = { 'police', 'sheriff' },
        coords = vec3(452.12, -980.55, 30.69)
    },
    {
        id = 2,
        name = 'Pillbox Medical Center',
        image = 'https://ultimate-mods.com/uploads/monthly_2021_03/FPe7Cra.png.3cc6fa9b2a3ac79ecffbcc4605c31935.png',
        description = 'If you need a doctor, contact the Los Santos Emergency Center!',
        job = { 'ambulance' },
        coords = vec3(335.12, -584.55, 43.69)
    }
    -- Add or edit markets as needed
}

```
