You can use the `DBMS_MACADM` PL/SQL package to manage Oracle Database Vault policies.

Only users who have been granted the `DV_OWNER` or `DV_ADMIN` role can use these procedures.

- ADD_CMD_RULE_TO_POLICY Procedure
  The `ADD_COMMAND_RULE_TO_POLICY` procedure enables you to add an existing command rule to an Oracle Database Vault policy.
- ADD_OWNER_TO_POLICY Procedure
  The `ADD_OWNER_TO_POLICY` procedure enables you to add an existing database user to an Oracle Database Vault policy as an owner.
- ADD_REALM_TO_POLICY Procedure
  The `ADD_REALM_TO_POLICY` procedure enables you to add an existing realm to an Oracle Database Vault policy.
- CREATE_POLICY Procedure
  The `CREATE_POLICY` procedure enables you to create an Oracle Database Vault policy.
- DELETE_CMD_RULE_FROM_POLICY Procedure
  The `DELETE_CMD_RULE_FROM_POLICY` procedure enables you to remove an existing command rule from an Oracle Database Vault policy.
- DELETE_OWNER_FROM_POLICY Procedure
  The `DELETE_OWNER_FROM_POLICY` procedure enables you to remove an owner from an Oracle Database Vault policy.
- DELETE_REALM_FROM_POLICY Procedure
  The `DELETE_REALM_FROM_POLICY` procedure enables you to remove an existing realm from an Oracle Database Vault policy.
- DROP_POLICY Procedure
  The `DROP_POLICY` procedure enables you to drop an existing Oracle Database Vault policy.
- RENAME_POLICY Procedure
  The `UPDATE_POLICY_DESCRIPTION` procedure enables you to rename an existing Oracle Database Vault policy.
- UPDATE_POLICY_DESCRIPTION Procedure
  The `UPDATE_POLICY_DESCRIPTION` procedure enables you to update the `description` field in an Oracle Database Vault policy.
- UPDATE_POLICY_STATE Procedure
  The `UPDATE_POLICY_STATE` procedure enables you to update the `policy_state` field in an Oracle Database Vault policy.

**Related Topics**

- [Configuring Oracle Database Vault Policies](configuring-oracle-database-vault-policies.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

### 22.1 ADD_CMD_RULE_TO_POLICY Procedure

The `ADD_COMMAND_RULE_TO_POLICY` procedure enables you to add an existing command rule to an Oracle Database Vault policy.

You can add a command rule to a policy when the command rule is in any state. For example, you can add a disabled command rule to an enabled policy. In this case, the disabled command rule will automatically become enabled when it is added to the policy. A command rules can be added to only one policy. In other words, you cannot assign the same command rule to multiple policies.

#### Syntax

    DBMS_MACADM.ADD_CMD_RULE_TO_POLICY(
     policy_name    IN VARCHAR2,
     command        IN VARCHAR2,
     object_owner   IN VARCHAR2,
     object_name    IN VARCHAR2,
     clause_name    IN VARCHAR2 DEFAULT,
     parameter_name IN VARCHAR2 DEFAULT,
     event_name     IN VARCHAR2 DEFAULT,
     component_name IN VARCHAR2 DEFAULT,
     action_name    IN VARCHAR2 DEFAULT,
     scope          IN NUMBER DEFAULT);

#### Parameters

Table 22-1 ADD_CMD_RULE_TO_POLICY Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                     |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                      |
| `command`        | Command rule name<br>To find existing Database Vault command rules in the current database instance, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md).                                                                             |
| `object_owner`   | Database schema to which the command rule applies<br>To find existing object owners for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                        |
| `object_name`    | Object to be protected by the command rule<br>To find existing objects for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                     |
| `clause_name`    | For `ALTER SYSTEM` and `ALTER SESSION` command rules, a clause from the SQL statement that was used to create the command rule<br>To find existing clauses for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) |
| `parameter_name` | For `ALTER SYSTEM` and `ALTER SESSION` command rules, a parameter from the `clause_name` parameter.<br>To find existing parameters for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                         |
| `event_name`     | For `ALTER SYSTEM` and `ALTER SESSION` command rules, an event that the command rule defines<br>To find existing event names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                               |
| `component_name` | A component of the `event_name` setting<br>To find existing component names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                |
| `action_name`    | An action of the `component_name` setting.<br>To find existing action names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule applies to all the PDBs         |

#### Example

The following example shows how to add a common command rule to a Database Vault policy. This command rule is in the application root of a multitenant environment, so the user running this procedure must be in the application root or the CDB root. Any rules or rule sets that are associated with this command rule must be common.

    BEGIN
     DBMS_MACADM.ADD_CMD_RULE_TO_POLICY(
      policy_name    => 'HR_DV_Policy',
      command        => 'ALTER SESSION',
      object_owner   => '%',
      object_name    => '%',
      clause_name    => 'PARALLEL DDL',
      parameter_name => '',
      event_name     => '',
      action_name    => '',
      scope          => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.2 ADD_OWNER_TO_POLICY Procedure

The `ADD_OWNER_TO_POLICY` procedure enables you to add an existing database user to an Oracle Database Vault policy as an owner.

When you add an owner to an enabled policy, the change takes place immediately. There is no limit to the number of users that you add to the policy.

#### Syntax

    DBMS_MACADM.ADD_OWNER_TO_POLICY(
      policy_name   IN VARCHAR2,
      owner_name    IN VARCHAR2);

#### Parameters

Table 22-2 ADD_OWNER_TO_POLICY Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                 |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                  |
| `owner_name`  | User name. To find existing database users (not roles) in the current instance, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md). To find existing policy owners, query the `DBA_DV_POLICY_OWNER` view, described in [DBA_DV_POLICY_OWNER View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    BEGIN
     DBMS_MACADM.ADD_OWNER_TO_POLICY(
      policy_name    => 'HR_DV_Policy',
      owner_name     => 'PSMITH');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.3 ADD_REALM_TO_POLICY Procedure

The `ADD_REALM_TO_POLICY` procedure enables you to add an existing realm to an Oracle Database Vault policy.

You can add a disabled realm to an enabled policy. In this case, the realm automatically becomes enabled when it is added. A realm can be added to only one policy. In other words, you cannot assign the same realm to multiple policies.

#### Syntax

    DBMS_MACADM.ADD_REALM_TO_POLICY(
      policy_name   IN VARCHAR2,
      realm_name    IN VARCHAR2);

#### Parameters

Table 22-3 ADD_REALM_TO_POLICY Parameters

| Parameter     | Description                                                                                                             |
|:--------------|:------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view. |
| `realm_name`  | Realm name. To find existing Database Vault realms in the current database instance.                                    |

#### Example

    BEGIN
     DBMS_MACADM.ADD_REALM_TO_POLICY(
      policy_name    => 'HR_DV_Policy',
      realm_name     => 'HR Realm');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.4 CREATE_POLICY Procedure

The `CREATE_POLICY` procedure enables you to create an Oracle Database Vault policy.

After you create the policy, you must add at least one realm and one command rule to the policy. Optionally, you can set these realms and command rules to be enforced individually or use the enforcement that the policy uses.

An owner for the policy is not required, but if you do not assign an owner to the policy, a user who has been granted the `DV_OWNER` or `DV_ADMIN` role must administer the policy.

After you create the policy, use the following procedures to complete the policy definition:

- `ADD_REALM_TO_POLICY` adds realms to the policy.

- `ADD_CMD_RULE_TO_POLICY` adds command rules to the policy.

- `ADD_OWNER_TO_POLICY` enables the specified database users to manage the policy.

#### Syntax

    DBMS_MACADM.CREATE_POLICY(
     policy_name  IN VARCHAR2,
     description  IN VARCHAR2 DEFAULT,
     policy_state IN NUMBER,
     pl_sql_stack IN BOOLEAN DEFAULT);

#### Parameters

Table 22-4 CREATE_POLICY Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`  | Policy name, up to 128 characters in mixed case<br>To find existing policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `description`  | Description of the purpose of the policy, up to 4000 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `policy_state` | Specifies how the policy is enabled. Possible values are:<br>• `DBMS_MACADM.G_ENABLED` (`1`), which enables the policy after you create it<br>• `DBMS_MACADM.G_DISABLED` (`0`), which disables the policy after you create it<br>• `DBMS_MACADM.G_SIMULATION` (`2`), which sets the policy to simulation mode. In simulation mode, any violations to realms or command rules used in the policy are logged in a designated log table with sufficient information to describe the error, such as the user name or SQL statement used.<br>• `DBMS_MACADM.G_PARTIAL` (`3`), which sets the policy to partial mode. In partial mode, the enforcement state of realms or command rules associated with the policy can be changed individually.<br>See [About Simulation Mode](using-training-mode-to-log-realm-and-command-rule-activities.md) for more information about simulation mode |
| `pl_sql_stack` | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

#### Example

The following example creates a policy that uses the partial state and enables the capture of the PL/SQL stack. Later on, when a realm or a command rule is added to this policy, their enforcement state will be able to be changed individually.

    BEGIN
     DBMS_MACADM.CREATE_POLICY(
      policy_name  => 'HR_DV_Policy',
      description  => 'Policy to protect the HR schema',
      policy_state => DBMS_MACADM.G_ENABLED,
      pl_sql_stack => TRUE);
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.5 DELETE_CMD_RULE_FROM_POLICY Procedure

The `DELETE_CMD_RULE_FROM_POLICY` procedure enables you to remove an existing command rule from an Oracle Database Vault policy.

You can remove command rules from a policy anytime regardless of the state of the policy. When a command rule is removed from a policy, the state of command rule remains the same. That is, if the policy is enabled, and a command rule is removed from the policy, then the command rule will be still enabled after you have removed it from the policy.

#### Syntax

    DBMS_MACADM.DELETE_CMD_RULE_FROM_POLICY(
     policy_name    IN VARCHAR2,
     command        IN VARCHAR2,
     object_owner   IN VARCHAR2,
     object_name    IN VARCHAR2,
     clause_name    IN VARCHAR2 DEFAULT,
     parameter_name IN VARCHAR2 DEFAULT,
     event_name     IN VARCHAR2 DEFAULT,
     component_name IN VARCHAR2 DEFAULT,
     action_name    IN VARCHAR2 DEFAULT,
     scope          IN NUMBER DEFAULT);

#### Parameters

Table 22-5 DELETE_CMD_RULE_FROM_POLICY Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                     |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                      |
| `command`        | Command rule name<br>To find existing Database Vault command rules in the current database instance, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md).                                                                             |
| `object_owner`   | Database schema to which the command rule applies<br>To find existing object owners for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                        |
| `object_name`    | Object to be protected by the command rule<br>To find existing objects for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                     |
| `clause_name`    | For `ALTER SYSTEM` and `ALTER SESSION` command rules, a clause from the SQL statement that was used to create the command rule<br>To find existing clauses for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md) |
| `parameter_name` | For `ALTER SYSTEM` and `ALTER SESSION` command rules, a parameter from the `clause_name` parameter.<br>To find existing parameters for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                         |
| `event_name`     | For `ALTER SYSTEM` and `ALTER SESSION` command rules, an event that the command rule defines<br>To find existing event names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                               |
| `component_name` | A component of the `event_name` setting<br>To find existing component names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                |
| `action_name`    | An action of the `component_name` setting.<br>To find existing action names for this command rule, query the `DBA_DV_COMMAND_RULE` view, described in [DBA_DV_COMMAND_RULE View](oracle-database-vault-data-dictionary-views.md)                                                                                |
| `scope`          | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the command rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the command rule is in the application root      |

#### Example

The following example shows how to delete a common command rule from a Database Vault policy. This command rule is in the application root of a multitenant environment, so the user running this procedure must be in the CDB root.

    BEGIN
     DBMS_MACADM.DELETE_CMD_RULE_FROM_POLICY(
      policy_name    => 'HR_DV_Policy',
      command        => 'ALTER SESSION',
      object_owner   => '%',
      object_name    => '%',
      clause_name    => 'END SESSION',
      parameter_name => 'KILL SESSION',
      event_name     => '',
      action_name    => '',
      scope          => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.6 DELETE_OWNER_FROM_POLICY Procedure

The `DELETE_OWNER_FROM_POLICY` procedure enables you to remove an owner from an Oracle Database Vault policy.

You can remove owners from policies any time, regardless of the state (enabled or disabled) of the policy. The change takes effect immediately.

#### Syntax

    DBMS_MACADM.DELETE_OWNER_FROM_POLICY(
      policy_name   IN VARCHAR2,
      owner_name    IN VARCHAR2);

#### Parameters

Table 22-6 DELETE_OWNER_FROM_POLICY Parameters

| Parameter     | Description                                                                                                                                                                                                |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `owner_name`  | User name. To find existing policy owners in the current instance, query the `DBA_DV_POLICY_OWNER` view, described in [DBA_DV_POLICY_OWNER View](oracle-database-vault-data-dictionary-views.md).          |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_OWNER_FROM_POLICY(
      policy_name    => 'HR_DV_Policy',
      owner_name     => 'PSMITH');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.7 DELETE_REALM_FROM_POLICY Procedure

The `DELETE_REALM_FROM_POLICY` procedure enables you to remove an existing realm from an Oracle Database Vault policy.

You can remove realms from policies any time, regardless of the state (enabled or disabled) of the policy. The change takes effect immediately.

#### Syntax

    DBMS_MACADM.DELETE_REALM_FROM_POLICY(
      policy_name   IN VARCHAR2,
      realm_name    IN VARCHAR2);

#### Parameters

Table 22-7 DELETE_REALM_FROM_POLICY Parameters

| Parameter     | Description                                                                                                             |
|:--------------|:------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view. |
| `realm_name`  | Realm name. To find existing Database Vault realms in the current database instance, query the `DV_REALM` view.         |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_REALM_FROM_POLICY(
      policy_name    => 'HR_DV_Policy',
      realm_name     => 'HR Realm');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.8 DROP_POLICY Procedure

The `DROP_POLICY` procedure enables you to drop an existing Oracle Database Vault policy.

You can remove a policy at any time, regardless of the state (enabled or disabled) of the policy.

#### Syntax

    DBMS_MACADM.DROP_POLICY(
      policy_name      IN VARCHAR2);

#### Parameters

Table 22-8 DROP_POLICY Parameters

| Parameter     | Description                                                                                                                                                                                                |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    BEGIN
     DBMS_MACADM.DROP_POLICY(
      policy_name      => 'HR_DV_Policy');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.9 RENAME_POLICY Procedure

The `UPDATE_POLICY_DESCRIPTION` procedure enables you to rename an existing Oracle Database Vault policy.

You can rename a policy at any time, regardless of the state (enabled or disabled) of the policy. The change takes effect immediately.

#### Syntax

    DBMS_MACADM.RENAME_POLICY(
      policy_name      IN VARCHAR2,
      new_policy_name  IN VARCHAR2);

#### Parameters

Table 22-9 RENAME_POLICY Parameters

| Parameter         | Description                                                                                                                                                                                                |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `new_policy_name` | New policy name, up to 128 characters in mixed case                                                                                                                                                        |

#### Example

    BEGIN
     DBMS_MACADM.RENAME_POLICY(
      policy_name      => 'HR_DV_Policy',
      new_policy_name  => 'HR_WEST_COAST_DV_Policy');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.10 UPDATE_POLICY_DESCRIPTION Procedure

The `UPDATE_POLICY_DESCRIPTION` procedure enables you to update the `description` field in an Oracle Database Vault policy.

#### Syntax

    DBMS_MACADM.UPDATE_POLICY_DESCRIPTION(
      policy_name  IN VARCHAR2,
      description  IN VARCHAR2 DEFAULT);

#### Parameters

Table 22-10 UPDATE_POLICY_DESCRIPTION Parameters

| Parameter     | Description                                                                                                                                                                                                |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `description` | New description of the purpose of the policy, up to 4000 characters in mixed-case                                                                                                                          |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_POLICY_DESCRIPTION(
      policy_name  => 'HR_DV_Policy',
      description  => 'HR schema protection policy');
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs

### 22.11 UPDATE_POLICY_STATE Procedure

The `UPDATE_POLICY_STATE` procedure enables you to update the `policy_state` field in an Oracle Database Vault policy.

#### Syntax

    DBMS_MACADM.UPDATE_POLICY_STATE(
      policy_name   IN VARCHAR2,
      policy_state  IN NUMBER,
     pl_sql_stack  IN BOOLEAN DEFAULT);

#### Parameters

Table 22-11 UPDATE_POLICY_STATE Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`  | Policy name. To find existing Database Vault policies in the current database instance, query the `DBA_DV_POLICY` view, described in [DBA_DV_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `policy_state` | Specifies how the policy is enabled. Possible values are:<br>• `DBMS_MACADM.G_ENABLED` (`1`), which enables the policy after you create it<br>• `DBMS_MACADM.G_DISABLED` (`0`), which disables the policy after you create it<br>• `DBMS_MACADM.G_SIMULATION` (`2`), which sets the policy to simulation mode. In simulation mode, any violations to realms or command rules used in the policy are logged in a designated log table with sufficient information to describe the error, such as the user name or SQL statement used.<br>• `DBMS_MACADM.G_PARTIAL` (`3`), which sets the policy to partial mode. In partial mode, the enforcement state of realms or command rules associated with the policy can be changed individually.<br>See [About Simulation Mode](using-training-mode-to-log-realm-and-command-rule-activities.md) for more information about simulation mode |
| `pl_sql_stack` | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_POLICY_STATE(
      policy_name   => 'HR_DV_Policy',
      policy_state  => DBMS_MACADM.G_DISABLED,
      pl_sql_stack  => TRUE);
    END;
    /

**Parent topic:** Oracle Database Vault Policy APIs
