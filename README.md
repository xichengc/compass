Compass
=======

A Deoployment Automation System. See Wiki page at https://wiki.openstack.org/wiki/Compass.

How to install Compass?
-----------------------
 1. Go to the Compass project directory.
 2. Run `./install/install.sh` to setup compass environment.
 3. Run `source /etc/profile` to setup compass profile.
 4. Run `./bin/refresh.sh` to initialize database.
 5. Run `service compassd start` to start compass daemon services.

FAQ
---

 * Why doesn't celery start?  What do I do if I get `celery died but pid file exists` message by running `service compassd status`?

  1. Simply remove celery pid file (`/var/run/celery.pid`).
  2. Try running `export C_FORCE_ROOT=1`
  3. Restart Compass daemon.

 * How to restart compass service?
  1. Run `service compassd restart`
  2. Run `service httpd restart` to restart web service.

 * How to check if the compass services run properly?
  1. Run `service compassd status` to check compass services status.
  2. Run `service httpd status` to check web service status.

 * How to troubleshoot if `comapassd` can not start the services?
   1. Try to remove /var/run/celeryd.pid to release the celeryd lock
   2. Try to remove /var/run/progress_update.pid to release the progress_update lock.

 * How to use compass to install distributed systems?

  Access http://<server_ip>/ods/ods.html. In the current version, we only support OpenStack deployment with a simplified configuration. Follow the simple wizard from the Web UI.

 * How to run unittest?
    `COMPASS_SETTING=<your own compass setting> python -m discover -s compass/tests`

 * Where to find the log file?
   1. `/var/log/compass/compass.log` is the compass web log.
   2. `/var/log/compass/celery.log` is the celery log
   3. The redirected celeryd stdout/stderr is at `/tmp/celeryd.log`.
   4. The redirected progress_update.py stdout/stderr is at `/tmp/progress_update.log`
   5. The web server (httpd) log files are under `/var/log/httpd/`.

 * Where to find the compass config file?
   1. the compass setting file is at /etc/compass/setting.
   2. the default global config file for installing distributed system is at /etc/compass/setting
   3. the default celery config file is at /etc/compass/celeryconfig

 * Where is the default database file?
  It is at `/opt/compass/db/app.db`

 * Where is the utility scripts for compass?
  It is at `/opt/compass/bin/`
