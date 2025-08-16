---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Interior System

Quasar Advanced Garages incorporates an IPL-based interior system that utilizes **bob74\_ipl** and the latest gamebuild for seamless integration. Ensure you have followed the **Installation Guide** to configure these prerequisites properly.

***

## **GameBuild Requirement**

If the interior system is not functioning as expected, ensure the following:

{% stepper %}
{% step %}
### **GameBuild Configuration**

Add the convar `sv_enforceGameBuild 2802` to your `server.cfg` to enable the necessary features for this system.
{% endstep %}

{% step %}
### **External Asset Conflicts**

Some external assets, such as `rcore_casino`, may interfere with internal IPLs. If the issue persists, contact the developers of conflicting assets for assistance.
{% endstep %}
{% endstepper %}

***

## **Interior Customization**

The asset supports all IPL interiors available in GTA V. You can customize interior configurations, including slot limits and vehicle positions, by modifying the file located in **`config/interiors.lua`**.

***

## **Slot System**

The interior system uses a **slot-based logic**:

{% stepper %}
{% step %}
### **Garage Slot Limits**

Each garage has a predefined vehicle limit. If the garage reaches its limit (e.g., 40 vehicles), no additional parking will be allowed until a vehicle is removed.
{% endstep %}

{% step %}
### **Sync Customization**

You can disable `Config.GarageSync` to make slots unique per player, removing the shared slot limitation. This offers a personalized experience for players but may deviate from the intended functionality.
{% endstep %}
{% endstepper %}
