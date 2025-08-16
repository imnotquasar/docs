---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Music Integration

The music and ambient sounds in Quasar Advanced Garages are designed to enhance immersion but can be adjusted or disabled to suit player preferences, particularly for streamers or those who prefer a quieter experience. Here's how to manage music settings effectively.

***

## **Music Integration**

By default, the garage includes background music tracks to enrich the player experience. You can customize this feature by adding or removing songs, adjusting volume levels, or disabling the music entirely.

{% stepper %}
{% step %}
#### Song filenames must not contain spaces. Replace spaces with underscores or hyphens, and avoid including file extensions (e.g., `.mp3`).
{% endstep %}

{% step %}
#### Ensure all music files are located in `html/sounds/` and use the specified naming conventions.
{% endstep %}
{% endstepper %}

***

## **Configuration Options**

The following settings are available for customizing the music system:

{% stepper %}
{% step %}
### **Enable/Disable Music**

Use `Config.Sounds` to toggle the feature on or off.
{% endstep %}

{% step %}
### **Adjust Volume**

`Config.SoundVolume` controls the volume level. Recommended values range between `0.01` and `0.05` for ambient music.
{% endstep %}

{% step %}
### **Song List**

Update `Config.SoundFiles` to add, remove, or change the tracks played in the garage.
{% endstep %}
{% endstepper %}

***

## **Example Configuration**

```lua
luaCopiarEditarConfig.Sounds = true -- Toggle music on/off
Config.SoundVolume = 0.04 -- Set ambient music volume
Config.SoundFiles = {
    'Gloria_Groove_-_Coisa_Boa',
    'TroyBoi_-_Say_Yeah',
    'NGHTMRE_AAP_Ferg_-_REDLIGHT',
    'Party_Favor_GTA_-_Work_It_Out',
    'Felix_Jaehn_Breaking_Beattz_-_LIITA',
    'Machine_Gun_Kelly_-_El_Diablo'
}
```

***

## **Streamer Mode**

Players who prefer a music-free environment, especially streamers, can activate "Streamer Mode" by disabling music through commands or by setting `Config.Sounds` to `false`. This ensures compliance with streaming platforms and avoids potential copyright issues.

The command for streamer mode is `togglesound`, when used once, it will remove the sound completely and when used again it will return the sound, this command is only for the player who uses it and does not affect the other players since it is local and personal.

<table><thead><tr><th width="279">Command</th><th>Description</th></tr></thead><tbody><tr><td>/togglesound</td><td>Switch to streamer mode on/off.</td></tr></tbody></table>
