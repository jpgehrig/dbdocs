Use the `RECOVER STANDBY DATABASE` command with the `FROM SERVICE` clause to refresh a physical standby database with changes that were made to the primary database.

This example assumes that the `DB_UNIQUE_NAME` of the primary database is `MAIN` and its net service name is `primary_db`. The `DB_UNIQUE_NAME` of the standby database is `STANDBY` and its net service name is `standby_db`.

To refresh the physical standby database with changes made to the primary database:

1.  Ensure that the following prerequisites are met:

    - Oracle Net connectivity is established between the physical standby database and the primary database.

      You can do this by adding an entry corresponding to the primary database in the `tnsnames.ora` file of the physical standby database.

    - The password files on the primary database and the physical standby database are the same.

    - The `COMPATIBLE` parameter in the initialization parameter file of the primary database and physical standby database is set to 12.0.

2.  Start RMAN and connect as target to the physical standby database. It is recommended that you also connect to a recovery catalog.

    The following commands connect as `TARGET` to the physical standby database and as `CATALOG` to the recovery catalog. The connection to the physical standby is established using the `sbu` user, who has been granted `SYSBACKUP` privilege. The net service name of the physical standby database is `standby_db` and that of the recovery catalog is `catdb`.

        CONNECT TARGET "sbu@standby_db AS SYSBACKUP";
        CONNECT CATALOG rman@catdb;

3.  Roll forward the physical standby database using the `RECOVER STANDBY DATABASE` command with the `FROM SERVICE` clause.

    The `FROM SERVICE` clause specifies the service name of the primary database using which the physical standby must be rolled forward. The standby database is restarted after the roll forward operation.

    The following example rolls forward the physical standby database using the primary database whose service name is `primary_db`.

        RECOVER STANDBY DATABASE FROM SERVICE primary_db;

4.  (For Active Data Guard only) Perform the following steps to recover redo data and open the physical standby database in read-only mode:

        ALTER DATABASE RECOVER MANAGED STANDBY DATABASE UNTIL CONSISTENT;
        ALTER DATABASE OPEN READ ONLY;

5.  Start the managed recovery processes on the physical standby database.

    The following command starts the managed recovery process:

        ALTER DATABASE RECOVER MANAGED STANDBY DATABASE DISCONNECT FROM SESSION;

    When using Data Guard Broker, use the following command to start the managed recovery process:

        DGMGRL> edit database standby_db set state='APPLY-ON';

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/identifying-and-accessing-database.md) for information about establishing Oracle Net connectivity

**Parent topic:** [Refresh and Switchover to the Physical Standby Oracle Database](refresh-and-switchover-to-the-phyical-standby-db.md)
