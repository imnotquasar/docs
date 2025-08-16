# Common Issues

## No Permissions / Restricted Screen

If you’re stuck on a restricted screen or missing access:

* This usually means there was an issue during the initial table creation.
* To fix it, **delete the following tables** from your database:
  * `qs_admin_ranks`
  * `qs_admin_settings`
* Then, **restart the script**. The system will regenerate the tables with default values.

***

## CPU / RAM Usage Shows 0%

* This indicates a misconfigured `shared/config.json` file.
* Double-check that:
  * `resourcesDir` is correctly set to your server’s resources folder
  * `logFiles` contain valid paths to your `fxserver.log` and `server.log`

***

## Empty Server Console or Not Updating

* Also caused by incorrect `shared/config.json` configuration.
* Verify that the log file paths listed in the `logFiles` array are accurate and point to your actual server log files.
