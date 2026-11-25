You must start the RMAN client and connect to the database instances as required by the chosen duplication technique. The RMAN client can be located on any host so long as it can connect to the necessary databases over the network.

To start RMAN and connect to the target and auxiliary instances:

1.  Start the RMAN client on any host that can connect to the necessary database instances.

    For example, enter the following command at the operating system prompt on the destination host:

    `% rman`

2.  At the RMAN prompt, run `CONNECT` commands for the database instances that are required for your duplication technique.

    **Note:**

    When you duplicate a whole CDB or one or more PDBs, connect to the root of both instances.

    - For active database duplication using image copies, you must connect to the source database as `TARGET` and to the auxiliary instance as `AUXILIARY`. You must supply the net service name to connect to the `AUXILIARY` instance. A recovery catalog connection is optional. On both instances, the password for the user performing the duplication must be the same. Any user with a `SYSDBA` or `SYSBACKUP` privilege can perform duplication.

    - For active database duplication using backup sets, you must connect to the source database as `TARGET` by using a net service name. The auxiliary instance uses this net service name to connect to the source database and retrieve the backup sets that are required for the duplication. Connect to the auxiliary instance as `AUXILIARY`. If you are connecting to the auxiliary instance remotely or intend to use the `PASSWORD FILE` option of the `DUPLICATE` command, then connect to the auxiliary instance with a net service name. On both instances, the password for the user performing the duplication must be the same. Any user with a `SYSDBA` or `SYSBACKUP` privilege can perform duplication. A recovery catalog connection is optional.

    - For backup-based duplication without a target connection, you must connect to the auxiliary instance as `AUXILIARY` and the recovery catalog as `CATALOG`.

    - For backup-based duplication with a target connection, you must connect to the source database as `TARGET` and the auxiliary instance as `AUXILIARY`. A recovery catalog is optional.

    - For backup-based duplication without target and recovery catalog connections, you must connect to the auxiliary instance as `AUXILIARY`.

    **Note:**

    You cannot connect as `TARGET` to a standby database.

### Example: Connecting to the Required Databases When Performing Active Database Duplication

In this example, a connection is established to the source database and the auxiliary instance using net service names. The Net Service name of the source database is `srcdb` and that of the auxiliary instance is `dupdb`.

To connect to required databases from the destination host:

1.  Start the RMAN client on the destination host.

    `% rman`

2.  Connect to the source database as `TARGET`.

    `RMAN> CONNECT TARGET sys@srcdb;`

    Enter the password for the `SYS` user on the source database when prompted.

3.  Connect to the auxiliary instance as `AUXILIARY`.

    `RMAN> CONNECT AUXILIARY sys@dupdb;`

    Enter the password for the `SYS` user on the auxiliary instance when prompted.

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
