Learn about running system privilege authentication tasks on the client computer.

Perform the following steps:

1.  Log in as a Windows domain user who is a member of one of the Windows local group on the server, according to the system privilege that you want Windows to grant. The administrator must add this domain user to the required Windows local group. Windows local group membership is created on the server system where Oracle Database runs.
2.  Ensure that the parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.
3.  Use Oracle Net Configuration Assistant to configure a network connection from your client computer to the Windows server on which Oracle Database is installed.
4.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
5.  Connect to Oracle Database:
        SQL> SET INSTANCE net_service_name

    where `net_service_name` is the Oracle Net net service name for Oracle Database.
6.  Enter either of the following SQL\*Plus commands so that you connect to the database with the required system privilege:
        SQL> CONNECT / AS SYSOPER
        SQL> CONNECT / AS SYSDBA
        SQL> CONNECT / AS SYSASM
        SQL> CONNECT / AS SYSDG
        SQL> CONNECT / AS SYSKM
        SQL> CONNECT / AS SYSBACKUP

    You are now connected to the Windows server. If you connect with `SYSDBA`, you are given DBA privileges.

    **See Also:**

    [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md)

**Related Topics**

- [Running System Privilege Authentication Tasks on the Oracle Database Server](running-system-privilege-authentication-tasks-on-the-database-server.md)

**Parent topic:** [Overview of Manually Granting Administrator, Operator, and Task-Specific Privileges for Databases](overview-of-manually-granting-administrator-operator-and-task-specific-privileges-for-databases.md)
