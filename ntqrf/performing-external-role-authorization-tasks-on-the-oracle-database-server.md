Learn how to perform external role authorization tasks on the Oracle Database server.

Perform the following steps:

1.  Add initialization parameter `OS_ROLES` to the `init.ora` file.
2.  Set `OS_ROLES` to `true`.
    The default setting for this parameter is `false`.
3.  Ensure that parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.
4.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
5.  Connect to your Windows server:
        SQL> CONNECT / AS SYSDBA
6.  Create a new database role. You can give this new role whatever name you want. In this example the role is named `DBSALES3`:
        SQL> CREATE ROLE DBSALES3 IDENTIFIED EXTERNALLY;
7.  Grant to `DBSALES3` whatever Oracle Database roles are appropriate to your database environment:
        SQL> GRANT DBA TO DBSALES3 WITH ADMIN OPTN;
8.  Connect to the database as `SYSDBA`:
        SQL> CONNECT / AS SYSDBA
9.  Shut down the database:
        SQL> SHUTDOWN
10. Restart the database:
        SQL> STARTUP
11. Create a Windows local group with the following syntax:
        ORA_sid_rolename[_D][_A]

    For this command, note the following:

    - `sid` identifies the database instance

    - `rolename` identifies the database role granted

    - `D` indicates that this database role is to be a default role of the database user

    - `A` indicates that this database role includes `ADMIN` `OPTN`

    Characters `D` and `A` are optional. If specified, they must be preceded by an underscore.

    For this example, `ORA_orcl_dbsales3_D` is created.
12. Add one or more Windows local or domain user names to this group.
    You can create multiple database roles and grant them to several possible Windows groups with differing options, as shown in the following table. Users connecting to the `ORCL` instance and authenticated by Windows as members of all four of these Windows local groups has the privileges associated with `dbsales3` and `dbsales4` by default (because of option `_D`). If these users first connect as members of `dbsales3` or `dbsales4` and use the `SET ROLE` command, then they can also gain access to database roles `dbsales1` and `dbsales2`. But if these users try to connect with `dbsales1` or `dbsales2` without first connecting with a default role, they are unable to connect. Finally, these users can grant `dbsales2` and `dbsales4` to other roles (because of option `_A`).

    | Database Roles | Windows Groups         |
    |:---------------|:-----------------------|
    | `dbsales1`     | `ORA_ORCL_dbsales1`    |
    | `dbsales2`     | `ORA_ORCL_dbsales2_a`  |
    | `dbsales3`     | `ORA_ORCL_dbsales3_d`  |
    | `dbsales4`     | `ORA_ORCL_dbsales4_da` |

    **Note:**

    When Oracle Database converts the group name to a role name, it changes the name to uppercase.

**See Also:**

Your operating system documentation for instructions on managing users and groups

**Parent topic:** [Overview of Manually Creating an External Role](overview-of-manually-creating-an-external-role.md)
