# Restart phone cache

When you update your asset or face issues with apps or related downloads, you can use a command to reset the app cache and then restart the asset or server. This won't affect existing accounts in the apps; it will only reset the default apps and clear the cache.

If you've updated asset data, made changes like updating images, or are experiencing issues with broken apps or images, you can resolve this easily. Run the command **/deleteallapps** in your server console. This will restore the default apps and clear the cache without deleting existing accounts. After running the command, restart the asset to ensure the changes take effect properly.

{% stepper %}
{% step %}
### Open the command console in txAdmin

Once opened, simply type the command **/deleteallapps** into the console.
{% endstep %}

{% step %}
### After using the command

After running the command, we recommend clearing the cache and restarting the server.
{% endstep %}

{% step %}
### Phone cache reset

You can now use the phone as intended. Don't forget to do this with every patch you apply.
{% endstep %}
{% endstepper %}
