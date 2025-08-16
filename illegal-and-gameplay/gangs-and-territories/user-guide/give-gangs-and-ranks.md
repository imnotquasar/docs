# Give Gangs and Ranks

Quasar Gangs & Territories uses a unique system where players can belong to a Gang while also holding a job. The only restriction is that police officers cannot join Gangs due to role conflicts. This system is straightforward but differs from traditional Gang systems, requiring careful attention to its configuration and use.

***

## Grade Configuration

The asset includes a basic grade system for managing Gang roles. Each grade has a numeric value and label, which can be used to assign privileges, such as withdrawing money from the Gang bank. For example:

```lua
Config.Grades = {
    ['none'] = 0,
    ['soldier'] = 1,
    ['underboss'] = 2,
    ['boss'] = 3,
}

Config.LabelGrades = {
    ['none'] = 'None',
    ['soldier'] = 'Soldier',
    ['underboss'] = 'Under Boss',
    ['boss'] = 'Boss',
}

Config.allowedGrades = {
    'boss', -- Grades allowed to access Gang bank
}
```

It is recommended to only modify labels for translation purposes unless you have programming experience.

***

## Assigning Gang Roles

{% stepper %}
{% step %}
### **As an Administrator**

Administrators can assign Gang roles using the `/setgang id gang rank` command. Ensure the PlayerIsAdmin function is correctly configured in `server/custom/framework/*.lua`. Remember, police officers cannot be assigned to Gangs.
{% endstep %}

{% step %}
### **As a Boss**

Gang leaders (bosses) can manage ranks and invite nearby players to their Gang using the boss menu in-game. The menu setup varies based on your Gang configuration in the asset.
{% endstep %}
{% endstepper %}
