## Net Service Names and the tnsnames.ora File

The installation process creates a `tnsnames.ora` file on each node.

The `tnsnames.ora` file acts as a repository of net service names. Each net service name is associated with a connect identifier. A connect identifier is an identifier that maps a user-defined name to a connect descriptor. A connect descriptor contains the following information:

- The network route to the service, including the location of the listener through a protocol address

- The `SERVICE_NAME` parameter, with the value set to the name of a database service

**Note:**

The `SERVICE_NAME` parameter you use in the `tnsnames.ora` file is singular, because you can specify only one service name.

The `tnsnames.ora` file is located in both the `Grid_home``\network\admin` and `Oracle_home``\network\admin` directories. By default, the `tnsnames.ora` file is read from the Grid home when Oracle Grid Infrastructure is installed.

With Oracle Clusterware 11g Release 2 and later, the listener association no longer requires `tnsnames.ora` file entries. The listener associations are configured as follows:

- Oracle Database Configuration Assistant (DBCA) no longer sets the `LOCAL_LISTENER` parameter. The Oracle Clusterware agent that starts the database sets the `LOCAL_LISTENER` parameter dynamically, and it sets it to the actual value, not an alias. So `listener_``alias` entries are no longer needed in the `tnsnames.ora` file.

- The `REMOTE_LISTENER` parameter is configured by DBCA to reference the SCAN and SCAN port, without any need for a `tnsnames.ora` entry. Oracle Clusterware uses the Easy Connect naming method with `scanname``:``scanport`, so no listener associations for the `REMOTE_LISTENER` parameter are needed in the `tnsnames.ora` file.

Example 6-2 Adding a Second Listener to an Oracle RAC Database

If you created a database named `orcl1`, to add a second listener, listening on port 2012, use a command similar to the following command to have the database register with both listeners on startup:

    SQL> alter system set local_listener='(DESCRIPTION=(
    ADDRESS_LIST=(ADDRESS=(PROTOCOL=TCP)(HOST=192.168.0.61)(PORT=1521))
    (ADDRESS=(PROTOCOL=TCP)(HOST=192.168.0.61)(PORT=2012))))'
    scope=BOTH SID='OCRL1';

**See Also:**

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for more information about the `tnsnames.ora` file

**Parent topic:** [Oracle Net Services Configuration Files and Parameters](oracle-net-services-configuration-files-and-parameters.md)
