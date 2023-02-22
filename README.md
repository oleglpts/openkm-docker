# openkm

Document management system, see: https://www.openkm.com/.

Usage:
------

* docker-compose up (user: okmAdmin, password: admin)

For production replace mysql password and root password in files
* docker-compose.yml
* init_file.sql
* server.xml

After recreate mysql container, set hibernate.hbm2ddl=create,

in OpenKM.cfg; see https://forum.openkm.com/viewtopic.php?t=24518

File init_file.sql is only needed the first time you run docker-compose up.

After starting the containers, make it empty, otherwise the database will be destroyed on restart.

Be patient, containers don't start up quickly the first time.
