## Deleting an Oracle RAC Database Using DBCA

Deleting an Oracle RAC database using DBCA involves first deleting the database, and then removing the database's initialization parameter files, instances, Optimal Flexible Architecture (OFA) structure, and the Oracle network configuration for the database.

To delete a database using DBCA:

1.  Start DBCA on one of the nodes:
    - Run the `dbca` command from the `$ORACLE_HOME/bin` directory.

    DBCA displays the Operations page, displaying different database deployment options.
2.  Select Delete a database, and click Next. DBCA displays a list of all Oracle RAC and single-instance databases running from the Oracle home where DBCA is run.
3.  If your user ID and password are not operating-system authenticated, then the List of Cluster Databases page displays the user name and password fields. If these fields appear, then enter a user ID and password for a user account that has `SYSDBA` privileges.
4.  Select the database to delete, and click Finish.
    After you click Finish, DBCA displays a dialog box to confirm the database and instances that you have configured DBCA to delete.
5.  Click OK to begin the deletion of the database and its associated files, services, and environment settings, or click Cancel to stop the operation.

When you click OK, DBCA continues the operation and deletes all the associated instances for this database. DBCA also removes the parameter files, password files, and `oratab` entries.

At this point, you have accomplished the following:

- Deleted the selected Oracle RAC database from the cluster

- Deleted high availability services assigned to the Oracle RAC database

- Deleted the Oracle Net configuration for the Oracle RAC database

- Deconfigured Oracle Enterprise Manager for the Oracle RAC database

- Deleted the OFA directory file structure for that Oracle RAC database from the cluster

- Deleted the Oracle RAC database data files

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](selecting-dbca-options-to-create-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
