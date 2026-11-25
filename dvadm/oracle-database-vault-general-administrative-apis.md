The `DBMS_MACADM` PL/SQL package and the `CONFIGURE_DV` standalone procedure enable you to you perform general maintenance tasks.

- DBMS_MACADM General System Maintenance Procedures
  The `DBMS_MACADM` PL/SQL package general system maintenance procedures perform tasks such as authorizing users or adding new language to Oracle Database Vault.
- CONFIGURE_DV General System Maintenance Procedure
  The `CONFIGURE_DV` procedure configures the initial two Oracle Database user accounts, which are granted the `DV_OWNER` and `DV_ACCTMGR` roles, respectively.

### 21.1 DBMS_MACADM General System Maintenance Procedures

The `DBMS_MACADM` PL/SQL package general system maintenance procedures perform tasks such as authorizing users or adding new language to Oracle Database Vault.

- ADD_APP_EXCEPTION Procedure
  The `ADD_APP_EXCEPTION` procedure enables a common user or package to access local schemas.
- ADD_NLS_DATA Procedure
  The `ADD_NLS_DATA` procedure adds a new language to Oracle Database Vault.
- AUTH_DATAPUMP_CREATE_USER Procedure
  The `AUTH_DATAPUMP_CREATE_USER` procedure authorizes an Oracle Data Pump user to create users during an Oracle Data Pump import operation.
- AUTH_DATAPUMP_GRANT Procedure
  The `AUTH_DATAPUMP_GRANT` procedure authorizes an Oracle Data Pump user to grant Oracle Database Vault-protected roles and system privileges during an Oracle Data Pump import operation.
- AUTH_DATAPUMP_GRANT_ROLE Procedure
  The `AUTH_DATAPUMP_GRANT_ROLE` procedure authorizes an Oracle Data Pump user to grant a specific role during an Oracle Data Pump import operation.
- AUTH_DATAPUMP_GRANT_SYSPRIV Procedure
  The `AUTH_DATAPUMP_GRANT_SYSPRIV` procedure authorizes an Oracle Data Pump user to grant system privileges during an Oracle Data Pump import operation.
- AUTHORIZE_DATAPUMP_USER Procedure
  The `AUTHORIZE_DATAPUMP_USER` procedure authorizes a user to perform Oracle Data Pump operations when Oracle Database Vault is enabled.
- AUTHORIZE_DBCAPTURE Procedure
  The `AUTHORIZE_DBCAPTURE` procedure grants a user authorization to perform Oracle Database Replay workload capture operations.
- AUTHORIZE_DBREPLAY Procedure
  The `AUTHORIZE_DBREPLAY` procedure grants a user authorization to perform Oracle Database Replay workload replay operations.
- AUTHORIZE_DDL Procedure
  The `AUTHORIZE_DDL` procedure grants a user authorization to execute Data Definition Language (DDL) statements on the specified schema.
- AUTHORIZE_DIAGNOSTIC_ADMIN Procedure
  The `AUTHORIZE_DIAGNOSTIC_ADMIN` procedure authorizes a user to query diagnostic views and tables.
- AUTHORIZE_MAINTENANCE_USER Procedure
  The `AUTHORIZE_MAINTENANCE_USER` procedure grants a user authorization to perform Information Lifecycle Management (ILM) operations in an Oracle Database Vault environment.
- AUTHORIZE_PREPROCESSOR Procedure
  The `AUTHORIZE_PREPROCESSOR` procedure grants a user authorization to execute preprocessor programs through external tables.
- AUTHORIZE_PROXY_USER Procedure
  The `AUTHORIZE_PROXY_USER` procedure grants a proxy user authorization to proxy other user accounts, as long as the proxy user has database authorization.
- AUTHORIZE_SCHEDULER_USER Procedure
  The `AUTHORIZE_SCHEDULER_USER` procedure grants a user authorization to schedule database jobs when Oracle Database Vault is enabled.
- AUTHORIZE_TTS_USER Procedure
  The `AUTHORIZE_TTS_USER` procedure authorizes a user to perform Oracle Data Pump transportable tablespace operations for a tablespace when Oracle Database Vault is enabled.
- DELETE_APP_EXCEPTION Procedure
  The `DELETE_APP_EXCEPTION` procedure removes a common user or a common user's package from the Database Vault operations control exception list.
- DISABLE_APP_PROTECTION Procedure
  The `DISABLE_APP_PROTECTION` procedure disables Database Vault operations control.
- DISABLE_DV Procedure
  The `DISABLE_DV` procedure disables Oracle Database Vault.
- DISABLE_DV_DICTIONARY_ACCTS Procedure
  The `DISABLE_DV_DICTIONARY_ACCTS` procedure prevents any user from logging into the database as the `DVSYS` or `DVF` schema user.
- DISABLE_DV_PATCH_ADMIN_AUDIT Procedure
  The `DISABLE_DV_PATCH_ADMIN_AUDIT` procedure disables realm, command rule, and rule set auditing of the actions by users who have the `DV_PATCH_ADMIN` role.
- DISABLE_ORADEBUG Procedure
  The `DISABLE_ORADEBUG` procedure disables the use of the `ORADEBUG` utility in an Oracle Database Vault environment.
- ENABLE_APP_PROTECTION Procedure
  The `ENABLE_APP_PROTECTION` procedure enables Database Vault operations control.
- ENABLE_DV Procedure
  The `ENABLE_DV` procedure enables Oracle Database Vault and Oracle Label Security.
- ENABLE_DV_DICTIONARY_ACCTS Procedure
  The `ENABLE_DV_DICTIONARY_ACCTS` procedure enables users to log into the database as the `DVSYS` or `DVF` user.
- ENABLE_DV_PATCH_ADMIN_AUDIT Procedure
  The `ENABLE_DV_PATCH_ADMIN_AUDIT` procedure enables realm, command rule, and rule set auditing of the actions by users who have the `DV_PATCH_ADMIN` role.
- ENABLE_ORADEBUG Procedure
  The `ENABLE_ORADEBUG` procedure enables the use of the `ORADEBUG` utility in an Oracle Database Vault environment.
- UNAUTH_DATAPUMP_CREATE_USER Procedure
  The `UNAUTH_DATAPUMP_CREATE_USER` procedure removes authorization from an Oracle Data Pump user to create users during an Oracle Data Pump import operation.
- UNAUTH_DATAPUMP_GRANT Procedure
  The `UNAUTH_DATAPUMP_GRANT` procedure removes authorization from an Oracle Data Pump user to grant Oracle Database Vault-protected roles and system privileges during an Oracle Data Pump import operation.
- UNAUTH_DATAPUMP_GRANT_ROLE Procedure
  The `UNAUTH_DATAPUMP_GRANT_ROLE` procedure removes authorization from an Oracle Data Pump user to grant a specific role during an Oracle Data Pump import operation.
- UNAUTH_DATAPUMP_GRANT_SYSPRIV Procedure
  The `UNAUTH_DATAPUMP_GRANT_SYSPRIV` procedure removes authorization from an Oracle Data Pump user to grant system privileges during an Oracle Data Pump import operation.
- UNAUTHORIZE_DATAPUMP_USER Procedure
  The `UNAUTHORIZE_DATAPUMP_USER` procedure revokes the authorization that was granted by the `AUTHORIZE_DATAPUMP_USER` procedure.
- UNAUTHORIZE_DBCAPTURE Procedure
  The `UNAUTHORIZE_DBCAPTURE` procedure revokes authorization from users to perform Oracle Database Replay workload capture operations.
- UNAUTHORIZE_DBREPLAY Procedure
  The `UNAUTHORIZE_DBREPLAY` procedure revokes authorization from users to perform Oracle Database Replay workload replay operations.
- UNAUTHORIZE_DDL Procedure
  The `UNAUTHORIZE_DDL` procedure revokes authorization from a user who was granted authorization to execute DDL statements through the `DBMS_MACDM.AUTHORIZE_DDL` procedure.
- UNAUTHORIZE_DIAGNOSTIC_ADMIN Procedure
  The `UNAUTHORIZE_DIAGNOSTIC_ADMIN` procedure revokes authorization from a user who was authorized with the `DBMS_MACADM.AUTHORIZE_DIAGNOSTIC_ADMIN` procedure to query diagnostic views and tables.
- UNAUTHORIZE_MAINTENANCE_USER Procedure
  The `UNAUTHORIZE_MAINTENANCE_USER` procedure revokes privileges from users who have been granted authorization to perform Information Lifecycle Management (ILM) operations in an Oracle Database Vault environment.
- UNAUTHORIZE_PREPROCESSOR Procedure
  The `UNAUTHORIZE_PREPROCESSOR` procedure revokes authorization from a user to execute preprocessor programs through external tables.
- UNAUTHORIZE_PROXY_USER Procedure
  The `UNAUTHORIZE_PROXY_USER` procedure revokes authorization from a user who was granted proxy authorization from the `DBMS_MACADM.AUTHORIZE_PROXY_USER` procedure.
- UNAUTHORIZE_SCHEDULER_USER Procedure
  The `UNAUTHORIZE_SCHEDULER_USER` procedure revokes the authorization that was granted by the `AUTHORIZE_SCHEDULER_USER` procedure.
- UNAUTHORIZE_TTS_USER Procedure
  The `UNAUTHORIZE_TTS_USER` procedure removes from authorization users who had previously been granted the authorization to perform Oracle Data Pump transportable tablespace operations.

**Parent topic:** Oracle Database Vault General Administrative APIs

#### 21.1.1 ADD_APP_EXCEPTION Procedure

The `ADD_APP_EXCEPTION` procedure enables a common user or package to access local schemas.

Use this procedure when you are configuring Database Vault operations control to automatically restrict common users from accessing pluggable database (PDB) local data. The procedure applies to the entire container, so you must run it from the CDB root. When the exception is for a package, then owner statements from the given package can access local schemas.

##### Syntax

    DBMS_MACADM.ADD_APP_EXCEPTION(
      owner         IN VARCHAR2,
      package_name  IN VARCHAR2);

##### Parameters

Table 21-1 ADD_APP_EXCEPTION

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                            |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `owner`        | Name of the user who you want to add as an exception<br>To find a list of available common users, query the `USERNAME` and `COMMON` columns of the `DBA_USERS` data dictionary view.                                                                                                                                                                   |
| `package_name` | Name of the package that you want to add as an exception if you want to specify a package instead of the entire user account. This package must be owned by the user specified in the `owner` parameter. If you want to create an exception for the entire schema and not any particular package, then specify `'%'` for the `package_name` parameter. |

##### Examples

    EXEC DBMS_MACADM.ADD_APP_EXCEPTION ('C##HR_ADMIN', '%'); --Applies to the user c##hr_admin

    EXEC DBMS_MACADM.ADD_APP_EXCEPTION('C##HR_ADMIN', 'validateHRdata'); --Applies to the package validateHRdata

**Related Topics**

- [Adding Common Users and Packages to an Exception List](dba-operations-in-an-oracle-database-vault-environment.md)
- ENABLE_APP_PROTECTION Procedure
- DISABLE_APP_PROTECTION Procedure
- DELETE_APP_EXCEPTION Procedure

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.2 ADD_NLS_DATA Procedure

The `ADD_NLS_DATA` procedure adds a new language to Oracle Database Vault.

##### Syntax

    DBMS_MACADM.ADD_NLS_DATA(
      language      IN VARCHAR );

##### Parameters

Table 21-2 ADD_NLS_DATA

| Parameter  | Description                                                                                                                                                                                                                                                        |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `language` | Enter one of the following settings. (This parameter is case insensitive.)<br>• `ENGLISH`<br>• `GERMAN`<br>• `SPANISH`<br>• `FRENCH`<br>• `ITALIAN`<br>• `JAPANESE`<br>• `KOREAN`<br>• `BRAZILIAN PORTUGUESE`<br>• `SIMPLIFIED CHINESE`<br>• `TRADITIONAL CHINESE` |

##### Examples

    EXEC DBMS_MACADM.ADD_NLS_DATA('french');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.3 AUTH_DATAPUMP_CREATE_USER Procedure

The `AUTH_DATAPUMP_CREATE_USER` procedure authorizes an Oracle Data Pump user to create users during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only.

##### Syntax

    DBMS_MACADM.AUTH_DATAPUMP_CREATE_USER(
      uname      IN VARCHAR2);

##### Parameters

Table 21-3 AUTH_DATAPUMP_CREATE_USER

| Parameter | Description                                                                                                                                                                               |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user who will need to create users during the import operation.<br>To find the user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.AUTH_DATAPUMP_CREATE_USER('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.4 AUTH_DATAPUMP_GRANT Procedure

The `AUTH_DATAPUMP_GRANT` procedure authorizes an Oracle Data Pump user to grant Oracle Database Vault-protected roles and system privileges during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only. Be aware that this authorization does not cover Oracle Database Vault roles such as `DV_OWNER`, `DV_ADMIN`, `DV_MONITOR`, and so on.

##### Syntax

    DBMS_MACADM.AUTH_DATAPUMP_GRANT(
      uname      IN VARCHAR2);

##### Parameters

Table 21-4 AUTH_DATAPUMP_GRANT

| Parameter   | Description                                                                                                                                                                                                    |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name` | Name of the Oracle Data Pump user who will need to grant roles and privileges to users during the import operation.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.AUTH_DATAPUMP_GRANT('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.5 AUTH_DATAPUMP_GRANT_ROLE Procedure

The `AUTH_DATAPUMP_GRANT_ROLE` procedure authorizes an Oracle Data Pump user to grant a specific role during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only.

##### Syntax

    DBMS_MACADM.AUTH_DATAPUMP_GRANT_ROLE(
      uname      IN VARCHAR2,
      role       IN VARCHAR2 DEFAULT %);

##### Parameters

Table 21-5 AUTH_DATAPUMP_GRANT_ROLE

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user who will need to grant a specific role to users during the import operation.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view.                                                                                                                                                                                                                                                                                            |
| `role`    | The role to grant to the user. Do not specify Oracle Database Vault roles such as `DV_OWNER`, `DV_ADMIN`, `DV_MONITOR`, and so on. If you omit this value or specify `%`, then the user is authorized to grant any roles (other than Oracle Database Vault roles) during the import operation. Note that if the user has been authorized with the `DBMS_MACADM.AUTH_DATAPUMP_GRANT` procedure, or if the user has authorization to grant a specific role, then the user can still grant these roles. |

##### Example

    EXEC DBMS_MACADM.AUTH_DATAPUMP_GRANT_ROLE('DP_MGR', 'DBA');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.6 AUTH_DATAPUMP_GRANT_SYSPRIV Procedure

The `AUTH_DATAPUMP_GRANT_SYSPRIV` procedure authorizes an Oracle Data Pump user to grant system privileges during an Oracle Data Pump import operation.

The procedure applies the `IMPDP` utility only.

##### Syntax

    DBMS_MACADM.AUTH_DATAPUMP_GRANT_SYSPRIV(
      uname      IN VARCHAR2);

##### Parameters

Table 21-6 AUTH_DATAPUMP_GRANT_SYSPRIV

| Parameter | Description                                                                                                                                                                                                  |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user who will need to grant system privileges to users during the `IMPDP` operation.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.AUTH_DATAPUMP_GRANT_SYSPRIV('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.7 AUTHORIZE_DATAPUMP_USER Procedure

The `AUTHORIZE_DATAPUMP_USER` procedure authorizes a user to perform Oracle Data Pump operations when Oracle Database Vault is enabled.

It applies to both the `expdp` and `impdp` utilities.

##### Syntax

    DBMS_MACADM.AUTHORIZE_DATAPUMP_USER(
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2 DEFAULT NULL,
      table_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-7 AUTHORIZE_DATAPUMP_USER

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                            |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the Oracle Data Pump user to whom you want to grant authorization.<br>To find a list of users who have privileges to use Oracle Data Pump (that is, the `EXP_FULL_DATABASE` and `IMP_FULL_DATABASE` roles), query the `DBA_ROLE_PRIVS` data dictionary view as follows:<br>`SELECT GRANTEE, GRANTED_ROLE FROM DBA_ROLE_PRIVS WHERE GRANTED_ROLE LIKE '%FULL%'` |
| `schema_name` | Name of the database schema that the Oracle Data Pump user must export or import. If you omit this parameter, then the user is granted global authorization to export and import any schema in the database. In this case, ensure the user has been granted the `DV_OWNER` role.                                                                                       |
| `table_name`  | Name of the table within the schema specified by the `schema_name` parameter. If you omit this parameter, then the user you specified can export and import all tables within the schema specified by the `schema_name` parameter.                                                                                                                                     |

##### Examples

    EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('DP_MGR');

    EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('DP_MGR', 'HR');

    EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('DP_MGR', 'HR', 'EMPLOYEES');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.8 AUTHORIZE_DBCAPTURE Procedure

The `AUTHORIZE_DBCAPTURE` procedure grants a user authorization to perform Oracle Database Replay workload capture operations.

To find information about users who have been granted this authorization, query the `DBA_DV_DBCAPTURE_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_DBCAPTURE(
      uname      IN VARCHAR2);

##### Parameters

Table 21-8 AUTHORIZE_DBCAPTURE

| Parameter | Description                                                                               |
|:----------|:------------------------------------------------------------------------------------------|
| `uname`   | Name of the user to whom you want to grant Database Replay workload capture authorization |

Example 21-1 Example

    EXEC DBMS_MACADM.AUTHORIZE_DBCAPTURE('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.9 AUTHORIZE_DBREPLAY Procedure

The `AUTHORIZE_DBREPLAY` procedure grants a user authorization to perform Oracle Database Replay workload replay operations.

To find information about users who have been granted this authorization, query the `DBA_DV_DBREPLAY_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_DBREPLAY(
      uname      IN VARCHAR2);

##### Parameters

Table 21-9 AUTHORIZE_DBREPLAY

| Parameter | Description                                                                              |
|:----------|:-----------------------------------------------------------------------------------------|
| `uname`   | Name of the user to whom you want to grant Database Replay workload replay authorization |

Example 21-2 Example

    EXEC DBMS_MACADM.AUTHORIZE_DBREPLAY('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.10 AUTHORIZE_DDL Procedure

The `AUTHORIZE_DDL` procedure grants a user authorization to execute Data Definition Language (DDL) statements on the specified schema.

The DDL authorization allows the grantee to perform DDL operations on users who are authorized to realms or granted Oracle Database Vault roles. However, the DDL authorization does not allow the grantee to perform DDL operations on realm-protected schemas. To enable such operations, you must authorize the user for the realm.

To find information about users who have been granted this authorization, query the `DBA_DV_DDL_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_DDL(
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2);

##### Parameters

Table 21-10 AUTHORIZE_DDL

| Parameter     | Description                                                                                                          |
|:--------------|:---------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the user to whom you want to grant DDL authorization.                                                        |
| `schema_name` | Name of the database schema in which the user wants to perform the DDL statements. Enter `%` to specify all schemas. |

##### Examples

The following example enables user `psmith` to execute DDL statements in any schema:

    EXEC DBMS_MACADM.AUTHORIZE_DDL('psmith', '%');

This example enables user `psmith` to execute DDL statements in the `HR` schema only.

    EXEC DBMS_MACADM.AUTHORIZE_DDL('psmith', 'HR');

**Related Topics**

- [Performing DDL Operations in Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.11 AUTHORIZE_DIAGNOSTIC_ADMIN Procedure

The `AUTHORIZE_DIAGNOSTIC_ADMIN` procedure authorizes a user to query diagnostic views and tables.

These views and tables are as follows:

| Views and Tables V\$            | Views and Tables X\$ |
|:--------------------------------|:---------------------|
| `V$DIAG_OPT_TRACE_RECORDS`      | `X$DBGTFOPTT`        |
| `V$DIAG_SESS_OPT_TRACE_RECORDS` | `X$DBGTFSOPTT`       |
| `V$DIAG_TRACE_FILE_CONTENTS`    | `X$DBGTFVIEW`        |

Without this authorization, when a user queries these tables and views, no values are returned.

##### Syntax

    DBMS_MACADM.AUTHORIZE_DIAGNOSTIC_ADMIN(
      uname      IN VARCHAR2);

##### Parameters

Table 21-11 AUTHORIZE_DIAGNOSTIC_ADMIN

| Parameter | Description                                               |
|:----------|:----------------------------------------------------------|
| `uname`   | Name of the user to whom you want to grant authorization. |

##### Example

    EXEC DBMS_MACADM.AUTHORIZE_DIAGNOSTIC_ADMIN('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.12 AUTHORIZE_MAINTENANCE_USER Procedure

The `AUTHORIZE_MAINTENANCE_USER` procedure grants a user authorization to perform Information Lifecycle Management (ILM) operations in an Oracle Database Vault environment.

To find information about users who have been granted this authorization, query the `DBA_DV_MAINTENANCE_AUTH` view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_MAINTENANCE_USER(
     uname        IN VARCHAR2,
     sname        IN VARCHAR2 DEFAULT NULL,
     objname      IN VARCHAR2 DEFAULT NULL,
     objtype      IN VARCHAR2 DEFAULT NULL,
     action       IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-12 AUTHORIZE_MAINTENANCE_USER

| Parameter | Description                                                                                                                                                    |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user to whom you want to grant authorization                                                                                                       |
| `sname`   | Name of the database schema for which the maintenance operations are to be performed. Enter `%` to specify all schemas.                                        |
| `objname` | Name of the object (such as the name of a table) in the schema that is specified in the `sname` parameter for which maintenance operations are to be performed |
| `objtype` | Type of the `objname` object, such as `table`, `index`, `tablespace`, and so on                                                                                |
| `action`  | Maintenance action. Enter `ilm` for Information Lifecycle Management                                                                                           |

##### Example

The following example enables user `psmith` to have Database Vault authorization to manage ILM features for the `HR.EMPLOYEES` table:

    BEGIN
     DBMS_MACADM.AUTHORIZE_MAINTENANCE_USER (
      uname       => 'psmith',
      sname       => 'HR',
      objname     => 'EMPLOYEES',
      objtype     => 'TABLE',
      action      => 'ILM');
    END;
    /

**Related Topics**

- [Using Information Lifecycle Management with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.13 AUTHORIZE_PREPROCESSOR Procedure

The `AUTHORIZE_PREPROCESSOR` procedure grants a user authorization to execute preprocessor programs through external tables.

To find information about users who have been granted this authorization, query the `DBA_DV_PREPROCESSOR_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_PREPROCESSOR(
      uname      IN VARCHAR2);

##### Parameters

Table 21-13 AUTHORIZE_PREPROCESSOR

| Parameter | Description                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user to whom you want to grant authorization to execute preprocessor programs through external tables |

Example 21-3 Example

    EXEC DBMS_MACADM.AUTHORIZE_PREPROCESSOR('PFITCH');

**Related Topics**

- [Executing Preprocessor Programs with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)
- [DBA_DV_PREPROCESSOR_AUTH View](oracle-database-vault-data-dictionary-views.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.14 AUTHORIZE_PROXY_USER Procedure

The `AUTHORIZE_PROXY_USER` procedure grants a proxy user authorization to proxy other user accounts, as long as the proxy user has database authorization.

For example, the `CREATE SESSION` privilege is a valid database authorization.

`AUTHORIZE_PROXY_USER` does not control whether a particular user can connect as a proxy of another user. That part is controlled by `GRANT CONNECT THROUGH`, which can be issued only by the a user who has the `DV_ACCTMGR` role. Instead, `AUTHORIZE_PROXY_USER` controls whether the proxy user is allowed to assume all the Database Vault authorizations that the target user has. For example, suppose that the proxy user `hr_proxy_user` successfully connects as user `HR`. Now being `HR`, `hr_proxy_user` can access all the objects to which `HR` has access. However, if the target objects are Database Vault protected and `HR` is authorized to access it, `hr_proxy_user` can access the objects if and only if `hr_proxy_user` is proxy-authorized for `HR`. If `hr_proxy_user` is not proxy-authorized for `HR`, then even after connecting as `HR`, `hr_proxy_user` cannot access the Database Vault-protected objects for which `HR` is authorized.

To find information about users who have been granted authorization using `AUTHORIZE_PROXY_USER`, query the `DBA_DV_PROXY_AUTH` view.

##### Syntax

    DBMS_MACADM.AUTHORIZE_PROXY_USER(
      proxy_user   IN VARCHAR2,
      user_name    IN VARCHAR2);

##### Parameters

Table 21-14 AUTHORIZE_PROXY_USER

| Parameter    | Description                                                                                             |
|:-------------|:--------------------------------------------------------------------------------------------------------|
| `proxy_user` | Name of the proxy user.                                                                                 |
| `user_name`  | Name of the database user who will be proxied by the `proxy_user` user. Enter `%` to specify all users. |

##### Examples

The following example enables proxy user `preston` to proxy all users:

    EXEC DBMS_MACADM.AUTHORIZE_PROXY_USER('preston', '%');

This example enables proxy user `preston` to proxy database user `dkent` only.

    EXEC DBMS_MACADM.AUTHORIZE_PROXY_USER('preston', 'dkent');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.15 AUTHORIZE_SCHEDULER_USER Procedure

The `AUTHORIZE_SCHEDULER_USER` procedure grants a user authorization to schedule database jobs when Oracle Database Vault is enabled.

This authorization applies to anyone who has privileges to schedule database jobs. These privileges include any of the following: `CREATE JOB`, `CREATE ANY JOB`, `CREATE EXTERNAL JOB`, `EXECUTE ANY PROGRAM`, `EXECUTE ANY CLASS`, `MANAGE SCHEDULER`.

##### Syntax

    DBMS_MACADM.AUTHORIZE_SCHEDULER_USER(
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-15 AUTHORIZE_SCHEDULER_USER

| Parameter     | Description                                                                                                                                                                                                                                                          |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the user to whom you want to grant authorization.<br>To find a list of users who have privileges (for example, `CREATE JOB` and `CREATE ANY JOB`) to schedule jobs, query the `GRANTEE` and `PRIVILEGE` columns of the `DBA_SYS_PRIVS` data dictionary view. |
| `schema_name` | Name of the database schema for which a job will be scheduled. If you omit this parameter, then the user is granted global authorization to schedule a job for any schema in the database.                                                                           |

##### Examples

The following example authorizes the user `JOB_MGR` to run a job under any schema.

    EXEC DBMS_MACADM.AUTHORIZE_SCHEDULER_USER('JOB_MGR');

This example authorizes user `JOB_MGR` to run a job under the `HR` schema only.

    EXEC DBMS_MACADM.AUTHORIZE_SCHEDULER_USER('JOB_MGR', 'HR');

**Related Topics**

- [Using Oracle Scheduler with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.16 AUTHORIZE_TTS_USER Procedure

The `AUTHORIZE_TTS_USER` procedure authorizes a user to perform Oracle Data Pump transportable tablespace operations for a tablespace when Oracle Database Vault is enabled.

It applies to both the `EXPDP` and `IMPDP` utilities.

##### Syntax

    DBMS_MACADM.AUTHORIZE_TTS_USER(
      uname      IN VARCHAR2,
      tsname     IN VARCHAR2);

##### Parameters

Table 21-16 AUTHORIZE_TTS_USER

| Parameter | Description                                                                                                                                                                                                          |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user who you want to authorize to perform Oracle Data Pump transportable tablespace operations.<br>To find a list of users and their current privileges, query the `DBA_SYS_PRIVS` data dictionary view. |
| `tsname`  | Name of the tablespace in which the `uname` user is to perform the transportable tablespace operation.<br>To find a list of tablespaces, query the `DBA_TABLESPACES` data dictionary view.                           |

##### Example

    EXEC DBMS_MACADM.AUTHORIZE_TTS_USER('PSMITH', 'HR_TS');

**Related Topics**

- [Authorizing Users or Roles for Oracle Data Pump Regular Operations in Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.17 DELETE_APP_EXCEPTION Procedure

The `DELETE_APP_EXCEPTION` procedure removes a common user or a common user's package from the Database Vault operations control exception list.

The exception list allows a user or package to access local PDB data. Removing a user or package from the exception list will block the user or package from accessing PDB local data.

##### Syntax

    DBMS_MACADM.DELETE_APP_EXCEPTION(
      owner         IN VARCHAR2,
      package_name  IN VARCHAR2);

##### Parameters

Table 21-17 DELETE_APP_EXCEPTION

| Parameter      | Description                                                         |
|:---------------|:--------------------------------------------------------------------|
| `owner`        | Name of the user who you want to remove from being an exception     |
| `package_name` | Name of the package that you want to remove from being an exception |

##### Examples

    EXEC DBMS_MACADM.DELETE_APP_EXCEPTION ('C##HR_ADMIN'); --Applies to the user c##hr_admin

    EXEC DBMS_MACADM.DELETE_APP_EXCEPTION('C##HR_ADMIN', 'validateHRdata'); --Applies to the package validateHRdata

**Related Topics**

- [Adding Common Users and Packages to an Exception List](dba-operations-in-an-oracle-database-vault-environment.md)
- ADD_APP_EXCEPTION Procedure
- ENABLE_APP_PROTECTION Procedure
- DISABLE_APP_PROTECTION Procedure

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.18 DISABLE_APP_PROTECTION Procedure

The `DISABLE_APP_PROTECTION` procedure disables Database Vault operations control.

##### Syntax

    DBMS_MACADM.DISABLE_APP_PROTECTION(
      pdb_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-18 DISABLE_APP_PROTECTION

| Parameter  | Description                                                                                                                                                                                                                                                         |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `pdb_name` | Name of the pluggable database (PDB) for which you want to disable Database Vault operations control. If you omit this setting, then it applies to all PDBs in the CDB environment.<br>To find a list of available PDBs, query the `DBA_PDBS` data dictionary view. |

##### Examples

    EXEC DBMS_MACADM.DISABLE_APP_PROTECTION; --Applies to all PDBs

    EXEC DBMS_MACADM.DISABLE_APP_PROTECTION('hr_pdb'); --Applies to a specific PDB

**Related Topics**

- [Disabling Database Vault Operations Control](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.19 DISABLE_DV Procedure

The `DISABLE_DV` procedure disables Oracle Database Vault.

After you run this procedure, you must restart the database.

##### Syntax

    DBMS_MACADM.DISABLE_DV;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.DISABLE_DV;

**Related Topics**

- [Disabling and Enabling Oracle Database Vault](disabling-and-enabling-oracle-database-vault.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.20 DISABLE_DV_DICTIONARY_ACCTS Procedure

The `DISABLE_DV_DICTIONARY_ACCTS` procedure prevents any user from logging into the database as the `DVSYS` or `DVF` schema user.

By default these two accounts are locked. Only a user who has been granted the `DV_OWNER` role can execute this procedure. To find the status of whether users can log into `DVSYS` and `DVF`, query the `DBA_DV_DICTIONARY_ACCTS` data dictionary view. For stronger security, run this procedure to better protect the `DVSYS` and `DVF` schemas. The disablement takes place immediately, so you do not need to restart the database after running this procedure.

##### Syntax

    DBMS_MACADM.DISABLE_DV_DICTIONARY_ACCTS;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.DISABLE_DV_DICTIONARY_ACCTS;

**Related Topics**

- [Archiving and Purging the Oracle Database Vault Audit Trail](auditing-oracle-database-vault.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.21 DISABLE_DV_PATCH_ADMIN_AUDIT Procedure

The `DISABLE_DV_PATCH_ADMIN_AUDIT` procedure disables realm, command rule, and rule set auditing of the actions by users who have the `DV_PATCH_ADMIN` role.

This procedure disables the successful actions of this user, not the failed actions. You should run this procedure after the `DV_PATCH_ADMIN` user has completed database patch operation. To find if auditing is enabled or not, query the `DBA_DV_PATCH_AUDIT` data dictionary view.

##### Syntax

    DBMS_MACADM.DISABLE_DV_PATCH_ADMIN_AUDIT;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.DISABLE_DV_PATCH_ADMIN_AUDIT;

**Related Topics**

- [DV_PATCH_ADMIN Database Vault Database Patch Role](oracle-database-vault-schemas-roles-and-accounts.md)
- ENABLE_DV_PATCH_ADMIN_AUDIT Procedure

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.22 DISABLE_ORADEBUG Procedure

The `DISABLE_ORADEBUG` procedure disables the use of the `ORADEBUG` utility in an Oracle Database Vault environment.

The disablement takes place immediately, so you do not need to restart the database after running this procedure. To find the status of whether the `ORADEBUG` utility is available in Database Vault, query the `DVYS.DBA_DV_ORADEBUG` data dictionary view.

##### Syntax

    DBMS_MACADM.DISABLE_ORADEBUG;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.DISABLE_ORADEBUG;

**Related Topics**

- [Using the ORADEBUG Utility with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.23 ENABLE_APP_PROTECTION Procedure

The `ENABLE_APP_PROTECTION` procedure enables Database Vault operations control.

##### Syntax

    DBMS_MACADM.ENABLE_APP_PROTECTION(
      pdb_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-19 ENABLE_APP_PROTECTION

| Parameter  | Description                                                                                                                                                                                                                                                                              |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `pdb_name` | Allows a single PDB to have Database Vault operations control re-enabled after it was disabled. The default is to omit the `pdb_name` setting and then enable operations control across all of the PDBs.<br>To find a list of available PDBs, query the `DBA_PDBS` data dictionary view. |

##### Examples

    EXEC DBMS_MACADM.ENABLE_APP_PROTECTION; --Applies to all PDBs

    EXEC DBMS_MACADM.ENABLE_APP_PROTECTION('hr_pdb'); --Applies to a specific PDB

**Related Topics**

- [Enabling Database Vault Operations Control](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.24 ENABLE_DV Procedure

The `ENABLE_DV` procedure enables Oracle Database Vault and Oracle Label Security.

If you want to run `DBMS_MACADM.ENABLE_DV` in an application container, then you must run it in the application container outside of application actions.

After you run this procedure, you must restart the database.

##### Syntax

    DBMS_MACADM.ENABLE_DV(
     strict_mode  IN VARCHAR2 DEFAULT);

##### Parameters

Table 21-20 ENABLE_DV

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `strict_mode` | In a multitenant environment, specifies one of the following modes:<br>• `n` specifies regular mode, which allows the PDBs to be Database Vault enabled or disabled. (Default)<br>• `y` specifies strict mode, which puts the PDBs that have not been Database Vault-enabled in restricted mode, until you enable Database Vault in them and then restart the PDB.<br>To apply this setting to all PDBs in the multitenant environment, run the `DBMS_MACADM.ENABLE_DV` procedure in the CDB root. To apply it to all PDBs in an application container, run the procedure in the application root.<br>In a non-multitenant environment, omit this parameter. |

##### Examples

The following example enables Oracle Database Vault in regular mode.

    EXEC DBMS_MACADM.ENABLE_DV;

This example enables Oracle Database Vault in strict mode in a multitenant environment.

    EXEC DBMS_MACADM.ENABLE_DV (strict_mode => 'y');

**Related Topics**

- [Disabling and Enabling Oracle Database Vault](disabling-and-enabling-oracle-database-vault.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.25 ENABLE_DV_DICTIONARY_ACCTS Procedure

The `ENABLE_DV_DICTIONARY_ACCTS` procedure enables users to log into the database as the `DVSYS` or `DVF` user.

By default, the `DVSYS` and `DVF` accounts are locked.

Only a user who has been granted the `DV_OWNER` role can execute this procedure. To find the status of whether users can log into `DVSYS` and `DVF`, query the `DBA_DV_DICTIONARY_ACCTS` data dictionary view. For stronger security, only run this procedure when you need to better protect the `DVSYS` and `DVF` schemas. The enablement takes place immediately, so you do not need to restart the database after running this procedure.

##### Syntax

    DBMS_MACADM.ENABLE_DV_DICTIONARY_ACCTS;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.ENABLE_DV_DICTIONARY_ACCTS;

**Related Topics**

- [Archiving and Purging the Oracle Database Vault Audit Trail](auditing-oracle-database-vault.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.26 ENABLE_DV_PATCH_ADMIN_AUDIT Procedure

The `ENABLE_DV_PATCH_ADMIN_AUDIT` procedure enables realm, command rule, and rule set auditing of the actions by users who have the `DV_PATCH_ADMIN` role.

This procedure is designed to audit these users' actions during a patch upgrade. To find if this auditing is enabled or not, query the `DBA_DV_PATCH_AUDIT` data dictionary view.

##### Syntax

    DBMS_MACADM.ENABLE_DV_PATCH_ADMIN_AUDIT;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.ENABLE_DV_PATCH_ADMIN_AUDIT;

**Related Topics**

- [DV_PATCH_ADMIN Database Vault Database Patch Role](oracle-database-vault-schemas-roles-and-accounts.md)
- DISABLE_DV_PATCH_ADMIN_AUDIT Procedure

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.27 ENABLE_ORADEBUG Procedure

The `ENABLE_ORADEBUG` procedure enables the use of the `ORADEBUG` utility in an Oracle Database Vault environment.

The enablement takes place immediately, so you do not need to restart the database after running this procedure. To find the status of whether the `ORADEBUG` utility is available in Database Vault, query the `DVYS.DBA_DV_ORADEBUG` data dictionary view.

##### Syntax

    DBMS_MACADM.ENABLE_ORADEBUG;

##### Parameters

None

##### Example

    EXEC DBMS_MACADM.ENABLE_ORADEBUG;

**Related Topics**

- [Using the ORADEBUG Utility with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.28 UNAUTH_DATAPUMP_CREATE_USER Procedure

The `UNAUTH_DATAPUMP_CREATE_USER` procedure removes authorization from an Oracle Data Pump user to create users during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only.

##### Syntax

    DBMS_MACADM.UNAUTH_DATAPUMP_CREATE_USER(
      uname      IN VARCHAR2);

##### Parameters

Table 21-21 UNAUTH_DATAPUMP_CREATE_USER

| Parameter | Description                                                                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user whose authorization must be removed.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.UNAUTH_DATAPUMP_CREATE_USER('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.29 UNAUTH_DATAPUMP_GRANT Procedure

The `UNAUTH_DATAPUMP_GRANT` procedure removes authorization from an Oracle Data Pump user to grant Oracle Database Vault-protected roles and system privileges during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only.

##### Syntax

    DBMS_MACADM.UNAUTH_DATAPUMP_GRANT(
      uname      IN VARCHAR2);

##### Parameters

Table 21-22 UNAUTH_DATAPUMP_GRANT

| Parameter   | Description                                                                                                                                                       |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name` | Name of the Oracle Data Pump user whose authorization must be removed.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.UNAUTH_DATAPUMP_GRANT('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.30 UNAUTH_DATAPUMP_GRANT_ROLE Procedure

The `UNAUTH_DATAPUMP_GRANT_ROLE` procedure removes authorization from an Oracle Data Pump user to grant a specific role during an Oracle Data Pump import operation.

This procedure applies to the `impdp` utility only.

##### Syntax

    DBMS_MACADM.UNAUTH_DATAPUMP_GRANT_ROLE(
      uname      IN VARCHAR2,
      role       IN VARCHAR2 DEFAULT %);

##### Parameters

Table 21-23 UNAUTH_DATAPUMP_GRANT_ROLE

| Parameter | Description                                                                                                                                                                                                                                                              |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user whose authorization must be removed.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view.                                                                                                        |
| `role`    | The role that the user is authorized to grant during the import operation. Do not specify Oracle Database Vault roles such as `DV_OWNER`, `DV_ADMIN`, `DV_MONITOR`, and so on. If you omit this value, then the user is not authorized to grant roles during the import. |

##### Example

    EXEC DBMS_MACADM.UNAUTH_DATAPUMP_GRANT_ROLE('DP_MGR', 'DBA');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.31 UNAUTH_DATAPUMP_GRANT_SYSPRIV Procedure

The `UNAUTH_DATAPUMP_GRANT_SYSPRIV` procedure removes authorization from an Oracle Data Pump user to grant system privileges during an Oracle Data Pump import operation.

This procedure applies the `impdp` utility only.

##### Syntax

    DBMS_MACADM.UNAUTH_DATAPUMP_GRANT_SYSPRIV(
      uname      IN VARCHAR2);

##### Parameters

Table 21-24 UNAUTH_DATAPUMP_GRANT_SYSPRIV

| Parameter | Description                                                                                                                                                       |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the Oracle Data Pump user whose authorization must be removed.<br>To find a user's current status, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view. |

##### Example

    EXEC DBMS_MACADM.UNAUTH_DATAPUMP_GRANT_SYSPRIV('DP_MGR');

**Related Topics**

- [Authorizing Users or Roles for Data Pump Regular Export and Import Operations](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.32 UNAUTHORIZE_DATAPUMP_USER Procedure

The `UNAUTHORIZE_DATAPUMP_USER` procedure revokes the authorization that was granted by the `AUTHORIZE_DATAPUMP_USER` procedure.

When you run this procedure, ensure that its settings correspond exactly to the equivalent `AUTHORIZE_DATAPUMP_USER` procedure.

For example, the following two procedures will work because the parameters are consistent:

    EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('DP_MGR');

    EXEC DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER('DP_MGR');

However, because the parameters in the following procedures are not consistent, the `UNAUTHORIZE_DATAPUMP_USER` procedure will not work:

    EXEC DBMS_MACADM.AUTHORIZE_DATAPUMP_USER('JSMITH');

    EXEC DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER('JSMITH', 'HR');

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER(
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2 DEFAULT NULL,
      table_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-25 UNAUTHORIZE_DATAPUMP_USER

| Parameter     | Description                                                                                                                                                                                                                                                                          |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the Oracle Data Pump user from whom you want to revoke authorization.<br>To find a list of users and authorizations from the `AUTHORIZE_DATAPUMP_USER` procedure, query the `DBA_DV_DATAPUMP_AUTH` data dictionary view as follows:<br>`SELECT * FROM DBA_DV_DATAPUMP_AUTH;` |
| `schema_name` | Name of the database schema that the Oracle Data Pump user is authorized to export or import.                                                                                                                                                                                        |
| `table_name`  | Name of the table within the schema specified by the `schema name` parameter.                                                                                                                                                                                                        |

##### Examples

    EXEC DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER('JSMITH');

    EXEC DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER('JSMITH', 'HR');

    EXEC DBMS_MACADM.UNAUTHORIZE_DATAPUMP_USER('JSMITH', 'HR', 'SALARY');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.33 UNAUTHORIZE_DBCAPTURE Procedure

The `UNAUTHORIZE_DBCAPTURE` procedure revokes authorization from users to perform Oracle Database Replay workload capture operations.

To find information about users who have been granted this authorization, query the `DBA_DV_DBCAPTURE_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_DBCAPTURE(
      uname      IN VARCHAR2);

##### Parameters

Table 21-26 UNAUTHORIZE_DBCAPTURE

| Parameter | Description                                                                                  |
|:----------|:---------------------------------------------------------------------------------------------|
| `uname`   | Name of the user from whom you want to revoke Database Replay workload capture authorization |

Example 21-4 Example

    EXEC DBMS_MACADM.UNAUTHORIZE_DBCAPTURE('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.34 UNAUTHORIZE_DBREPLAY Procedure

The `UNAUTHORIZE_DBREPLAY` procedure revokes authorization from users to perform Oracle Database Replay workload replay operations.

To find information about users who have been granted this authorization, query the `DBA_DV_DBREPLAY_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_DBREPLAY(
      uname      IN VARCHAR2);

##### Parameters

Table 21-27 UNAUTHORIZE_DBREPLAY

| Parameter | Description                                                                                 |
|:----------|:--------------------------------------------------------------------------------------------|
| `uname`   | Name of the user from whom you want to revoke Database Replay workload replay authorization |

Example 21-5 Example

    EXEC DBMS_MACADM.UNAUTHORIZE_DBREPLAY('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.35 UNAUTHORIZE_DDL Procedure

The `UNAUTHORIZE_DDL` procedure revokes authorization from a user who was granted authorization to execute DDL statements through the `DBMS_MACDM.AUTHORIZE_DDL` procedure.

To find information about users who have been granted this authorization, query the `DBA_DV_DDL_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_DDL(
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2);

##### Parameters

Table 21-28 UNAUTHORIZE_DDL

| Parameter     | Description                                                                                                       |
|:--------------|:------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the user from whom you want to revoke DDL authorization.                                                  |
| `schema_name` | Name of the database schema in which the user wants to perform the DDL statements. Enter `%` specify all schemas. |

##### Examples

The following example revokes DDL statement execution authorization from user `psmith` for all schemas:

    EXEC DBMS_MACADM.UNAUTHORIZE_DDL('psmith', '%');

This example revokes DDL statement execution authorization from user `psmith` for the `HR` schema only.

    EXEC DBMS_MACADM.UNAUTHORIZE_DDL('psmith', 'HR');

**Related Topics**

- [Performing DDL Operations in Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.36 UNAUTHORIZE_DIAGNOSTIC_ADMIN Procedure

The `UNAUTHORIZE_DIAGNOSTIC_ADMIN` procedure revokes authorization from a user who was authorized with the `DBMS_MACADM.AUTHORIZE_DIAGNOSTIC_ADMIN` procedure to query diagnostic views and tables.

These views and tables are as follows:

| Views and Tables V\$            | Views and Tables X\$ |
|:--------------------------------|:---------------------|
| `V$DIAG_OPT_TRACE_RECORDS`      | `X$DBGTFOPTT`        |
| `V$DIAG_SESS_OPT_TRACE_RECORDS` | `X$DBGTFSOPTT`       |
| `V$DIAG_TRACE_FILE_CONTENTS`    | `X$DBGTFVIEW`        |

Without this authorization, when a user queries these tables and views, no values are returned.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_DIAGNOSTIC_ADMIN(
      uname      IN VARCHAR2);

##### Parameters

Table 21-29 UNAUTHORIZE_DIAGNOSTIC_ADMIN

| Parameter | Description                                                  |
|:----------|:-------------------------------------------------------------|
| `uname`   | Name of the user from whom you want to revoke authorization. |

##### Example

    EXEC DBMS_MACADM.UNAUTHORIZE_DIAGNOSTIC_ADMIN('PFITCH');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.37 UNAUTHORIZE_MAINTENANCE_USER Procedure

The `UNAUTHORIZE_MAINTENANCE_USER` procedure revokes privileges from users who have been granted authorization to perform Information Lifecycle Management (ILM) operations in an Oracle Database Vault environment.

To find information about the settings for the ILM authorization, query the `DBA_DV_MAINTENANCE_AUTH` view.

When you run this procedure, ensure that its settings correspond exactly to the equivalent `AUTHORIZE_MAINTENANCE_USER` procedure.

For example, the following two procedures will work because the parameter settings correspond:

    EXEC DBMS_MACADM.AUTHORIZE_MAINTENANCE_USER('psmith', 'OE', 'ORDERS', 'TABLE', 'ILM');
    EXEC DBMS_MACADM.UNAUTHORIZE_MAINTENANCE_USER('psmith', 'OE', 'ORDERS', 'TABLE', 'ILM');

However, these two statements will fail because the settings do not correspond:

    EXEC DBMS_MACADM.AUTHORIZE_MAINTENANCE_USER('psmith', 'OE', 'ORDERS', 'TABLE', 'ILM');

    EXEC DBMS_MACADM.UNAUTHORIZE_MAINTENANCE_USER('psmith', '%', '%', '%', 'ILM');

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_MAINTENANCE_USER(
     uname        IN VARCHAR2,
     sname        IN VARCHAR2 DEFAULT NULL,
     objname      IN VARCHAR2 DEFAULT NULL,
     objtype      IN VARCHAR2 DEFAULT NULL,
     action       IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-30 UNAUTHORIZE_MAINTENANCE_USER

| Parameter | Description                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user from whom you want to revoke authorization                                                                                              |
| `sname`   | Name of the database schema for which the maintenance operations are performed. Enter `%` to specify all schemas.                                        |
| `objname` | Name of the object (such as the name of a table) in the schema that is specified in the `sname` parameter for which maintenance operations are performed |
| `objtype` | Type of the `objname` object, such as `table`, `index`, `tablespace`, and so on                                                                          |
| `action`  | Maintenance action. Enter `ilm` for Information Lifecycle Management                                                                                     |

##### Example

The following example revokes privileges from Database Vault user `psmith` so that she can no longer perform ILM operations in any `HR` schema objects:

    BEGIN
     DBMS_MACADM.UNAUTHORIZE_MAINTENANCE_USER (
      uname       => 'psmith',
      sname       => 'HR',
      objname     => 'EMPLOYEES',
      objtype     => 'TABLE',
      action      => 'ILM');
    END;
    /

**Related Topics**

- [Using Information Lifecycle Management with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.38 UNAUTHORIZE_PREPROCESSOR Procedure

The `UNAUTHORIZE_PREPROCESSOR` procedure revokes authorization from a user to execute preprocessor programs through external tables.

To find information about users who have been granted this authorization, query the `DBA_DV_PREPROCESSOR_AUTH` data dictionary view.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_PREPROCESSOR(
      uname      IN VARCHAR2);

##### Parameters

Table 21-31 UNAUTHORIZE_PREPROCESSOR

| Parameter | Description                                                                                                          |
|:----------|:---------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user from whom you want to revoke authorization to execute preprocessor programs through external tables |

Example 21-6 Example

    EXEC DBMS_MACADM.UNAUTHORIZE_PREPROCESSOR('PFITCH');

**Related Topics**

- [Executing Preprocessor Programs with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)
- [DBA_DV_PREPROCESSOR_AUTH View](oracle-database-vault-data-dictionary-views.md)

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.39 UNAUTHORIZE_PROXY_USER Procedure

The `UNAUTHORIZE_PROXY_USER` procedure revokes authorization from a user who was granted proxy authorization from the `DBMS_MACADM.AUTHORIZE_PROXY_USER` procedure.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_PROXY_USER(
      proxy_user   IN VARCHAR2,
      user_name    IN VARCHAR2);

##### Parameters

Table 21-32 UNAUTHORIZE_PROXY_USER

| Parameter    | Description                                                                                         |
|:-------------|:----------------------------------------------------------------------------------------------------|
| `proxy_user` | Name of the proxy user from whom you want to revoke authorization.                                  |
| `user_name`  | Name of the database user who was proxied by the `proxy_user` user. Enter `%` to specify all users. |

##### Examples

The following example revokes proxy authorization from user `preston` for proxying all users:

    DBMS_MACADM.UNAUTHORIZE_PROXY_USER('preston', '%');

This example revokes proxy authorization from user `preston` for proxying database user `psmith` only.

    EXEC DBMS_MACADM.UNAUTHORIZE_PROXY_USER('preston', 'psmith');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.40 UNAUTHORIZE_SCHEDULER_USER Procedure

The `UNAUTHORIZE_SCHEDULER_USER` procedure revokes the authorization that was granted by the `AUTHORIZE_SCHEDULER_USER` procedure.

When you run this procedure, ensure that its settings correspond exactly to the equivalent `AUTHORIZE_SCHEDULER_USER` procedure. For example, the following two procedures will work because the parameters are consistent:

    EXEC DBMS_MACADM.AUTHORIZE_SCHEDULER_USER('JOB_MGR');

    EXEC DBMS_MACADM.UNAUTHORIZE_SCHEDULER_USER('JOB_MGR');

However, because the parameters in the following procedures are not consistent, the `UNAUTHORIZE_SCHEDULER_USER` procedure will not work:

    EXEC DBMS_MACADM.AUTHORIZE_SCHEDULER_USER('JOB_MGR');

    EXEC DBMS_MACADM.UNAUTHORIZE_SCHEDULER_USER('JOB_MGR', 'HR');

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_SCHEDULER_USER
      user_name      IN VARCHAR2,
      schema_name    IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 21-33 UNAUTHORIZE_SCHEDULER_USER

| Parameter     | Description                                                                                                                                                                                                                                                               |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`   | Name of the job scheduling user from whom you want to revoke authorization.<br>To find a list of users and authorizations from the `AUTHORIZE_SCHEDULER_USER` procedure, query the `DBA_DV_JOB_AUTH` data dictionary view as follows:<br>`SELECT * FROM DBA_DV_JOB_AUTH;` |
| `schema_name` | Name of the database schema for which the user is authorized to schedule jobs.                                                                                                                                                                                            |

##### Examples

    EXEC DBMS_MACADM.UNAUTHORIZE_SCHEDULER_USER('JOB_MGR');

    EXEC DBMS_MACADM.UNAUTHORIZE_SCHEDULER_USER('JOB_MGR', 'HR');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

#### 21.1.41 UNAUTHORIZE_TTS_USER Procedure

The `UNAUTHORIZE_TTS_USER` procedure removes from authorization users who had previously been granted the authorization to perform Oracle Data Pump transportable tablespace operations.

##### Syntax

    DBMS_MACADM.UNAUTHORIZE_TTS_USER
      uname      IN VARCHAR2,
      tsname     IN VARCHAR2);

##### Parameters

Table 21-34 UNAUTHORIZE_TTS_USER

| Parameter | Description                                                                                                                                                                                                                             |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `uname`   | Name of the user who you want to remove from being authorized to perform Oracle Data Pump transportable tablespace operations.<br>To find a list of users and their current privileges, query the `DBA_SYS_PRIVS` data dictionary view. |
| `tsname`  | Name of the tablespace that is used in the transportable tablespace operation.<br>To find a list of tablespaces, query the `DBA_TABLESPACES` data dictionary view.                                                                      |

##### Example

    EXEC DBMS_MACADM.UNAUTHORIZE_TTS_USER('PSMITH', 'HR_TS');

**Parent topic:** DBMS_MACADM General System Maintenance Procedures

### 21.2 CONFIGURE_DV General System Maintenance Procedure

The `CONFIGURE_DV` procedure configures the initial two Oracle Database user accounts, which are granted the `DV_OWNER` and `DV_ACCTMGR` roles, respectively.

You can check the status of this configuration by querying the `DBA_DV_STATUS` data dictionary view. Before you run the `CONFIGURE_DV` procedure, you must create the two user accounts and grant them the `CREATE SESSION` privilege. The accounts can be either local or common. If you create common user accounts, then the Database Vault roles that are granted to these users apply to the current pluggable database (PDB) only. You then refer to these user accounts for the `CONFIGURE_DV` procedure.

The `CONFIGURE_DV` procedure resides in the `SYS` schema. Oracle provides a synonym, `DVSYS.CONFIGURE_DV`, so that any existing Oracle Database Vault configuration scripts that you may have created in previous releases will continue to work in this release.

You only can run the `CONFIGURE_DV` procedure once, when you are ready to configure and enable Oracle Database Vault with an Oracle database. After you run this procedure, you must run `utlrp.sql` script and then `DBMS_MACADM.ENABLE_DV` to complete the registration process. Oracle strongly recommends that for better security, you use the two accounts you create here as back-up accounts and then create additional accounts for every day use. See [Backup Oracle Database Vault Accounts](oracle-database-vault-schemas-roles-and-accounts.md) for guidance.

If after running `CONFIGURE_DV` you decide that you want to modify the settings that you had entered, you or another user who has the `DV_OWNER` role must disable Database Vault, and then have an administrator with the `SYSDBA` or `SYSOPER` administrative privilege restart the database. If you are in a multitenant environment, as user `SYS`, then commonly grant the `DV_OWNER` user the `DV_OWNER` role, with the `CONTAINER` clause set to `ALL`.

When you run the `CONFIGURE_DV` procedure, it checks the `DVSYS` schema for problems such as missing tables or packages. If it finds problems, then it raises an `ORA-47500 Database Vault cannot be configured` error. If this happens, then you can reinstall Oracle Database Vault by running `catmac.sql` on `CDB$ROOT` and the associated PDBs.

Together, the `CONFIGURE_DV` and `DBMS_MACADM.ENABLE_DV` procedures, and the and `utlrp.sql` script, are designed to be a command-line alternative to using Oracle Database Configuration Assistant (DBCA) to configure and enable Oracle Database Vault with an Oracle database.

When you configure and enable Oracle Database Vault with an Oracle database, you must run the `CONFIGURE_DV` procedure as user `SYS`.

#### Syntax

    CONFIGURE_DV
      dvowner_uname         IN VARCHAR2,
      dvacctmgr_uname       IN VARCHAR2,
      force_local_dvowner   IN BOOLEAN;

#### Parameters

Table 21-35 CONFIGURE_DV

| Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `dvowner_uname`       | Name of the user who will be the Database Vault Owner. This user will be granted the `DV_OWNER` role.                                                                                                                                                                                                                                                                                                                                               |
| `dvacctmgr_uname`     | Name of the user who will be the Database Vault Account Manager. This user will be granted the `DV_ACCTMGR` role. If you omit this setting, the user specified by the `dvowner_uname` parameter is made the Database Vault Account Manager and granted the `DV_ACCTMGR` role.                                                                                                                                                                       |
| `force_local_dvowner` | Applies only to the `DV_OWNER` (`dvowner_unname` user) in the CDB root or an application root in a multitenant environment. It does not apply to users who are created in a PDB.<br>• `TRUE` restricts the `DV_OWNER` role privileges of the `dvowner_unname` user to be local to the root.<br>• `FALSE`, the default setting,enables the `dvowner_unname` user to have `DV_OWNER` privileges for all containers that are associated with the root. |

#### Example

    CREATE USER c##dbv_owner_root_backup IDENTIFIED BY password CONTAINER = CURRENT;
    CREATE USER c##dbv_acctmgr_root_backup IDENTIFIED BY password CONTAINER = CURRENT;
    GRANT CREATE SESSION TO c##dbv_owner_root_backup, c##dbv_acctmgr_root_backup;

    BEGIN
     CONFIGURE_DV (
       dvowner_uname         => 'c##dbv_owner_root_backup',
       dvacctmgr_uname       => 'c##adbv_acctmgr_root_backup',
       force_local_dvowner   => TRUE);
     END;
    /

**Related Topics**

- [Deinstalling Oracle Database Vault](postinstallation-oracle-database-vault-procedures.md)
- [Reinstalling Oracle Database Vault](postinstallation-oracle-database-vault-procedures.md)
- [Getting Started with Oracle Database Vault](getting-started-with-oracle-database-vault.md)

**Parent topic:** Oracle Database Vault General Administrative APIs
