Learn how to perform external role authorization tasks on the client computer.

Perform the following steps:

1.  Create a Windows local or a domain user name with the same user name and password that exist on the Windows server (if the appropriate user name does not currently exist).
2.  Ensure that parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.
3.  Use Oracle Net Configuration Assistant to configure a network connection from your client computer to Oracle Database.
4.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
5.  Connect to the correct instance:
        SQL> SET INSTANCE connect_identifier

    where` ``connect_identifier` is the net service name for the Oracle Database connection that you created in Step 3.
6.  Connect to Oracle Database:
        SQL> CONNECT SMITH
        Enter password: password

    You are connected to the Windows server over net service with Oracle Database user name `smith`. Roles applied to Oracle Database user name `smith` consist of all roles defined for the Windows user name that were previously mapped to the database roles (in this case, `ORA_DBSALES3_D`). All roles available under an authenticated connection are determined by the Windows user name and the Oracle-specific Windows local groups to which the user belongs (for example,` ORA_``SID``_DBSALES1` or `ORA_``SID``_DBSALES4_DA`).

    **Note:**

    OSDBA and OSOPER are the generic names for the two special operating system groups that control database administrator logins when using operating system authentication.

    **See Also:**

    - [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md)

    - [Oracle Database Net Services Administrator's Guide](../netag/managing-oracle-net-services.md)

**Related Topics**

- [Overview of Manually Granting Administrator, Operator, and Task-Specific Privileges for Databases](overview-of-manually-granting-administrator-operator-and-task-specific-privileges-for-databases.md)

**Parent topic:** [Overview of Manually Creating an External Role](overview-of-manually-creating-an-external-role.md)
