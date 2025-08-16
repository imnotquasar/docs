# Penal Codes

Quasar Dispatch provides a system for defining and displaying **Penal Codes**, enabling jobs like police or EMS to access detailed penalty information via the MDT. While the fines and jail times are for reference only and not automatically applied, the system allows for comprehensive management and customization.

{% stepper %}
{% step %}
### Multiple Penal Code Lists

You can create multiple code lists and assign them to specific jobs (e.g., police, sheriff, EMS). A single job can access multiple lists if configured.
{% endstep %}

{% step %}
### Customization

Define penalties, fines, and jail times for various infractions in `qs-dispatch/config/jobsdata.lua`. Parameters include:

* `title`: The title of the infraction.
* `desc`: A brief description.
* `fine`: The fine amount (does not auto-charge the player).
* `jailTime`: Jail time in minutes.
{% endstep %}

{% step %}
### Example Usage

Each job (e.g., police, EMS) can have its own list of penal codes for easy access and reference.
{% endstep %}
{% endstepper %}

***

## Example Configuration

Penal Code for Police:

```lua
[0] = {
    title = 'Penal Code of San Andreas',
    desc = 'Primary set of laws governing San Andreas.',
    jobs = { 'police', 'sheriff', 'fbi' },
    PenalCode = {
        { id = 'code_theft', title = 'Theft', desc = 'Taking property without consent.', fine = 300, jailTime = 1 },
        { id = 'code_assault', title = 'Assault', desc = 'Causing harm to another person.', fine = 400, jailTime = 10 },
        { id = 'code_vandalism', title = 'Vandalism', desc = 'Damaging property without permission.', fine = 250, jailTime = 7 },
    }
}
```

Services for EMS:

```lua
[1] = {
    title = 'EMS Department of San Andreas',
    desc = 'List of services provided to citizens.',
    jobs = { 'ambulance', 'police' },
    PenalCode = {
        { id = 'code_injured', title = 'Injured', desc = 'Injured in an incident.', fine = 300, jailTime = 0 },
        { id = 'code_sick', title = 'Sick', desc = 'Suffering from illness.', fine = 400, jailTime = 0 },
        { id = 'code_dead', title = 'Dead', desc = 'Deceased individual.', fine = 500, jailTime = 0 },
    }
}
```

***

## Notes and Recommendations

By leveraging this system, your server's legal and EMS teams can operate more efficiently and with clear guidelines.

{% stepper %}
{% step %}
### Non-Automatic Actions

The system does not automatically send fines or apply jail times; it's designed for visual reference. Future updates may include automatic invoicing.
{% endstep %}

{% step %}
### Avoid Errors

* Do not set jail times below 1 minute unless it's `0`.
* Ensure all job lists and codes are correctly formatted to avoid conflicts.
{% endstep %}

{% step %}
### Customization

Tailor the penal codes to fit your server's roleplay needs, ensuring accurate representation of laws and services.
{% endstep %}
{% endstepper %}
