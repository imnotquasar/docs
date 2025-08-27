# isDead (dead state)

This check allows you to know whether a player is **dead** (`"dead"`), **knocked down/last stand** (`"lastStand"`) or **active** (`nil`). It’s useful for blocking actions, pausing job logic, or triggering events while the player can’t interact.

***

## How to Use

```lua
-- Get the serverId of the local player (or another player if needed)
local serverId = GetPlayerServerId(PlayerId())

-- Read the player state bag
local isDead = Player(serverId).state.dead  -- possible values: 'dead' | 'lastStand' | nil
print('isDead', isDead)
```

***

## Return values

* `"dead"` → the player is dead (requires respawn/revive).
* `"lastStand"` → the player is downed (bleeding/KO, can still be revived).
* `nil` → the player is alive and functional.

> **Compatibility:** if you use **esx\_ambulancejob** or **qb-hospital**, they automatically set this value. No need to adjust or add custom exports.

***

## Practical Examples

#### 1) Block actions when the player is not active

```lua
local sid = GetPlayerServerId(PlayerId())
local state = Player(sid).state.dead

if state == 'dead' or state == 'lastStand' then
    -- block shooting, interactions, animations, etc.
    DisablePlayerFiring(PlayerId(), true)
    -- your custom logic...
end
```

#### 2) Prevent opening a menu if dead/knocked

```lua
function TryOpenMenu()
    local sid = GetPlayerServerId(PlayerId())
    local state = Player(sid).state.dead
    if state ~= nil then
        lib.notify({title='Unavailable', description='You cannot open this menu while incapacitated.', type='error'})
        return
    end
    OpenMyMenu()
end
```

#### 3) Differentiate between “dead” and “lastStand”

```lua
local sid = GetPlayerServerId(PlayerId())
local state = Player(sid).state.dead

if state == 'dead' then
    -- dead logic (respawn UI, hard disable controls)
elseif state == 'lastStand' then
    -- downed logic (call for help, bleeding timer, limited movement)
else
    -- alive: normal behavior
end
```

***

## Notes & Requirements

* **State bags**: this relies on `Player(serverId).state`, so **OneSync** must be enabled.
* **Server/client**: the examples above are **client-side**. On the server you can also use `Player(playerId).state.dead` (with the server playerId).
* **Source of state**: **esx\_ambulancejob** and **qb-hospital** set this value automatically. If you’re using a custom medical system, make sure it writes `state.dead` with the same values for full compatibility.
