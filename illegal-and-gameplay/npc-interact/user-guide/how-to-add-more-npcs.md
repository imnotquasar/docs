# How to Add More NPCs

In **Quasar Interact**, you can easily add NPCs by editing the `Config.Peds` table. Each NPC has properties such as model, position, animations, and a list of interactions.

***

## Basic Example of an NPC

Each NPC is defined inside `{}` and added to the `Config.Peds` table:

```lua
{
    npc = 'a_m_m_business_01', -- NPC model
    coords = vector3(200.32, -900.58, 30.69), -- NPC position
    heading = 90.0, -- NPC facing direction
    name = 'Michael', -- Display name
    animName = 'mini@strip_club@idles@bouncer@base', -- Animation dictionary
    animDist = 'base', -- Animation name
    intro = 'Hello, I am Michael. How can I help you?', -- First message

    interactions = {
        {
            label = 'Tell me a joke',
            onPress = function(menu)
                menu.addMessage('Why don’t skeletons fight each other? They don’t have the guts!', 'npc')
            end,
        },
        {
            label = 'Give me a tip',
            onPress = function(menu)
                menu.addMessage('Stay away from trouble, it never ends well.', 'npc')
            end,
        },
        {
            label = 'Goodbye',
            onPress = function(menu)
                menu.addMessage('Take care!', 'npc')
                Wait(1000)
                menu.close()
            end,
        }
    }
}

```

***

## Adding More NPCs

To add more NPCs, simply copy the existing structure and modify the properties:

```lua
{
    npc = 's_m_y_cop_01',
    coords = vector3(450.25, -980.12, 30.69),
    heading = 180.0,
    name = 'Officer Davis',
    animName = 'amb@world_human_cop_idles@male@idle_a',
    animDist = 'idle_a',
    intro = 'Hello, I am Officer Davis. Need any help?',
    
    interactions = {
        {
            label = 'Ask for directions',
            onPress = function(menu)
                menu.addMessage('You should check your map for the best route.', 'npc')
            end,
        },
        {
            label = 'Report a crime',
            onPress = function(menu)
                menu.addMessage('I will log your report. Stay safe.', 'npc')
            end,
        },
    }
}

```
