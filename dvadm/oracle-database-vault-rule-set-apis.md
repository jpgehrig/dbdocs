You can use the `DBMS_MACADM` PL/SQL package and a set of Oracle Database Vault rule functions to manage rule sets.

- DBMS_MACADM Rule Set Procedures
  The `DBMS_MACADM` rule set procedures enable you to configure both rule sets and individual rules that go within these rule sets.
- Oracle Database Vault PL/SQL Rule Set Functions
  Oracle Database Vault provides functions to use in rule sets to inspect the SQL statement that the rule set protects.

### 15.1 DBMS_MACADM Rule Set Procedures

The `DBMS_MACADM` rule set procedures enable you to configure both rule sets and individual rules that go within these rule sets.

Only users who have been granted the `DV_OWNER` or `DV_ADMIN` role can use these procedures.

- ADD_RULE_TO_RULE_SET Procedure
  The `ADD_RULE_TO_RULE_SET` procedure adds rule to a rule set; you can enable having the rule checked when the rule set is evaluated.
- CREATE_RULE Procedure
  The `CREATE_RULE` procedure creates a rule, which afterwards, can be added to a rule set.
- CREATE_RULE_SET Procedure
  The `CREATE_RULE_SET` procedure creates a rule set.
- DELETE_RULE Procedure
  The `DELETE_RULE` procedure deletes a rule.
- DELETE_RULE_FROM_RULE_SET Procedure
  The `DELETE_RULE_FROM_RULE_SET` procedure deletes a rule from a rule set.
- DELETE_RULE_SET Procedure
  The `DELETE_RULE_SET` procedure deletes a rule set.
- RENAME_RULE Procedure
  The `RENAME_RULE` procedure renames a rule and causes the name change to take effect everywhere the rule is used
- RENAME_RULE_SET Procedure
  The `RENAME_RULE_SET` procedure renames a rule set and causes the name change to take effect everywhere the rule set is used.
- UPDATE_RULE Procedure
  The `UPDATE_RULE` procedure updates a rule.
- UPDATE_RULE_SET Procedure
  The `UPDATE_RULE_SET` procedure updates a rule set.

**Related Topics**

- [Configuring Rule Sets](configuring-rule-sets.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

**Parent topic:** Oracle Database Vault Rule Set APIs

#### 15.1.1 ADD_RULE_TO_RULE_SET Procedure

The `ADD_RULE_TO_RULE_SET` procedure adds rule to a rule set; you can enable having the rule checked when the rule set is evaluated.

##### Syntax

    DBMS_MACADM.ADD_RULE_TO_RULE_SET(
     rule_set_name  IN VARCHAR2,
     rule_name      IN VARCHAR2,
     rule_order     IN NUMBER,
     enabled        IN VARCHAR2);

##### Parameters

Table 15-1 ADD_RULE_TO_RULE_SET Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name` | Rule set name.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                         |
| `rule_name`     | Rule to add to the rule set.<br>To find existing rules, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, use `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).                                                |
| `rule_order`    | Does not apply to this release, but you must include a value for the `ADD_RULE_TO_RULE_SET` procedure to work. Enter `1`.                                                                                                                                                                                                                                                                     |
| `enabled`       | Optional. Determines whether the rule should be checked when the rule set is evaluated. Possible values are:<br>• `DBMS_MACUTL.G_YES` (default). Enables the rule to be checked during the rule set evaluation.<br>• `DBMS_MACUTL.G_NO` Prevents the rule from being checked during the rule set evaluation.<br>See [Table 20-1](oracle-database-vault-utility-apis.md) for more information. |

##### Examples

The following example adds a rule to a rule set, and by omitting the `enabled` parameter, automatically enables the rule to be checked when the rule set is evaluated.

    BEGIN
     DBMS_MACADM.ADD_RULE_TO_RULE_SET(
      rule_set_name => 'Limit_DBA_Access',
      rule_name     => 'Restrict DROP TABLE operations',
      rule_order    => 1);
    END;
    /

This example adds the rule to the rule set but disables rule checking.

    BEGIN
     DBMS_MACADM.ADD_RULE_TO_RULE_SET(
      rule_set_name => 'Limit_DBA_Access',
      rule_name     => 'Check UPDATE operations',
      rule_order    => 1,
      enabled       => DBMS_MACUTL.G_NO);
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.2 CREATE_RULE Procedure

The `CREATE_RULE` procedure creates a rule, which afterwards, can be added to a rule set.

In a multitenant environment, you can create both common and local rules.

##### Syntax

    DBMS_MACADM.CREATE_RULE(
     rule_name  IN VARCHAR2,
     rule_expr  IN VARCHAR2
     scope      IN NUMBER DEFAULT);

##### Parameters

Table 15-2 CREATE_RULE Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_name` | Rule name, up to 128 characters in mixed-case. Spaces are allowed.<br>To find existing rules in the current database instance, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, query `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md). |
| `rule_expr` | PL/SQL `BOOLEAN` expression.<br>If the expression contains quotation marks, do not use double quotation marks. Instead, use two single quotation marks. Enclose the entire expression within single quotation marks. For example:<br>`'TO_CHAR(SYSDATE,''HH24'') = ''12'''`<br>See [Creating a New Rule](configuring-rule-sets.md) for more information on rule expressions.                                                     |
| `scope`     | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the rule is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the rule is in the application root                                                                                                                                       |

##### Examples

The following example shows how to create a local rule expression that checks if the current session user is `SYSADM`. The user running this procedure must be in the same PDB in which the rule and its rule set reside. To find the existing PDBs, run the `show pdbs` command. The rule and rule set must be local.

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name  => 'Check UPDATE operations',
      rule_expr  =>'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''SYSADM''',
      scope      => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

This example shows a multitenant environment common version of the preceding example. The user running this procedure must be in the CDB root, and the rule and its associated rule set must be common. The rule will reside in the application root.

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name  => 'Check UPDATE operations',
      rule_expr  =>'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''SYSADM''',
      scope      => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This example shows how to create a rule expression that uses the public standalone function `OLS_LABEL_DOMINATES` to find if the session label of the `hr_ols_pol` Oracle Label Security policy dominates or is equal to the `hs` label. The value `0` indicates if it is false. (To check if it is equal, you would specify `1`.)

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name  => 'Check OLS Factor',
      rule_expr  => 'OLS_LABEL_DOMINATES(''hr_ols_pol'', ''hs'') = 1');
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.3 CREATE_RULE_SET Procedure

The `CREATE_RULE_SET` procedure creates a rule set.

After you create a rule set, you can use the `CREATE_RULE` and `ADD_RULE_TO_RULE_SET` procedures to create and add rules to the rule set.

##### Syntax

    DBMS_MACADM.CREATE_RULE_SET(
     rule_set_name    IN VARCHAR2,
     description      IN VARCHAR2,
     enabled          IN VARCHAR2,
     eval_options     IN NUMBER,
     audit_options    IN NUMBER,
     fail_options     IN NUMBER,
     fail_message     IN VARCHAR2,
     fail_code        IN NUMBER,
     handler_options  IN NUMBER,
     handler          IN VARCHAR2,
     is_static        IN BOOLEAN DEFAULT,
     scope            IN NUMBER DEFAULT);

##### Parameters

Table 15-3 CREATE_RULE_SET Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`   | Rule set name, up to 128 characters in mixed-case. Spaces are allowed.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `description`     | Description of the purpose of the rule set, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `enabled`         | `DBMS_MACUTL.G_YES` (Yes) enables the rule set; `DBMS_MACUTL.G_NO` (No) disables it. The default is `DBMS_MACUTL.G_YES`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `eval_options`    | If you plan to assign multiple rules to the rule set, enter one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_EVAL_ALL`: All rules in the rule set must evaluate to true for the rule set itself to evaluate to true (default).<br>• `DBMS_MACUTL.G_RULESET_EVAL_ANY`: At least one rule in the rule set must evaluate to true for the rule set itself to evaluate to true.                                                                                                                                                                                                                                                                                               |
| `audit_options`   | Select one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_AUDIT_OFF`: Disables auditing for the rule set (default)<br>• `DBMS_MACUTL.G_RULESET_AUDIT_FAIL`: Creates an audit record when a rule set violation occurs<br>• `DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS`: Creates an audit record for a successful rule set evaluation<br>• `DBMS_MACUTL.G_RULESET_AUDIT_FAIL + DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS`: Creates an audit record for both successful and failed rule set evaluations<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`. |
| `fail_options`    | Options for reporting errors:<br>• `DBMS_MACUTL.G_RULESET_FAIL_SHOW`: Shows an error message (default)<br>• `DBMS_MACUTL.G_RULESET_FAIL_SILENT`: Does not show an error message                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `fail_message`    | Enter an error message for failure, up to 80 characters in mixed-case, to associate with the fail code you specify for `fail_code`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `fail_code`       | Enter a number in the range of -20000 to -20999 or 20000 to 20999 to associate with the `fail_message` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `handler_options` | Select one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_HANDLER_OFF`: Disables error handling (default)<br>• `DBMS_MACUTL.G_RULESET_HANDLER_FAIL`: Calls handler on rule set failure<br>• `DBMS_MACUTL.G_RULESET_HANDLER_SUCCESS`: Calls handler on rule set success                                                                                                                                                                                                                                                                                                                                                                                                     |
| `handler`         | Name of the PL/SQL function or procedure that defines the custom event handler logic.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `is_static`       | Optional. Determines how often a rule set is evaluated when it is accessed. The default is `FALSE`.<br>• `TRUE`: The rule set is evaluated once during the user session. After that, the value is re-used.<br>• `FALSE`: The rule set is evaluated every time.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `scope`           | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the rule set is to be local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the rule set is to be in the application root                                                                                                                                                                                                                                                                                                                                                                     |

##### Examples

The following example creates a rule set that is enabled, is set so that at least one rule must evaluate to true for the rule set itself to evaluate to true, and audits both failed and successful attempts. It does not show error messages but uses the fail code 20461 to track failures. It also uses a handler to send email alerts to the appropriate users if their are violations to the rule set.

    BEGIN
     DBMS_MACADM.CREATE_RULE_SET(
      rule_set_name    => 'Limit_DBA_Access',
      description      => 'DBA access through predefined processes',
      enabled          => DBMS_MACUTL.G_YES,
      eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ANY,
      audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL + DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS,
      fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SILENT,
      fail_message     => '',
      fail_code        => 20461,
      handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_FAIL,
      handler          => 'dbavowner.email_alert',
      is_static        => TRUE);
    END;
    /

This rule set uses no fail messages or fail codes, nor does it use any handlers. This rule set will be in the application root of a multitenant environment, so the user running this procedure must be in the application root. Any rules or command rules that are associated with this rule set must be common.

    BEGIN
     DBMS_MACADM.CREATE_RULE_SET(
     rule_set_name    => 'Check_HR_Access',
     description      => 'Checks for failed access attempts to the HR schema',
     enabled          => DBMS_MACUTL.G_YES,
     eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ANY,
     audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL,
     fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SILENT,
     fail_message     => '',
     fail_code        => '',
     handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_OFF,
     handler          => '',
     is_static        => TRUE,
     scope            => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This rule set is a local version of the preceding rule set. The user who creates this rule set must be in the PDB in which this rule set will reside. To find the existing PDBs, query the `DBA_PDBS` data dictionary view. Any rules or command rules that are associated with this rule set must be local.

    BEGIN
     DBMS_MACADM.CREATE_RULE_SET(
     rule_set_name    => 'Check_HR_Access',
     description      => 'Checks for failed access attempts to the HR schema',
     enabled          => DBMS_MACUTL.G_YES,
     eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ANY,
     audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL,
     fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SILENT,
     fail_message     => '',
     fail_code        => '',
     handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_OFF,
     handler          => '',
     is_static        => TRUE,
     scope            => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**See Also:**

[Example 20-2](oracle-database-vault-utility-apis.md)

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.4 DELETE_RULE Procedure

The `DELETE_RULE` procedure deletes a rule.

##### Syntax

    DBMS_MACADM.DELETE_RULE(
     rule_name IN VARCHAR2);

##### Parameter

Table 15-4 DELETE_RULE Parameter

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                              |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_name` | Rule name.<br>To find existing rules in the current database instance, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, query `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXEC DBMS_MACADM.DELETE_RULE('Check UPDATE operations');

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.5 DELETE_RULE_FROM_RULE_SET Procedure

The `DELETE_RULE_FROM_RULE_SET` procedure deletes a rule from a rule set.

##### Syntax

    DBMS_MACADM.DELETE_RULE_FROM_RULE_SET(
     rule_set_name IN VARCHAR2,
     rule_name     IN VARCHAR2);

##### Parameters

Table 15-5 DELETE_RULE_FROM_RULE_SET Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name` | Rule set name.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                           |
| `rule_name`     | Rule to remove from the rule set.<br>To find existing rules in the current database instance, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, query `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.DELETE_RULE_FROM_RULE_SET(
      rule_set_name => 'Limit_DBA_Access',
      rule_name     => 'Check UPDATE operations');
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.6 DELETE_RULE_SET Procedure

The `DELETE_RULE_SET` procedure deletes a rule set.

##### Syntax

    DBMS_MACADM.DELETE_RULE_SET(
     rule_set_name IN VARCHAR2);

##### Parameters

Table 15-6 DELETE_RULE_SET Parameter

| Parameter       | Description                                                                                                                                                                                           |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name` | Rule set name.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXEC DBMS_MACADM.DELETE_RULE_SET('Limit_DBA_Access');

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.7 RENAME_RULE Procedure

The `RENAME_RULE` procedure renames a rule and causes the name change to take effect everywhere the rule is used

##### Syntax

    DBMS_MACADM.RENAME_RULE(
     rule_name  IN VARCHAR2,
     new_name   IN VARCHAR2);

##### Parameters

Table 15-7 RENAME_RULE Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_name` | Current rule name.<br>To find existing rules in the current database instance, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, query `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md). |
| `new_name`  | New rule name, up to 128 characters in mixed-case.                                                                                                                                                                                                                                                                                                                               |

##### Example

    BEGIN
     DBMS_MACADM.RENAME_RULE(
      rule_name  => 'Check UPDATE operations',
      new_name   => 'Check Sector 2 Processes');
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.8 RENAME_RULE_SET Procedure

The `RENAME_RULE_SET` procedure renames a rule set and causes the name change to take effect everywhere the rule set is used.

##### Syntax

    DBMS_MACADM.RENAME_RULE_SET(
     rule_set_name IN VARCHAR2,
     new_name      IN VARCHAR2,
     scope         IN NUMBER DEFAULT);

##### Parameters

Table 15-8 RENAME_RULE_SET Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                        |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name` | Current rule set name.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                      |
| `new_name`      | New rule set name, up to 128 characters in mixed-case. Spaces are allowed.                                                                                                                                                                                                                         |
| `scope`         | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the rule set is local in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the rule set is in the application root |

##### Example

    BEGIN
     DBMS_MACADM.RENAME_RULE_SET(
      rule_set_name => 'Limit_DBA_Access',
      new_name      => 'Limit Sector 2 Access');
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.9 UPDATE_RULE Procedure

The `UPDATE_RULE` procedure updates a rule.

##### Syntax

    DBMS_MACADM.UPDATE_RULE(
     rule_name  IN VARCHAR2,
     rule_expr  IN VARCHAR2);

##### Parameters

Table 15-9 UPDATE_RULE Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_name` | Rule name.<br>To find existing rules in the current database instance, query the `DBA_DV_RULE` view, described in [DBA_DV_RULE View](oracle-database-vault-data-dictionary-views.md).<br>To find rules that have been associated with rule sets, query `DBA_DV_RULE_SET_RULE`, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md).                                                                         |
| `rule_expr` | PL/SQL `BOOLEAN` expression.<br>If the expression contains quotation marks, do not use double quotation marks. Instead, use two single quotation marks. Enclose the entire expression within single quotation marks. For example:<br>`'TO_CHAR(SYSDATE,''HH24'') = ''12'''`<br>See [Creating a New Rule](configuring-rule-sets.md) for more information on rule expressions.<br>To find existing rule expressions, query the `DBA_DV_RULE` view. |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_RULE(
      rule_name  => 'Check UPDATE operations',
      rule_expr  =>'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''SYSADM'' AND
                   (
                     UPPER(SYS_CONTEXT(''USERENV'',''MODULE'')) LIKE ''APPSRVR%'' OR
                     UPPER(SYS_CONTEXT(''USERENV'',''MODULE'')) LIKE ''DBAPP%'' )'
                   );
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

#### 15.1.10 UPDATE_RULE_SET Procedure

The `UPDATE_RULE_SET` procedure updates a rule set.

##### Syntax

    DBMS_MACADM.UPDATE_RULE_SET(
     rule_set_name    IN VARCHAR2,
     description      IN VARCHAR2,
     enabled          IN VARCHAR2,
     eval_options     IN NUMBER,
     audit_options    IN NUMBER,
     fail_options     IN NUMBER,
     fail_message     IN VARCHAR2,
     fail_code        IN NUMBER,
     handler_options  IN NUMBER,
     handler          IN VARCHAR2,
     is_static        IN BOOLEAN DEFAULT);

##### Parameters

Table 15-10 UPDATE_RULE_SET Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `rule_set_name`   | Rule set name.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `description`     | Description of the purpose of the rule set, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `enabled`         | `DBMS_MACUTL.G_YES` (Yes) enables rule set checking; `DBMS_MACUTL.G_NO` (No) disables it.<br>The default for the `enabled` setting is the previously set value, which you can find by querying the `DBA_DV_RULE_SET` data dictionary view.                                                                                                                                                                                                                                                                                                                                                                                        |
| `eval_options`    | If you plan to assign multiple rules to the rule set, enter one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_EVAL_ALL`: All rules in the rule set must evaluate to true for the rule set itself to evaluate to true.<br>• `DBMS_MACUTL.G_RULESET_EVAL_ANY`: At least one rule in the rule set must evaluate to true for the rule set itself to evaluate to true.<br>The default for `eval_options` is the previously set value, which you can find by querying the `DBA_DV_RULE_SET` data dictionary view.                                                                                                              |
| `audit_options`   | Select one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_AUDIT_OFF`: Disables auditing for the rule set<br>• `DBMS_MACUTL.G_RULESET_AUDIT_FAIL`: Creates an audit record when a rule set violation occurs<br>• `DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS`: Creates an audit record for a successful rule set evaluation<br>• `DBMS_MACUTL.G_RULESET_AUDIT_FAIL + DBMS_MACUTL.G_RULESET_AUDIT_SUCCESS`: Creates an audit record for both successful and failed rule set evaluations<br>The default for `audit_options` is the previously set value, which you can find by querying the `DBA_DV_RULE_SET` data dictionary view. |
| `fail_options`    | Options for reporting errors:<br>• `DBMS_MACUTL.G_RULESET_FAIL_SHOW`: Shows an error message.<br>• `DBMS_MACUTL.G_RULESET_FAIL_SILENT`: Does not show an error message.<br>The default for `fail_options` is the previously set value, which you can find by querying the `DBA_DV_RULE_SET` data dictionary view.                                                                                                                                                                                                                                                                                                                 |
| `fail_message`    | Error message for failure, up to 80 characters in mixed-case, to associate with the fail code you specify for `fail_code`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `fail_code`       | Enter a number in the range of -20000 to -20999 or 20000 to 20999 to associate with the `fail_message` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `handler_options` | Select one of the following settings:<br>• `DBMS_MACUTL.G_RULESET_HANDLER_OFF`: Disables error handling.<br>• `DBMS_MACUTL.G_RULESET_HANDLER_FAIL`: Call handler on rule set failure.<br>• `DBMS_MACUTL.G_RULESET_HANDLER_SUCCESS`: Call handler on rule set success.<br>The default for `handler_options` is the previously set value, which you can find by querying the `DBA_DV_RULE_SET` data dictionary view.                                                                                                                                                                                                                |
| `handler`         | Name of the PL/SQL function or procedure that defines the custom event handler logic.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `is_static`       | Optional. Determines how often a rule set is evaluated when it is accessed by a SQL statement. The default is `FALSE`.<br>• `TRUE`: The rule set is evaluated once during the user session. After that, the value is re-used.<br>• `FALSE`: The rule set evaluated each time a SQL statement accesses it.                                                                                                                                                                                                                                                                                                                         |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_RULE_SET(
      rule_set_name    => 'Limit_DBA_Access',
      description      => 'DBA access through predefined processes',
      enabled          => DBMS_MACUTL.G_YES,
      eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ANY,
      audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL,
      fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SHOW,
      fail_message     => 'Access denied!',
      fail_code        => 20900,
      handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_OFF,
      handler          => '',
      is_static        =  TRUE);
    END;
    /

**Parent topic:** DBMS_MACADM Rule Set Procedures

### 15.2 Oracle Database Vault PL/SQL Rule Set Functions

Oracle Database Vault provides functions to use in rule sets to inspect the SQL statement that the rule set protects.

- DV_SYSEVENT Function
  The `DV_SYSEVENT` function returns the system event firing the rule set. .
- DV_LOGIN_USER Function
  The `DV_LOGIN_USER` function returns the session user name, in `VARCHAR2` data type.
- DV_INSTANCE_NUM Function
  The `DV_INSTANCE_NUM` function returns the database instance number, in `NUMBER` data type.
- DV_DATABASE_NAME Function
  The `DV_DATABASE_NAME` function returns the database name, in `VARCHAR2` data type.
- DV_DICT_OBJ_TYPE Function
  The `DV_DICT_OBJ_TYPE` function returns the type of the dictionary object on which the database operation occurred.
- DV_DICT_OBJ_OWNER Function
  The `DV_DICT_OBJ_OWNER` function returns the name of the owner of the dictionary object on which the database operation occurred.
- DV_DICT_OBJ_NAME Function
  The `DV_DICT_OBJ_NAME` function returns the name of the dictionary object on which the database operation occurred.
- DV_SQL_TEXT Function
  The `DV_SQL_TEXT` function returns the first 4000 characters of SQL text of the database statement used in the operation.

**Parent topic:** Oracle Database Vault Rule Set APIs

#### 15.2.1 DV_SYSEVENT Function

The `DV_SYSEVENT` function returns the system event firing the rule set. .

The event name is the same as that in the syntax of the SQL statement (for example, `INSERT`, `CREATE`.) The return type is `VARCHAR2`.

##### Syntax

    DV_SYSEVENT ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get System Event Firing the Maintenance Rule Set',
      rule_expr => 'DV_SYSEVENT = ''CREATE''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.2 DV_LOGIN_USER Function

The `DV_LOGIN_USER` function returns the session user name, in `VARCHAR2` data type.

##### Syntax

    DV_LOGIN_USER ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Session User Name',
      rule_expr => 'DV_LOGIN_USER = ''SEBASTIAN''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.3 DV_INSTANCE_NUM Function

The `DV_INSTANCE_NUM` function returns the database instance number, in `NUMBER` data type.

##### Syntax

    DV_INSTANCE_NUM ()
    RETURN NUMBER;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database Instance Number',
      rule_expr => 'DV_INSTANCE_NUM BETWEEN 6 AND 9');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.4 DV_DATABASE_NAME Function

The `DV_DATABASE_NAME` function returns the database name, in `VARCHAR2` data type.

##### Syntax

    DV_DATABASE_NAME ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database Name',
      rule_expr => 'DV_DATABASE_NAME = ''ORCL''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.5 DV_DICT_OBJ_TYPE Function

The `DV_DICT_OBJ_TYPE` function returns the type of the dictionary object on which the database operation occurred.

For example, dictionary objects it returns are table, procedure, or view. The return type is `VARCHAR2`.

##### Syntax

    DV_DICT_OBJ_TYPE ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Dictionary Object Type',
      rule_expr => 'DV_DICT_OBJ_TYPE IN (''TABLE'', ''VIEW'')');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.6 DV_DICT_OBJ_OWNER Function

The `DV_DICT_OBJ_OWNER` function returns the name of the owner of the dictionary object on which the database operation occurred.

The return type is `VARCHAR2`.

##### Syntax

    DV_DICT_OBJ_OWNER ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Dictionary Object Owner',
      rule_expr => 'DV_DICT_OBJ_OWNER = ''JSMITH''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.7 DV_DICT_OBJ_NAME Function

The `DV_DICT_OBJ_NAME` function returns the name of the dictionary object on which the database operation occurred.

The return type is `VARCHAR2`.

##### Syntax

    DV_DICT_OBJ_NAME ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Dictionary Object Name',
      rule_expr => 'DV_DICT_OBJ_NAME = ''SALES''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions

#### 15.2.8 DV_SQL_TEXT Function

The `DV_SQL_TEXT` function returns the first 4000 characters of SQL text of the database statement used in the operation.

The return type is `VARCHAR2`.

##### Syntax

    DV_SQL_TEXT ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check SQL Text',
      rule_expr => 'DV_SQL_TEXT = ''SELECT SALARY FROM HR.EMPLOYEES''');
    END;
    /

**Parent topic:** Oracle Database Vault PL/SQL Rule Set Functions
