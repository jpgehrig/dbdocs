The `DBMS_MACADM` PL/SQL package provides procedures for configuring command rules. .

Only users who have been granted the `DV_OWNER` or `DV_ADMIN` role can use these procedures.

- CREATE_COMMAND_RULE Procedure
  The `CREATE_COMMAND_RULE` procedure creates a command rule and associates it with a rule set.
- CREATE_CONNECT_COMMAND_RULE Procedure
  The `CREATE_CONNECT_COMMAND_RULE` procedure creates a CONNECT command rule that you can associate with a user and a rule set.
- CREATE_SESSION_EVENT_CMD_RULE Procedure
  The `CREATE_SESSION_EVENT_CMD_RULE` procedure creates a command rule that you can associate with session events, based on the `ALTER SESSION` statement.
- CREATE_SYSTEM_EVENT_CMD_RULE Procedure
  The `CREATE_SYSTEM_EVENT_CMD_RULE` procedure creates a command rule that you can associate with system events, based on the `ALTER SYSTEM` statement.
- DELETE_COMMAND_RULE Procedure
  The `DELETE_COMMAND_RULE` procedure drops a command rule declaration.
- DELETE_CONNECT_COMMAND_RULE Procedure
  The `DELETE_CONNECT_COMMAND_RULE` procedure deletes a CONNECT command rule that had been created with the `CREATE_CONNECT_COMMAND_RULE` procedure.
- DELETE_SESSION_EVENT_CMD_RULE Procedure
  The `DELETE_SESSION_EVENT_CMD_RULE` procedure deletes a session command rule that was associated with events.
- DELETE_SYSTEM_EVENT_CMD_RULE Procedure
  The `DELETE_SYSTEM_EVENT_CMD_RULE` procedure deletes a system command rule that was associated with events.
- UPDATE_COMMAND_RULE Procedure
  The `UPDATE_COMMAND_RULE` procedure updates a command rule declaration.
- UPDATE_CONNECT_COMMAND_RULE Procedure
  The `UPDATE_CONNECT_COMMAND_RULE` procedure updates a CONNECT command rule that had been created with the `CREATE_CONNECT_COMMAND_RULE` procedure.
- UPDATE_SESSION_EVENT_CMD_RULE Procedure
  The `UPDATE_SESSION_EVENT_CMD_RULE` procedure updates a session event command rule, based on the `ALTER SESSION` statement.
- UPDATE_SYSTEM_EVENT_CMD_RULE Procedure
  The `UPDATE_SYSTEM_EVENT_CMD_RULE` procedure updates a system event command rule, based on the `ALTER SYSTEM` statement.

**Related Topics**

- [Configuring Command Rules](configuring-command-rules.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

### 16.1 CREATE_COMMAND_RULE Procedure

The `CREATE_COMMAND_RULE` procedure creates a command rule and associates it with a rule set.

Optionally, you can use it to enable the command rule for rule checking with a rule set. In a multitenant environment, you can create both common and local command rules.

#### Syntax

    DBMS_MACADM.CREATE_COMMAND_RULE(
     command         IN VARCHAR2,
     rule_set_name   IN VARCHAR2,
     object_owner    IN VARCHAR2,
     object_name     IN VARCHAR2,
     enabled         IN VARCHAR2,
     privilege_scope IN NUMBER,
     clause_name     IN VARCHAR2 DEFAULT,
     parameter_name  IN VARCHAR2 DEFAULT,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-1 CREATE_COMMAND_RULE Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `command`         | SQL statement to protect.<br>See also the following:<br>• [Default Command Rules](configuring-command-rules.md) for information about default command rules<br>• [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) for a listing of existing command rules<br>• [SQL Statements That Can Be Protected by Command Rules](configuring-command-rules.md) for a listing of available SQL statements that you can use                                                                                                     |
| `rule_set_name`   | Name of rule set to associate with this command rule.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                  |
| `object_owner`    | Database schema to which this command rule will apply. The wildcard `%` is allowed, except for the `SELECT`, `INSERT`, `UPDATE`, `DELETE`, and `EXECUTE` statements.<br>To find the available users, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md).<br>See also "Object Owner" in [Creating a Command Rule](configuring-command-rules.md) for more information.                                                                                                                                 |
| `object_name`     | Object to be protected by the command rule. (The wildcard % is allowed. See "Object Name" in [Creating a Command Rule](configuring-command-rules.md) for more information about objects protected by command rules.)<br>To find the available objects, query the `ALL_OBJECTS` view, described in [Oracle Database Reference](../refrn/ALL_OBJECTS.md).                                                                                                                                                                                       |
| `enabled`         | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` (Yes) to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                    |
| `privilege_scope` | Obsolete parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `clause_name`     | A clause from the SQL statement that was used to create the command rule. For example, a command rule for the `ALTER SESSION` SQL statement could have the `SET` clause as the `clause_name` parameter.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.<br>The default is `%`, which includes all clauses.                                                                                                                                                                                                           |
| `parameter_name`  | A parameter from the `clause_name` parameter. For example, for an `ALTER SESSION` command rule, you could set `parameter_name` to `EVENTS` if the `clause_name` is `SET`.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.<br>The default is `%`, which includes all parameters.                                                                                                                                                                                                                                      |
| `event_name`      | An event that the command rule defines. For example, suppose an `ALTER SESSION` command rule uses `SET` for the `clause_name` and `EVENTS` as the `parameter_name`. The `event_name` could be set to `TRACE` if you want to track trace events.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `EVENTS`.<br>The default is `%`, which includes all events.                                                                                                                    |
| `component_name`  | A component of the `event_name` setting. For example, for a `TRACE` event, the `component_name` could be `GCS`.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `EVENTS`.<br>The default is `%`, which includes all components.                                                                                                                                                                                                                                                |
| `action_name`     | An action of the `component_name` setting.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `EVENTS`.<br>The default is `%`, which includes all actions.                                                                                                                                                                                                                                                                                                                        |
| `scope`           | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you create the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |

#### ALTER SYSTEM Command Rule Settings

Table 16-2 describes the `ALTER SYSTEM` command rule settings.

Table 16-2 ALTER SYSTEM Command Rule Settings

| clause_name            | parameter_name — Parameter Value                                                                                                                                                                                                                                                                                   |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ARCHIVE LOG`          | • `ALL` — `sequence_number`<br>• `CHANGE` — `change_number`<br>• `CURRENT` — N/A<br>• `GROUP` — `group_number`<br>• `LOGFILE` — `log_file_name`<br>• `NEXT` — N/A<br>• `SEQUENCE` — N/A                                                                                                                            |
| `CHECK DATAFILES`      | N/A — `global` or `local`                                                                                                                                                                                                                                                                                          |
| `CHECKPOINT`           | N/A — `global` or `local`                                                                                                                                                                                                                                                                                          |
| `COPY LOGFILE`         | N/A — N/A                                                                                                                                                                                                                                                                                                          |
| `DISTRIBUTED RECOVERY` | N/A — `enable` or `disable`                                                                                                                                                                                                                                                                                        |
| `DUMP`                 | • `DATAFILE` — N/A<br>• `FLASHBACK` — N/A<br>• `LOGFILE` — N/A<br>• `REDO` — N/A<br>• `TEMPFILE` — N/A<br>• `UNDO` — N/A                                                                                                                                                                                           |
| `END SESSION`          | `DISCONNECT SESSION` — N/A<br>`KILL SESSION` — N/A                                                                                                                                                                                                                                                                 |
| `FLUSH`                | `BUFFER_CACHE` — N/A<br>`GLOBAL CONTEXT` — N/A<br>`REDO` — `target_db_name`<br>`SHARED_POOL` — N/A                                                                                                                                                                                                                 |
| `QUIESCE`              | `QUIESCE RESTRICTED` — N/A<br>`UNQUIESCE` — N/A                                                                                                                                                                                                                                                                    |
| `REFRESH`              | `LDAP_REGISTRATION` — N/A                                                                                                                                                                                                                                                                                          |
| `REGISTER`             | N/A — N/A                                                                                                                                                                                                                                                                                                          |
| `RESET`                | `initialization_parameter_name` — N/A                                                                                                                                                                                                                                                                              |
| `RESUME`               | N/A — N/A                                                                                                                                                                                                                                                                                                          |
| `SECURITY`             | `RESTRICTED SESSION` — `enable` or `disable`<br>`SET ENCRYPTION KEY` — N/A<br>`SET ENCRYPTION WALLET` — `open` or `close`                                                                                                                                                                                          |
| `SET`                  | `EVENTS` — `event_string`<br>`GLOBAL_TOPIC_ENABLED` — `true` or `false`<br>`initialization_parameter_name` — `parameter_value`<br>`LDAP_REGISTRATION_ENABLED` — `true` or `false`<br>`LDAP_REG-SYNC_INTERVAL` — Number<br>`SINGLETASK DEBUG` — N/A<br>`USE_STORED_OUTLINES` — `true` , `false`, or `category_name` |
| `SHUTDOWN DISPPATCHER` | N/A — `dispatcher_name`                                                                                                                                                                                                                                                                                            |
| `SWITCH LOGFILE`       | N/A — `all` or `none`                                                                                                                                                                                                                                                                                              |
| `SUSPEND`              | N/A — N/A                                                                                                                                                                                                                                                                                                          |
| `TX RECOVERY`          | N/A — `enable` or `disable`                                                                                                                                                                                                                                                                                        |

#### ALTER SESSION Command Rule Settings

Table 16-3 describes the `ALTER SESSION` command rule settings.

Table 16-3 ALTER SESSION Command Rule Settings

| clause_name           | parameter_name — Parameter Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ADVISE`              | N/A — `COMMIT`, `ROLLBACK`, or `NOTHING`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `CLOSE DATABASE LINK` | N/A — `database_link`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `COMMIT IN PROCEDURE` | N/A — `ENABLE` or `DISABLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `GUARD`               | N/A — `ENABLE` or `DISABLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `ILM`                 | `ROW ACCESS TRACKING` — N/A<br>`ROW MODIFICATION TRACKING` — N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `LOGICAL REPLICATION` | N/A — N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `PARALLEL DML`        | N/A — `ENABLE`, `DISABLE`, or `FORCE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PARALLEL DDL`        | N/A — `ENABLE`, `DISABLE`, or `FORCE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `PARALLEL QUERY`      | N/A — `ENABLE`, `DISABLE`, or `FORCE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `RESUMABLE`           | N/A — `ENABLE` or `DISABLE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `SYNC WITH PRIMARY`   | N/A — N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `SET`                 | `APPLICATION ACTION` — `action_name`<br>`APPLICATION MODULE` — `module_name`<br>`CONSTRAINTS` — `IMMEDIATE`, `DEFERRED`, or `DEFAULT`<br>`CONTAINER` — `container_name`<br>`CURRENT SCHEMA` — `schema_name`<br>`EDITION` — `edition_name`<br>`ERROR ON OVERLAP TIME` — `TRUE` or `FALSE`<br>`EVENTS` — `event_string`<br>`FLAGGER` — `OFF`, `FULL`, `INTERMEDIATE`, `ENTRY`<br>`initialization_parameter_name` — `parameter_name`<br>`INSTANCE` — `instance_number`<br>`ISOLATION_LEVEL` — `SERIALIZABLE` or `READ COMMITTED`<br>`ROW_ARCHIVAL_VISABILITY` — `ACTIVE` or `ALL`<br>`SQL_TRANSFORMATION_PROFILE` — `profile_name`<br>`STANDBY_MAX_DATA_DELAY` — `NONE``number`<br>`TIME_ZONE` — `LOCAL`, `DBTIMEZONE`, or `other_value`<br>`USE_PRIVATE_OUTLINES` — `TRUE`, `FALSE`, or `category_name`<br>`USE_STORED_OUTLINES` — `TRUE`, `FALSE`, or `category_name` |

#### Examples

Simple Command Rules

The following example shows how to create a simple command rule for the `SELECT` statement on the `OE.ORDERS` table. This command rule uses no command rules.

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE(
      command         => 'SELECT',
      rule_set_name   => 'Check User Role',
      object_owner    => 'OE',
      object_name     => 'ORDERS',
      enabled         => DBMS_MACUTL.G_YES);
    END;
    /

This example shows how to create a command rule that checks if users can enable or disable the `hr_audit_pol` unified audit policy. Note that if the object is a unified audit policy, then you must have `AUDIT POLICY`, not just `AUDIT`, for the `command` parameter.

    BEGIN
    DBMS_MACADM.CREATE_COMMAND_RULE(
      command          => 'AUDIT POLICY',
      rule_set_name    => 'Check ability to audit',
      object_owner     => '%',
      object_name      => 'hr_audit_pol',
      enabled          => DBMS_MACUTL.G_YES,
      scope            => DBMS_MACUTL.G.SCOPE_LOCAL);
    END;
    /

ALTER SESSION Command Rule Using the SET Clause

The following example shows how to create an `ALTER SESSION` command rule that uses the `SET` clause with the `ERROR_ON_OVERLAP_TIME` parameter.

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE(
      command         => 'ALTER SESSION',
      rule_set_name   => 'Test ERROR_ON_OVERLAP_TIME for FALSE',
      object_owner    => '%',
      object_name     => '%',
      enabled         => DBMS_MACUTL.G_YES,
      clause_name     => 'SET',
      parameter_name  => 'ERROR_ON_OVERLAP_TIME',
      scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

In this example:

- `rule_set_name`: The `ALTER SESSION` SQL statement `ERROR_ON_OVERLAP_TIME` session parameter must be set to either `TRUE` or `FALSE`. You can create a rule set that checks if this setting. For example, for the rule:

      EXEC DBMS_MACADM.CREATE_RULE('RULE_TRUE', 'UPPER(PARAMETER_VALUE) = ''TRUE''');

  The rule set that is used with this rule can be similar to the following:

      BEGIN
       DBMS_MACADM.CREATE_RULE_SET(
        rule_set_name    => 'Test ERROR_ON_OVERLAP_TIME',
        description      => 'Checks if the ERROR_ON_OVERLAP_TIME setting is TRUE or FALSE',
        enabled          => DBMS_MACUTL.G_YES,
        eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ALL,
        audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL + DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS,
        fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SILENT,
        fail_message     => 'false error on overlaptime',
        fail_code        => 20461,
        handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_FAIL,
        handler          => '',
        is_static        => false);
      END;
      /
      EXEC DBMS_MACADM.ADD_RULE_TO_RULE_SET('Test ERROR_ON_OVERLAP_TIME', 'RULE_TRUE');

- `object_owner` and `object_name` must be set to `%` for `ALTER SESSION` and `ALTER SYSTEM` command rules.

- `enabled` uses the `DBMS_MACUTL.G_YES` constant to enable the command rule when it is created.

- `clause_name` sets the `ALTER SESSION` command rule to use the `SET` clause of the `ALTER SESSION` PL/SQL statement.

- `parameter_name` is set to the `ERROR_ON_OVERLAP_TIME` parameter of the `SET` clause.

- `scope` uses the `DBMS_MACUTL.G_SCOPE_COMMON` constant to set the command rule to be a common command rule. This command rule will be in the application root of a multitenant environment, so the user running this procedure must be in the CDB root. Any rules or rule sets that are associated with this command rule must be common.

  If you were creating the command rule locally, you would set `scope` to `DBMS_MACUTL.G_SCOPE_LOCAL`. In that case, the user who runs this procedure must be in the PDB in which the command rule will reside. To find the existing PDBs, you can query the `DBA_PDBS` data dictionary view. Any rules or rule sets that are associated with this command rule must be local.

ALTER SYSTEM Command Rule Using the CHECKPOINT Clause

This example shows how to create an ALTER SYSTEM command rule that users the `CHECKPOINT` clause. To have the command rule test for the `CHECKPOINT` setting, you must create a rule set and rule, similar to the ALTER SESSION command rule in the previous example. In this example, the `parameter` setting is not specified because the `CHECKPOINT` setting does not have parameters.

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE(
      command         => 'ALTER SYSTEM',
      rule_set_name   => 'Test CHECKPOINT Setting',
      object_owner    => '%',
      object_name     => '%',
      enabled         => DBMS_MACUTL.G_YES,
     clause_name     => 'CHECKPOINT',
     parameter_name  => '',
     scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

ALTER SESSION Command Rule Using the SET Clause

The following ALTER SESSION command rule uses the `SET` clause to specify an `event_name` and `component_name`. You can only use the `event_name`, `component_name`, and `action_name` parameters if the `clause_name` parameter specifies `SET`.

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE(
      command         => 'ALTER SESSION',
      rule_set_name   => 'Check Trace Events',
      object_owner    => '%',
      object_name     => '%',
      enabled         => DBMS_MACUTL.G_YES,
      clause_name     => 'SET',
      parameter_name  => 'EVENTS',
      event_name      => 'TRACE',
      component_name  => 'GCS',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

See also [ALTER SESSION and ALTER SYSTEM Command Rules](configuring-command-rules.md) for conceptual information about this topic.

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.2 CREATE_CONNECT_COMMAND_RULE Procedure

The `CREATE_CONNECT_COMMAND_RULE` procedure creates a CONNECT command rule that you can associate with a user and a rule set.

In a multitenant environment, you can create both common and local command rules.

#### Syntax

    DBMS_MACADM.CREATE_CONNECT_COMMAND_RULE(
     user_name       IN VARCHAR2,
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-4 CREATE_CONNECT_COMMAND_RULE Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`     | User to whom the CONNECT command rule will apply. If you enter the `%` wildcard, then the CONNECT command rule will be applied to every database user.<br>In a multitenant environment, if you execute this procedure in the root, then specifying `%` applies to all common users. If you run the procedure in a PDB, then it applies to all local and common users who have access to this PDB. If there are two command rules, one common and one local, and they both apply to the same object, then both must evaluate successfully for the operation to succeed.<br>In a multitenant environment, ensure that this user is common if the CONNECT command rule is common, and local or common if the CONNECT command rule is local.<br>To find existing database users in the current instance, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md). |
| `rule_set_name` | Name of rule set to associate with this command rule. In a multitenant environment, ensure that this rule set is common if the CONNECT command rule is common, and local if the CONNECT command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `enabled`       | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` (Yes) to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `scope`         | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you create the common CONNECT command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;`                                                                                                                                                                                                                                                                                                                                             |

#### Examples

The following example shows how to create a common CONNECT command rule in a multitenant environment. This command rule will be in the CDB root, so the user who runs this procedure must be in the CDB root. Any user names or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.CREATE_CONNECT_COMMAND_RULE(
      rule_set_name   => 'Allow Sessions',
      user_name       => 'C##HR_ADMIN',
      enabled         => DBMS_MACUTL.G_SIMULATION,
      scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This example is a local version of the preceding example. The user who runs this procedure must be in the PDB in which the local CONNECT command rule will reside. To find the available PDBs, run the `show pdbs` command. Any rule sets that are associated with this command rule must be local. The user can be either common or local.

    BEGIN
     DBMS_MACADM.CREATE_CONNECT_COMMAND_RULE(
     rule_set_name   => 'Allow Sessions',
     user_name       => 'PSMITH',
     enabled         => DBMS_MACUTL.G_SIMULATION,
     scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.3 CREATE_SESSION_EVENT_CMD_RULE Procedure

The `CREATE_SESSION_EVENT_CMD_RULE` procedure creates a command rule that you can associate with session events, based on the `ALTER SESSION` statement.

In a multitenant environment, you can create both session event common and local command rules.

#### Syntax

    DBMS_MACADM.CREATE_SESSION_EVENT_CMD_RULE(
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT,
     pl_sql_stack    IN BOOLEAN DEFAULT);

#### Parameters

Table 16-5 CREATE_SESSION_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`  | Name of the rule set to associate with the command rule. In a multitenant environment, ensure that this rule set is common if the session event command rule is common, and local if the command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                        |
| `enabled`        | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` (Yes) to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                    |
| `event_name`     | An event that the command rule defines. This setting enables the command rule to correspond with an `ALTER SESSION SET EVENTS` `event_name` statement. For example, to track trace events, you would set `event_name` to `TRACE`.                                                                                                                                                                                                                                                                                                             |
| `component_name` | A component of the `event_name` setting. Example settings are `DV`, `OLS`, or `GCS`.<br>You can find valid component names by issuing `ORADEBUG DOC COMPONENT RDBMS` as user `SYS`. The output displays parent and child components, which you can use for the `component_name` setting. For example, both `XS` (parent) and `XSSESSION` (child of `XS`) are valid component names. If you select the parent component, then the command rule applies to it and the child components.                                                         |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you create the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |
| `pl_sql_stack`   | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record. The default is `FALSE`.                                                                                                                                                                                                                                                                                                                                                  |

#### Examples

The following example shows how to create a common session event command rule in a multitenant environment. This command rule will be in the application root, so the user running this procedure must be in the CDB root. Any user names or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.CREATE_SESSION_EVENT_CMD_RULE(
      rule_set_name   => 'Allow Sessions',
      event_name      => 'TRACE',
      component_name  => 'DV',
      action_name     => 'CURSORTRACE',
      enabled         => DBMS_MACUTL.G_SIMULATION,
      scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This example shows how to create a session event for the 47998 trace event. This example will records the PL/SQL stack for failed operations.

    BEGIN  
     DBMS_MACADM.CREATE_SESSION_EVENT_CMD_RULE(
      rule_set_name   => 'Allow Sessions',
      event_name      => '47998',
      enabled         => 'y',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL,
      pl_sql_stack    => TRUE);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.4 CREATE_SYSTEM_EVENT_CMD_RULE Procedure

The `CREATE_SYSTEM_EVENT_CMD_RULE` procedure creates a command rule that you can associate with system events, based on the `ALTER SYSTEM` statement.

In a multitenant environment, you can create both ALTER SYSTEM common and local command rules.

#### Syntax

    DBMS_MACADM.CREATE_SYSTEM_EVENT_CMD_RULE(
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT
     pl_sql_stack    IN BOOLEAN DEFAULT);

#### Parameters

Table 16-6 CREATE_SYSTEM_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`  | Name of the rule set to associate with the command rule. In a multitenant environment, ensure that this rule set is common if the system event command rule is common, and local if the command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                         |
| `event_name`     | An event that the command rule defines. This setting enables the command rule to correspond to an `ALTER SYSTEM SET EVENTS` `event_name` statement. For example, to track trace events, you would set `event_name` to `TRACE`.                                                                                                                                                                                                                                                                                                                |
| `component_name` | A component of the `event_name` setting. Example settings are `DV`, `OLS`, or `GCS`.<br>You can find valid component names by issuing `ORADEBUG DOC COMPONENT RDBMS` as user `SYS`. The output displays parent and child components, which you can use for the `component_name` setting. For example, both `XS` (parent) and `XSSESSION` (child of `XS`) are valid component names. If you select the parent component, then the command rule applies to it and the child components.                                                         |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `enabled`        | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                          |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you create the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |
| `pl_sql_stack`   | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record. The default is `FALSE`.                                                                                                                                                                                                                                                                                                                                                  |

#### Example

The following example shows how to create a common system event command rule in a multitenant environment. This command rule will be in the application root, so the user running this procedure must be in the CDB root. Any user names or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.CREATE_SYSTEM_EVENT_CMD_RULE(
      rule_set_name   => 'Enabled',
      event_name      => 'TRACE',
      component_name  => 'GSIPC',
      action_name     => 'HEAPDUMP',
      enabled         => DBMS_MACUTL.G_YES,
      scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.5 DELETE_COMMAND_RULE Procedure

The `DELETE_COMMAND_RULE` procedure drops a command rule declaration.

#### Syntax

    DBMS_MACADM.DELETE_COMMAND_RULE(
     command         IN VARCHAR2,
     object_owner    IN VARCHAR2,
     object_name     IN VARCHAR2,
     clause_name     IN VARCHAR2,
     parameter_name  IN VARCHAR2 DEFAULT,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-7 DELETE_COMMAND_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `command`        | SQL statement the command rule protects.<br>To find available command rules, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                                 |
| `object_owner`   | Database schema to which this command rule applies.<br>To find the available users in the current database instance, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md).                                                                                          |
| `object_name`    | Object name. The wildcard `%` is allowed.<br>To find the available objects in the current database instance, query the `ALL_OBJECTS` view, described in [Oracle Database Reference](../refrn/ALL_OBJECTS.md).                                                                                              |
| `clause_name`    | A clause from the SQL statement that was used to create the command rule.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                         |
| `parameter_name` | A parameter from the `clause_name` parameter.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                     |
| `event_name`     | An event that the command rule defines.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                           |
| `component_name` | A component of the `event_name` setting.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                          |
| `action_name`    | An action of the `component_name` setting.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                        |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root |

#### Examples

When you drop a command rule, you must omit the `rule_set_name` and `enabled` parameters, and ensure that the rest of the parameters match the settings that were used the last time the command rule was updated. You can check the most recent settings by querying the `DBA_DV_COMMAND_RULE` data dictionary view.

For example, suppose you created the following command rule:

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE(
      command         => 'SELECT',
      rule_set_name   => 'Enabled',
      object_owner    => 'OE',
      object_name     => 'ORDERS',
      enabled         => DBMS_MACUTL.G_YES,
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

To drop this command rule, use the most of same parameters as shown here, but omit `rule_set_name` and `enabled`.

    BEGIN
     DBMS_MACADM.DELETE_COMMAND_RULE(
      command         => 'SELECT',
      object_owner    => 'OE',
      object_name     => 'ORDERS',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

The following example shows how to delete an `ALTER SESSION` command rule.

    BEGIN
     DBMS_MACADM.DELETE_COMMAND_RULE(
      command         => 'ALTER SESSION',
      object_owner    => '%',
      object_name     => '%',
      clause_name     => 'SET',
      parameter_name  => 'EVENTS',
      event_name      => 'TRACE',
      component_name  => 'GCS',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.6 DELETE_CONNECT_COMMAND_RULE Procedure

The `DELETE_CONNECT_COMMAND_RULE` procedure deletes a CONNECT command rule that had been created with the `CREATE_CONNECT_COMMAND_RULE` procedure.

#### Syntax

    DBMS_MACADM.DELETE_CONNECT_COMMAND_RULE(
     user_name       IN VARCHAR2,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-8 DELETE_CONNECT_COMMAND_RULE Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name` | User to whom the CONNECT command rule applied.<br>To find this user, query the `OBJECT_OWNER` field of the `DBA_DV_COMMAND_RULE` view.                                                                                                                                                                     |
| `scope`     | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_CONNECT_COMMAND_RULE(
      user_name       => 'PSMITH',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.7 DELETE_SESSION_EVENT_CMD_RULE Procedure

The `DELETE_SESSION_EVENT_CMD_RULE` procedure deletes a session command rule that was associated with events.

#### Syntax

    DBMS_MACADM.DELETE_SESSION_EVENT_CMD_RULE(
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-9 DELETE_SESSION_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_name`     | An event that the session event command rule defines.<br>[DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) for a information about existing command rules                                                                                                                         |
| `component_name` | A component of the `event_name` setting                                                                                                                                                                                                                                                                    |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                  |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root |

#### Example

The following example shows how to delete a common session event command rule in the application root a multitenant environment. The user running this procedure must be a common user in the CDB root. When you specify the parameters, ensure that they match exactly the parameters that were used the last time the command rule was updated. To find the current settings of the command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)

    BEGIN
    DBMS_MACADM.DELETE_SESSION_EVENT_CMD_RULE(
     event_name      => '47999',
     scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
     /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.8 DELETE_SYSTEM_EVENT_CMD_RULE Procedure

The `DELETE_SYSTEM_EVENT_CMD_RULE` procedure deletes a system command rule that was associated with events.

#### Syntax

    DBMS_MACADM.DELETE_SYSTEM_EVENT_CMD_RULE(
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-10 DELETE_SYSTEM_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_name`     | An event that the system event command rule defines.<br>See [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) for a information about existing command rules.                                                                                                                     |
| `component_name` | A component of the `event_name` setting                                                                                                                                                                                                                                                                    |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                  |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root |

#### Examples

The following example shows how to delete a common system event command rule in the application root of a multitenant environment. The user running this procedure must be a common user in the CDB root. When you specify the parameters, ensure that they match exactly the parameters that were used the last time the command rule was updated. To find the current settings of the command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)

    BEGIN
     DBMS_MACADM.DELETE_SYSTEM_EVENT_CMD_RULE(
     event_name      => 'TRACE',
     component_name  => 'DV',
     action_name     => '',
     scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.9 UPDATE_COMMAND_RULE Procedure

The `UPDATE_COMMAND_RULE` procedure updates a command rule declaration.

In a multitenant environment, you can update both common and local command rules.

#### Syntax

    DBMS_MACADM.UPDATE_COMMAND_RULE(
     command         IN VARCHAR2,
     rule_set_name   IN VARCHAR2,
     object_owner    IN VARCHAR2,
     object_name     IN VARCHAR2,
     enabled         IN VARCHAR2,
     privilege_scope IN NUMBER,
     clause_name     IN VARCHAR2,
     parameter_name  IN VARCHAR2 DEFAULT,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT,
     pl_sql_stack    IN BOOLEAN DEFAULT);

#### Parameters

Table 16-11 UPDATE_COMMAND_RULE Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `command`         | Command rule to update<br>See also the following:<br>• [SQL Statements That Can Be Protected by Command Rules](configuring-command-rules.md) for a listing of available SQL statements that you can use<br>• [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) for a information about existing command rules                                                                                                                                                                                                        |
| `rule_set_name`   | Name of rule set to associate with this command rule.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                           |
| `object_owner`    | Database schema to which this command rule applies.<br>To find the available users, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md). See also "Object Owner" in [Creating a Command Rule](configuring-command-rules.md) for more information.                                                                                                                                                                                                                                                     |
| `object_name`     | Object name. (The wildcard % is allowed. See "Object Name" in [Creating a Command Rule](configuring-command-rules.md) for more information about objects protected by command rules.)<br>To find the available objects, query the `ALL_OBJECTS` view, described in [Oracle Database Reference](../refrn/ALL_OBJECTS.md).                                                                                                                                                                                                                      |
| `enabled`         | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                          |
| `privilege_scope` | Obsolete parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `clause_name`     | A clause from the SQL statement that was used to create the command rule. For example, a command rule for the `ALTER SESSION` SQL statement could have the `SET` clause as the `clause_name` parameter.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                                                                                              |
| `parameter_name`  | A parameter from the `clause_name` parameter. For example, for an `ALTER SESSION` command rule, you could set `parameter_name` to `EVENTS` if the `clause_name` is `SET`.<br>Applies only to command rules for `ALTER SYSTEM` and `ALTER SESSION`.                                                                                                                                                                                                                                                                                            |
| `event_name`      | An event that the command rule defines. For example, for an `ALTER SESSION` command rule that uses `SET` for the `clause_name` and `EVENTS` as the `parameter_name`, then the `event_name` could be set to `TRACE`.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `events`.                                                                                                                                                                                                  |
| `component_name`  | A component of the `event_name` setting. For example, for a `TRACE` event, the `component_name` could be `GCS`.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `events`.                                                                                                                                                                                                                                                                                                      |
| `action_name`     | An action of the `component_name` setting. For example, if `component_name` is set to `GCS`, then the `action_name` setting could be `DISK HIGH`.<br>Applies only to `ALTER SYSTEM` and `ALTER SESSION` command rules that have the `parameter` parameter set to `events`.                                                                                                                                                                                                                                                                    |
| `scope`           | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you update the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |
| `pl_sql_stack`    | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record.                                                                                                                                                                                                                                                                                                                                                                          |

#### Examples

The following example shows how to create a simple command rule that protects the `HR.EMPLOYEES` schema.

    BEGIN
     DBMS_MACADM.UPDATE_COMMAND_RULE(
      command         => 'SELECT',
      rule_set_name   => 'Enabled',
      object_owner    => 'HR',
      object_name     => 'EMPLOYEES',
      enabled         => DBMS_MACUTL.G_SIMULATION,
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

This example shows how to update a more complex command rule, which is based on the `ALTER SESSION` SQL statement.

    BEGIN
     DBMS_MACADM.UPDATE_COMMAND_RULE(
      command         => 'ALTER SESSION',
      rule_set_name   => 'Enabled',
      object_owner    => '%',
      object_name     => '%',
      enabled         => 's',
      clause_name     => 'SET',
      parameter_name  => 'EVENTS',
      event_name      => 'TRACE',
      component_name  => 'GCS',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.10 UPDATE_CONNECT_COMMAND_RULE Procedure

The `UPDATE_CONNECT_COMMAND_RULE` procedure updates a CONNECT command rule that had been created with the `CREATE_CONNECT_COMMAND_RULE` procedure.

#### Syntax

    DBMS_MACADM.UPDATE_CONNECT_COMMAND_RULE(
     user_name       IN VARCHAR2,
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     scope           IN NUMBER DEFAULT);

#### Parameters

Table 16-12 UPDATE_CONNECT_COMMAND_RULE Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user_name`     | User to whom the CONNECT command rule will apply. If you enter the `%` wildcard, then the CONNECT command rule will be applied to every database user.<br>In a multitenant environment, if you execute this procedure in the root, then specifying `%` applies to all common users. If you run the procedure in a PDB, then it applies to all local and common users who have access to this PDB. If there are two command rules, one common and one local, and they both apply to the same object, then both must evaluate successfully for the operation to succeed.<br>In a multitenant environment, ensure that this user is common if the CONNECT command rule is common, and local or common if the CONNECT command rule is local.<br>To find existing command rules, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find existing database users in the current instance, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md). |
| `rule_set_name` | Name of rule set to associate with this command rule. In a multitenant environment, ensure that this rule set is common if the CONNECT command rule is common, and local if the CONNECT command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `enabled`       | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `scope`         | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you update the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_CONNECT_COMMAND_RULE(
      rule_set_name   => 'Allow Sessions',
      user_name       => 'PSMITH',
      enabled         => 'DBMS_MACUTL.G_YES',
      scope           => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.11 UPDATE_SESSION_EVENT_CMD_RULE Procedure

The `UPDATE_SESSION_EVENT_CMD_RULE` procedure updates a session event command rule, based on the `ALTER SESSION` statement.

In a multitenant environment, you can update both common and local session event command rules.

#### Syntax

    DBMS_MACADM.UPDATE_SESSION_EVENT_CMD_RULE(
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT,
     pl_sql_stack    IN BOOLEAN DEFAULT);

#### Parameters

Table 16-13 UPDATE_SESSION_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`  | Name of the rule set to associate with the command rule. In a multitenant environment, ensure that this rule set is common if the session event command rule is common, and local if the command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                        |
| `enabled`        | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                          |
| `event_name`     | An event that the command rule defines. This setting enables the command rule to correspond with an `ALTER SESSION SET EVENTS` `event_name` statement. For example, to track trace events, you would set `event_name` to `TRACE`.                                                                                                                                                                                                                                                                                                             |
| `component_name` | A component of the `event_name` setting. Example settings are `DV`, `OLS`, or `GCS`.<br>You can find valid component names by issuing `ORADEBUG DOC COMPONENT RDBMS` as user `SYS`. The output displays parent and child components, which you can use for the `component_name` setting. For example, both `XS` (parent) and `XSSESSION` (child of `XS`) are valid component names. If you select the parent component, then the command rule applies to it and the child components.                                                         |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you update the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |
| `pl_sql_stack`   | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record.                                                                                                                                                                                                                                                                                                                                                                          |

#### Example

The following example shows how to update a common session event command rule in a multitenant environment. This command rule is in the application root, so the user running this procedure must be in the CDB root. Any user names or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.UPDATE_SESSION_EVENT_CMD_RULE(
      rule_set_name => 'Allow Sessions',
      event_name    => '47999',
      enabled       => DBMS_MACUTL.G_NO,
      scope         => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs

### 16.12 UPDATE_SYSTEM_EVENT_CMD_RULE Procedure

The `UPDATE_SYSTEM_EVENT_CMD_RULE` procedure updates a system event command rule, based on the `ALTER SYSTEM` statement.

In a multitenant environment, you can update both common and local session event command rules.

#### Syntax

    DBMS_MACADM.UPDATE_SYSTEM_EVENT_CMD_RULE(
     rule_set_name   IN VARCHAR2,
     enabled         IN VARCHAR2,
     event_name      IN VARCHAR2 DEFAULT,
     component_name  IN VARCHAR2 DEFAULT,
     action_name     IN VARCHAR2 DEFAULT,
     scope           IN NUMBER DEFAULT,
     pl_sql_stack    IN BOOLEAN DEFAULT);

#### Parameters

Table 16-14 UPDATE_SYSTEM_EVENT_CMD_RULE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`  | Name of the rule set to associate with the command rule. In a multitenant environment, ensure that this rule set is common if the system event command rule is common, and local if the command rule is local.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                         |
| `enabled`        | Specify one of the following options to set the status of the command rule:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable the command rule (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable the command rule, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                          |
| `event_name`     | An event that the command rule defines. This setting enables the command rule to correspond to an `ALTER SYSTEM SET EVENTS` `event_name` statement. For example, to track trace events, you would set `event_name` to `TRACE`.                                                                                                                                                                                                                                                                                                                |
| `component_name` | A component of the `event_name` setting. Example settings are `DV`, `OLS`, or `GCS`.<br>You can find valid component names by issuing `ORADEBUG DOC COMPONENT RDBMS` as user `SYS`. The output displays parent and child components, which you can use for the `component_name` setting. For example, both `XS` (parent) and `XSSESSION` (child of `XS`) are valid component names. If you select the parent component, then the command rule applies to it and the child components.                                                         |
| `action_name`    | An action of the `component_name` setting                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root<br>If you update the common command rule in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;` |
| `pl_sql_stack`   | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record.                                                                                                                                                                                                                                                                                                                                                                          |

#### Example

The following example shows how to update a common system event command rule in a multitenant environment. This command rule is in the application root, so the user running this procedure must be in the CDB root. Any user names or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.UPDATE_SYSTEM_EVENT_CMD_RULE(
     rule_set_name   => 'Disabled',
     event_name      => 'TRACE',
     component_name  => 'DV',
     enabled         => 'n',
     scope           => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Command Rule APIs
