Oracle Label Security provides a set of PL/SQL packages.

- SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package
  For a non-unified auditing environment, the `SA_AUDIT_ADMIN` PL/SQL package configures auditing that is specific to Oracle Label Security.
- SA_COMPONENTS Label Components PL/SQL Package
  The `SA_COMPONENTS` PL/SQL package manages the component definitions of an Oracle Label Security label.
- SA_LABEL_ADMIN Label Management PL/SQL Package
  The `SA_LABEL_ADMIN` PL/SQL package provides an administrative interface to manage the labels used by a policy.
- SA_POLICY_ADMIN Policy Administration PL/SQL Package
  The `SA_POLICY_ADMIN` PL/SQL package manages Oracle Label Security policies as a whole.
- SA_SESSION Session Management PL/SQL Package
  The `SA_SESSION` PL/SQL package manages session behavior for user authorizations.
- SA_SYSDBA Policy Management PL/SQL Package
  The `SA_SYSDBA` PL/SQL package manages Oracle Label Security policies.
- SA_USER_ADMIN PL/SQL Package
  The `SA_USER_ADMIN` PL/SQL package manages user labels by label component.
- SA_UTL PL/SQL Utility Functions and Procedures
  The `SA_UTL` PL/SQL package contains utility functions and procedures that are used in PL/SQL programs.

**See Also:**

[Using Dominance Functions](advanced-topics-in-oracle-label-security.md) for additional standalone Oracle Label Security functions

**Parent topic:** [Appendixes](part4.md)

### E.1 SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

For a non-unified auditing environment, the `SA_AUDIT_ADMIN` PL/SQL package configures auditing that is specific to Oracle Label Security.

- About the SA_AUDIT_ADMIN PL/SQL Package
  The `SA_AUDIT_ADMIN` PL/SQL package configures auditing for labels and policies, as well as creating an auditing-related view.
- SA_AUDIT_ADMIN.AUDIT
  The `SA_AUDIT_ADMIN.AUDIT` procedure enables policy-specific auditing.
- SA_AUDIT_ADMIN.AUDIT_LABEL
  The `SA_AUDIT_ADMIN.AUDIT_LABEL` procedure records policy labels during auditing.
- SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED
  The `SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED` function shows whether labels are being recorded in audit records for the policy.
- SA_AUDIT_ADMIN.CREATE_VIEW
  The `SA_AUDIT_ADMIN.CREATE_VIEW` procedure creates an audit trail view named `DBA_``policyname``_AUDIT_TRAIL`.
- SA_AUDIT_ADMIN.DROP_VIEW
  The `SA_AUDIT_ADMIN.DROP_VIEW` procedure drops the audit trail view for the specified policy.
- SA_AUDIT_ADMIN.NOAUDIT
  The `SA_AUDIT_ADMIN.NOAUDIT` procedure disables Oracle Label Security policy-specific auditing.
- SA_AUDIT_ADMIN.NOAUDIT_LABEL
  The `SA_AUDIT_ADMIN.NOAUDIT_LABEL` procedure disables the auditing of policy labels.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.1.1 About the SA_AUDIT_ADMIN PL/SQL Package

The `SA_AUDIT_ADMIN` PL/SQL package configures auditing for labels and policies, as well as creating an auditing-related view.

If you are using unified auditing, then see [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md) for information about creating unified audit policies for Oracle Label Security. In a unified auditing environment, no new audit records will be generated as a result of setting the procedures that are described in this section.

After you have enabled systemwide auditing, you can use `SA_AUDIT_ADMIN` PL/SQL package procedures to enable or disable Oracle Label Security auditing. To use this package, you must be granted the `policy``_DBA` role (for example, `HR_OLS_POL_DBA` for a role for the `hr_ols_pol` policy) and the `EXECUTE` privilege for the `SA_AUDIT_ADMIN` package.

**See Also:**

[Duties of Oracle Label Security Administrators](introduction-to-oracle-label-security.md) for information about the `policy_``DBA` role

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.2 SA_AUDIT_ADMIN.AUDIT

The `SA_AUDIT_ADMIN.AUDIT` procedure enables policy-specific auditing.

Auditing of each policy is independent of the others. The audit records capture Oracle Label Security administrative actions and the use of Oracle Label Security privileges that were used during logons, DML executions, and trusted stored procedure invocations.

##### Syntax

    SA_AUDIT_ADMIN.AUDIT (
         policy_name     IN VARCHAR2,
         users           IN VARCHAR2 DEFAULT NULL,
         audit_option    IN VARCHAR2 DEFAULT NULL,
         audit_type      IN VARCHAR2 DEFAULT NULL,
         success         IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-1 SA_AUDIT_ADMIN.AUDIT Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`  | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `users`        | Optional. A comma-delimited list of user names to audit, as follows:<br>• If you are auditing OLS administrative actions, then ensure that the users you enter have the `policy_``DBA` role and the `EXECUTE` privilege for the Oracle Label Security packages.<br>• If you are auditing the use of OLS privileges, then these users do not need to be OLS administrators.<br>• If you do not specify any users, then all users are audited.<br>To find users who have privileges to modify Oracle Label Security policies, query the `USER_NAME` column of the `DBA_SA_USERS` view.                                                                                                                       |
| `audit_option` | Optional. A comma-delimited list of options to be audited. Options are as follows:<br>• `APPLY`: Audits application of specified Oracle Label Security policies to tables and schemas<br>• `REMOVE`: Audits removal of specified Oracle Label Security policies from tables and schemas<br>• `SET`: Audits the setting of user authorizations, and user and program privileges<br>• `PRIVILEGES`: Audits use of all policy-specific privileges<br>If not specified, then all default options (that is, options not including privileges) are audited. Audit options for privileged operations should be set explicitly by specifying the `PRIVILEGES` option, which sets audit options for all privileges. |
| `audit_type`   | Optional. `BY` `ACCESS` or `BY` `SESSION`. If not specified, then audit records are written `BY SESSION`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `success`      | Optional. `SUCCESSFUL` if the action was successful, or `NOT` `SUCCESSFUL`. If not specified, then audit is written for both.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

##### Examples

The following example audits any failed `APPLY` and `REMOVE` attempts by the users `psmith` and `rlayton`.

    BEGIN
     SA_AUDIT_ADMIN.AUDIT(
      policy_name      => 'hr_ols_pol',
      users            => 'jjones, rlayton',
      audit_option     => 'apply, remove',
      audit_type       => 'by access',
      success          => 'not successful');
    END;
    /

If the you do not specify any audit options, then all options except the privilege-related ones are audited. You must specify the auditing of privileges explicitly. For example, if you enter the following statement, then the default options are set for the `hr_ols_pol` policy:

    EXEC SA_AUDIT_ADMIN.AUDIT ('hr_ols_pol');

When you enable auditing, it will be performed on all users by session, whether their actions are successful or not.

When you set auditing parameters and options, the new values apply only to subsequent sessions, not to the current session.

Consider also a case in which one `SA_AUDIT_ADMIN.AUDIT` call (with no users specified) enables auditing for `APPLY` operations for all users, and then a second call enables auditing of `REMOVE` operations for a specific user. For example:

    EXEC SA_AUDIT_ADMIN.AUDIT ('hr_ols_pol', null, 'apply');
    EXEC SA_AUDIT_ADMIN.AUDIT ('hr_ols_pol', 'scott', 'remove');

In this case, `SCOTT` is audited for both `APPLY` and `REMOVE` operations.

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.3 SA_AUDIT_ADMIN.AUDIT_LABEL

The `SA_AUDIT_ADMIN.AUDIT_LABEL` procedure records policy labels during auditing.

This procedure stores the user's session label in the audit table.

##### Syntax

    SA_AUDIT_ADMIN.AUDIT_LABEL (
         policy_name     IN VARCHAR2);

##### Parameter

Table E-2 SA_AUDIT_ADMIN.AUDIT_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example writes output indicating whether the Oracle Label Security labels are being audited for the `hr_ols_pol` policy.

    BEGIN
     SA_AUDIT_ADMIN.AUDIT_LABEL(
      policy_name      => 'hr_ols_pol');
    END;
    /

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.4 SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED

The `SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED` function shows whether labels are being recorded in audit records for the policy.

##### Syntax

    SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED (
      policy_name IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameters

Table E-3 SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example writes output indicating whether the Oracle Label Security labels are being audited for the `hr_ols_pol` policy.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_AUDIT_ADMIN.AUDIT_LABEL_ENABLED('hr_ols_pol')
      THEN DBMS_OUTPUT.PUT_LINE('OLS hr_ols_pol labels are being audited.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('OLS hr_ols_pol labels not being audited.');
     END IF;
    END;
    /

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.5 SA_AUDIT_ADMIN.CREATE_VIEW

The `SA_AUDIT_ADMIN.CREATE_VIEW` procedure creates an audit trail view named `DBA_``policyname``_AUDIT_TRAIL`.

This view contains the specified policy's label column as well as all the entries in the audit trail written on behalf of this policy. If the view name exceeds the database limit of 30 characters, then the user can optionally specify a shorter view name.

Oracle Label Security grants the `SELECT` privilege on the `DBA_``policyname``_AUDIT_TRAIL` view to the Oracle Label Security policy database administrator.

**See Also:**

[Oracle Label Security User-Created Auditing View](oracle-label-security-reference.md) to find the columns that are contained in the `DBA_``policyname``_AUDIT_TRAIL` view

##### Syntax

    SA_AUDIT_ADMIN.CREATE_VIEW (
         policy_name     IN VARCHAR2,
         view_name       IN VARCHAR2    DEFAULT NULL);

##### Parameters

Table E-4 SA_AUDIT_ADMIN.CREATE_VIEW Parameters

| Parameter     | Description                                                                                                                          |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.       |
| `view_name`   | Optional. Specifies the name of the view name. If you omit this setting, then the name defaults to `DBA_``policyname``_AUDIT_TRAIL`. |

##### Examples

The following example creates a view called `hr_ols_pol_view` for the `hr_ols_pol` policy.

    BEGIN
     SA_AUDIT_ADMIN.CREATE_VIEW(
      policy_name      => 'hr_ols_pol',
      view_name        => 'hr_ols_pol_view');
    END;
    /

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.6 SA_AUDIT_ADMIN.DROP_VIEW

The `SA_AUDIT_ADMIN.DROP_VIEW` procedure drops the audit trail view for the specified policy.

##### Syntax

    SA_AUDIT_ADMIN.DROP_VIEW (
         policy_name     IN VARCHAR2,
         view_name       IN VARCHAR2    DEFAULT NULL);

##### Parameters

Table E-5 SA_AUDIT_ADMIN.DROP_VIEW Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                               |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                            |
| `view_name`   | Specifies an existing view's name. You can find this view by first querying the `ALL_SA_POLICIES` data dictionary view to find the name of the policy on which the view was based, and then querying `ALL_VIEWS` data dictionary view to find any views that have the name of the policy. |

##### Example

The following example drops the view called `hr_ols_pol_view` from the `hr_ols_pol` policy.

    BEGIN
     SA_AUDIT_ADMIN.DROP_VIEW(
      policy_name      => 'hr_ols_pol',
      view_name        => 'hr_ols_pol_view');
    END;
    /

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.7 SA_AUDIT_ADMIN.NOAUDIT

The `SA_AUDIT_ADMIN.NOAUDIT` procedure disables Oracle Label Security policy-specific auditing.

##### Syntax

    SA_AUDIT_ADMIN.NOAUDIT (
         policy_name     IN VARCHAR2,
         users           IN VARCHAR2 DEFAULT NULL,
         audit_option    IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-6 SA_AUDIT_ADMIN.NO_AUDIT Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`  | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `users`        | Optional. A comma-delimited list of users who were audited. If not specified, then auditing is disabled for all users.<br>To find users who have privileges to modify Oracle Label Security policies, query the `USER_NAME` column of the `ALL_SA_AUDIT_OPTIONS` view.                                                                                                                                                                                                                                                                                                                                                  |
| `audit_option` | Optional. A comma-delimited list of options to be disabled. Options are as follows:<br>• `APPLY`: Disables auditing of the application of specified Oracle Label Security policies to tables and schemas<br>• `REMOVE`: Disables auditing of the removal of specified Oracle Label Security policies from tables and schemas<br>• `SET`: Disables auditing of the setting of user authorizations, and user and program privileges<br>• `PRIVILEGES`: Disables auditing of the use of all policy-specific privileges<br>If not specified, then all default options are disabled. Privileges must be disabled explicitly. |

##### Examples

The following example disables auditing for failed `APPLY` and `REMOVE` attempts by the users `psmith` and `rlayton`.

    BEGIN
     SA_AUDIT_ADMIN.NOAUDIT(
      policy_name      => 'hr_ols_pol',
      users            => 'jjones',
      audit_option     => 'apply, remove');
    END;
    /

You can disable auditing for all enabled options, or only for a subset of enabled options. All auditing for the specified options is disabled for all specified users (or all users, if the users parameter is `NULL`). For example, the following statement disables auditing of the `APPLY` and `REMOVE` operations for users John, Mary, and Scott:

    EXEC SA_AUDIT_ADMIN.NOAUDIT ('HR', 'JOHN, MARY, SCOTT', 'APPLY, REMOVE');

Consider also a case in which one `AUDIT` call enables auditing for a specific user, and a second call (with no user specified) enables auditing for all users. For example:

    EXEC SA_AUDIT_ADMIN.AUDIT ('HR', 'SCOTT');
    EXEC SA_AUDIT_ADMIN.AUDIT ('HR');

In this case, a subsequent call to `NOAUDIT` with no users specified (such as the following statement) does not reverse the auditing that was set for `SCOTT` explicitly in the first call. So, auditing continues to be performed on `SCOTT`.

    EXEC SA_AUDIT_ADMIN.NOAUDIT ('HR');

In this way, even if `SA_AUDIT_ADMIN.NOAUDIT` is set for all users, Oracle Label Security still audits any users for whom auditing was explicitly set.

Auditing of privileged operations must be specified explicitly. If you run `SA_AUDIT_ADMIN.NOAUDIT` with no options, the Oracle Label Security will nonetheless continue to audit privileged operations. For example, if auditing is enabled and you enter

    EXEC SA_AUDIT_ADMIN.NOAUDIT ('HR');

then auditing will continue to be performed on the privileged operations (such as `WRITEDOWN`).

`SA_AUDIT_ADMIN.NOAUDIT` parameters and options that you set apply only to subsequent sessions, not to current sessions.

If you try to enable an audit option that has already been set, or if you try to disable an audit option that has not been set, then Oracle Label Security processes the statement without indicating an error.An attempt to specify an invalid option results in an error message. You can find the status of audit options by querying the `ALL_SA_AUDIT_OPTIONS` data dictionary view.

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

#### E.1.8 SA_AUDIT_ADMIN.NOAUDIT_LABEL

The `SA_AUDIT_ADMIN.NOAUDIT_LABEL` procedure disables the auditing of policy labels.

##### Syntax

    SA_AUDIT_ADMIN.NOAUDIT_LABEL (
       policy_name     IN VARCHAR2);

##### Parameters

Table E-7 SA_AUDIT_ADMIN.NO_AUDIT_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example disables auditing for the `hr_ols_pol` policy.

    BEGIN
     SA_AUDIT_ADMIN.NOAUDIT_LABEL(
      policy_name      => 'hr_ols_pol');
    END;
    /

**Parent topic:** SA_AUDIT_ADMIN Oracle Label Security Auditing PL/SQL Package

### E.2 SA_COMPONENTS Label Components PL/SQL Package

The `SA_COMPONENTS` PL/SQL package manages the component definitions of an Oracle Label Security label.

- About the SA_COMPONENTS PL/SQL Package
  The `SA_COMPONENTS` PL/SQL package configures compartments, groups, parent groups, and levels.
- SA_COMPONENTS.ALTER_COMPARTMENT
  The `SA_COMPONENTS.ALTER_COMPARTMENT` procedure changes the short name and long name associated with a compartment.
- SA_COMPONENTS.ALTER_GROUP
  The `SA_COMPONENTS.ALTER_GROUP` procedure changes the short name and long name associated with a group.
- SA_COMPONENTS.ALTER_GROUP_PARENT
  The `SA_COMPONENTS.ALTER_GROUP_PARENT` procedure changes the parent group associated with a particular group.
- SA_COMPONENTS.ALTER_LEVEL
  The `SA_COMPONENTS.ALTER_LEVEL` procedure changes the short name and long name associated with a level.
- SA_COMPONENTS.CREATE_COMPARTMENT
  The `SA_COMPONENTS.CREATE_COMPARTMENT` procedure creates a compartment and specify its short name and long name.
- SA_COMPONENTS.CREATE_GROUP
  The `SA_COMPONENTS.CREATE_GROUP` procedure creates a group and specify its short name and long name, and optionally a parent group.
- SA_COMPONENTS.CREATE_LEVEL
  The `SA_COMPONENTS.CREATE_LEVEL` procedure creates a level and specify its short name and long name.
- SA_COMPONENTS.DROP_COMPARTMENT
  The `SA_COMPONENTS.DROP_COMPARTMENT` procedure removes a compartment.
- SA_COMPONENTS.DROP_GROUP
  The `SA_COMPONENTS.DROP_GROUP` procedure removes a group.
- SA_COMPONENTS.DROP_LEVEL
  The `SA_COMPONENTS.DROP_LEVEL` procedure removes a level.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.2.1 About the SA_COMPONENTS PL/SQL Package

The `SA_COMPONENTS` PL/SQL package configures compartments, groups, parent groups, and levels.

To use this package, you must be granted the `policy_``DBA` role (for example, `HR_OLS_POL_DBA` for a role for the `hr_ols_pol` policy) and the `EXECUTE` privilege on the `SA_COMPONENTS` package.

**Related Topics**

- [Understanding Data Labels and User Labels](understanding-data-labels-and-user-labels.md)

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.2 SA_COMPONENTS.ALTER_COMPARTMENT

The `SA_COMPONENTS.ALTER_COMPARTMENT` procedure changes the short name and long name associated with a compartment.

Once set, the `comp_num` parameter cannot be changed. If the `comp_num` parameter is used in any existing label, then its short name cannot be changed but its long name can be changed.

##### Syntax

    SA_COMPONENTS.ALTER_COMPARTMENT (
       policy_name       IN VARCHAR2,
       comp_num          IN NUMBER(38),
       new_short_name    IN VARCHAR2,
       new_long_name     IN VARCHAR2);

    SA_COMPONENTS.ALTER_COMPARTMENT (
       policy_name       IN VARCHAR2,
       short_name        IN VARCHAR2 DEFAULT NULL,
       new_long_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-8 SA_COMPONENTS.ALTER_COMPARTMENT Parameters

| Parameter        | Description                                                                                                                                                                        |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                     |
| `comp_num`       | Specifies the number of the compartment to be altered. To find a list of existing compartment numbers, query the `COMP_NUM` column of the `ALL_SA_COMPARTMENTS` view.              |
| `short_name`     | Specifies the short name of the compartment to be altered (up to 30 characters). To find the current compartment, query the `SHORT_NAME` column of the `ALL_SA_COMPARTMENTS` view. |
| `new_short_name` | Specifies the new short name of the compartment (up to 30 characters)                                                                                                              |
| `new_long_name`  | Specifies the new long name of the compartment (up to 80 characters).                                                                                                              |

##### Example

The following example modifies the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.ALTER_COMPARTMENT (
       policy_name         => 'hr_ols_pol',
       comp_num            => '48',
       new_short_name      => 'FIN',
       new_long_name       => 'FINANCE');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.3 SA_COMPONENTS.ALTER_GROUP

The `SA_COMPONENTS.ALTER_GROUP` procedure changes the short name and long name associated with a group.

Once set, the `group_num` parameter cannot be changed. If the group is used in any existing label, then its short name cannot be changed, but its long name can be changed.

##### Syntax

    SA_COMPONENTS.ALTER_GROUP (
       policy_name    IN VARCHAR2,
       group_num      IN NUMBER(38),
       new_short_name IN VARCHAR2 DEFAULT NULL,
       new_long_name  IN VARCHAR2 DEFAULT NULL);

    SA_COMPONENTS.ALTER_GROUP (
       policy_name    IN VARCHAR2,
       short_name     IN VARCHAR2,
       new_long_name  IN VARCHAR2);

##### Parameters

Table E-9 SA_COMPONENTS.ALTER_GROUP Parameters

| Parameter        | Description                                                                                                                                     |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                  |
| `group_num`      | Specifies the existing group number to be altered. To find existing group numbers, query the `GROUP_NUM` column of the `ALL_SA_GROUPS` view.    |
| `short_name`     | Specifies the existing group short name to be altered. To find existing short names, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view. |
| `new_short_name` | Specifies the new short name for the group (up to 30 characters)                                                                                |
| `new_long_name`  | Specifies the new long name for the group (up to 80 characters)                                                                                 |

##### Example

The following example modifies the `long_name` setting for the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.ALTER_GROUP (
       policy_name     => 'hr_ols_pol',
       short_name      => 'ER_FIN',
       new_long_name   => 'ER_FINANCES');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.4 SA_COMPONENTS.ALTER_GROUP_PARENT

The `SA_COMPONENTS.ALTER_GROUP_PARENT` procedure changes the parent group associated with a particular group.

##### Syntax

    SA_COMPONENTS.ALTER_GROUP_PARENT (
       policy_name     IN VARCHAR2,
       group_num       IN NUMBER(38),
       new_parent_num  IN NUMBER(38));

    SA_COMPONENTS.ALTER_GROUP_PARENT (
       policy_name     IN VARCHAR2,
       group_num       IN NUMBER(38),
       new_parent_name IN VARCHAR2);

    SA_COMPONENTS.ALTER_GROUP_PARENT (
       policy_name     IN VARCHAR2,
       short_name      IN VARCHAR2,
       new_parent_name IN VARCHAR2);

##### Parameters

Table E-10 SA_COMPONENTS.ALTER_GROUP_PARENT Parameters

| Parameter         | Description                                                                                                                                               |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                            |
| `group_num`       | Specifies the existing group number to be altered. To find existing group numbers, query the `GROUP_NUM` column of the `ALL_SA_GROUPS` view.              |
| `short_name`      | Specifies the existing group short name to be altered. To find existing short names, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.           |
| `new_parent_num`  | Specifies the number of an existing group as the parent group. To find existing parent groups, query the `PARENT_NUM` column of the `ALL_SA_GROUPS` view. |
| `new_parent_name` | Specifies the short name of an existing group as the parent group. To find existing groups, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.    |

##### Example

The following example modifies the parent name for the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.ALTER_GROUP_PARENT (
       policy_name         => 'hr_ols_pol',
       group_num           => 2100,
       new_parent_name     => 'ER');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.5 SA_COMPONENTS.ALTER_LEVEL

The `SA_COMPONENTS.ALTER_LEVEL` procedure changes the short name and long name associated with a level.

Once they are defined, level numbers cannot be changed. If a level is used in any existing label, then its short name cannot be changed, but its long name can be changed.

##### Syntax

    SA_COMPONENTS.ALTER_LEVEL (
       policy_name     IN VARCHAR2,
       level_num       IN NUMBER(38),
       new_short_name  IN VARCHAR2 DEFAULT NULL,
       new_long_name   IN VARCHAR2 DEFAULT NULL);

    SA_COMPONENTS.ALTER_LEVEL (
       policy_name     IN VARCHAR2,
       short_name      IN VARCHAR2,
       new_long_name   IN VARCHAR2);

##### Parameters

Table E-11 SA_COMPONENTS.ALTER_LEVEL Parameters

| Parameter        | Description                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Specifies the policy, which much exist. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `level_num`      | Specifies the number of the level to be altered. To find existing levels, query the `LEVEL_NUM` column of the `ALL_SA_LEVELS` view.              |
| `short_name`     | Specifies the existing short name of the level. To find existing level short names, query the `SHORT_NAME` column of the `ALL_SA_LEVELS` view.   |
| `new_short_name` | Specifies the new short name for the level (up to 30 characters)                                                                                 |
| `new_long_name`  | Specifies the new long name for the level (up to 80 characters)                                                                                  |

##### Example

The following example modifies the short and long names for the `hr_ols_pol` policy level.

    BEGIN
     SA_COMPONENTS.ALTER_LEVEL (
       policy_name     => 'hr_ols_pol',
       level_num       => 40,
       new_short_name  => 'TS',
       new_long_name   => 'TOP_SECRET');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.6 SA_COMPONENTS.CREATE_COMPARTMENT

The `SA_COMPONENTS.CREATE_COMPARTMENT` procedure creates a compartment and specify its short name and long name.

The `comp_num` parameter determines the order in which compartments are listed in the character string representation of labels.

##### Syntax

    SA_COMPONENTS.CREATE_COMPARTMENT (
       policy_name IN VARCHAR2,
       comp_num    IN NUMBER(38),
       short_name  IN VARCHAR2,
       long_name   IN VARCHAR2);

##### Parameters

Table E-12 SA_COMPONENTS.CREATE_COMPARTMENT Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `comp_num`    | Specifies the compartment number (0-9999)                                                                                      |
| `short_name`  | Specifies the short name for the compartment (up to 30 characters)                                                             |
| `long_name`   | Specifies the long name for the compartment (up to 80 characters)                                                              |

##### Example

The following example creates a compartment for the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.CREATE_COMPARTMENT (
       policy_name     => 'hr_ols_pol',
       comp_num        => '48',
       short_name      => 'FIN',
       long_name       => 'FINANCE');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.7 SA_COMPONENTS.CREATE_GROUP

The `SA_COMPONENTS.CREATE_GROUP` procedure creates a group and specify its short name and long name, and optionally a parent group.

##### Syntax

    SA_COMPONENTS.CREATE_GROUP (
       policy_name IN VARCHAR2,
       group_num   IN NUMBER(38),
       short_name  IN VARCHAR2,
       long_name   IN VARCHAR2,
       parent_name IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-13 SA_COMPONENTS.CREATE_GROUP Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `group_num`   | Specifies the group number (0-9999)                                                                                            |
| `short_name`  | Specifies the short name for the group (up to 30 characters)                                                                   |
| `long_name`   | Specifies the long name for the group (up to 80 characters)                                                                    |
| `parent_name` | Specifies the short name of an existing group as the parent group. If `NULL`, then the group is a top-level group.             |

Note that the group number affects the order in which groups will be displayed when labels are selected.

##### Examples

In the following examples, the first creates a parent group, `ER`, and the second creates a second group that is part of the parent group.

    BEGIN
      SA_COMPONENTS.CREATE_GROUP (
       policy_name     => 'hr_ols_pol',
       group_num       => 2000,
       short_name      => 'ER',
       long_name       => 'EAST_REGION');
    END;
    /

    BEGIN
      SA_COMPONENTS.CREATE_GROUP (
       policy_name     => 'hr_ols_pol',
       group_num       => 2100,
       short_name      => 'ER_FIN',
       long_name       => 'ER_FINANCES',
       parent_name     => 'ER');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.8 SA_COMPONENTS.CREATE_LEVEL

The `SA_COMPONENTS.CREATE_LEVEL` procedure creates a level and specify its short name and long name.

The numeric values assigned to the `level_num` parameter determine the sensitivity ranking (that is, a lower number indicates less sensitive data).

##### Syntax

    SA_COMPONENTS.CREATE_LEVEL (
       policy_name       IN VARCHAR2,
       level_num         IN NUMBER(38),
       short_name        IN VARCHAR2,
       long_name         IN VARCHAR2);

##### Parameters

Table E-14 SA_COMPONENTS.CREATE_LEVEL Parameters

| Parameter     | Description                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy, which must exist. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `level_num`   | Specifies the level number (0-9999)                                                                                                              |
| `short_name`  | Specifies the short name for the level (up to 30 characters)                                                                                     |
| `long_name`   | Specifies the long name for the level (up to 80 characters)                                                                                      |

##### Example

The following example creates a level for the `hr_ols_pol` policy.

    BEGIN
     SA_COMPONENTS.CREATE_LEVEL (
       policy_name   => 'hr_ols_pol',
       level_num     => 40,
       short_name    => 'HS',
       long_name     => 'HIGHLY_SENSITIVE');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.9 SA_COMPONENTS.DROP_COMPARTMENT

The `SA_COMPONENTS.DROP_COMPARTMENT` procedure removes a compartment.

If the compartment is used in any existing label, then it cannot be dropped. You can find all existing labels by querying the `LABEL` column of the `ALL_SA_DATA_LABELS` data dictionary view.

##### Syntax

    SA_COMPONENTS.DROP_COMPARTMENT (
       policy_name IN VARCHAR2,
       comp_num    IN INTEGER);

    SA_COMPONENTS.DROP_COMPARTMENT (
       policy_name IN VARCHAR2,
       short_name  IN VARCHAR2);

##### Parameters

Table E-15 SA_COMPONENTS.DROP_COMPARTMENT Parameters

| Parameter     | Description                                                                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                 |
| `comp_num`    | Specifies the number of an existing compartment for the policy. To find existing compartment numbers, query the `COMP_NUM` column of the `DBA_SA_COMPARTMENTS` view.           |
| `short_name`  | Specifies the short name of an existing compartment for the policy. To find existing compartment short names, query the `SHORT_NAME` column of the `DBA_SA_COMPARTMENTS` view. |

##### Example

The following example removes the `FIN` compartment from the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.DROP_COMPARTMENT (
       policy_name     => 'hr_ols_pol',
       short_name      => 'FIN');
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.10 SA_COMPONENTS.DROP_GROUP

The `SA_COMPONENTS.DROP_GROUP` procedure removes a group.

If the group is used in an existing label, then it cannot be dropped.

##### Syntax

    SA_COMPONENTS.DROP_GROUP (
       policy_name IN VARCHAR2,
       group_num   IN NUMBER(38));

    SA_COMPONENTS.DROP_GROUP (
       policy_name IN VARCHAR2,
       short_name  IN VARCHAR2);

##### Parameters

Table E-16 SA_COMPONENTS.DROP_GROUP Parameters

| Parameter     | Description                                                                                                                                         |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                      |
| `group_num`   | Specifies the number of an existing group for the policy. To find existing group numbers, query the `GROUP_NUM` column of the `ALL_SA_GROUPS` view. |
| `short_name`  | Specifies the short name of an existing group. To find existing group short names, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.       |

##### Example

The following example removes a group based on the group number for the `hr_ols_pol` policy.

    BEGIN
      SA_COMPONENTS.DROP_GROUP (
       policy_name     => 'hr_ols_pol',
       group_num       => 2000);
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

#### E.2.11 SA_COMPONENTS.DROP_LEVEL

The `SA_COMPONENTS.DROP_LEVEL` procedure removes a level.

If the level is used in any existing label, then it cannot be dropped.

##### Syntax

    SA_COMPONENTS.DROP_LEVEL (
       policy_name IN VARCHAR2,
       level_num   IN NUMBER(38));

    SA_COMPONENTS.DROP_LEVEL (
       policy_name IN VARCHAR2,
       short_name  IN VARCHAR2);

##### Parameters

Table E-17 SA_COMPONENTS.DROP_LEVEL Parameters

| Parameter     | Description                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy, which much exist. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.             |
| `level_num`   | Specifies the number of an existing level for the policy. To find existing level numbers, query the `LEVEL_NUM` column of the `ALL_SA_LEVELS` view.          |
| `short_name`  | Specifies the short name for the level (up to 30 characters). To find existing level short names, query the `SHORT_NAME` column of the `ALL_SA_LEVELS` view. |

##### Example

The following example drops the level `40` from the `hr_ols_pol` policy.

    BEGIN
     SA_COMPONENTS.DROP_LEVEL (
       policy_name     => 'hr_ols_pol',
       level_num       => 40);
    END;
    /

**Parent topic:** SA_COMPONENTS Label Components PL/SQL Package

### E.3 SA_LABEL_ADMIN Label Management PL/SQL Package

The `SA_LABEL_ADMIN` PL/SQL package provides an administrative interface to manage the labels used by a policy.

- About the SA_LABEL_ADMIN PL/SQL Package
  The `SA_LABEL_ADMIN` PL/SQL package creates, alters, and deletes labels.
- SA_LABEL_ADMIN.ALTER_LABEL
  The `SA_LABEL_ADMIN.ALTER_LABEL` procedure changes the character string label definition associated with a label tag.
- SA_LABEL_ADMIN.CREATE_LABEL
  The `SA_LABEL_ADMIN.CREATE_LABEL` procedure creates data labels.
- SA_LABEL_ADMIN.DROP_LABEL
  The `SA_LABEL_ADMIN.DROP_LABEL` procedure deletes a specified policy label.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.3.1 About the SA_LABEL_ADMIN PL/SQL Package

The `SA_LABEL_ADMIN` PL/SQL package creates, alters, and deletes labels.

**Parent topic:** SA_LABEL_ADMIN Label Management PL/SQL Package

#### E.3.2 SA_LABEL_ADMIN.ALTER_LABEL

The `SA_LABEL_ADMIN.ALTER_LABEL` procedure changes the character string label definition associated with a label tag.

The label tag itself cannot be changed.

If you change the character string associated with a label tag, then the sensitivity of the data in the rows changes accordingly. For example, if the label character string `TS:A` with an associated label tag value of `4001` is changed to the label `TS:B`, then access to the data changes accordingly. This is true even when the label tag value (`4001`) has not changed. In this way, you can change the data's sensitivity without the need to update all the rows.

Ensure that when you specify a label to alter, you can refer to it either by its label tag or by its character string value.

##### Syntax

    SA_LABEL_ADMIN.ALTER_LABEL (
       policy_name       IN VARCHAR2,
       label_tag         IN BINARY_INTEGER,
       new_label_value   IN VARCHAR2 DEFAULT NULL,
       new_data_label    IN BOOLEAN  DEFAULT NULL);

    SA_LABEL_ADMIN.ALTER_LABEL (
       policy_name       IN VARCHAR2,
       label_value       IN VARCHAR2,
       new_label_value   IN VARCHAR2 DEFAULT NULL,
       new_data_label    IN BOOLEAN  DEFAULT NULL);

##### Parameters

Table E-18 SA_LABEL_ADMIN.ALTER_LABEL Parameters

| Parameter         | Description                                                                                                                                                                  |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the name of an existing policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                           |
| `label_tag`       | Identifies the integer tag assigned to the label to be altered. To find existing label tags, query the `LABEL_TAG` column of the `ALL_SA_LABELS` view.                       |
| `label_value`     | Identifies the existing character string representation of the label to be altered. To find the existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view. |
| `new_label_value` | Specifies the new character string representation of the label value. If `NULL`, the existing value is not changed.                                                          |
| `new_data_label`  | `TRUE` if the label can be used to label row data. If `NULL`, the existing value is not changed.                                                                             |

##### Example

The following example modifies the `label_tag` and `label_value` settings of `hr_ols_pol` policy.

    BEGIN
      SA_LABEL_ADMIN.ALTER_LABEL (
       policy_name       => 'hr_ols_pol',
       label_tag         => 1111,
       new_label_value   => 'HS',
       new_data_label    => TRUE);
    END;
    /

**Parent topic:** SA_LABEL_ADMIN Label Management PL/SQL Package

#### E.3.3 SA_LABEL_ADMIN.CREATE_LABEL

The `SA_LABEL_ADMIN.CREATE_LABEL` procedure creates data labels.

##### Syntax

    SA_LABEL_ADMIN.CREATE_LABEL (
       policy_name IN VARCHAR2,
       label_tag   IN BINARY_INTEGER,
       label_value IN VARCHAR2,
       data_label  IN BOOLEAN DEFAULT TRUE);

##### Parameters

Table E-19 SA_LABEL_ADMIN.CREATE_LABEL Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the name of an existing policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                         |
| `label_tag`   | Specifies a unique integer value representing the sort order of the label, relative to other policy labels (0-99999999). This value must be 1 to 8 digits long.                                                                                                            |
| `label_value` | Specifies the character string representation of the label to be created. Use the short name of the level, compartment, and group. You can find these values by querying the `SHORT_NAME` column of the `ALL_SA_LEVELS`, `ALL_SA_COMPARTMENTS`, and `ALL_SA_GROUPS` views. |
| `data_label`  | `TRUE` if the label can be used to label row data. Use this to define the label as valid for data.                                                                                                                                                                         |

When you identify valid labels, you specify which of all the possible combinations of levels, compartments, and groups can potentially be used to label data in tables.

##### Example

The following example creates a label for the `hr_ols_pol` policy.

    BEGIN
      SA_LABEL_ADMIN.CREATE_LABEL (
       policy_name     => 'hr_ols_pol',
       label_tag       => 1111,
       label_value     => 'HS:FIN',
       data_label      => TRUE);
    END;
    /

**Note:**

If you create a new label by using the `TO_DATA_LABEL` procedure, then a system-generated label tag of 10 digits is generated automatically.

However, when Oracle Label Security is installed to work with Oracle Internet Directory, dynamic label generation is not permitted, because labels are managed centrally in Oracle Internet Directory, using `olsadmintool` commands.

So, when Oracle Label Security is directory-enabled, the `TO_DATA_LABEL` function is not available and will generate an error message if used.

**Parent topic:** SA_LABEL_ADMIN Label Management PL/SQL Package

#### E.3.4 SA_LABEL_ADMIN.DROP_LABEL

The `SA_LABEL_ADMIN.DROP_LABEL` procedure deletes a specified policy label.

Any subsequent reference to the label (in data rows, or in user or program unit labels) will raise an invalid label error.

Use this procedure only while setting up labels, prior to data population. If you should inadvertently drop a label that is being used, you can recover it by disabling the policy, fixing the problem, and then re-enabling the policy.

##### Syntax

    SA_LABEL_ADMIN.DROP_LABEL (
       policy_name       IN VARCHAR2,
       label_tag         IN BINARY_INTEGER);

    SA_LABEL_ADMIN.DROP_LABEL (
       policy_name       IN VARCHAR2,
       label_value       IN VARCHAR2);

##### Parameters

Table E-20 SA_LABEL_ADMIN.DROP_LABEL Parameters

| Parameter     | Description                                                                                                                                           |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the name of an existing policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.    |
| `label_tag`   | Specifies the integer tag assigned to the label to be dropped. To find existing label tags, query the `LABEL_TAG` column of the `ALL_SA_LABELS` view. |
| `label_value` | Specifies the string value of the label to be dropped. To find existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view.           |

**WARNING:**

Do not drop a label that is in use anywhere in the database. You can find labels by querying the `ALL_SA_LABELS` data dictionary view.

##### Example

The following example drops the `hr_ols_pol` policy label based on its `label_tag` setting.

    BEGIN
      SA_LABEL_ADMIN.DROP_LABEL (
       policy_name     => 'hr_ols_pol',
       label_tag       => 1111);
    END;
    /

**Parent topic:** SA_LABEL_ADMIN Label Management PL/SQL Package

### E.4 SA_POLICY_ADMIN Policy Administration PL/SQL Package

The `SA_POLICY_ADMIN` PL/SQL package manages Oracle Label Security policies as a whole.

- About the SA_POLICY_ADMIN PL/SQL Package
  The `SA_POLICY_ADMIN` PL/SQL package configures schema and table policies, and performs subscribe and unsubscribe actions.
- SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY
  The `SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY` procedure changes the default enforcement options for the policy.
- SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY
  The `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY` procedure applies a policy to all of the tables in a schema and enables the policy for these tables.
- SA_POLICY_ADMIN.APPLY_TABLE_POLICY
  The `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` procedure adds the specified policy to a table.
- SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY
  The `SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY` procedure disables the enforcement of the policy for all tables in a schema.
- SA_POLICY_ADMIN.DISABLE_TABLE_POLICY
  The `SA_POLICY_ADMIN.DISABLE_TABLE_POLICY` procedure disables the enforcement of the policy for a table without changing the enforcement options, labeling function, or predicate values.
- SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY
  The `SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY` procedure reenables the current enforcement options, labeling function, and predicate for the tables in the specified schema.
- SA_POLICY_ADMIN.ENABLE_TABLE_POLICY
  The `SA_POLICY_ADMIN.ENABLE_TABLE_POLICY` procedure reenables the current enforcement options, labeling function, and predicate for the specified table.
- SA_POLICY_ADMIN.POLICY_SUBSCRIBE
  In an Oracle Internet Directory-enabled Oracle Label Security configuration, the `SA_POLICY_ADMIN.POLICY_SUBSCRIBE` procedure subscribes to the policy for usage in `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` and `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY`.
- SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE
  In an Oracle Internet Directory enabled Oracle Label Security configuration, the `SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE` procedure unsubscribes to the policy.
- SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY
  The `SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY` procedure removes the specified policy from a schema.
- SA_POLICY_ADMIN.REMOVE_TABLE_POLICY
  The `SA_POLICY_ADMIN.REMOVE_TABLE_POLICY` procedure removes the specified policy from a table.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.4.1 About the SA_POLICY_ADMIN PL/SQL Package

The `SA_POLICY_ADMIN` PL/SQL package configures schema and table policies, and performs subscribe and unsubscribe actions.

To use this package, you must be granted the `policy``_DBA` role (for example, `HR_OLS_POL_DBA` for a role for the `hr_ols_pol` policy) and the `EXECUTE` privilege for the `SA_POLICY_ADMIN` package.

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.2 SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY

The `SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY` procedure changes the default enforcement options for the policy.

Any new tables created in the schema will automatically have the new enforcement options applied. The existing tables in the schema are not affected.

To change enforcement options on a table (rather than a schema), you must first drop the policy from the table, make the change, and then reapply the policy.

If you alter the enforcement options on a schema, then this will take effect the next time a table is created in the schema. As a result, different tables within a schema may have different policy enforcement options in force.

##### Syntax

    SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY (
      policy_name         IN VARCHAR2,
      schema_name         IN VARCHAR2,
      default_options     IN VARCHAR2);

##### Parameters

Table E-21 SA_POLICY_ADMIN.ALTER_SCHEMA Parameters

| Parameter         | Description                                                                                                                                                                                                                              |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                           |
| `schema_name`     | The schema that contains the table. To find existing schemas associated with this policy, query the `POLICY_NAME` and `SCHEMA_NAME` columns of the `ALL_SA_TABLE_POLICIES` view.                                                         |
| `default_options` | The default options to be used for new tables in the schema. Separate each option with a comma.<br>See [Table 11-2](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the default enforcement options. |

##### Example

The following example adds the `UPDATE_CONTROL` default option to the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.ALTER_SCHEMA_POLICY(
      policy_name      => 'hr_ols_pol',
      schema_name      => 'HR',
      default_options  => 'read_control, write_control, update_control');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.3 SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY

The `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY` procedure applies a policy to all of the tables in a schema and enables the policy for these tables.

That is, it applies to those tables that do not already have the policy applied. Then, whenever a new table is created in the schema, the policy is automatically applied to that table, using the schema's default options. No changes are made to existing tables in the schema that already have the policy applied.

##### Syntax

    SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY (
      policy_name        IN VARCHAR2,
      schema_name        IN VARCHAR2,
      default_options    IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-22 SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                        |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                                     |
| `schema_name`     | The schema that contains the table to protect                                                                                                                                                                                                                                                                                                                                      |
| `default_options` | The default options to be used for tables in the schema. Separate each option with a comma. If the `default_options` parameter is `NULL`, then the policy's default options will be used to apply the policy to the tables in the schema.<br>See [Table 11-2](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the default enforcement options. |

##### Example

The following example applies the `READ_CONTROL` and `WRITE_CONTROL` options to the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY(
      policy_name      => 'hr_ols_pol',
      schema_name      => 'HR',
      default_options  => 'read_control, write_control');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.4 SA_POLICY_ADMIN.APPLY_TABLE_POLICY

The `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` procedure adds the specified policy to a table.

A policy label column is added to the table if it does not exist, and is set to `NULL`. When a policy is applied, it is automatically enabled. To change the table options, labeling function, or predicate, you must first remove the policy, and then reapply it.

##### Syntax

    SA_POLICY_ADMIN.APPLY_TABLE_POLICY (
      policy_name       IN VARCHAR2,
      schema_name       IN VARCHAR2,
      table_name        IN VARCHAR2,
      table_options     IN VARCHAR2 DEFAULT NULL,
      label_function    IN VARCHAR2 DEFAULT NULL,
      predicate         IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-23 SA_POLICY_ADMIN.APPLY_TABLE_POLICY Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                    |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`    | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                 |
| `schema_name`    | The schema that contains the table that the policy protects                                                                                                                                                                                                                    |
| `table_name`     | The table to be protected by the policy                                                                                                                                                                                                                                        |
| `table_options`  | A comma-delimited list of policy enforcement options to be used for the table. If `NULL`, then the policy's default options are used.<br>See [Table 11-2](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the default enforcement options. |
| `label_function` | A string calling a function to return a label value to use as the default. For example, `my_label(:new.dept,:new.status)` computes the label based on the new values of the `DEPT` and `STATUS` columns in the row.                                                            |
| `predicate`      | An additional predicate to combine (using `AND` or `OR`) with the label-based predicate for `READ_CONTROL`                                                                                                                                                                     |

##### Example

The following statement applies the `hr_ols_pol` policy to the `EMPLOYEES` table in the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.APPLY_TABLE_POLICY(
      policy_name    => 'hr_ols_pol',
      schema_name    => 'HR',
      table_name     => 'EMPLOYEES',
      table_options  => NULL,
      label_function => 'hs(:new.dept,:new.status)',
      predicate      => 'no_control');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.5 SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY

The `SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY` procedure disables the enforcement of the policy for all tables in a schema.

However, it does not change the enforcement options, labeling function, or predicate values.

This procedure removes the row level security predicate and DML triggers from all the tables in the schema.

##### Syntax

    SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY (
      policy_name    IN VARCHAR2,
      schema_name    IN VARCHAR2);

##### Parameters

Table E-24 SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY Parameters

| Parameter     | Description                                                                                                                                                     |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                  |
| `schema_name` | The schema that contains the table for this policy. To find this schema, query the `POLICY_NAME` and `SCHEMA_NAME` columns of the `ALL_SA_TABLE_POLICIES` view. |

##### Example

The following example disables the `hr_ols_pol` policy for the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY(
      policy_name      => 'hr_ols_pol',
      schema_name      => 'HR');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.6 SA_POLICY_ADMIN.DISABLE_TABLE_POLICY

The `SA_POLICY_ADMIN.DISABLE_TABLE_POLICY` procedure disables the enforcement of the policy for a table without changing the enforcement options, labeling function, or predicate values.

This procedure removes the row level security predicate and DML triggers from the table.

##### Syntax

    SA_POLICY_ADMIN.DISABLE_TABLE_POLICY (
      policy_name      IN VARCHAR2,
      schema_name      IN VARCHAR2,
      table_name       IN VARCHAR2);

##### Parameters

Table E-25 SA_POLICY_ADMIN.DISABLE_TABLE_POLICY Parameters

| Parameter     | Description                                                                                                                                                                   |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                |
| `schema_name` | The schema that contains the table. To find this schema, query the `POLICY_NAME` and `SCHEMA_NAME` columns of the `ALL_SA_TABLE_POLICIES` view.                               |
| `table_name`  | The table in the schema specified by `schema_name`. To find this table, query the `POLICY_NAME`, `SCHEMA_NAME`, and `TABLE_NAME` columns of the `ALL_SA_TABLE_POLICIES` view. |

##### Example

The following statement disables the `hr_ols_pos` policy on the `EMPLOYEES` table in the `HR` schema:

    BEGIN
     SA_POLICY_ADMIN.DISABLE_TABLE_POLICY(
      policy_name   => 'hr_ols_pol',
      schema_name   => 'HR',
      table_name    => 'EMPLOYEES');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.7 SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY

The `SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY` procedure reenables the current enforcement options, labeling function, and predicate for the tables in the specified schema.

It accomplishes this by re-applying the row level security predicate and DML triggers. The result is similar to enabling a policy for a table, but it covers all the tables in the schema.

##### Syntax

    SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY (
      policy_name    IN VARCHAR2,
      schema_name    IN VARCHAR2);

##### Parameters

Table E-26 SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY Parameters

| Parameter     | Description                                                                                                                                                   |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies and their status, query the `POLICY_NAME` and `STATUS` columns of the `ALL_SA_POLICIES` data dictionary view. |
| `schema_name` | The schema that contains the table. To find this schema, query the `POLICY_NAME` and `SCHEMA_NAME` columns of the `ALL_SA_TABLE_POLICIES` view.               |

##### Example

The following example enables the `hr_ols_pol` policy for the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.ENABLE_SCHEMA_POLICY(
      policy_name      => 'hr_ols_pol',
      schema_name      => 'HR');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.8 SA_POLICY_ADMIN.ENABLE_TABLE_POLICY

The `SA_POLICY_ADMIN.ENABLE_TABLE_POLICY` procedure reenables the current enforcement options, labeling function, and predicate for the specified table.

It accomplishes this by reapplying the row level security predicate and DML triggers.

##### Syntax

    SA_POLICY_ADMIN.ENABLE_TABLE_POLICY (
      policy_name     IN VARCHAR2,
      schema_name     IN VARCHAR2,
      table_name      IN VARCHAR2);

##### Parameters

Table E-27 SA_POLICY_ADMIN.ENABLE_TABLE_POLICY Parameters

| Parameter     | Description                                                                                                                                                                   |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. `POLICY_NAME` and `STATUS` columns of the `ALL_SA_POLICIES` data dictionary view.                                                                       |
| `schema_name` | The schema that contains the table. To find this schema, query the `POLICY_NAME` and `SCHEMA_NAME` columns of the `ALL_SA_TABLE_POLICIES` view.                               |
| `table_name`  | The table in the schema specified by `schema_name`. To find this table, query the `POLICY_NAME`, `SCHEMA_NAME`, and `TABLE_NAME` columns of the `ALL_SA_TABLE_POLICIES` view. |

##### Example

The following statement reenables the `hr_ols_pol` policy on the `EMPLOYEES` table in the `HR` schema:

    BEGIN
     SA_POLICY_ADMIN.ENABLE_TABLE_POLICY(
      policy_name   => 'hr_ols_pol',
      schema_name   => 'HR',
      table_name    => 'EMPLOYEES');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.9 SA_POLICY_ADMIN.POLICY_SUBSCRIBE

In an Oracle Internet Directory-enabled Oracle Label Security configuration, the `SA_POLICY_ADMIN.POLICY_SUBSCRIBE` procedure subscribes to the policy for usage in `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` and `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY`.

You must call this procedure for a policy before that policy can be applied to a table or schema. Subscribing is needed only once, not for each use of the policy in a table or schema.

You cannot drop any subscribed policy unless it has been removed from any table or schema to which it was applied, and then unsubscribed.

##### Syntax

    SA_POLICY.POLICY_SUBSCRIBE(
      policy_name     IN VARCHAR2);

##### Parameter

Table E-28 SA_POLICY_ADMIN.POLICY_SUBSCRIBE Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

**Note:**

This procedure must be used before policy usage only in the case of Oracle Internet Directory-enabled Oracle Label Security configuration. In the standalone Oracle Label Security case, the policy can be used in `APPLY_TABLE_POLICY` and `APPLY_SCHEMA_POLICY` directly without the need to subscribe.

##### Example

The following statement subscribes the database to the `hr_ols_pol` policy so that it can used by applying on tables and schema.

    BEGIN
     SA_POLICY_ADMIN.POLICY_SUBSCRIBE(
      policy_name   => 'hr_ols_pol');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.10 SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE

In an Oracle Internet Directory enabled Oracle Label Security configuration, the `SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE` procedure unsubscribes to the policy.

You can use this procedure only if the policy is not in use; that is, it has not been applied to any table or schema. (If it has been applied to tables or schemas, then it must be removed from all of them before it can be unsubscribed.) A policy can be dropped in Oracle Internet Directory only if is not subscribed in any of the databases that have registered with that Oracle Internet Directory. To unsubscribe a policy, use the `olsadmintool dropprofile` command.

You cannot drop any subscribed policy unless it has been removed from any table or schema to which it was applied, and then unsubscribed.

##### Syntax

    SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE(
      policy_name  IN VARCHAR2);

##### Parameter

Table E-29 SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following statement unsubscribes the database to the `hr_ols_pol` policy.

    BEGIN
     SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE(
      policy_name   => 'hr_ols_pol');
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.11 SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY

The `SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY` procedure removes the specified policy from a schema.

The policy will be removed from all the tables in the schema and, optionally, the label column for the policy will be dropped from all the tables.

##### Syntax

    SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY (
      policy_name     IN VARCHAR2,
      schema_name     IN VARCHAR2,
      drop_column     IN BOOLEAN DEFAULT FALSE);

##### Parameters

Table E-30 SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY Parameters

| Parameter     | Description                                                                                                                                        |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                     |
| `schema_name` | The schema that contains the table associated with this policy. To find this schema, query the `SCHEMA_NAME` of the `ALL_SA_SCHEMA_POLICIES` view. |
| `drop_column` | If `TRUE`, then the policy's column will be dropped from the tables, otherwise, the column will remain.                                            |

##### Example

The following example drops the `human_resource` policy's column from the `HR` schema.

    BEGIN
     SA_POLICY_ADMIN.REMOVE_SCHEMA_POLICY(
      policy_name      => 'hr_ols_pol',
      schema_name      => 'HR',
      drop_column      => TRUE);
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

#### E.4.12 SA_POLICY_ADMIN.REMOVE_TABLE_POLICY

The `SA_POLICY_ADMIN.REMOVE_TABLE_POLICY` procedure removes the specified policy from a table.

The policy predicate and any DML triggers will be removed from the table, and the policy label column can optionally be dropped. Policies can be removed from tables belonging to a schema that is protected by the policy.

##### Syntax

    SA_POLICY_ADMIN.REMOVE_TABLE_POLICY (
    policy_name        IN VARCHAR2,
    schema_name        IN VARCHAR2,
    table_name         IN VARCHAR2,
    drop_column        IN BOOLEAN DEFAULT FALSE);

##### Parameters

Table E-31 SA_POLICY_ADMIN.REMOVE_TABLE_POLICY Parameters

| Parameter     | Description                                                                                                                                                                  |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                               |
| `schema_name` | The schema that contains the table associated with this policy. To find this schema, query the `SCHEMA_NAME` of the `ALL_SA_SCHEMA_POLICIES` view.                           |
| `table_name`  | The table in the schema specified by `schema_name`. To find this table query the `POLICY_NAME`, `SCHEMA_NAME`, and `TABLE_NAME` columns of the `ALL_SA_TABLE_POLICIES` view. |
| `drop_column` | Whether the column is to be dropped: if `TRUE`, then the policy's column will be dropped from the table, otherwise, it will remain                                           |

##### Example

The following statement removes the `hr_ols_pol` policy from the `EMPLOYEES` table in the `HR` schema:

    BEGIN
     SA_POLICY_ADMIN.REMOVE_TABLE_POLICY(
      policy_name    => 'hr_ols_pol',
      schema_name    => 'HR',
      table_name     => 'EMPLOYEES',
      drop_column    => TRUE);
    END;
    /

**Parent topic:** SA_POLICY_ADMIN Policy Administration PL/SQL Package

### E.5 SA_SESSION Session Management PL/SQL Package

The `SA_SESSION` PL/SQL package manages session behavior for user authorizations.

- About the SA_SESSION PL/SQL Package
  The `SA_SESSION` PL/SQL package manages user name, levels, labels, and read and write permissions for a user session.
- SA_SESSION.COMP_READ
  The `SA_SESSION.COMP_READ` function returns a comma-delimited list of compartments that the user is authorized to read.
- SA_SESSION.COMP_WRITE
  The `SA_SESSION.COMP_WRITE` function returns a comma-delimited list of compartments to which the user is authorized to write.
- SA_SESSION.GROUP_READ
  The `SA_SESSION.GROUP_READ` function returns a comma-delimited list of groups that the user is authorized to read.
- SA_SESSION.GROUP_WRITE
  The `SA_SESSION.GROUP_WRITE` function returns a comma-delimited list of groups that the user is authorized to write.
- SA_SESSION.LABEL
  The `SA_SESSION.LABEL` function returns the label that is associated with the specified policy for the current session.
- SA_SESSION.MAX_LEVEL
  The `SA_SESSION.MAX_LEVEL` function returns the maximum Oracle Label Security level authorized for the session.
- SA_SESSION.MAX_READ_LABEL
  The `SA_SESSION.MAX_READ_LABEL` function returns the label string that was used to initialize the user's maximum authorized read label.
- SA_SESSION.MAX_WRITE_LABEL
  The `SA_SESSION.MAX_WRITE_LABEL` function returns the label string that was used to initialize the user's maximum authorized write label.
- SA_SESSION.MIN_LEVEL
  The `SA_SESSION.MIN_LEVEL` function returns the minimum Oracle Label Security level authorized for the session.
- SA_SESSION.MIN_WRITE_LABEL
  The `SA_SESSION.MIN_WRITE_LABEL` function retrieves the label string that was used to initialize the user's minimum authorized write label.
- SA_SESSION.PRIVS
  The `SA_SESSION.PRIVS` function returns the set of current session privileges, in a comma-delimited list.
- SA_SESSION.RESTORE_DEFAULT_LABELS
  The `SA_SESSION.RESTORE_DEFAULT_LABELS` procedure restores the session label and row label to those stored in the data dictionary.
- SA_SESSION.ROW_LABEL
  The `SA_SESSION.ROW_LABEL` function returns the name of the row label that is associated with the policy for the current session.
- SA_SESSION.SET_LABEL
  The `SA_SESSION.SET_LABEL` procedure sets the label of the current database session.
- SA_SESSION.SA_USER_NAME
  The `SA_SESSION.SA_USER_NAME` function returns the name of the current Oracle Label Security user, as set by the `SA_SESSION.SET_ACCESS_PROFILE` procedure (or as established at login).
- SA_SESSION.SAVE_DEFAULT_LABELS
  The `SA_SESSION.SAVE_DEFAULT_LABELS` procedure stores the current session label and row label as your initial session label and default row label.
- SA_SESSION.SET_ACCESS_PROFILE
  The `SA_SESSION.SET_ACCESS_PROFILE` procedure sets the Oracle Label Security authorizations and privileges of the database session to those of the specified user.
- SA_SESSION.SET_ROW_LABEL
  The `SA_SESSION.SET_ROW_LABEL` procedure sets the default row label value for the current database session.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.5.1 About the SA_SESSION PL/SQL Package

The `SA_SESSION` PL/SQL package manages user name, levels, labels, and read and write permissions for a user session.

Users can change labels during a session within the authorizations set by the administrator.

You do not need special privileges to use this package.

**See Also:**

SA_UTL PL/SQL Utility Functions and Procedures for additional functions that return numeric label tags and `BOOLEAN` values

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.2 SA_SESSION.COMP_READ

The `SA_SESSION.COMP_READ` function returns a comma-delimited list of compartments that the user is authorized to read.

##### Syntax

    SA_SESSION.COMP_READ (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-32 SA_SESSION.COMP_READ Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the compartments that the user can read for the `hr_ols_pol` policy.

    SELECT SA_SESSION.COMP_READ ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.3 SA_SESSION.COMP_WRITE

The `SA_SESSION.COMP_WRITE` function returns a comma-delimited list of compartments to which the user is authorized to write.

This function is a subset of `SA_SESSION.COMP_READ`.

##### Syntax

    SA_SESSION.COMP_WRITE (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-33 SA_SESSION.COMP_WRITE Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the compartments that the user can modify for the `hr_ols_pol` policy.

    SELECT SA_SESSION.COMP_WRITE ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.4 SA_SESSION.GROUP_READ

The `SA_SESSION.GROUP_READ` function returns a comma-delimited list of groups that the user is authorized to read.

##### Syntax

    SA_SESSION.GROUP_READ (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-34 SA_SESSION.GROUP_READ Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the list of groups that a user can read for the `hr_ols_pol` policy.

    SELECT SA_SESSION.GROUP_READ ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.5 SA_SESSION.GROUP_WRITE

The `SA_SESSION.GROUP_WRITE` function returns a comma-delimited list of groups that the user is authorized to write.

This function is a subset of `SA_SESSION.GROUP_READ`.

##### Syntax

    SA_SESSION.GROUP_WRITE (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-35 SA_SESSION.GROUP_WRITE Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the groups the user is authorized to modify for the `hr_ols_pol` policy.

    SELECT SA_SESSION.GROUP_WRITE ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.6 SA_SESSION.LABEL

The `SA_SESSION.LABEL` function returns the label that is associated with the specified policy for the current session.

##### Syntax

    SA_SESSION.LABEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-36 SA_SESSION.LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the label that is associated with the `hr_ols_pol` policy.

    SELECT SA_SESSION.LABEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.7 SA_SESSION.MAX_LEVEL

The `SA_SESSION.MAX_LEVEL` function returns the maximum Oracle Label Security level authorized for the session.

##### Syntax

    SA_SESSION.MAX_LEVEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-37 SA_SESSION.MAX_LEVEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the maximum Oracle Label Security level that is authorized for the `hr_ols_pol` policy.

    SELECT SA_SESSION.MAX_LEVEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.8 SA_SESSION.MAX_READ_LABEL

The `SA_SESSION.MAX_READ_LABEL` function returns the label string that was used to initialize the user's maximum authorized read label.

The return string is composed of the user's maximum level, compartments authorized for read access, and groups authorized for read access.

##### Syntax

    SA_SESSION.MAX_READ_LABEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-38 SA_SESSION.MAX_READ_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the maximum read label privileges for the `hr_ols_pol` policy.

    SELECT SA_SESSION.MAX_READ_LABEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.9 SA_SESSION.MAX_WRITE_LABEL

The `SA_SESSION.MAX_WRITE_LABEL` function returns the label string that was used to initialize the user's maximum authorized write label.

This return string is composed of the user's maximum level, compartments authorized for write access, and groups authorized for write access.

##### Syntax

    SA_SESSION.MAX_WRITE_LABEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-39 SA_SESSION.MAX_WRITE_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the maximum write label privileges for the `hr_ols_pol` policy.

    SELECT SA_SESSION.MAX_WRITE_LABEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.10 SA_SESSION.MIN_LEVEL

The `SA_SESSION.MIN_LEVEL` function returns the minimum Oracle Label Security level authorized for the session.

##### Syntax

    SA_SESSION.MIN_LEVEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-40 SA_SESSION.MIN_LEVEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the current minimum level for the `hr_ols_pol` policy.

    SELECT SA_SESSION.MIN_LEVEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.11 SA_SESSION.MIN_WRITE_LABEL

The `SA_SESSION.MIN_WRITE_LABEL` function retrieves the label string that was used to initialize the user's minimum authorized write label.

The return string contains only the level, with no compartments or groups.

##### Syntax

    SA_SESSION.MIN_WRITE_LABEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-41 SA_SESSION.MIN_WRITE_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the maximum write label privileges for the `hr_ols_pol` policy.

    SELECT SA_SESSION.MIN_WRITE_LABEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.12 SA_SESSION.PRIVS

The `SA_SESSION.PRIVS` function returns the set of current session privileges, in a comma-delimited list.

##### Syntax

    SA_SESSION.PRIVS (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-42 SA_SESSION.Privs Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the current session privileges for the `hr_ols_pol` policy.

    SELECT SA_SESSION.PRIVS ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.13 SA_SESSION.RESTORE_DEFAULT_LABELS

The `SA_SESSION.RESTORE_DEFAULT_LABELS` procedure restores the session label and row label to those stored in the data dictionary.

This command is useful to reset values after a `SA_SESSION.SET_LABEL` command has been processed.

##### Syntax

    SA_SESSION.RESTORE_DEFAULT_LABELS (
     policy_name in VARCHAR2);

##### Parameter

Table E-43 SA_SESSION.RESTORE_DEFAULT_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example restores the default labels for the `hr_ols_pol` policy.

    BEGIN
     SA_SESSION.RESTORE_DEFAULT_LABELS (
      policy_name         => 'hr_ols_pol');
    END;
    /

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.14 SA_SESSION.ROW_LABEL

The `SA_SESSION.ROW_LABEL` function returns the name of the row label that is associated with the policy for the current session.

##### Syntax

    SA_SESSION.ROW_LABEL (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-44 SA_SESSION.ROW_LABEL Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns the row label that is associated with the `hr_ols_pol` policy.

    SELECT SA_SESSION.ROW_LABEL ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.15 SA_SESSION.SET_LABEL

The `SA_SESSION.SET_LABEL` procedure sets the label of the current database session.

You can set the session label to:

- Any level equal to or less than the maximum, and equal to or greater than the minimum level

- Include any compartments in the authorized compartment list

- Include any groups in the authorized group list. (Subgroups of authorized groups are implicitly included in the authorized list.)

Note that if you change the session label, this change may affect the value of the session's row label. The session's row label contains the subset of compartments and groups for which the user has write access. This may or may not be equivalent to the session label. For example, if you use the `SA_SESSION.SET_LABEL` procedure to set your current session label to `C:A,B:US` and you have write access only on the `A` compartment, then your row label would be set to `C:A`.

##### Syntax

    SA_SESSION.SET_LABEL (
     policy_name IN VARCHAR2,
     label       IN VARCHAR2);

##### Parameters

Table E-45 SA_SESSION.SET_LABEL Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `label`       | The value to set as the label                                                                                                  |

##### Example

The following example sets the label for the `hr_ols_pol` policy.

    BEGIN
     SA_SESSION.SET_LABEL (
      policy_name         => 'hr_ols_pol',
      label               => 'C:A,B:US');
    END;
    /

**Related Topics**

- SA_USER_ADMIN.SET_DEFAULT_LABEL

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.16 SA_SESSION.SA_USER_NAME

The `SA_SESSION.SA_USER_NAME` function returns the name of the current Oracle Label Security user, as set by the `SA_SESSION.SET_ACCESS_PROFILE` procedure (or as established at login).

This is how you can determine the identity of the current user in relation to Oracle Label Security, rather than in relation to your Oracle login name.

##### Syntax

    SA_SESSION.SA_USER_NAME (
      policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table E-46 SA_SESSION.SA_USER_NAME Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example finds the name of the Oracle Label Security user for the `hr_ols_pol` policy.

    SELECT SA_SESSION.SA_USER_NAME ('hr_ols_pol') FROM DUAL;

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.17 SA_SESSION.SAVE_DEFAULT_LABELS

The `SA_SESSION.SAVE_DEFAULT_LABELS` procedure stores the current session label and row label as your initial session label and default row label.

This procedure permits you to change your defaults to reflect your current session label and row label. The saved labels will be used as the initial default settings for future sessions.

When you log in to a database, your default session label and row label are used to initialize the session label and row label. When the administrator originally authorized your Oracle Label Security labels, he or she also defined your default level, default compartments, and default groups. If you change your session label and row label, and want to save these values as the default labels, you can use the `SA_SESSION.SAVE_DEFAULT_LABELS` procedure.

This procedure is useful if you have multiple sessions and want to be sure that all additional sessions have the same labels. You can save the current labels as the default, and all future sessions will have these as the initial labels.

Consider a situation in which you connect to the database through Oracle Forms and want to run a report. By saving the current session labels as the default before you call Oracle Reports, you ensure that Oracle Reports will initialize at the same labels as are being used by Oracle Forms.

##### Syntax

    SA_SESSION.SAVE_DEFAULT_LABELS (
      policy_name IN VARCHAR2);

##### Parameter

Table E-47 SA_SESSION.SAVE_DEFAULT_LABELS Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example saves the label defaults for the `hr_ols_pol` policy.

    BEGIN
     SA_SESSION.SAVE_DEFAULT_LABELS (
      policy_name       => 'hr_ols_pol');
    END;
    /

**Note:**

The `SA_SESSION.SAVE_DEFAULT_LABELS` procedure overrides the settings established by the administrator.

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.18 SA_SESSION.SET_ACCESS_PROFILE

The `SA_SESSION.SET_ACCESS_PROFILE` procedure sets the Oracle Label Security authorizations and privileges of the database session to those of the specified user.

Note that the originating user retains the `PROFILE_ACCESS` privilege.

The user who executes the `SA_SESSION.SET_ACCESS_PROFILE` procedure must have the `PROFILE_ACCESS` privilege. The logged-in database user (the Oracle user ID) does not change. That user assumes only the authorizations and privileges of the specified user. By contrast, the Oracle Label Security user name is changed.

This administrative procedure is useful for various tasks:

- With `SA_SESSION.SET_ACCESS_PROFILE`, you can see the result of the authorization and privilege settings for a particular user.

- Applications need to have proxy accounts connect as (and assume the identity of) application users, for purposes of accessing labeled data. With the `SA_SESSION.SET_ACCESS_PROFILE` privilege, the proxy account can act on behalf of the application users.

##### Syntax

    SA_SESSION.SET_ACCESS_PROFILE (
      policy_name IN VARCHAR2
      user_name   IN VARCHAR2);

##### Parameters

Table E-48 SA_SESSION.SET_ACCESS_PROFILE Parameters

| Parameter     | Description                                                                                                                                                                                                              |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                           |
| `user_name`   | Name of the user whose authorizations and privileges should be assumed (typically, the user associated with this policy). To find this user, query the `USER_NAME` and `POLICY_NAME` columns of the `DBA_SA_USERS` view. |

##### Example

The following example enables user `psmith` to have Oracle Label Security authorizations and privileges for the database session.

    BEGIN
     SA_SESSION.SET_ACCESS_PROFILE (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jjones');
    END;
    /

**Parent topic:** SA_SESSION Session Management PL/SQL Package

#### E.5.19 SA_SESSION.SET_ROW_LABEL

The `SA_SESSION.SET_ROW_LABEL` procedure sets the default row label value for the current database session.

The compartments and groups in the label must be a subset of the compartments and groups in the session label to which the user has write access. When the `LABEL_DEFAULT` option is set, this row label value is used on insert if the user does not explicitly specify the label.

If the `SA_SESSION.SET_ROW_LABEL` procedure is not used to set the default row label value, then this value is automatically derived from the session label. It contains the level of the session label and the subset of the compartments and groups in the session label for which the user has write authorization.

The row label is automatically reset if the session label changes. For example, if you change your session level from `HIGHLY_SENSITIVE` to `SENSITIVE`, then the level component of the row label automatically changes to `SENSITIVE`.

The user can set the row label independently, but only to include:

- A level that is less than or equal to the level of the session label, and greater than or equal to the user's minimum level

- A subset of the compartments and groups from the session label, for which the user is authorized to have write access

If the user tries to set the row label to an invalid value, then the operation is not permitted and the row label value is unchanged.

##### Syntax

    SA_SESSION.SET_ROW_LABEL (
     policy_name   IN VARCHAR2,
     row_label     IN VARCHAR2);

##### Parameters

Table E-49 SA_SESSION.SET_ROW_LABEL Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `label`       | The value to set as the default row label                                                                                      |

##### Example

The following example sets the row label for the `hr_ols_pol` policy.

    BEGIN
     SA_SESSION.SET_ROW_LABEL (
      policy_name     => 'hr_ols_pol',
      label           => 'HR');
    END;
    /

**Related Topics**

- SA_USER_ADMIN.SET_ROW_LABEL

**Parent topic:** SA_SESSION Session Management PL/SQL Package

### E.6 SA_SYSDBA Policy Management PL/SQL Package

The `SA_SYSDBA` PL/SQL package manages Oracle Label Security policies.

- About the SA_SYSDBA PL/SQL Package
  The `SA_SYSDBA` PL/SQL package creates, modifies, enables or disables, and drops Oracle Label Security policies.
- SA_SYSDBA.ALTER_POLICY
  The `SA_SYSDBA.ALTER_POLICY` procedure sets and modifies column names that are associated with the policy.
- SA_SYSDBA.CREATE_POLICY
  The `SA_SYSDBA.CREATE_POLICY` procedure creates a new Oracle Label Security policy, defines a policy-specific column name, and specifies default policy options.
- SA_SYSDBA.DISABLE_POLICY
  The `SA_SYSDBA.DISABLE_POLICY` procedure turns off enforcement of a policy, without removing it from the database.
- SA_SYSDBA.DROP_POLICY
  The `SA_SYSDBA.DROP_POLICY` procedure deletes the policy and its associated user labels and data labels from the database.
- SA_SYSDBA.ENABLE_POLICY
  The `SA_SYSDBA.ENABLE_POLICY` procedure enforces access control on the tables and schemas protected by the policy.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.6.1 About the SA_SYSDBA PL/SQL Package

The `SA_SYSDBA` PL/SQL package creates, modifies, enables or disables, and drops Oracle Label Security policies.

To use this package, you must be granted the `LBAC_DBA` role and the `EXECUTE` privilege on the `SA_SYSDBA` package. The `SA_SYSDBA` package is an invoker’s rights package, so you must provide the following `INHERIT PRIVILEGES` grant to the user `SYS` before you can use this package:

    GRANT INHERIT PRIVILEGES ON USER SYS TO LBACSYS;

You only need to grant this privilege on user `SYS.` You do not need to grant it on other users.

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

#### E.6.2 SA_SYSDBA.ALTER_POLICY

The `SA_SYSDBA.ALTER_POLICY` procedure sets and modifies column names that are associated with the policy.

`SA_SYSDBA.ALTER_POLICY` can only be used to change column name for policies that are not applied on any user tables or schemas. Otherwise, this error appears:

    12474, 00000, "cannot change column name for a policy in use"

##### Syntax

    SA_SYSDBA.ALTER_POLICY (
       policy_name       IN  VARCHAR2,
       default_options   IN  VARCHAR2 DEFAULT NULL,
       column_name       IN  VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-50 SA_SYSDBA.ALTER_POLICY Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                             |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                                                                          |
| `default_options` | Specifies the default enforcement options to be used when the policy is applied and no table- or schema-specific options are specified. Includes enforcement options and the option to hide the label column. Separate each option with a comma.<br>See [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the default enforcement options. |
| `column_name`     | Specifies the column name associated with the policy. To find this column name, query the `COLUMN_NAME` column of the `ALL_SA_POLICIES` view.                                                                                                                                                                                                                                                                           |

##### Example

The following example updates the `hr_ols_pol` policy to use a different set of default options. Because the name of the column does not need to change, the `column_name` parameter is omitted.

    BEGIN
     SA_SYSDBA.ALTER_POLICY (
      policy_name      => 'hr_ols_pol',
      default_options  => 'read_control, delete_control');
    END;
    /

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

#### E.6.3 SA_SYSDBA.CREATE_POLICY

The `SA_SYSDBA.CREATE_POLICY` procedure creates a new Oracle Label Security policy, defines a policy-specific column name, and specifies default policy options.

After you create the policy, a role for it is created and granted to you. The format of the role name is `policy_``DBA` (for example, `my_ols_pol_DBA`).

##### Syntax

    SA_SYSDBA.CREATE_POLICY (
       policy_name       IN VARCHAR2,
       column_name       IN VARCHAR2 DEFAULT NULL,
       default_options   IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-51 SA_SYSDBA.CREATE_POLICY Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy name, which must be unique within the database. It can have a maximum of 30 characters, but only the first 26 characters in the `policy_name` are significant. Two policies may not have the same first 26 characters in the `policy_name`.<br>To find a list of existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                      |
| `column_name`     | Specifies the name of the column to be added to tables protected by the policy. If `NULL`, then the name `policy_name``_COL` is used. Two Oracle Label Security policies cannot share the same column name.                                                                                                                                                                                                 |
| `default_options` | Specifies the default options to be used when the policy is applied and no table- or schema-specific options are specified. Includes enforcement options and the option to hide the label column. Separate each option with a comma.<br>See [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the default enforcement options. |

##### Example

The following example creates a policy container whose default options are `READ_CONTROL` and `WRITE_CONTROL`. The `WRITE_CONTROL` option encompasses the `INSERT_CONTROL`, `UPDATE_CONTROL`, and `DELETE_CONTROL` options.

    BEGIN
     SA_SYSDBA.CREATE_POLICY (
      policy_name      => 'hr_ols_pol',
      column_name      => 'ols_col',
      default_options  => 'read_control, write_control');
    END;
    /

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

#### E.6.4 SA_SYSDBA.DISABLE_POLICY

The `SA_SYSDBA.DISABLE_POLICY` procedure turns off enforcement of a policy, without removing it from the database.

The policy is not enforced for all subsequent access to the database.

To disable a policy means that no access control is enforced on the tables and schemas protected by the policy. The administrator can continue to perform administrative operations while the policy is disabled.

**Note:**

This feature is extremely powerful, and should be used with caution. When a policy is disabled, anyone who connects to the database can access all the data normally protected by the policy. So, your site should establish guidelines for use of this feature.

Normally, a policy should not be disabled in order to manage data. At times, however, an administrator may need to disable a policy to perform application debugging tasks. In this case, the database should be run in single-user mode. In a development environment, for example, you may need to observe data processing operations without the policy turned on. When you reenable the policy, all of the selected enforcement options become effective again.

##### Syntax

    SA_SYSDBA.DISABLE_POLICY (
     policy_name IN VARCHAR2);

##### Parameters

Table E-52 SA_SYSDBA.DISABLE_POLICY Parameters

| Parameter     | Description                                                                                                                                                   |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies and their status, query the `POLICY_NAME` and `STATUS` columns of the `ALL_SA_POLICIES `data dictionary view. |

##### Example

The following example disables the `hr_ols_pol` policy:

    EXEC SA_SYSDBA.DISABLE_POLICY ('hr_ols_pol');

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

#### E.6.5 SA_SYSDBA.DROP_POLICY

The `SA_SYSDBA.DROP_POLICY` procedure deletes the policy and its associated user labels and data labels from the database.

This procedure purges the policy and these associations from the system entirely. You can optionally drop the label column from all tables controlled by the policy. The policy does not need to be disabled before you drop it.

##### Syntax

    SA_SYSDBA.DROP_POLICY (
       policy_name IN VARCHAR2,
       drop_column  BOOLEAN DEFAULT FALSE);

##### Parameters

Table E-53 SA_SYSDBA.DROP_POLICY Parameters

| Parameter     | Description                                                                                                                                  |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy to be dropped. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `drop_column` | Indicates that the policy column should be dropped from protected tables (`TRUE`)                                                            |

##### Example

The following example deletes the `hr_ols_pol` policy.

    EXEC SA_SYSDBA.DROP_POLICY ('hr_ols_pol');

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

#### E.6.6 SA_SYSDBA.ENABLE_POLICY

The `SA_SYSDBA.ENABLE_POLICY` procedure enforces access control on the tables and schemas protected by the policy.

A policy is automatically enabled when it is created. After creation or enablement, the policy is enforced for all subsequent access to tables protected by the policy.

##### Syntax

    SA_SYSDBA.ENABLE_POLICY (policy_name IN VARCHAR2);

##### Parameters

Table E-54 SA_SYSDBA.ENABLE_POLICY Parameters

| Parameter     | Description                                                                                                                                                   |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies and their status, query the `POLICY_NAME` and `STATUS` columns of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example enables the `hr_ols_pol` policy.

    EXEC SA_SYSDBA.ENABLE_POLICY('hr_ols_pol');

**Parent topic:** SA_SYSDBA Policy Management PL/SQL Package

### E.7 SA_USER_ADMIN PL/SQL Package

The `SA_USER_ADMIN` PL/SQL package manages user labels by label component.

- About the SA_USER_ADMIN PL/SQL Package
  The `SA_USER_ADMIN` PL/SQL package configures compartments, groups, user access, labels, levels, and privileges.
- SA_USER_ADMIN.ADD_COMPARTMENTS
  The `SA_USER_ADMIN.ADD_COMPARTMENTS` procedure adds (assigns) compartments to a user's authorizations, indicating if the compartments are authorized for write and read privileges.
- SA_USER_ADMIN.ADD_GROUPS
  The `SA_USER_ADMIN.ADD_GROUPS` procedure adds (assigns) groups to a user, indicating if the groups are authorized for write and read privileges.
- SA_USER_ADMIN.ALTER_COMPARTMENTS
  The `SA_USER_ADMIN.ALTER_COMPARTMENTS` procedure changes the write access, default label indicator, and row label indicator for the specified compartments.
- SA_USER_ADMIN.ALTER_GROUPS
  The `SA_USER_ADMIN.ALTER_GROUPS` procedure changes the write access, default label indicator, and row label indicator for the specified groups.
- SA_USER_ADMIN.DROP_ALL_COMPARTMENTS
  The `SA_USER_ADMIN.DROP_ALL_COMPARTMENTS` procedure drops all compartments from a user's authorizations.
- SA_USER_ADMIN.DROP_ALL_GROUPS
  The `SA_USER_ADMIN.DROP_ALL_GROUPS` procedure drops all groups from a user's authorizations.
- SA_USER_ADMIN.DROP_COMPARTMENTS
  The `SA_USER_ADMIN.DROP_COMPARTMENTS` procedure drops the specified compartments from a user's authorizations.
- SA_USER_ADMIN.DROP_GROUPS
  The `SA_USER_ADMIN.DROP_GROUPS` procedure drops the specified groups from a user's authorizations.
- SA_USER_ADMIN.DROP_USER_ACCESS
  The `SA_USER_ADMIN.DROP_USER_ACCESS` procedure removes all Oracle Label Security authorizations and privileges from the specified user.
- SA_USER_ADMIN.SET_COMPARTMENTS
  The `SA_USER_ADMIN.SET_COMPARTMENTS` procedure assigns compartments to a user and identifies default values for the user's session label and row label.
- SA_USER_ADMIN.SET_DEFAULT_LABEL
  The `SA_USER_ADMIN.SET_DEFAULT_LABEL` procedure sets the user's initial session label to the one specified.
- SA_USER_ADMIN.SET_GROUPS
  The `SA_USER_ADMIN.SET_GROUPS` procedure assigns groups to a user and identifies default values for the user's session label and row label.
- SA_USER_ADMIN.SET_LEVELS
  The `SA_USER_ADMIN.SET_LEVELS` procedure assigns a user minimum and maximum levels and identifies default values for the user's session label and row label.
- SA_USER_ADMIN.SET_PROG_PRIVS
  The `SA_USER_ADMIN.SET_PROG_PRIVS` procedure sets policy-specific privileges for program units.
- SA_USER_ADMIN.SET_ROW_LABEL
  The `SA_USER_ADMIN.SET_ROW_LABEL` procedure sets a user's initial row label to the one specified.
- SA_USER_ADMIN.SET_USER_LABELS
  The `SA_USER_ADMIN.SET_USER_LABELS` procedure sets the user's levels, compartments, and groups using a set of labels, instead of the individual components.
- SA_USER_ADMIN.SET_USER_PRIVS
  The `SA_USER_ADMIN.SET_USER_PRIVS` procedure sets policy-specific privileges for users.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.7.1 About the SA_USER_ADMIN PL/SQL Package

The `SA_USER_ADMIN` PL/SQL package configures compartments, groups, user access, labels, levels, and privileges.

To use this package, you must be granted the `policy_``DBA` role (for example, `HR_OLS_POL_DBA` for a role for the `hr_ols_pol` policy) and the `EXECUTE` privilege on the `SA_USER_ADMIN` package.

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.2 SA_USER_ADMIN.ADD_COMPARTMENTS

The `SA_USER_ADMIN.ADD_COMPARTMENTS` procedure adds (assigns) compartments to a user's authorizations, indicating if the compartments are authorized for write and read privileges.

This procedure is useful if you have already used the `SA_USER_ADMIN.SET_COMPARTMENTS` procedure for the user but then decide that you want to grant this user authorization for additional compartments, or to update the current set of compartments. You also can use it in place of `SA_USER_ADMIN.SET_COMPARTMENTS`.

##### Syntax

    SA_USER_ADMIN.ADD_COMPARTMENTS (
    policy_name    IN VARCHAR2,
    user_name      IN VARCHAR2,
    comps          IN VARCHAR2,
    access_mode    IN VARCHAR2 DEFAULT NULL,
    in_def         IN VARCHAR2 DEFAULT NULL,
    in_row         IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-55 SA_USER_ADMIN.ADD_COMPARTMENTS Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                         |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                      |
| `user_name`   | Specifies the user name. This user can be either a new user or a user who has already been authorized for this policy's compartments. To find an existing user, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS` view.                                                                                                                |
| `comps`       | A comma-delimited list of compartments to add, by short name only. To find existing compartments, query the `SHORT_NAME` column of the `ALL_SA_COMPARTMENTS` view.                                                                                                                                                                                  |
| `access_mode` | One of two public variables that contain string values that can specify the type of access authorized. The variable names, values, and meaning are as follows:<br>• `SA_UTL.READ_ONLY` indicates no write access<br>• `SA_UTL.READ_WRITE` indicates that write is authorized<br>• If `access_mode` is `NULL`, then it is set to `SA_UTL.READ_ONLY`. |
| `in_def`      | Specifies whether these compartments should be in the default compartments (`Y`/`N`)<br>If `in_def` is `NULL`, then it is set to `Y`.                                                                                                                                                                                                               |
| `in_row`      | Specifies whether these compartments should be in the row label (`Y`/`N`)<br>If `in_row` is `NULL`, then it is set to `N`.                                                                                                                                                                                                                          |

##### Example

The following example adds compartments to the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.ADD_COMPARTMENTS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      comps          => 'FIN',
      access_mode    => SA_UTL.READ_ONLY,
      in_def         => 'y',
      in_row         => 'y');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.3 SA_USER_ADMIN.ADD_GROUPS

The `SA_USER_ADMIN.ADD_GROUPS` procedure adds (assigns) groups to a user, indicating if the groups are authorized for write and read privileges.

This procedure is useful if you have already used the `SA_USER_ADMIN.SET_GROUPS` procedure for the user but then decide that you want to grant this user authorization for additional groups or to update the current set of groups. You also can use it in place of `SA_USER_ADMIN.SET_GROUPS`.

##### Syntax

    SA_USER_ADMIN.ADD_GROUPS (
      policy_name       IN VARCHAR2,
      user_name         IN VARCHAR2,
      groups            IN VARCHAR2,
      access_mode       IN VARCHAR2 DEFAULT NULL,
      in_def            IN VARCHAR2 DEFAULT NULL,
      in_row            IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-56 SA_USER_ADMIN.ADD_GROUPS Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                    |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                 |
| `user_name`   | Specifies the user. This user can be either a new user or a user who has already been authorized for this policy's groups. To find an existing user, query the `USER_NAME` column of the `DBA_SA_USER_GROUPS` view.                                                                                                                                            |
| `groups`      | A comma-delimited list of groups to add, by short name only. To find a list of existing groups, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.                                                                                                                                                                                                     |
| `access_mode` | One of two public variables that contain string values that can specify the type of access authorized. The variable names, values, and meaning are as follows:<br>• `SA_UTL.READ_ONLY` indicates no write access<br>• `SA_UTL.READ_WRITE` indicates that write is authorized<br>• If `access_mode` is `NULL`, then `access_mode` is set to `SA_UTL.READ_ONLY`. |
| `in_def`      | Specifies whether these groups should be in the default groups (`Y`/`N`)<br>If `in_def` is `NULL`, then it is set to `Y`.                                                                                                                                                                                                                                      |
| `in_row`      | Specifies whether these groups should be in the row label (`Y`/`N`)<br>If `in_row` is `NULL`, then it is set to `N`.                                                                                                                                                                                                                                           |

##### Example

The following example adds several groups to the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.ADD_GROUPS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      groups         => 'ER_FIN, SR_FIN, NR_FIN, WR_FIN',
      access_mode    => SA_UTL.READ_WRITE,
      in_def         => 'y',
      in_row         => 'y');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.4 SA_USER_ADMIN.ALTER_COMPARTMENTS

The `SA_USER_ADMIN.ALTER_COMPARTMENTS` procedure changes the write access, default label indicator, and row label indicator for the specified compartments.

##### Syntax

    SA_USER_ADMIN.ALTER_COMPARTMENTS (
      policy_name  IN VARCHAR2,
      user_name    IN VARCHAR2,
      comps        IN VARCHAR2,
      access_mode  IN VARCHAR2 DEFAULT NULL,
      in_def       IN VARCHAR2 DEFAULT NULL,
      in_row       IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-57 SA_USER_ADMIN.ALTER_COMPARTMENTS Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                               |
| `user_name`   | Specifies the user who has been authorized for the compartment. To find authorized users, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS` view.                                                                                                                                                                                               |
| `comps`       | A comma-delimited list of compartments to modify, using the short name only. To find existing compartments, query the `SHORT_NAME` column of the `ALL_SA_COMPARTMENTS` view.                                                                                                                                                                                 |
| `access_mode` | One of two public variables that contain string values that can specify the type of access authorized. The variable names, values, and meaning are as follows:<br>`SA_UTL.READ_ONLY` indicates no write access<br>`SA_UTL.READ_WRITE` indicates that write is authorized<br>If `access_mode` is `NULL`, then `access_mode` for the compartment is unaltered. |
| `in_def`      | Specifies whether these compartments should be in the default compartments (`Y`/`N`)<br>If `in_def` is `NULL`, then `in_def` for the compartment is unaltered.                                                                                                                                                                                               |
| `in_row`      | Specifies whether these compartments should be in the row label (`Y`/`N`)<br>If `in_row` is `NULL`, then `in_row` for the compartment is unaltered.<br>If `in_def` is `N`, then `in_row` cannot be `Y`. This is because the row label compartments must be a subset of the session label compartments.                                                       |

##### Example

The following example modifies compartments for the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.ALTER_COMPARTMENTS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      comps          => 'FIN',
      access_mode    => SA_UTL.READ_ONLY,
      in_def         => 'y',
      in_row         => 'y');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.5 SA_USER_ADMIN.ALTER_GROUPS

The `SA_USER_ADMIN.ALTER_GROUPS` procedure changes the write access, default label indicator, and row label indicator for the specified groups.

##### Syntax

    SA_USER_ADMIN.ALTER_GROUPS (
      policy_name      IN VARCHAR2,
      user_name        IN VARCHAR2,
      groups           IN VARCHAR2,
      access_mode      IN VARCHAR2 DEFAULT NULL,
      in_def           IN VARCHAR2 DEFAULT NULL,
      in_row           IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-58 SA_USER_ADMIN.ALTER_GROUPS Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                             |
| `user_name`   | Specifies the user who has been authorized for the group. To find existing users, query the `USER_NAME` and `GRP` columns of the `DBA_SA_USER_GROUPS` view.                                                                                                                                                                                |
| `groups`      | A comma-delimited list of groups to alter, by short name only. To find existing groups, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.                                                                                                                                                                                         |
| `access_mode` | Two public variables contain string values that can specify the type of access authorized. The variable names, values, and meaning are as follows:<br>`SA_UTL.READ_ONLY` indicates no write access<br>`SA_UTL.READ_WRITE` indicates that write is authorized<br>If `access_mode` is `NULL`, then `access_mode` for the group is unaltered. |
| `in_def`      | Specifies whether these groups should be in the default groups (`Y`/`N`)<br>If `in_def` is `NULL`, then `in_def` for the group is unaltered.                                                                                                                                                                                               |
| `in_row`      | Specifies whether these groups should be in the row label ((`Y`/`N`)<br>If `in_row` is `NULL`, then `in_row` for the group is unaltered.<br>If `in_def` is `N`, then `in_row` cannot be `Y`. This is because the row label groups must be a subset of the session label groups.                                                            |

##### Example

The following example sets the access mode for the existing groups to be read only.

    BEGIN
     SA_USER_ADMIN.ALTER_GROUPS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      groups         => 'ER',
      access_mode    => SA_UTL.READ_ONLY);
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.6 SA_USER_ADMIN.DROP_ALL_COMPARTMENTS

The `SA_USER_ADMIN.DROP_ALL_COMPARTMENTS` procedure drops all compartments from a user's authorizations.

##### Syntax

    SA_USER_ADMIN.DROP_ALL_COMPARTMENTS (
     policy_name  IN VARCHAR2,
     user_name    IN VARCHAR2);

##### Parameters

Table E-59 SA_USER_ADMIN.DROP_ALL_COMPARTMENTS Parameters

| Parameter     | Description                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                               |
| `user_name`   | Specifies the user who has been authorized for the compartment. To find existing users, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS` view. |

##### Example

The following example drops all compartments for the `hr_ols_pol` policy for user `jjones`.

    BEGIN
     SA_USER_ADMIN.DROP_ALL_COMPARTMENTS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.7 SA_USER_ADMIN.DROP_ALL_GROUPS

The `SA_USER_ADMIN.DROP_ALL_GROUPS` procedure drops all groups from a user's authorizations.

##### Syntax

    SA_USER_ADMIN.DROP_ALL_GROUPS (
      policy_name IN VARCHAR2,
      user_name   IN VARCHAR2);

##### Parameters

Table E-60 SA_USER_ADMIN.DROP_ALL_GROUPS Parameters

| Parameter     | Description                                                                                                                                                 |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                              |
| `user_name`   | Specifies the user who has been authorized for the group. To find existing users, query the `USER_NAME` and `GRP` columns of the `DBA_SA_USER_GROUPS` view. |

##### Example

The following example drops all groups from the `hr_ols_pol` policy for user `jjones`.

    BEGIN
     SA_USER_ADMIN.DROP_ALL_GROUPS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.8 SA_USER_ADMIN.DROP_COMPARTMENTS

The `SA_USER_ADMIN.DROP_COMPARTMENTS` procedure drops the specified compartments from a user's authorizations.

##### Syntax

    SA_USER_ADMIN.DROP_COMPARTMENTS (
      policy_name     IN VARCHAR2,
      user_name       IN VARCHAR2,
      comps           IN VARCHAR2);

##### Parameters

Table E-61 SA_USER_ADMIN.DROP_COMPARTMENTS Parameters

| Parameter     | Description                                                                                                                                                           |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                        |
| `user_name`   | Specifies the user who has been authorized for the compartment. To find existing users, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS` view.          |
| `comps`       | A comma-delimited list of compartments to drop. To find all comps for this policy, query the `POLICY_NAME` and `COMP` columns of the `DBA_SA_USER_COMPARTMENTS` view. |

##### Example

The following example drops the `FINANCIAL` compartment from the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.DROP_COMPARTMENTS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      comps          => 'HR');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.9 SA_USER_ADMIN.DROP_GROUPS

The `SA_USER_ADMIN.DROP_GROUPS` procedure drops the specified groups from a user's authorizations.

##### Syntax

    SA_USER_ADMIN.DROP_GROUPS (
      policy_name IN VARCHAR2,
      user_name   IN VARCHAR2,
      groups      IN VARCHAR2);

##### Parameters

Table E-62 SA_USER_ADMIN.DROP_GROUPS Parameters

| Parameter     | Description                                                                                                                                                 |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                              |
| `user_name`   | Specifies the user who has been authorized for the group. To find existing users, query the `USER_NAME` and `GRP` columns of the `DBA_SA_USER_GROUPS` view. |
| `groups`      | A comma-delimited list of groups to drop, by short name only. To find a list of groups, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.          |

##### Example

The following example drops the `NR_FIN` group from the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.DROP_GROUPS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      groups         => 'ER');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.10 SA_USER_ADMIN.DROP_USER_ACCESS

The `SA_USER_ADMIN.DROP_USER_ACCESS` procedure removes all Oracle Label Security authorizations and privileges from the specified user.

##### Syntax

    SA_USER_ADMIN.DROP_USER_ACCESS (
      policy_name      IN VARCHAR2,
      user_name        IN VARCHAR2);

##### Parameters

Table E-63 SA_USER_ADMIN.DROP_USER_ACCESS Parameters

| Parameter     | Description                                                                                                                                              |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                           |
| `user_name`   | Specifies the user name. To find all users associated with this policy, query the `USER_NAME` and `POLICY_NAME` columns of the `DBA_SA_USER_PRIVS` view. |

##### Examples

The following example removes user `jjones`'s authorization for the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.DROP_USER_ACCESS (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jjones');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.11 SA_USER_ADMIN.SET_COMPARTMENTS

The `SA_USER_ADMIN.SET_COMPARTMENTS` procedure assigns compartments to a user and identifies default values for the user's session label and row label.

After you have set the compartment, you can configure additional compartments by using the `SA_USER_ADMIN.ADD_COMPARTMENTS` procedure. (See SA_USER_ADMIN.ADD_COMPARTMENTS.)

All users must have their levels set before their authorized compartments can be established.

The write compartments, if specified, must be a subset of the read compartments. (The write compartments are those to which the user should have write access.)

##### Syntax

    SA_USER_ADMIN.SET_COMPARTMENTS (
      policy_name   IN VARCHAR2,
      user_name     IN VARCHAR2,
      read_comps    IN VARCHAR2,
      write_comps   IN VARCHAR2 DEFAULT NULL,
      def_comps     IN VARCHAR2 DEFAULT NULL,
      row_comps     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-64 SA_USER_ADMIN.SET_COMPARTMENTS Parameters

| Parameter     | Description                                                                                                                                                                                                                         |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                      |
| `user_name`   | Specifies the user name to assign compartments                                                                                                                                                                                      |
| `read_comps`  | A comma-delimited list of compartments authorized for read access, by short name only<br>To find all compartments, query the `SHORT_NAME` column of the `ALL_SA_COMPARTMENTS` view.                                                 |
| `write_comps` | A comma-delimited list of compartments authorized for write access (subset of `read_comps`), by short name only. If `write_comps` are `NULL`, then they are set to the `read_comps`.                                                |
| `def_comps`   | Specifies the default compartments, by short name only. This must be a subset of `read_comps`. If the `def_comps` are `NULL`, then they are set to the `read_comps`.                                                                |
| `row_comps`   | Specifies the row compartments, by short name only. This must be a subset of `write_comps` and `def_comps`. If the `row_comps` are `NULL`, then they are set to the components in `def_comps` that are authorized for write access. |

##### Example

The following example sets compartments for the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.SET_COMPARTMENTS (
      policy_name   => 'hr_ols_pol',
      user_name     => 'jjones',
      read_comps    => 'FIN',
      write_comps   => 'FIN',
      def_comps     => 'FIN',
      row_comps     => 'FIN');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.12 SA_USER_ADMIN.SET_DEFAULT_LABEL

The `SA_USER_ADMIN.SET_DEFAULT_LABEL` procedure sets the user's initial session label to the one specified.

As long as the row label will still be dominated by the new write label, you can set the session label to:

- Any level equal to or less than his maximum, and equal to or greater than his minimum label

- Include any compartments in the authorized compartment list

- Include any groups in the authorized group list. (Subgroups of authorized groups are implicitly included in the authorized list.)

The row label must be dominated by the new write label that will result from resetting the session label. If this condition is not true, then the `SET_DEFAULT_LABEL` procedure will fail.

For example, suppose the current row label is `S:A,B`, and that you have write access to both compartments. If you attempt to set the new default label to `C:A,B`, then the `SET_LABEL` procedure will fail. This is because the new write label would be `C:A,B`, which does not dominate the current row label.

To successfully reset the session label in this case, you must first lower the row label to a value that will be dominated by the resulting session label.

##### Syntax

    SA_USER_ADMIN.SET_DEFAULT_LABELS (
      policy_name  IN VARCHAR2,
      user_name    IN VARCHAR2,
      def_label    IN VARCHAR2);

##### Parameters

Table E-65 SA_USER_ADMIN.SET_DEFAULT_LABEL Parameters

| Parameter     | Description                                                                                                                                                                                                                                           |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                        |
| `user_name`   | Specifies the user who has been authorized with label components. To find this user, query the `USER_NAME` column of the `ALL_SA_USER_LABELS` view.                                                                                                   |
| `def_label`   | Specifies the label string to be used to initialize the user's default labels. This label may contain any compartments and groups that are authorized for read access. To find existing labels, query the `LABEL` column of the `ALL_SA_LABELS` view. |

##### Example

The following example sets the default label for `hr_ols_pol` for user `jjones`.

    BEGIN
     SA_USER_ADMIN.SET_DEFAULT_LABEL (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jjones',
      def_label         => 'HS');
    END;
    /

**Related Topics**

- SA_SESSION Session Management PL/SQL Package

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.13 SA_USER_ADMIN.SET_GROUPS

The `SA_USER_ADMIN.SET_GROUPS` procedure assigns groups to a user and identifies default values for the user's session label and row label.

All users must have their levels set before their authorized groups can be established. You can find information about a user's level authorization by querying the `DBA_SA_USER_LEVELS` data dictionary view.

##### Syntax

    SA_USER_ADMIN.SET_GROUPS (policy_name IN VARCHAR2,
      user_name        IN VARCHAR2,
      read_groups      IN VARCHAR2,
      write_groups     IN VARCHAR2 DEFAULT NULL,
      def_group        IN VARCHAR2 DEFAULT NULL,
      row_groups       IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-66 SA_USER_ADMIN.SET_GROUPS Parameters

| Parameter      | Description                                                                                                                                                                                                                                            |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`  | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                         |
| `user_name`    | Specifies the user name. This user is a first-time user for group authorization, but the user must already be authorized for levels. To find users who have been authorized for levels, query the `USER_NAME` column of the `DBA_SA_USER_LEVELS` view. |
| `read_groups`  | A comma-delimited list of groups authorized for read, by short name only.<br>To find existing groups, query the `SHORT_NAME` column of the `ALL_SA_GROUPS` view.                                                                                       |
| `write_groups` | A comma-delimited list of groups authorized for write, by short name only. This must be a subset of `read_groups`. If set to `NULL`, then this setting defaults to `read_groups`.                                                                      |
| `def_groups`   | Specifies the default groups, by short name only. This must be a subset of `read_groups`. If set to `NULL`, then this setting defaults to `read_groups`.                                                                                               |
| `row_groups`   | Specifies the row groups, by short name only. This must be a subset of `write_groups` and `def_groups`. If set to `NULL`, then this setting defaults to the groups in `def_groups` that are authorized for write access.                               |

##### Example

The following example defines groups for the `hr_ols_pol` policy.

    BEGIN
     SA_USER_ADMIN.SET_GROUPS (
      policy_name    => 'hr_ols_pol',
      user_name      => 'jjones',
      read_groups    => 'ER_FIN',
      write_groups   => 'ER_FIN',
      def_groups     => 'ER_FIN',
      row_groups     => 'ER_FIN');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.14 SA_USER_ADMIN.SET_LEVELS

The `SA_USER_ADMIN.SET_LEVELS` procedure assigns a user minimum and maximum levels and identifies default values for the user's session label and row label.

##### Syntax

    SA_USER_ADMIN.SET_LEVELS (policy_name IN VARCHAR2,
       user_name        IN VARCHAR2,
       max_level        IN VARCHAR2,
       min_level        IN VARCHAR2 DEFAULT NULL,
       def_level        IN VARCHAR2 DEFAULT NULL,
       row_level        IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-67 SA_USER_ADMIN.SET_LEVELS Parameters

| Parameter     | Description                                                                                                                                                                                            |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                         |
| `user_name`   | Specifies the user name. This user does not need to have any Oracle Label Security authorizations before you run this procedure.                                                                       |
| `max_level`   | The highest level for read and write access, by short name only.<br>To find existing levels, query the `SHORT_NAME` column of the `ALL_SA_LEVELS` view.                                                |
| `min_level`   | The lowest level for write access, by short name only. If set to `NULL`, then the default is the lowest level for the policy.                                                                          |
| `def_level`   | Specifies the default level (equal to or greater than the minimum level, and equal to or less than the maximum level). Use the short name only. If set to `NULL`, then the default is the `max_level`. |
| `row_level`   | Specifies the row level (equal to or greater than the minimum level, and equal to or less than the default level). Use the short name only. If set to `NULL`, then it is set to the `def_level`.       |

##### Example

The following example sets levels for the `hr_ols_pol` policy.

    BEGIN
      SA_USER_ADMIN.SET_LEVELS (
       policy_name     => 'hr_ols_pol',
       user_name       => 'jjones',
       max_level       => 'PUB',
       min_level       => 'HS');
    END;
    /

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.15 SA_USER_ADMIN.SET_PROG_PRIVS

The `SA_USER_ADMIN.SET_PROG_PRIVS` procedure sets policy-specific privileges for program units.

If the `privileges` parameter is `NULL`, then the program unit's privileges for the policy are removed.

To grant privileges to a stored program unit, you must have the `policy``_DBA` role, and the `EXECUTE` permission on the `SA_USER_ADMIN.SA_USER_ADMIN` package. You can use either the `SA_USER_ADMIN` package or Oracle Enterprise Manager to manage Oracle Label Security privileges.

##### Syntax

    SA_USER_ADMIN.SET_PROG_PRIVS (
      policy_name           IN VARCHAR2,
      schema_name           IN VARCHAR2,
      program_unit_name     IN VARCHAR2,
      privileges            IN VARCHAR2);

##### Parameters

Table E-68 SA_USER_ADMIN.SET_PROG_PRIVS Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`       | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                 |
| `schema_name`       | The name of the schema that contains the program unit                                                                                                                                                                                                                                                                                          |
| `program_unit_name` | Specifies the program unit to be granted privileges                                                                                                                                                                                                                                                                                            |
| `privileges`        | A comma-delimited character string of policy-specific privileges. If you set privileges to `NULL`, then the program unit's privileges for the policy are removed.<br>See [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md) for list of available privileges to grant. |

##### Example

The following example gives the `READ` privilege to the `SUM_PURCHASES` function (described in [Example: Trusted Stored Program Unit](administering-and-using-trusted-stored-program-units.md)):

    BEGIN
     SA_USER_ADMIN.SET_PROG_PRIVS (
      policy_name         => 'hr_ols_pol',
      schema_name         => 'HR',
      program_unit_name   => 'sum_purchases',
      privileges          => 'READ');
    END;
    /

When the `check_emp_hours` procedure is then called, it runs with the `READ` privilege as well as the current user's Oracle Label Security privileges. Using this technique, the user can be allowed to find the value of the total employee hours that were logged, without learning what hours any individual employee logged.

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.16 SA_USER_ADMIN.SET_ROW_LABEL

The `SA_USER_ADMIN.SET_ROW_LABEL` procedure sets a user's initial row label to the one specified.

The user can set the row label independently, but only to:

- A level that is less than or equal to the level of the session label, and greater than or equal to the user's minimum level

- Include a subset of the compartments and groups from the session label, for which the user is authorized to have write access

If you try to set the row label to an invalid value, then the operation is disallowed, and the row label value is unchanged.

##### Syntax

    SA_USER_ADMIN.SET_ROW_LABEL (
      policy_name   IN VARCHAR2,
      user_name     IN VARCHAR2,
      row_label     IN VARCHAR2);

##### Parameters

Table E-69 SA_USER_ADMIN.SET_ROW_LABEL Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                           |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                        |
| `user_name`   | Specifies the user name. This user must have the sufficient compartment, group, and level authorizations. To find this user, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS`, `DBA_SA_USER_GROUPS`, and `DBA_SA_USER_LEVELS` views.                                                    |
| `row_label`   | Specifies the label string to be used to initialize the user's row label. The label must contain only those compartments and groups from the default label that are authorized for write access. To find existing compartments and groups, query the `ALL_SA_COMPARTMENTS` and `ALL_SA_GROUPS` views. |

##### Example

The following example sets the row label for the `hr_ols_pol` policy for user `jjones`.

    BEGIN
     SA_USER_ADMIN.SET_ROW_LABEL (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jjones',
      row_label         => 'HS');
    END;
    /

**Related Topics**

- SA_SESSION.SET_ROW_LABEL

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.17 SA_USER_ADMIN.SET_USER_LABELS

The `SA_USER_ADMIN.SET_USER_LABELS` procedure sets the user's levels, compartments, and groups using a set of labels, instead of the individual components.

##### Syntax

    SA_USER_ADMIN.SET_USER_LABELS (
      policy_name      IN VARCHAR2,
      user_name        IN VARCHAR2,
      max_read_label   IN VARCHAR2,
      max_write_label  IN VARCHAR2 DEFAULT NULL,
      min_write_label  IN VARCHAR2 DEFAULT NULL,
      def_label        IN VARCHAR2 DEFAULT NULL,
      row_label        IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table E-70 SA_USER_ADMIN.SET_USER_LABELS Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                   |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`     | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                |
| `user_name`       | Specifies the user name. The user can be an existing database user, a Real Application Security user, or any named user that resides in Oracle Internet Directory. This user does not need any Oracle Label Security authorizations before you run this procedure.                                            |
| `max_read_label`  | Specifies the label string to be used to initialize the user's maximum authorized read label. Composed of the user's maximum level, compartments authorized for read access, and groups authorized for read access.<br>To find information for these settings, query the `DBA_SA_USERS` data dictionary view. |
| `max_write_label` | Specifies the label string to be used to initialize the user's maximum authorized write label. Composed of the user's maximum level, compartments authorized for write access, and groups authorized for write access. If `max_write_label` is not specified, then it is set to `max_read_label`.             |
| `min_write_label` | Specifies the label string to be used to initialize the user's minimum authorized write label. Contains only the level, with no compartments or groups. If `min_write_label` is not specified, then it is set to the lowest defined level for the policy, with no compartments or groups.                     |
| `def_label`       | Specifies the label string to be used to initialize the user's session label, including level, compartments, and groups (a subset of `max_read_label`). If `default_label `is not specified, then it is set to `max_read_label`.                                                                              |
| `row_label`       | Specifies the label string to be used to initialize the program's row label. Includes level, components, and groups: subsets of `max_write_label` and `def_label`. If `row_label` is not specified, then it is set to `def_label`, with only the compartments and groups authorized for write access.         |

##### Examples

The following example sets user labels for the `hr_ols_pol` policy for user `jjones`.

    BEGIN
     SA_USER_ADMIN.SET_USER_LABELS (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jjones',
      max_read_label    => 'HS:FIN',
      max_write_label   => 'HS',
      def_label         => 'HS',
      row_label         => 'HS');
    END;
    /

The following example sets user labels for the `XSOLSPOL1` policy for the Oracle Database Real Application Security user `XSUSER1`. To execute the following example, you must either be an administrative user named `LBACSYS`, be granted the `LBAC_DBA` database role and granted the `EXECUTE` privilege, or be granted the `XSOLSPOL1_DBA` role and granted the `EXECUTE` privilege on the `SA_USER_ADMIN` package.

    EXEC SA_USER_ADMIN.SET_USER_LABELS('XSOLSPOL1', 'XSUSER1',‘MID','MID');

In this specification:

- `XSOLSPOL1` is the name of an existing OLS policy.

- `XSUSER1` is the name of an existing Oracle Database Real Application Security user.

- `MID` is the value of the `max_read_label`.

- `MID` is the value of the `max_write_label`.

**Related Topics**

- SA_USER_ADMIN.SET_PROG_PRIVS

**Parent topic:** SA_USER_ADMIN PL/SQL Package

#### E.7.18 SA_USER_ADMIN.SET_USER_PRIVS

The `SA_USER_ADMIN.SET_USER_PRIVS` procedure sets policy-specific privileges for users.

These privileges do not become effective until the next time the user logs into the database. The new set of privileges replaces any existing privileges. A `NULL` value for the privileges parameter removes the user's privileges for the policy.

To assign policy privileges to users, you must have the `EXECUTE` privilege for the `SA_USER_ADMIN` package, and must have been granted the `policy_``DBA` role.

##### Syntax

    SA_USER_ADMIN.SET_USER_PRIVS (
      policy_name     IN VARCHAR2,
      user_name       IN VARCHAR2,
      privileges      IN VARCHAR2);

##### Parameters

Table E-71 SA_USER_ADMIN.SET_USER_PRIVS Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                                                                                               |
| `user_name`   | The name of the user to be granted privileges. The user can be an existing database user, a Real Application Security user, or any named user that resides in Oracle Internet Directory. This user should already have been authorized for policy levels, compartments, and groups. To find this user, query the `USER_NAME` column of the `DBA_SA_USER_COMPARTMENTS`, `DBA_SA_USER_GROUPS`, and `DBA_SA_USER_LABELS` views. |
| `privileges`  | A character string of policy-specific privileges separated by commas. See [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md) for list of available privileges to grant.                                                                                                                                                                              |

##### Examples

The following example grants user `jgodfrey` full privileges for the `hr_ols_pol` policy settings.

    BEGIN
     SA_USER_ADMIN.SET_USER_PRIVS (
      policy_name       => 'hr_ols_pol',
      user_name         => 'jgodfrey',
      privileges        => 'FULL');
    END;
    /

The following example grants Oracle Database Real Application Security user `XSUSER1` the `READ` privilege for the Oracle Label Security policy `XSOLSPOL1`. To execute the following example, you must either be an administrative user named `LBACSYS`, be granted the `LBAC_DBA` database role and granted the `EXECUTE` privilege, or be granted the `XSOLSPOL1_DBA` role and granted the `EXECUTE` privilege on the `SA_USER_ADMIN` package.

    EXEC SA_USER_ADMIN.SET_USER_PRIVS('XSOLSPOL1', 'XSUSER1','READ');

In this specification:

- `XSOLSPOL1` is the name of an existing OLS policy.

- `XSUSER1` is the name of an existing Oracle Database Real Application Security user.

- `READ` is the privilege to be granted to `XSUSER1` in OLS policy `XSOLSPOL1`.

**Related Topics**

- [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md)

**Parent topic:** SA_USER_ADMIN PL/SQL Package

### E.8 SA_UTL PL/SQL Utility Functions and Procedures

The `SA_UTL` PL/SQL package contains utility functions and procedures that are used in PL/SQL programs.

- About the SA_UTL PL/SQL Package
  The `SA_UTL` PL/SQL package utility functions include returning the values such as user privileges or label information.
- SA_UTL.CHECK_LABEL_CHANGE
  The `SA_UTL.CHECK_LABEL_CHANGE` function checks if the user can change the data label for a policy protected table row.
- SA_UTL.CHECK_READ
  The `SA_UTL.CHECK_READ` function checks if a user can read a policy-protected table row.
- SA_UTL.CHECK_WRITE
  The `SA_UTL.CHECK_WRITE` function to checks if the user can insert, update, or delete data in a policy protected table row.
- SA_UTL.DATA_LABEL
  The `SA_UTL.DATA_LABEL` function returns `TRUE` if the label is a data label.
- SA_UTL.GREATEST_LBOUND
  The `SA_UTL.GREATEST_LBOUND` function returns a label that is the greatest lower bound of the two label arguments.
- SA_UTL.LEAST_UBOUND
  The `SA_UTL.LEAST_UBOUND` function returns a label that is the least upper bound of the label arguments.
- SA_UTL.NUMERIC_LABEL
  The `SA_UTL.NUMERIC_LABEL` function returns the current session label.
- SA_UTL.NUMERIC_ROW_LABEL
  The `SA_UTL.NUMERIC_ROW_LABEL` function returns the current row label. .
- SA_UTL.SET_LABEL
  The `SA_UTL.SET_LABEL` procedure sets the label of the current database session.
- SA_UTL.SET_ROW_LABEL
  The `SA_UTL.SET_ROW_LABEL` procedure sets the row label of the current database session.

**Parent topic:** Oracle Label Security PL/SQL Packages

#### E.8.1 About the SA_UTL PL/SQL Package

The `SA_UTL` PL/SQL package utility functions include returning the values such as user privileges or label information.

These programs return information about the current values of the session security attributes, as numeric label values. They are primarily for use in trusted stored program units. You do not need special privileges to use this package.

**Related Topics**

- [How Setting and Returning Label Information Works](administering-and-using-trusted-stored-program-units.md)

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.2 SA_UTL.CHECK_LABEL_CHANGE

The `SA_UTL.CHECK_LABEL_CHANGE` function checks if the user can change the data label for a policy protected table row.

This function returns `1` if the user can change the data label. It returns `0` if the user cannot change the data label. The input values are the policy name, the current data label, and the new data label.

##### Syntax

    SA_UTL.CHECK_LABEL_CHANGE (
      policy_name     IN VARCHAR2,
      current_label   IN NUMBER,
      new_label       IN NUMBER)
    RETURN NUMBER;

**Note:**

You must have update privileges on the table to write any data into the table.

##### Parameters

Table E-72 SA_UTL.CHECK_LABEL_CHANGE Parameters

| Parameter       | Description                                                                                                                    |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name`   | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `current_label` | The current value of the label. To find existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view.           |
| `new_label`     | The new value for the label                                                                                                    |

##### Example

The following example indicates if users can change data labels in policy-protected rows.

    SET SERVEROUTPUT ON
    BEGIN
      IF SA_UTL.CHECK_LABEL_CHANGE('hr_ols_pol',2000, 2200) = 1
       THEN DBMS_OUTPUT.PUT_LINE('Users can chagne data labels in policy-protected rows.');
      ELSE
       DBMS_OUTPUT.PUT_LINE('Users cannot change data labels in policy-protected rows.');
      END IF;
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.3 SA_UTL.CHECK_READ

The `SA_UTL.CHECK_READ` function checks if a user can read a policy-protected table row.

This function returns `1` if the user can read the table row. It returns `0` if the user cannot read the table row.

**Note:**

The user must have the `SELECT` privilege on the table to read any data from the table.

##### Syntax

    SA_UTL.CHECK_READ (
      policy_name     IN VARCHAR2,
      label           IN NUMBER)
    RETURN NUMBER;

##### Parameters

Table E-73 SA_UTL.CHECK_READ Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `label`       | The label to be checked. To find existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view.                  |

##### Example

The following example indicates if users can read a policy-protected row.

    SET SERVEROUTPUT ON
    BEGIN
      IF SA_UTL.CHECK_READ('hr_ols_pol',2000) = 1
       THEN DBMS_OUTPUT.PUT_LINE('Users can read policy-protected rows.');
      ELSE
       DBMS_OUTPUT.PUT_LINE('Users cannot read policy-protected rows.');
      END IF;
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.4 SA_UTL.CHECK_WRITE

The `SA_UTL.CHECK_WRITE` function to checks if the user can insert, update, or delete data in a policy protected table row.

The user should already have the `UPDATE` privilege on the table to write any data into the table. This function returns `1` if the user can write to the table row. It returns `0` if the user cannot write to the table row. The input values are the policy name and the row data label.

##### Syntax

    SA_UTL.CHECK_WRITE (
      policy_name     IN VARCHAR2,
      label           IN NUMBER)
    RETURN NUMBER;

##### Parameters

Table E-74 SA_UTL.CHECK_WRITE Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |
| `label`       | The label to be checked. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view.       |

##### Example

The following example indicates if users can write to policy-protected rows.

    SET SERVEROUTPUT ON
    BEGIN
      IF SA_UTL.CHECK_WRITE('hr_ols_pol',2000) = 1
       THEN DBMS_OUTPUT.PUT_LINE('Users can write to policy-protected rows.');
      ELSE
       DBMS_OUTPUT.PUT_LINE('Users cannot write to policy-protected rows.');
      END IF;
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.5 SA_UTL.DATA_LABEL

The `SA_UTL.DATA_LABEL` function returns `TRUE` if the label is a data label.

##### Syntax

    SA_UTL.DATA_LABEL(
     label IN NUMBER)
    RETURN BOOLEAN;

##### Parameters

Table E-75 SA_UTL.DATA_LABEL Parameter

| Parameter | Description                                                                                                              |
|:----------|:-------------------------------------------------------------------------------------------------------------------------|
| `label`   | The label to be checked. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |

##### Example

The following example indicates if the label `2000` is a data label.

    SET SERVEROUTPUT ON
    BEGIN
     IF SA_UTL.DATA_LABEL(2000)
      THEN DBMS_OUTPUT.PUT_LINE('Label 2000 is a data label.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('Label 2000 is not a data label.');
     END IF;
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.6 SA_UTL.GREATEST_LBOUND

The `SA_UTL.GREATEST_LBOUND` function returns a label that is the greatest lower bound of the two label arguments.

##### Syntax

    SA_UTL.GREATEST_LBOUND (
     label1 IN NUMBER,
     label2 IN NUMBER)
    RETURN NUMBER;

##### Parameters

Table E-76 SA_UTL.GREATEST_LBOUND Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Examples

The following example compares existing label tags `3110` and `3111`.

    SELECT SA_UTL.GREATEST_LBOUND(3110,3111) FROM DUAL;

    SA_UTL.GREATEST_LBOUND(3110,3111)
    ---------------------------------
                                 3111

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.7 SA_UTL.LEAST_UBOUND

The `SA_UTL.LEAST_UBOUND` function returns a label that is the least upper bound of the label arguments.

##### Syntax

    SA_UTL.LEAST_UBOUND (
     label1 IN NUMBER,
     label2 IN NUMBER)
    RETURN NUMBER;

##### Parameters

Table E-77 SA_UTL.LEAST_UBOUND Parameters

| Parameter | Description                                                                                                               |
|:----------|:--------------------------------------------------------------------------------------------------------------------------|
| `label1`  | The first label to check. To find existing label values, query the `LABEL` and `TAG` columns of the `ALL_SA_LABELS` view. |
| `label2`  | The second label to check                                                                                                 |

##### Example

The following example compares existing labels `3110` and `3111`.

    SELECT SA_UTL.LEAST_UBOUND(3110,3111) FROM DUAL;

    SA_UTL.LEAST_UOUND(3110,3111)
    -----------------------------
                             3110

**See Also:**

[Determination of the Upper and Lower Bounds of Labels](working-with-labeled-data.md). The functions described here are the same as those described in that topic, except that these return a number instead of a character string.

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.8 SA_UTL.NUMERIC_LABEL

The `SA_UTL.NUMERIC_LABEL` function returns the current session label.

This function takes a policy name as the input parameter and returns a `NUMBER` value.

##### Syntax

    SA_UTL.NUMERIC_LABEL (
      policy_name)
    RETURN NUMBER;

##### Parameters

Table E-78 SA_UTL.NUMERIC_LABEL Parameter

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Example

The following example returns a the session numeric label for the user who is currently connected to the database instance.

    SET SERVEROUTPUT ON
    DECLARE
     num_label number;
    BEGIN
     num_label := SA_UTL.NUMERIC_LABEL('hr_ols_pol');
     DBMS_OUTPUT.PUT_LINE('Numeric label: '||num_label);
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.9 SA_UTL.NUMERIC_ROW_LABEL

The `SA_UTL.NUMERIC_ROW_LABEL` function returns the current row label. .

This function takes a policy name as the input parameter and returns a `NUMBER` value

##### Syntax

    SA_UTL.NUMERIC_ROW_LABEL (
      policy_name)
    RETURN NUMBER;

##### Parameters

Table E-79 SA_UTL.NUMERIC_ROW_LABEL Parameters

| Parameter     | Description                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view. |

##### Examples

The following example returns the session numeric row label for the user who is currently connected to the database instance.

    SET SERVEROUTPUT ON
    DECLARE
     num_row number;
    BEGIN
     num_row := SA_UTL.NUMERIC_ROW_LABEL('hr_ols_pol');
     DBMS_OUTPUT.PUT_LINE('Numeric row label: '||num_row);
    END;
    /

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.10 SA_UTL.SET_LABEL

The `SA_UTL.SET_LABEL` procedure sets the label of the current database session.

The session's write label and row label are set to the subset of the label's compartments and groups that are authorized for write access.

##### Syntax

    SA_UTL.SET_LABEL (
     policy_name IN VARCHAR2,
     label       IN LBAC_LABEL);

##### Parameters

Table E-80 SA_UTL.SET_LABEL Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.                                                                                                                                                                                                                   |
| `label`       | The label to set as the session label. To find existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view.<br>You must pass this parameter through as an output of the `TO_LBAC_DATA_LABEL` function, which converts a label in character form to an `LBAC_LABEL` type. (The example in the next section shows how to do this.) |

##### Example

The following example sets the label for the `hr_ols_pol` policy.

    BEGIN
      SA_UTL.SET_LABEL (
        policy_name => 'hr_ols_pol',
        label       => to_lbac_data_label('hr_ols_pol','hs:pii'));
    END;
    /

**Related Topics**

- [How Labeling Functions in Oracle Label Security Policies Works](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures

#### E.8.11 SA_UTL.SET_ROW_LABEL

The `SA_UTL.SET_ROW_LABEL` procedure sets the row label of the current database session.

The compartments and groups in the label must be a subset of compartments and groups in the session label that are authorized for write access.

##### Syntax

    SA_UTL.SET_ROW_LABEL (
     policy_name IN VARCHAR2,
     label       IN BINARY_INTEGER);

##### Parameters

Table E-81 SA_UTL.SET_ROW_LABEL Parameters

| Parameter     | Description                                                                                                                             |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Specifies the policy. To find existing policies, query the `POLICY_NAME` column of the `ALL_SA_POLICIES` data dictionary view.          |
| `label`       | The label to set as the session default row label. To find existing label values, query the `LABEL` column of the `ALL_SA_LABELS` view. |

##### Example

The following example sets the row label for the `hr_ols_pol` policy to `1111`.

    BEGIN
     SA_UTL.SET_ROW_LABEL (
      policy_name         => 'hr_ols_pol',
      label               => 1111);
    END;
    /

**Related Topics**

- SA_SESSION Session Management PL/SQL Package

**Parent topic:** SA_UTL PL/SQL Utility Functions and Procedures
