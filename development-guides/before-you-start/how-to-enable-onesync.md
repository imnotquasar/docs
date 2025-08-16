# How to enable onesync

OneSync is a feature in FiveM that allows for larger server capacities and improved synchronization of entities and players. Enabling OneSync is a straightforward process that requires a simple edit to your server.cfg file.

***

## Steps to Enable OneSync

{% stepper %}
{% step %}
### Open the `server.cfg` File

Navigate to your server's root directory and locate the `server.cfg` file. Open it with a text editor (e.g., Notepad++ or Visual Studio Code).
{% endstep %}

{% step %}
### Add the OneSync Command

Add the following line to your `server.cfg` file to enable OneSync:

```lua
onesync on
```

This ensures OneSync is active for your server.
{% endstep %}

{% step %}
### Optional: Enable Infinity Mode

If your server needs support for more than 64 players (up to 1024), enable OneSync Infinity by adding this line:

```lua
onesync_enableInfinity 1
```

Infinity mode is designed for large-scale servers and requires proper resource optimization.
{% endstep %}

{% step %}
### Save and Restart Your Server

Save the changes to the `server.cfg` file and restart your server to apply the OneSync settings.
{% endstep %}
{% endstepper %}

<figure><img src="../../.gitbook/assets/ezgif-1-94b0006c40.gif" alt=""><figcaption></figcaption></figure>
