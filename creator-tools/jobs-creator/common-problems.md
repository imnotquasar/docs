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

<summary>ESX: I get a spam in console "IMPORTANT: RESTART THE SERVER TOAPPLY..."</summary>

#### Troubleshooting Installation Issues

The error you’re encountering is due to a problem in the auto-installation process. To resolve it, you’ll need to manually modify two files: `es_extended/server/common.lua` and `esx_addonaccount/server/main.lua`. Follow the instructions below carefully.

**1. Update `es_extended/server/common.lua`**

This step ensures compatibility with the `qs-jobs-creator` integration.

* **Action**: Open the file `es_extended/server/common.lua` and check if the text `"qs-jobs-creator"` appears at the bottom of the file.
* **If it’s missing**: Add the following code snippet at the end of the file:

```lua
-- Jobs Creator integration (qs-jobs-creator)
RegisterNetEvent('esx:refreshJobs')
AddEventHandler('esx:refreshJobs', function()
    MySQL.Async.fetchAll('SELECT * FROM jobs', {}, function(jobs)
        for k, v in ipairs(jobs) do
            ESX.Jobs[v.name] = v
            ESX.Jobs[v.name].grades = {}
        end

        MySQL.Async.fetchAll('SELECT * FROM job_grades', {}, function(jobGrades)
            for k, v in ipairs(jobGrades) do
                if ESX.Jobs[v.job_name] then
                    ESX.Jobs[v.job_name].grades[tostring(v.grade)] = v
                else
                    print(('[es_extended] [^3WARNING^7] Ignoring job grades for "%s" due to missing job'):format(v.job_name))
                end
            end

            for k2, v2 in pairs(ESX.Jobs) do
                if ESX.Table.SizeOf(v2.grades) == 0 then
                    ESX.Jobs[v2.name] = nil
                    print(('[es_extended] [^3WARNING^7] Ignoring job "%s" due to no job grades found'):format(v2.name))
                end
            end
        end)
    end)
end)
```

* **Purpose**: This code integrates `qs-jobs-creator` by registering an event (`esx:refreshJobs`) that refreshes the job data in the ESX framework. It fetches job and job grade information from the database and updates the `ESX.Jobs` table accordingly, including error handling for missing jobs or grades.

***

**2. Update `esx_addonaccount/server/main.lua`**

This step adds support for refreshing addon accounts with `qs-jobs-creator`.

* **Action**: Open the file `esx_addonaccount/server/main.lua` and append the following code at the bottom:

```lua
-- Jobs Creator integration (qs-jobs-creator)
RegisterNetEvent('esx_addonaccount:refreshAccounts')
AddEventHandler('esx_addonaccount:refreshAccounts', function()
    local result = MySQL.query.await('SELECT * FROM addon_account')

    for i = 1, #result, 1 do
        local name    = result[i].name
        local label   = result[i].label
        local shared  = result[i].shared

        local result2 = MySQL.query.await('SELECT * FROM addon_account_data WHERE account_name = ?', { name })

        if shared == 0 then
            table.insert(AccountsIndex, name)
            Accounts[name] = {}

            for j = 1, #result2, 1 do
                local addonAccount = CreateAddonAccount(name, result2[j].owner, result2[j].money)
                table.insert(Accounts[name], addonAccount)
            end
        else
            local money = nil

            if #result2 == 0 then
                MySQL.insert('INSERT INTO addon_account_data (account_name, money, owner) VALUES (?, ?, ?)',
                    { name, 0, NULL })
                money = 0
            else
                money = result2[1].money
            end

            local addonAccount   = CreateAddonAccount(name, nil, money)
            SharedAccounts[name] = addonAccount
        end
    end
end)
```

* **Purpose**: This code registers an event (`esx_addonaccount:refreshAccounts`) to refresh addon account data. It retrieves account details from the `addon_account` table and processes them based on whether they are shared or individual accounts. For shared accounts, it ensures a default entry exists in the database if none is found.

***

#### Summary

By adding these code snippets, you enable proper integration with `qs-jobs-creator`, allowing the system to dynamically refresh jobs and accounts. Ensure both files are saved after modification, then restart your server to apply the changes.

</details>

<details>

<summary>QBCORE: I get a spam in console "IMPORTANT: RESTART THE SERVER TOAPPLY..."</summary>

#### Resolving Installation Issues with `qs-jobs-creator` in QBCore

The error you’re experiencing stems from a failure in the auto-installation process. To fix this, you’ll need to manually update two files: `qb-core/client/main.lua` and `qb-core/server/main.lua`. Follow the steps below to integrate `qs-jobs-creator` correctly.

***

**1. Update `qb-core/client/main.lua`**

This step ensures the client-side job data refreshes properly with `qs-jobs-creator`.

* **Action**: Open `qb-core/client/main.lua` and search for the text `"qs-jobs-creator"` at the bottom of the file.
* **If it’s missing**: Append the following code at the end of the file:

```lua
-- Jobs Creator integration (qs-jobs-creator)
RegisterNetEvent('qb:refreshJobs')
AddEventHandler('qb:refreshJobs', function(jobs)
    QBCore.Shared.Jobs = jobs
end)

Citizen.CreateThread(function()
    while true do
        Citizen.Wait(5000) -- Check every 5 seconds
        -- Check the resource state: "missing", "started", "starting", "stopped", "stopping", "uninitialized", or "unknown"
        local retval = GetResourceState('qs-jobs-creator')
        if retval ~= 'started' then
            -- Display a prominent warning in the server console
            print("^7-----------------------------------------------------^7")
            print("^1[QBCore] The 'qs-jobs-creator' resource is not running. Please start it to enable job creator integration.^7")
            print("^1When the resource is not running, players with jobs created via 'qs-jobs-creator' will be assigned the default job (unemployed).^7")
            print("^1If you don’t have this resource, remove this warning by editing 'qb-core/server/main.lua' at the bottom.^7")
            print("^2If you don’t own the resource, you can purchase it at: https://buy.quasar-store.com^7")
            print("^4[QBCore] If you have 'qs-jobs-creator' and it’s starting, ensure the resource name is correct ('qs-jobs-creator') and that the script is properly configured.^7")
            print("^7-----------------------------------------------------^7")
        end
    end
end)
```

* **Purpose**:
  * The `qb:refreshJobs` event updates the client-side `QBCore.Shared.Jobs` table with job data from `qs-jobs-creator`.
  * The `Citizen.CreateThread` loop checks every 5 seconds if the `qs-jobs-creator` resource is running. If it isn’t, a colorful, attention-grabbing warning is printed to the console, alerting the server owner to potential issues.

***

**2. Update `qb-core/server/main.lua`**

This step ensures the server-side job data is synchronized with `qs-jobs-creator`.

* **Action**: Open `qb-core/server/main.lua` and append the following code at the bottom:

```lua
-- Jobs Creator integration (qs-jobs-creator)
RegisterNetEvent('qb:refreshJobs')
AddEventHandler('qb:refreshJobs', function(jobs)
    QBCore.Shared.Jobs = jobs
end)

Citizen.CreateThread(function()
    while true do
        Citizen.Wait(5000) -- Check every 5 seconds
        -- Check the resource state: "missing", "started", "starting", "stopped", "stopping", "uninitialized", or "unknown"
        local retval = GetResourceState('qs-jobs-creator')
        if retval ~= 'started' then
            -- Display a prominent warning in the server console
            print("^7-----------------------------------------------------^7")
            print("^1[QBCore] The 'qs-jobs-creator' resource is not running. Please start it to enable job creator integration.^7")
            print("^1When the resource is not running, players with jobs created via 'qs-jobs-creator' will be assigned the default job (unemployed).^7")
            print("^1If you don’t have this resource, remove this warning by editing 'qb-core/server/main.lua' at the bottom.^7")
            print("^2If you don’t own the resource, you can purchase it at: https://buy.quasar-store.com^7")
            print("^4[QBCore] If you have 'qs-jobs-creator' and it’s starting, ensure the resource name is correct ('qs-jobs-creator') and that the script is properly configured.^7")
            print("^7-----------------------------------------------------^7")
        end
    end
end)
```

* **Purpose**:
  * The `qb:refreshJobs` event updates the server-side `QBCore.Shared.Jobs` table with job data.
  * The `Citizen.CreateThread` loop mirrors the client-side check, ensuring the server also monitors the `qs-jobs-creator` resource state and provides the same warning if it’s not running.

***

#### Summary

These changes integrate `qs-jobs-creator` with your QBCore framework by enabling job data synchronization and adding a monitoring system to alert you if the resource isn’t running. After adding the code to both files, save them and restart your server. If the warning persists, verify that:

1. The `qs-jobs-creator` resource is installed and named correctly.
2. The resource is started in your server configuration (e.g., `ensure qs-jobs-creator` in your `server.cfg`).
3. The script is configured properly per its documentation.

If you don’t plan to use `qs-jobs-creator`, you can remove the warning by deleting or commenting out the `Citizen.CreateThread` block in both files.

</details>
