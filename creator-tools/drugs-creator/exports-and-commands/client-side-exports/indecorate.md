# isDead (dead state)

This check allows you to know whether a player is dead (`"dead"`), knocked down/last stand (`"lastStand"`) or active (`nil`). It’s useful for blocking actions, pausing job logic, or triggering events while the player can’t interact.

***

## How to Use

```lua
-- Read the player state bag using source
local isDead = Player(source).state.dead  -- possible values: 'dead' | 'lastStand' | nil
print('isDead', isDead)
```

***

## Return values

* `"dead"` → the player is dead (requires respawn/revive).
* `"lastStand"` → the player is downed (bleeding/KO, can still be revived).
* `nil` → the player is alive and functional.

**Compatibility**: if you use `esx_ambulancejob` or `qb-hospital`, they automatically set this value. No need to adjust or add custom exports.

***

## Practical Examples

**1) Block actions when the player is not active**

```lua
local state = Player(source).state.dead

if state == 'dead' or state == 'lastStand' then
    -- block shooting, interactions, animations, etc.
    DisablePlayerFiring(source, true)
    -- your custom logic...
end
```

***

**2) Prevent opening a menu if dead/knocked**

```lua
function TryOpenMenu()
    local state = Player(source).state.dead
    if state ~= nil then
        lib.notify({
            title = 'Unavailable',
            description = 'You cannot open this menu while incapacitated.',
            type = 'error'
        })
        return
    end
    OpenMyMenu()
end
```

***

**3) Differentiate between “dead” and “lastStand”**

```lua
local state = Player(source).state.dead

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

* **State bags**: this relies on `Player(source).state`, so **OneSync must be enabled**.
* **Server/client**: the examples above are written with `source`, which is directly available on server-side events or callbacks.
* **Source of state**: `esx_ambulancejob` and `qb-hospital` set this value automatically. If you’re using a custom medical system, make sure it writes `state.dead` with the same values for full compatibility.
