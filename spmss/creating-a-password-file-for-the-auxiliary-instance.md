Connections to the auxiliary instance can be established by using operating system authentication or password file authentication. For backup-based duplication, you can either create a password file or use operating system authentication to connect to the auxiliary instance. For active database duplication, you must use password file authentication.

To connect to a database by using password file authentication, you must create a password file for the database. When duplicating to a remote host, setting up a password file is mandatory. The default location for the password file is `$ORACLE_BASE``\database` on Windows and `$ORACLE_BASE``/dbs` on Linux and UNIX.

**Note:**

When you create a standby database by using RMAN duplication, password files are always copied. In all other cases, password files are copied only if you specify the `PASSWORD FILE` option in the `DUPLICATE` command.

Use one of the following options to create a password file for the auxiliary instance on the destination host:

- Use operating system-specific utilities to copy the source database password file to the destination host and then rename it to match the auxiliary instance name. This is applicable only if the source and destination hosts are on the same platform.
- Create the password file manually. Ensure that the password for the `SYSDBA` and `SYSBACKUP` users are the same in the source database and auxiliary instance.
- Create the password file with the `orapwd` utility. The `SYSBACKUP` option creates a `SYSBACKUP` entry in the new password file.
  The following example creates a password file in the 12.2 format names `orapworcl` that is located in the default location in an operating system file:

      orapwd FILE='/u01/oracle/dbs/orapworcl' FORMAT=12.2
- Specify the `PASSWORD FILE` option on the `DUPLICATE... FROM ACTIVE DATABASE` command.
  RMAN copies the source database password file to the destination host and overwrites any existing password file for the auxiliary instance. This technique is useful if the source database password file has multiple passwords to make available on the duplicate database.

  When you use active database duplication, the password file must contain at least two passwords, for the `SYS` user and the `SYSBACKUP` user. These passwords must match the passwords in the source database.

  **Note:**

  If you create a standby database with the `FROM ACTIVE DATABASE` option, then RMAN always copies the password file to the standby host.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
