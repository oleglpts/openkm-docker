# openkm

Document management system, see: https://www.openkm.com/.

Usage:
------

Certificate authority:
----------------------
* openssl genrsa -aes256 -passout pass:password -out ./ca.key 4096
* openssl req -new -key ca.key -passin pass:password -out ca.csr
* openssl x509 -req -in ca.csr -signkey ca.key -passin pass:password -days 3650 -out ca.pem

Server certificate:
-------------------
* openssl genrsa -aes256 -passout pass:password -out server.key 4096
* openssl req -new -key Server-private-key.key -passin pass:password -out server.csr
* openssl x509 -req -in server.csr -CA ca.pem -CAkey ca.key -passin pass:password -CAcreateserial -days 3650 -out server.pem
* openssl pkcs12 -export -in server.pem -inkey server.key -passin pass:password -passout pass:password -out server.p12

* docker-compose up

For production replace mysql password and root password in files
* docker-compose.yml
* init_file.sql
* server.xml

After recreate mysql container, set hibernate.hbm2ddl=create,

in OpenKM.cfg; see https://forum.openkm.com/viewtopic.php?t=24518

File init_file.sql is only needed the first time you run docker-compose up.

After starting the containers, make it empty, otherwise the database will be destroyed on restart.

Be patient, containers don't start up quickly the first time.
