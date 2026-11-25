## Task 2: Modify the Primary Database Service

On the primary database server, modify the existing database service that was created as part of the original Oracle GoldenGate on Oracle RAC configuration.

Set the service role to `PRIMARY`, so that the service is only be started when the database becomes the Data Guard primary database role after a role transition.

As the `oracle` user, modify the service using the following command:

    $ srvctl modify service -db dbName -service service_name
     -role PRIMARY

If your database is part of a multitenant environment, remember to modify both the multitenant container database (CDB) and pluggable database (PDB) services.
