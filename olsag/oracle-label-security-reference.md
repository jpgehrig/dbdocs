Oracle Label Security provides data dictionary tables, data dictionary views, and an user-created auditing view.

- Oracle Database Data Dictionary Tables
  Oracle Label Security does not label the Oracle data dictionary tables; access is controlled by standard Oracle Database system and object privileges.
- Oracle Label Security Data Dictionary Views
  Oracle Label Security maintains an independent set of data dictionary views, which are exempt from any policy enforcement.
- Oracle Label Security User-Created Auditing View
  The `SA_AUDIT_ADMIN.CREATE_VIEW` procedure can be used to create an audit trail view for a specific policy.

**Parent topic:** [Appendixes](part4.md)

### F.1 Oracle Database Data Dictionary Tables

Oracle Label Security does not label the Oracle data dictionary tables; access is controlled by standard Oracle Database system and object privileges.

**See Also:**

[Oracle Database Reference](../refrn/index.md) for detailed information about all data dictionary tables and views

**Parent topic:** Oracle Label Security Tables and Views

### F.2 Oracle Label Security Data Dictionary Views

Oracle Label Security maintains an independent set of data dictionary views, which are exempt from any policy enforcement.

Access to the data dictionary views is granted by default to the `SELECT_CATALOG_ROLE`, a standard Oracle Database role that lets you examine the Oracle Database data dictionary.

- ALL_SA_AUDIT_OPTIONS View
  The `ALL_SA_AUDIT_OPTIONS` data dictionary view shows for the current user Oracle Label Security auditing options, based on the `SA_AUDIT_ADMIN.AUDIT` procedure settings.
- ALL_SA_COMPARTMENTS
  The `ALL_SA_COMPARTMENTS` data dictionary view shows information for the current user about Oracle Label Security policy compartments, based on the `SA_COMPONENTS.CREATE_COMPARTMENT` procedure settings.
- ALL_SA_DATA_LABELS
  The `ALL_SA_DATA_LABELS` data dictionary view shows for the current user Oracle Label Security policy labels and tags, based on the `SA_LABEL_ADMIN.CREATE_LABEL` procedure settings.
- ALL_SA_GROUPS
  The `ALL_SA_GROUPS` data dictionary shows information about the current user’s Oracle Label Security policy groups, based on the `SA_COMPONENTS.CREATE_GROUP` and `SA_COMPONENTS.ALTER_GROUP_PARENT` procedures.
- ALL_SA_LABELS
  The `ALL_SA_LABELS` data dictionary view shows for the current user information about the tags and types of labels, based on `SA_LABEL_ADMIN.CREATE_LABEL` and `SA_LABEL_ADMIN.ALTER_LABEL`.
- ALL_SA_LEVELS
  The `ALL_SA_LEVELS` data dictionary view shows for the current user information about levels, based on the `SA_COMPONENTS.CREATE_LEVEL` procedure.
- ALL_SA_POLICIES
  The `ALL_SA_POLICIES` data dictionary view shows for the current user information about Oracle Label Security policies, based on the `SA_SYSDBA.CREATE_POLICY` procedure.
- ALL_SA_PROG_PRIVS
  The `ALL_SA_PROG_PRIVS` data dictionary view shows for the current user information about the policy-specific privileges for program units, based on `SA_USER_ADMIN.SET_PROG_PRIVS`.
- ALL_SA_SCHEMA_POLICIES
  The `ALL_SA_SCHEMA_POLICIES` data dictionary view shows for the current user information about policies applied to all tables in the schema, based on `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY`.
- ALL_SA_TABLE_POLICIES
  The `ALL_SA_TABLE_POLICIES` data dictionary view shows for the current user information about a policy added to a database table, based `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` settings.
- ALL_SA_USERS
  The `ALL_SA_USERS` data dictionary view shows for the current user information about Oracle Label Security user privileges, based on `SA_USER_ADMIN.SET_USER_LABELS` and `SA_USER_ADMIN.SET_USER_PRIVS`.
- ALL_SA_USER_LABELS
  The `ALL_SA_USER_LABELS` data dictionary view shows for the current user label-specific information about users, based on the `SA_USER_ADMIN.SET_USER_LABELS` procedure settings.
- ALL_SA_USER_LEVELS
  The `ALL_SA_USER_LEVELS` data dictionary view shows for the current user the minimum and maximum levels assigned to users, based on the `SA_USER_ADMIN.SET_LEVELS` procdure.
- ALL_SA_USER_PRIVS
  The `ALL_SA_USER_PRIVS` data dictionary view shows for the current user policy-specific privileges granted to users, based on the `SA_USER_ADMIN.SET_USER_PRIVS` procedure.
- DBA_SA_AUDIT_OPTIONS
  The `DBA_SA_AUDIT_OPTIONS` data dictionary view data dictionary view shows for the entire database the Oracle Label Security audit options.
- DBA_SA_COMPARTMENTS
  The `ALL_SA_COMPARTMENTS` data dictionary view shows for the entire database information about Oracle Label Security policy compartments.
- DBA_SA_DATA_LABELS
  The `ALL_SA_DATA_LABELS` data dictionary view shows for the entire database the labels and label tags for the specified Oracle Label Security policy.
- DBA_SA_GROUPS
  The `ALL_SA_GROUPS` data dictionary view shows for the entire database information about Oracle Label Security policy groups.
- DBA_SA_GROUP_HIERARCHY
  The `DBA_SA_GROUP_HIERARCHY` data dictionary view shows the hierarchy of groups (that is, parent-child relationships) in a policy.
- DBA_SA_LABELS
  The `DBA_SA_LABELS` data dictionary view shows for the entire database information about the tags and types of labels for a policy.
- DBA_SA_LEVELS
  The `DBA_SA_LEVELS` data dictionary view shows for the entire database information about levels associated with a policy.
- DBA_SA_POLICIES
  The `DBA_SA_POLICIES` data dictionary view shows for the entire database information about Oracle Label Security policies, based on the `SA_SYSDBA.CREATE_POLICY` procedure.
- DBA_SA_PROG_PRIVS
  The `DBA_SA_PROG_PRIVS` data dictionary view shows for the entire database information about the policy-specific privileges for program units.
- DBA_SA_SCHEMA_POLICIES
  The `DBA_SA_SCHEMA_POLICIES` data dictionary view shows for the entire database information about policies that have been applied to all tables in the schema.
- DBA_SA_TABLE_POLICIES
  The `DBA_SA_TABLE_POLICIES` data dictionary view shows for the entire database information about a policy that has been added to a database table.
- DBA_SA_USERS
  The `DBA_SA_USERS` data dictionary view shows for the entire database information about the privileges that Oracle Label Security users have.
- DBA_SA_USER_COMPARTMENTS
  The `DBA_SA_USER_COMPARTMENTS` data dictionary view shows for the entire database the user authorizations, based on the `SA_USER_ADMIN.ADD_COMPARTMENTS` procedure.
- DBA_SA_USER_GROUPS
  The `DBA_SA_USER_GROUPS` data dictionary view shows for the entire database the groups associated with users, based on the `SA_USER_ADMIN.ADD_GROUPS` procedure.
- DBA_SA_USER_LABELS
  The `DBA_SA_USER_LABELS` data dictionary view shows for the entire database label-specific information about users.
- DBA_SA_USER_LEVELS
  The `DBA_SA_USER_LEVELS` data dictionary view shows for the entire database the minimum and maximum levels that have been assigned to users.
- DBA_SA_USER_PRIVS
  The `DBA_SA_USER_PRIVS` data dictionary view shows for the current user the policy-specific privileges that have been granted to users.
- DBA_OLS_STATUS
  The `DBA_OLS_STATUS` data dictionary view shows the configuration status of Oracle Label Security in the database.
- USER_SA_SESSION
  The `USER_SA_SESSION` data dictionary view shows the security attribute values for the current database session.

**Parent topic:** Oracle Label Security Tables and Views

#### F.2.1 ALL_SA_AUDIT_OPTIONS View

The `ALL_SA_AUDIT_OPTIONS` data dictionary view shows for the current user Oracle Label Security auditing options, based on the `SA_AUDIT_ADMIN.AUDIT` procedure settings.

See [SA_AUDIT_ADMIN.AUDIT](oracle-label-security-pl-sql-packages.md).

This view displays whether auditing is configured to generate audit records per session (`BY SESSION`) or per access (`BY ACCESS`) and for successful or unsuccessful operations. Possible values are as follows:

- A dash (`-`) indicates that the audit option is not set.

- The `S` character indicates that the audit option is set `BY SESSION`.

- The `A` character indicates that the audit option is set `BY ACCESS`.

- Each audit option has two possible settings, `WHENEVER SUCCESSFUL` and `WHENEVER NOT SUCCESSFUL`, separated by a slash (`/`).

For example, in the following output, user `jjones` is audited with the `BY ACCESS` audit type for successful actions involving policy-specific privileges. User `rlayton` is audited with the `BY SESSION` audit type: audit records are written for failed attempts to remove policies and for successful attempts at setting user authorizations.

    SELECT * FROM DBA_SA_AUDIT_OPTIONS;

    POLICY_NAME      USER_NAME     APY  REM   SET_  PRV
    -----------      ------------  ---  ----  ----  ---
    HR_OLS_POL       JJONES        -/-   -/-  -/-   A/-
    HR_OLS_POL       RLAYTON       -/-  -/S   S/-   -/-

| Column        | Datatype        | Null       | Description                                                                                               |
|:--------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`  | `NOT NULL` | Name of the Oracle Label Security policy                                                                  |
| `USER_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the user associated with the policy                                                               |
| `APY`         | `VARCHAR2(3)`   | `NULL`     | Audit option; refers to the application of specified Oracle Label Security policies to tables and schemas |
| `REM`         | `VARCHAR2(3)`   | `NULL`     | Audit option; refers to the removal of specified Oracle Label Security policies from tables and schemas   |
| `SET_`        | `VARCHAR2(3)`   | `NULL`     | Audit option; refers to the setting of user authorizations, and user and program privileges               |
| `PRV`         | `VARCHAR2(3)`   | `NULL`     | Audit option; refers to the use of all policy-specific privileges                                         |

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.2 ALL_SA_COMPARTMENTS

The `ALL_SA_COMPARTMENTS` data dictionary view shows information for the current user about Oracle Label Security policy compartments, based on the `SA_COMPONENTS.CREATE_COMPARTMENT` procedure settings.

| Column        | Datatype       | Null       | Description                                 |
|:--------------|:---------------|:-----------|:--------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)` | `NOT NULL` | Name of the Oracle Label Security policy    |
| `COMP_NUM`    | `NUMBER(4)`    | `NOT NULL` | Compartment number in the range of (0-9999) |
| `SHORT_NAME`  | `VARCHAR2(30)` | `NOT NULL` | Short name for the compartment              |
| `LONG_NAME`   | `VARCHAR2(80)` | `NOT NULL` | Long name for the compartment               |

**Related Topics**

- [SA_COMPONENTS.CREATE_COMPARTMENT](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.3 ALL_SA_DATA_LABELS

The `ALL_SA_DATA_LABELS` data dictionary view shows for the current user Oracle Label Security policy labels and tags, based on the `SA_LABEL_ADMIN.CREATE_LABEL` procedure settings.

| Column        | Datatype         | Null       | Description                                                                                       |
|:--------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                          |
| `LABEL`       | `VARCHAR2(4000)` | `NULL`     | Short name of the level, compartment, or group that was specified as the label value              |
| `LABEL_TAG`   | `NUMBER`         | `NULL`     | Integer that represents the sort order of the label, relative to other policy labels (0-99999999) |

**Related Topics**

- [SA_LABEL_ADMIN.CREATE_LABEL](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.4 ALL_SA_GROUPS

The `ALL_SA_GROUPS` data dictionary shows information about the current user’s Oracle Label Security policy groups, based on the `SA_COMPONENTS.CREATE_GROUP` and `SA_COMPONENTS.ALTER_GROUP_PARENT` procedures.

| Column        | Datatype       | Null       | Description                                            |
|:--------------|:---------------|:-----------|:-------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)` | `NOT NULL` | Name of the Oracle Label Security policy               |
| `GROUP_NUM`   | `NUMBER(4)`    | `NOT NULL` | Group number (0-9999)                                  |
| `SHORT_NAME`  | `VARCHAR2(30)` | `NOT NULL` | Short name of the group                                |
| `LONG_NAME`   | `VARCHAR2(80)` | `NOT NULL` | Long name of the group                                 |
| `PARENT_NUM`  | `NUMBER(4)`    | `NULL`     | Numerical ID for the associated parent group           |
| `PARENT_NAME` | `VARCHAR2(30)` | `NULL`     | Name of the group assigned as the parent for the group |

**Related Topics**

- [SA_COMPONENTS.CREATE_GROUP](oracle-label-security-pl-sql-packages.md)
- [SA_COMPONENTS.ALTER_GROUP_PARENT](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.5 ALL_SA_LABELS

The `ALL_SA_LABELS` data dictionary view shows for the current user information about the tags and types of labels, based on `SA_LABEL_ADMIN.CREATE_LABEL` and `SA_LABEL_ADMIN.ALTER_LABEL`.

Access to `ALL_SA_LABELS` is `PUBLIC`. However, only the labels authorized for read access by the session are visible.

| Column        | Datatype         | Null       | Description                                        |
|:--------------|:-----------------|:-----------|:---------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy           |
| `LABEL`       | `VARCHAR2(4000)` | `NOT NULL` | Short name of the level associated with this label |
| `LABEL_TAG`   | `NUMBER(30)`     | `NOT NULL` | Integer tag assigned to the label                  |
| `LABEL_TYPE`  | `VARCHAR2(15)`   | `NULL`     | Type of label                                      |

**Related Topics**

- [SA_LABEL_ADMIN.CREATE_LABEL](oracle-label-security-pl-sql-packages.md)
- [SA_LABEL_ADMIN.ALTER_LABEL](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.6 ALL_SA_LEVELS

The `ALL_SA_LEVELS` data dictionary view shows for the current user information about levels, based on the `SA_COMPONENTS.CREATE_LEVEL` procedure.

| Column        | Datatype       | Null       | Description                              |
|:--------------|:---------------|:-----------|:-----------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)` | `NOT NULL` | Name of the Oracle Label Security policy |
| `LEVEL_NUM`   | `NUMBER(4)`    | `NOT NULL` | Level number (0-9999)                    |
| `SHORT_NAME`  | `VARCHAR2(30)` | `NOT NULL` | Short name for the level                 |
| `LONG_NAME`   | `VARCHAR2(80)` | `NOT NULL` | Long name for the level                  |

**Related Topics**

- [SA_COMPONENTS.CREATE_LEVEL](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.7 ALL_SA_POLICIES

The `ALL_SA_POLICIES` data dictionary view shows for the current user information about Oracle Label Security policies, based on the `SA_SYSDBA.CREATE_POLICY` procedure.

| Column           | Datatype         | Null       | Description                                                                                                                                                                                                   |
|:-----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`    | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                                      |
| `COLUMN_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the column that was added to tables protected by the policy                                                                                                                                           |
| `STATUS`         | `VARCHAR2(8)`    | `NULL`     | Whether the policy has been enabled or disabled                                                                                                                                                               |
| `POLICY_OPTIONS` | `VARCHAR2(4000)` | `NULL`     | Options that were set for this policy<br>See [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the possible enforcement options. |

**Related Topics**

- [SA_SYSDBA.CREATE_POLICY](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.8 ALL_SA_PROG_PRIVS

The `ALL_SA_PROG_PRIVS` data dictionary view shows for the current user information about the policy-specific privileges for program units, based on `SA_USER_ADMIN.SET_PROG_PRIVS`.

| Column               | Datatype         | Null       | Description                                                                                                                                                                                    |
|:---------------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SCHEMA_NAME`        | `VARCHAR2(128)`  | `NOT NULL` | Name of the schema that contains the program unit                                                                                                                                              |
| `PROGRAM_NAME`       | `VARCHAR(128)`   | `NOT NULL` | Program unit that was granted privileges                                                                                                                                                       |
| `POLICY_NAME`        | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                       |
| `PROGRAM_PRIVILEGES` | `VARCHAR2(4000)` | `NULL`     | Policy-specific privileges.<br>See [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md) for list of possible privileges. |

**Related Topics**

- [SA_USER_ADMIN.SET_PROG_PRIVS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.9 ALL_SA_SCHEMA_POLICIES

The `ALL_SA_SCHEMA_POLICIES` data dictionary view shows for the current user information about policies applied to all tables in the schema, based on `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY`.

| Column           | Datatype         | Null       | Description                                                                                                                                                            |
|:-----------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`    | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                               |
| `SCHEMA_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Name of the schema associated with this policy                                                                                                                         |
| `STATUS`         | `VARCHAR2(8)`    | `NULL`     | Whether the policy has been enabled or disabled for the schema (by the `SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY` or `SA_POLICY_ADMIN.DISABLE_SCHEMA_POLICY` for procedure) |
| `SCHEMA_OPTIONS` | `VARCHAR2(4000)` | `NULL`     | Options that have been applied.                                                                                                                                        |

**Related Topics**

- [SA_POLICY_ADMIN.APPLY_SCHEMA_POLICY](oracle-label-security-pl-sql-packages.md)
- [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.10 ALL_SA_TABLE_POLICIES

The `ALL_SA_TABLE_POLICIES` data dictionary view shows for the current user information about a policy added to a database table, based `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` settings.

| Column          | Datatype         | Null       | Description                                                                                                                                                         |
|:----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`   | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                            |
| `SCHEMA_NAME`   | `VARCHAR2(128)`  | `NOT NULL` | Schema that contains the table that the policy protects                                                                                                             |
| `TABLE_NAME`    | `VARCHAR2(128)`  | `NOT NULL` | Table to be protected by the policy                                                                                                                                 |
| `STATUS`        | `VARCHAR2(8)`    | `NULL`     | Whether the policy has been enabled or disabled for the table (by the `SA_POLICY_ADMIN.APPLY_TABLE_POLICY` or `SA_POLICY_ADMIN.DISABLE_TABLE_POLICY` for procedure) |
| `TABLE_OPTIONS` | `VARCHAR2(4000)` | `NULL`     | Policy enforcement options to be used for the table                                                                                                                 |
| `FUNCTION`      | `VARCHAR2(1024)` | `NULL`     | Name of the function to return a label value to use as the default                                                                                                  |
| `PREDICATE`     | `VARCHAR2(256)`  | `NULL`     | Predicate to combine (using `AND` or `OR`) with the label-based predicate for `READ_CONTROL`                                                                        |

**Related Topics**

- [SA_POLICY_ADMIN.APPLY_TABLE_POLICY](oracle-label-security-pl-sql-packages.md)
- [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.11 ALL_SA_USERS

The `ALL_SA_USERS` data dictionary view shows for the current user information about Oracle Label Security user privileges, based on `SA_USER_ADMIN.SET_USER_LABELS` and `SA_USER_ADMIN.SET_USER_PRIVS`.

| Column                | Type             | Null       | Description                                                                                                                                                                                                                                                                              |
|:----------------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USER_NAME`           | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                                                                                                                                                                                                                                                                         |
| `POLICY_NAME`         | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                                                                                                                 |
| `USER_PRIVILEGES`     | `VARCHAR2(4000)` | `NULL`     | Policy-specific privileges granted to the user.                                                                                                                                                                                                                                          |
| `MAX_READ_LABEL`      | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's maximum authorized read label                                                                                                                                                                                                                      |
| `MAX_WRITE_LABEL`     | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's maximum authorized write label                                                                                                                                                                                                                     |
| `MIN_WRITE_LABEL`     | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's minimum authorized write label                                                                                                                                                                                                                     |
| `DEFAULT_READ_LABEL`  | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's session label, including level, compartments, and groups, for read access                                                                                                                                                                          |
| `DEFAULT_WRITE_LABEL` | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's session label, including level, compartments, and groups, for write access                                                                                                                                                                         |
| `DEFAULT_ROW_LABEL`   | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the program's row label; includes level, components, and groups                                                                                                                                                                                               |
| `USER_LABELS`         | `VARCHAR2(4000)` | `NULL`     | Retained solely for backward compatibility and will be removed in the next release.<br>The `USER_LABELS` column is deprecated starting with Oracle Database 18c because it is redundant. The information in this column is displayed in other `ALL_SA_USERS` and `DBA_SA_USERS` columns. |

**Related Topics**

- [SA_USER_ADMIN.SET_USER_LABELS](oracle-label-security-pl-sql-packages.md)
- [SA_USER_ADMIN.SET_USER_PRIVS](oracle-label-security-pl-sql-packages.md)
- [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.12 ALL_SA_USER_LABELS

The `ALL_SA_USER_LABELS` data dictionary view shows for the current user label-specific information about users, based on the `SA_USER_ADMIN.SET_USER_LABELS` procedure settings.

| Column                | Datatype         | Null       | Description                                                                                                                                                                                                                                                                                                  |
|:----------------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USER_NAME`           | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                                                                                                                                                                                                                                                                                             |
| `POLICY_NAME`         | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                                                                                                                                     |
| `LABELS`              | `VARCHAR2(4000)` | `NULL`     | Retained solely for backward compatibility and will be removed in the next release.<br>The `LABELS` column is deprecated starting with Oracle Database 12c release (12.2.0.2) because it is redundant. The information in this column is displayed in `ALL_SA_USER_LABELS` and `DBA_SA_USER_LABELS` columns. |
| `MAX_READ_LABEL`      | `VARCHAR2(4000)` | `NOT NULL` | Label string to initialize the user's maximum authorized read label                                                                                                                                                                                                                                          |
| `MAX_WRITE_LABEL`     | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's maximum authorized write label                                                                                                                                                                                                                                         |
| `MIN_WRITE_LABEL`     | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's minimum authorized write label                                                                                                                                                                                                                                         |
| `DEFAULT_READ_LABEL`  | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's session label, including level, compartments, and groups, for read access                                                                                                                                                                                              |
| `DEFAULT_WRITE_LABEL` | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the user's session label, including level, compartments, and groups, for write access                                                                                                                                                                                             |
| `DEFAULT_ROW_LABEL`   | `VARCHAR2(4000)` | `NULL`     | Label string to initialize the program's row label; includes level, components, and groups                                                                                                                                                                                                                   |

**Related Topics**

- [SA_USER_ADMIN.SET_USER_LABELS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.13 ALL_SA_USER_LEVELS

The `ALL_SA_USER_LEVELS` data dictionary view shows for the current user the minimum and maximum levels assigned to users, based on the `SA_USER_ADMIN.SET_LEVELS` procdure.

It also lists the user's session label and row label default values.

| Column        | Datatype         | Null       | Description                                               |
|:--------------|:-----------------|:-----------|:----------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                  |
| `USER_NAME`   | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                                          |
| `MAX_LEVEL`   | `VARCHAR2(30)`   | `NOT NULL` | Short name of the highest level for read and write access |
| `MIN_LEVEL`   | `VARCHAR2(30)`   | `NOT NULL` | Short name of the lowest level for read and write access  |
| `DEF_LEVEL`   | `VARCHAR2(30)`   | `NOT NULL` | Short name of the default level                           |
| `ROW_LEVEL`   | `VARCHAR2(30)`   | `NOT NULL` | Short name of the row level                               |

**Related Topics**

- [SA_USER_ADMIN.SET_LEVELS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.14 ALL_SA_USER_PRIVS

The `ALL_SA_USER_PRIVS` data dictionary view shows for the current user policy-specific privileges granted to users, based on the `SA_USER_ADMIN.SET_USER_PRIVS` procedure.

| Column            | Datatype         | Null       | Description                                    |
|:------------------|:-----------------|:-----------|:-----------------------------------------------|
| `USER_NAME`       | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                               |
| `POLICY_NAME`     | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy       |
| `USER_PRIVILEGES` | `VARCHAR2(4000)` | `NULL`     | Policy-specific privileges granted to the user |

**Related Topics**

- [SA_USER_ADMIN.SET_USER_PRIVS](oracle-label-security-pl-sql-packages.md)
- [About Granting Privileges to Users and Trusted Program Units for the Policy](creating-an-oracle-label-security-policy.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.15 DBA_SA_AUDIT_OPTIONS

The `DBA_SA_AUDIT_OPTIONS` data dictionary view data dictionary view shows for the entire database the Oracle Label Security audit options.

Its columns are the same as `ALL_SA_AUDIT_OPTIONS`.

**Related Topics**

- ALL_SA_AUDIT_OPTIONS View

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.16 DBA_SA_COMPARTMENTS

The `ALL_SA_COMPARTMENTS` data dictionary view shows for the entire database information about Oracle Label Security policy compartments.

Its columns are the same as `ALL_SA_COMPARTMENTS`.

**Related Topics**

- ALL_SA_COMPARTMENTS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.17 DBA_SA_DATA_LABELS

The `ALL_SA_DATA_LABELS` data dictionary view shows for the entire database the labels and label tags for the specified Oracle Label Security policy.

Its columns are the same as `ALL_SA_DATA_LABELS`.

**Related Topics**

- ALL_SA_DATA_LABELS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.18 DBA_SA_GROUPS

The `ALL_SA_GROUPS` data dictionary view shows for the entire database information about Oracle Label Security policy groups.

Its columns are the same as `ALL_SA_GROUPS`.

**Related Topics**

- ALL_SA_GROUPS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.19 DBA_SA_GROUP_HIERARCHY

The `DBA_SA_GROUP_HIERARCHY` data dictionary view shows the hierarchy of groups (that is, parent-child relationships) in a policy.

| Column            | Type             | Null       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`     | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `HIERARCHY_LEVEL` | `NUMBER`         | `NULL`     | Indicates the level of a particular group in a group hierarchy. A group with no parent group will have `HIERARCHY_LEVEL` `1`. Its child group will have `HIERARCHY_LEVEL` `2` and so on.<br>For example, consider these groups in the following order:<br>1. `G1`, `G4`<br>2. `G2`, `G5`<br>3. `G3`<br>Here, `G1` and `G4` have `HIERARCHY_LEVEL` `1`; `G2` and `G5` have `HIERARCHY_LEVEL` `2`, and `G3` has `HIERARCHY_LEVEL` `3`.<br>The parent-child relationships are:<br>• `G3` is the child group of `G2`, and `G2` is the child group of `G1`.<br>• `G5` is the child group of `G4`. |
| `GROUP_NAME`      | `VARCHAR2(4000)` | `NULL`     | Short name of the group intended to indicate the hierarchy level                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.20 DBA_SA_LABELS

The `DBA_SA_LABELS` data dictionary view shows for the entire database information about the tags and types of labels for a policy.

Its columns are the same as `ALL_SA_LABELS`.

**Related Topics**

- ALL_SA_LABELS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.21 DBA_SA_LEVELS

The `DBA_SA_LEVELS` data dictionary view shows for the entire database information about levels associated with a policy.

Its columns are the same as `ALL_SA_LEVELS`.

**Related Topics**

- ALL_SA_LABELS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.22 DBA_SA_POLICIES

The `DBA_SA_POLICIES` data dictionary view shows for the entire database information about Oracle Label Security policies, based on the `SA_SYSDBA.CREATE_POLICY` procedure.

This view also shows whether the policy has been enabled or disabled and its subscription status.

| Column              | Datatype         | Null       | Description                                                                                                                                                                                                    |
|:--------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`       | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                                                                                       |
| `COLUMN_NAME`       | `VARCHAR2(128)`  | `NOT NULL` | Name of the column that was added to tables protected by the policy                                                                                                                                            |
| `STATUS`            | `VARCHAR2(8)`    | `NULL`     | Whether the policy has been enabled or disabled                                                                                                                                                                |
| `POLICY_OPTIONS`    | `VARCHAR2(4000)` | `NULL`     | Options that were set for this policy.<br>See [Categories of Policy Enforcement Options](implementing-policy-enforcement-options-and-labeling-functions.md) for a listing of the possible enforcement options. |
| `POLICY_SUBSCRIBED` | `VARCHAR2(5)`    | `NULL`     | Indicates the policy's subscription status, based on the `SA_POLICY_ADMIN.POLICY_SUBSCRIBE` or `SA_POLICY_ADMIN.POLICY_UNSUBSCRIBE` procedure                                                                  |

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.23 DBA_SA_PROG_PRIVS

The `DBA_SA_PROG_PRIVS` data dictionary view shows for the entire database information about the policy-specific privileges for program units.

Its columns are the same as `ALL_SA_PROG_PRIVS`.

**Related Topics**

- ALL_SA_PROG_PRIVS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.24 DBA_SA_SCHEMA_POLICIES

The `DBA_SA_SCHEMA_POLICIES` data dictionary view shows for the entire database information about policies that have been applied to all tables in the schema.

Its columns are the same as `ALL_SA_SCHEMA_POLICIES`.

**Related Topics**

- ALL_SA_SCHEMA_POLICIES

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.25 DBA_SA_TABLE_POLICIES

The `DBA_SA_TABLE_POLICIES` data dictionary view shows for the entire database information about a policy that has been added to a database table.

Its columns are the same as `ALL_SA_TABLE_POLICIES`.

**Related Topics**

- ALL_SA_SCHEMA_POLICIES

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.26 DBA_SA_USERS

The `DBA_SA_USERS` data dictionary view shows for the entire database information about the privileges that Oracle Label Security users have.

Its columns are the same as `ALL_SA_USERS`.

**Related Topics**

- ALL_SA_USERS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.27 DBA_SA_USER_COMPARTMENTS

The `DBA_SA_USER_COMPARTMENTS` data dictionary view shows for the entire database the user authorizations, based on the `SA_USER_ADMIN.ADD_COMPARTMENTS` procedure.

This view also indicates whether the compartments are authorized for write and read privileges

| Column        | Datatype         | Null       | Description                                                                                                                                     |
|:--------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                        |
| `USER_NAME`   | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                                                                                                                                |
| `COMP`        | `VARCHAR2(30)`   | `NOT NULL` | Short name of compartments that were added                                                                                                      |
| `RW_ACCESS`   | `VARCHAR2(5)`    | `NULL`     | Access mode. Possible values are:<br>• `SA_UTL.READ_ONLY` indicates no write access<br>• `SA_UTL.READ_WRITE` indicates that write is authorized |
| `DEF_COMP`    | `VARCHAR2(1)`    | `NOT NULL` | Whether the compartments are in the default compartments                                                                                        |
| `ROW_COMP`    | `VARCHAR2(1)`    | `NOT NULL` | whether the compartments are in the row label                                                                                                   |

**Related Topics**

- [SA_USER_ADMIN.ADD_COMPARTMENTS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.28 DBA_SA_USER_GROUPS

The `DBA_SA_USER_GROUPS` data dictionary view shows for the entire database the groups associated with users, based on the `SA_USER_ADMIN.ADD_GROUPS` procedure.

| Column        | Datatype         | Null       | Description                                                                                                                                   |
|:--------------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                                                                                      |
| `USER_NAME`   | `VARCHAR2(1024)` | `NOT NULL` | Name of the user                                                                                                                              |
| `GRP`         | `VARCHAR2(30)`   | `NOT NULL` | Short name of groups that were added                                                                                                          |
| `RW_ACCESS`   | `VARCHAR2(5)`    | `NULL`     | Access mode. Possible values are:<br>• `SA_UTL.READ_ONLY` indicates read-only access<br>• `SA_UTL.READ_WRITE` indicates read and write access |
| `DEF_GROUP`   | `VARCHAR2(1)`    | `NOT NULL` | Whether the group is in a default group                                                                                                       |
| `ROW_GROUP`   | `VARCHAR2(1)`    | `NOT NULL` | Whether the group is in a label                                                                                                               |

**Related Topics**

- [SA_USER_ADMIN.ADD_GROUPS](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.29 DBA_SA_USER_LABELS

The `DBA_SA_USER_LABELS` data dictionary view shows for the entire database label-specific information about users.

Its columns are the same as `ALL_SA_USER_LABELS`.

**Related Topics**

- ALL_SA_USER_LABELS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.30 DBA_SA_USER_LEVELS

The `DBA_SA_USER_LEVELS` data dictionary view shows for the entire database the minimum and maximum levels that have been assigned to users.

This view also shows the default values for the user's session label and row label.

Its columns are the same as `ALL_SA_USER_LEVELS`.

**Related Topics**

- ALL_SA_USER_LEVELS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.31 DBA_SA_USER_PRIVS

The `DBA_SA_USER_PRIVS` data dictionary view shows for the current user the policy-specific privileges that have been granted to users.

Its columns are the same as `ALL_SA_USER_PRIVS`.

**Related Topics**

- ALL_SA_USER_PRIVS

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.32 DBA_OLS_STATUS

The `DBA_OLS_STATUS` data dictionary view shows the configuration status of Oracle Label Security in the database.

| Column        | Datatype         | Null   | Description                                                                                                                                                                                                                                                                                     |
|:--------------|:-----------------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`        | `VARCHAR2(20)`   | `NULL` | Name of the status. Values are:<br>• `OLS_CONFIGURE_STATUS`<br>• `OLS_DIRECTORY_STATUS`<br>• `OLS_ENABLE_STATUS`                                                                                                                                                                                |
| `STATUS`      | `VARCHAR2(5)`    | `NULL` | Indicates the status of the feature mentioned in the corresponding name column. For example, a `TRUE` value for the `OLS_CONFIGURE_STATUS` status says that Oracle Label Security has been configured.                                                                                          |
| `DESCRIPTION` | `VARCHAR2(4000)` | `NULL` | Description of the status:<br>• `OLS_CONFIGURE_STATUS`:Determines if Oracle Label Security is configured.<br>• `OLS_DIRECTORY_STATUS`: Determines if Oracle Internet Directory is enabled with Oracle Label Security.<br>• `OLS_ENABLE_STATUS`: Determines if Oracle Label Security is enabled. |

**Parent topic:** Oracle Label Security Data Dictionary Views

#### F.2.33 USER_SA_SESSION

The `USER_SA_SESSION` data dictionary view shows the security attribute values for the current database session.

Access to this view is `PUBLIC`.

| Column            | Datatype         | Null       | Description                                                             |
|:------------------|:-----------------|:-----------|:------------------------------------------------------------------------|
| `POLICY_NAME`     | `VARCHAR2(30)`   | `NOT NULL` | Name of the Oracle Label Security policy                                |
| `SA_USER_NAME`    | `VARCHAR2(4000)` | `NULL`     | Name of the current session user                                        |
| `PRIVS`           | `VARCHAR2(4000)` | `NULL`     | Current session privileges                                              |
| `MAX_READ_LABEL`  | `VARCHAR2(4000)` | `NULL`     | Label string that initialized the user's maximum authorized read label  |
| `MAX_WRITE_LABEL` | `VARCHAR2(4000)` | `NULL`     | Label string that initialized the user's maximum authorized write label |
| `MIN_LEVEL`       | `VARCHAR2(4000)` | `NULL`     | Minimum Oracle Label Security level authorized for the session          |
| `LABEL`           | `VARCHAR2(4000)` | `NULL`     | Label for the current database session                                  |
| `COMP_WRITE`      | `VARCHAR2(4000)` | `NULL`     | Compartments to which the user is authorized to write                   |
| `GROUP_WRITE`     | `VARCHAR2(4000)` | `NULL`     | Groups to which the user is authorized to write                         |
| `ROW_LABEL`       | `VARCHAR2(4000)` | `NULL`     | Row label that is associated with the policy for the current session    |

**Parent topic:** Oracle Label Security Data Dictionary Views

### F.3 Oracle Label Security User-Created Auditing View

The `SA_AUDIT_ADMIN.CREATE_VIEW` procedure can be used to create an audit trail view for a specific policy.

By default, this view is named `DBA_``policyname_``AUDIT_TRAIL`.

| Column               | Datatype                       | Null       | Description                                                                                                                                                                                                                                                                                                                             |
|:---------------------|:-------------------------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`           | `VARCHAR2(128)`                | `NULL`     | Name of the user whose actions were audited                                                                                                                                                                                                                                                                                             |
| `USERHOST`           | `VARCHAR2(128)`                | `NULL`     | Client host machine name                                                                                                                                                                                                                                                                                                                |
| `TERMINAL`           | `VARCHAR2(255)`                | `NULL`     | Identifier of the user's terminal                                                                                                                                                                                                                                                                                                       |
| `TIMESTAMP`          | `DATE`                         | `NULL`     | Date and time of the creation of the audit trail entry (date and time of user login for entries created by `AUDIT SESSION`) in the local database session time zone                                                                                                                                                                     |
| `OWNER`              | `VARCHAR2(128)`                | `NULL`     | Creator of the object affected by the action                                                                                                                                                                                                                                                                                            |
| `OBJ_NAME`           | `VARCHAR2(128)`                | `NULL`     | Name of the object affected by the action                                                                                                                                                                                                                                                                                               |
| `ACTION`             | `NUMBER`                       | `NOT NULL` | Numeric action type code. The corresponding name of the action type is in the `ACTION_NAME` column.                                                                                                                                                                                                                                     |
| `ACTION_NAME`        | `VARCHAR2(47)`                 | `NULL`     | Name of the action type corresponding to the numeric code in the `ACTION` column                                                                                                                                                                                                                                                        |
| `COMMENT_TEXT`       | `VARCHAR2(4000)`               | `NULL`     | Text comment on the audit trail entry, providing more information about the statement audited<br>Also indicates how the user was authenticated. The method can be one of the following:<br>• `DATABASE`: Authentication was done by password<br>• `NETWORK`: Authentication was done by Oracle Net Services or by strong authentication |
| `SESSIONID`          | `NUMBER`                       | `NOT NULL` | Numeric ID for each Oracle session                                                                                                                                                                                                                                                                                                      |
| `ENTRYID`            | `NUMBER`                       | `NOT NULL` | Numeric ID for each audit trail entry in the session                                                                                                                                                                                                                                                                                    |
| `STATEMENTID`        | `NUMBER`                       | `NOT NULL` | Numeric ID for each statement run                                                                                                                                                                                                                                                                                                       |
| `RETURNCODE`         | `NUMBER`                       | `NOT NULL` | Oracle error code generated by the action. Some useful values:<br>• `0`: Action succeeded<br>• `2004`: Security violation                                                                                                                                                                                                               |
| `EXTENDED_TIMESTAMP` | `TIMESTAMP (6) WITH TIME ZONE` | `NULL`     | Timestamp of the creation of the audit trail entry (timestamp of user login for entries created by `AUDIT SESSION`) in UTC (Coordinated Universal Time) time zone                                                                                                                                                                       |
| `OLS_COL`            | `VARCHAR2(4000)`               | `NULL`     | Name of the column that was added to the tables that Oracle Label Security protects                                                                                                                                                                                                                                                     |

**Related Topics**

- [SA_AUDIT_ADMIN.CREATE_VIEW](oracle-label-security-pl-sql-packages.md)

**Parent topic:** Oracle Label Security Tables and Views
