# History Entry for Player

{% hint style="info" %}
You can only use these events on client-side, do not try any other way.
{% endhint %}

This feature is used to insert a history entry for a player and is compatible only when `Config.MDT.newMdt = false`. It allows history data to be added to the player's job database. For example, if the callback is executed for a police officer, only players in the police job can view the entry.

***

## Parameters

The server callback requires three parameters:

{% stepper %}
{% step %}
### **Callback Function**

Executes upon receiving a response from the server. The `resp` argument indicates success (`true`) or failure (`false`).
{% endstep %}

{% step %}
### **Data Object**

Contains the history data to be inserted:

* **identifier** (string): The player's identifier.
* **datatype** (string): Specifies the type of entry (e.g., `infraction`). Do not modify this value.
* **dataobj** (table): Includes detailed information about the entry:
  * **message** (string): A descriptive message.
  * **by** (string): The individual adding the entry (e.g., "John#1234").
  * **title** (string): The title for the entry.
  * **data** (table): Key-value pairs for additional details:
    * **key**: The label/title of the data.
    * **value**: The content/value of the data.
{% endstep %}
{% endstepper %}

***

## Example (Client-Side)

```lua
TriggerServerCallback("qs-dispatch:server:insertHistoryData", function(resp)
    if resp then
        print("BOLO SUCCESS")
    else
        print("BOLO ERROR")
    end
end, {
    identifier = "12345",
    datatype = "infraction",
    dataobj = {
        message = "Historial de incidente",
        by = "John#1234",
        title = "Incidente de tráfico",
        data = {
            { key = "Descripción", value = "Accidente de tráfico en la intersección" },
            { key = "Fecha", value = "2023-07-13" },
            { key = "Hora", value = "15:30" },
            { key = "Lugar", value = "Calle principal" }
        }
    }
})
```

* This feature is designed for **client-side** usage.
* Ensure that the `identifier` and `dataobj` values are correctly formatted and adapted to your server's logic.
