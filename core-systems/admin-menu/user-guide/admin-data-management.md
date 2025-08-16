---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Admin Data Management

**Quasar Admin Menu** manages its own database automatically and requires no manual SQL setup. The system creates and maintains the following tables on its own:

* `qs_admin_settings`
* `qs_admin_ranks`
* `qs_admin_permissions`

If you encounter issues related to permission access or rank inconsistencies, a simple fix is to **delete** the `qs_admin_ranks` and `qs_admin_permissions` tables, then **restart the resource**. The script will regenerate them with default values.

***

## Warnings & Best Practices

### Discord Role Assignments

Avoid assigning **multiple Discord roles** that are linked to Admin Menu permissions to a single user.\
For example, if both `Moderator` and `Jr Moderator` roles are defined within the Admin Menu, do **not** assign both roles to the same person.

Doing so can lead to **permission conflicts**, resulting in unpredictable or broken access behavior.
