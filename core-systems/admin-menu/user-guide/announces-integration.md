---
description: >-
  The Quasar Smartphone includes a police app with a simple yet functional MDT
  for receiving alerts and dispatches. Officers can get notifications with
  locations for various incidents.
---

# Announces Integration

**Quasar Admin Menu** allows you to **replace the default txAdmin announcement UI** with your own fully customized system using **`qs-announce`**.

***

## Replace Default txAdmin Announcements

To enable this feature, add the following lines to your `server.cfg`:

```bash
setr txAdmin-hideDefaultAnnouncement true
setr txAdmin-hideDefaultScheduledRestartWarning true
```

This will disable txAdmin’s built-in announcement messages and allow `qs-announce` to take full control over scheduled restarts, warnings, and global announcements — styled and managed your way.
