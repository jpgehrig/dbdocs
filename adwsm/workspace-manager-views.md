Workspace Manager creates and maintains static data dictionary views to hold information about such things as version-enabled tables, workspaces, savepoints, users, privileges, locks, and conflicts.

These views are read-only to users. You can use the information in these views to help administer the Workspace Manager environment and diagnose problems.

There are also views created for each version-enabled table, as follows:

- Conflict view, each having a name in the form \<table_name\>\_CONF. (See xxx_CONF Views.)

- Difference view, each having a name in the form \<table_name\>\_DIFF. (See xxx_DIFF Views.)

- History view (if history tracking is enabled), each having a name in the form \<table_name\>\_HIST. (See xxx_HIST Views.)

- Lock view, each having a name in the form \<table_name\>\_LOCK. (See xxx_LOCK Views.)

- Multiworkspace view, each having a name in the form \<table_name\>\_MW. (See xxx_MW Views.)

**Note:**

When an ALL\_xxx or USER\_xxx view is queried from a procedure, the results returned are based on whether the procedure has definer's rights or the rights of the database user whose privileges are currently active.

### CDB\_xxx Views

For every DBA\_xxx view, a CDB\_xxx view is defined. In the root of a multitenant container database (CDB), CDB\_xxx views can be used to obtain information about tables, tablespaces, users, privileges, parameters, and so on contained in the root and in pluggable databases (PDBs).

CDB\_xxx views are container data objects. When a user connected to the root queries a CDB\_xxx view, the query results will depend on the CONTAINER_DATA attribute for users for the view. The CONTAINER_DATA clause of the SQL ALTER USER statement is used to set and modify users' CONTAINER_DATA attribute.

The CDB\_xxx views are owned by SYS, regardless of which user owns the underlying DBA\_xxx view.

By default, a user connected to the root will only see data pertaining to the root.

In a PDB, the CDB\_xxx views only show objects visible through a corresponding DBA\_xxx view.

In addition to all the columns found in a given DBA\_xxx view, the corresponding CDB\_xxx view also contains the CON_ID column, which identifies a container whose data a given CDB\_\* row represents. In a non-CDB, the value of a CON_ID column will be 0.

CDB views can return data from different containers in a CDB when queried from the root container. These objects will implicitly convert data to the character set of the root container (AL32UTF8) and then return the result to the user. Some character sets may have character expansion (more bytes needed to represent a character) when converted to AL32UTF8, so there may be data truncation if the view column width is not able to accommodate data from a given PDB.

Data returned by these views depends on whether a given PDB is open at the time the query is issued. In particular, in an Oracle RAC environment, data returned by these view may vary according to the instance to which a session is connected.

- ALL_MP_GRAPH_WORKSPACES
- ALL_MP_PARENT_WORKSPACES
- ALL_REMOVED_WORKSPACES
- ALL_VERSION_HVIEW
- ALL_WM_CONS_COLUMNS
- ALL_WM_CONSTRAINT_VIOLATIONS
- ALL_WM_CONSTRAINTS
- ALL_WM_IND_COLUMNS
- ALL_WM_IND_EXPRESSIONS
- ALL_WM_LOCKED_TABLES
- ALL_WM_MODIFIED_TABLES
- ALL_WM_POLICIES
- ALL_WM_RIC_INFO
- ALL_WM_TAB_TRIGGERS
- ALL_WM_VERSIONED_TABLES
- ALL_WM_VT_ERRORS
- ALL_WORKSPACE_PRIVS
- ALL_WORKSPACE_SAVEPOINTS
- ALL_WORKSPACES
- DBA_REMOVED_WORKSPACES
- DBA_WM_SYS_PRIVS
- DBA_WM_VERSIONED_TABLES
- DBA_WM_VT_ERRORS
- DBA_WORKSPACE_PRIVS
- DBA_WORKSPACE_SAVEPOINTS
- DBA_WORKSPACE_SESSIONS
- DBA_WORKSPACES
- ROLE_WM_PRIVS
- USER_MP_GRAPH_WORKSPACES
- USER_MP_PARENT_WORKSPACES
- USER_REMOVED_WORKSPACES
- USER_WM_CONS_COLUMNS
- USER_WM_CONSTRAINTS
- USER_WM_IND_COLUMNS
- USER_WM_IND_EXPRESSIONS
- USER_WM_LOCKED_TABLES
- USER_WM_MODIFIED_TABLES
- USER_WM_POLICIES
- USER_WM_PRIVS
- USER_WM_RIC_INFO
- USER_WM_TAB_TRIGGERS
- USER_WM_VERSIONED_TABLES
- USER_WM_VT_ERRORS
- USER_WORKSPACE_PRIVS
- USER_WORKSPACE_SAVEPOINTS
- USER_WORKSPACES
- WM_COMPRESS_BATCH_SIZES
- WM_COMPRESSIBLE_TABLES
- WM_EVENTS_INFO
- WM_INSTALLATION
- xxx_CONF Views
- xxx_DIFF Views
- xxx_HIST Views
- xxx_LOCK Views
- xxx_MW Views

**Parent topic:** [Reference Information](workspace-manager-reference.md)

### 5.1 ALL_MP_GRAPH_WORKSPACES

ALL_MP_GRAPH_WORKSPACES contains information about multiparent graph workspaces (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)) for which the leaf workspace can be accessed by the current user.

Related View

- USER_MP_GRAPH_WORKSPACES contains information about multiparent graph workspaces for which the leaf workspace is owned by the current user.

| Column              | Datatype        | Null?      | Description                                                                                                                                                                                                                                                                 |
|:--------------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MP_LEAF_WORKSPACE` | `VARCHAR2(128)` | `NOT NULL` | Name of the multiparent leaf workspace.                                                                                                                                                                                                                                     |
| `GRAPH_WORKSPACE`   | `VARCHAR2(128)` | `NOT NULL` | Name of the multiparent graph workspace.                                                                                                                                                                                                                                    |
| `GRAPH_FLAG`        | `VARCHAR2(22)`  |            | `L` if the multiparent graph workspace is the leaf workspace in the multiparent graph; `I` if the multiparent graph workspace is an intermediate workspace in the multiparent graph; `R` if the multiparent graph workspace is the root workspace in the multiparent graph. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.2 ALL_MP_PARENT_WORKSPACES

ALL_MP_PARENT_WORKSPACES contains information about parent workspaces of multiparent workspaces (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)) that the current user can access.

Related View

- USER_MP_PARENT_WORKSPACES contains information about parent workspaces of multiparent workspaces that the current user owns.

| Column              | Datatype                   | Null?      | Description                                                                                                                                                    |
|:--------------------|:---------------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MP_LEAF_WORKSPACE` | `VARCHAR2(128)`            | `NOT NULL` | Name of the multiparent leaf workspace.                                                                                                                        |
| `PARENT_WORKSPACE`  | `VARCHAR2(128)`            | `NOT NULL` | Name of the parent workspace.                                                                                                                                  |
| `CREATOR`           | `VARCHAR2(128)`            |            | Name of the user that made `PARENT_WORKSPACE` a parent workspace of `MP_LEAF_WORKSPACE`.                                                                       |
| `CREATETIME`        | `TIMESTAMP WITH TIME ZONE` |            | Date and time when `PARENT_WORKSPACE` became a parent workspace of `MP_LEAF_WORKSPACE`.                                                                        |
| `ISREFRESHED`       | `VARCHAR2(3)`              |            | `YES` if the multiparent leaf workspace is a continually refreshed workspace; `NO` if the multiparent leaf workspace is not a continually refreshed workspace. |
| `PARENT_FLAG`       | `VARCHAR2(17)`             |            | `DP` if `PARENT_WORKSPACE` is the default parent of `MP_LEAF_WORKSPACE`; `MP` if `PARENT_WORKSPACE` was added as a parent of `MP_LEAF_WORKSPACE`.              |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.3 ALL_REMOVED_WORKSPACES

ALL_REMOVED_WORKSPACES contains information about workspaces, that the current user has access to, that have been removed during a [RemoveWorkspace](DBMS_WM-reference.md) operation or a [MergeWorkspace](DBMS_WM-reference.md) operation in which the `remove_workspace` parameter value was `true`, and while the value of the Workspace Manager system parameter `KEEP_REMOVED_WORKSPACES_INFO` was `ON`. (This system parameter is described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).)

Related Views

- USER_REMOVED_WORKSPACES contains information about workspaces, that the current user owns, that have been removed during a [RemoveWorkspace](DBMS_WM-reference.md) operation or a [MergeWorkspace](DBMS_WM-reference.md) operation in which the `remove_workspace` parameter value was `true`, and while the value of the Workspace Manager system parameter `KEEP_REMOVED_WORKSPACES_INFO` was `ON`.

- DBA_REMOVED_WORKSPACES contains information about workspaces that have been removed during a [RemoveWorkspace](DBMS_WM-reference.md) operation or a [MergeWorkspace](DBMS_WM-reference.md) operation in which the `remove_workspace` parameter value was `true`, and while the value of the Workspace Manager system parameter `KEEP_REMOVED_WORKSPACES_INFO` was `ON`.

| Column                  | Datatype                   | Null?      | Description                                                                                                                                                                                                            |
|:------------------------|:---------------------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`                 | `VARCHAR2(128)`            |            | User name of the owner of the removed workspace.                                                                                                                                                                       |
| `WORKSPACE_NAME`        | `VARCHAR2(128)`            |            | Name of the removed workspace.                                                                                                                                                                                         |
| `WORKSPACE_ID`          | `NUMBER(38)`               | `NOT NULL` | ID of the removed workspace.                                                                                                                                                                                           |
| `PARENT_WORKSPACE_NAME` | `VARCHAR2(128)`            |            | Name of the parent workspace of the removed workspace.                                                                                                                                                                 |
| `PARENT_WORKSPACE_ID`   | `NUMBER(38)`               |            | ID of the parent workspace of the removed workspace.                                                                                                                                                                   |
| `CREATETIME`            | `TIMESTAMP WITH TIME ZONE` |            | Date and time when the removed workspace was created.                                                                                                                                                                  |
| `RETIRETIME`            | `TIMESTAMP WITH TIME ZONE` |            | Date and time when the removed workspace was removed.                                                                                                                                                                  |
| `DESCRIPTION`           | `VARCHAR2(1000)`           |            | Description of the removed workspace.                                                                                                                                                                                  |
| `MP_ROOT_WORKSPACE_ID`  | `NUMBER(38)`               |            | ID of the root workspace of the multiparent graph; null if the workspace is not part of a multiparent graph. (Multiparent workspaces are explained in [Multiparent Workspaces](introduction-to-workspace-manager.md).) |
| `CONTINUALLY_REFRESHED` | `VARCHAR2(3)`              |            | `YES` if the workspace is continually refreshed (see the description of the `isrefreshed` parameter of the [CreateWorkspace](DBMS_WM-reference.md) procedure); `NO` if the workspace is not continually refreshed.     |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.4 ALL_VERSION_HVIEW

`ALL_VERSION_HVIEW` contains information about the version hierarchy. It is used by Workspace Manager to perform queries against the xxx\_HIST views (described in xxx_HIST Views).

| Column           | Datatype        | Null?      | Description                                                                             |
|:-----------------|:----------------|:-----------|:----------------------------------------------------------------------------------------|
| `VERSION`        | `NUMBER(38)`    | `NOT NULL` | Version number of the workspace identified in the `WORKSPACE` column.                   |
| `PARENT_VERSION` | `NUMBER(38)`    |            | Version number of the parent version of the version identified in the `VERSION` column. |
| `WORKSPACE`      | `VARCHAR2(128)` |            | Name of the workspace associated with the version number in the `VERSION` column.       |
| `WORKSPACE_ID`   | `NUMBER`        |            | ID of the workspace associated with the version number in the `VERSION` column.         |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.5 ALL_WM_CONS_COLUMNS

ALL_WM_CONS_COLUMNS contains information about columns in unique constraints on version-enabled tables on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `UPDATE`, or `DELETE`.

Related View

- USER_WM_CONS_COLUMNS contains information about columns in unique constraints on version-enabled tables that the current user owns.

| Column            | Datatype         | Null? | Description                                                           |
|:------------------|:-----------------|:------|:----------------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)`  |       | User name of the constraint owner.                                    |
| `CONSTRAINT_NAME` | `VARCHAR2(128)`  |       | Name of the constraint.                                               |
| `TABLE_NAME`      | `VARCHAR2(128)`  |       | Name of the version-enabled table on which the constraint is defined. |
| `COLUMN_NAME`     | `VARCHAR2(4000)` |       | Column in the constraint definition.                                  |
| `POSITION`        | `NUMBER`         |       | Position of the column in the constraint.                             |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.6 ALL_WM_CONSTRAINT_VIOLATIONS

ALL_WM_CONSTRAINT_VIOLATIONS contains information related to unique, foreign key, and check constraint violation errors raised while executing the [MergeWorkspace](DBMS_WM-reference.md), [MergeTable](DBMS_WM-reference.md), [RefreshWorkspace](DBMS_WM-reference.md), [RefreshTable](DBMS_WM-reference.md), [CommitDDL](DBMS_WM-reference.md), [AddAsParentWorkspace](DBMS_WM-reference.md), [RemoveAsParentWorkspace](DBMS_WM-reference.md), and [PurgeTable](DBMS_WM-reference.md) procedures.

The view is only populated within a session after executing one of the these procedures and it fails due to a constraint violation. The view data is cleared any time one of these procedures is executed and a constraint check is successfully performed or the session disconnects.

| Column        | Datatype        | Null?      | Description                                                                                 |
|:--------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------|
| `VIOLATION#`  | `NUMBER`        | `NOT NULL` | An identifier representing the violation number.                                            |
| `TABLE_NAME1` | `VARCHAR2(128)` |            | Name of the first table involved in the constraint violation.                               |
| `PREDICATE1`  | `CLOB`          |            | A primary key predicate that can be used to identify the violating row of the first table.  |
| `VERSION1`    | `NUMBER`        |            | The version of the row within the first table involved in the constraint violation.         |
| `TABLE_NAME2` | `VARCHAR2(128)` |            | Name of the second table involved in the constraint violation.                              |
| `PREDICATE2`  | `CLOB`          |            | A primary key predicate that can be used to identify the violating row of the second table. |
| `VERSION2`    | `NUMBER`        |            | The version of the row within the second table involved in the constraint violation.        |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.7 ALL_WM_CONSTRAINTS

ALL_WM_CONSTRAINTS contains information about constraints on version-enabled tables on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `UPDATE`, or `DELETE`. It provides information about the following kinds of constraints: `UNIQUE` constraint, unique index, `PRIMARY KEY` constraints, and `CHECK` constraints.

Related View

- USER_WM_CONSTRAINTS contains information about constraints on version-enabled tables that the current user owns.

| Column             | Datatype        | Null?      | Description                                                                                                                                                                                                                                                                                                                            |
|:-------------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER `           | `VARCHAR2(128)` | `NOT NULL` | User name of the constraint owner. (Same as the owner of `TABLE_NAME`.)                                                                                                                                                                                                                                                                |
| `CONSTRAINT_NAME`  | `VARCHAR2(128)` |            | Name of the constraint.                                                                                                                                                                                                                                                                                                                |
| `CONSTRAINT_TYPE`  | `VARCHAR2(2)`   |            | One of the following values: `P` = primary constraint, `PU` = primary constraint enforced using unique index, `PN` = primary constraint enforced using non-unique index, `U` = unique constraint, `UU` = unique constraint enforced using unique index, `UN` = unique constraint enforced using non-unique index, `UI` = unique index. |
| `TABLE_NAME`       | `VARCHAR2(128)` |            | Name of the table on which the constraint is defined.                                                                                                                                                                                                                                                                                  |
| `SEARCH_CONDITION` | `CLOB`          |            | Condition for checking the constraint.                                                                                                                                                                                                                                                                                                 |
| `STATUS`           | `VARCHAR2(8)`   |            | `ENABLED` if the constraint is enabled; `DISABLED` if the constraint is disabled.                                                                                                                                                                                                                                                      |
| `INDEX_OWNER`      | `VARCHAR2(128)` |            | Owner of the index used for enforcing the constraint.                                                                                                                                                                                                                                                                                  |
| `INDEX_NAME`       | `VARCHAR2(128)` |            | Name of the index used for enforcing the constraint.                                                                                                                                                                                                                                                                                   |
| `INDEX_TYPE`       | `VARCHAR2(26)`  |            | `NORMAL` if the index is not a function-based index; `FUNCTION-BASED NORMAL` for a function-based index.                                                                                                                                                                                                                               |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.8 ALL_WM_IND_COLUMNS

ALL_WM_IND_COLUMNS contains information about indexes used for enforcing unique constraints on version-enabled tables on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `UPDATE`, or `DELETE`.

Related View

- USER_WM_IND_COLUMNS contains information about indexes used for enforcing unique constraints on version-enabled tables that the current user owns.

| Column            | Datatype         | Null? | Description                                                                                                                 |
|:------------------|:-----------------|:------|:----------------------------------------------------------------------------------------------------------------------------|
| `INDEX_OWNER`     | `VARCHAR2(128)`  |       | User name of the index owner.                                                                                               |
| `INDEX_NAME`      | `VARCHAR2(128)`  |       | Name of the index.                                                                                                          |
| `OWNER`           | `VARCHAR2(128)`  |       | User name of the owner of the version-enabled table on which the index is defined.                                          |
| `TABLE_NAME`      | `VARCHAR2(128)`  |       | Name of the version-enabled table on which the index is defined.                                                            |
| `COLUMN_NAME`     | `VARCHAR2(4000)` |       | Column on which the index is defined.                                                                                       |
| `COLUMN_POSITION` | `NUMBER`         |       | Position of the column in the index.                                                                                        |
| `COLUMN_LENGTH`   | `NUMBER`         |       | Length of the column.                                                                                                       |
| `DESCEND`         | `VARCHAR2(4)`    |       | `ASC` if the column data in the index is in ascending order; `DESC` if the column data in the index is in descending order. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.9 ALL_WM_IND_EXPRESSIONS

ALL_WM_IND_EXPRESSIONS contains information about functional expressions on functional unique indexes on version-enabled tables on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `UPDATE`, or `DELETE`.

Related View

- USER_WM_IND_EXPRESSIONS contains information about functional expressions on functional unique indexes on version-enabled tables that the current user owns.

| Column              | Datatype        | Null? | Description                                                                        |
|:--------------------|:----------------|:------|:-----------------------------------------------------------------------------------|
| `INDEX_OWNER`       | `VARCHAR2(128)` |       | User name of the index owner.                                                      |
| `INDEX_NAME`        | `VARCHAR2(128)` |       | Name of the index.                                                                 |
| `OWNER`             | `VARCHAR2(128)` |       | User name of the owner of the version-enabled table on which the index is defined. |
| `TABLE_NAME`        | `VARCHAR2(128)` |       | Name of the version-enabled table on which the index is defined.                   |
| `COLUMN_EXPRESSION` | `LONG`          |       | Test of the functional expression on which the index is defined.                   |
| `COLUMN_POSITION`   | `NUMBER`        |       | Position of the expression in the index.                                           |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.10 ALL_WM_LOCKED_TABLES

ALL_WM_LOCKED_TABLES contains information about Workspace Manager locks on rows in version-enabled tables that the current user can access.

Related View

- USER_WM_LOCKED_TABLES contains information about Workspace Manager locks on rows in version-enabled tables that the current user owns.

  | Column          | Datatype         | Null? | Description                             |
  |:----------------|:-----------------|:------|:----------------------------------------|
  | `TABLE_OWNER `  | `VARCHAR2(128)`  |       | User name of the table owner.           |
  | `TABLE_NAME`    | `VARCHAR2(128)`  |       | Name of the table.                      |
  | `LOCK_MODE`     | `VARCHAR2(19)`   |       | Type of lock: `EXCLUSIVE` or `SHARED`.  |
  | `LOCK_OWNER`    | `VARCHAR2(4000)` |       | User name of the owner of the lock.     |
  | `LOCKING_STATE` | `VARCHAR2(4000)` |       | Workspace in which the lock was placed. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.11 ALL_WM_MODIFIED_TABLES

ALL_WM_MODIFIED_TABLES contains information about all version-enabled tables that have been modified and on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `DELETE`, `UPDATE`.

Related View

- USER_WM_MODIFIED_TABLES contains information about version-enabled tables that have been modified and that the current user owns.

| Column        | Datatype        | Null?      | Description                                                                                                                         |
|:--------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------|
| `TABLE_NAME ` | `VARCHAR2(257)` |            | Name of a version-enabled table.                                                                                                    |
| `WORKSPACE `  | `VARCHAR2(128)` | `NOT NULL` | Workspace in which the modification occurred.                                                                                       |
| `SAVEPOINT `  | `VARCHAR2(128)` |            | Name of the savepoint associated with the most recent modification, or `LATEST` if a savepoint does not yet exist is the workspace. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.12 ALL_WM_POLICIES

ALL_WM_POLICIES contains information about Oracle Virtual Private Database (VPD) security policies defined on any version-enabled table or related view accessible to the current user. Its columns are the same as those in the ALL_POLICIES view, described in [Oracle Database Reference](../refrn/ALL_POLICIES.md).

Workspace Manager uses this information to provide VPD support, which is described in [Virtual Private Database Considerations](introduction-to-workspace-manager.md).

Related View

- USER_WM_POLICIES contains information about Oracle Virtual Private Database (VPD) security policies defined on any version-enabled table or related view owned by the current user.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.13 ALL_WM_RIC_INFO

ALL_WM_RIC_INFO contains information about referential integrity constraints in version-enabled tables that the current user can access. Workspace Manager uses this information to provide referential integrity support, which is described in [Referential Integrity Support](introduction-to-workspace-manager.md).

Related View

- USER_WM_RIC_INFOcontains information about referential integrity constraints in version-enabled tables that the current user owns.

| Column              | Datatype         | Null?      | Description                                                                                                                                                                                                                                                                           |
|:--------------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CT_OWNER `         | `VARCHAR2(128)`  | `NOT NULL` | Owner of the child table in the referential integrity constraint.                                                                                                                                                                                                                     |
| `CT_NAME `          | `VARCHAR2(128)`  |            | Name of the child table in the referential integrity constraint.                                                                                                                                                                                                                      |
| `PT_OWNER `         | `VARCHAR2(128)`  |            | Owner of the parent table in the referential integrity constraint.                                                                                                                                                                                                                    |
| `PT_NAME `          | `VARCHAR2(128)`  |            | Name of the parent table in the referential integrity constraint.                                                                                                                                                                                                                     |
| `RIC_NAME`          | `VARCHAR2(128)`  | `NOT NULL` | Name of the referential integrity constraint.                                                                                                                                                                                                                                         |
| `CT_COLS`           | `VARCHAR2(4000)` |            | List of foreign key columns in the child table in the referential integrity constraint.                                                                                                                                                                                               |
| `PT_COLS`           | `VARCHAR2(4000)` |            | List of foreign key columns in the parent table in the referential integrity constraint.                                                                                                                                                                                              |
| `R_CONSTRAINT_NAME` | `VARCHAR2(128)`  |            | Name of the unique constraint defined on the parent table in the referential integrity constraint.                                                                                                                                                                                    |
| `DELETE_RULE`       | `VARCHAR2(1)`    |            | Rule to apply when deletion occurs in the parent table. `C` (Cascade) causes related child table rows to be deleted; `N` (Set Null) causes the foreign key of related child table rows to be set to null; `R` (Restrict) prevents the deletion if any related child table rows exist. |
| `STATUS`            | `VARCHAR2(8)`    |            | `ENABLED` if the referential integrity constraint is enabled; `DISABLED` if the referential integrity constraint is disabled.                                                                                                                                                         |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.14 ALL_WM_TAB_TRIGGERS

ALL_WM_TAB_TRIGGERS contains information about triggers that the current user created and for version-enabled tables owned by the current user that have triggers defined on them. If the current user has the `CREATE ANY TRIGGER` privilege, trigger information is displayed for all version-enabled tables.

Related View

- USER_WM_TAB_TRIGGERS contains information about triggers that are owned by the current user and that are on version-enabled tables.

| Column                 | Datatype         | Null?      | Description                                                                                                                                                                                        |
|:-----------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TRIGGER_OWNER`        | `VARCHAR2(128)`  | `NOT NULL` | Owner (schema) of the trigger.                                                                                                                                                                     |
| `TRIGGER_NAME`         | `VARCHAR2(128)`  | `NOT NULL` | Name of the trigger.                                                                                                                                                                               |
| `TABLE_OWNER`          | `VARCHAR2(128)`  |            | Owner (schema) of the table on which the trigger is defined.                                                                                                                                       |
| `TABLE_NAME`           | `VARCHAR2(128)`  |            | Name of the table on which the trigger is defined.                                                                                                                                                 |
| `TRIGGER_TYPE`         | `VARCHAR2(4000)` |            | Trigger type: one of the codes described following this table.                                                                                                                                     |
| `STATUS`               | `VARCHAR2(8)`    |            | `ENABLED` if the trigger is enabled; `DISABLED` if the trigger is disabled.                                                                                                                        |
| `WHEN_CLAUSE`          | `VARCHAR2(4000)` |            | Clause that must evaluate to `TRUE` for the trigger body (`TRIGGER_BODY`) to execute.                                                                                                              |
| `DESCRIPTION`          | `VARCHAR2(4000)` |            | Description of the trigger. Useful if the trigger must be re-created.                                                                                                                              |
| `TRIGGER_BODY`         | `CLOB`           |            | Statements executed by the trigger.                                                                                                                                                                |
| `TAB_MERGE_WO_REMOVE`  | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.TABLE_MERGE_WO_REMOVE_DATA` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.TABLE_MERGE_WO_REMOVE_DATA` has not been set.         |
| `TAB_MERGE_W_REMOVE`   | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.TABLE_MERGE_W_REMOVE_DATA` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.TABLE_MERGE_W_REMOVE_DATA` has not been set.           |
| `WSPC_MERGE_WO_REMOVE` | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.WORKSPACE_MERGE_WO_REMOVE_DATA` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.WORKSPACE_MERGE_WO_REMOVE_DATA` has not been set. |
| `WSPC_MERGE_W_REMOVE`  | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.WORKSPACE_MERGE_W_REMOVE_DATA` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.WORKSPACE_MERGE_W_REMOVE_DATA` has not been set.   |
| `DML`                  | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.DML` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.DML` has not been set.                                                       |
| `TABLE_IMPORT`         | `VARCHAR2(3)`    |            | `ON` if `DBMS_WM.TABLE_IMPORT` has been set (see the [SetTriggerEvents](DBMS_WM-reference.md) procedure), or `OFF` if `DBMS_WM.TABLE_IMPORT` has not been set.                                     |

`TRIGGER_TYPE` is one of the following values:

- `BIR`: before insert for each row

- `AIR`: after insert for each row

- `BUR`: before update for each row

- `AUR`: after update for each row

- `BDR`: before delete for each row

- `ADR`: after delete for each row

- `BIS`: before insert for each statement

- `AIS`: after insert for each statement

- `BUS`: before update for each statement

- `AUS`: after update for each statement

- `BDS`: before delete for each statement

- `ADS`: after delete for each statement

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.15 ALL_WM_VERSIONED_TABLES

ALL_WM_VERSIONED_TABLES contains information about all version-enabled tables on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `DELETE`, `UPDATE`.

Related Views

- USER_WM_VERSIONED_TABLES contains information about version-enabled tables that the current user owns.

- DBA_WM_VERSIONED_TABLES contains information about all that the current user owns.

| Column         | Datatype         | Null?      | Description                                                                                                                                                                                                                                                                  |
|:---------------|:-----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TABLE_NAME`   | `VARCHAR2(128)`  | `NOT NULL` | Name of a version-enabled table.                                                                                                                                                                                                                                             |
| `OWNER`        | `VARCHAR2(128)`  | `NOT NULL` | Owner (schema) of the table.                                                                                                                                                                                                                                                 |
| `STATE`        | `VARCHAR2(11)`   |            | State of the table: one of the values described following this table.                                                                                                                                                                                                        |
| `HISTORY`      | `VARCHAR2(22)`   |            | History option for the table: `NONE`, `VIEW_W_OVERWRITE`, or `VIEW_WO_OVERWRITE`. (For an explanation of the history option values, see the information about the [EnableVersioning](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md).) |
| `NOTIFICATION` | `VARCHAR2(3)`    |            | (Not used for this release.)                                                                                                                                                                                                                                                 |
| `CONFLICT`     | `VARCHAR2(4000)` |            | `YES` if there are any conflicts on the table between the workspace that performed the [SetConflictWorkspace](DBMS_WM-reference.md) operation and its parent workspace; otherwise, `NO`.                                                                                     |
| `DIFF`         | `VARCHAR2(4000)` |            | `YES` if there are any differences for this table as a result of a [SetDiffVersions](DBMS_WM-reference.md) operation; otherwise, `NO`.                                                                                                                                       |
| `VALIDTIME`    | `VARCHAR2(3)`    |            | `YES` if valid time is enabled on the table; otherwise, `NO`.                                                                                                                                                                                                                |

`STATE` is one of the following values:

- `ADD_VT`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'ADD_VALID_TIME`') is being performed on this table.

- `AVTDDL`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure is being performed on this table.

- `BDDL`: The [BeginDDL](DBMS_WM-reference.md) procedure is being performed on the table.

- `BL_F_BEGIN`: The [CommitBulkLoading](DBMS_WM-reference.md) procedure is being performed on this table.

- `BL_P_BEGIN`: The [BeginBulkLoading](DBMS_WM-reference.md) procedure is being performed on this table.

- `BL_P_END`: The table is active in a bulk loading session.

- `BL_R_BEGIN`: The [RollbackBulkLoading](DBMS_WM-reference.md) procedure is being performed on this table.

- `CDDL`: The [CommitDDL](DBMS_WM-reference.md) procedure is being performed on the table.

- `D_HIST_COLS`: The columns of the table version-enabled are being downgraded.

- `DDL`: The table is active in a DDL session.

- `DV`: The table is being version-disabled.

- `EV`: The table is being version-enabled.

- `IDDL`: The [Initialize_After_Import](DBMS_WM-reference.md) procedure is being performed on the table.

- `LW_DISABLED`: The table has been lightweight version-disabled (an internal operation).

- `LWDV`: The table is being lightweight version-disabled (an internal operation).

- `LWEV`: The table is being lightweight version-enabled (an internal operation).

- `ODDL`: The [GetOriginalDDL](DBMS_WM-reference.md) procedure is being performed on this table.

- `RB_IND`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'REBUILD_INDEX'`) is being performed on this table.

- `RN_CONS`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'RENAME_CONSTRAINT'`) is being performed on this table.

- `RN_IND`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'RENAME_INDEX'`) is being performed on this table.

- `SYNCVTV1`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'USE_WM_PERIOD_FOR_VALIDTIME'`) is being performed on this table.

- `SYNCVTV2`: The [AlterVersionedTable](DBMS_WM-reference.md) procedure (with the `alter_option` parameter set to `'USE_SCALAR_TYPES_FOR_VALIDTIME`') is being performed on this table.

- `TDDL`: The [Add_Topo_Geometry_Layer](DBMS_WM-reference.md) or [Add_Topo_Geometry_Layer](DBMS_WM-reference.md) procedure is being performed on this table.

- `U_HIST_COLS`: The columns of the table version-enabled are being upgraded.

- `VERSIONED`: The table has been version-enabled.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.16 ALL_WM_VT_ERRORS

ALL_WM_VT_ERRORS contains information about the error that occurred during the last call to the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure that specified a table on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `DELETE`, `UPDATE`.

Related View

- USER_WM_VT_ERRORS contains information about the error that occurred during the last call to the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure that specified a table that the current user owns and on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `DELETE`, `UPDATE`.

| Column       | Datatype         | Null?      | Description                                                                                                                                                                         |
|:-------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`      | `VARCHAR2(128)`  | `NOT NULL` | Owner (schema) of the table.                                                                                                                                                        |
| `TABLE_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of a version-enabled table.                                                                                                                                                    |
| `STATE`      | `VARCHAR2(11)`   |            | State of the table. For example, `EV` means that the table is being version-enabled, and `DV` means that the table is being version-disabled.                                       |
| `SQL_STR`    | `VARCHAR2(4000)` |            | The SQL statement that failed during the processing of the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure.                                |
| `STATUS`     | `VARCHAR2(49)`   |            | Information about the state of the SQL statement that failed during the processing of the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure. |
| `ERROR_MSG`  | `VARCHAR2(200)`  |            | Error message caused by the SQL statement that failed during the processing of the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure.        |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.17 ALL_WORKSPACE_PRIVS

ALL_WORKSPACE_PRIVS contains information about Workspace Manager privileges in all workspaces that the current user can access.

Related Views

- USER_WORKSPACE_PRIVS contains information about Workspace Manager privileges in workspaces created by the current user.

- DBA_WORKSPACE_PRIVS contains information about Workspace Manager privileges in all workspaces.

| Column       | Datatype        | Null? | Description                                                                                                                                        |
|:-------------|:----------------|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE`    | `VARCHAR2(128)` |       | User or role to which the privilege was granted.                                                                                                   |
| `WORKSPACE ` | `VARCHAR2(128)` |       | Name of the workspace.                                                                                                                             |
| `PRIVILEGE ` | `VARCHAR2(23)`  |       | Name of the Workspace Manager privilege.                                                                                                           |
| `GRANTOR`    | `VARCHAR2(128)` |       | User or role that granted the privilege.                                                                                                           |
| `GRANTABLE`  | `VARCHAR2(3)`   |       | `YES` if `grantee` was given the grant option (that is, can grant the privilege to other users); `NO` if `grantee` was not given the grant option. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.18 ALL_WORKSPACE_SAVEPOINTS

ALL_WORKSPACE_SAVEPOINTS contains information about savepoints in all workspaces that the current user can access.

Related Views

- USER_WORKSPACE_SAVEPOINTS contains information about savepoints in workspaces created by the current user.

- DBA_WORKSPACE_SAVEPOINTS contains information about savepoints in all workspaces.

| Column          | Datatype                   | Null?      | Description                                                                                                                                                                                                                                                                                                                                                                          |
|:----------------|:---------------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SAVEPOINT`     | `VARCHAR2(128)`            | `NOT NULL` | Name of the savepoint. Explicit savepoints are named by users; implicit savepoints are named by Workspace Manager.                                                                                                                                                                                                                                                                   |
| `WORKSPACE`     | `VARCHAR2(128)`            | `NOT NULL` | Workspace in which the savepoint was created.                                                                                                                                                                                                                                                                                                                                        |
| `IMPLICIT`      | `VARCHAR2(3)`              |            | `YES` if the savepoint is implicit (that is, was created automatically by Workspace Manager); `NO` if the savepoint is explicit (that is, was created by a user).                                                                                                                                                                                                                    |
| `POSITION`      | `NUMBER(38)`               |            | Position of the savepoint in the sequence in which savepoints were created.                                                                                                                                                                                                                                                                                                          |
| `OWNER`         | `VARCHAR2(128)`            |            | Name of the user that created the savepoint.                                                                                                                                                                                                                                                                                                                                         |
| `CREATETIME`    | `TIMESTAMP WITH TIME ZONE` |            | Date and time that the savepoint was created.                                                                                                                                                                                                                                                                                                                                        |
| `DESCRIPTION`   | `VARCHAR2(1000)`           |            | Description of the savepoint.                                                                                                                                                                                                                                                                                                                                                        |
| `CANROLLBACKTO` | `VARCHAR2(3)`              |            | `YES` if the savepoint can be rolled back to; `NO` if the savepoint cannot be rolled back to. In a [RollbackToSP](DBMS_WM-reference.md) operation, if any implicit savepoints have greater `POSITION` values than the position of the savepoint to be rolled back to, you must first merge or remove the workspaces that caused these intervening implicit savepoints to be created. |
| `REMOVABLE`     | `VARCHAR2(3)`              |            | `YES` if the savepoint can be removed; `NO` if the savepoint cannot be removed. An implicit savepoint cannot be removed if it has any child dependencies; all other implicit savepoints and all explicit savepoints can be removed.                                                                                                                                                  |
| `VERSION`       | `NUMBER`                   |            | Version number of the specified savepoint within the workspace.                                                                                                                                                                                                                                                                                                                      |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.19 ALL_WORKSPACES

ALL_WORKSPACES contains information about all workspaces that the current user can access.

Its columns are the same as those for the DBA_WORKSPACES view, except for the following:

- ALL_WORKSPACES includes the following columns that are not in DBA_WORKSPACES: CONTINUALLY_REFRESHED, WORKSPACE_LOCKMODE, and WORKSPACE_LOCKMODE_OVERRIDE.

- DBA_WORKSPACES includes the following columns that are not in ALL_WORKSPACES: SID and SERIAL#.

Related Views

- DBA_WORKSPACES contains information about all workspaces. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

- USER_WORKSPACES contains information about workspaces created by the current user.

| Column                        | Datatype                   | Null? | Description                                                                                                                                                                                                                                                                                                     |
|:------------------------------|:---------------------------|:------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `WORKSPACE`                   | `VARCHAR2(128)`            |       | Name of the workspace.                                                                                                                                                                                                                                                                                          |
| `WORKSPACE_ID`                | `NUMBER(38)`               |       | ID of the workspace.                                                                                                                                                                                                                                                                                            |
| `PARENT_WORKSPACE`            | `VARCHAR2(128)`            |       | Parent workspace of this workspace.                                                                                                                                                                                                                                                                             |
| `PARENT_SAVEPOINT `           | `VARCHAR2(128)`            |       | Implicit savepoint that was created in the parent workspace when this workspace was created.                                                                                                                                                                                                                    |
| `OWNER`                       | `VARCHAR2(128)`            |       | Name of the user that created the workspace.                                                                                                                                                                                                                                                                    |
| `CREATETIME`                  | `TIMESTAMP WITH TIME ZONE` |       | Date and time that the workspace was created.                                                                                                                                                                                                                                                                   |
| `DESCRIPTION`                 | `VARCHAR2(1000)`           |       | Description of the workspace.                                                                                                                                                                                                                                                                                   |
| `FREEZE_STATUS`               | `VARCHAR2(8)`              |       | `FROZEN` if the workspace is frozen (by a [FreezeWorkspace](DBMS_WM-reference.md) operation); `UNFROZEN` if the workspace is not frozen.                                                                                                                                                                        |
| `FREEZE_MODE`                 | `VARCHAR2(16)`             |       | `NO_ACCESS`, `READ_ONLY`, `1WRITER`, or `1WRITER_SESSION`. See the `freezemode` parameter description for the [FreezeWorkspace](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .                                                                                         |
| `FREEZE_WRITER`               | `VARCHAR2(128)`            |       | The user allowed to make changes in the workspace; or null if the workspace is not frozen or if it is frozen in `NO_ACCESS` or `READ_ONLY` mode. See the `freezewriter` parameter description for the [FreezeWorkspace](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) . |
| `FREEZE_OWNER`                | `VARCHAR2(128)`            |       | Name of the user that froze the workspace.                                                                                                                                                                                                                                                                      |
| `SESSION_DURATION`            | `VARCHAR2(3)`              |       | `YES` if the workspace is frozen only for the duration of the current session; `NO` if the workspace is frozen until an explicit [UnfreezeWorkspace](DBMS_WM-reference.md) procedure call is made; null if the workspace is not currently frozen.                                                               |
| `CURRENT_SESSION`             | `VARCHAR2(3)`              |       | `YES` if the current session is allowed to make changes in the workspace; `NO` if the current session is not allowed to make changes in the workspace; null if the workspace is not currently frozen in `session_duration` mode.                                                                                |
| `RESOLVE_STATUS`              | `VARCHAR2(8)`              |       | `ACTIVE` if a conflict resolution session is in progress; `INACTIVE` if a conflict resolution session is not in progress.                                                                                                                                                                                       |
| `RESOLVE_USER`                | `VARCHAR2(128)`            |       | Name of the user that started the conflict resolution session if `resolve_status` is `ACTIVE`; otherwise, null.                                                                                                                                                                                                 |
| `CONTINUALLY_REFRESHED`       | `VARCHAR2(3)`              |       | `YES` if the workspace is continually refreshed (see the description of the `isrefreshed` parameter of the [CreateWorkspace](DBMS_WM-reference.md) procedure); `NO` if the workspace is not continually refreshed.                                                                                              |
| `WORKSPACE_LOCKMODE`          | `VARCHAR2(19)`             |       | `EXCLUSIVE` if the locking mode is exclusive; `SHARED` is the locking mode is shared; `CARRY` if the locking mode is carry-forward. See the `lockmode` parameter description for the [SetWorkspaceLockModeON](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .           |
| `WORKSPACE_LOCKMODE_OVERRIDE` | `VARCHAR2(3)`              |       | `YES` if the override option is `TRUE`; `NO` if the override option is `FALSE`; null if the workspace lock mode is not set. See the `override` parameter description for the [SetWorkspaceLockModeON](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .                   |
| `MP_ROOT_WORKSPACE`           | `VARCHAR2(128)`            |       | Name of the root workspace of the multiparent graph; null if the workspace is not part of a multiparent graph. (Multiparent workspaces are explained in [Multiparent Workspaces](introduction-to-workspace-manager.md).)                                                                                        |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.20 DBA_REMOVED_WORKSPACES

`DBA_REMOVED_WORKSPACES` contains information about workspaces that have been removed during a [RemoveWorkspace](DBMS_WM-reference.md) operation or a [MergeWorkspace](DBMS_WM-reference.md) operation in which the `remove_workspace` parameter value was `true`, and while the value of the Workspace Manager system parameter `KEEP_REMOVED_WORKSPACES_INFO` was `ON`. (This system parameter is described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).) Its columns are the same as those in ALL_REMOVED_WORKSPACES. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.21 DBA_WM_SYS_PRIVS

DBA_WM_SYS_PRIVS contains information about all users that have Workspace Manager system-level privileges (that is, privilege names containing \_ANY_WORKSPACE, as explained in [Privilege Management with Workspace Manager](introduction-to-workspace-manager.md)). This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

| Column      | Datatype        | Null? | Description                                                                                                                                        |
|:------------|:----------------|:------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `GRANTEE`   | `VARCHAR2(128)` |       | User or role to which the system-level privilege was granted.                                                                                      |
| `PRIVILEGE` | `VARCHAR2(23)`  |       | Name of the Workspace Manager system-level privilege.                                                                                              |
| `GRANTOR`   | `VARCHAR2(128)` |       | User or role that granted the system-level privilege.                                                                                              |
| `GRANTABLE` | `VARCHAR2(3)`   |       | `YES` if `grantee` was given the grant option (that is, can grant the privilege to other users); `NO` if `grantee` was not given the grant option. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.22 DBA_WM_VERSIONED_TABLES

DBA_WM_VERSIONED_TABLES contains information about all version-enabled tables. Its columns are the same as those in ALL_WM_VERSIONED_TABLES. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.23 DBA_WM_VT_ERRORS

DBA_WM_VT_ERRORS contains information about the error that occurred during the last call to the [DisableVersioning](DBMS_WM-reference.md), [CommitDDL](DBMS_WM-reference.md), or [RecoverFromDroppedUser](DBMS_WM-reference.md) procedure. Its columns are the same as those in ALL_WM_VT_ERRORS. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.24 DBA_WORKSPACE_PRIVS

DBA_WORKSPACE_PRIVS contains information about Workspace Manager privileges in all workspaces. Its columns are the same as those in ALL_WORKSPACE_PRIVS. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.25 DBA_WORKSPACE_SAVEPOINTS

DBA_WORKSPACE_SAVEPOINTS contains information about savepoints in all workspaces. Its columns are the same as those in ALL_WORKSPACE_SAVEPOINTS. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.26 DBA_WORKSPACE_SESSIONS

DBA_WORKSPACE_SESSIONS contains information about all users and workspaces (except for the `LIVE` workspace). This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role. It is useful for monitoring users in the different workspaces.

| Column        | Datatype        | Null?      | Description                                                                                                                                                                                                                |
|:--------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME `   | `VARCHAR2(128)` |            | User name.                                                                                                                                                                                                                 |
| `WORKSPACE `  | `VARCHAR2(128)` | `NOT NULL` | Workspace that the user is currently in.                                                                                                                                                                                   |
| `SID`         | `NUMBER`        |            | Session ID.                                                                                                                                                                                                                |
| `STATUS `     | `VARCHAR2(8)`   |            | `ACTIVE` if the user currently has an open transaction (that is, a database transaction); `INACTIVE` if the user does not have an open transaction.                                                                        |
| `ISIMPLICIT ` | `VARCHAR2(3)`   |            | `NO` if the session has executed GotoWorkspace or performed a DML operation on a version-enabled table. Otherwise, `YES` for any session in the `LIVE` workspace (the default for any session connecting to the database). |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.27 DBA_WORKSPACES

DBA_WORKSPACES contains information about all workspaces, including those whose removal has been deferred. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

Its columns are the same as those for the ALL_WORKSPACES view, except for the following:

- ALL_WORKSPACES includes the following columns that are not in DBA_WORKSPACES: CONTINUALLY_REFRESHED, WORKSPACE_LOCKMODE, and WORKSPACE_LOCKMODE_OVERRIDE.

- DBA_WORKSPACES includes the following columns that are not in ALL_WORKSPACES: SID, SERIAL#, and INST_ID.

Related Views

- ALL_WORKSPACES contains information about all workspaces.

- USER_WORKSPACES contains information about workspaces created by the current user.

| Column              | Datatype                   | Null? | Description                                                                                                                                                                                                                                                                                                                                                                                           |
|:--------------------|:---------------------------|:------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `WORKSPACE`         | `VARCHAR2(128)`            |       | Name of the workspace.                                                                                                                                                                                                                                                                                                                                                                                |
| `WORKSPACE_ID`      | `NUMBER(38)`               |       | ID of the workspace.                                                                                                                                                                                                                                                                                                                                                                                  |
| `PARENT_WORKSPACE`  | `VARCHAR2(128)`            |       | Parent workspace of this workspace.                                                                                                                                                                                                                                                                                                                                                                   |
| `PARENT_SAVEPOINT ` | `VARCHAR2(128)`            |       | Implicit savepoint that was created in the parent workspace when this workspace was created.                                                                                                                                                                                                                                                                                                          |
| `OWNER`             | `VARCHAR2(128)`            |       | Name of the user that created the workspace.                                                                                                                                                                                                                                                                                                                                                          |
| `CREATETIME`        | `TIMESTAMP WITH TIME ZONE` |       | Date and time that the workspace was created.                                                                                                                                                                                                                                                                                                                                                         |
| `DESCRIPTION`       | `VARCHAR2(1000)`           |       | Description of the workspace.                                                                                                                                                                                                                                                                                                                                                                         |
| `FREEZE_STATUS`     | `VARCHAR2(8)`              |       | `FROZEN` if the workspace is frozen (by a [FreezeWorkspace](DBMS_WM-reference.md) operation); `UNFROZEN` if the workspace is not frozen.                                                                                                                                                                                                                                                              |
| `FREEZE_MODE`       | `VARCHAR2(16)`             |       | `NO_ACCESS`, `READ_ONLY`, `1WRITER`, `1WRITER_SESSION`, or `DEFERRED_REMOVAL`. See the `freezemode` parameter description for the [FreezeWorkspace](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .<br>If the value is `1WRITER_SESSION`, you can examine the `SID`, `SERIAL#`, and `INST_ID` column values to see which session has a lock on the workspace. |
| `FREEZE_WRITER`     | `VARCHAR2(128)`            |       | The user allowed to make changes in the workspace; or null if the workspace is not frozen or if it is frozen in `NO_ACCESS`, `READ_ONLY`, or `DEFERRED_REMOVAL` mode. See the `freezewriter` parameter description for the [FreezeWorkspace](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md).                                                                   |
| `SID`               | `NUMBER`                   |       | Oracle session identifier (SID) of the associated session.                                                                                                                                                                                                                                                                                                                                            |
| `SERIAL#`           | `NUMBER`                   |       | Serial number associated with the session.                                                                                                                                                                                                                                                                                                                                                            |
| `INST_ID`           | `NUMBER`                   |       | Instance ID associated with the session.                                                                                                                                                                                                                                                                                                                                                              |
| `FREEZE_OWNER`      | `VARCHAR2(128)`            |       | Name of the user that froze the workspace.                                                                                                                                                                                                                                                                                                                                                            |
| `SESSION_DURATION`  | `VARCHAR2(3)`              |       | `YES` if the workspace is frozen only for the duration of the current session; `NO` if the workspace is frozen until an explicit [UnfreezeWorkspace](DBMS_WM-reference.md) procedure call is made; null if the workspace is not currently frozen.                                                                                                                                                     |
| `CURRENT_SESSION`   | `VARCHAR2(3)`              |       | `YES` if the current session is allowed to make changes in the workspace; `NO` if the current session is not allowed to make changes in the workspace; null if the workspace is not currently frozen in `session_duration` mode.                                                                                                                                                                      |
| `RESOLVE_STATUS`    | `VARCHAR2(8)`              |       | `ACTIVE` if a conflict resolution session is in progress; `INACTIVE` if a conflict resolution session is not in progress.                                                                                                                                                                                                                                                                             |
| `RESOLVE_USER`      | `VARCHAR2(128)`            |       | Name of the user that started the conflict resolution session if `resolve_status` is `ACTIVE`; otherwise, null.                                                                                                                                                                                                                                                                                       |
| `MP_ROOT_WORKSPACE` | `VARCHAR2(128)`            |       | Name of the root workspace of the multiparent graph; null if the workspace is not part of a multiparent graph. (Multiparent workspaces are explained in [Multiparent Workspaces](introduction-to-workspace-manager.md).)                                                                                                                                                                              |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.28 ROLE_WM_PRIVS

ROLE_WM_PRIVS contains information about privileges that all roles granted to the current user have in each workspace.

Related View

- USER_WM_PRIVS contains information about privileges that the current user has in each workspace.

| Column       | Datatype        | Null? | Description                                                                                                                                      |
|:-------------|:----------------|:------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `ROLE `      | `VARCHAR2(128)` |       | Name of the role.                                                                                                                                |
| `WORKSPACE ` | `VARCHAR2(128)` |       | Name of the workspace.                                                                                                                           |
| `PRIVILEGE ` | `VARCHAR2(23)`  |       | Name of the Workspace Manager privilege.                                                                                                         |
| `GRANTABLE`  | `VARCHAR2(3)`   |       | `YES` if the role was given the grant option (that is, can grant the privilege to other users); `NO` if the role was not given the grant option. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.29 USER_MP_GRAPH_WORKSPACES

USER_MP_GRAPH_WORKSPACES contains information about multiparent graph workspaces (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)) for which the leaf workspace is owned by the current user. Its columns are the same as those in ALL_MP_GRAPH_WORKSPACES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.30 USER_MP_PARENT_WORKSPACES

USER_MP_PARENT_WORKSPACES contains information about parent workspaces of multiparent workspaces (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)) that the current user owns. Its columns are the same as those in ALL_MP_PARENT_WORKSPACES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.31 USER_REMOVED_WORKSPACES

`USER_REMOVED_WORKSPACES` contains information about workspaces, that the current user owns, that have been removed during a [RemoveWorkspace](DBMS_WM-reference.md) operation or a [MergeWorkspace](DBMS_WM-reference.md) operation in which the `remove_workspace` parameter value was `true`, and while the value of the Workspace Manager system parameter `KEEP_REMOVED_WORKSPACES_INFO` was `ON`. (This system parameter is described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).) Its columns are the same as those in ALL_REMOVED_WORKSPACES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.32 USER_WM_CONS_COLUMNS

USER_WM_CONS_COLUMNS contains information about columns in unique constraints on version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_CONS_COLUMNS, except it does not contain an `OWNER` column.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.33 USER_WM_CONSTRAINTS

USER_WM_CONSTRAINTS contains information about constraints on version-enabled tables that the current user owns. It provides information about the following kinds of constraints: `UNIQUE` constraint, unique index, `PRIMARY KEY` constraints, and `CHECK` constraints. Its columns are the same as those in ALL_WM_CONSTRAINTS, except it does not contain an `OWNER` or `INDEX_OWNER` column.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.34 USER_WM_IND_COLUMNS

USER_WM_IND_COLUMNS contains information about indexes used for enforcing unique constraints on version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_IND_COLUMNS, except it does not contain an `OWNER` column.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.35 USER_WM_IND_EXPRESSIONS

USER_WM_IND_EXPRESSIONS contains information about indexes used for enforcing unique constraints on version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_IND_EXPRESSIONS, except it does not contain an `OWNER` column.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.36 USER_WM_LOCKED_TABLES

USER_WM_LOCKED_TABLES contains information about Workspace Manager locks on rows in version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_LOCKED_TABLES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.37 USER_WM_MODIFIED_TABLES

USER_WM_MODIFIED_TABLES contains information about version-enabled tables that have been modified and that the current user owns. Its columns are the same as those in ALL_WM_MODIFIED_TABLES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.38 USER_WM_POLICIES

USER_WM_POLICIES contains information about Oracle Virtual Private Database (VPD) security policies defined on any version-enabled table or related view owned by the current user. Its columns are the same as those in the ALL_WM_POLICIES view, except it does not include an OWNER column.

Workspace Manager uses this information to provide VPD support, which is described in [Virtual Private Database Considerations](introduction-to-workspace-manager.md).

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.39 USER_WM_PRIVS

USER_WM_PRIVS contains information about privileges that the current user has in each workspace.

Related View

- ROLE_WM_PRIVS contains information about privileges that all roles granted to the current user have in each workspace.

| Column       | Datatype        | Null? | Description                                                                                                                                      |
|:-------------|:----------------|:------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `WORKSPACE ` | `VARCHAR2(128)` |       | Name of the workspace.                                                                                                                           |
| `PRIVILEGE ` | `VARCHAR2(23)`  |       | Name of the Workspace Manager privilege.                                                                                                         |
| `GRANTOR`    | `VARCHAR2(128)` |       | Name of the user that granted the privilege to the current user.                                                                                 |
| `GRANTABLE`  | `VARCHAR2(3)`   |       | `YES` if the user was given the grant option (that is, can grant the privilege to other users); `NO` if the user was not given the grant option. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.40 USER_WM_RIC_INFO

USER_WM_RIC_INFO contains information about referential integrity constraints in version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_RIC_INFO.

Workspace Manager uses this information to provide referential integrity support, which is described in [Referential Integrity Support](introduction-to-workspace-manager.md).

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.41 USER_WM_TAB_TRIGGERS

USER_WM_TAB_TRIGGERS contains information about triggers that are owned by the current user and that are on version-enabled tables. Its columns are the same as those in ALL_WM_TAB_TRIGGERS, except that it does not contain the `TRIGGER_OWNER` column.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.42 USER_WM_VERSIONED_TABLES

USER_WM_VERSIONED_TABLES contains information about version-enabled tables that the current user owns. Its columns are the same as those in ALL_WM_VERSIONED_TABLES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.43 USER_WM_VT_ERRORS

USER_WM_VT_ERRORS contains information about the error that occurred during the last call to the [DisableVersioning](DBMS_WM-reference.md) or [CommitDDL](DBMS_WM-reference.md) procedure that specified a table that the current user owns and on which the current user has one or more of the following privileges: `SELECT`, `INSERT`, `DELETE`, `UPDATE`. Its columns are the same as those in ALL_WM_VT_ERRORS.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.44 USER_WORKSPACE_PRIVS

USER_WORKSPACE_PRIVS contains information about Workspace Manager privileges in workspaces created by the current user. Its columns are the same as those in ALL_WORKSPACE_PRIVS.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.45 USER_WORKSPACE_SAVEPOINTS

USER_WORKSPACE_SAVEPOINTS contains information about savepoints in workspaces created by the current user. Its columns are the same as those in ALL_WORKSPACE_SAVEPOINTS.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.46 USER_WORKSPACES

USER_WORKSPACES contains information about workspaces created by the current user. Its columns are the same as those in ALL_WORKSPACES.

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.47 WM_COMPRESS_BATCH_SIZES

WM_COMPRESS_BATCH_SIZES contains information related to compression capabilities for version-enabled tables. This view is only available to users with the `WM_ADMIN_ROLE` or `SELECT_CATALOG_ROLE` role.

| Column        | Datatype        | Null?      | Description                                                                                                                                                          |
|:--------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | User name of the table owner.                                                                                                                                        |
| `TABLE_NAME`  | `VARCHAR2(128)` | NOT NULL   | Name of the version-enabled table.                                                                                                                                   |
| `BATCH_SIZE`  | `VARCHAR2(23)`  |            | `TABLE` if the table can be compressed as a single batch only; `TABLE/PRIMARY_KEY_RANGE` if the table can be compressed as a single batch or in multiple batches.    |
| `NUM_BATCHES` | `NUMBER`        |            | `1` if `BATCH_SIZE` is `TABLE`, or a number specifying the number of batches to be used for compression operations when a batch size of `PRIMARY_KEY_RANGE` is used. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.48 WM_COMPRESSIBLE_TABLES

WM_COMPRESSIBLE_TABLES contains information about version-enabled tables that need to be compressed (if compression is to be performed) between two savepoints in a workspace. To create rows in this view, use the [SetCompressWorkspace](DBMS_WM-reference.md) procedure.

| Column            | Datatype        | Null?      | Description                                                                                                                                                                                                                 |
|:------------------|:----------------|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | User name of the table owner.                                                                                                                                                                                               |
| `TABLE_NAME`      | `VARCHAR2(128)` | NOT NULL   | Name of the version-enabled table.                                                                                                                                                                                          |
| `WORKSPACE`       | `VARCHAR2(256)` |            | Name of a workspace that was set as a result of a call to the [SetCompressWorkspace](DBMS_WM-reference.md) procedure.                                                                                                       |
| `BEGIN_SAVEPOINT` | VARCHAR2(256)   |            | Savepoint on the first version of the compression range. If the `firstSP` parameter was null in the call to the [SetCompressWorkspace](DBMS_WM-reference.md) procedure, this column contains `BEGINNING`.                   |
| `END_SAVEPOINT`   | VARCHAR2(256)   |            | Savepoint on the last version of the compression range. If both the `firstSP` and `secondSP` parameters were null in the call to the [SetCompressWorkspace](DBMS_WM-reference.md) procedure, this column contains `LATEST`. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.49 WM_EVENTS_INFO

WM_EVENTS_INFO contains information about the capture of Workspace Manager events. For information about Workspace Manager events, see [Workspace Manager Events](workspace-manager-events.md).

| Column       | Datatype        | Null?      | Description                                                                                          |
|:-------------|:----------------|:-----------|:-----------------------------------------------------------------------------------------------------|
| `EVENT_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name indicating the type of event.                                                                   |
| `CAPTURE`    | `VARCHAR2(3)`   |            | `ON` if events of this type are being captured; `OFF` if events of this type are not being captured. |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.50 WM_INSTALLATION

WM_INSTALLATION contains information about the installed release of Workspace Manager. The information includes the Workspace Manager version number (`OWM_VERSION`) and the Workspace Manager system parameters.

| Column  | Datatype         | Null? | Description                                                                                                                                                                                                                                   |
|:--------|:-----------------|:------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`  | `VARCHAR2(128)`  |       | Name of an informational item or system parameter pertaining to the current release of Workspace Manager on the system. (System parameters are explained in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).) |
| `VALUE` | `VARCHAR2(4000)` |       | Value associated with the informational item or system parameter identified in the `NAME` column.                                                                                                                                             |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.51 xxx_CONF Views

There is one conflict view for each version-enabled table. Each conflict view has a name in the form \<table_name\>\_CONF. For example, if the `EMPLOYEE` table is version-enabled, the `EMPLOYEE_CONF` metadata view exists.

Each conflict view contains the columns shown in Table 5-1.

Table 5-1 Columns in the xxx_CONF Views

| Column                                         | Datatype                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------------|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `WM_WORKSPACE`                                 | `VARCHAR2(256)`                    | Workspace in which the conflict exists.                                                                                                                                                                                                                                                                                                                                                                                                                |
| (One column for each column in original table) | (Same as column in original table) | Value of the column in this workspace.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_VALID`                                     | `WM_PERIOD`                        | Time period during which the row is valid, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).<br>If you set the `USE_SCALAR_TYPES_FOR_VALIDTIME` system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)) to `ON`, this column is replaced by two columns, `WM_VALIDFROM` and `WM_VALIDTILL`, of type `TIMEZONE WITH TIMESTAMP`. |
| `WM_DELETED`                                   | `VARCHAR2(3)`                      | `YES` if the row has been deleted; `NO` if the row has not been deleted; `NE` if the row is nonexistent (does not exist).                                                                                                                                                                                                                                                                                                                              |
| `WM_CONFLICTPERIOD`                            | `WM_PERIOD`                        | Overlapping period of the rows for which conflicts were detected, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).                                                                                                                                                                                                                                                                    |

A SELECT operation from a conflict view uses the workspace conflict context established by the [GotoWorkspace](DBMS_WM-reference.md) procedure, unless you have specified a workspace conflict context for the session by using the [SetConflictWorkspace](DBMS_WM-reference.md) procedure. Selecting from the conflict view finds rows in that table that are changed in the current workspace context, and compares their values with corresponding rows in the parent workspace to identify conflicts. If the current workspace conflict context is the `LIVE` workspace, all rows in the table are selected and no conflicts are found.

The following example lists the key value and all column values of conflicting rows in the `EMPLOYEE` table in the current workspace and its parent workspace. The conflict view reflects the context established by a previous call to the [GetWorkspace](DBMS_WM-reference.md) or [SetConflictWorkspace](DBMS_WM-reference.md) procedure to set the workspace conflict context (the current workspace in this case).

    SELECT * FROM EMPLOYEE_CONF;

If `ID`, `NAME`, and `CITY` are the columns in the `EMPLOYEE` table, then assume the following values:

    WM_WORKSPACE  ID   NAME    CITY     WM_DELETED
    NEWWORKSPACE  12   SMITH   NASHUA   NO
    DiffBase      12   SMITH   NY       NO
    LIVE          12   SMITH   BOSTON   NO

The database row identified by `ID = 12` was changed in `NEWWORKSPACE` and `LIVE` workspaces. In `NEWWORKSPACE` the city was changed to `NASHUA`, and in the `LIVE` workspace the city was changed to `BOSTON`. When `NEWWORKSPACE` is merged into `LIVE`, this row will show up as a conflict. The application must pick between the choices and resolve conflicts in favor of the workspace with the desired value.

Note that `DiffBase` refers to the common ancestor (or base), as explained in the Usage Notes for the [SetDiffVersions](DBMS_WM-reference.md) procedure.

The following example begins a conflict resolution session, calls the [ResolveConflicts](DBMS_WM-reference.md) procedure to delete the conflicting row from the `NEWWORKSPACE` workspace and to insert the value in the parent workspace (`LIVE`) into both workspaces, commits the transaction, and ends the conflict resolution session.

    DBMS_WM.BeginResolve ('NEWWORKSPACE');
    DBMS_WM.ResolveConflicts ('NEWWORKSPACE', 'EMPLOYEE', 'ID = 12', 'PARENT');
    COMMIT;
    DBMS_WM.CommitResolve ('NEWWORKSPACE');

For additional information about conflict resolution, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.52 xxx_DIFF Views

There is one difference view for each version-enabled table. Each difference view has a name in the form \<table_name\>\_DIFF. For example, if the `EMPLOYEE` table is version-enabled, the `EMPLOYEE_DIFF` metadata view exists. Rows are added to one or more xxx\_DIFF views each time the [SetDiffVersions](DBMS_WM-reference.md) procedure is executed.

Each difference view contains the columns shown in Table 5-2.

Table 5-2 Columns in the xxx_DIFF Views

| Column                                         | Datatype                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------------|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (One column for each column in original table) | (Same as column in original table) | Value of the column in this workspace.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_VALID`                                     | `WM_PERIOD`                        | Time period during which the row is valid, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).<br>If you set the `USE_SCALAR_TYPES_FOR_VALIDTIME` system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)) to `ON`, this column is replaced by two columns, `WM_VALIDFROM` and `WM_VALIDTILL`, of type `TIMEZONE WITH TIMESTAMP`. |
| `WM_DIFFVER`                                   | `VARCHAR2(256)`                    | Branch from which the values in the preceding columns are taken. (See the explanation following this table.)                                                                                                                                                                                                                                                                                                                                           |
| `WM_CODE`                                      | `VARCHAR2(2)`                      | One of the following codes describing the change: `U` (updated), `D` (deleted), `I` (inserted), `NC` (no change), `NE` (nonexistent).                                                                                                                                                                                                                                                                                                                  |
| `WM_DIFFPERIOD`                                | `WM_PERIOD`                        | Overlapping period of the rows for which a difference was detected, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).                                                                                                                                                                                                                                                                  |

The `WM_DIFFVER` value is in one of the following formats:

- `'<workspace1>, <savepoint1>'`

- `'<workspace2>, <savepoint2>'`

- `'DiffBase'`

If the two-parameter version of the [SetDiffVersions](DBMS_WM-reference.md) procedure was used, the value of `savepoint1` or `savepoint2` is `LATEST`.

Note the following about the possible values for `WM_CODE`:

- `NC` will appear for rows in workspaces that did not change the value when another workspace did change the value. For example, if `'<workspace2>, <savepoint2>'` updated the row, the code for that row is `U`, but the code for the `'<workspace1>, <savepoint1>'` and `'DiffBase'` rows is `NC` if they did not modify the row.

- `NE` will appear for `'DiffBase'` if a row is inserted in one or more branches, and `NE` will appear for `'DiffBase'` and a branch if only one branch has had any insert operations.

For more information, including an example showing rows being added to a differences view, see the section on the [SetDiffVersions](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.53 xxx_HIST Views

There is one history view for each version-enabled table, regardless of the value specified for the `hist` parameter in the call to the [EnableVersioning](DBMS_WM-reference.md) procedure. Each history view has a name in the form \<table_name\>\_HIST. For example, if the `EMPLOYEE` table is version-enabled, the `EMPLOYEE_HIST` metadata view exists.

You can use the history views to log and audit modifications to version-enabled tables.

Each history view contains the columns shown in Table 5-3. However, the WM_CREATETIME and WM_RETIRETIME columns are included only if the `hist` parameter was set to `VIEW_W_OVERWRITE` or `VIEW_WO_OVERWRITE` in the call to the [EnableVersioning](DBMS_WM-reference.md) procedure.

Table 5-3 Columns in the xxx_HIST Views

| Column                                         | Datatype                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------------|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (One column for each column in original table) | (Same as column in original table) | Value of the column in this workspace.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_VALID`                                     | `WM_PERIOD`                        | Time period during which the row is valid, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).<br>If you set the `USE_SCALAR_TYPES_FOR_VALIDTIME` system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)) to `ON`, this column is replaced by two columns, `WM_VALIDFROM` and `WM_VALIDTILL`, of type `TIMEZONE WITH TIMESTAMP`. |
| `WM_WORKSPACE`                                 | `VARCHAR2(128)`                    | Name of the workspace containing the row.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `WM_VERSION`                                   | `NUMBER(38)`                       | Version number of the row with which the data is associated.                                                                                                                                                                                                                                                                                                                                                                                           |
| `WM_USERNAME`                                  | `VARCHAR2(128)`                    | Name of the user that created the row.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_OPTYPE`                                    | `VARCHAR2(1)`                      | Type of change operation that was performed on the row: `D` (delete), `I` (insert), or `U` (update).                                                                                                                                                                                                                                                                                                                                                   |
| `WM_CREATETIME`                                | `TIMESTAMP WITH TIME ZONE`         | Time when the row was created or updated. (This column is present only if `VIEW_W_OVERWRITE` or `VIEW_WO_OVERWRITE` was specified for the `hist` parameter in the call to the [EnableVersioning](DBMS_WM-reference.md) procedure.)                                                                                                                                                                                                                     |
| `WM_RETIRETIME`                                | `TIMESTAMP WITH TIME ZONE`         | Time when the row was deleted or modified. (This column is present only if `VIEW_W_OVERWRITE` or `VIEW_WO_OVERWRITE` was specified for the `hist` parameter in the call to the [EnableVersioning](DBMS_WM-reference.md) procedure.)                                                                                                                                                                                                                    |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.54 xxx_LOCK Views

There is one lock view for each version-enabled table. Each lock view has a name in the form \<table_name\>\_LOCK. For example, if the `EMPLOYEE` table is version-enabled, the `EMPLOYEE_LOCK` metadata view exists. (For an explanation of Workspace Manager locking, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).)

Each lock view contains the columns shown in Table 5-4.

Table 5-4 Columns in the xxx_LOCK Views

| Column                                         | Datatype                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------------|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (One column for each column in original table) | (Same as column in original table) | Value of the column in this workspace.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_VALID`                                     | `WM_PERIOD`                        | Time period during which the row is valid, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).<br>If you set the `USE_SCALAR_TYPES_FOR_VALIDTIME` system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)) to `ON`, this column is replaced by two columns, `WM_VALIDFROM` and `WM_VALIDTILL`, of type `TIMEZONE WITH TIMESTAMP`. |
| `WM_LOCKMODE`                                  | `VARCHAR2(19)`                     | Type of lock: `EXCLUSIVE`, `WORKSPACE EXCLUSIVE`, `VERSION EXCLUSIVE`, or `SHARED`.                                                                                                                                                                                                                                                                                                                                                                    |
| `WM_USERNAME`                                  | `VARCHAR2(128)`                    | User name of the owner of the lock.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `WM_LOCKINGWORKSPACE`                          | `VARCHAR2(128)`                    | Name of the workspace in which the lock was placed.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `WM_INCURWORKSPACE`                            | `VARCHAR2(3)`                      | `YES` if the row is contained in the current workspace; `NO` if the row is not contained in the current workspace.                                                                                                                                                                                                                                                                                                                                     |

**Parent topic:** Workspace Manager Static Data Dictionary Views

### 5.55 xxx_MW Views

There is one multiworkspace view for each version-enabled table. Each multiworkspace view has a name in the form \<table_name\>\_MW. For example, if the `EMPLOYEE` table is version-enabled, the `EMPLOYEE_MW` metadata view exists. Rows are added to one or more xxx\_MW views each time the [SetMultiWorkspaces](DBMS_WM-reference.md) procedure (described in [DBMS_WM Package: Reference](DBMS_WM-reference.md) ) is executed.

Each multiworkspace view contains the columns shown in Table 5-5.

Table 5-5 Columns in the xxx_MW Views

| Column                                         | Datatype                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------------------------------------|:-----------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (One column for each column in original table) | (Same as column in original table) | Value of the column in this workspace.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `WM_VALID`                                     | `WM_PERIOD`                        | Time period during which the row is valid, if the table has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)).<br>If you set the `USE_SCALAR_TYPES_FOR_VALIDTIME` system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)) to `ON`, this column is replaced by two columns, `WM_VALIDFROM` and `WM_VALIDTILL`, of type `TIMEZONE WITH TIMESTAMP`. |
| `WM_MODIFIED_BY`                               | `VARCHAR2(128)`                    | Workspace containing the row that was modified.                                                                                                                                                                                                                                                                                                                                                                                                        |
| `WM_SEEN_BY`                                   | `CLOB`                             | Comma-delimited list of workspaces from which the row is visible.                                                                                                                                                                                                                                                                                                                                                                                      |
| `WM_OPTYPE`                                    | `VARCHAR2(1)`                      | One of the following codes describing the change: `U` (updated), `I` (inserted).                                                                                                                                                                                                                                                                                                                                                                       |

You can use the \<table_name\>\_MW view to see changes in another workspace without leaving the current workspace (for example, to check if there is a conflict with the other workspace). Each row in the view shows the data as it would be in that workspace if the workspace had been merged when the row was inserted in the view.

You can also use the \<table_name\>\_DIFF view (see xxx_DIFF Views) to see changes in another workspace without leaving the current workspace; however, the \<table_name\>\_DIFF view can be used for only two workspaces, whereas the \<table_name\>\_MW view can be used for any number of workspaces. In addition, the \<table_name\>\_DIFF view shows deleted rows, whereas the \<table_name\>\_MW view does not show deleted rows.

For more information and several examples, see the information about the [SetMultiWorkspaces](DBMS_WM-reference.md) procedure in [DBMS_WM Package: Reference](DBMS_WM-reference.md) .

**Parent topic:** Workspace Manager Static Data Dictionary Views
