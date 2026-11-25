When you execute `DUPLICATE` with `FROM ACTIVE DATABASE`, at least one normal target channel and at least one `AUXILIARY` channel are required.

If you do not configure or preallocate channels, RMAN allocates the necessary channels by default. If you configure or manually allocate channels for active duplication with backup sets, ensure that the number of auxiliary channels is greater than or equal to the number of target channels.

When you connect RMAN to the source database as `TARGET`, you must specify a user name and password, even if RMAN uses operating system authentication. The connection to the auxiliary instance must use the same user name and password as the source database connection. The source database must be mounted or open. If the source database is open, then archiving must be enabled. If the source database is not open, then it must have been shut down consistently.

When you connect RMAN to the auxiliary instance, the following rules apply:

- When running RMAN on the same host as the auxiliary instance, you can connect locally without a net service name, provided that you connect using a user name and password, and provided that your `DUPLICATE` command does not include the `PASSWORD FILE` clause. The connecting user must have the `SYSDBA` or `SYSBACKUP` privilege.

- When connecting remotely, or when using the `PASSWORD FILE` clause in the `DUPLICATE` command, you must connect using a net service name. You must first create a password file for the auxiliary instance.

The source database and auxiliary instances must use the same `SYS` and `SYSBACKUP` password, which means that both instances must have password files. The password file must contain at least two passwords, for the `SYS` and `SYSBACKUP` users. You can start the auxiliary instance and enable the source database to connect to it.

The `DUPLICATE` behavior for password files varies depending on whether your duplicate database will act as a standby database. If you create a duplicate database that is not a standby database, then RMAN does not copy the password file by default. You can specify the `PASSWORD FILE` option to indicate that RMAN can overwrite the existing password file on the auxiliary instance. If you create a standby database, then RMAN copies the password file to the standby host by default, overwriting the existing password file. In this case, the `PASSWORD FILE` clause is not necessary.

You cannot use the `UNTIL` clause when performing active database duplication. RMAN chooses a time based on when the online data files have been completely copied, so that the data files can be recovered to a consistent point in time.

**Parent topic:** [Preparing Servers and Network for Database Duplication](preparing-servers-and-network-for-db-duplication.md)
