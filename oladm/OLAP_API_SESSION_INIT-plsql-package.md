The `OLAP_API_SESSION_INIT` PL/SQL package provides procedures for maintaining a table of initialization parameters for the OLAP API.

This chapter contains the following topics:

- Initialization Parameters for the OLAP API

- Viewing the Configuration Table

- Summary of OLAP_API_SESSION_INIT Subprograms

### C.1 Initialization Parameters for the OLAP API

The `OLAP_API_SESSION_INIT` package contains procedures for maintaining a configuration table of initialization parameters. When the OLAP API opens a session, it executes the `ALTER SESSION` commands listed in the table for any user who has the specified roles. Only the OLAP API uses this table; no other type of application executes the commands stored in it.

This functionality provides an alternative to setting these parameters in the database initialization file or the `init.ora` file, which would alter the environment for all users.

During installation, the table is populated with `ALTER SESSION` commands that have been shown to enhance the performance of the OLAP API. Unless new settings prove to be more beneficial, you do not have to make changes to the table.

The information in the table can be queried through the `ALL_OLAP_ALTER_SESSION` view alias, which is also described in this chapter.

**Note:**

This package is owned by the `SYS` user. You must explicitly be granted execution rights before you can use it.

### C.2 Viewing the Configuration Table

`ALL_OLAP_ALTER_SESSION` is the public synonym for `V$OLAP_ALTER_SESSION`, which is a view for the `OLAP$ALTER_SESSION` table. The view and table are owned by the `SYS` user.

#### C.2.1 ALL_OLAP_ALTER_SESSION View

Each row of `ALL_OLAP_ALTER_SESSION` identifies a role and a session initialization parameter. When a user opens a session using the OLAP API, the session is initialized using the parameters for roles granted to that user.

Table C-1 ALL_OLAP_ALTER_SESSION Column Descriptions

| Column        | Datatype         | NULL       | Description                |
|:--------------|:-----------------|:-----------|:---------------------------|
| `ROLE`        | `VARCHAR2(30)`   | `NOT NULL` | A database role            |
| `CLAUSE_TEXT` | `VARCHAR2(3000)` |            | An `ALTER SESSION` command |

### C.3 Summary of OLAP_API_SESSION_INIT Subprograms

The following table describes the subprograms provided in `OLAP_API_SESSION_INIT`.

Table C-2 OLAP_API_SESSION_INIT Subprograms

| Subprogram                     | Description                                                                                                          |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| ADD_ALTER_SESSION Procedure    | Specifies an `ALTER SESSION` parameter for OLAP API users with a particular database role.                           |
| CLEAN_ALTER_SESSION Procedure  | Removes orphaned data, that is, any `ALTER SESSION` parameters for roles that are no longer defined in the database. |
| DELETE_ALTER_SESSION Procedure | Removes a previously defined `ALTER SESSION` parameter for OLAP API users with a particular database role.           |

#### C.3.1 ADD_ALTER_SESSION Procedure

This procedure specifies an `ALTER SESSION` parameter for OLAP API users with a particular database role. It adds a row to the `OLAP$ALTER_SESSION` table.

##### Syntax

    ADD_ALTER_SESSION (
         role_name           IN     VARCHAR2,
         session_parameter   IN     VARCHAR2);

##### Parameters

The `role_name` and `session_parameter` are added as a row in `OLAP$ALTER_SESSION`.

Table C-3 ADD_ALTER_SESSION Procedure Parameters

| Parameter           | Description                                                               |
|:--------------------|:--------------------------------------------------------------------------|
| `role_name`         | The name of a valid role in the database. Required.                       |
| `session_parameter` | A parameter that can be set with a SQL `ALTER SESSION` command. Required. |

##### Example

The following example inserts a row in `OLAP$ALTER_SESSION` that turns on query rewrite for users with the `OLAP_DBA` role.

    EXECUTE olap_api_session_init.add_alter_session('OLAP_DBA',
         'SET QUERY_REWRITE_ENABLED=TRUE');
    Row inserted

    SELECT * FROM all_olap_alter_session WHERE role='OLAP_DBA';

    ROLE         CLAUSE_TEXT
    ------------ ------------------------------------------------------------
    OLAP_DBA     ALTER SESSION SET QUERY_REWRITE_ENABLED=TRUE

#### C.3.2 CLEAN_ALTER_SESSION Procedure

This procedure removes all `ALTER SESSION` parameters for any role that is not currently defined in the database. It removes all orphaned rows in the `OLAP$ALTER_SESSION` table for those roles.

##### Syntax

    CLEAN_ALTER_SESSION ();

##### Example

The following example deletes all orphaned rows.

    EXECUTE olap_api_session_init.clean_alter_session();

#### C.3.3 DELETE_ALTER_SESSION Procedure

This procedure removes a previously defined `ALTER SESSION` parameter for OLAP API users with a particular database role. It deletes a row from the `OLAP$ALTER_SESSION` table.

##### Syntax

    DELETE_ALTER_SESSION (
         role_name           IN     VARCHAR2,
         session_parameter   IN     VARCHAR2);

##### Parameters

The `role_name` and `session_parameter` together uniquely identify a row in `OLAP$ALTER_SESSION`.

Table C-4 DELETE_ALTER_SESSION Procedure Parameters

| Parameter         | Description                                                               |
|:------------------|:--------------------------------------------------------------------------|
| role_name         | The name of a valid role in the database. Required.                       |
| session_parameter | A parameter that can be set with a SQL `ALTER SESSION` command. Required. |

##### Examples

The following call deletes a row in `OLAP$ALTER_SESSION` that contains a value of `OLAP_DBA` in the first column and `QUERY_REWRITE_ENABLED=TRUE` in the second column.

    EXECUTE olap_api_session_init.delete_alter_session('OLAP_DBA',
         'SET QUERY_REWRITE_ENABLED=TRUE');

    SELECT * FROM all_olap_alter_session WHERE role='OLAP_DBA';

    no rows selected
