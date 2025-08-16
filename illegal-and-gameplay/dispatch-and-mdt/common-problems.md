# Common problems

{% hint style="info" %}
Please note that most common errors can be caused by a bad installation or a poorly done update, always verify this using the default asset before communicating your problem to us, this will save time.
{% endhint %}

If you've made it this far, congratulations, you're one of the few customers reading through the documentation and taking an interest in fixing problems that come your way using our resources.

This section is intended for the common problems that some players usually have when using this asset, we ask you to check one by one to find your problem here and save long waits on community tickets. If your problem still persists, do not hesitate to contact us from the Discord community by opening a ticket.

***

## List of common problems

Deploy each section according to your problem, so you will find the solution quickly, each problem has a general and basic solution in its description that will help you solve the case.

<details>

<summary>I get spam alerts when a dispatch call is executed</summary>

The problem occurs when calling the client function 'ramdomscript:client:fight' from the server code, setting the value to -1. This causes an alert to be generated for each player on the server.

```lua
RegisterCommand('test', function ()
    TriggerClientEvent('ramdomscript:client:fight', -1)
end)
```

Or

```lua
RegisterCommand('test', function(source, args, rawCommand)
    local xPlayers = ESX.GetExtendedPlayers() -- Devuelve todos los xPlayers
    for _, xPlayer in pairs(xPlayers) do
        if player.job.name == 'police' then -- Envía el evento A TODOS LOS POLICÍAS CONECTADOS
            TriggerClientEvent('ramdomscript:client:fight', xPlayer.source)
        end
    end
end, false)
```

The solution to the problem:

The solution is to assign the correct values to the function. Instead of using TriggerClientEvent('qs-dispatch:client:fight', -1), we should use 'source' instead.

```lua
RegisterCommand('test', function (source, args, rawCommand)
    TriggerClientEvent('qs-dispatch:client:fight', source)
end)
```

Or

```lua
RegisterCommand('pepe', function(source, args, rawCommand)
    exports['qs-dispatch']:GetPlayerInfo(source, function(playerData)
        if (not playerData) then
            print("Error al obtener los datos del jugador")
            return
        end
        exports['qs-dispatch']:GetSSURL(source, function(screenshot)
            TriggerEvent('qs-dispatch:server:CreateDispatchCall', {
                job = { 'police', 'sheriff', 'traffic', 'patrol' },
                callLocation = playerData.coords,
                callCode = { code = 'Alta velocidad', snippet = 'Vehículo' },
                message = " street_1: " .. playerData.street_1 .. " street_2: " .. playerData.street_2 .. " sex: " .. playerData.sex .. " vehicle_label: " .. playerData.vehicle_label .. " vehicle_colour: " .. playerData.vehicle_colour .. " vehicle_plate: " .. playerData.vehicle_plate .. " speed: " .. playerData.speed .. "",
                flashes = false,
                image = screenshot or nil,
                blip = {
                    sprite = 488,
                    scale = 1.5,
                    colour = 1,
                    flashes = true,
                    text = 'Alta velocidad',
                    time = (20 * 1000), -- 20 segundos
                }
            })
        end)
    end)
end, false)
```

In short, the solution ensures that the event is sent only to the player who initiated it ('source'), thus avoiding issuing alerts to all players on the server. Additionally, some bugs in the code, such as incorrect use of variables, were fixed and readability was improved.

</details>

<details>

<summary>Data overflow (qs-dispatch:blips:updateAll)</summary>



If you have problems with this event qs-dispatch:blips:updateAll and you get out of your server, is that you are using the default configuration of Config.PlayerLocationTick, so this is equal to 5 seconds, this means that you are running the event of the blips every 5 seconds per player, a solution to this is to increase the value, to prevent repeating this event as often as possible.

```lua
Config.PlayerLocationTick = 5 -- Change to 10 for example
```

</details>

<details>

<summary>Open job menu key sends a dispatch call</summary>



Go to client/custom/misc/commands.lua and replace the commands name, and restart the server.

<pre class="language-lua"><code class="lang-lua">TriggerEvent('chat:addSuggestion', '/police', 'Call to Police Services', {
    { name = 'message', help = 'Message to send to police' },
})

<strong>RegisterCommand("police", function(source, args, rawCommand)
</strong>    -- Rest of the call code
end, false)
</code></pre>

The modified code is:

```lua
-- The change was in the /police command
TriggerEvent('chat:addSuggestion', '/policecall', 'Call to Police Services', {
    { name = 'message', help = 'Message to send to police' },
})

RegisterCommand("policecall", function(source, args, rawCommand)
    -- Rest of the call code
end, false)
```

</details>

<details>

<summary>illegal mix of collations error SQL</summary>

#### **How to Fix the Error**

Don’t worry! Follow these simple steps one at a time. You don’t need to be a pro to fix this issue. 😊

***

#### 1. **Check the Collation of the `players` Table**

The problem happens because the database tables have different "collations" (settings for how text is stored and compared). Here’s how to check what collation your `players` table is using:

**Step-by-Step:**

1. **Open Your Database Tool**
   * Use **phpMyAdmin** (if you have it in your hosting panel), **HeidiSQL**, or any other tool to access your database.
2. **Find the Table**\
   Look for a table called `players`.
3.  **Run This Command**\
    In the SQL query box, paste the following command and run it:

    ```sql
    SHOW TABLE STATUS WHERE Name = 'players';
    ```

    * Look for the column called `Collation` in the result. It will say something like `utf8mb4_unicode_ci` or `utf8mb4_general_ci`. Write this down.

***

#### 2. **Change the Collation of the `dispatch_mdt_data` Table**

Now, make the `dispatch_mdt_data` table use the same collation as the `players` table.

**Step-by-Step:**

1.  Once you know the collation of the `players` table (e.g., `utf8mb4_unicode_ci`), run the following command in your database tool:

    ```sql
    ALTER TABLE dispatch_mdt_data CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
    ```

    * Replace `utf8mb4_unicode_ci` with the collation you found for the `players` table.
2. **Save and Close**\
   Close your database tool after running the command.

***

#### 3. **Edit the Script Files**

Depending on whether you use **QB** or **ESX**, follow these steps:

**If You Use QB Framework:**

1. Open your server files.
   * Go to the folder: `qs-dispatch\server\custom\framework\`.
2. Open the file `qb.lua` using **Notepad** or **Notepad++** or **VsCode**.
3. Delete lines **41 to 47**.
   * These are the lines that are causing issues. Highlight them and delete them.

**If You Use ESX Framework:**

1. Open your server files.
   * Go to the folder: `qs-dispatch\server\custom\framework\`.
2. Open the file `esx.lua` using **Notepad** or **Notepad++** or **VsCode**.
3. Delete lines **47 to 53**.
   * Just highlight those lines and delete them.
4. **Save the File**\
   Press `Ctrl + S` or click Save.

***

#### 4. **Restart Your Server**

After making all the changes:

1. Stop your server using your hosting panel or local server control.
2. Start it again.
3. Test everything to make sure it works correctly.

***

#### **How to Ask for Help (If Needed)**

If anything is still not working:

* Double-check that you followed the steps exactly.

You’ve got this! 🚀 Good luck!

</details>
