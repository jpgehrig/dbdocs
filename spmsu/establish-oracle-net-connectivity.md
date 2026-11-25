You must be able to establish a connection between the source database and auxiliary instance for certain forms of duplication.

If any of the following conditions is true, the auxiliary instance must be available through Oracle Net Services:

- The RMAN client is run from a host other than the destination host

- The duplication technique chosen is active database duplication

- The destination host is different from the source host

To perform active database duplication, you must connect to the auxiliary instance with `SYSDBA` or `SYSBACKUP` privilege and by using a net service name. The source database to which RMAN is connected as `TARGET` uses this net service name to connect directly to the auxiliary database instance.

To establish Oracle Net connectivity and set up a static listener:

- Follow the instructions in [Oracle Database Administrator’s Guide](../bradv/configuring-rman-client-basic.md) to configure a client for connection to a database and add static service information for the listener.

Example 4-2 Example: Establishing Oracle Net Connectivity Between the Source Database and Auxiliary Instance

Assume that the `DB_NAME` of the source database is `src` and the source host is `src.example.com`. The `DB_NAME` of the auxiliary instance is `dup` and the auxiliary instance is created on the host `dup.example.com`.

Use the following steps to establish Oracle Net connectivity between the source database and the auxiliary instance:

1.  In the `tnanames.ora` file of the source database, add the following entry that corresponds to the duplicate database:
        dupdb = (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=dup.example.com)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=dup)))
2.  On the destination host, create the `tnsnames.ora` file in the `$``ORACLE_HOME``/admin/network` folder. Add the following entry that corresponds to the source database.
        srcdb = (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=src.example.com)(PORT=1521))(CONNECT_DATA=(SERVICE_NAME=src)))

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
