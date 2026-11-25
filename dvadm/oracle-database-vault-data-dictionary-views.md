You can find information about the Oracle Database Vault configuration settings by querying the Database Vault-specific data dictionary views.

- About the Oracle Database Vault Data Dictionary Views
  Oracle Database Vault provides a set of `DBA`-style data dictionary views that can be accessed through the `DV_SECANALYST` role or the `DV_ADMIN` role.
- CDB_DV_STATUS View
  The `CDB_DV_STATUS` data dictionary view shows the Database Vault operations control, configuration, and enablement status for all PDBs.
- DBA_DV_APP_EXCEPTION View
  The `DBA_DV_APP_EXCEPTION` data dictionary view lists the common schemas and package names that are in the Database Vault operations control exception list.
- DBA_DV_CODE View
  The `DBA_DV_CODE` data dictionary view lists generic lookup codes for the user interface, error messages, and constraint checking.
- DBA_DV_COMMAND_RULE View
  The `DBA_DV_COMMAND_RULE` data dictionary view lists the SQL statements that are protected by command rules.
- DBA_DV_DATAPUMP_AUTH View
  The `DBA_DV_DATAPUMP_AUTH` data dictionary view lists the authorizations for using Oracle Data Pump in an Oracle Database Vault environment.
- DBA_DV_DBCAPTURE_AUTH View
  The `DBA_DV_DBCAPTURE_AUTH` data dictionary view shows users who have been granted authorization to perform Oracle Database Replay workload capture operations.
- DBA_DV_DBREPLAY View
  The `DBA_DV_DBREPLAY_AUTH` data dictionary view shows users who have been granted authorization to perform Oracle Database Replay workload replay operations.
- DBA_DV_DDL_AUTH View
  The `DBA_DV_DDL` data dictionary view lists the users and schemas that were specified by the `DBMS_MACADM.AUTHORIZE_DDL` procedure.
- DBA_DV_DICTIONARY_ACCTS View
  The `DBA_DV_DICTIONARY_ACCTS` data dictionary view indicates whether users can directly log into the `DVSYS` and `DVF` schema accounts.
- DBA_DV_FACTOR View
  The `DBA_DV_FACTOR` data dictionary view lists the existing factors in the current database instance.
- DBA_DV_FACTOR_TYPE View
  The `DBA_DV_FACTOR_TYPE` data dictionary view lists the names and descriptions of factor types used in the system.
- DBA_DV_FACTOR_LINK View
  The `DBA_DV_FACTOR_LINK` data dictionary view shows the relationships of each factor whose identity is determined by the association of child factors.
- DBA_DV_IDENTITY View
  The `DBA_DV_IDENTITY` data dictionary view lists the identities for each factor.
- DBA_DV_IDENTITY_MAP View
  The `DBA_DV_IDENTITY_MAP` data dictionary view lists the mappings for each factor identity.
- DBA_DV_JOB_AUTH View
  The `DBA_DV_JOB_AUTH` data dictionary view lists the authorizations for using Oracle Scheduler in an Oracle Database Vault environment.
- DBA_DV_MAC_POLICY View
  The `DBA_DV_MAC_POLICY` data dictionary view lists the Oracle Label Security policies defined for use with Oracle Database Vault.
- DBA_DV_MAC_POLICY_FACTOR View
  The `DBA_DV_MAC_POLICY` data dictionary view lists the factors that are associated with Oracle Label Security policies.
- DBA_DV_MAINTENANCE_AUTH View
  The `DBA_DV_MAINTENANCE_AUTH` data dictionary view provides information about the configuration of Oracle Database Vault authorizations to use Information Life Management (ILM) features.
- DBA_DV_ORADEBUG View
  The `DBA_DV_ORADEBUG` data dictionary view indicates whether users can use the `ORADEBUG` utility in an Oracle Database Vault environment.
- DBA_DV_PATCH_ADMIN_AUDIT View
  The `DBA_DV_PATCH_ADMIN_AUDIT` data dictionary view indicates if auditing has been enabled or disabled for the user who has been granted the `DV_ADMIN_PATCH` role.
- DBA_DV_POLICY View
  The `DBA_DV_POLICY` data dictionary view lists the Oracle Database Vault policies that were created in the current database instance.
- DBA_DV_POLICY_LABEL View
  The `DBA_DV_POLICY_LABEL` data dictionary view lists the Oracle Label Security label for each factor identifier in the `DBA_DV_IDENTITY` view for each policy.
- DBA_DV_POLICY_OBJECT View
  The `DBA_DV_POLICY_OBJECT` data dictionary view lists information about the objects that are protected by Oracle Database Vault policies in the current database instance.
- DBA_DV_POLICY_OWNER View
  The `DBA_DV_POLICY_OWNER` data dictionary view lists the owners of Oracle Database Vault policies that were created in the current database instance.
- DBA_DV_PREPROCESSOR_AUTH View
  The `DBA_DV_PREPROCESSOR_AUTH` data dictionary view shows users who have been granted authorization to execute preprocessor programs through external tables.
- DBA_DV_PROXY_AUTH View
  The `DBA_DV_PROXY_AUTH` data dictionary view lists the proxy users and schemas that were specified by the `DBMS_MACADM.AUTHORIZE_PROXY_USER` procedure.
- DBA_DV_PUB_PRIVS View
  The `DBA_DV_PUB_PRIVS` data dictionary view lists data reflected in the Oracle Database Vault privilege management reports used in Oracle Database Vault Administrator.
- DBA_DV_REALM View
  The `DBA_DV_REALM` data dictionary view lists the realms created in the current database instance.
- DBA_DV_REALM_AUTH View
  The `DBA_DV_REALM_AUTH` data dictionary view lists database user account or role authorization (`GRANTEE`) who can access realm objects.
- DBA_DV_REALM_OBJECT View
  The `DBA_DV_REALM_OBJECT` data dictionary view lists the database schemas, or subsets of schemas, that are secured by the realms.
- DBA_DV_ROLE View
  The `DBA_DV_ROLE` data dictionary view lists the Oracle Database Vault secure application roles used in privilege management.
- DBA_DV_RULE View
  The `DBA_DV_RULE` data dictionary view lists the rules that have been defined.
- DBA_DV_RULE_SET View
  The `DBA_DV_RULE_SET` data dictionary view lists the rules sets that have been created.
- DBA_DV_RULE_SET_RULE View
  The `DBA_DV_RULE_SET_RULE` data dictionary view lists rules that are associated with existing rule sets.
- DBA_DV_SIMULATION_LOG View
  The `DBA_DV_SIMULATION_LOG` data dictionary view captures simulation log information for realms and command rules that have had simulation mode enabled.
- DBA_DV_STATUS or SYS.DBA_DV_STATUS View
  The `DBA_DV_STATUS` or `DBA_DV_STATUS` data dictionary view shows the status of Oracle Database Vault being enabled and configured.
- DBA_DV_TTS_AUTH View
  The `DBA_DV_TTS_AUTH` data dictionary view lists users who have been granted authorization through the `DBMS_MACADM.AUTHORIZE_TTS_USER` procedure to perform Oracle Data Pump transportable operations.
- DBA_DV_USER_PRIVS View
  The `DBA_DV_USER_PRIVS` data dictionary view lists the privileges for a database user account excluding privileges granted through the `PUBLIC` role.
- DBA_DV_USER_PRIVS_ALL View
  The `DBA_DV_USER_PRIVS_ALL` data dictionary view lists the privileges for a database account including privileges granted through `PUBLIC`.
- DVSYS.DV\$CONFIGURATION_AUDIT View
  The `DVSYS.DV$CONFIGURATION_AUDIT` data dictionary view captures `DVSYS.AUDIT_TRAIL$` table audit trail records.
- DVSYS.DV\$ENFORCEMENT_AUDIT View
  The `DVSYS.DV$ENFORCEMENT_AUDIT` data dictionary view provides information about enforcement-related audits from the `DVSYS.AUDIT_TRAIL$` table.
- DVSYS.DV\$REALM View
  The `DVSYS.DV$REALM` data dictionary view describes settings that were used to create Oracle Database Vault realms, such as which audit options have been assigned or whether the realm is a mandatory realm.
- DVSYS.POLICY_OWNER_COMMAND_RULE View
  The `DVSYS.POLICY_OWNER_COMMAND_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the command rules that have been associated with Database Vault policies.
- DVSYS.POLICY_OWNER_POLICY View
  The `DVSYS.POLICY_OWNER_POLICY` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information such as the names, descriptions, and states of existing policies in the current database instance, including policies created by other policy owners.
- DVSYS.POLICY_OWNER_REALM View
  The `POLICY_OWNER_REALM` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the realms that have been associated with Database Vault policies.
- DVSYS.POLICY_OWNER_REALM_AUTH View
  The `DVSYS.POLICY_OWNER_REALM_AUTH` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the authorization that was granted to realms that have been associated with Database Vault policies.
- DVSYS.POLICY_OWNER_REALM_OBJECT View
  The `DVSYS.POLICY_OWNER_REALM_OBJECT` data dictionary view enables users to find information about the objects that have been added to realms that are associated with Database Vault policies, such as. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.
- DVSYS.POLICY_OWNER_RULE View
  The `DVSYS.POLICY_OWNER_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rules that have been associated with rule sets in Database Vault policies, such as the rule name and its expression. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.
- DVSYS.POLICY_OWNER_RULE_SET View
  The `DVSYS.POLICY_OWNER_RULE_SET` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rule sets that have been associated with Database Vault policies.
- DVSYS.POLICY_OWNER_RULE_SET_RULE View
  The `DVSYS.POLICY_OWNER_RULE_SET_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rule sets that contain rules used in Database Vault policies.
- AUDSYS.DV\$CONFIGURATION_AUDIT View
  The `AUDSYS.DV$CONFIGURATION_AUDIT` view is almost the same as the `DVSYS.DV$CONFIGURATION_AUDIT` view except that it captures unified audit trail Database Vault audit records.
- AUDSYS.DV\$ENFORCEMENT_AUDIT View
  The `AUDSYS.DV$ENFORCEMENT_AUDIT` view is almost the same as the `DVSYS.DV$ENFORCEMENT_AUDIT` view except that it captures unified audit trail Database Vault audit records.

### 24.1 About the Oracle Database Vault Data Dictionary Views

Oracle Database Vault provides a set of `DBA`-style data dictionary views that can be accessed through the `DV_SECANALYST` role or the `DV_ADMIN` role.

These views provide access to the various underlying Oracle Database Vault tables in the `DVSYS` and `LBACSYS` schemas without exposing the primary and foreign key columns that may be present. These views are intended for the database administrative user to report on the state of the Oracle Database Vault configuration without having to perform the joins required to get the labels for codes that are stored in the core tables or from the related tables.

**See Also:**

[Oracle Database Vault Reports](oracle-database-vault-reports.md) if you are interested in running reports on Oracle Database Vault

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.2 CDB_DV_STATUS View

The `CDB_DV_STATUS` data dictionary view shows the Database Vault operations control, configuration, and enablement status for all PDBs.

Only Oracle Database administrative users, such users who have been granted the `DBA` role, can query this view. Database Vault administrators do not have access to this view.

For example:

    SELECT * FROM CDB_DV_STATUS;

Output similar to the following appears:

    NAME                 STATUS  CON_ID
    -------------------- ------- ------
    DV_APP_PROTECTION    ENABLED     5
    DV_CONFIGURE_STATUS  TRUE        5
    DV_ENABLE_STATUS     TRUE        5

#### Related Views

- DBA_DV_STATUS or SYS.DBA_DV_STATUS View

| Column   | Datatype           | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------|:-------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`   | `VARCHAR2(19)`     | `NOT NULL` | Shows either of the following settings:<br>• `DV_APP_PROTECTION` shows whether Database Vault operations control is enabled or not enabled.<br>• `DV_CONFIGURE_STATUS` shows whether Oracle Database Vault is configured (that is, with the `CONFIGURE_DV` procedure).<br>• `DV_ENABLE_STATUS` shows whether Oracle Database Vault is enabled (that is, with the `DBMS_MACADM.ENABLE_DV` procedure). |
| `STATUS` | `VARCHAR2(64)`     | `NOT NULL` | For `DV_CONFIGURE_STATUS` and `DV_ENABLE_STATUS`, `TRUE` means that Oracle Database Vault is configured or enabled; `FALSE` means that it is not. For `DV_APP_PROTECTION`, the output is `ENABLED` or `DISABLED`.                                                                                                                                                                                    |
| `CON_ID` | `NUMBER`           | `NOT NULL` | The identification number of the PDB container in which Oracle Database Vault is used                                                                                                                                                                                                                                                                                                                |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.3 DBA_DV_APP_EXCEPTION View

The `DBA_DV_APP_EXCEPTION` data dictionary view lists the common schemas and package names that are in the Database Vault operations control exception list.

You must query this view from the CDB root only. If you try to query this view from a pluggable database (PDB), then no output appears.

For example:

    SELECT * FROM DBA_DV_APP_EXCEPTION WHERE GRANTEE = 'C##HR_ADMIN';

Output similar to the following appears:

    GRANTEE       PACKAGE_NAME
    --------------- ------------
    C##HR_ADMIN     PATCH_APP

| Column         | Datatype               | Null       | Description                                                                                                                                  |
|:---------------|:-----------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE`      | `VARCHAR(128)`         | `NOT NULL` | Name of the grantee<br>To find the names of common users, query the `USERNAME` and `COMMON` columns of the `DBA_USERS` data dictionary view. |
| `PACKAGE_NAME` | `VARCHAR(128)`         | `NOT NULL` | Name of the package                                                                                                                          |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.4 DBA_DV_CODE View

The `DBA_DV_CODE` data dictionary view lists generic lookup codes for the user interface, error messages, and constraint checking.

These codes are used for the user interface, views, and for validating input in a translatable fashion.

For example:

    SELECT CODE, VALUE FROM DBA_DV_CODE WHERE CODE_GROUP = 'BOOLEAN';

Output similar to the following appears:

    CODE    VALUE
    ------- --------
    Y       True
    N       False

| Column        | Datatype            | Null       | Description                                                                                                                                                                                                                                                                                                                              |
|:--------------|:--------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CODE_GROUP`  | `VARCHAR(128)`      | `NOT NULL` | Displays one of the code groups that are listed in Table 24-1                                                                                                                                                                                                                                                                            |
| `CODE`        | `VARCHAR(128)`      | `NOT NULL` | Boolean code used; either `Y` (Yes) or `N` (No).                                                                                                                                                                                                                                                                                         |
| `VALUE`       | `VARCHAR(4000)`     | `NULL`     | Boolean value used; either `True` if the Boolean code is `Y` or `False` if the Boolean code is `N`.                                                                                                                                                                                                                                      |
| `LANGUAGE`    | `VARCHAR(3)`        | `NOT NULL` | Language for this installation of Oracle Database Vault.<br>Supported languages are as follows:<br>• `en`: English<br>• `de`: German<br>• `es`: Spanish<br>• `fr`: French<br>• `it`: Italian<br>• `ja`: Japanese<br>• `ko`: Korean<br>• `pt_BR`: Brazilian Portuguese<br>• `zh_CN`: Simplified Chinese<br>• `zh_TW`: Traditional Chinese |
| `DESCRIPTION` | `VARCHAR(1024)`     | `NULL`     | Brief description of the code group.                                                                                                                                                                                                                                                                                                     |

Table 24-1 describes the possible values from the `CODE_GROUP` column in the `DBA_DV_CODE` data dictionary view.

Table 24-1 DBA_DV_CODE View CODE_GROUP Values

| CODE_GROUP Name    | Description                                                                                                                                                                                                                                            |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUDIT_EVENTS`     | Contains the action numbers and action names that are used for the custom event audit trail records                                                                                                                                                    |
| `BOOLEAN`          | A simple Yes or No or True or False lookup                                                                                                                                                                                                             |
| `DB_OBJECT_TYPE`   | The database object types that can be used for realm objects and command authorizations                                                                                                                                                                |
| `SQL_CMDS`         | The DDL commands that can be protected through command rules                                                                                                                                                                                           |
| `FACTOR_AUDIT`     | The auditing options for factor retrieval processing                                                                                                                                                                                                   |
| `FACTOR_EVALUATE`  | The evaluation options (by session or by access) for factor retrieval                                                                                                                                                                                  |
| `FACTOR_FAIL`      | The options for propagating errors when a factor retrieval method fails                                                                                                                                                                                |
| `FACTOR_IDENTIFY`  | The options for determining how a factor identifier is resolved (for example, by method or by factors)                                                                                                                                                 |
| `FACTOR_LABEL`     | The options for determining how a factor identifier is labeled in the session establishment phase                                                                                                                                                      |
| `LABEL_ALG`        | The algorithms that can be used to determine the maximum session label for a database session for each policy. See [Table 19-2](oracle-database-vault-oracle-label-security-apis.md) for a listing of the Oracle Label Security merge algorithm codes. |
| `OPERATORS`        | The Boolean operators that can be used for identity maps                                                                                                                                                                                               |
| `REALM_AUDIT`      | The options for auditing realm access or realm violations                                                                                                                                                                                              |
| `REALM_OPTION`     | The options for ownership of a realm                                                                                                                                                                                                                   |
| `RULESET_AUDIT`    | The options for auditing rule set execution or rule set errors                                                                                                                                                                                         |
| `RULESET_EVALUATE` | The options for determining the success or failure of a rule set based on all associated rules being true or any associated rule being true                                                                                                            |
| `RULESET_EVENT`    | The options to invoke a custom event handler when a rule set evaluates to Succeeds or Fails                                                                                                                                                            |
| `RULESET_FAIL`     | The options to determine the run-time visibility of a rule set failing                                                                                                                                                                                 |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.5 DBA_DV_COMMAND_RULE View

The `DBA_DV_COMMAND_RULE` data dictionary view lists the SQL statements that are protected by command rules.

See [Configuring Command Rules](configuring-command-rules.md), for more information about command rules.

For example:

    SELECT COMMAND, RULE_SET_NAME FROM DBA_DV_COMMAND_RULE;

Output similar to the following appears:

    COMMAND         RULE_SET_NAME
    --------------- -----------------------------
    GRANT           Can Grant VPD Administration
    REVOKE          Can Grant VPD Administration
    ALTER SYSTEM    Allow System Parameters
    ALTER USER      Can Maintain Own Account
    CREATE USER     Can Maintain Account/Profiles
    DROP USER       Can Maintain Account/Profiles
    CREATE PROFILE  Can Maintain Account/Profiles
    DROP PROFILE    Can Maintain Account/Profiles
    ALTER PROFILE   Can Maintain Account/Profiles

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------------|:-----------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COMMAND`         | `VARCHAR(128)`         | `NOT NULL` | Name of the command rule. For a list of default command rules, see [Default Command Rules](configuring-command-rules.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `CLAUSE_NAME`     | `VARCHAR(100)`         | `NOT NULL` | A clause from either the `ALTER SYSTEM` or `ALTER SESSION` SQL statement, which was used to create the command rule. For example, you it could list the `SET` clause for the `ALTER SESSION` statement.<br>For a full list of possible clause values, see the following topics:<br>• [Table 16-2](oracle-database-vault-command-rule-apis.md)<br>• [Table 16-3](oracle-database-vault-command-rule-apis.md)                                                                                                                                                                                                                                                                          |
| `PARAMETER_NAME`  | `VARCHAR(128)`         | `NOT NULL` | A parameter from the `ALTER SYSTEM` or `ALTER SESSION` command rule `CLAUSE_NAME` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `EVENT_NAME`      | `VARCHAR(128)`         | `NOT NULL` | An event that the `ALTER SYSTEM` or `ALTER SESSION` command rule defines                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `COMPONENT_NAME`  | `VARCHAR(128)`         | `NOT NULL` | A component of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `ACTION_NAME`     | `VARCHAR(128)`         | `NOT NULL` | An action of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `RULE_SET_NAME`   | `VARCHAR(128)`         | `NOT NULL` | Name of the rule set associated with this command rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `OBJECT_OWNER`    | `VARCHAR(128)`         | `NOT NULL` | The owner of the object that the command rule affects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `OBJECT_NAME`     | `VARCHAR(128)`         | `NOT NULL` | The name of the database object the command rule affects (for example, a database table).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `ENABLED`         | `VARCHAR(1)`           | `NOT NULL` | Possible values are as follows:<br>• `Y` indicates the command rule is enabled<br>• `N` indicates it is disabled<br>• `S` indicates it is in simulation mode                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `PRIVILEGE_SCOPE` | `NUMBER`               | `NOT NULL` | Obsolete column                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `COMMON`          | `VARCHAR(3`)           | `NOT NULL` | For a multitenant environment, indicates whether the command rule is local or common. Possible values are:<br>• `YES` if the command rule is common<br>• `NO` if the command rule is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`       | `VARCHAR(3)`           | `NOT NULL` | Shows the inheritance status of the command rule, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the command rule was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the command rule is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the command rule, which is automatically generated when the command rule is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NULL`     | Indicates whether the command rule is a default (that is, Oracle-supplied) command rule or a user-created command rule. Possible values are:<br>• `YES` if the command rule is a default command rule<br>• `NO` if the command rule is a user-created command rule                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `PL_SQL_STACK`    | `VARCHAR(3)`           | `NULL`     | When simulation mode is enabled, indicates whether the PL/SQL stack has been recorded for failed operations. `TRUE` indicates that the PL/SQL stack has been recorded; `FALSE` indicates that the PL/SQL stack has not been recorded.                                                                                                                                                                                                                                                                                                                                                                                                                                                |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.6 DBA_DV_DATAPUMP_AUTH View

The `DBA_DV_DATAPUMP_AUTH` data dictionary view lists the authorizations for using Oracle Data Pump in an Oracle Database Vault environment.

See [Using Oracle Data Pump with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information.

For example:

    SELECT * FROM DBA_DV_DATAPUMP_AUTH WHERE GRANTEE = 'PRESTON';

Output similar to the following appears:

    GRANTEE SCHEMA OBJECT  TYPE  ACTION
    ------- ------ ------- –---- –----------
    PRESTON OE     ORDERS  %     CREATE_USER

| Column    | Datatype                  | Null       | Description                                                                                                                                        |
|:----------|:--------------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the user who has been granted Data Pump authorization                                                                                      |
| `SCHEMA`  | `VARCHAR2(128)`           | `NOT NULL` | Name of the schema on which the user `GRANTEE` is authorized to perform Data Pump operations                                                       |
| `OBJECT`  | `VARCHAR2(128)`           | `NOT NULL` | Name of the object within the schema specified by the `SCHEMA` parameter on which the `GRANTEE` user has Data Pump authorization (such as a table) |
| `TYPE`    | `VARCHAR2(32)`            | `NOT NULL` | For Oracle Data Pump import operations, indicates the type of grant, such as `ROLE`)                                                               |
| `ACTION`  | `VARCHAR2(30)`            | `NOT NULL` | For Oracle Data Pump import operations, indicates action that is associated with the `TYPE`: `%`, `TABLE`, `CREATE_USER`, or `GRANT`               |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.7 DBA_DV_DBCAPTURE_AUTH View

The `DBA_DV_DBCAPTURE_AUTH` data dictionary view shows users who have been granted authorization to perform Oracle Database Replay workload capture operations.

See [Using Oracle Database Replay with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information.

For example:

    SELECT * FROM DBA_DV_DBCAPTURE_AUTH WHERE GRANTEE = 'PFITCH';

Output similar to the following appears:

    GRANTEE
    -------
    PFITCH

| Column    | Datatype                  | Null       | Description                                                                          |
|:----------|:--------------------------|:-----------|:-------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the user who has been granted Database Replay workload capture authorization |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.8 DBA_DV_DBREPLAY View

The `DBA_DV_DBREPLAY_AUTH` data dictionary view shows users who have been granted authorization to perform Oracle Database Replay workload replay operations.

See [Using Oracle Database Replay with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information.

For example:

    SELECT * FROM DBA_DV_DBREPLAY_AUTH WHERE GRANTEE = 'PFITCH';

Output similar to the following appears:

    GRANTEE
    -------
    PFITCH

| Column    | Datatype                  | Null       | Description                                                                         |
|:----------|:--------------------------|:-----------|:------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the user who has been granted Database Replay workload replay authorization |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.9 DBA_DV_DDL_AUTH View

The `DBA_DV_DDL` data dictionary view lists the users and schemas that were specified by the `DBMS_MACADM.AUTHORIZE_DDL` procedure.

This procedure grants a user authorization to execute Data Definition Language (DDL) statements.

For example:

    SELECT * FROM DBA_DV_DDL_AUTH WHERE GRANTEE = 'psmith';

Output similar to the following appears:

    GRANTEE SCHEMA
    ------- ------
    PSMITH  HR

| Column    | Datatype                  | Null       | Description                                                                            |
|:----------|:--------------------------|:-----------|:---------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the user who has been granted DDL authorization                                |
| `SCHEMA`  | `VARCHAR2(128)`           | `NOT NULL` | Name of the schema on which the user `GRANTEE` is authorized to perform DDL operations |

**See Also:**

- [AUTHORIZE_DDL Procedure](oracle-database-vault-general-administrative-apis.md)

- [UNAUTHORIZE_DDL Procedure](oracle-database-vault-general-administrative-apis.md)

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.10 DBA_DV_DICTIONARY_ACCTS View

The `DBA_DV_DICTIONARY_ACCTS` data dictionary view indicates whether users can directly log into the `DVSYS` and `DVF` schema accounts.

For example:

    SELECT * FROM DBA_DV_DICTIONARY_ACCTS;

Output similar to the following appears:

    STATE
    -------
    ENABLED

| Column  | Datatype                  | Null       | Description                                                                                                                                                                                                                                                                   |
|:--------|:--------------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATE` | `VARCHAR2(8)`             | `NOT NULL` | Describes whether users can log directly into the `DVSYS` and `DVF` schemas. Possible values are:<br>• `ENABLED` means that users can log directly into the `DVSYS` and `DVF` schemas<br>• `DISABLED` means that users cannot log directly into the `DVSYS` and `DVF` schemas |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.11 DBA_DV_FACTOR View

The `DBA_DV_FACTOR` data dictionary view lists the existing factors in the current database instance.

For example:

    SELECT NAME, GET_EXPR FROM DBA_DV_FACTOR WHERE NAME = 'Session_User';

Output similar to the following appears:

    NAME          GET_EXPR
    ------------- ---------------------------------------------
    Session_User  UPPER(SYS_CONTEXT('USERENV', 'SESSION_USER'))

#### Related Views

- DBA_DV_FACTOR_LINK View

- DBA_DV_FACTOR_TYPE View

| Column                  | Datatype                  | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------------------|:--------------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`                  | `VARCHAR2(128)`           | `NOT NULL` | Name of the factor. See [Default Factors](configuring-factors.md) for a list of default factors.                                                                                                                                                                                                                                                                                                                                                                                          |
| `DESCRIPTION`           | `VARCHAR2(4000)`          | `NULL`     | Description of the factor.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `FACTOR_TYPE_NAME`      | `VARCHAR2(128)`           | `NOT NULL` | Category of the factor, which is used to classify the purpose of the factor.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `ASSIGN_RULE_SET_NAME`  | `VARCHAR2(128)`           | `NULL`     | Rule set used to control the identify of the factor.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `GET_EXPR`              | `VARCHAR2(1024)`          | `NULL`     | PL/SQL expression that retrieves the identity of a factor.                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `VALIDATE_EXPR`         | `VARCHAR2(1024)`          | `NULL`     | PL/SQL expression used to validate the identify of the factor. It returns a Boolean value.                                                                                                                                                                                                                                                                                                                                                                                                |
| `IDENTIFIED_BY`         | `NUMBER`                  | `NOT NULL` | Determines the identity of a factor, based on the expression listed in the `GET_EXPR` column. Possible values are:<br>• `0`: By constant<br>• `1`: By method<br>• `2`: By factors                                                                                                                                                                                                                                                                                                         |
| `IDENTIFIED_BY_MEANING` | `VARCHAR2(4000)`          | `NULL`     | Provides a text description for the corresponding value in the `IDENTIFIED_BY` column. Possible values are:<br>• `By Constant`: If `IDENTIFIED_COLUMN` is `0`<br>• `By Method`: If `IDENTIFIED_COLUMN` is `1`<br>• `By Factors`: If `IDENTIFIED_COLUMN` is `2`                                                                                                                                                                                                                            |
| `LABELED_BY`            | `NUMBER`                  | `NOT NULL` | Determines the labeling the factor:<br>• `0`: Labels the identities for the factor directly from the labels associated with an Oracle Label Security policy<br>• `1`: Derives the factor identity label from the labels of its child factor identities.                                                                                                                                                                                                                                   |
| `LABELED_BY_MEANING`    | `VARCHAR2(4000)`          | `NULL`     | Provides a text description for the corresponding value in the `LABELED_BY` column. Possible values are:<br>• `By Self`: If `LABELED_BY` column is `0`<br>• `By Factors`: If `LABELED_BY` column is `1`                                                                                                                                                                                                                                                                                   |
| `EVAL_OPTIONS`          | `NUMBER`                  | `NOT NULL` | Determines how the factor is evaluated when the user logs on:<br>• `0`: When the database session is created<br>• `1`: Each time the factor is accessed<br>• `2`: On start-up                                                                                                                                                                                                                                                                                                             |
| `EVAL_OPTIONS_MEANING`  | `VARCHAR2(4000)`          | `NULL`     | Provides a text description for the corresponding value in the `EVAL_OPTIONS` column. Possible values are:<br>• `For Session`: If `EVAL_OPTIONS` is `0`<br>• `By Access`: If `EVAL_OPTIONS` is `1`<br>• `On Startup`: If `EVAL_OPTIONS` is `2`                                                                                                                                                                                                                                            |
| `AUDIT_OPTIONS`         | `NUMBER`                  | `NOT NULL` | Option for auditing the factor if you want to generate a custom Oracle Database Vault audit record. Possible values are:<br>• `0`: No auditing set<br>• `1`: Always audits<br>• `2`: Audits if `get_expr` returns an error<br>• `4`: Audits if `get_expr` is null<br>• `8`: Audits if the validation procedure returns an error<br>• `16`: Audits if the validation procedure is false<br>• `32`: Audits if there is no trust level set<br>• `64`: Audits if the trust level is negative. |
| `FAIL_OPTIONS`          | `NUMBER`                  | `NOT NULL` | Options for reporting factor errors:<br>• `1`: Shows an error message.<br>• `2`: Does not show an error message.                                                                                                                                                                                                                                                                                                                                                                          |
| `FAIL_OPTIONS_MEANING`  | `VARCHAR2(4000)`          | `NULL`     | Provides a text description for the corresponding value in the `FAIL_OPTIONS` column. Possible values are:<br>• `Show Error Message`<br>• `Do Not Show Error Message`:                                                                                                                                                                                                                                                                                                                    |
| `ID#`                   | `NUMBER`                  | `NOT NULL` | The ID number of the factor, which is automatically generated when the factor is created                                                                                                                                                                                                                                                                                                                                                                                                  |
| `ORACLE_SUPPLIED`       | `VARCHAR(3)`              | `NOT NULL` | Indicates whether the factor is a default (that is, Oracle-supplied) factor or a user-created factor. Possible values are:<br>• `YES` if the factor is a default factor<br>• `NO` if the factor is a user-created factor                                                                                                                                                                                                                                                                  |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.12 DBA_DV_FACTOR_TYPE View

The `DBA_DV_FACTOR_TYPE` data dictionary view lists the names and descriptions of factor types used in the system.

For example:

    SELECT * FROM DBA_DV_FACTOR_TYPE WHERE NAME = 'Time';

Output similar to the following appears:

    NAME      DESCRIPTION
    --------- ----------------------------------------------------------------------
    Time      Time-based factor

#### Related Views

- DBA_DV_FACTOR View

- DBA_DV_FACTOR_LINK View

| Column        | Datatype              | Null       | Description                     |
|:--------------|:----------------------|:-----------|:--------------------------------|
| `NAME`        | `VARCHAR(128)`        | `NOT NULL` | Name of the factor type.        |
| `DESCRIPTION` | `VARCHAR(1024)`       | `NULL`     | Description of the factor type. |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.13 DBA_DV_FACTOR_LINK View

The `DBA_DV_FACTOR_LINK` data dictionary view shows the relationships of each factor whose identity is determined by the association of child factors.

This view contains one entry for each parent factor and child factor. You can use this view to resolve the relationships from the factor links to identity maps.

For example:

    SELECT PARENT_FACTOR_NAME, CHILD_FACTOR_NAME FROM DBA_DV_FACTOR_LINK;

Output similar to the following appears:

    PARENT_FACTOR_NAME             CHILD_FACTOR_NAME
    ------------------------------ ------------------------------
    Domain                         Database_Instance
    Domain                         Database_IP
    Domain                         Database_Hostname

#### Related Views

- DBA_DV_FACTOR View

- DBA_DV_FACTOR_TYPE View

| Column               | Datatype           | Null       | Description                                                                                                                                                                                                             |
|:---------------------|:-------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PARENT_FACTOR_NAME` | `VARCHAR(128)`     | `NOT NULL` | Name of the parent factor                                                                                                                                                                                               |
| `CHILD_FACTOR_NAME`  | `VARCHAR(128)`     | `NOT NULL` | Name of the child factor of the parent factor                                                                                                                                                                           |
| `LABEL_IND`          | `VARCHAR(1)`       | `NOT NULL` | Indicates whether the child factor that is linked to the parent factor contributes to the label of the parent factor in an Oracle Label Security integration. Possible values are:<br>• `Y` (for Yes)<br>• `N` (for No) |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.14 DBA_DV_IDENTITY View

The `DBA_DV_IDENTITY` data dictionary view lists the identities for each factor.

For example:

    SELECT * FROM DBA_DV_IDENTITY WHERE VALUE = 'GLOBAL SHARED';

Output similar to the following appears, assuming you have created only one factor identity:

    FACTOR_NAME          VALUE          TRUST_LEVEL
    ----------------     -------------- ------------
    Identification_Type  GLOBAL SHARED  1

#### Related Views

- DBA_DV_FACTOR View

- DBA_DV_IDENTITY_MAP View

| Column        | Datatype              | Null       | Description                                                                                    |
|:--------------|:----------------------|:-----------|:-----------------------------------------------------------------------------------------------|
| `FACTOR_NAME` | `VARCHAR(128)`        | `NOT NULL` | Name of the factor.                                                                            |
| `VALUE`       | `VARCHAR(1024)`       | `NOT NULL` | Value of the factor.                                                                           |
| `TRUST_LEVEL` | `NUMBER`              | `NOT NULL` | Number that indicates the magnitude of trust relative to other identities for the same factor. |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.15 DBA_DV_IDENTITY_MAP View

The `DBA_DV_IDENTITY_MAP` data dictionary view lists the mappings for each factor identity.

The view includes mapping factors that are identified by other factors to combinations of parent-child factor links. For each factor, the maps are joined by the `OR` operation, and for different factors, the maps are joined by the `AND` operation.

You can use this view to resolve the identity for factors that are identified by other factors (for example, a domain) or for factors that have continuous domains (for example, Age or Temperature).

For example:

    SELECT FACTOR_NAME, IDENTITY_VALUE FROM DBA_DV_IDENTITY_MAP;

Output similar to the following appears:

    FACTOR_NAME      IDENTITY_VALUE
    ---------------- --------------------
    Sector2_Program  Accounting-Sensitive

#### Related Views

- DBA_DV_FACTOR View

- DBA_DV_IDENTITY View

| Column               | Datatype                 | Null       | Description                                                                                                                                                                                                           |
|:---------------------|:-------------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FACTOR_NAME`        | `VARCHAR(128)`           | `NOT NULL` | Factor the identity map is for.                                                                                                                                                                                       |
| `IDENTITY_VALUE`     | `VARCHAR(1024)`          | `NOT NULL` | Value the factor assumes if the identity map evaluates to `TRUE`.                                                                                                                                                     |
| `OPERATION_CODE`     | `VARCHAR(128)`           | `NOT NULL` | Descriptive name of the operation in the `OPERATION_VALUE` column.                                                                                                                                                    |
| `OPERATION_VALUE`    | `VARCHAR(4000)`          | `NULL`     | Relational operator for the identity map (for example, \<, \>, =, and so on).                                                                                                                                         |
| `OPERAND1`           | `VARCHAR(1024)`          | `NULL`     | Left operand for the relational operator; refers to the low value you enter.                                                                                                                                          |
| `OPERAND2`           | `VARCHAR(1024)`          | `NULL`     | Right operand for the relational operator; refers to the high value you enter.                                                                                                                                        |
| `PARENT_FACTOR_NAME` | `VARCHAR(128)`           | `NULL`     | The parent factor link to which the map is related.                                                                                                                                                                   |
| `CHILD_FACTOR_NAME`  | `VARCHAR(128)`           | `NULL`     | The child factor link to which the map is related.                                                                                                                                                                    |
| `LABEL_IND`          | `VARCHAR(1)`             | `NULL`     | Indicates whether the child factor being linked to the parent factor contributes to the label of the parent factor in an Oracle Label Security integration. Possible values are:<br>• `Y` (for Yes)<br>• `N` (for No) |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.16 DBA_DV_JOB_AUTH View

The `DBA_DV_JOB_AUTH` data dictionary view lists the authorizations for using Oracle Scheduler in an Oracle Database Vault environment.

For example:

    SELECT * FROM DBA_DV_JOB_AUTH WHERE GRANTEE = 'PRESTON';

Output similar to the following appears:

    GRANTEE SCHEMA
    ------- ------
    PRESTON OE

| Column    | Datatype           | Null       | Description                                                                                         |
|:----------|:-------------------|:-----------|:----------------------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`    | `NOT NULL` | Name of the user who has been granted Oracle Scheduler authorization                                |
| `SCHEMA`  | `VARCHAR2(128)`    | `NOT NULL` | Name of the schema on which the user `GRANTEE` is authorized to perform Oracle Scheduler operations |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.17 DBA_DV_MAC_POLICY View

The `DBA_DV_MAC_POLICY` data dictionary view lists the Oracle Label Security policies defined for use with Oracle Database Vault.

For example:

    SELECT POLICY_NAME, ALGORITHM_CODE, ALGORITHM_MEANING
     FROM DBA_DV_MAC_POLICY;

Output similar to the following appears:

    POLICY_NAME     ALGORITHM_CODE    ALGORITHM_MEANING
    --------------- ----------------- --------------------------------
    ACCESS_DATA     LUI               Minimum Level/Union/Intersection

#### Related Views

- DBA_DV_MAC_POLICY_FACTOR View

- DBA_DV_POLICY_LABEL View

| Column              | Datatype              | Null       | Description                                                                                                                                                                                                 |
|:--------------------|:----------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`       | `VARCHAR(128)`        | `NOT NULL` | Name of the policy.                                                                                                                                                                                         |
| `ALGORITHM_CODE`    | `VARCHAR(128)`        | `NOT NULL` | Merge algorithm code used for the policy. See [Table 19-2](oracle-database-vault-oracle-label-security-apis.md) for a listing of algorithm codes.                                                           |
| `ALGORITHM_MEANING` | `VARCHAR(4000)`       | `NULL`     | Provides a text description for the corresponding value in the `ALGORITHM_CODE` column. See [Table 19-2](oracle-database-vault-oracle-label-security-apis.md) for a listing of algorithm code descriptions. |
| `ERROR_LABEL`       | `VARCHAR(4000)`       | `NULL`     | Label specified for initialization errors, to be set when a configuration error or run-time error occurs during session initialization.                                                                     |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.18 DBA_DV_MAC_POLICY_FACTOR View

The `DBA_DV_MAC_POLICY` data dictionary view lists the factors that are associated with Oracle Label Security policies.

You can use this view to determine what factors contribute to the maximum session label for each policy using the `DBA_DV_MAC_POLICY` view.

For example:

    SELECT * FROM DBA_DV_MAC_POLICY_FACTOR;

Output similar to the following appears:

    FACTOR_NAME    MAC_POLICY_NAME
    -------------- ------------------
    App_Host_Name  Access Locations

#### Related Views

- DBA_DV_MAC_POLICY View

- DBA_DV_POLICY_LABEL View

| Column            | Datatype             | Null       | Description                                                         |
|:------------------|:---------------------|:-----------|:--------------------------------------------------------------------|
| `FACTOR_NAME`     | `VARCHAR(128)`       | `NOT NULL` | Name of the factor                                                  |
| `MAC_POLICY_NAME` | `VARCHAR(128)`       | `NOT NULL` | Name of the Oracle Label Security policy associated with this facto |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.19 DBA_DV_MAINTENANCE_AUTH View

The `DBA_DV_MAINTENANCE_AUTH` data dictionary view provides information about the configuration of Oracle Database Vault authorizations to use Information Life Management (ILM) features.

For example:

    SELECT GRANTEE, ACTION STATE FROM DBA_DV_MAINTENANCE_AUTH;

Output similar to the following appears:

    GRANTEE                   ACTION
    ------------------------- --------
    PSMITH                    ILM

| Column        | Datatype              | Null       | Description                                      |
|:--------------|:----------------------|:-----------|:-------------------------------------------------|
| `GRANTEE`     | `VARCHAR(128)`        | `NOT NULL` | Name of the grantee                              |
| `SCHEMA`      | `VARCHAR(128)`        | `NOT NULL` | Schema name or `%` (for all schemas)             |
| `OBJECT`      | `VARCHAR(128)`        | `NOT NULL` | Object name or `%` (for all objects in a schema) |
| `OBJECT_TYPE` | `VARCHAR(30)`         | `NOT NULL` | Object type                                      |
| `ACTION`      | `VARCHAR(30)`         | `NOT NULL` | Maintenance action `ILM` for ILM operations      |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.20 DBA_DV_ORADEBUG View

The `DBA_DV_ORADEBUG` data dictionary view indicates whether users can use the `ORADEBUG` utility in an Oracle Database Vault environment.

For example:

    SELECT * FROM DBA_DV_ORADEBUG;

Output similar to the following appears:

    STATE
    --------
    DISABLED

| Column  | Datatype             | Null       | Description                                                                                                                                                                                                                                          |
|:--------|:---------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATE` | `VARCHAR2(8)`        | `NOT NULL` | Describes whether the `ORADEBUG` utility can be used in a Database Vault-enabled environment. Possible values are:<br>• `ENABLED` means that users can run the `ORADEBUG` utility<br>• `DISABLED` means that users cannot run the `ORADEBUG` utility |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.21 DBA_DV_PATCH_ADMIN_AUDIT View

The `DBA_DV_PATCH_ADMIN_AUDIT` data dictionary view indicates if auditing has been enabled or disabled for the user who has been granted the `DV_ADMIN_PATCH` role.

The `DBMS_MACADM.ENABLE_DV_PATCH_ADMIN_AUDIT` procedure enables this type of auditing.

For example:

    SELECT * FROM DBA_DV_PATCH_ADMIN_AUDIT;

Output similar to the following appears:

    STATE
    --------
    DISABLED

| Column  | Datatype             | Null       | Description                                                                                                                                                                                                                        |
|:--------|:---------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `STATE` | `VARCHAR2(8)`        | `NOT NULL` | Describes whether auditing has been enabled or disabled for the `DV_ADMIN_PATCH` role user. Possible values are:<br>• `ENABLED` means that the auditing has been enabled<br>• `DISABLED` means that the auditing has been disabled |

**See Also:**

- [ENABLE_DV_PATCH_ADMIN_AUDIT Procedure](oracle-database-vault-general-administrative-apis.md)

- [DISABLE_DV_PATCH_ADMIN_AUDIT Procedure](oracle-database-vault-general-administrative-apis.md)

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.22 DBA_DV_POLICY View

The `DBA_DV_POLICY` data dictionary view lists the Oracle Database Vault policies that were created in the current database instance.

For example:

    SELECT POLICY_NAME, STATE FROM DBA_DV_POLICY
      WHERE STATE = 'ENABLED';

Output similar to the following appears:

    POLICY_NAME                        STATE
    ---------------------------------- -------
    Oracle Account Management Controls ENABLED
    Oracle System Protection Controls  ENABLED

#### Related Views

- DBA_DV_POLICY_OWNER View

- DBA_DV_POLICY_OBJECT View

- DBA_DV_SIMULATION_LOG View

- DVSYS.POLICY_OWNER_POLICY View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                           |
|:------------------|:-----------------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`     | `VARCHAR(128)`         | `NOT NULL` | Names of the Oracle Database Vault policies that have been created. See [Default Oracle Database Vault Policies](configuring-oracle-database-vault-policies.md)for a listing of default policies.                                     |
| `DESCRIPTION`     | `VARCHAR(1024)`        | `NULL`     | Description of the policy that was created                                                                                                                                                                                            |
| `STATE`           | `VARCHAR(8)`           | `NULL`     | Specifies whether the policy is enabled. Possible values are:<br>• `ENABLED`<br>• `DISABLED`<br>• `SIMULATION`                                                                                                                        |
| `ID#`             | `VARCHAR(1)`           | `NOT NULL` | Is a system-generated ID that was assigned to the policy when the policy was created                                                                                                                                                  |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NULL`     | Indicates whether the policy is a default Oracle Database Vault policy                                                                                                                                                                |
| `PL_SQL_STACK`    | `VARCHAR(3)`           | `NULL`     | When simulation mode is enabled, indicates whether the PL/SQL stack has been recorded for failed operations. `TRUE` indicates that the PL/SQL stack has been recorded; `FALSE` indicates that the PL/SQL stack has not been recorded. |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.23 DBA_DV_POLICY_LABEL View

The `DBA_DV_POLICY_LABEL` data dictionary view lists the Oracle Label Security label for each factor identifier in the `DBA_DV_IDENTITY` view for each policy.

For example:

    SELECT * FROM DBA_DV_POLICY_LABEL;

Output similar to the following appears:

    IDENTITY_VALUE   FACTOR_NAME     POLICY_NAME       LABEL
    ---------------- --------------  ----------------  ---------
    App_Host_Name    Sect2_Fin_Apps  Access Locations  Sensitive

#### Related Views

- DBA_DV_MAC_POLICY View

- DBA_DV_MAC_POLICY_FACTOR View

| Column           | Datatype                | Null       | Description                                                           |
|:-----------------|:------------------------|:-----------|:----------------------------------------------------------------------|
| `IDENTITY_VALUE` | `VARCHAR(1024)`         | `NOT NULL` | Name of the factor identifier.                                        |
| `FACTOR_NAME`    | `VARCHAR(128)`          | `NOT NULL` | Name of the factor associated with the factor identifier.             |
| `POLICY_NAME`    | `VARCHAR(128)`          | `NOT NULL` | Name of the Oracle Label Security policy associated with this factor. |
| `LABEL`          | `VARCHAR(4000)`         | `NOT NULL` | Name of the Oracle Label Security label associated with the policy.   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.24 DBA_DV_POLICY_OBJECT View

The `DBA_DV_POLICY_OBJECT` data dictionary view lists information about the objects that are protected by Oracle Database Vault policies in the current database instance.

For example:

    SELECT POLICY_NAME, OBJECT_TYPE FROM DBA_DV_POLICY_OBJECT WHERE POLICY_NAME LIKE '%Protection Controls';

Output similar to the following appears:

    POLICY_NAME                        OBJECT_TYPE
    ---------------------------------- ------------
    Oracle System Protection Controls  REALM

#### Related Views

- DBA_DV_POLICY View

- DBA_DV_POLICY_OWNER View

| Column              | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:--------------------|:-----------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`       | `VARCHAR(128)`         | `NOT NULL` | Names of the Oracle Database Vault policies that have been created.<br>See [Default Oracle Database Vault Policies](configuring-oracle-database-vault-policies.md) for a listing of default policies.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `OBJECT_TYPE`       | `VARCHAR(12)`          | `NULL`     | Type of object that is being protected, such as `REALM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `COMMAND`           | `VARCHAR(128)`         | `NULL`     | Name of the command rules that are protected by Database Vault policies                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `COMMAND_OBJ_OWNER` | `VARCHAR(128)`         | `NULL`     | Names of object owners that are associated with Database Vault policies                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `COMMAND_OBJ_NAME`  | `VARCHAR(128)`         | `NULL`     | Names of objects that are associated with Database Vault policies                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `COMMAND_CLAUSE`    | `VARCHAR(100)`         | `NULL`     | A clause from either the `ALTER SYSTEM` or `ALTER SESSION` SQL statement, which was used to create the command rule. For example, you it could list the `SET` clause for the `ALTER SESSION` statement.<br>For a full list of possible clause values, see the following topics:<br>• [Table 16-2](oracle-database-vault-command-rule-apis.md)<br>• [Table 16-3](oracle-database-vault-command-rule-apis.md)                                                                                                                                                                                                                                                                             |
| `COMMAND_PARAMETER` | `VARCHAR(128)`         | `NULL`     | A parameter from the `ALTER SYSTEM` or `ALTER SESSION`command rule `CLAUSE_NAME` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `COMMAND_EVENT`     | `VARCHAR(128)`         | `NULL`     | An event that the `ALTER SYSTEM` or `ALTER SESSION` command rule defines                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `COMMAND_COMPONENT` | `VARCHAR(128)`         | `NULL`     | A component of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `COMMAND_ACTION`    | `VARCHAR(128)`         | `NULL`     | An action of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `COMMON`            | `VARCHAR(3)`           | `NULL`     | For a multitenant environment, indicates if the policy objects are local or common. Possible values are:<br>• `YES` if the policy objects are common<br>• `NO` if the policy objects are local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `INHERITED`         | `VARCHAR(3)`           | `NULL`     | Shows the inheritance status of the policy object, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the policy object was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the policy object is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.25 DBA_DV_POLICY_OWNER View

The `DBA_DV_POLICY_OWNER` data dictionary view lists the owners of Oracle Database Vault policies that were created in the current database instance.

For example:

    SELECT * FROM DBA_DV_POLICY_OWNER;

Output similar to the following appears:

    POLICY_OWNER                       POLICY_OWNER
    ---------------------------------- ------------
    Oracle System Protection Controls  PSMITH

#### Related Views

- DBA_DV_POLICY View

- DBA_DV_POLICY_OBJECT View

| Column         | Datatype               | Null       | Description                                                                                                                                                                                           |
|:---------------|:-----------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`  | `VARCHAR(128)`         | `NOT NULL` | Names of the Oracle Database Vault policies that have been created.<br>See [Default Oracle Database Vault Policies](configuring-oracle-database-vault-policies.md) for a listing of default policies. |
| `POLICY_OWNER` | `VARCHAR(128)`         | `NOT NULL` | Names of users who have own Database Vault policies                                                                                                                                                   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.26 DBA_DV_PREPROCESSOR_AUTH View

The `DBA_DV_PREPROCESSOR_AUTH` data dictionary view shows users who have been granted authorization to execute preprocessor programs through external tables.

See [Using Oracle Database Replay with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information.

For example:

    SELECT * FROM DBA_DV_PREPROCESSOR_AUTH WHERE GRANTEE = 'PFITCH';

Output similar to the following appears:

    GRANTEE
    -------
    PFITCH

| Column    | Datatype                  | Null       | Description                                                                          |
|:----------|:--------------------------|:-----------|:-------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the user who has been granted authorization to execute preprocessor programs |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.27 DBA_DV_PROXY_AUTH View

The `DBA_DV_PROXY_AUTH` data dictionary view lists the proxy users and schemas that were specified by the `DBMS_MACADM.AUTHORIZE_PROXY_USER` procedure.

This procedure grants a proxy user authorization to proxy other user accounts.

For example:

    SELECT * FROM DBA_DV_DDL_AUTH WHERE GRANTEE = 'PRESTON';

Output similar to the following appears:

    GRANTEE SCHEMA
    ------- ------
    PRESTON DKENT

| Column    | Datatype                  | Null       | Description                                               |
|:----------|:--------------------------|:-----------|:----------------------------------------------------------|
| `GRANTEE` | `VARCHAR2(128)`           | `NOT NULL` | Name of the proxy user                                    |
| `SCHEMA`  | `VARCHAR2(128)`           | `NOT NULL` | Name of the schema that is proxied by the `GRANTEE` user. |

**See Also:**

- [AUTHORIZE_PROXY_USER Procedure](oracle-database-vault-general-administrative-apis.md)

- [UNAUTHORIZE_PROXY_USER Procedure](oracle-database-vault-general-administrative-apis.md)

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.28 DBA_DV_PUB_PRIVS View

The `DBA_DV_PUB_PRIVS` data dictionary view lists data reflected in the Oracle Database Vault privilege management reports used in Oracle Database Vault Administrator.

See also [Privilege Management - Summary Reports](oracle-database-vault-reports.md).

For example:

    SELECT USERNAME, ACCESS_TYPE FROM DBA_DV_PUB_PRIVS WHERE USERNAME = 'OE';

Output similar to the following appears:

    USERNAME    ACCESS_TYPE
    ----------- -----------------
    OE          PUBLIC

#### Related Views

- DBA_DV_USER_PRIVS View

- DBA_DV_USER_PRIVS_ALL View

- DBA_DV_ROLE View

| Column        | Datatype             | Null       | Description                                                                              |
|:--------------|:---------------------|:-----------|:-----------------------------------------------------------------------------------------|
| `USERNAME`    | `VARCHAR(128)`       | `NOT NULL` | Database schema in the current database instance.                                        |
| `ACCESS_TYPE` | `VARCHAR(128)`       | `NULL`     | Access type granted to the user listed in the `USERNAME` column (for example, `PUBLIC`). |
| `PRIVILEGE`   | `VARCHAR(40`)        | `NOT NULL` | Privilege granted to the user listed in the `USERNAME` column.                           |
| `OWNER`       | `VARCHAR(128)`       | `NOT NULL` | Owner of the database schema to which the `USERNAME` user has been granted privileges.   |
| `OBJECT_NAME` | `VARCHAR(128)`       | `NOT NULL` | Name of the object within the schema listed in the `OWNER` column.                       |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.29 DBA_DV_REALM View

The `DBA_DV_REALM` data dictionary view lists the realms created in the current database instance.

For example:

    SELECT NAME, AUDIT_OPTIONS, ENABLED, COMMON FROM DBA_DV_REALM
      WHERE AUDIT_OPTIONS = '1';

Output similar to the following appears:

    NAME                          AUDIT_OPTIONS    ENABLED  COMMON
    ----------------------------- ---------------- -------- ------
    Performance Statistics Realm  1                Y        NO

#### Related Views

- DBA_DV_REALM_AUTH View

- DBA_DV_REALM_OBJECT View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------|:-----------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR(128)`         | `NOT NULL` | Names of the realms created. See[Default Realms](configuring-realms.md) for a listing of default realms.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DESCRIPTION`     | `VARCHAR(1024`)        | `NOT NULL` | Description of the realm created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `AUDIT_OPTIONS`   | `NUMBER`               | `NOT NULL` | Specifies whether auditing is enabled. Possible values are:<br>• `0`: No auditing for the realm.<br>• `1`: Creates an audit record when a realm violation occurs (for example, when an unauthorized user tries to modify an object that is protected by the realm).<br>• `2`: Creates an audit record for authorized activities on objects protected by the realm.<br>• `3`: Creates an audit record for both authorized and unauthorized activities on objects protected by the realm.                                                                                                                                                                         |
| `REALM_TYPE`      | `VARCHAR(9)`           | `NULL`     | Type of realm: whether it is a regular realm or a mandatory realm. See `realm_type` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON`          | `VARCHAR(3`)           | `NOT NULL` | For a multitenant environment, indicates whether the realm is local or common. Possible values are:<br>• `YES` if the realm is common<br>• `NO` if the realm is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`       | `VARCHAR(3)`           | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ENABLED`         | `VARCHAR(1)`           | `NOT NULL` | Possible values are as follows:<br>• `Y` indicates that realm checking is enabled<br>• `N` indicates it is disabled<br>• `S` indicates the realm is in simulation mode                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the realm, which is automatically generated when the realm is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NOT NULL` | Indicates whether the realm is a default (that is, Oracle-supplied) realm or a user-created command rule. Possible values are:<br>• `YES` if the realm is a default realm<br>• `NO` if the realm is a user-created realm                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `PL_SQL_STACK`    | `VARCHAR(3)`           | `NULL`     | When simulation mode is enabled, indicates whether the PL/SQL stack has been recorded for failed operations. `TRUE` indicates that the PL/SQL stack has been recorded; `FALSE` indicates that the PL/SQL stack has not been recorded.                                                                                                                                                                                                                                                                                                                                                                                                                           |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.30 DBA_DV_REALM_AUTH View

The `DBA_DV_REALM_AUTH` data dictionary view lists database user account or role authorization (`GRANTEE`) who can access realm objects.

See [About Realm Authorization](configuring-realms.md) for more information.

For example:

    SELECT REALM_NAME, GRANTEE, AUTH_RULE_SET_NAME FROM DBA_DV_REALM_AUTH;

Output similar to the following appears:

    REALM_NAME                    GRANTEE  AUTH_RULE_SET_NAME
    ---------------------------- --------- ---------------------
    Performance Statistics Realm  SYSADM   Check Conf Access

#### Related Views

- DBA_DV_REALM View

- DBA_DV_REALM_OBJECT View

| Column               | Datatype                 | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:---------------------|:-------------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `REALM_NAME`         | `VARCHAR(128)`           | `NULL`     | Name of the realm.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON_REALM`       | `VARCHAR(3)`             | `NULL`     | For a multitenant environment, indicates whether the realm is local or common. Possible values are:<br>• `YES` if the realm is common<br>• `NO` if the realm is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED_REALM`    | `VARCHAR(3)`             | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `GRANTEE`            | `VARCHAR(128)`           | `NOT NULL` | User or role name to authorize as owner or participant.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AUTH_RULE_SET_NAME` | `VARCHAR(128`)           | `NULL`     | Rule set to check before authorizing. If the rule set evaluates to `TRUE`, then the authorization is allowed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `AUTH_OPTIONS`       | `VARCHAR(4000)`          | `NULL`     | Type of realm authorization: either `Participant` or `Owner`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `COMMON_AUTH`        | `VARCHAR(3)`             | `NULL`     | For a multitenant environment, indicates whether the authorization to the common realm is local or common. Possible values are:<br>• `YES` if the authorization is common<br>• `NO` if the authorization is local to this PDB                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `INHERITED_AUTH`     | `VARCHAR(3)`             | `NULL`     | Shows the inheritance status of the realm authorization, when the `COMMON_AUTH` column output is `YES`. Values are as follows:<br>• `YES` means that the realm authorization was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was applied.<br>• `NO` means that the realm authorization is local, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED_AUTH` value `NO` but a CDB root common command rule will have an `INHERITED_AUTH` value of `YES`.                         |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.31 DBA_DV_REALM_OBJECT View

The `DBA_DV_REALM_OBJECT` data dictionary view lists the database schemas, or subsets of schemas, that are secured by the realms.

See [About Realm-Secured Objects](configuring-realms.md) for more information.

For example:

    SELECT REALM_NAME, OWNER, OBJECT_NAME, COMMON_REALM FROM DBA_DV_REALM_OBJECT;

Output similar to the following appears:

    REALM_NAME                   OWNER    OBJECT_NAME COMMON_REALM
    ---------------------------- -------- ----------- ------------
    Performance Statistics Realm OE       ORDERS      NO

#### Related Views

- DBA_DV_REALM View

- DBA_DV_REALM_AUTH View

| Column            | Datatype            | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------|:--------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `REALM_NAME`      | `VARCHAR(128)`      | `NOT NULL` | Name of the realm.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `COMMON_REALM`    | `VARCHAR(3)`        | `NOT NULL` | Indicates whether this realm is a common realm or a local realm. Possible values are:<br>• `YES` if the realm is common<br>• `NO` if the realm is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `INHERITED_REALM` | `VARCHAR(3)`        | `NOT NULL` | Shows the inheritance status of the realm when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `OWNER`           | `VARCHAR(128)`      | `NOT NULL` | Database schema owner who owns the object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `OBJECT_NAME`     | `VARCHAR(128)`      | `NOT NULL` | Name of the object the realm protects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `OBJECT_TYPE`     | `VARCHAR(32)`       | `NOT NULL` | Type of object the realm protects, such as a database table, view, index, or role.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.32 DBA_DV_ROLE View

The `DBA_DV_ROLE` data dictionary view lists the Oracle Database Vault secure application roles used in privilege management.

For example:

    SELECT ROLE, RULE_NAME FROM DBA_DV_ROLE;

Output similar to the following appears:

    ROLE               RULE_NAME
    ------------------ --------------------
    Sector2_APP_MGR    Check App2 Access
    Sector2_APP_DBA    Check App2 Access

#### Related Views

- DBA_DV_PUB_PRIVS View

- DBA_DV_USER_PRIVS View

- DBA_DV_USER_PRIVS_ALL View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                        |
|:------------------|:-----------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ROLE`            | `VARCHAR(128)`         | `NOT NULL` | Name of the secure application role.                                                                                                                                                                                                                               |
| `RULE_NAME`       | `VARCHAR(128)`         | `NOT NULL` | Name of the rule set associated with the secure application role.                                                                                                                                                                                                  |
| `ENABLED`         | `VARCHAR(1)`           | `NOT NULL` | Indicates whether the secure application role is enabled. Possible values are:<br>• `Y` (Yes) if the role is enabled<br>• `N` (No) if the role is disabled                                                                                                         |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the command rule, which is automatically generated when the command rule is created                                                                                                                                                               |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NOT NULL` | Indicates whether the command rule is a default (that is, Oracle-supplied) command rule or a user-created command rule. Possible values are:<br>• `YES` if the command rule is a default command rule<br>• `NO` if the command rule is a user-created command rule |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.33 DBA_DV_RULE View

The `DBA_DV_RULE` data dictionary view lists the rules that have been defined.

For example:

    SELECT NAME, RULE_EXPR FROM DBA_DV_RULE WHERE NAME = 'Maintenance Window';

Output similar to the following appears:

    NAME                RULE_EXP
    ------------------- ----------------------------------------------
    Maintenance Window  TO_CHAR(SYSDATE,'HH24') BETWEEN '10' AND '12'

To find the rule sets that use specific rules, query the `DBA_DV_RULE_SET_RULE` view.

#### Related Views

- DBA_DV_RULE_SET View

- DBA_DV_RULE_SET_RULE View

| Column            | Datatype              | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------|:----------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR(128)`        | `NOT NULL` | Name of the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `RULE_EXPR`       | `VARCHAR(1024)`       | `NOT NULL` | PL/SQL expression for the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON`          | `VARCHAR(3`)          | `NOT NULL` | For a multitenant environment, indicates whether the rule is local or common. Possible values are:<br>• `YES` if the rule is common<br>• `NO` if the rule is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`       | `VARCHAR(3`)          | `NULL`     | Shows the inheritance status of the rule, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the rule was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the rule is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ID#`             | `NUMBER`              | `NOT NULL` | The ID number of the rule, which is automatically generated when the rule is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`          | `NULL`     | Indicates whether the rule is a default (that is, Oracle-supplied) rule or a user-created rule. Possible values are:<br>• `YES` if the rule is a default rule<br>• `NO` if the rule is a user-created rule                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.34 DBA_DV_RULE_SET View

The `DBA_DV_RULE_SET` data dictionary view lists the rules sets that have been created.

For example:

    SELECT RULE_SET_NAME, HANDLER_OPTIONS, HANDLER FROM DBA_DV_RULE_SET
     WHERE RULE_SET_NAME = 'Maintenance Period';

Output similar to the following appears:

    RULE_SET_NAME       HANDLER_OPTIONS  HANDLER
    ------------------- ---------------- ----------------------
    Maintenance Period                   1 dbavowner.email_alert

#### Related Views

- DBA_DV_RULE View

- DBA_DV_RULE_SET_RULE View

| Column                 | Datatype                | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------------|:------------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RULE_SET_NAME`        | `VARCHAR(128)`          | `NOT NULL` | Name of the rule set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DESCRIPTION`          | `VARCHAR(1024)`         | `NULL`     | Description of the rule set.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `ENABLED`              | `VARCHAR(1)`            | `NOT NULL` | Indicates whether the rule set has been enabled. `Y` (Yes) enables the rule set; `N` (No) disables it.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `EVAL_OPTIONS_MEANING` | `VARCHAR(4000)`         | `NULL`     | For rules sets that contain multiple rules, determines how many rules are evaluated. Possible values are:<br>• `All True`: All rules in the rule set must evaluate to true for the rule set itself to evaluate to `TRUE`.<br>• `Any True`: At least one rule in the rule set must evaluate to true for the rule set itself to evaluate to `TRUE`.                                                                                                                                                                                                                                                                                                                        |
| `AUDIT_OPTIONS`        | `NUMBER`                | `NOT NULL` | Indicates when auditing is used. Possible values are:<br>• `0`: No auditing<br>• `1`: Audit on failure<br>• `2`: Audit on success<br>• `3`: Audit on both failure and success                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `FAIL_OPTIONS_MEANING` | `VARCHAR(4000)`         | `NULL`     | Determines when an audit record is created for the rule set. Possible values are:<br>• `Do Not Show Error Message`.<br>• `Show Error Message`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `FAIL_MESSAGE`         | `VARCHAR(80)`           | `NULL`     | Error message for failure that is associated with the fail code listed in the `FAIL_CODE` column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `FAIL_CODE`            | `VARCHAR(10)`           | `NULL`     | The error message number associated with the message listed in the `FAIL_MESSAGE` column. Possible values are in the ranges of -20000 to -20999 or 20000 to 20999.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `HANDLER_OPTIONS`      | `NUMBER`                | `NOT NULL` | Determines how error handling is used. Possible values are:<br>• `0`: Disables error handling.<br>• `1`: Call handler on rule set failure.<br>• `2`: Call handler on rule set success.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `HANDLER`              | `VARCHAR(1024)`         | `NULL`     | Name of the PL/SQL function or procedure that defines the custom event handler logic.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `IS_STATIC`            | `VARCHAR2(5)`           | `NULL`     | Indicates how often the rule set is evaluated during a user session. Possible values are:<br>• `TRUE`: The rule set is evaluated once, and result of the rule set is reused throughout the user session.<br>• `FALSE` (default): The rule set is evaluated each time it is accessed during the user session.                                                                                                                                                                                                                                                                                                                                                             |
| `COMMON`               | `VARCHAR2(3)`           | `NULL`     | For a multitenant environment, indicates whether the rule set is local or common. Possible values are:<br>• `YES` if the rule set is common<br>• `NO` if the rule set is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`            | `VARCHAR2(3)`           | `NULL`     | Shows the inheritance status of the rule set, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the rule set was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the rule set is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ID#`                  | `NUMBER)`               | `NOT NULL` | The ID number of the rule set, which is automatically generated when the rule set is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `ORACLE_SUPPLIED`      | `VARCHAR2(3)`           | `NULL`     | Indicates whether the rule set is a default (that is, Oracle-supplied) rule set or a user-created rule set. Possible values are:<br>• `YES` if the rule set is a default rule set<br>• `NO` if the rule set is a user-created rule set                                                                                                                                                                                                                                                                                                                                                                                                                                   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.35 DBA_DV_RULE_SET_RULE View

The `DBA_DV_RULE_SET_RULE` data dictionary view lists rules that are associated with existing rule sets.

For example:

    SELECT RULE_SET_NAME, RULE_NAME, RULE_EXPR FROM DBA_DV_RULE_SET_RULE
     WHERE RULE_NAME = 'Is Security Officer';

Output similar to the following appears:

    RULE_SET_NAME                RULE_NAME          RULE_EXP
    ---------------------------- ------------------ ---------------------------------
    Can Grant VPD Administration Is Security Owner  DBMS_MACUTL.USER_HAS_ROLE_VARCHAR
                                                    ('DV_OWNER',
                                                      dvsys.dv_login_user) = 'Y'


#### Related Views

- DBA_DV_RULE View

- DBA_DV_RULE_SET View

| Column          | Datatype              | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------|:----------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RULE_SET_NAME` | `VARCHAR(128)`        | `NOT NULL` | Name of the rule set that contains the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `RULE_NAME`     | `VARCHAR(128)`        | `NOT NULL` | Name of the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `RULE_EXPR`     | `VARCHAR(1024)`       | `NOT NULL` | PL/SQL expression that defines the rule listed in the `RULE_NAME` column.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `ENABLED`       | `VARCHAR(1)`          |            | Indicates whether the rule is enabled or disabled. `Y` (Yes) enables the rule set; `N` (No) disables it.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `RULE_ORDER`    | `NUMBER`              | `NOT NULL` | The order in which rules are used within the rule set. Does not apply to this release.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `COMMON`        | `VARCHAR(3`)          | `NOT NULL` | For a multitenant environment, indicates whether the rule is local or common. Possible values are:<br>• `YES` if the rule is common<br>• `NO` if the rule is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`     | `VARCHAR(3)`          | `NOT NULL` | Shows the inheritance status of the rule, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the rule was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the rule is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.36 DBA_DV_SIMULATION_LOG View

The `DBA_DV_SIMULATION_LOG` data dictionary view captures simulation log information for realms and command rules that have had simulation mode enabled.

For example:

    SELECT USERNAME, COMMAND
    FROM DBA_DV_SIMULATION_LOG, TABLE(DBA_DV_SIMULATION_LOG.REALM_NAME) RN
    WHERE RN.COLUMN_VALUE = 'HR Realm';

Output similar to the following appears:

    USERNAME      COMMAND
    ------------- ---------------------------------------------
    PSMITH        SELECT

#### Related Views

- DBA_DV_REALM View for information about simulation mode settings for realms

- DBA_DV_COMMAND_RULE View for information about simulation mode settings for command rules

- DBA_DV_POLICY View for information about simulation mode settings in Oracle Database Vault policies

| Column                      | Datatype                      | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------|:------------------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ID`                        | `NUMBER`                      | `NOT NULL` | Simulation log ID                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `USERNAME`                  | `VARCHAR2(128)`               | `NOT NULL` | Name of the user whose information is being tracked                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `COMMAND`                   | `VARCHAR2(128)`               | `NOT NULL` | Command rule being tracked<br>For a listing of existing command rules, query the `DBA_DV_COMMAND_RULE` view, described in DBA_DV_COMMAND_RULE View.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `VIOLATION_TYPE`            | `VARCHAR2(4000)`              | `NULL`     | Type of violation. See Table 24-2 for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `REALM_NAME`                | `DVSYS.DV_OBJ_NAME`           | `NULL`     | Realm being tracked. The data type, `DVSYS.DV_OBJ_NAME`, is a nested list object that allows the capture of multiple realms in the query.<br>For a listing of existing realms, query the `DBA_DV_REALM` view, described in DBA_DV_REALM View.                                                                                                                                                                                                                                                                                                                                          |
| `REALM_TYPE`                | `VARCHAR2(9)`                 | `NULL`     | Type of realm being tracked (for example, mandatory realms).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `OBJECT_OWNER`              | `VARCHAR2(128)`               | `NULL`     | For command rules, the database schema to which the command rule applied                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `OBJECT_NAME`               | `VARCHAR2(128)`               | `NULL`     | For command rules, the database object that the command rule protects                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `OBJECT_TYPE`               | `VARCHAR2(129)`               | `NULL`     | For command rules, the type of object that is being protected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `RULE_SET_NAME`             | `DVSYS.DV_OBJ_NAME`           | `NULL`     | Rule set being tracked; it is associated with a command rule. The data type, `DVSYS.DV_OBJ_NAME`, is a nested list object that allows the capture of multiple rule sets in the query.<br>For a listing of existing rule sets, query the `DBA_DV_RULE_SET` view, described in DBA_DV_RULE_SET View                                                                                                                                                                                                                                                                                      |
| `RETURNCODE`                | `NUMBER`                      | `NOT NULL` | The Oracle Database `ORA` error that results if the Database Vault entity was in the enabled state rather than in simulation state                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `SQLTEXT`                   | `VARCHAR2(4000)`              | `NULL`     | SQL text that the simulation mode captures                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `AUTHENTICATION_METHOD`     | `VARCHAR2(10)`                | `NULL`     | Authentication method used. See [Default Factors](configuring-factors.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `CLIENT_IP`                 | `VARCHAR2(45)`                | `NULL`     | The IP address of the machine from which the client is connected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `DB_DOMAIN`                 | `VARCHAR2(128)`               | `NULL`     | The domain of the database as specified in the `DB_DOMAIN` initialization parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `DATABASE_HOSTNAME`         | `VARCHAR2(128)`               | `NULL`     | The host name of the computer on which the instance is running                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `DATABASE_INSTANCE`         | `VARCHAR2(5)`                 | `NULL`     | The instance identification number of the current instance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `DATABASE_IP`               | `VARCHAR2(45)`                | `NULL`     | The IP address of the computer on which the instance is running                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DATABASE_NAME`             | `VARCHAR2(128)`               | `NULL`     | The name of the database as specified in the `DB_NAME` initialization parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DOMAIN`                    | `VARCHAR2(4000)`              | `NULL`     | A named collection of physical, configuration, or implementation-specific factors in the run-time environment. See [Default Factors](configuring-factors.md).                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `ENTERPRISE_IDENTITY`       | `VARCHAR2(1024)`              | `NULL`     | The enterprise-wide identity for the user. See [Default Factors](configuring-factors.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `IDENTIFICATION_TYPE`       | `VARCHAR2(14)`                | `NULL`     | The way the user schema was created in the database. See [Default Factors](configuring-factors.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `LANG`                      | `VARCHAR2(10)`                | `NULL`     | The ISO abbreviation for the language name, a shorter form than the existing `LANGUAGE` parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `LANGUAGE`                  | `VARCHAR2(100)`               | `NULL`     | The language and territory your session currently uses, along with the database character set. See [Default Factors](configuring-factors.md).                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `MACHINE`                   | `VARCHAR2(64)`                | `NULL`     | The host name for the database client that established the current session. If you must find out whether the computer was used for a client or server session, then you can compare this setting with the Database_Hostname factor to make the determination                                                                                                                                                                                                                                                                                                                           |
| `NETWORK_PROTOCOL`          | `VARCHAR2(4)`                 | `NULL`     | The network protocol being used for communication, as specified in the `PROTOCOL=protocol` portion of the connect string                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `PROXY_ENTERPRISE_IDENTITY` | `VARCHAR2(1024)`              | `NULL`     | The Oracle Internet Directory DN when the proxy user is an enterprise user                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `PROXY_USER`                | `VARCHAR2(128)`               | `NULL`     | The name of the database user who opened the current session on behalf of `SESSION_USER`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `SESSION_USER`              | `VARCHAR2(128)`               | `NULL`     | The database user name by which the current user is authenticated. This value remains the same throughout the session.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `DV$_DBLINK_INFO`           | `VARCHAR2(128)`               | `NULL`     | Returns the source of a database link session. The string that it returns has this form:<br>`SOURCE_GLOBAL_NAME=``dblink_src_global_name``, `<br>`DBLINK_NAME=``dblink_name``,`<br>`SOURCE_AUDIT_SESSIONID=``dblink_src_audit_sessionid`<br>In this specification:<br>• `dblink_src_global_name` is the unique global name of the source database<br>• `dblink_name` is the name of the database link on the source database<br>• `dblink_src_audit_sessionid` source database that initiated source database that initiated the connection to the remote database using `dblink_name` |
| `DV$_MODULE`                | `VARCHAR2(64)`                | `NULL`     | The application name (module) that was set through the `DBMS_APPLICATION_INFO` PL/SQL package or Oracle Call Interface (OCI).                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `DV$_CLIENT_IDENTIFIER`     | `VARCHAR2(64)`                | `NULL`     | Returns an identifier that is set by the application through the `DBMS_SESSION.SET_IDENTIFIER` procedure, the OCI attribute `OCI_ATTR_CLIENT_IDENTIFIER`, or Oracle Dynamic Monitoring Service (DMS). Various Oracle Database components use this attribute to identify lightweight application users who authenticate as the same database user.                                                                                                                                                                                                                                      |
| `FACTOR_CONTEXT`            | `VARCHAR2(4000)`              | `NULL`     | An XML document that contains all of the factor identifiers for the current session at the point when the audit event was triggered                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `TIMESTAMP`                 | `TIMESTAMP(6) WITH TIME ZONE` | `NULL`     | Time stamp of user action, in UTC (Coordinated Universal Time) time zone                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `PL_SQL_STACK`              | `CLOB`                        | `NULL`     | When simulation mode is enabled, indicates whether the PL/SQL stack has been recorded for failed operations. `TRUE` indicates that the PL/SQL stack has been recorded; `FALSE` indicates that the PL/SQL stack has not been recorded.                                                                                                                                                                                                                                                                                                                                                  |

#### VIOLATION_TYPE Code Values

Table 24-2 lists the `VIOLATION_TYPE` code values for the `DBA_DV_SIMULATION_LOG` view.

Table 24-2 DBA_DV_SIMULATION_LOG VIOLATION_TYPE Code Values

| Code   | Meaning                                  |
|:-------|:-----------------------------------------|
| `1000` | Realm violation                          |
| `1001` | Command rule violation                   |
| `1002` | Oracle Data Pump authorization violation |
| `1003` | Simulation violation                     |
| `1004` | Oracle Scheduler authorization violation |
| `1005` | DDL authorization violation              |
| `1006` | `PARSE_AS_USER` violation                |

**Related Topics**

- [Using Simulation Mode for Logging Realm and Command Rule Activities](using-training-mode-to-log-realm-and-command-rule-activities.md)

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.37 DBA_DV_STATUS or SYS.DBA_DV_STATUS View

The `DBA_DV_STATUS` or `DBA_DV_STATUS` data dictionary view shows the status of Oracle Database Vault being enabled and configured.

How you query the `DBA_DV_STATUS` and `DBA_DV_STATUS` data dictionary views depends on the privileges that you have.

- If you are connected as a user who has the `DBA` role or the `SYSDBA` administrative privilege, then query `DBA_DV_STATUS`. For example:

      SELECT * FROM DBA_DV_STATUS;

- If you are connected as a user who has the `DV_OWNER` or `DV_ADMIN` role, then prepend `DBA_DV_STATUS` with `SYS.`. For example:

      SELECT * FROM SYS.DBA_DV_STATUS;

Output similar to the following appears:

    NAME               STATUS
    -------------------- --------------
    DV_APP_PROTECTION    NOT CONFIGURED
    DV_CONFIGURE_STATUS  TRUE
    DV_ENABLE_STATUS     TRUE

#### Related Views

- CDB_DV_STATUS View

| Column   | Datatype           | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                            |
|:---------|:-------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`   | `VARCHAR2(19)`     | `NOT NULL` | Shows one of the following settings:<br>• `DV_APP_PROTECTION` shows whether Database Vault operations control has been configured or not configured<br>• `DV_CONFIGURE_STATUS` shows whether Oracle Database Vault has been configured, that is, with the `CONFIGURE_DV` procedure.<br>• `DV_ENABLE_STATUS` shows whether Oracle Database Vault has been enabled, that is, with the `DBMS_MACADM.ENABLE_DV` procedure. |
| `STATUS` | `VARCHAR2(64)`     | `NOT NULL` | `TRUE` means that Oracle Database Vault is configured or enabled; `FALSE` means that it is not. For `DV_APP_PROTECTION`, it shows either `CONFIGURED` or `NOT CONFIGURED`.                                                                                                                                                                                                                                             |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.38 DBA_DV_TTS_AUTH View

The `DBA_DV_TTS_AUTH` data dictionary view lists users who have been granted authorization through the `DBMS_MACADM.AUTHORIZE_TTS_USER` procedure to perform Oracle Data Pump transportable operations.

See [Using Oracle Data Pump with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md) for more information.

For example:

    SELECT * FROM DBA_DV_TTS_AUTH;

Output similar to the following appears:

    GRANTEE  TSNAME
    -------- --------
    DB_MGR   HR_TS

#### Related Views

- DBA_DV_DATAPUMP_AUTH View

| Column    | Datatype             | Null       | Description                                                                                     |
|:----------|:---------------------|:-----------|:------------------------------------------------------------------------------------------------|
| `GRANTEE` | `VARCHAR(128)`       | `NOT NULL` | Name of the user who has been granted transportable tablespace authorization                    |
| `TSNAME`  | `VARCHAR(128)`       | `NOT NULL` | Name of the transportable tablespace to which the `GRANTEE` user has been granted authorization |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.39 DBA_DV_USER_PRIVS View

The `DBA_DV_USER_PRIVS` data dictionary view lists the privileges for a database user account excluding privileges granted through the `PUBLIC` role.

For example:

    SELECT USERNAME, ACCESS_TYPE, PRIVILEGE FROM DBA_DV_USER_PRIVS;

Output similar to the following appears:

    USERNAME  ACCESS_TYPE          PRIVILEGE
    --------- -------------------- ------------
    DVSYS     DV_PUBLIC            EXECUTE
    DVOWNER   DV_ADMIN             SELECT
    SYS       SELECT_CATALOG_ROLE  SELECT
    ...

#### Related Views

- DBA_DV_PUB_PRIVS View

- DBA_DV_ROLE View

- DBA_DV_USER_PRIVS_ALL View

| Column        | Datatype             | Null       | Description                                                                                                                                    |
|:--------------|:---------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`    | `VARCHAR(128)`       | `NOT NULL` | Name of the database schema account in which privileges have been defined.                                                                     |
| `ACCESS_TYPE` | `VARCHAR(128)`       | `NULL`     | Role the database user account listed in the `USERNAME` column uses to access the database. Oracle Database Vault accounts have direct access. |
| `PRIVILEGE`   | `VARCHAR(40)`        | `NOT NULL` | Privilege granted to the user listed in the `USERNAME` column.                                                                                 |
| `OWNER`       | `VARCHAR(128)`       | `NOT NULL` | Name of the database user account.                                                                                                             |
| `OBJECT_NAME` | `VARCHAR(128)`       | `NOT NULL` | Name of the PL/SQL function or procedure used to define privileges.                                                                            |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.40 DBA_DV_USER_PRIVS_ALL View

The `DBA_DV_USER_PRIVS_ALL` data dictionary view lists the privileges for a database account including privileges granted through `PUBLIC`.

For example:

    SELECT USERNAME, ACCESS_TYPE, PRIVILEGE FROM DBA_DV_USER_PRIVS;

Output similar to the following appears:

    USERNAME            ACCESS_TYPE  PRIVILEGE
    ------------------- ------------ -----------------
    ACCTS_ADMIN_ACE     CONNECT      CREATE_SESSION
    SEC_ADMIN_OWEN      DIRECT       CREATE PROCEDURE
    ...

#### Related Views

- DBA_DV_PUB_PRIVS View

- DBA_DV_ROLE View

- DBA_DV_USER_PRIVS View

| Column        | Datatype              | Null   | Description                                                                                                                                    |
|:--------------|:----------------------|:-------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`    | `VARCHAR(128)`        | `NULL` | Name of the database schema account in which privileges have been defined.                                                                     |
| `ACCESS_TYPE` | `VARCHAR(128)`        | `NULL` | Role the database user account listed in the `USERNAME` column uses to access the database. Oracle Database Vault accounts have direct access. |
| `PRIVILEGE`   | `VARCHAR(40)`         | `NULL` | Privilege granted to the user listed in the `USERNAME` column.                                                                                 |
| `OWNER`       | `VARCHAR(128)`        | `NULL` | Name of the database user account.                                                                                                             |
| `OBJECT_NAME` | `VARCHAR(128)`        | `NULL` | Name of the PL/SQL function or procedure used to define privileges.                                                                            |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.41 DVSYS.DV\$CONFIGURATION_AUDIT View

The `DVSYS.DV$CONFIGURATION_AUDIT` data dictionary view captures `DVSYS.AUDIT_TRAIL$` table audit trail records.

It includes records that are related to successful and failed configuration changes made to realms, rules, rule sets, factors, and other Oracle Database Vault policy configuration activities.

For example:

    SELECT USERNAME, ACTION_NAME FROM DVSYS.DV$CONFIGURATION_AUDIT
    WHERE USERNAME = 'PSMITH';

Output similar to the following appears:

    USERNAME   ACTION_NAME
    ---------- ---------------------
    PSMITH     Realm Creation Audit
    PSMITH     Rule Set Update Audit

#### Related View

- AUDSYS.DV\$CONFIGURATION_AUDIT View

| Column               | Datatype                      | Null       | Description                                                                                                                                                                                                                              |
|:---------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ID#`                | `NUMBER`                      | `NOT NULL` | Numeric identifier for the audit record                                                                                                                                                                                                  |
| `OS_USERNAME`        | `VARCHAR(255)`                | `NULL`     | Operating system login user name of the user whose actions were audited                                                                                                                                                                  |
| `USERNAME`           | `VARCHAR(128)`                | `NULL`     | Name of the database user whose actions were audited                                                                                                                                                                                     |
| `USERHOST`           | `VARCHAR2(128)`               | `NULL`     | Client computer name                                                                                                                                                                                                                     |
| `TERMINAL`           | `VARCHAR2(30)`                | `NULL`     | Identifier for the user's terminal                                                                                                                                                                                                       |
| `TIMESTAMP`          | `DATA`                        | `NULL`     | Date and time of creation of the audit trail entry (in the local database session time zone)                                                                                                                                             |
| `OWNER`              | `VARCHAR2(128)`               | `NULL`     | Creator of the object affected by the action, always `DVSYS` (because `DVSYS` is where objects are created)                                                                                                                              |
| `OBJ_NAME`           | `VARCHAR2(128)`               | `NULL`     | Name of the object affected by the action. Expected values are:<br>• `ROLE$`<br>• `REALM$`<br>• `CODE$`<br>• `FACTOR$`                                                                                                                   |
| `ACTION`             | `NUMBER`                      | `NOT NULL` | Numeric action type code. The corresponding name of the action type is in the `ACTION_NAME` column. See Table 24-3 for a listing of the possible actions.                                                                                |
| `ACTION_NAME`        | `VARCHAR2(128)`               | `NULL`     | Name of the action type corresponding to the numeric code in the `ACTION` column. See Table 24-3 for a listing of the possible actions.                                                                                                  |
| `ACTION_OBJECT_ID`   | `NUMBER`                      | `NULL`     | The unique identifier of the record in the table specified under `OBJ_NAME`                                                                                                                                                              |
| `ACTION_OBJECT_NAME` | `VARCHAR2(128)`               | `NULL`     | The unique name or natural key of the record in the table specified under `OBJ_NAME`                                                                                                                                                     |
| `ACTION_COMMAND`     | `VARCHAR2(4000)`              | `NULL`     | The SQL text of the command procedure that was executed that resulted in the audit event being triggered                                                                                                                                 |
| `AUDIT_OPTION`       | `VARCHAR2(4000)`              | `NULL`     | The labels for all audit options specified in the record that resulted in the audit event being triggered. For example, a factor set operation that is supposed to audit on get failure and get `NULL` would indicate these two options. |
| `RULE_SET_ID`        | `NUMBER`                      | `NULL`     | The unique identifier of the rule set that was executing and caused the audit event to trigger                                                                                                                                           |
| `RULE_SET_NAME`      | `VARCHAR2(128)`               | `NULL`     | The unique name of the rule set that was executing and caused the audit event to trigger                                                                                                                                                 |
| `RULE_ID`            | `NUMBER`                      | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `RULE_NAME`          | `VARCHAR2(128)`               | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `FACTOR_CONTEXT`     | `VARCHAR2(4000)`              | `NULL`     | An XML document that contains all of the factor identifiers for the current session at the point when the audit event was triggered                                                                                                      |
| `COMMENT_TEXT`       | `VARCHAR2(4000)`              | `NULL`     | Text comment on the audit trail entry, providing more information about the statement audited                                                                                                                                            |
| `SESSIONID`          | `NUMBER`                      | `NOT NULL` | Numeric identifier for each Oracle session                                                                                                                                                                                               |
| `ENTRYID`            | `NUMBER`                      | `NOT NULL` | Same as the value in the `ID#` column                                                                                                                                                                                                    |
| `STATEMENTID`        | `NUMBER`                      | `NOT NULL` | Numeric identifier for the statement invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                                                                           |
| `RETURNCODE`         | `NUMBER`                      | `NOT NULL` | Oracle error code generated by the action. The error code for a statement or procedure invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                         |
| `EXTENDED_TIMESTAMP` | `TIMESTAMP(6) WITH TIME ZONE` | `NULL`     | Time stamp of creation of the audit trail entry (time stamp of user login for entries) in UTC (Coordinated Universal Time) time zone                                                                                                     |
| `PROXY_SESSIONID`    | `NUMBER`                      | `NULL`     | Proxy session serial number, if an enterprise user has logged in through the proxy mechanism                                                                                                                                             |
| `GLOBAL_UID`         | `VARCHAR2(32)`                | `NULL`     | Global user identifier for the user, if the user has logged in as an enterprise user                                                                                                                                                     |
| `INSTANCE_NUMBER`    | `NUMBER`                      | `NULL`     | Instance number as specified by the `INSTANCE_NUMBER` initialization parameter                                                                                                                                                           |
| `OS_PROCESS`         | `VARCHAR2(16)`                | `NULL`     | Operating system process identifier of the Oracle process                                                                                                                                                                                |
| `CREATED_BY`         | `VARCHAR2(128)`               | `NULL`     | Database login user name of the user whose actions were audited                                                                                                                                                                          |
| `CREATE_DATE`        | `DATE`                        | `NULL`     | Date on which the action occurred, based on the `SYSDATE` date                                                                                                                                                                           |
| `UPDATED_BY`         | `VARCHAR2(128)`               | `NULL`     | Same as `CREATED_BY` column value                                                                                                                                                                                                        |
| `UPDATE_DATE`        | `DATE`                        | `NULL`     | Same as `UPDATED_BY` column value                                                                                                                                                                                                        |
| `GRANTEE`            | `VARCHAR2(128)`               | `NULL`     | User ID of users who have been granted Database Vault-protected roles, realm authorization, command-rule authorization, job scheduler authorization, or Oracle Data Pump authorizations                                                  |
| `ENABLED_STATUS`     | `VARCHAR2(1)`                 | `NULL`     | Indicates whether the configuration was enabled                                                                                                                                                                                          |

Table 24-3 describes the possible values for the `ACTION` column of the `DVSYS.DV$CONFIGURATION_AUDIT` view.

Table 24-3 DVSYS.DV\$CONFIGURATION_AUDIT View ACTION Values

| Action Type Code | Action Name                             |
|:-----------------|:----------------------------------------|
| `20001`          | `Enable DV enforcement Audit`           |
| `20002`          | `Disable DV enforcement Audit`          |
| `20003`          | `Realm Creation Audit`                  |
| `20004`          | `Realm Update Audit`                    |
| `20005`          | `Realm Rename Audit`                    |
| `20006`          | `Realm Deletion Audit`                  |
| `20007`          | `Add Realm Auth Audit`                  |
| `20008`          | `Delete Realm Auth Audit`               |
| `20009`          | `Update Realm Auth Audit`               |
| `20010`          | `Add Realm Object Audit`                |
| `20011`          | `Update Realm Object Audit`             |
| `20012`          | `Delete Realm Object Audit`             |
| `20013`          | `Enable Event Audit`                    |
| `20014`          | `Disable Event Audit`                   |
| `20015`          | `Rule Set Creation Audit`               |
| `20016`          | `Rule Set Update Audit`                 |
| `20017`          | `Rule Set Rename Audit`                 |
| `20018`          | `Rule Set Deletion Audit`               |
| `20019`          | `Add Rule To Rule Set Audit`            |
| `20020`          | `Delete Rule From Rule Set Audit`       |
| `20021`          | `Rule Creation Audit`                   |
| `20022`          | `Rule Update Audit`                     |
| `20023`          | `Rule Rename Audit`                     |
| `20024`          | `Rule Deletion Audit`                   |
| `20025`          | `CommandRule Creation Audit`            |
| `20026`          | `CommandRule Update Audit`              |
| `20027`          | `CommandRule Deletion Audit`            |
| `20028`          | `Authorize Datapump User Audit`         |
| `20029`          | `Unauthorize Datapump User Audit`       |
| `20030`          | `Authorize Job User Audit`              |
| `20031`          | `Unauthorize Job User Audit`            |
| `20032`          | `Factor_Type Creation Audit`            |
| `20033`          | `Factor_Type Deletion Audit`            |
| `20034`          | `Factor_Type Update Audit`              |
| `20035`          | `Factor_Type Rename Audit`              |
| `20036`          | `Factor Creation Audit`                 |
| `20037`          | `G_FACTOR_DELETION_AUDIT_CODE`          |
| `20038`          | `Factor Update Audit`                   |
| `20039`          | `Factor Rename Audit`                   |
| `20040`          | `Add Factor Link Audit`                 |
| `20041`          | `Delete Factor Link Audit`              |
| `20042`          | `Add Policy Factor Audit`               |
| `20043`          | `Delete Policy Factor Audit`            |
| `20044`          | `Create Identity Audit`                 |
| `20045`          | `Delete Identity Audit`                 |
| `20046`          | `Update Identity Audit`                 |
| `20047`          | `Change Identity Factor Audit`          |
| `20048`          | `Change Identity Value Audit`           |
| `20049`          | `Create Identity Map Audit`             |
| `20050`          | `Delete Identity Map Audit`             |
| `20051`          | `Create Policy Label Audit`             |
| `20052`          | `Delete Policy Label Audit`             |
| `20053`          | `Create Mac Policy Audit`               |
| `20054`          | `Update Mac Policy Audit`               |
| `20055`          | `Delete Mac Policy Audit`               |
| `20056`          | `Create Role Audit`                     |
| `20057`          | `Delete Role Audit`                     |
| `20058`          | `Update Role Audit`                     |
| `20059`          | `Rename Role Audit`                     |
| `20060`          | `Create Domain Identity Audit`          |
| `20061`          | `Drop Domain Identity Audit`            |
| `20062`          | `Enable Oradebug Audit`                 |
| `20063`          | `Disable Oradebug Audit`                |
| `20064`          | `Authorize Proxy User Audit`            |
| `20065`          | `Unauthorize Proxy User Audit`          |
| `20066`          | `Enable DV Dictionary Accounts Audit`   |
| `20067`          | `Disable DV Dictionary Accounts Audit`  |
| `20068`          | `Authorize DDL Audit`                   |
| `20069`          | `Unauthorize DDL Audit`                 |
| `20070`          | `Authorize TTS Audit`                   |
| `20071`          | `Unauthorize TTS Audit`                 |
| `20072`          | `Authorize PREPROCESSOR Audit`          |
| `20073`          | `Unauthorize PREPROCESSOR Audit`        |
| `20074`          | `Create Policy Audit`                   |
| `20075`          | `Update Policy Description Audit`       |
| `20076`          | `Update Policy State Audit`             |
| `20077`          | `Rename Policy Audit`                   |
| `20078`          | `Drop Policy Audit`                     |
| `20079`          | `Add Realm to Policy Audit`             |
| `20080`          | `Delete Realm From Policy Audit`        |
| `20081`          | `Add Command Rule to Policy Audit`      |
| `20082`          | `Delete Command Rule from Policy Audit` |
| `20083`          | `Add Policy Owner Audit`                |
| `20084`          | `Delete Policy Owner Audit`             |
| `20085`          | `Authorize Maintenance Audit`           |
| `20086`          | `Unauthorize Maintenance Audit`         |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.42 DVSYS.DV\$ENFORCEMENT_AUDIT View

The `DVSYS.DV$ENFORCEMENT_AUDIT` data dictionary view provides information about enforcement-related audits from the `DVSYS.AUDIT_TRAIL$` table.

It captures user violations on command rules, realms, and factors.

For example:

    SELECT USERNAME, ACTION_COMMMAND FROM DVSYS.DV$ENFORCEMENT_AUDIT
    WHERE OWNER = 'HR';

Output similar to the following appears:

    USERNAME    ACTION_COMMMAND
    ----------- ------------------------------
    PSMITH      CREATE_REALM

#### Related View

- AUDSYS.DV\$ENFORCEMENT_AUDIT View

| Column               | Datatype                      | Null       | Description                                                                                                                                                                                                                              |
|:---------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ID#`                | `NUMBER`                      | `NOT NULL` | Numeric identifier for the audit record                                                                                                                                                                                                  |
| `OS_USERNAME`        | `VARCHAR(255)`                | `NULL`     | Operating system login user name of the user whose actions were audited                                                                                                                                                                  |
| `USERNAME`           | `VARCHAR(128)`                | `NULL`     | Name of the database user whose actions were audited                                                                                                                                                                                     |
| `USERHOST`           | `VARCHAR(255)`                | `NULL`     | Client computer name                                                                                                                                                                                                                     |
| `TERMINAL`           | `VARCHAR(255)`                | `NULL`     | Identifier for the user's terminal                                                                                                                                                                                                       |
| `TIMESTAMP`          | `DATE`                        | `NULL`     | Date and time of creation of the audit trail entry (in the local database session time zone)                                                                                                                                             |
| `OWNER`              | `VARCHAR(128)`                | `NULL`     | Creator of the object affected by the action, always `DVSYS` (because `DVSYS` is where objects are created)                                                                                                                              |
| `OBJ_NAME`           | `VARCHAR(128)`                | `NULL`     | Name of the object affected by the action. Expected values are:<br>• `ROLE$`<br>• `REALM$`<br>• `CODE$`<br>• `FACTOR$`                                                                                                                   |
| `ACTION`             | `NUMBER`                      | `NOT NULL` | Numeric action type code. The corresponding name of the action type is in the `ACTION_NAME` column. See Table 24-4 for a listing of the possible actions.                                                                                |
| `ACTION_NAME`        | `VARCHAR(128)`                | `NULL`     | Name of the action type corresponding to the numeric code in the `ACTION` column                                                                                                                                                         |
| `ACTION_OBJECT_ID`   | `NUMBER`                      | `NULL`     | The unique identifier of the record in the table specified under `OBJ_NAME`                                                                                                                                                              |
| `ACTION_OBJECT_NAME` | `VARCHAR(128)`                | `NULL`     | The unique name or natural key of the record in the table specified under `OBJ_NAME`                                                                                                                                                     |
| `ACTION_COMMAND`     | `VARCHAR2(4000)`              | `NULL`     | The SQL text of the command procedure that was executed that resulted in the audit event being triggered                                                                                                                                 |
| `AUDIT_OPTION`       | `VARCHAR2(4000)`              | `NULL`     | The labels for all audit options specified in the record that resulted in the audit event being triggered. For example, a factor set operation that is supposed to audit on get failure and get `NULL` would indicate these two options. |
| `RULE_SET_ID`        | `NUMBER`                      | `NULL`     | The unique identifier of the rule set that was executing and caused the audit event to trigger                                                                                                                                           |
| `RULE_SET_NAME`      | `VARCHAR(128)`                | `NULL`     | The unique name of the rule set that was executing and caused the audit event to trigger                                                                                                                                                 |
| `RULE_ID`            | `NUMBER`                      | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `RULE_NAME`          | `VARCHAR2(128)`               | `NULL`     | Not used                                                                                                                                                                                                                                 |
| `FACTOR_CONTEXT`     | `VARCHAR2(4000)`              | `NULL`     | An XML document that contains all of the factor identifiers for the current session at the point when the audit event was triggered                                                                                                      |
| `COMMENT_TEXT`       | `VARCHAR2(4000)`              | `NULL`     | Text comment on the audit trail entry, providing more information about the statement audited                                                                                                                                            |
| `SESSIONID`          | `NUMBER`                      | `NOT NULL` | Numeric identifier for each Oracle session                                                                                                                                                                                               |
| `ENTRYID`            | `NUMBER`                      | `NOT NULL` | Same as the value in the `ID#` column                                                                                                                                                                                                    |
| `STATEMENTID`        | `NUMBER`                      | `NOT NULL` | Numeric identifier for the statement invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                                                                           |
| `RETURNCODE`         | `NUMBER`                      | `NOT NULL` | Oracle error code generated by the action. The error code for a statement or procedure invoked that caused the audit event to be generated. This is empty for most Oracle Database Vault events.                                         |
| `EXTENDED_TIMESTAMP` | `TIMESTAMP(6) WITH TIME ZONE` | `NULL`     | Time stamp of creation of the audit trail entry (time stamp of user login for entries) in UTC (Coordinated Universal Time) time zone                                                                                                     |
| `PROXY_SESSIONID`    | `NUMBER`                      | `NULL`     | Proxy session serial number, if an enterprise user has logged in through the proxy mechanism                                                                                                                                             |
| `GLOBAL_UID`         | `VARCHAR2(32)`                | `NULL`     | Global user identifier for the user, if the user has logged in as an enterprise user                                                                                                                                                     |
| `INSTANCE_NUMBER`    | `NUMBER`                      | `NULL`     | Instance number as specified by the `INSTANCE_NUMBER` initialization parameter                                                                                                                                                           |
| `OS_PROCESS`         | `VARCHAR2(16)`                | `NULL`     | Operating system process identifier of the Oracle process                                                                                                                                                                                |
| `CREATED_BY`         | `VARCHAR2(128)`               | `NULL`     | Database login user name of the user whose actions were audited                                                                                                                                                                          |
| `CREATE_DATE`        | `DATE`                        | `NULL`     | Date on which the action occurred, based on the `SYSDATE` date                                                                                                                                                                           |
| `UPDATED_BY`         | `VARCHAR2(128)`               | `NULL`     | Same as `CREATED_BY` column value                                                                                                                                                                                                        |
| `UPDATE_DATE`        | `DATE`                        | `NULL`     | Same as `UPDATED_BY` column value                                                                                                                                                                                                        |

The following table describes the possible values for the `ACTION` column of the `DVSYS.DV$ENFORCEMENT_AUDIT` view.

Table 24-4 DVSYS.DV\$ENFORCEMENT_AUDIT View ACTION Values

| Action Type Code | Action Name                          |
|:-----------------|:-------------------------------------|
| `10000`          | `Factor Evaluation Audit`            |
| `10001`          | `Factor Assignment Audit`            |
| `10002`          | `Factor Expression Audit`            |
| `10003`          | `Realm Violation Audit`              |
| `10004`          | `Realm Authorization Audit`          |
| `10005`          | `Command Authorization Audit`        |
| `10006`          | `Secure Role Audit`                  |
| `10007`          | `Session Initialization Audit`       |
| `10008`          | `Secure Command Authorization Audit` |
| `10009`          | `OLS Session Initialization Audit`   |
| `10010`          | `OLS Attempt to Upgrade Label Audit` |
| `10011`          | `Command Failure Audit`              |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.43 DVSYS.DV\$REALM View

The `DVSYS.DV$REALM` data dictionary view describes settings that were used to create Oracle Database Vault realms, such as which audit options have been assigned or whether the realm is a mandatory realm.

This view also indicates information such as who created and updated the realm, and when the realm was created and updated.

For example:

    SELECT NAME, CREATED_BY, TYPE FROM DVSYS.DV$REALM WHERE NAME LIKE 'Statistics';

Output similar to the following appears:

    NAME                         CREATED_BY TYPE
    ---------------------------- ---------- -----
    Performance Statistics Realm JGODFREY   2

#### Related Views

- DBA_DV_REALM View

| Column          | Datatype                 | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------|:-------------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ID#`           | `NUMBER`                 | `NOT NULL` | ID number of the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `NAME`          | `VARCHAR2(128)`          | `NOT NULL` | Name of the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `DESCRIPTION`   | `VARCHAR2(1024)`         | `NULL`     | Description of the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `AUDIT_OPTIONS` | `NUMBER`                 | `NOT NULL` | Audit options set for the realm. See `audit_options` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `REALM_TYPE`    | `NUMBER`                 | `NULL`     | Type of realm: whether it is a regular realm or a mandatory realm. See `realm_type` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON`        | `VARCHAR2(3)`            | `NULL`     | For a multitenant environment, indicates whether the realm is local or common. Possible values are:<br>• `YES` if the realm is common<br>• `NO` if the realm is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`     | `VARCHAR2(3)`            | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ENABLED`       | `VARCHAR2(1)`            | `NOT NULL` | Whether the realm has been enabled. See `enabled` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `VERSION`       | `NUMBER`                 | `NULL`     | Version of Oracle Database Vault in which the realm was created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `CREATED_BY`    | `VARCHAR2(128)`          | `NULL`     | User who created the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `CREATE_DATE`   | `DATE`                   | `NULL`     | Date on which the realm was created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `UPDATED_BY`    | `VARCHAR2(128)`          | `NULL`     | User who last updated the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `UPDATE_DATE`   | `DATE`                   | `NULL`     | Date on which the realm was last updated                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.44 DVSYS.POLICY_OWNER_COMMAND_RULE View

The `DVSYS.POLICY_OWNER_COMMAND_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the command rules that have been associated with Database Vault policies.

Examples of information that users can find include the command rule name, its associated rule set, and whether it is enabled. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT COMMAND, OBJECT_OWNER, OBJECT_NAME FROM DVSYS.POLICY_OWNER_COMMAND_RULE;

Output similar to the following appears:

    COMMAND       OBJECT_OWNER  OBJECT_NAME
    ------------- ------------- ------------
    SELECT        HR            EMPLOYEES

#### Related Views

- DVSYS.POLICY_OWNER_POLICY View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:-----------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COMMAND`         | `VARCHAR(128)`         | `NOT NULL` | Name of the command rule. For a list of default command rules, see [Default Command Rules](configuring-command-rules.md).                                                                                                                                                                                                                                                                                   |
| `CLAUSE_NAME`     | `VARCHAR(100)`         | `NOT NULL` | A clause from either the `ALTER SYSTEM` or `ALTER SESSION` SQL statement, which was used to create the command rule. For example, you it could list the `SET` clause for the `ALTER SESSION` statement.<br>For a full list of possible clause values, see the following topics:<br>• [Table 16-2](oracle-database-vault-command-rule-apis.md)<br>• [Table 16-3](oracle-database-vault-command-rule-apis.md) |
| `PARAMETER_NAME`  | `VARCHAR(128)`         | `NOT NULL` | A parameter from the `ALTER SYSTEM` or `ALTER SESSION` command rule `CLAUSE_NAME` setting                                                                                                                                                                                                                                                                                                                   |
| `EVENT_NAME`      | `VARCHAR(128)`         | `NOT NULL` | An event that the `ALTER SYSTEM` or `ALTER SESSION` command rule defines                                                                                                                                                                                                                                                                                                                                    |
| `COMPONENT_NAME`  | `VARCHAR(128)`         | `NOT NULL` | A component of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule.                                                                                                                                                                                                                                                                                                             |
| `ACTION_NAME`     | `VARCHAR(128)`         | `NOT NULL` | An action of the `EVENT_NAME` setting for the `ALTER SYSTEM` or `ALTER SESSION` command rule                                                                                                                                                                                                                                                                                                                |
| `RULE_SET_NAME`   | `VARCHAR(128)`         | `NOT NULL` | Name of the rule set associated with this command rule.                                                                                                                                                                                                                                                                                                                                                     |
| `OBJECT_OWNER`    | `VARCHAR(128)`         | `NOT NULL` | The owner of the object that the command rule affects.                                                                                                                                                                                                                                                                                                                                                      |
| `OBJECT_NAME`     | `VARCHAR(128)`         | `NOT NULL` | The name of the database object the command rule affects (for example, a database table).                                                                                                                                                                                                                                                                                                                   |
| `ENABLED`         | `VARCHAR(1)`           | `NOT NULL` | `Y` indicates the command rule is enabled; `N` indicates it is disabled.                                                                                                                                                                                                                                                                                                                                    |
| `PRIVILEGE_SCOPE` | `NUMBER`               | `NOT NULL` | Obsolete column                                                                                                                                                                                                                                                                                                                                                                                             |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the command rule, which is automatically generated when the command rule is created                                                                                                                                                                                                                                                                                                        |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NULL`     | Indicates whether the command rule is a default (that is, Oracle-supplied) command rule or a user-created command rule. Possible values are:<br>• `YES` if the command rule is a default command rule<br>• `NO` if the command rule is a user-created command rule                                                                                                                                          |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.45 DVSYS.POLICY_OWNER_POLICY View

The `DVSYS.POLICY_OWNER_POLICY` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information such as the names, descriptions, and states of existing policies in the current database instance, including policies created by other policy owners.

The columns of the `DVSYS.POLICY_OWNER_POLICY` view are the same as those in `DBA_DV_POLICY`. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT POLICY_NAME, STATE FROM DVSYS.POLICY_OWNER_POLICY
      WHERE STATE != 'ENABLED';

Output similar to the following appears:

    POLICY_NAME                        STATE
    ---------------------------------- --------
    HR.EMPLOYEES_pol                   ENABLED

#### Related View

- DBA_DV_POLICY View

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.46 DVSYS.POLICY_OWNER_REALM View

The `POLICY_OWNER_REALM` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the realms that have been associated with Database Vault policies.

Examples of information that users can find include the realm name, audit options, type, whether it is inherited, and if it is enabled. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT NAME, ENABLED FROM DVSYS.POLICY_OWNER_REALM;

Output similar to the following appears:

    NAME                       ENABLED
    -------------------------- --------
    HR.EMPLOYEES_realm         S

#### Related Views

- DVSYS.POLICY_OWNER_REALM_AUTH View

- DVSYS.POLICY_OWNER_REALM_OBJECT View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------|:-----------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR(128)`         | `NOT NULL` | Names of the realms that have been associated with Database Vault policies.<br>See DBA_DV_REALM View for a full listing of realms.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `DESCRIPTION`     | `VARCHAR(1024)`        | `NULL`     | Description of the realm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `AUDIT_OPTIONS`   | `NUMBER`               | `NOT NULL` | Audit options set for the realm. See `audit_options` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `REALM_TYPE`      | `NUMBER`               | `NULL`     | Type of realm: whether it is a regular realm or a mandatory realm. See `realm_type` in [Table 14-9](oracle-database-vault-realm-apis.md) for a description of the possible values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON_REALM`    | `VARCHAR2(3)`          | `NULL`     | For a multitenant environment, indicates whether the realm is local or common. Possible values are:<br>• `YES` if the realm is common<br>• `NO` if the realm is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED_REALM` | `VARCHAR2(3)`          | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ENABLED`         | `VARCHAR2(1)`          | `NOT NULL` | Indicates the enablement status of the realm. Possible values are:<br>• `Y` for yes (enabled)<br>• `N` for no (not enabled)<br>• `S` for simulation mode                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the realm, which is automatically generated when the realm is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NOT NULL` | Indicates whether the realm is a default (that is, Oracle-supplied) realm or a user-created realm. Possible values are:<br>• `YES` if the realm is a default realm<br>• `NO` if the realm is a user-created realm                                                                                                                                                                                                                                                                                                                                                                                                                                               |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.47 DVSYS.POLICY_OWNER_REALM_AUTH View

The `DVSYS.POLICY_OWNER_REALM_AUTH` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the authorization that was granted to realms that have been associated with Database Vault policies.

Examples of the information that users can find are the realm name, grantee, and associated rule set. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT REALM_NAME, INHERITED_REALM FROM DVSYS.POLICY_OWNER_REALM_AUTH;

Output similar to the following appears:

    REALM_NAME                 INHERITED
    -------------------------- --------
    HR.EMPLOYEES_realm         NO

#### Related Views

- DVSYS.POLICY_OWNER_REALM View

- DVSYS.POLICY_OWNER_REALM_OBJECT View

| Column               | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:---------------------|:-----------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `REALM_NAME`         | `VARCHAR(128)`         | `NOT NULL` | Names of the realms that have been associated with Database Vault policies.<br>See DBA_DV_REALM View for a full listing of realms.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON_REALM`       | `VARCHAR2(3)`          | `NULL`     | For a multitenant environment, indicates whether the realm is local or common.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `INHERITED_REALM`    | `VARCHAR2(3)`          | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `GRANTEE`            | `VARCHAR(128)`         | `NOT NULL` | User or role name to authorize as owner or participant.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `AUTH_RULE_SET_NAME` | `VARCHAR(128)`         | `NULL`     | Rule set to check before authorizing. If the rule set evaluates to `TRUE`, then the authorization is allowed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `AUTH_OPTIONS`       | `VARCHAR(4000)`        | `NULL`     | Type of realm authorization: either `Participant` or `Owner`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `COMMON_AUTH`        | `VARCHAR(3)`           | `NULL`     | For a multitenant environment, indicates whether the user who is authorized for this realm is local or common. Possible values are:<br>• `YES` if the user is a common user<br>• `NO` if the users is a local user                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `INHERITED_AUTH`     | `VARCHAR(3)`           | `NULL`     | Possible values are:<br>• `YES`<br>• `NO`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.48 DVSYS.POLICY_OWNER_REALM_OBJECT View

The `DVSYS.POLICY_OWNER_REALM_OBJECT` data dictionary view enables users to find information about the objects that have been added to realms that are associated with Database Vault policies, such as. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

Examples of information that users can find include the realm name, grantee, and associated rule set.

For example:

    SELECT REALM_NAME, OWNER, OBJECT_NAME, OBJECT_TYPE FROM DVSYS.POLICY_OWNER_REALM_OBJECT;

Output similar to the following appears:

    REALM_NAME         OWNER  OBJECT_NAME OBJECT_TYPE
    ------------------ ------ ----------- -----------
    HR.EMPLOYEES_realm HR     EMPLOYEES   TABLE

#### Related Views

- DVSYS.POLICY_OWNER_REALM View

- DVSYS.POLICY_OWNER_REALM_AUTH View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------|:-----------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `REALM_NAME`      | `VARCHAR(128)`         | `NOT NULL` | Names of the realms that have been associated with Database Vault policies.<br>See DBA_DV_REALM View for a full listing of realms.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON_REALM`    | `VARCHAR2(3)`          | `NULL`     | For a multitenant environment, indicates whether the realm is local or common.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `INHERITED_REALM` | `VARCHAR2(3)`          | `NULL`     | Shows the inheritance status of the realm, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the realm was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the realm is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `OWNER`           | `VARCHAR(128)`         | `NOT NULL` | Database schema owner who owns the object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `OBJECT_NAME`     | `VARCHAR(128)`         | `NOT NULL` | Name of the object the realm protects.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `OBJECT_TYPE`     | `VARCHAR(32)`          | `NOT NULL` | Type of object the realm protects, such as a database table, view, index, or role.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.49 DVSYS.POLICY_OWNER_RULE View

The `DVSYS.POLICY_OWNER_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rules that have been associated with rule sets in Database Vault policies, such as the rule name and its expression. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT NAME, RULE_EXPR FROM DVSYS.POLICY_OWNER_RULE WHERE NAME = 'True';

Output similar to the following appears:

    NAME       RULE_EXPR
    ---------- --------
    True       1=1

#### Related Views

- DVSYS.POLICY_OWNER_COMMAND_RULE View

- DVSYS.POLICY_OWNER_RULE_SET View

| Column            | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------|:-----------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR(128)`         | `NOT NULL` | Name of the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `RULE_EXPR`       | `VARCHAR(1024)`        | `NOT NULL` | PL/SQL expression for the rule.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `COMMON`          | `VARCHAR(3`)           | `NOT NULL` | For a multitenant environment, indicates whether the rule is local or common. Possible values are:<br>• `YES` if the rule is common<br>• `NO` if the rule is local                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `INHERITED`       | `VARCHAR(3`)           | `NULL`     | Shows the inheritance status of the rule, when the `COMMON` column output is `YES`. Values are as follows:<br>• `YES` means that the rule was defined in another container that is higher in the hierarchy of the container tree, and inherited in this container when the Database Vault policy was synced during the synchronization process of applications in an application PDB.<br>• `NO` means that the rule is a local object, or it is common from that container. For example, in an application root, an application common realm will have an `INHERITED` value `NO` but a CDB root common command rule will have an `INHERITED` value of `YES`. |
| `ID#`             | `NUMBER`               | `NOT NULL` | The ID number of the rule, which is automatically generated when the rule is created                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ORACLE_SUPPLIED` | `VARCHAR(3)`           | `NULL`     | Indicates whether the rule is a default (that is, Oracle-supplied) rule or a user-created rule. Possible values are:<br>• `YES` if the rule is a default rule<br>• `NO` if the rule is a user-created rule                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.50 DVSYS.POLICY_OWNER_RULE_SET View

The `DVSYS.POLICY_OWNER_RULE_SET` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rule sets that have been associated with Database Vault policies.

Examples of information that users can find include the rule set name, its handler information, and whether it is enabled. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT RULE_SET_NAME, ENABLED FROM DVSYS.POLICY_OWNER_RULE_SET;

Output similar to the following appears:

    RULE_SET_NAME  ENABLED
    -------------- --------
    Allow Sessions Y

#### Related Views

- DVSYS.POLICY_OWNER_COMMAND_RULE View

- DVSYS.POLICY_OWNER_RULE View

- DVSYS.POLICY_OWNER_RULE_SET_RULE View

| Column                 | Datatype               | Null       | Description                                                                                                                                                                                                                                                                                                                                       |
|:-----------------------|:-----------------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RULE_SET_NAME`        | `VARCHAR(128)`         | `NOT NULL` | Name of the rule set.                                                                                                                                                                                                                                                                                                                             |
| `DESCRIPTION`          | `VARCHAR(1024)`        | `NULL`     | Description of the rule set.                                                                                                                                                                                                                                                                                                                      |
| `ENABLED`              | `VARCHAR(1)`           | `NOT NULL` | Indicates whether the rule set has been enabled. `Y` (Yes) enables the rule set; `N` (No) disables it.                                                                                                                                                                                                                                            |
| `EVAL_OPTIONS_MEANING` | `VARCHAR(4000)`        | `NULL`     | For rules sets that contain multiple rules, determines how many rules are evaluated. Possible values are:<br>• `All True`: All rules in the rule set must evaluate to true for the rule set itself to evaluate to `TRUE`.<br>• `Any True`: At least one rule in the rule set must evaluate to true for the rule set itself to evaluate to `TRUE`. |
| `AUDIT_OPTIONS`        | `NUMBER`               | `NOT NULL` | Indicates when auditing is used. Possible values are:<br>• `0`: No auditing<br>• `1`: Audit on failure<br>• `2`: Audit on success<br>• `3`: Audit on both failure and success                                                                                                                                                                     |
| `FAIL_OPTIONS_MEANING` | `VARCHAR(4000)`        | `NULL`     | Determines when an audit record is created for the rule set. Possible values are:<br>• `Do Not Show Error Message`.<br>• `Show Error Message`                                                                                                                                                                                                     |
| `FAIL_MESSAGE`         | `VARCHAR(80)`          | `NULL`     | Error message for failure that is associated with the fail code listed in the `FAIL_CODE` column.                                                                                                                                                                                                                                                 |
| `FAIL_CODE`            | `VARCHAR(10)`          | `NULL`     | The error message number associated with the message listed in the `FAIL_MESSAGE` column. Possible values are in the ranges of -20000 to -20999 or 20000 to 20999.                                                                                                                                                                                |
| `HANDLER_OPTIONS`      | `NUMBER`               | `NOT NULL` | Determines how error handling is used. Possible values are:<br>• `0`: Disables error handling.<br>• `1`: Call handler on rule set failure.<br>• `2`: Call handler on rule set success.                                                                                                                                                            |
| `HANDLER`              | `VARCHAR(1024)`        | `NULL`     | Name of the PL/SQL function or procedure that defines the custom event handler logic.                                                                                                                                                                                                                                                             |
| `IS_STATIC`            | `VARCHAR2(5)`          | `NULL`     | Indicates how often the rule set is evaluated during a user session. Possible values are:<br>• `TRUE`: The rule set is evaluated once, and result of the rule set is reused throughout the user session.<br>• `FALSE` (default): The rule set is evaluated each time it is accessed during the user session.                                      |
| `ID#`                  | `NUMBER)`              | `NOT NULL` | The ID number of the rule set, which is automatically generated when the rule set is created                                                                                                                                                                                                                                                      |
| `ORACLE_SUPPLIED`      | `VARCHAR2(3)`          | `NULL`     | Indicates whether the rule set is a default (that is, Oracle-supplied) rule set or a user-created rule set. Possible values are:<br>• `YES` if the rule set is a default rule set<br>• `NO` if the rule set is a user-created rule set                                                                                                            |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.51 DVSYS.POLICY_OWNER_RULE_SET_RULE View

The `DVSYS.POLICY_OWNER_RULE_SET_RULE` data dictionary view enables users who have been granted the `DV_POLICY_OWNER` role to find information about the rule sets that contain rules used in Database Vault policies.

Examples of information that users can find include the rule set name and whether it is enabled. Only users who have been granted the `DV_POLICY_OWNER` role can query this view.

For example:

    SELECT ENABLED FROM DVSYS.POLICY_OWNER_RULE_SET_RULE WHERE RULE_SET_NAME = 'Can Maintain Own Account';

Output similar to the following appears:

    ENABLED
    ----------
    Y

#### Related Views

- DVSYS.POLICY_OWNER_COMMAND_RULE View

- DVSYS.POLICY_OWNER_RULE_SET View

- DVSYS.POLICY_OWNER_RULE View

| Column          | Datatype               | Null       | Description                                                                                              |
|:----------------|:-----------------------|:-----------|:---------------------------------------------------------------------------------------------------------|
| `RULE_SET_NAME` | `VARCHAR(128)`         | `NOT NULL` | Name of the rule set that contains the rule.                                                             |
| `RULE_NAME`     | `VARCHAR(128)`         | `NOT NULL` | Name of the rule.                                                                                        |
| `RULE_EXPR`     | `VARCHAR(1024)`        | `NOT NULL` | PL/SQL expression that defines the rule listed in the `RULE_NAME` column.                                |
| `ENABLED`       | `VARCHAR(1)`           |            | Indicates whether the rule is enabled or disabled. `Y` (Yes) enables the rule set; `N` (No) disables it. |
| `RULE_ORDER`    | `NUMBER`               | `NOT NULL` | The order in which rules are used within the rule set. Does not apply to this release.                   |

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.52 AUDSYS.DV\$CONFIGURATION_AUDIT View

The `AUDSYS.DV$CONFIGURATION_AUDIT` view is almost the same as the `DVSYS.DV$CONFIGURATION_AUDIT` view except that it captures unified audit trail Database Vault audit records.

**Related Topics**

- DVSYS.DV\$CONFIGURATION_AUDIT View

**Parent topic:** Oracle Database Vault Data Dictionary Views

### 24.53 AUDSYS.DV\$ENFORCEMENT_AUDIT View

The `AUDSYS.DV$ENFORCEMENT_AUDIT` view is almost the same as the `DVSYS.DV$ENFORCEMENT_AUDIT` view except that it captures unified audit trail Database Vault audit records.

**Related Topics**

- DVSYS.DV\$ENFORCEMENT_AUDIT View

**Parent topic:** Oracle Database Vault Data Dictionary Views
