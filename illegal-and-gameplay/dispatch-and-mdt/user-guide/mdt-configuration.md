# MDT Configuration

The **MDT (Mobile Data Terminal)** system in Quasar Dispatch is highly customizable, allowing you to define how different jobs interact with it, their permissions, and the categories they can access.

***

## Key Configuration Parameters

{% stepper %}
{% step %}
Enable the New MDT System

`newMdt`: Set to `true` to enable the new MDT system. If set to `false`, the old MDT system will be used (if available).
{% endstep %}

{% step %}
Job-Specific Access

* `JobsAllowedToMDT`: This defines which jobs can use the MDT and what permissions they have. Each job includes:
  * **`gradesAllowedToEdit`**: Specifies which ranks within a job can edit information in the MDT.
  * **`categoryes`**: Defines the sections accessible to the job (e.g., Citizens, Incidents, BOLOs).
  * **`availableLicences`**: Licenses the job can manage within the MDT.
  * **`readDatabaseFor`**: Additional jobs the current job can query in the MDT database.
{% endstep %}

{% step %}
Permissions by Job

* **Police**:
  * Full access to most categories, including Citizens, Incidents, and BOLOs.
  * Can manage licenses and tags, view vehicle/house information, and query mechanics and ambulance jobs.
* **Mechanic**:
  * Limited access; can only edit specific categories (e.g., Incidents, BOLOs).
  * Restricted from managing licenses or viewing citizen details.
* **Ambulance**:
  * Access to essential categories like Incidents and BOLOs.
  * Permissions tailored for medical tasks, excluding license or vehicle management.
{% endstep %}
{% endstepper %}

***

## Default Configuration Example

Police Configuration:

```lua
["police"] = {
    gradesAllowedToEdit = {
        [0] = true,
        [1] = true,
        ['officer'] = true,
        ['boss'] = true
    },
    categoryes = {
        ['citizens'] = {
            enabled = true,
            CanManageLicences = true,
            CanManageTags = true,
            CanViewVehicles = true,
            CanViewHouses = true
        },
        ['incidents'] = { enabled = true },
        ['bolos'] = { enabled = true }
    },
    availableLicences = {
        "driver",
        "weapon"
    },
    readDatabaseFor = {
        "mechanic",
        "ambulance"
    }
}
```

Mechanic Configuration:

```lua
["mechanic"] = {
    gradesAllowedToEdit = {
        [4] = true,
        ['boss'] = true
    },
    categoryes = {
        ['citizens'] = {
            enabled = true,
            CanManageLicences = false,
            CanManageTags = false
        },
        ['incidents'] = { enabled = true },
        ['bolos'] = { enabled = true }
    }
}
```

***

## How to Customize

By fine-tuning these settings, you can tailor the MDT system to suit the unique needs of your server.

{% stepper %}
{% step %}
### Enable or Disable MDT

Use `newMdt` to switch between the new and old systems.
{% endstep %}

{% step %}
### Add Jobs

Add new jobs to `JobsAllowedToMDT` with their specific permissions and accessible categories.
{% endstep %}

{% step %}
### Set Permissions

Modify `gradesAllowedToEdit` and `categoryes` for detailed control over job interactions.
{% endstep %}

{% step %}
### Manage Licenses

Adjust `availableLicences` to define which licenses jobs can manage.
{% endstep %}

{% step %}
### Query Additional Jobs

Use `readDatabaseFor` to allow jobs to query others in the MDT.
{% endstep %}
{% endstepper %}
