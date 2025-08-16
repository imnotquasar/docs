# Replace DrawText3D

To use **Quasar Text UI** as a replacement for DrawText3D, add this function to your **client-side script**:

```lua
local texts = {}
function DrawText3D(x, y, z, text, id, key)
    local _id = id
    if not texts[_id] then
        CreateThread(function()
            texts[_id] = 5
            while texts[_id] > 0 do
                texts[_id] = texts[_id] - 1
                Wait(0)
            end
            texts[_id] = nil
            exports['qs-textui']:DeleteDrawText3D(id)
            Debug('Deleted text', id)
        end)
        TriggerEvent('textui:DrawText3D', x, y, z, text, id, key)
    end
    texts[_id] = 5
end
```

***

## How to Replace Basic DrawText3D Calls

Modify your existing DrawText3D usage like this:

{% stepper %}
{% step %}
### **Before (Basic `DrawText3D`):**

```lua
DrawText3D(x, y, z, "Add your text here")
```
{% endstep %}

{% step %}
### **After (Using Quasar Text UI):**

```lua
DrawText3D(x, y, z, "Add your text here", 'track_sit', 'E')
```

This will integrate **Quasar Text UI** for cleaner and optimized text rendering in FiveM.
{% endstep %}
{% endstepper %}
