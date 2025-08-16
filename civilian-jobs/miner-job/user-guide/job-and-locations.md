# Job and Locations

This guide explains how to configure job-specific settings and the various locations used in the mining system. Follow the steps below to customize these aspects according to your server's needs.

***

## **Job Configuration**

The job configuration determines which players or roles can interact with the mining system. If you want the mining system to be restricted to specific jobs, you can enable it as follows:

{% stepper %}
{% step %}
### **Enable Job Requirement**

Set `Config.RequireJob` to `true` to restrict access to players with specific jobs.

```lua
Config.RequireJob = true
```
{% endstep %}

{% step %}
### **Specify Allowed Jobs**

In the `Config.MinerJob` section, list the jobs that are allowed to interact with the mining system. Set each job to `true` for access.

```lua
Config.MinerJob = {
    ['miner'] = true, -- Only players with the "miner" job can access
    -- ['jobname'] = true, -- Add additional jobs here
}
```
{% endstep %}

{% step %}
### **Disable Job Requirement**

If you want all players to access the mining system, set `Config.RequireJob` to `false`.

```lua
Config.RequireJob = false
```
{% endstep %}
{% endstepper %}

***

## **Locations Configuration**

The mining system allows for various key locations such as mining zones, NPC interactions, and item purchase spots. Below is a breakdown of these locations and how to configure them.

{% stepper %}
{% step %}
### **Mining Zone**

Defines the main mining area where players can collect minerals.

* **Key Settings:**
  * `public`: Set to `true` if all players should see the blip on the map.
  * `coords`: The coordinates for the mining zone.
  * `details`: Configure blip settings such as name, sprite, size, color, and display options.
*   **Example Configuration:**

    ```lua
    Config.Locations.miningZone = {
        public = true,
        coords = { x = 2943.91, y = 2747.42, z = 43.33 },
        details = { name = 'Mining Zone', sprite = 762, size = 1.0, color = 10, display = 2 }
    }
    ```
{% endstep %}

{% step %}
### **Ped Locations**

Configure NPCs for interaction within the mining system.

*   **Ped Manager (General Interaction):**

    * Location: Handles general management for the mining system.

    ```lua
    Config.Locations.pedManager = {
        model = "s_m_m_dockwork_01",
        pos = vec4(2943.91, 2747.42, 43.33, 277.795288),
        marker = vec3(2943.91, 2747.42, 44.50)
    }
    ```
*   **Ped Seller (Sell Minerals):**

    * Location: Enables players to sell collected minerals.

    ```lua
    Config.Locations.pedSeller = {
        model = "s_m_m_dockwork_01",
        pos = vec4(2951.063, 2746.15, 43.43, 19.84),
        details = { name = 'Sell minerals', sprite = 431, size = 1.0, color = 10, display = 2 },
        coords = { x = 2951.063, y = 2746.15, z = 43.43 }
    }
    ```
*   **Ped Quest (Mining Quests):**

    * Location: Offers mining-related quests for players.

    ```lua
    Config.Locations.pedQuest = {
        model = "s_m_m_dockwork_01",
        pos = vec4(2948.84, 2751.30, 43.34, 195.59),
        details = { name = 'Miners quest', sprite = 306, size = 1.3, color = 10, display = 2 },
        coords = { x = 2948.84, y = 2751.30, z = 43.34 }
    }
    ```
*   **Ped Leaderboard:**

    * Location: Displays leaderboard rankings for miners.

    ```lua
    Config.Locations.pedLeaderboard = {
        model = "s_m_m_dockwork_01",
        pos = vec4(2956.73, 2745.66, 43.51, 5.66),
        details = { name = 'Miners leaderboard', sprite = 439, size = 1.0, color = 10, display = 2 },
        coords = { x = 2956.73, y = 2745.66, z = 43.51 }
    }
    ```
{% endstep %}

{% step %}
### **Pickaxe Box**

Defines the location for accessing pickaxes.

*   **Example Configuration:**

    ```lua
    Config.Locations.pickaxeBox = {
        marker = vec3(2945.56, 2745.92, 43.80)
    }
    ```
{% endstep %}

{% step %}
### **Conveyor**

Defines the location for refining or processing minerals.

*   **Example Configuration:**

    ```lua
    Config.Locations.conveyor = {
        marker = vec3(2954.04, 2794.23, 41.23)
    }
    ```
{% endstep %}
{% endstepper %}
