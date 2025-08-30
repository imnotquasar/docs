---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Diagnosis system

The **Diagnosis system** makes medical roleplay more realistic and challenging. Instead of simply reviving a patient using the F5 menu, doctors and EMS staff must first **examine the body** and treat the specific injuries before attempting a revival.

If the patient’s body is severely damaged, they cannot be revived until the injuries are properly treated. This ensures that each case requires correct diagnosis and use of medical tools.

***

## How to Diagnose a Patient

1. Open the **F5 radial menu**.
2. Select the **Diagnose** option.
3. A diagnosis screen will appear, showing the **body parts** and their damage level.
4. Review the **injuries report** at the bottom to see the type of wounds.

***

## Treating Injuries

To treat the patient, drag the correct medical item from your inventory to the affected body part. Each injury requires a **specific treatment item**, configured in `Config.TreatmentItems`:

## **Testing and Verification**

{% stepper %}
{% step %}
### **Tweezers**

* Used for **gunshot wounds**.
* Allows you to remove bullets lodged in the patient’s body.
{% endstep %}

{% step %}
### Suture Kit

* Used for **stab wounds**.
* Helps stitch deep cuts and prevent further bleeding.
{% endstep %}

{% step %}
### Ice Pack

* Used for **beat wounds**.
* Reduces swelling and treats bruising caused by blunt trauma.
{% endstep %}

{% step %}
### Burn Cream

* Used for **burn wounds**.
* Provides relief and healing for patients suffering from burns.
{% endstep %}
{% endstepper %}
