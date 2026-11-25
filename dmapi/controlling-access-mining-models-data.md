Understand how to create a Data Mining user and grant necessary privileges.

- Creating a Data Mining User

- System Privileges for Data Mining

- Object Privileges for Mining Models

### 34.4.1 Creating a Data Mining User

Explains how to create a Data Mining user.

A Data Mining user is a database user account that has privileges for performing data mining activities. Example 34-6 shows how to create a database user. Example 34-7 shows how to assign data mining privileges to the user.

**Note:**

To create a user for the Data Mining sample programs, you must run two configuration scripts as described in "The Data Mining Sample Programs".

Example 34-6 Creating a Database User in SQL\*Plus

1.  Log in to SQL\*Plus with system privileges.

            Enter user-name: sys as sysdba
            Enter password: password

2.  To create a user named `dmuser`, type these commands. Specify a password of your choosing.

        CREATE USER dmuser IDENTIFIED BY password
               DEFAULT TABLESPACE USERS
               TEMPORARY TABLESPACE TEMP
               QUOTA UNLIMITED ON USERS;
        Commit;

    The `USERS` and `TEMP` tablespace are included in the pre-configured database that Oracle ships with the database media. `USERS` is used mostly by demo users; it is appropriate for running the sample programs described in "The Data Mining Sample Programs". `TEMP` is the temporary tablespace that is shared by most database users.

    **Note:**

    Tablespaces for Data Mining users must be assigned according to standard DBA practices, depending on system load and system resources.

3.  To login as `dmuser`, type the following.

        CONNECT dmuser
        Enter password: password

**Related Topics**

- [The Data Mining Sample Programs](the-data-mining-sample-programs.md)

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-USER.md) for the complete syntax of the `CREATE USER` statement

#### 34.4.1.1 Granting Privileges for Data Mining

You must have the `CREATE MINING MODEL` privilege to create models in your own schema. You can perform any operation on models that you own. This includes applying the model, adding a cost matrix, renaming the model, and dropping the model.

The `GRANT` statements in the following example assign a set of basic data mining privileges to the `dmuser` account. Some of these privileges are not required for all mining activities, however it is prudent to grant them all as a group.

Additional system and object privileges are required for enabling or restricting specific mining activities.

Example 34-7 Privileges Required for Data Mining

    GRANT CREATE MINING MODEL TO dmuser;
    GRANT CREATE SESSION TO dmuser;
    GRANT CREATE TABLE TO dmuser;
    GRANT CREATE VIEW TO dmuser;
    GRANT EXECUTE ON CTXSYS.CTX_DDL TO dmuser;

`READ` or `SELECT` privileges are required for data that is not in your schema. For example, the following statement grants `SELECT` access to the `sh.customers` table.

    GRANT SELECT ON sh.customers TO dmuser;

### 34.4.2 System Privileges for Data Mining

Learn different privileges to control operations on mining models.

A system privilege confers the right to perform a particular action in the database or to perform an action on a type of schema objects. For example, the privileges to create tablespaces and to delete the rows of any table in a database are system privileges.

You can perform specific operations on mining models in other schemas if you have the appropriate system privileges. For example, `CREATE ANY MINING MODEL` enables you to create models in other schemas. `SELECT ANY MINING MODEL` enables you to apply models that reside in other schemas. You can add comments to models if you have the `COMMENT ANY MINING MODEL` privilege.

To grant a system privilege, you must either have been granted the system privilege with the `ADMIN OPTION` or have been granted the `GRANT ANY PRIVILEGE` system privilege.

The system privileges listed in the following table control operations on mining models.

Table 34-2 System Privileges for Data Mining

| System Privilege           | Allows you to....                                                                                             |
|:---------------------------|:--------------------------------------------------------------------------------------------------------------|
| `CREATE MINING MODEL`      | Create mining models in your own schema.                                                                      |
| `CREATE ANY MINING MODEL`  | Create mining models in any schema.                                                                           |
| `ALTER ANY MINING MODEL`   | Change the name or cost matrix of any mining model in any schema.                                             |
| `DROP ANY MINING MODEL`    | Drop any mining model in any schema.                                                                          |
| `SELECT ANY MINING MODEL`  | Apply a mining model in any schema, also view model details in any schema.                                    |
| `COMMENT ANY MINING MODEL` | Add a comment to any mining model in any schema.)                                                             |
| `AUDIT_ADMIN` role         | Generate an audit trail for any mining model in any schema. (See Oracle Database Security Guide for details.) |

Example 34-8 Grant System Privileges for Data Mining

The following statements allow `dmuser` to score data and view model details in any schema as long as `SELECT` access has been granted to the data. However, `dmuser` can only create models in the `dmuser` schema.

    GRANT CREATE MINING MODEL TO dmuser;
    GRANT SELECT ANY MINING MODEL TO dmuser;

The following statement revokes the privilege of scoring or viewing model details in other schemas. When this statement is executed, `dmuser` can only perform data mining activities in the `dmuser` schema.

    REVOKE SELECT ANY MINING MODEL FROM dmuser;

**Related Topics**

- [Adding a Comment to a Mining Model](auditing-adding-comments-mining-models.md)
- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)

### 34.4.3 Object Privileges for Mining Models

An object privilege confers the right to perform a particular action on a specific schema object. For example, the privilege to delete rows from the `SH.PRODUCTS` table is an example of an object privilege.

You automatically have all object privileges for schema objects in your own schema. You can grant object privilege on objects in your own schema to other users or roles.

The object privileges listed in the following table control operations on specific mining models.

Table 34-3 Object Privileges for Mining Models

| Object Privilege      | Allows you to....                                                    |
|:----------------------|:---------------------------------------------------------------------|
| `ALTER MINING MODEL`  | Change the name or cost matrix of the specified mining model object. |
| `SELECT MINING MODEL` | Apply the specified mining model object and view its model details.  |

Example 34-9 Grant Object Privileges on Mining Models

The following statements allow `dmuser` to apply the model `testmodel` to the `sales` table, specifying different cost matrixes with each apply. The user `dmuser` can also rename the model `testmodel`. The `testmodel` model and `sales` table are in the `sh` schema, not in the `dmuser` schema.

    GRANT SELECT ON MINING MODEL sh.testmodel TO dmuser;
    GRANT ALTER ON MINING MODEL sh.testmodel TO dmuser;
    GRANT SELECT ON sh.sales TO dmuser;

The following statement prevents `dmuser` from renaming or changing the cost matrix of `testmodel`. However, `dmuser` can still apply `testmodel` to the `sales` table.

    REVOKE ALTER ON MINING MODEL sh.testmodel FROM dmuser;
