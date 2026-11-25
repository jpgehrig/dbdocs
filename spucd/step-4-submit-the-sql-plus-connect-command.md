Submit the SQL\*Plus `CONNECT` command to initially connect to the Oracle database instance or at any time to reconnect as a different user.

- In SQL\*Plus, submit the `CONNECT` command.

Example 3-4 Connecting to a Local Database User

This simple example connects to a local database as user `SYSTEM`. SQL\*Plus prompts for the `SYSTEM` user password.

    connect system

Example 3-5 Connecting to a Local Database User with SYSDBA Privilege

This example connects to a local database as user `SYS` with the `SYSDBA` privilege. SQL\*Plus prompts for the `SYS` user password.

    connect sys as sysdba

When connecting as user `SYS`, you must connect `AS SYSDBA`.

Example 3-6 Connecting to a Local Database User with SYSBACKUP Privilege

This example connects to a local database as user `SYSBACKUP` with the `SYSBACKUP` privilege. SQL\*Plus prompts for the `SYSBACKUP` user password.

    connect sysbackup as sysbackup

When connecting as user `SYSBACKUP`, you must connect `AS SYSBACKUP`.

Example 3-7 Connecting Locally with SYSDBA Privilege with Operating System Authentication

This example connects locally with the `SYSDBA` privilege with operating system authentication.

    connect / as sysdba

Example 3-8 Connecting with Easy Connect Syntax

This example uses easy connect syntax to connect as user `salesadmin` to a remote database running on the host `dbhost.example.com`. The Oracle Net listener (the listener) is listening on the default port (1521). The database service is `sales.example.com`. SQL\*Plus prompts for the `salesadmin` user password.

    connect salesadmin@"dbhost.example.com/sales.example.com"

Example 3-9 Connecting with Easy Connect Syntax with the Service Handler Type Indicated

This example is identical to Example 3-8, except that the service handler type is indicated.

    connect salesadmin@"dbhost.example.com/sales.example.com:dedicated"

Example 3-10 Connecting with Easy Connect Syntax with a Nondefault Listener Port

This example is identical to Example 3-8, except that the listener is listening on the nondefault port number 1522.

    connect salesadmin@"dbhost.example.com:1522/sales.example.com"

Example 3-11 Connecting with Easy Connect Syntax with the Host IP Address

This example is identical to Example 3-8, except that the host IP address is substituted for the host name.

    connect salesadmin@"192.0.2.5/sales.example.com"

Example 3-12 Connecting with an IPv6 Address

This example connects using an IPv6 address. Note the enclosing square brackets.

    connect salesadmin@"[2001:0DB8:0:0::200C:417A]/sales.example.com"

Example 3-13 Connecting by Specifying an Instance

This example specifies the instance to which to connect and omits the database service name. Note that when you specify only the instance, you cannot specify the service handler type.

    connect salesadmin@"dbhost.example.com//orcl"

Example 3-14 Connecting with a Net Service Name

This example connects remotely as user `salesadmin` to the database service designated by the net service name `sales1`. SQL\*Plus prompts for the `salesadmin` user password.

    connect salesadmin@sales1

Example 3-15 Connecting with External Authentication

This example connects remotely with external authentication to the database service designated by the net service name `sales1`.

    connect /@sales1

Example 3-16 Connecting with SYSDBA Privilege and External Authentication

This example connects remotely with the `SYSDBA` privilege and with external authentication to the database service designated by the net service name `sales1`.

    connect /@sales1 as sysdba

Example 3-17 Connecting as a User with a Service Name

This example connects remotely as user `salesadmin` to the database service designated by the net service name `sales1`. The database session starts in the `rev21` edition. SQL\*Plus prompts for the `salesadmin` user password.

    connect salesadmin@sales1 edition=rev21

**Note:**

If you come across any issues while connecting to the database as a user with the `SYSDBA` privileges, then refer to My Oracle Support Notes 69642.1, 233223.1, 18089.1, and 747456.1.

**Parent topic:** [Connecting to the Database with SQL\*Plus](connecting-to-the-database-with-sql-plus.md)
