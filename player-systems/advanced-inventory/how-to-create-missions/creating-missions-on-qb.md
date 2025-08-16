# Creating Missions on QB

{% hint style="danger" %}
f you don't have the skills to develop basic code, we recommend that you contact a trusted developer.
{% endhint %}

The quest system in `qs-inventory`lets you create small missions for your players, such as buying items, using objects, visiting places, or interacting with systems. You can reward XP. Here’s how it works, step-by-step. These events and exports are ONLY for server-side.

***

{% stepper %}
{% step %}
## Assign Quests When the Player Joins <a href="#how-to-use-in-qbcore" id="how-to-use-in-qbcore"></a>

{% hint style="success" %}
You must **wait a few seconds** before giving quests to make sure the character is fully loaded. This avoids problems where the player doesn’t receive the quests due to timing.
{% endhint %}

You want every player to **receive their quests** as soon as they connect to your server and their character is fully loaded. Example (inside `server/main.lua`):

```lua
RegisterNetEvent('QBCore:Server:OnPlayerLoaded', function()
    local src = source
    print('Loaded player:', src)
    CreateQuests(src)
end)
```

In this configuration we will place whether or not we want to use this system and below the name of the item that will be the money, in this case it is cash. This item must be added in your qb-core/shared/items.lua.
{% endstep %}

{% step %}
## Why Do We Use CreateQuests(id)?

This function creates the quests you want for that specific player (`id`). It uses an export from `qs-inventory`to create each quest and assign it to the player.

You must **define this function** yourself.
{% endstep %}

{% step %}
## How To Write the CreateQuests Function

This function checks if `qs-inventory`is running, then uses the `createQuest` export to register one or more missions for the player.

You can customize the quests as you wish.

#### ✅ Example:

```lua
function CreateQuests(source)
    if not GetResourceState('qs-inventory'):find('started') then
        print('qs-inventory not started, skipping quest creation.')
        return
    end

    -- Example Quest: Use a radio
    exports['qs-inventory']:createQuest(source, {
        name = 'use_radio',
        title = 'Stay Tuned',
        description = 'Use your radio for 10 times.',
        reward = 150,
        requiredLevel = 0,
    })

    -- Example Quest: Visit the hospital
    exports['qs-inventory']:createQuest(source, {
        name = 'visit_hospital',
        title = 'Health Check',
        description = 'Visit the hospital at least once.',
        reward = 200,
        requiredLevel = 1,
    })

    print('Quests assigned to player:', source)
end

```

#### 🔍 Explanation of Each Field:

<table data-header-hidden><thead><tr><th width="138.00006103515625">Field</th><th>Purpose</th></tr></thead><tbody><tr><td>name</td><td>A unique internal ID used to update progress later</td></tr><tr><td>title</td><td>The title that appears in the quest UI</td></tr><tr><td>description</td><td>A brief explanation of what the player needs to do</td></tr><tr><td>reward</td><td>What the player will get once the quest reaches 100%</td></tr><tr><td>requiredLevel</td><td>Optional: lets you hide or lock quests until the player reaches a level</td></tr></tbody></table>

You can add **as many quests as you want** inside this function.
{% endstep %}

{% step %}
## Assigning Quests to Already Connected Players

If your script restarts while players are already online, you need to reassign their quests. You can do this with a loop that runs on server start:

#### ✅ Example:

```lua
CreateThread(function()
    for k, v in pairs(QBCore.Functions.GetPlayers()) do
        if v then
            print('Loaded player:', v)
            CreateQuests(v)
        end
    end
end)
```

This makes sure **no one is left without quests**, even if they were online during a resource restart.
{% endstep %}

{% step %}
## How To Update Quest Progress



Now that your player has quests, you can make **progress happen** by calling:

```lua
exports['qs-inventory']:UpdateQuestProgress(source, questName, amount)
```

You can call this **any time the player does something** related to a quest. You can increase progress slowly, or complete the quest instantly.

> ✅ A quest is considered completed once it reaches **100** progress.

#### ✅ Example:

```lua
if GetResourceState('qs-inventory'):find('started') then
    local success = exports['qs-inventory']:UpdateQuestProgress(source, 'use_radio', 10)
    if success then
        Debug('Quest "use_radio" progress updated')
    else
        Debug('Failed to update quest "use_radio"')
    end
end
```

#### 🧠 How Does the 10 Work?

That number means **“add 10% to the progress bar”** of the quest. Here are examples:

<table data-header-hidden><thead><tr><th width="162.99993896484375">Value</th><th>What Happens</th></tr></thead><tbody><tr><td>5</td><td>Adds 5% progress</td></tr><tr><td>10</td><td>Adds 10% progress — call it 10 times to complete</td></tr><tr><td>100</td><td>Instantly completes the quest</td></tr></tbody></table>

You can also make quests with multiple steps, like:

* Harvest 5 plants (each adds 20)
* Win 3 matches (each adds 33)
* Use 10 radios (each use adds 10)
{% endstep %}

{% step %}
## Safety Check – Only Run if the System is Started

Always wrap your quest-related code with this check to make sure `qs-inventory`is actually loaded:

```lua
if not GetResourceState('qs-inventory'):find('started') then return end
```

This avoids errors if the resource hasn't started yet or crashed.
{% endstep %}
{% endstepper %}

## Example of a mini-script with Missions

* Loads the QB framework.
* Assigns quests when the player joins (`QBCore:Server:OnPlayerLoaded`).
* Reassigns quests to already-connected players if the resource restarts.
* Adds a sample quest that completes when the player eats a `sandwich`.

```lua
-- STEP 1: Load the QB framework
QBCore = exports['qb-core']:GetCoreObject()

-- STEP 2: Create quests when a player joins the server
RegisterNetEvent('QBCore:Server:OnPlayerLoaded', function()
    local src = source
    Wait(2000) -- Wait 2 seconds to make sure the character is fully loaded
    print('[Quests] Loaded player:', id)
    CreateQuests(id) -- Assign quests
end)

-- STEP 3: Reassign quests to all online players when the script starts (e.g., after restart)
CreateThread(function()
    for k, v in pairs(QBCore.Functions.GetPlayers()) do
        if v then
            print('[Quests] Reassigning quests to online player:', v.source)
            CreateQuests(v.source)
        end
    end
end)

-- STEP 4: Function to create quests
function CreateQuests(source)
    -- Make sure the quest system is running
    if not GetResourceState('qs-inventory'):find('started') then
        print('[Quests] qs-inventorynot started. Skipping.')
        return
    end

    -- Example quest: Eat 5 sandwiches
    exports['qs-inventory']:createQuest(source, {
        name = 'eat_sandwich',
        title = 'A Tasty Start',
        description = 'Eat 5 sandwiches to prove your survival instincts.',
        reward = 200,
        requiredLevel = 0,
    })

    print('[Quests] Assigned quest "eat_sandwich" to player:', source)
end

-- STEP 5: Track progress when the sandwich is used
-- This should be triggered from your item system when a player uses a sandwich
RegisterNetEvent('qs:useItem:sandwich', function()
    local src = source

    if not GetResourceState('qs-inventory'):find('started') then return end

    -- Add 20% progress every time a sandwich is eaten (5x = 100%)
    local success = exports['qs-inventory']:UpdateQuestProgress(src, 'eat_sandwich', 20)
    if success then
        print('[Quests] Updated progress for "eat_sandwich" quest - player:', src)
    else
        print('[Quests] Failed to update quest progress - player:', src)
    end
end)

```
