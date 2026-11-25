Workspace Manager includes PL/SQL subprograms (procedures and functions), in a package named `DBMS_WM`, that perform the available features of the product. This chapter provides reference information on each subprogram.

**Note:**

Most Workspace Manager subprograms are procedures, but a few are functions. (A function returns a value; a procedure does not return a value.)

Most functions have names starting with Get (such as GetConflictWorkspace and GetWorkspace).

The subprograms are presented in alphabetical order. For a brief description of subprograms according to their logical groupings, see [DBMS_WM Subprogram Categories](introduction-to-workspace-manager.md).

Errors (exceptions) that can occur with Workspace Manager subprograms are documented in [Workspace Manager Error Messages](workspace-manager-error-messages.md), including the cause and suggested user action for each error.

Syntax notes:

- The `DBMS_WM` public synonym for the Workspace Manager PL/SQL package must be used with the subprogram name. The `DBMS_WM` public synonym is included in the format and in any examples.

- Subprogram calls are not case-sensitive, except for any quoted literal values. For example, the following code line excerpts are valid and semantically identical:

      EXECUTE DBMS_WM.CreateWorkspace ('NEWWORKSPACE');
      EXECUTE dbms_wm.createworkspace ('NEWWORKSPACE');
      EXECUTE dBms_Wm.cReatEwoRksPace ('NEWWORKSPACE');

**Note:**

When executing a DBMS_WM procedure from another procedure, the privilege checks take into account whether the procedure has definer's rights or the rights of the database user whose privileges are currently active.

- Add_Topo_Geometry_Layer
- AddAsParentWorkspace
- AddUserDefinedHint
- AlterSavepoint
- AlterVersionedTable
- AlterWorkspace
- BeginBulkLoading
- BeginDDL
- BeginResolve
- ChangeWorkspaceType
- CommitBulkLoading
- CommitDDL
- CommitResolve
- CompressWorkspace
- CompressWorkspaceTree
- CopyForUpdate
- CopyWorkspace
- CreateSavepoint
- CreateWorkspace
- Delete_Topo_Geometry_Layer
- DeleteSavepoint
- DisableVersioning
- EnableVersioning
- Export
- Export_Schemas
- FindRICSet
- FreezeWorkspace
- GetBulkLoadVersion
- GetConflictWorkspace
- GetDiffVersions
- GetLockMode
- GetMultiWorkspaces
- GetOpContext
- GetOriginalDDL
- GetPhysicalTableName
- GetPrivs
- GetSessionInfo
- GetSystemParameter
- GetValidFrom
- GetValidTill
- GetVersion
- GetWMMetadataSpace
- GetWorkspace
- GotoDate
- GotoSavepoint
- GotoWorkspace
- GrantGraphPriv
- GrantPrivsOnPolicy
- GrantSystemPriv
- GrantWorkspacePriv
- Import
- Import_Schemas
- Initialize_After_Import
- IsWorkspaceOccupied
- LockRows
- MergeTable
- MergeWorkspace
- Move_Proc
- PurgeTable
- RecoverAllMigratingTables
- RecoverFromDroppedUser
- RecoverMigratingTable
- RefreshTable
- RefreshWorkspace
- RemoveAsParentWorkspace
- RemoveDeferredWorkspaces
- RemoveUserDefinedHint
- RemoveWorkspace
- RemoveWorkspaceTree
- RenameSavepoint
- RenameWorkspace
- ResolveConflicts
- RevokeGraphPriv
- RevokeSystemPriv
- RevokeWorkspacePriv
- RollbackBulkLoading
- RollbackDDL
- RollbackResolve
- RollbackTable
- RollbackToSP
- RollbackWorkspace
- SetCaptureEvent
- SetCompressWorkspace
- SetConflictWorkspace
- SetDiffVersions
- SetLockingOFF
- SetLockingON
- SetMultiWorkspaces
- SetSystemParameter
- SetTriggerEvents
- SetValidTime
- SetValidTimeFilterOFF
- SetValidTimeFilterON
- SetWMValidUpdateModeOFF
- SetWMValidUpdateModeON
- SetWoOverwriteOFF
- SetWoOverwriteON
- SetWorkspaceLockModeOFF
- SetWorkspaceLockModeON
- UnfreezeWorkspace
- UnlockRows
- UseDefaultValuesForNulls

**Parent topic:** [Reference Information](workspace-manager-reference.md)

### 4.1 Add_Topo_Geometry_Layer

Adds a topology geometry layer from a version-enabled feature table to a topology.

#### Format

    DBMS_WM.Add_Topo_Geometry_Layer(     
      topology        IN VARCHAR2,      
      table_name      IN VARCHAR2,      
      column_name     IN VARCHAR2,      
      tg_layer_type   IN VARCHAR2);

#### Parameters

Table 4-1 Add_Topo_Geometry_Layer Procedure Parameters

| Parameter       | Description                                                                                                                                                                                        |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topology`      | Topology to which to add the topology geometry layer containing the topology geometries in the specified column. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure. |
| `table_name`    | Name of the topology geometry layer table containing the column specified in `column_name`.                                                                                                        |
| `column_name`   | Name of the column (of type `SDO_TOPO_GEOMETRY`) containing the topology geometries in the topology geometry layer to be added to the topology.                                                    |
| `tg_layer_type` | Type of topology geometry layer: `POINT`, `LINE`, `CURVE`, or `POLYGON`.                                                                                                                           |

#### Usage Notes

This procedure has the same format and meaning as the SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER procedure, which is documented in [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/SDO_TOPO-reference.md). However, you must use DBMS_WM.Add_Topo_Geometry_Layer, and not SDO_TOPO.ADD_TOPO_GEOMETRY_LAYER, to add a topology geometry layer from a version-enabled feature table to a topology. For information about Workspace Manager support for topologies, see [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).

The first call to this procedure for a given topology creates the \<topology-name\>\_RELATION\$ table, which is described in [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/topology-data-model-overview.md).

An exception is raised if `topology`, `table_name`, or `column_name` does not exist, if `topology` or `table_name` is not version-enabled, or if `tg_layer_type` is not one of the supported values.

#### Examples

The following example adds a topology geometry layer to the `CITY_DATA` topology. The topology geometry layer consists of polygon geometries in the `FEATURE` column of the `LAND_PARCELS` table.

    EXECUTE DBMS_WM.Add_Topo_Geometry_Layer('CITY_DATA', 'LAND_PARCELS', 'FEATURE', 'POLYGON');

**Parent topic:** DBMS_WM Package: Reference

### 4.2 AddAsParentWorkspace

Adds a workspace as a parent workspace to a child workspace in a multiparent workspace environment.

#### Syntax

    DBMS_WM.AddAsParentWorkspace(
       workspace         IN VARCHAR2,
       parent_workspace  IN VARCHAR2,
       auto_commit       IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-2 AddAsParentWorkspace Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`        | Name of the workspace to which to add the parent workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `parent_workspace` | Name of the workspace to add as a parent workspace of `workspace`. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `auto_commit`      | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

This procedure is part of the support for the multiparent workspaces feature, which is described in [Multiparent Workspaces](introduction-to-workspace-manager.md). If `workspace` has only one parent workspace, this procedure makes `workspace` a multiparent workspace. If `workspace` is already a multiparent workspace, this procedure adds another parent workspace to `workspace`.

An exception is raised if one or more of the following apply:

- The value of the Workspace Manager system parameter `ALLOW_MULTI_PARENT_WORKSPACES` is `OFF`.

- The value of the Workspace Manager system parameter `CR_WORKSPACE_MODE` or `NONR_WORKSPACE_MODE` (whichever is applicable, depending on whether or not `workspace` is a continually refreshed workspace) is `OPTIMISTIC_LOCKING`.

- `workspace` or `parent_workspace` does not exist.

- `parent_workspace` is already in the ancestor hierarchy of `workspace`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- There is a violation of a primary key constraint, referential integrity constraint, or unique constraint in the view of the data in a version-enabled table in `workspace`.

#### Examples

The following example adds `Workspace4` as a parent workspace of `Workspace3`. (See the hierarchy illustration in [Multiparent Workspaces](introduction-to-workspace-manager.md).)

    -- Allow multiparent workspaces. (Required for AddAsParentWorkspace)
    EXECUTE DBMS_WM.SetSystemParameter ('ALLOW_MULTI_PARENT_WORKSPACES', 'ON');
    -- Make Workspace3 multiparent by adding Workspace4 as a parent.
    EXECUTE DBMS_WM.AddAsParentWorkspace ('Workspace3', 'Workspace4');

**Parent topic:** DBMS_WM Package: Reference

### 4.3 AddUserDefinedHint

Adds a user-defined hint: that is, modifies (and thus overrides) a default optimizer hint, with the goal of improving the performance of SQL statements executed by the DBMS_WM package on a specified version-enabled table or all version-enabled tables.

#### Syntax

    DBMS_WM.AddUserDefinedHint(
       hint_id   IN NUMBER,
       table_id  IN VARCHAR2 DEFAULT NULL,
       hint      IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table 4-3 AddUserDefinedHint Procedure Parameters

| Parameter  | Description                                                                                                                                                                                         |
|:-----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `hint_id`  | Numeric ID that uniquely identifies the user-defined hint. Must match an existing hint ID used by Workspace Manager for one or more SQL statements.                                                 |
| `table_id` | Name of the table to which to apply the hint. The name is not case-sensitive. If this value is null, the hint is used with all version-enabled tables for any SQL statements that specify the hint. |
| `hint`     | The text of the optimizer hint. For an explanation of optimizer hints, see the chapter about using optimizer hints in [Oracle Database SQL Tuning Guide](../tgsql/influencing-the-optimizer.md).    |

#### Usage Notes

Use this procedure only if you are dissatisfied with the performance of any DBMS_WM package operations, and if you know how to use application tracing and SQL optimizer hints. For information about tracing, see the chapter about application tracing tools in [Oracle Database SQL Tuning Guide](../tgsql/performing-application-tracing.md).

In the trace output, any SQL statements using the DBMS_WM package that allow a user-defined hint include one or more comments in the following format:

    /* WM$SQL (hint_id) (table_id) */

If you have identified a statement that is performing poorly, and if you know an optimizer hint that will improve performance, you can use the `AddUserDefinedHint` procedure to specify the hint that should be used for the specified hint ID. You can also indicate whether to use the specified hint associated with the hint ID only for a specified table, or for all tables.

If you specify the `table_id` parameter, the specified hint will be used only when SQL statements that use the hint ID access the specified table, and the default Workspace Manager-supplied hint will be used with other tables. If the `table_id` parameter is null, the specified hint will be used when any DBMS_WM statement use the hint ID.

If the `hint` parameter specifies an object name (such as an index name), the `table_id` parameter must not be null.

Any table aliases can be used within user-defined hints; however, standard scoping rules still apply.

To remove a user-defined hint (that is, to cause the default hint associated with a hint ID to be used), use the RemoveUserDefinedHint procedure.

#### Examples

The following example specifies a full table scan on the TABLE1 table and any associated Workspace Manager infrastructure tables when a SQL statement specifies hint ID 1101 with the SCOTT.TABLE1 table.

    EXECUTE DBMS_WM.AddUSerDefinedHint (1101, 'scott.table1', 'full(t1)');

**Parent topic:** DBMS_WM Package: Reference

### 4.4 AlterSavepoint

Modifies the description of a savepoint.

#### Syntax

    DBMS_WM.AlterSavepoint(
       workspace      IN VARCHAR2,
       sp_name        IN VARCHAR2,
       sp_description IN VARCHAR2);

#### Parameters

Table 4-4 AlterSavepoint Procedure Parameters

| Parameter        | Description                                                                           |
|:-----------------|:--------------------------------------------------------------------------------------|
| `workspace`      | Name of the workspace in which the savepoint was created. The name is case-sensitive. |
| `sp_name`        | Name of the savepoint. The name is case-sensitive.                                    |
| `sp_description` | Description of the savepoint.                                                         |

#### Usage Notes

To see the current description of the savepoint, examine the `DESCRIPTION` column value for the savepoint in the [ALL_WORKSPACE_SAVEPOINTS](workspace-manager-views.md) metadata view, which is described in [ALL_WORKSPACE_SAVEPOINTS](workspace-manager-views.md).

An exception is raised if the user is not the workspace owner or savepoint owner or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example modifies the description of savepoint `SP1` in the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.AlterSavepoint ('NEWWORKSPACE', 'SP1', 'First set of changes for scenario');

**Parent topic:** DBMS_WM Package: Reference

### 4.5 AlterVersionedTable

Alters a version-enabled table to add valid time support, rename a constraint, or rename an index.

#### Syntax

    DBMS_WM.AlterVersionedTable(
       table_name         IN VARCHAR2,
       alter_option       IN VARCHAR2,
       parameter_options  IN VARCHAR2 DEFAULT NULL,
       ignore_last_error  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-5 AlterVersionedTable Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`        | Name of the version-enabled table to which to add valid time support. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `alter_option`      | One of the following values: `ADD_VALID_TIME` to add valid time support, `DDL` to make DDL changes, `RENAME_CONSTRAINT` to rename a constraint, `REBUILD_INDEX` to rebuild an index, `RENAME_INDEX` to rename an index, or either `USE_SCALAR_TYPES_FOR_VALIDTIME` or `USE_WM_PERIOD_FOR_VALIDTIME` to specify whether views on an existing version-enabled table should use two scalar columns for the valid time range.<br>See the Usage Notes for information about these options, including when you must and can use this procedure to rename an index or a constraint.                                                                   |
| `parameter_options` | A quoted string (in the general format 'keyword=value, keyword2=value2, ...') containing keywords valid for the specified `alter_option` parameter value. See the Usage Notes for keywords that are valid for each `alter_option` parameter value.                                                                                                                                                                                                                                                                                                                                                                                             |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the AlterVersionedTable procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the AlterVersionedTable procedure. |

#### Usage Notes

Use this procedure to add valid time support, rename a constraint, or rename an index for an existing version-enabled table. For more information about adding valid time support, see [Adding Valid Time Support to an Existing Table](valid-time-support.md).

If the `alter_option` value is `ADD_VALID_TIME`, you can specify none, one, or more of the following `parameter_options` keywords:

- `validFrom`: Starting time period to be set in the WM_VALID column of all existing rows. The default value is the current timestamp.

- `validTill`: Ending time period to be set in the WM_VALID column of all existing rows. The default value is `UNTIL_CHANGED`.

- `fmt`: Date format. The default value is `'mmddyyyyhh24miss'`. The options are the same as for the TO_TIMESTAMP_TZ function, which is described in [Oracle Database SQL Language Reference](../sqlrf/TO_TIMESTAMP_TZ.md).

- `nlsparam`: Globalization support options. The options and default are the same as for the `nlsparam` argument to the TO_CHAR function for date conversion, which is described in [Oracle Database SQL Language Reference](../sqlrf/TO_CHAR-datetime.md).

If the `alter_option` value is `DDL`, the currently supported operations for this procedure are adding, merging, and splitting table partitions. You must have SYSDBA privileges, and you must specify the following `parameter_options` keywords:

- `ddl`: The DDL (data definition language) statement to be executed. The DDL statement must refer to the fully qualified base table (for example, SCOTT.EMP_LT if SCOTT.EMP is the version-enabled table).

- `force`: A value of `true` causes Workspace Manager to attempt to execute the DDL statement, regardless of whether the operation is officially supported for this procedure; a value of `false` (the default) causes Workspace Manager not to attempt to execute the DDL statement. Thus, to execute the DDL statement, you must override the default value by explicitly specifying `'force=true'`; however, do not specify `'force=true'` unless you know what you are doing.

If the `alter_option` value is `RENAME_CONSTRAINT`, you must specify both of the following `parameter_options` keywords:

- `constraint_name`: The current name of the constraint to be renamed. The name is not case-sensitive.

- `new_constraint_name`: The new name for the constraint. The name is not case-sensitive.

If the `alter_option` value is `RENAME_INDEX`, you must specify all of the following `parameter_options` keywords:

- `index_owner`: The name of the schema that owns the index to be renamed. The schema name is not case-sensitive.

- `index_name`: The current name of the index to be renamed. The name is not case-sensitive.

- `new_index_name`: The new name for the index. The name is not case-sensitive.

If the name of a constraint or index on a version-enabled table is longer than 26 characters, you must use the AlterVersionedTable procedure if you want to rename the constraint or index; you cannot use the ALTER TABLE (for a constraint) or ALTER INDEX (for an index) statement with the RENAME clause. If you use the AlterVersionedTable procedure, you do not need to include it between calls to the BeginDDL and CommitDDL procedures.

If the name of the constraint or index on a version-enabled table is 26 or fewer characters long, you can do either of the following to rename the constraint or index: use the AlterVersionedTable procedure, or use the ALTER TABLE (for a constraint) or ALTER INDEX (for an index) statement with the RENAME clause between calls to the BeginDDL and CommitDDL procedures (as explained in [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md)).

If the `alter_option` value is `REBUILD_INDEX`, you must specify the `index_owner` and `index_name` keywords to identify the database user that owns the index and the name of the index; and you can specify either the `reverse` or `noreverse` keyword, to specify whether or not to store the bytes of the index block in reverse order, excluding the rowid.

The `alter_option` values `USE_SCALAR_TYPES_FOR_VALIDTIME` and `USE_WM_PERIOD_FOR_VALIDTIME` can be used only to change the views on an existing version-enabled table to be consistent with the current setting for the Workspace Manager system parameter `USE_SCALAR_TYPES_FOR_VALIDTIME` (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)). For example, if you set the Workspace Manager system parameter `USE_SCALAR_TYPES_FOR_VALIDTIME` to `ON`, but an existing version-enabled table named MYTABLE has views that use a single column named WM_VALID (of type `WM_PERIOD`) to indicate the valid time range, you can change the views on MY_TABLE to use two columns of type TIMESTAMP WITH TIME ZONE by calling the AlterVersionedTable procedure and specifying the `alter_option` value `USE_SCALAR_TYPES_FOR_VALIDTIME`.

The `alter_option` parameter cannot be used to override the current value of the Workspace Manager system parameter `USE_SCALAR_TYPES_FOR_VALIDTIME`. If the system parameter value is `ON`, the `alter_option` parameter value must be `USE_SCALAR_TYPES_FOR_VALIDTIME`; and if the system parameter value is `OFF`, the `alter_option` parameter value must be `USE_WM_PERIOD_FOR_VALIDTIME`.

You can use double quotation marks for parameter values within the `parameter_options` string. For example, the following two specifications are semantically identical:

    'index_owner=scott, index_name=my_index, new_index_name=my_new_index'
    'index_owner="scott", index_name="my_index", new_index_name="my_new_index"'

If a call to the AlterVersionedTable procedure fails, you should try to fix the cause of the error. Examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message. Fix the cause of the error, and then call the AlterVersionedTable procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you can ignore the error by calling the AlterVersionedTable procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

An exception is raised if one or more of the following apply:

- `table_name` does not exist.

- `alterOptions` is not `ADD_VALID_TIME`.

#### Examples

The following example creates a table named `MY_TABLE`, version-enables it without valid time support, and then adds valid time support. After valid time support is added, the `WM_VALID` column contains the default valid time period.

    CREATE TABLE my_table (id NUMBER PRIMARY KEY);
    EXECUTE DBMS_WM.EnableVersioning ('my_table');
    INSERT INTO my_table VALUES (1);
    SELECT * FROM my_table;

            ID
    ----------
             1

    EXECUTE DBMS_WM.AlterVersionedTable('my_table', 'ADD_VALID_TIME');
    SELECT * FROM my_table;

            ID
    ----------
    WM_VALID(VALIDFROM, VALIDTILL)
    --------------------------------------------------------------------------------
             1
    WM_PERIOD('09-JUN-2003 10:04:13 -04:00', NULL)

The following example creates a table named `SCOTT.MY_TABLE`, creates an index named `MY_INDEX` on the `VALUE` column in that table, version-enables the table, and then renames the index to `MY_NEW_INDEX`.

    CREATE TABLE scott.my_table (id NUMBER PRIMARY KEY, value INTEGER);
    CREATE INDEX scott.my_index on scott.my_table(value);
    EXECUTE DBMS_WM.EnableVersioning ('scott.my_table');
    EXECUTE DBMS_WM.AlterVersionedTable ('scott.my_table', 'RENAME_INDEX',
      'index_owner=scott, index_name=my_index, new_index_name=my_new_index');

**Parent topic:** DBMS_WM Package: Reference

### 4.6 AlterWorkspace

Modifies the description of a workspace.

#### Syntax

    DBMS_WM.AlterWorkspace(
       workspace              IN VARCHAR2,
       workspace_description  IN VARCHAR2);

#### Parameters

Table 4-6 AlterWorkspace Procedure Parameters

| Parameter               | Description                                        |
|:------------------------|:---------------------------------------------------|
| `workspace`             | Name of the workspace. The name is case-sensitive. |
| `workspace_description` | Description of the workspace.                      |

#### Usage Notes

To see the current description of the workspace, examine the `DESCRIPTION` column value for the savepoint in the [ALL_WORKSPACES](workspace-manager-views.md) metadata view, which is described in [ALL_WORKSPACES](workspace-manager-views.md).

An exception is raised if the user is not the workspace owner or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example modifies the description of the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.AlterWorkspace ('NEWWORKSPACE', 'Testing proposed scenario B');

**Parent topic:** DBMS_WM Package: Reference

### 4.7 BeginBulkLoading

Starts the bulk loading process for a version-enabled table.

#### Syntax

    DBMS_WM.BeginBulkLoading(
       table_name            IN VARCHAR2,
       workspace             IN VARCHAR2,
       version               IN INTEGER DEFAULT NULL,
       check_for_duplicates  IN BOOLEAN DEFAULT TRUE,
       ignore_last_error     IN BOOLEAN DEFAULT FALSE,
       single_transaction    IN BOOLEAN DEFAULT FALSE,
       savepoint_name        IN DEFAULT LATEST);

#### Parameters

Table 4-7 BeginBulkLoading Procedure Parameters

| Parameter              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`           | Name of the version-enabled table into which data will be bulk loaded. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `workspace`            | Name of the workspace in which bulk loading will be performed. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `version`              | (Ignored for the current release. Before Release 12.1, this was the version number returned by the GetBulkLoadVersion function.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `check_for_duplicates` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) checks for rows in the data to be bulk loaded that have the same values in primary key columns. For any duplicate records, only the record with the lowest ROWID value is kept in the table, and the rest are moved to the discards table specified in the call to the CommitBulkLoading procedure. See the Usage Notes for more information about this parameter.<br>`FALSE` does not check if any rows in the data to be bulk loaded have the same values in primary key columns.                                                                                                                                                                                                                         |
| `ignore_last_error`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the BeginBulkLoading procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the BeginBulkLoading procedure.                                                                                                                                 |
| `single_transaction`   | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes Workspace Manager not to perform an internal commit operation after each of several steps that it will perform after you call the CommitBulkLoading procedure, but instead to perform a commit only after it has performed all the necessary steps. `TRUE` also allows queries to be made on the version-enabled table.<br>`FALSE` (the default) causes Workspace Manager to perform an internal commit operation after each of several steps that it will perform after you call the CommitBulkLoading procedure, and it also disallows queries to be made on the table until a CommitBulkLoading or RollbackBulkLoading operation is complete.<br>See the Usage Notes for more information about this parameter. |
| `savepoint_name`       | The version in the workspace in which data will be bulk loaded. If specified, must be one of the following: `LATEST` or `ROOT_VERSION`.<br>`LATEST` (the default) is the current version in the workspace.<br>`ROOT_VERSION` is the root version (version number 0, which is in the `LIVE` workspace). The root version is the ancestor of all other versions, so data in the root version is visible from all other workspaces (unless non-`LIVE` workspaces have updated the data). You can specify `ROOT_VERSION` only if `workspace` is `LIVE`.                                                                                                                                                                                                                      |

#### Usage Notes

Before you can begin bulk loading data into a version-enabled table, you must call the BeginBulkLoading procedure. You must end the bulk loading session by calling either the CommitBulkLoading procedure (to commit changes made when the data was loaded) or the RollbackBulkLoading procedure (to roll back changes made when the data was loaded). For more information about bulk loading with Workspace Manager, see [Bulk Loading into Version-Enabled Tables](introduction-to-workspace-manager.md).

If `single_transaction` is `FALSE` (the default), the BeginBulkLoading procedure drops some internal Workspace Manager views on the table, to prevent DML operations and certain Workspace Manager operations on the table; however, this also prevents any queries from being made using the specified version-enabled table. Regardless of the `single_transaction` parameter value, and especially if it is `FALSE`, you should complete the bulk loading as quickly as possible and at a time when applications and users will not need to access the table. The value of the `single_transaction` parameter must be the same for both the BeginBulkLoading and CommitBulkLoading procedures for a bulk loading session with a specified table.

A `TRUE` value for the `check_for_duplicates` parameter does not cause any existing data in the version-enabled table to be checked. If an existing row in the version in which data is being bulk loaded (which could be the latest version of a workspace or the root version) has the same primary key values as a row in the data to be bulk loaded, the behavior depends on the history option setting for the table: if `VIEW_WO_OVERWRITE` is set, the newly loaded row is chained to the existing row that has the same primary key values; if `VIEW_WO_OVERWRITE` is not set, the new data is not bulk loaded but is instead moved to the discards table.

If a call to the BeginBulkLoading procedure fails, you should try to fix the cause of the error. Examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message. Fix the cause of the error, and then call the BeginBulkLoading procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the BeginBulkLoading procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

If performance is an issue, carefully consider whether or not you need to check for duplicate records, because a `check_for_duplicates` value of `TRUE` (the default) causes Workspace Manager to perform additional internal processing.

An exception is raised if one or more of the following apply:

- `table_name` does not exist.

- `table_name` is not version-enabled.

- The user does not own the table or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example starts the bulk load operation into the `EMP` table in the `W1` workspace.

    EXECUTE DBMS_WM.BeginBulkLoading ('EMP', 'W1');

**Parent topic:** DBMS_WM Package: Reference

### 4.8 BeginDDL

Starts a DDL (data definition language) session for a specified table.

#### Syntax

    DBMS_WM.BeginDDL(
       table_name  IN VARCHAR2);

#### Parameters

Table 4-8 BeginDDL Procedure Parameters

| Parameter    | Description                                                        |
|:-------------|:-------------------------------------------------------------------|
| `table_name` | Name of the version-enabled table. The name is not case-sensitive. |

#### Usage Notes

This procedure starts a DDL session, and it creates a special table whose name is the same as `table_name` but with \_LTS added to the table name. After calling this procedure, you can perform one or more DDL operations on the table or any indexes or triggers that are based on the table, and then call either the CommitDDL or RollbackDDL procedure.

In addition to creating the special \<table-name\>\_LTS table, the procedure creates other objects:

- The \<table-name\>\_LTS table has the same triggers, columns, and indexes as the \<table-name\> table.

- For each parent table with which the \<table-name\> table has a referential integrity constraint, the same constraint is defined for the \<table-name\>\_LTS table.

- Triggers, columns, and referential integrity constraints on the \<table-name\>\_LTS table have the same names as the corresponding ones on the \<table-name\> table.

- For each index on the \<table-name\> table, the corresponding index on the \<table-name\>\_LTS table has a name in the form \<index-name\>\_LTS.

- The primary key constraint on the \<table-name\>\_LTS table has a name in the form \<primary-key\>\_LTS.

- All unique constraints on the \<table-name\>\_LTS table have a name in the form \<unique-constraint-name\>\_LTS.

For detailed information about performing DDL operations related to version-enabled tables, see [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- `table_name` does not exist or is not version-enabled.

- `table_name` has a domain index defined on it, and the user has not been directly granted the `CREATE TABLE` and `CREATE SEQUENCE` privileges.

- An open DDL session exists for `table_name`. (That is, the BeginDDL procedure has already been called specifying this table, and the CommitDDL or RollbackDDL procedure has not been called specifying this table.)

#### Examples

The following example begins a DDL session, adds a column named `COMMENTS` to the `COLA_MARKETING_BUDGET` table by using the special table named `COLA_MARKETING_BUDGET_LTS`, and ends the DDL session by committing the change.

    EXECUTE DBMS_WM.BeginDDL('COLA_MARKETING_BUDGET');
    ALTER TABLE cola_marketing_budget_lts ADD (comments VARCHAR2(100));
    EXECUTE DBMS_WM.CommitDDL('COLA_MARKETING_BUDGET');

**Parent topic:** DBMS_WM Package: Reference

### 4.9 BeginResolve

Starts a conflict resolution session.

#### Syntax

    DBMS_WM.BeginResolve(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-9 BeginResolve Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

This procedure starts a conflict resolution session. While this procedure is executing, the workspace is frozen in `1WRITER` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

After calling this procedure, you can execute the ResolveConflicts procedure as needed for various tables that have conflicts, and then call either the CommitResolve or RollbackResolve procedure. For more information about conflict resolution, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- There are one or more open database transactions in `workspace`.

- The user executing the BeginResolve procedure does not have the privilege to access `workspace` and its parent workspace.

#### Examples

The following example starts a conflict resolution session in `Workspace1`.

    EXECUTE  DBMS_WM.BeginResolve ('Workspace1');

**Parent topic:** DBMS_WM Package: Reference

### 4.10 ChangeWorkspaceType

Changes a workspace from not continually refreshed to continually refreshed. (Continually refreshed workspaces are explained in [Continually Refreshed Workspaces](introduction-to-workspace-manager.md).)

#### Syntax

    DBMS_WM.ChangeWorkspaceType(
       workspace       IN VARCHAR2,
       workspace_type  IN VARCHAR2 DEFAULT DBMS_WM.CR_WORKSPACE_TYPE,
       auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-10 ChangeWorkspaceType Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`      | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `workspace_type` | Must be `DBMS_WM.CR_WORKSPACE_TYPE` (the default), for continually refreshed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `auto_commit`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

For this release, you can only change a workspace that is not continually refreshed to continually refreshed; you cannot change a continually refreshed workspace to not continually refreshed.

An exception is raised if one or more of the following occur:

- The user is not the owner of `workspace`, and the user does not have the `WM_ADMIN` system privilege.

- `workspace_type` is not valid.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The workspace type cannot be changed. For example, the change cannot be made if the Workspace Manager system parameter `CR_WORKSPACE_MODE` is set to `PESSIMISTIC_LOCKING`, but the `NONCR_WORKSPACE_MODE` parameter is set to `OPTIMISTIC_LOCKING` and there is versioned data in any continually refreshed workspace.

#### Examples

The following example changes the `NEWWORKSPACE` workspace type from not continually refreshed to continually refreshed.

    EXECUTE DBMS_WM.ChangeWorkspaceType ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.11 CommitBulkLoading

Ends the bulk loading process for a version-enabled table by committing the bulk load changes.

#### Syntax

    DBMS_WM.CommitBulkLoading(
       table_name            IN VARCHAR2,
       discards_table        IN VARCHAR2,
       check_for_duplicates  IN BOOLEAN DEFAULT TRUE,
       enforceUCFlag         IN BOOLEAN DEFAULT TRUE,
       enforceRICFlag        IN BOOLEAN DEFAULT TRUE,
       ignore_last_error     IN BOOLEAN DEFAULT FALSE,
       single_transaction    IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-11 CommitBulkLoading Procedure Parameters

| Parameter              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-----------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`           | Name of the version-enabled table into which data has been bulk loaded. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `discards_table`       | Name of the table into which discard records are inserted. The name is not case-sensitive. If the table does not already exist, it is created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `check_for_duplicates` | A Boolean value (`TRUE` or `FALSE`). Note: Effective with Release 12.1, this parameter is ignored; the value from the call to the BeginBulkLoading procedure is used.<br>`TRUE` (the default) checks for rows in the data to be bulk loaded that have the same values in primary key columns. For any duplicate records, only the record with the lowest ROWID value is kept in the table, and the rest are moved to the discards table. See the Usage Notes for more information about this parameter.<br>`FALSE` does not check if any rows in the data to be bulk loaded have the same values in primary key columns.                                                                                                                                              |
| `enforceUCFlag`        | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) enforces any unique constraints defined on `to_table`, ensuring that the bulk load operation does not violate any such constraints.<br>`FALSE` does not enforce any unique constraints defined on `to_table` for the bulk load operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `enforceRICFlag`       | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) enforces any referential integrity constraints defined on `to_table`, ensuring that the bulk load operation does not violate any such constraints.<br>`FALSE` does not enforce any referential integrity constraints defined on `to_table` for the bulk load operation.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `ignore_last_error`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the CommitBulkLoading procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the CommitBulkLoading procedure.                                                                                                                            |
| `single_transaction`   | A Boolean value (`TRUE` or `FALSE`). Note: Effective with Release 12.1, this parameter is ignored; the value from the call to the BeginBulkLoading procedure is used.<br>`TRUE` causes Workspace Manager not to perform an internal commit operation after each of several steps that it performs after you call the CommitBulkLoading procedure, but instead to perform a commit only after it has performed all the necessary steps.<br>`FALSE` (the default) causes Workspace Manager to perform an internal commit operation after each of several steps that it performs after you call the CommitBulkLoading procedure.<br>The value of this parameter must be the same as when you called the BeginBulkLoading procedure specifying the table in `table_name`. |

#### Usage Notes

For information about the requirements for bulk loading data into version-enabled tables, see [Bulk Loading into Version-Enabled Tables](introduction-to-workspace-manager.md).

This procedure generates versioning metadata for newly loaded data and synchronizes the newly loaded data with the existing versioned data in the table. It can also enforce unique and referential constraints on the newly loaded data. It re-creates all the views that were dropped by the BeginBulkLoading procedure.

A `TRUE` value for the `check_for_duplicates` parameter does not cause any existing data in the version-enabled table to be checked. If an existing row in the version in which data is being bulk loaded (which could be the latest version of a workspace or the root version) has the same primary key values as a row in the data to be bulk loaded, the behavior depends on the history option setting for the table: if `VIEW_WO_OVERWRITE` is set, the newly loaded row is chained to the existing row that has the same primary key values; if `VIEW_WO_OVERWRITE` is not set, the new data is not bulk loaded but is instead moved to the discards table.

If a call to the CommitBulkLoading procedure fails, you should try to fix the cause of the error. Examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message. Fix the cause of the error, and then call the CommitBulkLoading procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the CommitBulkLoading procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

Note the following performance considerations:

- A `TRUE` value for `check_for_duplicates` requires additional processing time, and a `TRUE` value for `enforceUCFlag` or `enforceRICFlag` may require additional processing time.

- If performance is an issue, carefully consider whether or not you need to check for duplicate records.

- If the table does not have unique or referential constraints, setting the `enforceUCFlag` or `enforceRICFlag` parameter to `TRUE` does not have a significant effect on performance.

An exception is raised if one or more of the following apply:

- `table_name` does not exist.

- `table_name` is not version-enabled.

- The BeginBulkLoading procedure has not been called on the table.

- The user does not own the table or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example commits changes made to the `EMP` table during a bulk load operation, and specifies `DISCARDS` as the table to hold discard records.

    EXECUTE DBMS_WM.CommitBulkLoading ('EMP', 'DISCARDS');

**Parent topic:** DBMS_WM Package: Reference

### 4.12 CommitDDL

Commits DDL (data definition language) changes made during a DDL session for a specified table, and ends the DDL session.

#### Syntax

    DBMS_WM.CommitDDL(
       table_name                  IN VARCHAR2,
       ignore_last_error           IN BOOLEAN DEFAULT FALSE,
       enforce_unique_constraints  IN BOOLEAN DEFAULT FALSE,
       enforce_RICs                IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-12 CommitDDL Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`                 | Name of the version-enabled table. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ignore_last_error`          | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the CommitDDL procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the CommitDDL procedure. |
| `enforce_unique_constraints` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` enforces any unique constraints defined on `table_name` on existing versioned data in the table. This ensures that the DDL changes do not cause any such constraints to be violated, but it causes Workspace Manager to take additional time to perform the operation.<br>`FALSE` (the default) does not enforce any unique constraints defined on `table_name` on existing versioned data in the table.                                                                                                                                                                    |
| `enforce_RICs`               | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` enforces any referential integrity constraints defined on `table_name` on existing versioned data in the table. This ensures that the changes do not cause any such constraints to be violated, but it causes Workspace Manager to take additional time to perform the operation.<br>`FALSE` (the default) does not enforce any referential integrity constraints defined on `table_name` on existing versioned data in the table.                                                                                                                                          |

#### Usage Notes

This procedure commits changes that were made to a version-enabled table and to any indexes, triggers, and referential integrity constraints based on the version-enabled table during a DDL session. It also deletes the special \<table-name\>\_LTS table that was created by the BeginDDL procedure.

For detailed information about performing DDL operations related to version-enabled tables, see [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md).

The `enforce_unique_constraints` and `enforce_RICs` parameter settings apply only to existing versioned data, and do not affect whether or not existing constraints are enforced for future DML operations on the table.

If a call to the CommitDDL procedure fails, the table is left in an inconsistent state. If this occurs, you should try to fix the cause of the error. Examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message. For example, the CommitDDL procedure might have failed because the tablespace was not large enough to add a column. Fix the cause of the error, and then call the CommitDDL procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the CommitDDL procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

An exception is raised if one or more of the following apply:

- `table_name` does not exist or is not version-enabled.

- `table_name` has a domain index defined on it, and the user has not been directly granted the `CREATE TABLE` and `CREATE SEQUENCE` privileges.

- An open DDL session does not exist for `table_name`. (That is, the BeginDDL procedure has not been called specifying this table, or the CommitDDL or RollbackDDL procedure was already called specifying this table.)

Some invalid DDL operations also cause an exception when CommitDDL procedure is called. See [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md) for information about DDL operations that are supported.

#### Examples

The following example begins a DDL session, adds a column named `COMMENTS` to the `COLA_MARKETING_BUDGET` table by using the special table named `COLA_MARKETING_BUDGET_LTS`, and ends the DDL session by committing the change.

    EXECUTE DBMS_WM.BeginDDL('COLA_MARKETING_BUDGET');
    ALTER TABLE cola_marketing_budget_lts ADD (comments VARCHAR2(100));
    EXECUTE DBMS_WM.CommitDDL('COLA_MARKETING_BUDGET');

**Parent topic:** DBMS_WM Package: Reference

### 4.13 CommitResolve

Ends a conflict resolution session and saves (makes permanent) any changes in the workspace since the BeginResolve procedure was executed.

#### Syntax

    DBMS_WM.CommitResolve(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-13 CommitResolve Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

This procedure ends the current conflict resolution session (started by the BeginResolve procedure), and saves all changes in the workspace since the start of the conflict resolution session. Contrast this procedure with the RollbackResolve procedure, which discards all changes.

For more information about conflict resolution, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- There are one or more open database transactions in `workspace`.

- The procedure was called by a user that does not have the `WM_ADMIN` system privilege or that did not execute the BeginResolve procedure on `workspace`.

#### Examples

The following example ends the conflict resolution session in `Workspace1` and saves all changes.

    EXECUTE  DBMS_WM.CommitResolve ('Workspace1');

**Parent topic:** DBMS_WM Package: Reference

### 4.14 CompressWorkspace

Deletes removable savepoints in a workspace and minimizes the Workspace Manager metadata structures for the workspace. (Removable savepoints are explained in [Using Savepoints](introduction-to-workspace-manager.md).)

#### Syntax

    DBMS_WM.CompressWorkspace(
       workspace                   IN VARCHAR2,
       compress_view_wo_overwrite  IN BOOLEAN
       firstSP                     IN VARCHAR2 DEFAULT NULL,
       secondSP                    IN VARCHAR2 DEFAULT NULL,
       auto_commit                 IN BOOLEAN DEFAULT TRUE,
       commit_in_batches           IN BOOLEAN DEFAULT FALSE,
       batch_size                  IN VARCHAR2 DEFAULT 'PRIMARY_KEY_RANGE',
       remove_latest_deleted_rows  IN BOOLEAN DEFAULT FALSE);

or

    DBMS_WM.CompressWorkspace(
       workspace          IN VARCHAR2,
       firstSP            IN VARCHAR2 DEFAULT NULL,
       secondSP           IN VARCHAR2 DEFAULT NULL,
       auto_commit        IN BOOLEAN DEFAULT TRUE,
       commit_in_batches  IN BOOLEAN DEFAULT FALSE,
       batch_size         IN VARCHAR2 DEFAULT 'PRIMARY_KEY_RANGE',
       remove_latest_deleted_rows  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-14 CompressWorkspace Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`                  | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `compress_view_wo_overwrite` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes history information between the affected savepoints to be deleted even if `VIEW_WO_OVERWRITE` was specified when versioning was enabled.<br>`FALSE` causes history information (between the affected savepoints) for a table not to be deleted if `VIEW_WO_OVERWRITE` was specified when versioning was enabled. (If `VIEW_WO_OVERWRITE` was not specified for a table, history information for the table is deleted regardless of the parameter value.) `FALSE` is assumed if the procedure format without this parameter is used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `firstSP`                    | First savepoint. Savepoint names are case-sensitive.<br>If only `workspace` and `firstSP` are specified, all removable savepoints between workspace creation and `firstSP` (but not including `firstSP`) are deleted.<br>If `workspace`, `firstSP`, and `secondSP` are specified, all removable savepoints from `firstSP` (and including `firstSP` if it is a removable savepoint) to `secondSP` (but not including `secondSP`) are deleted.<br>If only `workspace` is specified (no savepoints), all removable savepoints in the workspace are deleted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `secondSP`                   | Second savepoint. All removable savepoints from `firstSP` (and including `firstSP` if it is a removable savepoint) to `secondSP` (but not including `secondSP`) are deleted.<br>However, if `secondSP` is `LATEST`, all removable savepoints from `firstSP` (and including `firstSP` if it is a removable savepoint) to the end of the workspace are deleted.<br>Savepoint names are case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `auto_commit`                | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `commit_in_batches`          | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes an internal commit operation to be performed after compression operations on `batch_size` rows in version-enabled tables. Periodic commit operations can be useful or necessary if version-enabled tables have many rows affected by the compression, which can cause substantial Oracle database resources (such as rollback segments and undo tablespaces) to be used. If you specify `TRUE`, the `auto_commit` value must also be `TRUE`.<br>`FALSE` (the default) causes internal commit operations not to be performed during the compression operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `batch_size`                 | Batch size for internal commit operations if `commit_in_batches` is `TRUE`; otherwise, the parameter is ignored. If specified, must be `TABLE` or `PRIMARY_KEY_RANGE`.<br>`TABLE` causes an internal commit operation to be performed after compressing each version-enabled table that needs to be compressed.<br>`PRIMARY_KEY_RANGE` specifies that each table is divided into batches of different ranges of primary key values, and an internal commit operation is to be performed after compressing each batch of rows in each version-enabled table that needs to be compressed. You must previously have generated statistics on the first column of the primary key, such as by using the DBMS_STATS.GATHER_TABLE_STATS procedure on the \<table_name\>\_LT table associated with each affected version-enabled table. See the Usage Notes for more information. The following example generates histogram statistics:<br>`EXECUTE DBMS_STATS.GATHER_TABLE_STATS('', 'cola_marketing_budget_lt', estimate_percent=>50, method_opt=>'FOR COLUMNS SIZE 50 product_id');` |
| `remove_latest_deleted_rows` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes any `LATEST` row that has been deleted and that will not adversely affect conflict resolution to be removed, if `workspace` is `LIVE`. A value of `TRUE` is ignored for other workspaces.)<br>`FALSE` (the default) causes any `LATEST` row that has been deleted to be preserved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

#### Usage Notes

You can compress a workspace when the explicit savepoints (all or some of them) in the workspace are no longer needed. The compression operation is useful for the following reasons:

- You can reuse savepoint names after they are deleted. (You cannot create a savepoint that has the same name as an existing savepoint.)

- Less disk storage is used for Workspace Manager structures (fewer table rows, smaller indexes, less Workspace Manager metadata).

- Because of the reduction in disk space usage, runtime performance for Workspace Manager operations is improved.

This procedure deletes implicit savepoints only if they do not have any child dependencies, and the existence of any such non-removable savepoints will not allow the entire range to be compressed as a single unit. However, you can remove or move such savepoints by using the RemoveWorkspace or RefreshWorkspace procedure, respectively.

While this procedure is executing, the current workspace is frozen in `NO_ACCESS` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

A workspace cannot be compressed if there are any sessions in the workspace (except for the `LIVE` workspace), or if any user has executed a GotoDate operation or a GotoSavepoint operation specifying a savepoint in the workspace.

If the procedure format without the `compress_view_wo_overwrite` parameter is used, a value of `FALSE` is assumed for the parameter.

For information about `VIEW_WO_OVERWRITE` and other history options, see the information about the EnableVersioning procedure.

If you expect to purge a subset of your historical data periodically, such as removing historical data older than one year, plan to create a savepoint at each expected deletion point on the day it occurs. For example, if you plan to purge 2005 historical data when it is a year old, you need to create a savepoint on January 1, 2006. Then, on January 1, 2007 you can call the CompressWorkspace procedure, specifying the workspace name and the January 1, 2006 savepoint, to delete all history that occurred before 2006.

To see if a version-enabled table can be compressed in primary key range batches, check the value of the `BATCH_SIZE` column in the [WM_COMPRESS_BATCH_SIZES](workspace-manager-views.md) metadata view, which is described in [WM_COMPRESS_BATCH_SIZES](workspace-manager-views.md).

To specify a `batch_size` value of `PRIMARY_KEY_RANGE`, you must first generate either histogram statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, `TIMESTAMP`, `CHAR`, or `VARCHAR2`) or general statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`) on the first column of the primary key. The procedure DBMS_STATS.GATHER_TABLE_STATS generates general statistics. If general but not histogram statistics are available for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`, the Workspace Manager system parameter `NUMBER_OF_COMPRESS_BATCHES` is used to compute the number of batches when `batch_size` is specified as `PRIMARY_KEY_RANGE`. For more information about statistics, see [Oracle Database Performance Tuning Guide](../tgdba/measuring-database-performance.md).

If the current version within the specified workspace needs to be compressed, Workspace Manager attempts to acquire a Shared Sub eXclusive lock of the workspace. If the lock is not acquired, no error is raised, but the current version is not compressed. (See [Locks Taken for Workspace Manager Operations](introduction-to-workspace-manager.md).)

An exception is raised if `auto_commit` is `TRUE` and an open transaction exists, if the user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers), or if the user does not have the privilege to access and merge changes in `workspace`.

To compress a workspace and all its descendant workspaces, use the CompressWorkspaceTree procedure.

#### Examples

The following example compresses `NEWWORKSPACE`.

    EXECUTE DBMS_WM.CompressWorkspace ('NEWWORKSPACE');

The following example compresses `NEWWORKSPACE`, deleting all explicit savepoints between the creation of the workspace and the savepoint `SP1`.

    EXECUTE DBMS_WM.CompressWorkspace ('NEWWORKSPACE', 'SP1');

The following example compresses `NEWWORKSPACE`, deleting the explicit savepoint `SP1` and all explicit savepoints up to but not including `SP2`.

    EXECUTE DBMS_WM.CompressWorkspace ('NEWWORKSPACE', 'SP1', 'SP2');

The following example compresses `B_focus_1`, accepts the default values for the `firstSP` and `secondSP` parameters (that is, deletes all explicit savepoints), and specifies `FALSE` for the `auto_commit` parameter.

    EXECUTE DBMS_WM.CompressWorkspace ('B_focus_1', auto_commit => FALSE);

The following example analyzes the `COLA_MARKETING_BUDGET_LT` table to generate the necessary histogram statistics for the next statement, and then it compresses `B_focus_1`. The call to the `CompressWorkspace` procedure accepts the default values for the `firstSP`, `secondSP`, and `auto_commit` parameters; specifies `TRUE` for the `commit_in_batches` parameter; and specifies `PRIMARY_KEY_RANGE` for the `batch_size` parameter.

    EXECUTE DBMS_STATS.GATHER_TABLE_STATS('', 'cola_marketing_budget_lt', estimate_percent=>50, method_opt=>'FOR COLUMNS SIZE 50 product_id');
    EXECUTE DBMS_WM.CompressWorkspace ('B_focus_1', NULL, NULL, NULL, TRUE, 'PRIMARY_KEY_RANGE');

**Parent topic:** DBMS_WM Package: Reference

### 4.15 CompressWorkspaceTree

Deletes removable savepoints in a workspace and all its descendant workspaces. (Removable savepoints are explained in [Using Savepoints](introduction-to-workspace-manager.md).) It also minimizes the Workspace Manager metadata structures for the affected workspaces, and eliminates any redundant data that might arise from the deletion of the savepoints.

#### Syntax

    DBMS_WM.CompressWorkspaceTree(
       workspace                   IN VARCHAR2,
       compress_view_wo_overwrite  IN BOOLEAN DEFAULT FALSE,
       auto_commit                 IN BOOLEAN DEFAULT TRUE,
       commit_in_batches           IN BOOLEAN DEFAULT FALSE,
       batch_size                  IN VARCHAR2 DEFAULT 'PRIMARY_KEY_RANGE',
       remove_latest_deleted_rows  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-15 CompressWorkspaceTree Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`                  | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `compress_view_wo_overwrite` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes history information to be deleted even if `VIEW_WO_OVERWRITE` was specified when versioning was enabled.<br>`FALSE` (the default) causes history information for a table not to be deleted if `VIEW_WO_OVERWRITE` was specified when versioning was enabled. (If `VIEW_WO_OVERWRITE` was not specified for a table, history information for the table is deleted regardless of the parameter value.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `auto_commit`                | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `commit_in_batches`          | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes an internal commit operation to be performed after compression operations on `batch_size` rows in version-enabled tables. Periodic commit operations can be useful or necessary if version-enabled tables have many rows affected by the compression, which can cause substantial Oracle database resources (such as rollback segments and undo tablespaces) to be used. If you specify `TRUE`, the `auto_commit` value must also be `TRUE`.<br>`FALSE` (the default) causes internal commit operations not to be performed during the compression operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `batch_size`                 | Batch size for internal commit operations if `commit_in_batches` is `TRUE`; otherwise, the parameter is ignored. If specified, must be `TABLE` or `PRIMARY_KEY_RANGE`.<br>`TABLE` causes an internal commit operation to be performed after compressing each version-enabled table that needs to be compressed.<br>`PRIMARY_KEY_RANGE` specifies that each table is divided into batches of different ranges of primary key values, and an internal commit operation is to be performed after compressing each batch of rows in each version-enabled table that needs to be compressed. You must previously have generated statistics on the first column of the primary key, such as by using the DBMS_STATS.GATHER_TABLE_STATS procedure on the \<table_name\>\_LT table associated with each affected version-enabled table. See the Usage Notes for more information. The following example generates histogram statistics:<br>`EXECUTE DBMS_STATS.GATHER_TABLE_STATS('', 'cola_marketing_budget_lt', estimate_percent=>50, method_opt=>'FOR COLUMNS SIZE 50 product_id');` |
| `remove_latest_deleted_rows` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes any `LATEST` row that has been deleted and that will not adversely affect conflict resolution to be removed, if `workspace` is `LIVE`. A value of `TRUE` is ignored for other values of the `workspace` parameter.)<br>`FALSE` (the default) causes any `LATEST` row that has been deleted to be preserved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

#### Usage Notes

You can compress a workspace and all its descendant workspaces when the explicit savepoints in the affected workspaces are no longer needed (for example, if you will not need to go to or roll back to any of these savepoints). For example, in the hierarchy shown in [Workspace Hierarchy](introduction-to-workspace-manager.md), a CompressWorkspaceTree operation specifying Workspace1 compresses Workspace1, Workspace2, and Workspace3. (For an explanation of database workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).)

The compression operation is useful for the following reasons:

- You can reuse savepoint names after they are deleted. (You cannot create a savepoint that has the same name as an existing savepoint.)

- Runtime performance for Workspace Manager operations is improved.

- Less disk storage is used for Workspace Manager structures.

While this procedure is executing, the current workspace is frozen in `NO_ACCESS` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

A workspace cannot be compressed if there are any sessions in the workspace (except for the `LIVE` workspace), or if any user has executed a GotoDate operation or a GotoSavepoint operation specifying a savepoint in the workspace.

To see if a version-enabled table can be compressed in primary key range batches, check the value of the `BATCH_SIZE` column in the [WM_COMPRESS_BATCH_SIZES](workspace-manager-views.md) metadata view, which is described in [WM_COMPRESS_BATCH_SIZES](workspace-manager-views.md).

To specify a `batch_size` value of `PRIMARY_KEY_RANGE`, you must first generate either histogram statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, `TIMESTAMP`, `CHAR,` or `VARCHAR2`) or general statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`) on the first column of the primary key. The procedure DBMS_STATS.GATHER_TABLE_STATS generates general statistics. If general but not histogram statistics are available for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`, the Workspace Manager system parameter `NUMBER_OF_COMPRESS_BATCHES` is used to compute the number of batches when `batch_size` is specified as `PRIMARY_KEY_RANGE`. For more information about statistics, see [Oracle Database Performance Tuning Guide](../tgdba/measuring-database-performance.md).

An exception is raised if `auto_commit` is `TRUE` and an open transaction exists, if the user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers), or if the user does not have the privilege to access and merge changes in `workspace`.

If the CompressWorkspaceTree operation fails in any affected workspace, the entire operation is rolled back, and no workspaces are compressed.

When the current version within any affected workspace is contained in a compressible range with at least one other version,  an attempt is made to acquire a Shared Sub eXclusive lock on that workspace. If it fails to be acquired, no error is raised, but the current version is not compressed. (See [Locks Taken for Workspace Manager Operations](introduction-to-workspace-manager.md).)

To compress a single workspace (deleting all explicit savepoints or just some of them), use the CompressWorkspace procedure.

#### Examples

The following example compresses `NEWWORKSPACE` and all its descendant workspaces.

    EXECUTE DBMS_WM.CompressWorkspaceTree ('NEWWORKSPACE');

The following example compresses `NEWWORKSPACE` and all its descendant workspaces, accepts the default value for the `compress_view_wo_overwrite` parameter, and specifies `FALSE` for the `auto_commit` parameter.

    EXECUTE DBMS_WM.CompressWorkspaceTree ('NEWWORKSPACE', auto_commit => FALSE);

The following example compresses `NEWWORKSPACE` and all its descendant workspaces; accepts the default value for the `compress_view_wo_overwrite` and `auto_commit` parameters; specifies `TRUE` for the `commit_in_batches` parameter; and specifies `PRIMARY_KEY_RANGE` for the `batch_size` parameter.

    EXECUTE DBMS_WM.CompressWorkspaceTree ('NEWWORKSPACE', NULL, NULL, TRUE, 'PRIMARY_KEY_RANGE');

**Parent topic:** DBMS_WM Package: Reference

### 4.16 CopyForUpdate

Allows LOB columns (BLOB, CLOB, or NCLOB) in version-enabled tables to be modified. Use this procedure only if a version-enabled table has any LOB columns.

#### Syntax

    DBMS_WM.CopyForUpdate(
       table_name    IN VARCHAR2,
       where_clause  IN VARCHAR2 DEFAULT '');

#### Parameters

Table 4-16 CopyForUpdate Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`   | Name of the table containing one or more LOB columns. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                |
| `where_clause` | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows affected. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `table_name` are affected. |

#### Usage Notes

This procedure is intended for use only with version-enabled tables containing one or more large object (LOB) columns. The CopyForUpdate procedure must be used because updates performed using the DBMS_LOB package do not fire `INSTEAD OF` triggers on the versioning views. Workspace Manager creates `INSTEAD OF` triggers on the versioning views to implement the copy-on-write semantics. (For non-LOB columns, you can directly perform the update operation, and the triggers work.)

#### Examples

The following example updates the `SOURCE_CLOB` column of `TABLE1` for the document with `DOC_ID = 1`.

      Declare
        clob_var
      Begin
         /* This procedure copies the LOB columns if necessary, that is,
            if the row with doc_id = 1 has not been versioned in the
            current version */
         dbms_wm.copyForUpdate('table1', 'doc_id = 1');

         select source_clob into clob_var
         from   table1
         where  doc_id = 1 for update;

         dbms_lob.write(clob_var,<amount>, <offset>, buff);

      End;

**Parent topic:** DBMS_WM Package: Reference

### 4.17 CopyWorkspace

Copies all of the rows modified in a specified workspace into a target workspace.

#### Syntax

    DBMS_WM.CopyWorkspace(
       source_workspace  IN VARCHAR2,
       target_workspace  IN VARCHAR2);

#### Parameters

Table 4-17 CopyWorkspace Procedure Parameters

| Parameter          | Description                                               |
|:-------------------|:----------------------------------------------------------|
| `source_workspace` | Name of the source workspace. The name is case-sensitive. |
| `target_workspace` | Name of the target workspace. The name is case-sensitive. |

#### Usage Notes

This procedure copies all of the rows that have been modified in the source workspace into the target workspace. Only tables that do not use the `validtime` option will be copied.  There is no conflict checking done between the two workspaces, so any rows that already exist in the target workspace will be overwritten. For each row that exits in the source workspace, the appropriate DML will be performed in the target workspace. For example, if a row was inserted into the source but the row already exists in the target, then the row in the target will be updated with the column values from the source. Or, if a row is updated in the source but the row was deleted in the target, then the row will be inserted into the target.

Once all of the rows are copied into the target workspace, all unique, check, and foreign key constraints will be enforced on the target workspace to ensure the data remains valid. If a constraint violation is found, an error will be raised and the operation will be rolled back.

If a row in the source has been locked in exclusive or shared mode, it will not be possible to copy the row into the target, and an error will be raised. Similarly, if the target workspace has a default lock mode set by previously having executed the SetWorkspaceLockModeON procedure, then an error will be raised in this case as well, due to the row already having been versioned. As a result, it is recommended not to have locking enabled, other than workspace-exclusive, on either the source or target workspaces. In addition, if the target workspace uses the pessimistic locking setting, then an error will be raised when attempting to copy the rows to the target workspace.

The changes to the target workspace are performed in the currently open transaction, or a new transaction is started if one does not yet exist.

An exception is raised if one or more of the following apply:

- The target and source workspace are the same workspace .

- The target or source workspace parameter is 'LIVE' .

- The target or source workspace parameter is NULL.

- The user does not have ACCESS privileges on both workspaces and all versioned tables that have been modified in the source workspace.

#### Examples

The following example copies any rows modified in the `child_1` workspace into `child_2`. Both workspace are child workspace of `LIVE`.

    EXECUTE DBMS_WM.CopyWorkspace('child_1', 'child_2');

**Parent topic:** DBMS_WM Package: Reference

### 4.18 CreateSavepoint

Creates a savepoint for the current version.

#### Syntax

    DBMS_WM.CreateSavepoint(
      workspace       IN VARCHAR2,
      savepoint_name  IN VARCHAR2,
      description     IN VARCHAR2 DEFAULT NULL,
      auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-18 CreateSavepoint Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`      | Name of the workspace in which to create the savepoint. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `savepoint_name` | Name of the savepoint to be created. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `description`    | Description of the savepoint to be created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `auto_commit`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

There are no explicit privileges associated with savepoints; any user who can access a workspace can create a savepoint in the workspace.

This procedure can be performed while there are users in the workspace. There can be open database transactions, but only if these transactions have not modified a versioned table.

While this procedure is executing, the current workspace is frozen in `READ_ONLY` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- The user is not in the latest version in the workspace (for example, if the user has called the GotoDate procedure).

- `workspace` does not exist.

- `savepoint_name` already exists.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The user does not have the privilege to go to the specified workspace.

#### Examples

The following example creates a savepoint named `Savepoint1` in the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.CreateSavepoint ('NEWWORKSPACE', 'Savepoint1');

**Parent topic:** DBMS_WM Package: Reference

### 4.19 CreateWorkspace

Creates a new workspace in the database.

#### Syntax

    DBMS_WM.CreateWorkspace(
       workspace    IN VARCHAR2,
       description  IN VARCHAR2 DEFAULT NULL,
       auto_commit  IN BOOLEAN DEFAULT TRUE);

or

    DBMS_WM.CreateWorkspace(
      workspace    IN VARCHAR2,
      isrefreshed  IN BOOLEAN,
      description  IN VARCHAR2 DEFAULT NULL,
      auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-19 CreateWorkspace Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`   | Name of the workspace. The name is case-sensitive, and it must be unique (no other workspace of the same name). The name must not contain any of the following characters: `"` (double quotes), `'` (single quote),``  ` `` (grave accent), or `|` (vertical bar).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `isrefreshed` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes the workspace to be continually refreshed. In a continually refreshed workspace (described in [Continually Refreshed Workspaces](introduction-to-workspace-manager.md)), changes made in the parent workspace are automatically applied to the workspace whenever data changes are committed in the parent workspace or are merged into the parent workspace from another child workspace. That is, you do not need to call the RefreshWorkspace procedure to apply the changes. See the Usage Notes for more information about continually refreshed workspaces.<br>`FALSE` causes the workspace not to be continually refreshed. To refresh the workspace, you must call the RefreshWorkspace procedure.<br>If you use the syntax without the `isrefreshed` parameter, the workspace is not continually refreshed. |
| `description` | Description of the workspace.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                                                                                                                                                                                                                                           |

#### Usage Notes

The new workspace is a child of the current workspace. If the session has not explicitly entered a workspace, it is in the `LIVE` database workspace, and the new workspace is a child of the `LIVE` workspace. For an explanation of database workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).

The owner of the workspace is the user that executed the CreateWorkspace procedure (or another procedure that executed the CreateWorkspace procedure), not the user that had the active permissions at the time the workspace was being created.

An implicit savepoint is created in the current version of the current workspace. (The current version does not have to be the latest version in the current workspace.) For an explanation of savepoints (explicit and implicit), see [Using Savepoints](introduction-to-workspace-manager.md).

While this procedure is executing, the current workspace is frozen in `READ_ONLY` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

This procedure does not implicitly go to the workspace created. To go to the workspace, use the GotoWorkspace procedure.

The following rules apply to continually refreshed workspaces (`isrefreshed` value of `TRUE`):

- The session must be on the latest version in order to create a continually refreshed workspace.

- You cannot turn off locking using the SetLockingOFF or SetWorkspaceLockModeOFF procedure for a continually refreshed workspace.

An exception is raised if one or more of the following apply:

- `workspace` already exists.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The user does not have the privilege to create a workspace.

#### Examples

The following example creates a workspace named `NEWWORKSPACE` in the database.

    EXECUTE DBMS_WM.CreateWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.20 Delete_Topo_Geometry_Layer

Deletes a topology geometry layer from a topology.

#### Format

    DBMS_WM.Delete_Topo_Geometry_Layer(
         topology     IN VARCHAR2,
         table_name   IN VARCHAR2,
         column_name  IN VARCHAR2);

#### Parameters

Table 4-20 Delete_Topo_Geometry_Layer Procedure Parameters

| Parameter     | Description                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `topology`    | Topology from which to delete the topology geometry layer containing the topology geometries in the specified column. The topology must have been created using the SDO_TOPO.CREATE_TOPOLOGY procedure. |
| `table_name`  | Name of the topology geometry layer table containing the column specified in `column_name`.                                                                                                             |
| `column_name` | Name of the column (of type `SDO_TOPO_GEOMETRY`) containing the topology geometries in the topology geometry layer to be deleted from the topology.                                                     |

#### Usage Notes

This procedure has the same format and meaning as the SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER procedure, which is documented in [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/SDO_TOPO-reference.md). However, you must use DBMS_WM.Delete_Topo_Geometry_Layer, and not SDO_TOPO.DELETE_TOPO_GEOMETRY_LAYER, to delete a topology geometry layer from a version-enabled feature table from a topology. For information about Workspace Manager support for topologies, see [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).

This procedure deletes data associated with the specified topology geometry layer from the edge, node, and face tables (described in [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/topology-data-model-overview.md)).

An exception is generated if `topology` or `table_name` is not version-enabled, or if `table_name` is the only feature table in `topology`.

#### Examples

The following example deletes the topology geometry layer that is based on the geometries in the `FEATURE` column of the `LAND_PARCELS` table from the topology named `CITY_DATA`.

    EXECUTE DBMS_WM.Delete_Topo_Geometry_Layer('CITY_DATA', 'LAND_PARCELS', 'FEATURE');

**Parent topic:** DBMS_WM Package: Reference

### 4.21 DeleteSavepoint

Deletes a savepoint and associated rows in version-enabled tables.

#### Syntax

    DBMS_WM.DeleteSavepoint(
       workspace                   IN VARCHAR2,
       savepoint_name              IN VARCHAR2,
       compress_view_wo_overwrite  IN BOOLEAN DEFAULT FALSE,
       auto_commit                 IN BOOLEAN DEFAULT TRUE,
       commit_in_batches           IN BOOLEAN DEFAULT FALSE,
       batch_size                  IN VARCHAR2 DEFAULT 'PRIMARY_KEY_RANGE');

#### Parameters

Table 4-21 DeleteSavepoint Procedure Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`                  | Name of the workspace in which the savepoint was created. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `savepoint_name`             | Name of the savepoint to be deleted. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `compress_view_wo_overwrite` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes history information to be deleted even if `VIEW_WO_OVERWRITE` was specified when versioning was enabled.<br>`FALSE` (the default) causes history information for a table not to be deleted if `VIEW_WO_OVERWRITE` was specified when versioning was enabled. (If `VIEW_WO_OVERWRITE` was not specified for a table, history information for the table is deleted regardless of the parameter value.)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `auto_commit`                | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `commit_in_batches`          | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes an internal commit operation to be performed after compression operations on `batch_size` rows in version-enabled tables. Periodic commit operations can be useful or necessary if version-enabled tables have many rows affected by the savepoint deletion, which can cause substantial Oracle database resources (such as rollback segments and undo tablespaces) to be used. If you specify `TRUE`, the `auto_commit` value must also be `TRUE`.<br>`FALSE` (the default) causes internal commit operations not to be performed during the savepoint deletion operation.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `batch_size`                 | Batch size for internal commit operations if `commit_in_batches` is `TRUE`; otherwise, the parameter is ignored. If specified, must be `TABLE` or `PRIMARY_KEY_RANGE`.<br>`TABLE` causes an internal commit operation to be performed after compressing each version-enabled table that needs to be compressed.<br>`PRIMARY_KEY_RANGE` specifies that each table is divided into batches of different ranges of primary key values, and an internal commit operation is to be performed after compressing each batch of rows in each version-enabled table that needs to be compressed. You must previously have generated statistics on the first column of the primary key, such as by using the DBMS_STATS.GATHER_TABLE_STATS procedure on the \<table_name\>\_LT table associated with each affected version-enabled table. See the Usage Notes for more information. The following example generates histogram statistics:<br>`EXECUTE DBMS_STATS.GATHER_TABLE_STATS('', 'cola_marketing_budget_lt', estimate_percent=>50, method_opt=>'FOR COLUMNS SIZE 50 product_id');` |

#### Usage Notes

You can delete a savepoint when it is no longer needed (for example, you will not need to go to it or roll back to it).

Deleting a savepoint is useful for the following reasons:

- You can reuse a savepoint name after it is deleted. (You cannot create a savepoint that has the same name as an existing savepoint.)

- Runtime performance for Workspace Manager operations is improved.

- Less disk storage is used for Workspace Manager structures.

While this procedure is executing, the current workspace is frozen in `NO_ACCESS` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

To delete a savepoint, you must have the `WM_ADMIN` system privilege or be the owner of the workspace or the savepoint.

This procedure cannot be executed if there are any sessions with an open database transaction, or if any user has executed a GotoDate operation or a GotoSavepoint operation specifying a savepoint in the workspace.

To specify a `batch_size` value of `PRIMARY_KEY_RANGE`, you must first generate either histogram statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, `TIMESTAMP`, `CHAR`, or `VARCHAR2`) or general statistics (for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`) on the first column of the primary key. The procedure DBMS_STATS.GATHER_TABLE_STATS generates general statistics. If general but not histogram statistics are available for columns of type `NUMBER`, `INTEGER`, `DATE`, or `TIMESTAMP`, the Workspace Manager system parameter `NUMBER_OF_COMPRESS_BATCHES` is used to compute the number of batches when `batch_size` is specified as `PRIMARY_KEY_RANGE`. For more information about statistics, see [Oracle Database Performance Tuning Guide](../tgdba/measuring-database-performance.md).

An exception is raised if one or more of the following apply:

- One or more sessions are already in `workspace` (unless the workspace is `LIVE`).

- `workspace` does not exist.

- `savepoint_name` does not exist.

- `savepoint_name` is not a removable savepoint. (Removable savepoints are explained in [Using Savepoints](introduction-to-workspace-manager.md).)

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The user does not have the privilege to go to the specified workspace.

#### Examples

The following example deletes a savepoint named `Savepoint1` in the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.DeleteSavepoint ('NEWWORKSPACE', 'Savepoint1');

**Parent topic:** DBMS_WM Package: Reference

### 4.22 DisableVersioning

Deletes all support structures that were created to enable the table to support versioned rows.

#### Syntax

    DBMS_WM.DisableVersioning(
       table_name         IN VARCHAR2,
       force              IN BOOLEAN DEFAULT FALSE,
       ignore_last_error  IN BOOLEAN DEFAULT FALSE,
       isTopology         IN BOOLEAN DEFAULT FALSE,
       keepWMValid        IN BOOLEAN DEFAULT TRUE,
       undo_space         IN VARCHAR2 DEFAULT NULL;

#### Parameters

Table 4-22 DisableVersioning Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`        | Name of the table or (if `isTopology` is `TRUE`) Oracle Spatial and Graph topology, or a comma-delimited list of names of tables related by multilevel referential integrity constraints. (Multilevel referential integrity constraints are explained in [Referential Integrity Support](introduction-to-workspace-manager.md).) Table names are not case-sensitive.                                                                                                                                                                                                                                                                       |
| `force`             | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` forces all data in workspaces other than `LIVE` to be discarded before versioning is disabled.<br>`FALSE` `(`the default) prevents versioning from being disabled if `table_name` was modified in any workspace other than `LIVE` and if the workspace that modified `table_name` still exists.                                                                                                                                                                                                                                                                                             |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the DisableVersioning procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the DisableVersioning procedure. |
| `isTopology`        | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` indicates that the value specified for the `table_name` parameter is the name of an Oracle Spatial and Graph topology (not a database table name), as explained in [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).<br>`FALSE` (the default) indicates that the value specified for the `table_name` parameter is not an Oracle Spatial and Graph topology name.                                                                                                                                                                                                 |
| `keepWMValid`       | A Boolean value (`TRUE` or `FALSE`). Applies only if valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)) has been enabled for the table.<br>`TRUE` (the default) causes the `WM_VALID` column and all data in that column to be kept in the table after the procedure completes.<br>`FALSE` causes the `WM_VALID` column to be dropped and all data in that column deleted as a result of the procedure. Only the current row for each primary key value is kept.                                                                                                                              |
| `undo_space`        | The string `UNLIMITED` (for no specified limit) or a number representing the maximum number of bytes for undo space available for the version-enable operation. Example: `'1048576'` for 1 megabyte. Any value specified overrides the value of the `UNDO_SPACE` Workspace Manager system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)).                                                                                                                                                                                                                                        |

#### Usage Notes

This procedure is used to reverse the effect of the EnableVersioning procedure. It deletes the Workspace Manager infrastructure (support structures) for versioning of rows, but does not affect any user data in the `LIVE` workspace. The workspace hierarchy and any savepoints still exist, but all rows are the same as in the `LIVE` workspace. (If there are multiple versions in the `LIVE` workspace of a row in the table for which versioning is disabled, only the most recent version of the row is kept.)

If `table_name` has valid time support (described in [Workspace Manager Valid Time Support](valid-time-support.md)), this procedure deletes the `WM_VALID` column and all data in that column. If deleting the `WM_VALID` column would cause a primary key constraint violation, only the row valid at the current time is retained.

If a call to the DisableVersioning procedure fails, the table is left in an inconsistent state. If this occurs, you should try to fix the cause of the error (examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message), and then call the DisableVersioning procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the DisableVersioning procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

Some causes for the failure of the DisableVersioning procedure include the following:

- The table contains much data in workspaces and the size of the undo tablespace required for the DisableVersioning procedure is not sufficient.

- A compilation error occurred while transferring user-defined triggers from the version-enabled table to the version-disabled table.

The DisableVersioning operation fails if the `force` value is `FALSE` and any of the following apply:

- The table is being modified by any user in any workspace other than the `LIVE` workspace.

- There are versioned rows of the table in any workspace other than the `LIVE` workspace.

Only the owner of a table or a user with the `WM_ADMIN` system privilege can disable versioning on the table.

Tables that are version-enabled and users that own version-enabled tables cannot be deleted. You must first disable versioning on the relevant table or tables.

An exception is raised if the table is not version-enabled.

For information about Workspace Manager support for tables in an Oracle Spatial and Graph topology, see [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).

#### Examples

The following example disables the `EMPLOYEE` table for versioning.

    EXECUTE DBMS_WM.DisableVersioning ('employee');

The following example disables the `EMPLOYEE` table for versioning and ignores the last error that occurred during the previous call to the DisableVersioning procedure.

    EXECUTE DBMS_WM.DisableVersioning ('employee', ignore_last_error => true);

The following example disables the `EMPLOYEE`, `DEPARTMENT`, and `LOCATION` tables (which have multilevel referential integrity constraints) for versioning.

    EXECUTE DBMS_WM.DisableVersioning('employee,department,location');

**Parent topic:** DBMS_WM Package: Reference

### 4.23 EnableVersioning

Version-enables a table, creating the necessary structures to enable the table to support multiple versions of rows.

#### Syntax

    DBMS_WM.EnableVersioning(
       table_name     IN VARCHAR2,
       hist           IN VARCHAR2 DEFAULT 'NONE',
       isTopology     IN BOOLEAN DEFAULT FALSE,
       validTime      IN BOOLEAN DEFAULT FALSE,
       undo_space     IN VARCHAR2 DEFAULT NULL,
       validTimeRange IN WM_PERIOD DEFAULT NULL);

#### Parameters

Table 4-23 EnableVersioning Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`     | Name of the table or (if `isTopology` is `TRUE`) Oracle Spatial and Graph topology, or a comma-delimited list of names of tables related by multilevel referential integrity constraints. (Multilevel referential integrity constraints are explained in [Referential Integrity Support](introduction-to-workspace-manager.md).) The length of a table name must not exceed 25 characters. The table must not contain any columns with names that start with WM\_ or WM\$. The table name and any column names must not contain any characters that need to be quoted, such as (but not restricted to) `!`, `?`, or `*`. The table name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `hist`           | History option, for tracking modifications to `table_name`. Must be one of the following values:<br>`NONE`: The timestamps for modifications to the table are not tracked. (This is the default.) A view named `<table_name>_HIST` (described in [xxx_HIST Views](workspace-manager-views.md)) is created to contain limited history information, but it will show only the most recent modifications to the same version of the table, and it will not contain the WM_CREATETIME and WM_RETIRETIME columns. A history of modifications to the version is not maintained; that is, subsequent changes to a row in the same version overwrite earlier changes.<br>`VIEW_W_OVERWRITE`: The with overwrite (W\_OVERWRITE) option. A view named `<table_name>_HIST` (described in [xxx_HIST Views](workspace-manager-views.md)) is created to contain history information, but it will show only the most recent modifications to the same version of the table. A history of modifications to the version is not maintained; that is, subsequent changes to a row in the same version overwrite earlier changes.<br>`VIEW_WO_OVERWRITE`: The without overwrite (WO\_OVERWRITE) option. A view named `<table_name>_HIST` (described in [xxx_HIST Views](workspace-manager-views.md)) is created to contain history information, and it will show all modifications to the same version of the table. A history of modifications to the version is maintained; that is, subsequent changes to a row in the same version do not overwrite earlier changes. |
| `isTopology`     | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` indicates that the value specified for the `table_name` parameter is the name of an Oracle Spatial and Graph topology (not a database table name), as explained in [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).<br>`FALSE` (the default) indicates that the value specified for the `table_name` parameter is not an Oracle Spatial and Graph topology name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `validTime`      | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes valid time support to be included. Workspace Manager valid time support is explained in [Workspace Manager Valid Time Support](valid-time-support.md).<br>`FALSE` (the default) causes valid time support not to be included.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `undo_space`     | A string containing `UNLIMITED` (for no specified limit) or a number representing the maximum number of bytes for undo space available for the version-enable operation. Example: `'1048576'` for 1 megabyte. Any value specified overrides the value of the `UNDO_SPACE` Workspace Manager system parameter (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `validTimeRange` | An object of type `WM_PERIOD` (explained in [WM_PERIOD Data Type](valid-time-support.md)) that specifies the initial valid time range for the `WM_VALID` column. If you specify a value, you must also specify the `validTime` parameter value as `TRUE`. By default, if valid time support is included, the valid time range is from the current system time and until changed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

#### Usage Notes

The table that is being version-enabled must have a primary key defined. The primary key can be a composite (multicolumn) primary key.

Only the owner of a table or a user with the `WM_ADMIN` system privilege can enable versioning on the table.

Tables that are version-enabled and users that own version-enabled tables cannot be deleted. You must first disable versioning on the relevant table or tables.

Tables owned by `SYS` cannot be version-enabled, and version-enabled tables cannot have any associated indexes or triggers owned by `SYS`.

A table that has a redaction policy defined on it cannot be version-enabled.

A table that has an invisible column cannot be version-enabled.

A table that has a deferrable constraint cannot be version-enabled.

A table that has a “generated by default” identity column cannot be version-enabled. However, an identity column defined as “default by default on null” is allowed.

If the table has an identity column, the “by default on null” and “by default” options have the same behavior: whenever the value for the column in an INSERT statement evaluates to null, the sequence will be accessed to get the next value. (To change this behavior, use the UseDefraultValuesForNulls procedure.)

An exception is raised if one or more of the following apply:

- `table_name` is already version-enabled.

- `table_name` contains a list of tables and any of the tables has a referential integrity constraint with a table that is not in the list.

- `table_name` contains any columns whose names start with WM\_ or WM\$.

- `table_name` or the name of any related object of the table (including columns, indexes, and triggers) contains any quoted identifiers.

If the table is version-enabled with the `VIEW_WO_OVERWRITE` hist option specified, this option can later be disabled and re-enabled by calling the SetWoOverwriteOFF and SetWoOverwriteON procedures.

The history option enables you to log and audit modifications.

The history option affects the behavior of the GotoDate procedure. See the Usage Notes for that procedure.

If you expect to purge a subset of your historical data periodically, such as removing historical data older than one year, plan to create a savepoint at each expected deletion point on the day it occurs. For example, if you plan to purge 2005 historical data when it is a year old, you need to create a savepoint on January 1, 2006. Then, on January 1, 2007 you can call the CompressWorkspace procedure, specifying the workspace name and the January 1, 2006 savepoint, to delete all history that occurred before 2006

For information about Workspace Manager support for tables in an Oracle Spatial and Graph topology, see [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).

Current notes and restrictions include the following:

- If you have referential integrity constraints on version-enabled tables, note the considerations and restrictions in [Referential Integrity Support](introduction-to-workspace-manager.md).

- If you have triggers defined on version-enabled tables, note the considerations and restrictions in [Triggers on Version-Enabled Tables](introduction-to-workspace-manager.md).

- Constraints and privileges defined on the table are carried over to the version-enabled table.

- DDL operations on version-enabled tables are subject to the procedures and restrictions described in [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md).

- Index-organized tables cannot be version-enabled.

- Object tables cannot be version-enabled.

- A table with one or more columns of LONG data type cannot be version-enabled.

- A table with one or more nested table columns cannot be version-enabled unless the `ALLOW_NESTED_TABLE_COLUMNS` Workspace Manager system parameter is set to `ON`.

- A table that has a redaction policy defined on it cannot be version-enabled.

#### Examples

The following example enables versioning on the `EMPLOYEE` table.

    EXECUTE DBMS_WM.EnableVersioning('employee');

The following example enables versioning on the `EMPLOYEE`, `DEPARTMENT`, and `LOCATION` tables, which have multilevel referential integrity constraints.

    EXECUTE DBMS_WM.EnableVersioning('employee,department,location');

**Parent topic:** DBMS_WM Package: Reference

### 4.24 Export

Exports data from a version-enabled table (all rows, or as limited by any combination of several parameters) to a staging table.

#### Syntax

    DBMS_WM.Export(
       table_name          IN VARCHAR2,
       staging_table       IN VARCHAR2,
       workspace           IN VARCHAR2,
       where_clause        IN VARCHAR2 DEFAULT NULL,
       export_scope        IN VARCHAR2 DEFAULT DBMS_WM.EXPORT_MODIFIED_DATA_ONLY,
       after_savepoint_name  IN VARCHAR2 DEFAULT NULL,
       as_of_savepoint_name  IN VARCHAR2 DEFAULT NULL,
       after_instant       IN DATE DEFAULT NULL,
       as_of_instant       IN DATE DEFAULT NULL,
       versioned_db        IN BOOLEAN DEFAULT TRUE,
       overwrite_existing_data  IN BOOLEAN DEFAULT FALSE,
       auto_commit         IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-24 Export Procedure Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`              | Name of the table containing the data to be exported. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `staging_table`           | Name of the table to hold the exported data. Must not exceed 25 characters. The name is not case-sensitive. If the table does not exist, a new table with this name is created, with a structure suitable for Workspace Manager export and import operations. (See the Usage Notes for more information about the staging table.)                                                                                                                                                                                                                                                                |
| `workspace`               | Name of the workspace from which to export the data. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `where_clause`            | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be exported. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `table_name` are exported.                                                                                                                                                                       |
| `export_scope`            | The scope (amount of data) for the export operation.<br>`DBMS_WM.EXPORT_ALL_DATA` exports all relevant data in `workspace`.<br>`DBMS_WM.EXPORT_MODIFIED_DATA_ONLY` (the default) exports only relevant data that was inserted, updated, or deleted in `workspace`.                                                                                                                                                                                                                                                                                                                               |
| `after_savepoint_name`    | Name of a savepoint: only data inserted, updated, or deleted after this savepoint is exported.<br>If you do not specify `after_savepoint_name` or `as_of_savepoint_name`, savepoints are ignored in determining the data to be exported.<br>See the Usage Notes for guidelines relating to the savepoint-related and instant-related parameters.                                                                                                                                                                                                                                                 |
| `as_of_savepoint_name`    | Name of a savepoint: only data in the workspace at the time the savepoint was created is exported.<br>If you do not specify `after_savepoint_name` or `as_of_savepoint_name`, savepoints are ignored in determining the data to be exported.<br>See the Usage Notes for guidelines relating to the savepoint-related and instant-related parameters.                                                                                                                                                                                                                                             |
| `after_instant`           | Date/time specification: only data inserted, updated, or deleted after this time is exported.<br>If you do not specify `after_instant` or `as_of_instant`, time is ignored in determining the data to be exported.<br>See the Usage Notes for guidelines relating to the savepoint-related and instant-related parameters.                                                                                                                                                                                                                                                                       |
| `as_of_instant`           | Date/time specification: only data that was in the workspace at this time is exported.<br>If you do not specify `after_instant` or `as_of_instant`, time is ignored in determining the data to be exported.<br>See the Usage Notes for guidelines relating to the savepoint-related and instant-related parameters.                                                                                                                                                                                                                                                                              |
| `versioned_db`            | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) creates a staging table that contains versioning information.<br>`FALSE` creates a staging table that contains only user-defined columns and user-visible data.                                                                                                                                                                                                                                                                                                                                                                     |
| `overwrite_existing_data` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` overwrites existing data in the staging table with the data that is exported.<br>`FALSE` (the default) preserves all existing data in the staging table, and raises an exception if the exported data conflicts with the existing data.                                                                                                                                                                                                                                                                                                           |
| `auto_commit`             | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

All data that satisfies the `where_clause` in the version-enabled table `table_name`, the `export_scope` parameter, and any parameters relating to a time or a savepoint in `workspace` is exported to the staging table (`staging_table` parameter).

Each row of data to be exported is considered to be one of the following: inserted, updated, or deleted in `workspace` (that is, modified data); or data that was not modified in `workspace` but can be seen in it (that is, ancestor data). If data is exported from the `LIVE` workspace, it is all modified data. If a workspace is created and no data has yet been versioned in it, and the Export procedure is called, all the data is ancestor data.

The first time you export data from a version-enabled table, the staging table should not exist; that is, do not try to create a staging table, but let the procedure create one for you using the name specified for the `staging_table` parameter. The staging table will contain all columns in the original table (`table_name` parameter), plus some columns for use by Workspace Manager.

After the staging table is created, you can use it for subsequent export operations from the original table, as long as you have not done any of the following DDL operations on the original table: altered any column names or data types, or modified or deleted the primary key constraint. If you have made any of these alterations to the original table, drop the staging table before you call the Export procedure, so that Workspace Manager can create a new staging table. (If you want to overwrite data in an existing staging table, you must also specify `overwrite_existing_data` as `TRUE`.)

The staging table must be in the current user's schema; or if it is in another schema, the current user must have the `CREATE ANY TABLE` and `INSERT ANY TABLE` privileges.

It is recommended that you specify no more than one of the following savepoint-related and instant-related parameters: `after_savepoint_name`, `as_of_savepoint_name`, `after_instant`, `as_of_instant`. If you specify `after_savepoint_name` and `after_instant`, the interaction of the two parameters can have complex results. You cannot specify the following parameter combinations: `after_savepoint_name` and `as_of_savepoint_name`, `after_instant` and `as_of_instant`, or `as_of_savepoint_name` and `as_of_instant`.

If `versioned_db` is `TRUE`, the staging table has three metadata columns in addition to all user-defined columns. The three added metadata columns are WM\$DELETEDROW, and two invisible columns (WM\$FLAG and WM\$WORKSPACE) that are used internally. You can use the WM\$DELETEDROW column to determine if the row was in a deleted form in the source workspace.

An exception is raised if one or more of the following apply:

- A specified table, workspace, or savepoint does not exist.

- `table_name` contains a nested table column.

- `table_name` contains a column named WM_VALID of type WM_PERIOD. (That is, this procedure is not supported for tables with valid time support, which is explained in [Workspace Manager Valid Time Support](valid-time-support.md).)

- `staging_table` exists but is not in a valid format for the export operation.

- `staging_table` is not in the current user's schema and the current user does not have the `CREATE TABLE` and `INSERT TABLE` privileges.

- The user does not have the `ACCESS_WORKSPACE` privilege for `workspace` or the `ACCESS_ANY_WORKSPACE` privilege.

- `overwrite_existing_data` is `FALSE` and data that needs to be exported already exists in `staging_table`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

See also [Import and Export Considerations](introduction-to-workspace-manager.md).

#### Examples

The following example exports all data from the `COLA_MARKETING_BUDGET` table in workspace `B_Focus_2` into the staging table `COLA_MARKETING_BUDGET_STG`. (The `EXECUTE` statement is actually on a single line.)

    EXECUTE DBMS_WM.Export(table_name => 'COLA_MARKETING_BUDGET', staging_table => 'COLA_MARKETING_BUDGET_STG', workspace => 'B_focus_2');

**Parent topic:** DBMS_WM Package: Reference

### 4.25 Export_Schemas

Creates a dump file containing everything related to Workspace Manager. Uses the Oracle Data Pump Export utility.

#### Syntax

    DBMS_WM.Export_Schemas(
       job_name           IN VARCHAR2,
       alt_schema         IN VARCHAR2 DEFAULT 'WMSYS_N',
       ignore_last_error  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-25 Export_Schemas Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `job_name`          | Name of the Data Pump job to be used for the export operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `alt_schema`        | Name of the database schema to be used for temporary storage of Workspace Manager metadata. The default is `WMSYS_N`. This schema must not already exist when the procedure is called, and it is automatically dropped when the procedure completes successfully.                                                                                                                                                                                                                                                                                                              |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the Export_Schemas procedure. Information about the last error is stored in the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view, which is described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the Export_Schemas procedure. |

#### Usage Notes

This procedure creates a dump file that contains all of the schemas that contain a version-enabled table or a parent table in a referential integrity constraint of a version-enabled table, as well as any internal Workspace Manager metadata. For any included schema, all objects and data within the schema are included in the dump file, not just the objects related to Workspace Manager. All other schemas are excluded.

This procedure makes use of an already existing Data Pump Export job. When you create this job using the `DBMS_DATAPUMP.OPEN` procedure, the `operation` parameter must be set to `EXPORT` and the `mode` parameter must be set to `SCHEMA`. The dump file(s) and log file should also be specified before you call `DBMS_WM.Export_Schemas`. No procedures that modify or limit what gets exported (such as `DBMS_DATAPUMP.METADATA_FILTER`) should be executed on this job. The Data Pump job should not be created while using SYSDBA privileges.

Because the WMSYS schema cannot be exported by the Oracle Data Pump Export utility, a temporary schema is required to hold some of the required data. This schema, specified by the `alt_schema` parameter, cannot exist before you call this procedure. Because this schema will be included within the generated dump file, it should be a schema that does not exist on the target database.

For information about using the Data Pump Utility, see [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md).

If a call to the Export_Schemas procedure fails, you should try to fix the cause of the error. Examine the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view where the STATE column is equal to `EXPORT` to see the SQL statement and error message. Fix the cause of the error, and then call the Export_Schemas procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you can ignore the error by calling the Export_Schemas procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

If the Export_Schemas procedure fails and if you must execute the procedure again, and if a row for this procedure exists in the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view, the procedure will continue to use the original Data Pump job that was specified (you do not need to create a new job). However, if the SQL statements being executed attempt to use the original job but that job no longer exists, you must set the `ignore_last_error` parameter to `TRUE` and execute the Export_Schemas procedure; and after that succeeds, execute the Export_Schemas procedure again.

Before exporting a version-enabled topology using either a full database export or the DBMS_WM.Export_Schemas procedure, you must do the following:

1.  Connect to the database as the owner of the topology.

2.  Execute the SDO_TOPO.PREPARE_FOR_EXPORT procedure, to create the topology export information table, with a name in the format \<topology-name\>\_EXP\$. This table contains the same columns as the USER_SDO_TOPO_INFO and ALL_SDO_TOPO_INFO views.

An exception is raised if one or more of the following apply:

- `job_name` does not exist.

- `alt_schema` already exists.

- The executing user does not have the DATAPUMP_EXP_FULL_DATABASE role.

- Errors exist in the `WMSYS` schema or in any required user schemas.

See also [Import and Export Considerations](introduction-to-workspace-manager.md).

#### Examples

The following example exports the Workspace Manager metadata using the Oracle Data Pump job named `EXPORT_OWM_SCHEMAS`. It assumes that the `DUMP_DIR` directory has already been created.

    DECLARE
      job_name varchar2(128) := 'EXPORT_OWM_SCHEMAS' ;
      dpj number ;
    BEGIN
      dpj := dbms_datapump.open('EXPORT', 'SCHEMA', null, job_name, 'COMPATIBLE') ;
      dbms_datapump.add_file(dpj, 'owm_schema.dmp', 'DUMP_DIR') ;
      dbms_datapump.add_file(dpj, 'owm_schema_export.log', 'DUMP_DIR', filetype=>dbms_datapump.KU$_FILE_TYPE_LOG_FILE) ;
      dbms_wm.export_schemas(job_name) ;
      dbms_datapump.detach(dpj);

    exception when others then
      dbms_datapump.detach(dpj);
      raise ;
    END;
    /

The following example exports the Workspace Manager metadata to the Oracle Cloud Infrastructure Object Storage using the `dbms_datapump` API job. The example assumes that the Object Storage bucket and the credentials to access the object store are already created. Also, ensure that Oracle Workspace Manager is enabled on your Autonomous Database instance. See [Enable Oracle Workspace Manager on Autonomous Database](http://www.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-EE7225CC-6EB1-44F5-BA39-272BBAD03448) for more information.

**Note:**

Oracle Workspace Manager is enabled on Autonomous Database Serverless only in selected cloud regions. The following table lists the cloud regions that support Oracle Workspace Manager:

Table 4-26 Supported Cloud Regions for Oracle Workspace Manager

| Region Name                         | Region Identifier |
|:------------------------------------|:------------------|
| Singapore (Singapore)               | ap-singapore-1    |
| France South (Marseille)            | eu-marseille-1    |
| UAE Central (Abu Dhabi)             | me-abudhabi-1     |
| Italy Northwest (Milan)             | eu-milan-1        |
| Sweden Central (Stockholm)          | eu-stockholm-1    |
| South Africa Central (Johannesburg) | af-johannesburg-1 |
| France Central (Paris)              | eu-paris-1        |

    DECLARE
      hdl          NUMBER;         -- Datapump handle
      dumpFile     VARCHAR2(1024)  := 'https://objectstorage.<region>.oraclecloud.com/n/<namespace-string>/b/<bucket_name>/o/';
      dumpType     NUMBER          := dbms_datapump.ku$_file_type_uridump_file;
      credName     VARCHAR2(1024)  := 'CRED_NAME';
      logFile      VARCHAR2(1024)  := 'export_test.log';
      logDir       VARCHAR2(20)    := 'DATA_PUMP_DIR';
      logType      NUMBER          := dbms_datapump.ku$_file_type_log_file;
      jobName varchar2(128)        := DBMS_SCHEDULER.GENERATE_JOB_NAME('EXP_SD_' );
    BEGIN
      dumpFile := dumpFile||jobName;
      dbms_output.put_line(  jobName);
      hdl := dbms_datapump.open('EXPORT', 'SCHEMA', job_name=>jobName);
      dbms_output.put_line(' LOCAL ' ||  jobName);
      dbms_datapump.add_file(hdl, dumpFile, credName, '30MB', dumpType, 1);
      dbms_datapump.add_file(hdl, logfile, logdir, null, logType);
      dbms_wm.export_schemas('ADMIN.' ||   jobName, 'WMSYS_N') ;
    EXCEPTION
      WHEN OTHERS THEN
        dbms_output.put_line(SQLERRM);
        dbms_output.put_line( dbms_utility.format_error_backtrace );
    END;
    /

**Parent topic:** DBMS_WM Package: Reference

### 4.26 FindRICSet

Finds tables that need to be version-enabled along with a specified table, due to referential integrity constraint relationships.

#### Syntax

    DBMS_WM.FindRICSet(
       table_name    IN VARCHAR2,
       result_table  IN VARCHAR2);

#### Parameters

Table 4-27 FindRICSet Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                       |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`   | Name of the table for which to find all other tables that will need to be version-enabled along with it, because of referential integrity constraint relationships. The name is not case-sensitive.                                                               |
| `result_table` | Name of the table to hold the results. The name is not case-sensitive.<br>This table must have two columns, `TABLE_OWNER` and `TABLE_NAME`, both of type `VARCHAR2`. If the table does not exist, a new table with this name and the required columns is created. |

#### Usage Notes

Workspace Manager has several considerations relating to referential integrity constraints, as explained in [Referential Integrity Support](introduction-to-workspace-manager.md). Sometimes, before you can version-enable a table, you must version-enable other tables that are in referential integrity constraints affecting the table. The `FindRICSet` procedure enables you to find all these other tables.

To display the results, use the `SET SERVEROUTPUT ON` statement before calling this procedure.

If the result table is not in the current user's schema, the following requirements apply:

- If the result table does not exist, the current user must have the `CREATE ANY TABLE` privilege.

- If the result table already exists, the current user must have the required privileges to insert into the table.

An exception is raised if one or more of the following apply:

- `table_name` does not exist.

- `result_table` exists but is not in a valid format.

- `result_table` exists and the current user does not have the required privileges to insert into the table.

- `result_table` does not exist, is specified for a schema other than the current user's schema, and the current user does not have the `CREATE ANY TABLE` privilege.

#### Examples

The following example creates two tables, `EMPLOYEES` and `DEPARTMENTS`, where `DEPARTMENTS.MANAGER_ID` has a foreign key relationship referencing `EMPLOYEES.EMPLOYEE_ID`. The example then finds all tables that would need to be version-enabled if `EMPLOYEES` and `DEPARTMENTS` were version-enabled.

The results show that if you want to version-enable the `EMPLOYEES` table, you must version-enable both the `EMPLOYEES` and `DEPARTMENTS` tables; but if you want to version-enable the `DEPARTMENTS` table, you do not need to version-enable any other tables.

    create table employees (employee_id number primary key, employee_name varchar2(30));
    create table departments (dept_id number primary key, manager_id number references employees(employee_id));

    -- Check RICs; result table does not already exist.
    EXECUTE DBMS_WM.FindRICSet('EMPLOYEES', 'EMPLOYEES_RESULTS');
    SELECT * FROM employees_results;

    TABLE_OWNER                    TABLE_NAME
    ------------------------------ ------------------------------
    WM_DEVELOPER                   EMPLOYEES
    WM_DEVELOPER                   DEPARTMENTS

    EXECUTE DBMS_WM.FindRICSet('DEPARTMENTS', 'DEPARTMENTS_RESULTS');
    SELECT * FROM departments_results;

    TABLE_OWNER                    TABLE_NAME
    ------------------------------ ------------------------------
    WM_DEVELOPER                   DEPARTMENTS

**Parent topic:** DBMS_WM Package: Reference

### 4.27 FreezeWorkspace

Restricts access to a workspace and the ability of users to make changes in the workspace.

#### Syntax

    DBMS_WM.FreezeWorkspace(
       workspace     IN VARCHAR2,
       freezemode    IN VARCHAR2 DEFAULT 'NO_ACCESS',
       freezewriter  IN VARCHAR2 DEFAULT NULL,
       force         IN BOOLEAN DEFAULT FALSE);

or

    DBMS_WM.FreezeWorkspace(
       workspace         IN VARCHAR2,
       session_duration  IN BOOLEAN,
       freezemode        IN VARCHAR2 DEFAULT 'NO_ACCESS',
       freezewriter      IN VARCHAR2 DEFAULT NULL,
       force             IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-28 FreezeWorkspace Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`        | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `session_duration` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes the workspace to be unfrozen when the session that called the FreezeWorkspace procedure disconnects from the database. This value is valid for all freeze modes.<br>`FALSE` causes the workspace not to be unfrozen when the session that called the FreezeWorkspace procedure disconnects from the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `freezemode`       | Mode for the frozen workspace. Must be one of the following values:<br>`NO_ACCESS`: No sessions are allowed in the workspace. (This is the default.)<br>`READ_ONLY`: Sessions are allowed in the workspace, but no write operations (insert, update, delete) are allowed.<br>`1WRITER`: Sessions are allowed in the workspace, but only one user (see the `freezewriter` parameter) is allowed to perform write operations (insert, update, delete).<br>`1WRITER_SESSION`: Sessions are allowed in the workspace, but only the database session (as opposed to the database user) that called the FreezeWorkspace procedure is allowed to perform write operations (insert, update, delete). The workspace is unfrozen after the session that called the FreezeWorkspace procedure disconnects from the database.<br>`WM_ONLY`: Only Workspace Manager operations are permitted. No sessions can directly modify data values; however, child workspaces can be merged into the workspace, and savepoints can be created in the workspace. |
| `freezewriter`     | The user that is allowed to make changes in the workspace. Can be specified only if `freezemode` is `1WRITER`. The default is `USER` (the current user).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `force`            | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` forces the workspace to be frozen even if it is already frozen. For example, this value enables you to freeze the workspace with a different `freezemode` parameter value without having first to call the UnfreezeWorkspace procedure.<br>`FALSE` (the default) prevents the workspace from being frozen if it is already frozen.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

#### Usage Notes

If you specify the procedure syntax that does not include the `session_duration` parameter, it is equivalent to specifying `FALSE` for that parameter: that is, the workspace is not unfrozen when the session that called the FreezeWorkspace procedure disconnects from the database.

The operation fails if one or more of the following apply:

- `workspace` is already frozen (unless `force` is `TRUE`).

- Any sessions are in `workspace` and `freezemode` is `NO_ACCESS` (specified or defaulted).

- `session_duration` is `FALSE and freezemode` is `1WRITER_SESSION`.

If `freezemode` is `READ_ONLY` or `1WRITER`, the workspace cannot be frozen if there is an active database transaction.

You can freeze a workspace only if one or more of the following apply:

- You are the owner of the specified workspace.

- You have the `WM_ADMIN` system privilege, the `FREEZE_ANY_WORKSPACE` privilege, or the `FREEZE_WORKSPACE` privilege for the specified workspace.

The `LIVE` workspace can be frozen only if `freezemode` is `READ_ONLY` or `1WRITER`.

To reverse the effect of FreezeWorkspace, use the UnfreezeWorkspace procedure.

#### Examples

The following example freezes the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.FreezeWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.28 GetBulkLoadVersion

Returns a version number that can be specified in the call to the BeginBulkLoading procedure and in the SQL\*Loader control file.

**Note:**

Effective with Oracle Database Release 12.1, this function is not necessary, and it always returns a null value.

#### Format

    DBMS_WM.GetBulkLoadVersion(
       workspace      IN VARCHAR2,
       savepoint_var  IN VARCVHAR2 DEFAULT 'LATEST') RETURN INTEGER;

#### Parameters

Table 4-29 GetBulkLoadVersion Function Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`     | Name of the workspace for which to return the bulk load version. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `savepoint_var` | The version in the workspace in which data will be bulk loaded. Must be one of the following: `LATEST` or `ROOT_VERSION`.<br>`LATEST` (the default) is the current version in the workspace.<br>`ROOT_VERSION` is into the root version (version number 0, which is in the `LIVE` workspace). The root version is the ancestor of all other versions, so data in the root version is visible from all other workspaces (unless non-`LIVE` workspaces have updated the data). You can specify `ROOT_VERSION` only if `workspace` is `LIVE`. |

#### Usage

Effective with Oracle Database Release 12.1, this function is not necessary and it always returns a null value. The BeginBulkLoading procedure automatically determines the bulk load version based on the workspace name and the optional savepoint name. (However, the bulk loading process in effect for previous releases is still supported.)

Before you can begin bulk loading data into a version-enabled table, you must call the BeginBulkLoading procedure. You must end the bulk loading session by calling either the CommitBulkLoading procedure (to commit changes made when the data was loaded) or the RollbackBulkLoading procedure (to roll back changes made when the data was loaded). For more information about bulk loading with Workspace Manager, see [Bulk Loading into Version-Enabled Tables](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- `workspace` does not exist.

- `savepoint_var` is not a valid value.

- `savepoint_var` is `ROOT_VERSION` but `workspace` is not `LIVE`.

#### Examples

The following example gets a bulk load version number for the `W1` workspace, and starts the bulk load operation into the `EMP` table in that workspace.

    DECLARE
      version INTEGER;
    BEGIN
      SELECT DBMS_WM.GetBulkLoadVersion ('W1') INTO version FROM DUAL;
      DBMS_WM.BeginBulkLoading ('EMP', 'W1', version);
    END;
    /

**Parent topic:** DBMS_WM Package: Reference

### 4.29 GetConflictWorkspace

Returns the name of the workspace on which the session has performed the SetConflictWorkspace procedure.

#### Format

    DBMS_WM.GetConflictWorkspace() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

If the SetConflictWorkspace procedure has not been executed, the name of the current workspace is returned.

#### Examples

The following example displays the name of the workspace on which the session has performed the SetConflictWorkspace procedure.

    SELECT DBMS_WM.GetConflictWorkspace FROM DUAL;

    GETCONFLICTWORKSPACE
    -----------------------------------------------------------------------------
    B_focus_2

**Parent topic:** DBMS_WM Package: Reference

### 4.30 GetDiffVersions

Returns the names of the (workspace, savepoint) pairs on which the session has performed the SetDiffVersions operation.

#### Format

    DBMS_WM.GetDiffVersions() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

The returned string is in the format `'(WS1,SP1), (WS2,SP2)'`. This format, including the parentheses, is intended to help you if you later want to use parts of the returned string in a call to the SetDiffVersions procedure.

#### Examples

The following example displays the names of the (workspace, savepoint) pairs on which the session has performed the SetDiffVersions operation.

    SELECT DBMS_WM.GetDiffVersions FROM DUAL;

    GETDIFFVERSIONS
    --------------------------------------------------------------------------------
    (B_focus_1, LATEST), (B_focus_2, LATEST)

**Parent topic:** DBMS_WM Package: Reference

### 4.31 GetLockMode

Returns the locking mode for the current session, which determines whether or not access is enabled to versioned rows and corresponding rows in the previous version.

#### Format

    DBMS_WM.GetLockMode() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

This function returns `E`, `S`, `C`, or `NULL`.

- For explanations of `E` (exclusive), `S` (shared), and `C` (carry-forward), see the description of the `lockmode` parameter of the SetLockingON procedure.

- `NULL` indicates that locking is not in effect. (Calling the SetLockingOFF procedure results in this setting.)

For an explanation of Workspace Manager locking, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md). See also the descriptions of the SetLockingON and SetLockingOFF procedures.

#### Examples

The following example displays the locking mode in effect for the session.

    SELECT DBMS_WM.GetLockMode FROM DUAL;

    GETLOCKMODE
    --------------------------------------------------------------------------------
    C

**Parent topic:** DBMS_WM Package: Reference

### 4.32 GetMultiWorkspaces

Returns the names of workspaces visible in the multiworkspace views for version-enabled tables.

#### Format

    DBMS_WM.GetMultiWorkspaces() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

This procedure returns the names of workspaces visible in the multiworkspace views, which are described in [xxx_MW Views](workspace-manager-views.md).

If no workspaces are visible in the multiworkspace views, `NULL` is returned. If more than one workspace name is returned, names are separated by a comma (for example: `workspace1,workspace2,workspace3`).

To make a workspace visible in the multiworkspace views, use the SetMultiWorkspaces procedure.

#### Examples

The following example displays the names of workspaces visible in the multiworkspace views.

    SELECT DBMS_WM.GetMultiWorkspaces FROM DUAL;

**Parent topic:** DBMS_WM Package: Reference

### 4.33 GetOpContext

Returns the context of the current operation for the current session.

#### Format

    DBMS_WM.GetOpContext() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

This function returns one of the following values:

- `DML`: The current operation is driven by data manipulation language (DML) initiated by the user.

- `IMPORT`: The current operation was initiated by a Import procedure call.

- `MERGE_REMOVE`: The current operation was initiated by a MergeWorkspace procedure call with the `remove_workspace` parameter set to `TRUE` or a MergeTable procedure call with the `remove_data` parameter set to `TRUE`.

- `MERGE_NOREMOVE`: The current operation was initiated by a MergeWorkspace procedure call with the `remove_workspace` parameter set to `FALSE` or a MergeTable procedure call with the `remove_data` parameter set to `FALSE`.

- `WORKSPACE_COPY`: The current operation was initiated by a CopyWorkspace procedure call.

The returned value can be used in user-defined triggers to take appropriate action based on the current operation.

#### Examples

The following example displays the context of the current operation.

    SELECT DBMS_WM.GetOpContext FROM DUAL;

    GETOPCONTEXT
    --------------------------------------------------------------------------------
    DML

**Parent topic:** DBMS_WM Package: Reference

### 4.34 GetOriginalDDL

Returns the original DDL of the version-enabled table as it existed before the call to the EnableVersioning procedure.

#### Format

    DBMS_WM.GetOriginalDDL
       table_id   IN VARCHAR2,
       ddl_stmts  IN OUT KU$_DDLS;

or

    DBMS_WM.GetOriginalDDL
       table_id  IN VARCHAR2,
       ddl_clob  IN OUT CLOB;

#### Parameters

Table 4-30 GetOriginalDDL Procedure Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_id`  | Name of the table for which to return the original DDL for creating the table. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                  |
| `ddl_stmts` | The original DDL statements for creating the table and any indexes, triggers, and grants on the table.<br>The type `KU$DLLS` is defined as `TABLE OF KU$_DD``L`. The type `KU$DDL` is defined as `(DDLTEXT CLOB, PARSEDITEMS KU$_PARSED_ITEMS)`. The type `KU$_PARSED_ITEMS` is defined as `TABLE OF KU$_PARSED_ITEM`. The type `KU$_PARSED_ITEM` is defined as `(ITEM VARCHAR2(30), VALUE VARCHAR2(4000), OBJECT_ROW NUMBER)`. |
| `ddl_clob`  | (Same information as for `ddl_stmts`, but using the type `CLOB`.)                                                                                                                                                                                                                                                                                                                                                               |

#### Usage

When the EnableVersioning procedure is called, DDL statements are executed on the table that modify its structure and that of related objects. (Some of these changes are outlined in [Infrastructure for Version-Enabling of Tables](introduction-to-workspace-manager.md).) The GetOriginalDDL procedure returns a series of DDL statements (CREATE TABLE, CREATE INDEX, CREATE TRIGGER, GRANT, and so on) that represent the table as if it was not a version-enabled table. These statements can then be used to create the table in a non-versioned form in another schema or in another database. This new table can then be version-enabled or used in its non-versioned form.

An exception is raised if either of the following applies:

- `table_id` does not exist.

- You do not have access to `table_id`.

#### Examples

The following example returns the original DDL statements for the `COLA_MARKETING_BUDGET` table into a variable of type `KU$_DLLS`.

    DECLARE
      original_ddl KU$_DDLS;
    BEGIN
      DBMS_WM.GetOriginalDDL('cola_marketing_budget',
                             original_ddl);
    END;
    /

**Parent topic:** DBMS_WM Package: Reference

### 4.35 GetPhysicalTableName

Returns the name (\<table_name\>\_LT form) of the physical table for a version-enabled table.

#### Format

    DBMS_WM.GetPhysicalTableName(
       table_owner  IN VARCHAR2,
       table_name   IN VARCHAR2) RETURN VARCHAR2;

#### Parameters

Table 4-31 GetPhysicalTableName Function Parameters

| Parameter     | Description                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------|
| `table_owner` | Name of the schema that owns `table_name`.                                                       |
| `table_name`  | Name of the version-enabled table for which to return the name of its associated physical table. |

#### Usage

If `table_name` is a version-enabled table, this function returns the name of the table, whose name is in the form \<table_name\>\_LT, that was created by Workspace Manager when the EnableVersioning procedure was called. For information about these \<table_name\>\_LT tables, see [Infrastructure for Version-Enabling of Tables](introduction-to-workspace-manager.md).

If `table_name` is a not a version-enabled table, this function returns `table_name`. Thus, you can also use this function to check whether or not a table is version-enabled (that is, by checking whether a name in the form \<table_name\>\_LT or the original table name is returned).

If the user executing the function does not have access to the table or the table does not exist, the function returns a null value.

#### Examples

The following example displays the physical table name associated with the `COLA_MARKETING_BUDGET` table after that table is version-enabled.

    SELECT DBMS_WM.GetPhysicalTableName('wm_developer', 'cola_marketing_budget')
       FROM DUAL;

    DBMS_WM.GETPHYSICALTABLENAME('WM_DEVELOPER','COLA_MARKETING_BUDGET')
    --------------------------------------------------------------------------------
    COLA_MARKETING_BUDGET_LT

**Parent topic:** DBMS_WM Package: Reference

### 4.36 GetPrivs

Returns a comma-delimited list of all privileges that the current user has for the specified workspace.

#### Format

    DBMS_WM.GetPrivs(
       workspace  IN VARCHAR2) RETURN VARCHAR2;

#### Parameters

Table 4-32 GetPrivs Function Parameters

| Parameter   | Description                                                                                   |
|:------------|:----------------------------------------------------------------------------------------------|
| `workspace` | Name of the workspace for which to return the list of privileges. The name is case-sensitive. |

#### Usage

For information about Workspace Manager privileges, see [Privilege Management with Workspace Manager](introduction-to-workspace-manager.md).

#### Examples

The following example displays the privileges that the current user has for the `B_focus_2` workspace.

    SELECT DBMS_WM.GetPrivs ('B_focus_2') FROM DUAL;

    DBMS_WM.GETPRIVS('B_FOCUS_2')
    --------------------------------------------------------------------------------
    ACCESS,MERGE,CREATE,REMOVE,ROLLBACK

**Parent topic:** DBMS_WM Package: Reference

### 4.37 GetSessionInfo

Retrieves information about the current workspace and session context.

#### Format

    DBMS_WM.GetSessionInfo(
       workspace     OUT VARCHAR2,
       context       OUT VARCHAR2,
       context_type  OUT VARCHAR2);

#### Parameters

Table 4-33 GetSessionInfo Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                              |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace that the current session is in.                                                                                                                                                                                    |
| `context`      | The context of the current session in the workspace, expressed as one of the following: `LATEST`, a savepoint name, or an instant (point in time) in 'DD-MON-YYYY HH24:MI:SS' date format. (See the Usage Notes for details.)            |
| `context_type` | The type of context for the current session in the workspace. Specifically, one of the following values: `LATEST` (if `context` is `LATEST`), `SAVEPOINT` (if `context` is a savepoint name), or `INSTANT` (if `context` is an instant). |

#### Usage Notes

This procedure is useful if you need to know where a session is (workspace and context) -- for example, after you have performed a combination of GotoWorkspace, GotoSavepoint, and GotoDate operations.

After the procedure successfully executes, the `context` parameter contains one of the following values:

- `LATEST`: The session is currently on the `LATEST` logical savepoint (explained in [Using Savepoints](introduction-to-workspace-manager.md)), and it can see changes as they are made in the workspace. The context is automatically set to `LATEST` when the session enters the workspace (using the GotoWorkspace procedure).

- A savepoint name: The session is currently on a savepoint in the workspace. The session cannot see changes as they are made in the latest version of the workspace, but instead sees a static view of the data as of the savepoint creation time. The session context is set to the savepoint name after a call to the GotoSavepoint procedure.

- An instant (a point in time): The session is currently on a specific point in time. The session cannot see changes as they are made in the latest version of the workspace, but instead sees a static view of the data as of the specific time. The session context is set to an instant after a call to the GotoDate procedure.

For detailed information about the session context, see [Session Context Information for Workspace Manager](introduction-to-workspace-manager.md).

#### Examples

The following example retrieves and displays information about the current workspace and context in the session.

    DECLARE
      current_workspace VARCHAR2(128);
      current_context VARCHAR2(128);
      current_context_type VARCHAR2(128);
    BEGIN
      DBMS_WM.GetSessionInfo(current_workspace,
                             current_context,
                             current_context_type);
      DBMS_OUTPUT.PUT_LINE('Session currently in workspace: ' ||current_workspace);
      DBMS_OUTPUT.PUT_LINE('Session context is: ' ||current_context);
      DBMS_OUTPUT.PUT_LINE('Session context is on: ' ||current_context_type);
    END;
    /
    Session currently in workspace: B_focus_2
    Session context is: LATEST
    Session context is on: LATEST

    PL/SQL procedure successfully completed.

**Parent topic:** DBMS_WM Package: Reference

### 4.38 GetSystemParameter

Returns the value of a Workspace Manager system parameter.

#### Syntax

    DBMS_WM.GetSytstemParameter(
       name   IN VARCHAR2) RETURN VARCHAR2;

#### Parameters

Table 4-34 GetSystemParameter Procedure Parameters

| Parameter | Description                                                                                                                                                                                                                                                                              |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | Name of the Workspace Manager system parameter for which to set the value. The name must be one of the following: `ALLOW_CAPTURE_EVENTS`, `ALLOW_MULTI_PARENT_WORKSPACES`, `ALLOW_NESTED_TABLE_COLUMNS`, `CR_WORKSPACE_MODE`, `FIRE_TRIGGERS_FOR_NONDML_EVENTS`, `NONCR_WORKSPACE_MODE`. |

#### Usage Notes

For information about Workspace Manager system parameters, see [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).

An exception is raised if the `name` value is not valid.

#### Examples

The following checks if multiparent workspaces (described in [Multiparent Workspaces](introduction-to-workspace-manager.md)) are allowed.

    SELECT DBMS_WM.GetSystemParameter ('ALLOW_MULTI_PARENT_WORKSPACES') FROM DUAL;

    DBMS_WM.GETSYSTEMPARAMETER('ALLOW_MULTI_PARENT_WORKSPACES')
    --------------------------------------------------------------------------------
    ON

**Parent topic:** DBMS_WM Package: Reference

### 4.39 GetValidFrom

Returns the `ValidFrom` attribute of the current session valid time. (Valid time support is described in [Workspace Manager Valid Time Support](valid-time-support.md).)

#### Format

    DBMS_WM.GetValidFrom() RETURN TIMESTAMP WITH TIME ZONE;

#### Parameters

None.

#### Usage Notes

To set the session valid time period, use the SetValidTime procedure.

To get the `ValidTill` attribute of the current session valid time, use the GetValidTill function.

#### Examples

The following example displays the `ValidFrom` attribute of the current session valid time.

    SELECT DBMS_WM.GetValidFrom FROM DUAL;

    GETVALIDFROM
    ---------------------------------------------------------------------------
    01-JAN-1995 12:00:00 -04:00

**Parent topic:** DBMS_WM Package: Reference

### 4.40 GetValidTill

Returns the `ValidTill` attribute of the current session valid time. (Valid time support is described in [Workspace Manager Valid Time Support](valid-time-support.md).)

#### Format

    DBMS_WM.GetValidTill() RETURN TIMESTAMP WITH TIME ZONE;

#### Parameters

None.

#### Usage Notes

To set the session valid time period, use the SetValidTime procedure.

To get the `ValidFrom` attribute of the current session valid time, use the GetValidFrom function.

#### Examples

The following example displays the `ValidTill` attribute of the current session valid time.

    SELECT DBMS_WM.GetValidTill FROM DUAL;

    GETVALIDTILL
    ---------------------------------------------------------------------------
    01-JAN-1996 12:00:00 -04:00

**Parent topic:** DBMS_WM Package: Reference

### 4.41 GetVersion

Returns the current version of Workspace Manager.

#### Format

    DBMS_WM.GetVersion() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

The value returned is the same as that in the [WM_INSTALLATION](workspace-manager-views.md) view for the VALUE column where the NAME column value is `OMW_VERSION`.

#### Examples

The following example displays the Workspace Manager version number.

    SELECT DBMS_WM.GetVersion FROM DUAL;

    GETOPCONTEXT
    --------------------------------------------------------------------------------
    12.2.0.1.0

**Parent topic:** DBMS_WM Package: Reference

### 4.42 GetWMMetadataSpace

Returns the number of bytes currently used to store the Workspace Manager metadata.

#### Format

    DBMS_WM.GetWMMetadataSpace() RETURN NUMBER;

#### Parameters

None.

#### Usage Notes

The Workspace Manager metadata (views, internal tables, and other objects) is by default stored in the default tablespace of the `WMSYS` user. You cannot directly control the size of the Workspace Manager metadata, but you can control its placement by using the Move_Proc procedure to move the metadata to a different tablespace. You can use the GetWMMetadataSpace function to determine the approximate minimum space that you will need to have available in the tablespace into which you are considering moving the Workspace Manager metadata.

#### Examples

The following example displays the number of bytes currently used to store the Workspace Manager metadata.

    SELECT DBMS_WM.GetWMMetadataSpace FROM DUAL;

    GETWMMETADATASPACE
    ------------------
               6750208

**Parent topic:** DBMS_WM Package: Reference

### 4.43 GetWorkspace

Returns the current workspace for the session.

#### Format

    DBMS_WM.GetWorkspace() RETURN VARCHAR2;

#### Parameters

None.

#### Usage Notes

None.

#### Examples

The following example displays the current workspace for the session.

    SELECT DBMS_WM.GetWorkspace FROM DUAL;

    GETWORKSPACE
    --------------------------------------------------------------------------------
    B_focus_2

**Parent topic:** DBMS_WM Package: Reference

### 4.44 GotoDate

Goes to a point at or near the specified date and time in the current workspace.

#### Syntax

    DBMS_WM.GotoDate(
       in_date   IN VARCHAR2,
       fmt       IN VARCHAR2 DEFAULT 'mmddyyyyhh24miss',
       nlsparam  IN VARCHAR2 DEFAULT NULL,
       tsWtz     IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-35 GotoDate Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                         |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `in_date`  | Date and time for the read-only view of the workspace. (See the Usage Notes for details.)<br>If `in_date` is a VARCHAR2 string, it is a date string or a timestamp with time zone, depending on the value of the `tsWtz` parameter. |
| `fmt`      | Date format. The options are the same as for the `TO_TIMESTAMP_TZ` function, which is described in [Oracle Database SQL Language Reference](../sqlrf/TO_TIMESTAMP_TZ.md).<br>Default: `'mmddyyyyhh24miss'`                          |
| `nlsparam` | Globalization support options. The options are the same as for the `TO_TIMESTAMP_TZ` function, which is described in [Oracle Database SQL Language Reference](../sqlrf/TO_TIMESTAMP_TZ.md).                                         |
| `tsWtz`    | Timestamp with time zone flag. A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` means that `in_date` is considered a timestamp with time zone information.<br>`FALSE` (the default) means that `in_date` is a date string.            |

#### Usage Notes

You are presented a read-only view of the current workspace at or near the specified date and time. The exact time point depends on the history option for tracking changes to data in version-enabled tables, as set by the EnableVersioning procedure or modified by the SetWoOverwriteOFF or SetWoOverwriteON procedure:

- `NONE`: The read-only view reflects the first savepoint after `in_date`.

- `VIEW_W_OVERWRITE`: The read-only view reflects the data values in effect at `in_date`, except if `in_date` is between two savepoints and data was changed between the two savepoints. In this case, data that had been changed between the savepoints might be seen as empty or as having a previous value. To ensure the most complete and accurate view of the data, specify the `VIEW_WO_OVERWRITE` history option when version-enabling a table.

- `VIEW_WO_OVERWRITE`: The read-only view reflects the data values in effect at `in_date`.

For an explanation of the history options, see the description of the `hist` parameter for the EnableVersioning procedure.

The following example scenario shows the effect of the `VIEW_WO_OVERWRITE` setting. Assume the following sequence of events:

1.  The `MANAGER_NAME` value in a row is `Adams`.

2.  Savepoint `SP1` is created.

3.  The `MANAGER_NAME` value is changed to `Baxter`.

4.  The time point that will be specified as `in_date` (in step 7) occurs.

5.  The `MANAGER_NAME` value is changed to `Chang`. (Thus, the value has been changed both before and after `in_date` since the first savepoint and before the second savepoint.)

6.  Savepoint `SP2` is created.

7.  A GotoDate operation is executed, specifying the time point in step 4 as `in_date`.

In the preceding scenario:

- If the history option in effect is `VIEW_WO_OVERWRITE`, the `MANAGER_NAME` value after step 7 is `Baxter`. After step 5, the versioned table has three rows, each with a different `MANAGER_NAME` value (`Adams`, `Baxter`, `Chang`), because each change is made in a new copy of the row.

- If the history option in effect is `VIEW_W_OVERWRITE`, no value is seen after step 7. The updates in steps 3 and 5 are made in the same copy of the row, and the update in step 5 overwrites the update in step 3. As a result, after step 5 the versioned table has two rows, with `MANAGER_NAME` values `Adams` and `Chang`. Because the `MANAGER_NAME` value (`Baxter`) that was in effect at the specified instant has been overwritten, no row is visible.

- If the history option in effect is `NONE`, the `MANAGER_NAME` value after step 7 is `Chang`, because the first savepoint after the specified instant is `SP2`. After step 5, the versioned table has two rows, with `MANAGER_NAME` values `Adams` and `Chang`.

The GotoDate procedure should be executed while users exist in the workspace. There are no explicit privileges associated with this procedure.

#### Examples

The following example goes to a point at or near midnight at the start of 08-Jun-2004, depending on the history option currently in effect.

    EXECUTE DBMS_WM.GotoDate ('08-JUN-04', 'DD-MON-YY');

**Parent topic:** DBMS_WM Package: Reference

### 4.45 GotoSavepoint

Goes to the specified savepoint in the current workspace.

#### Syntax

    DBMS_WM.GotoSavePoint(
       savepoint_name  IN VARCHAR2 DEFAULT 'LATEST');

#### Parameters

Table 4-36 GotoSavepoint Procedure Parameters

| Parameter        | Description                                                                                                       |
|:-----------------|:------------------------------------------------------------------------------------------------------------------|
| `savepoint_name` | Name of the savepoint. The name is case-sensitive. If `savepoint_name` is not specified, the default is `LATEST`. |

#### Usage Notes

You are presented a read-only view of the workspace at the time of savepoint creation. This procedure is useful for examining the workspace from different savepoints before performing a rollback to a specific savepoint by calling the RollbackToSP procedure to delete all rows from that savepoint forward.

This operation can be executed while users exist in the workspace. There are no explicit privileges associated with this operation.

If you do not want to roll back to the savepoint, you can call the GotoSavepoint procedure with a null parameter to go to the currently active version in the workspace. (This achieves the same result as calling the GotoWorkspace procedure and specifying the workspace.)

For more information about savepoints, including the `LATEST` savepoint, see [Using Savepoints](introduction-to-workspace-manager.md).

#### Examples

The following example goes to the savepoint named `Savepoint1`.

    EXECUTE DBMS_WM.GotoSavepoint ('Savepoint1');

**Parent topic:** DBMS_WM Package: Reference

### 4.46 GotoWorkspace

Moves the current session to the specified workspace.

#### Syntax

    DBMS_WM.GotoWorkspace(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-37 GotoWorkspace Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

After a user goes to a workspace, modifications to data can be made there.

To go to the live database, specify `workspace` as `LIVE`. Because many operations are prohibited when any users (including you) are in the workspace, it is often convenient to go to the `LIVE` workspace before performing operations on created workspaces.

An exception is raised if one or more of the following apply:

- `workspace` does not exist.

- The user does not have `ACCESS_WORKSPACE` privilege for `workspace`.

- `workspace` has been frozen in `NO_ACCESS` mode (see the FreezeWorkspace procedure).

#### Examples

The following example includes the user in the `NEWWORKSPACE` workspace. The user will begin to work in the latest version in that workspace.

    EXECUTE DBMS_WM.GotoWorkspace ('NEWWORKSPACE');

The following example includes the user in the `LIVE` database workspace. By default, when users connect to a database, they are placed in this workspace.

    EXECUTE DBMS_WM.GotoWorkspace ('LIVE');

**Parent topic:** DBMS_WM Package: Reference

### 4.47 GrantGraphPriv

Grants privileges on multiparent graph workspaces to users and roles. The `grant_option` parameter enables the grantee to grant the specified privileges to other users and roles.

#### Syntax

    DBMS_WM.GrantGraphPriv(
       priv_types      IN VARCHAR2,
       leaf_workspace  IN VARCHAR2,
       grantee         IN VARCHAR2,
       node_types      IN VARCHAR2 DEFAULT '(''R'',''I'',''L'')',
       grant_option    IN VARCHAR2 DEFAULT 'NO',
       auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-38 GrantGraphPriv Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`     | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, `CREATE_WORKSPACE`, `REMOVE_WORKSPACE`, `ROLLBACK_WORKSPACE`, and `FREEZE_WORKSPACE`.                                                                                                                                                                                                       |
| `leaf_workspace` | Name of the leaf workspace in the directed acyclic graph. (Leaf workspaces, directed acyclic graphs, and other concepts related to multiparent workspaces are explained in [Multiparent Workspaces](introduction-to-workspace-manager.md).) The name is case-sensitive.                                                                                                                                                                                                                                                                                                                          |
| `grantee`        | Name of the user (can be the `PUBLIC` user group) or role to which to grant `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `node_types`     | List of letters (in parentheses and comma-delimited) representing the types of nodes on which to grant the privileges: `R` for the root of the graph, `I` for the specified intermediate node, `L` for the leaf of the graph. The default is all types of nodes.                                                                                                                                                                                                                                                                                                                                 |
| `grant_option`   | Specify `YES` to enable the grant option for grantee, or `NO` (the default) to disable the grant option for grantee. The grant option allows `grantee` to grant the privileges specified in `priv_types` on the workspace specified in `leaf_workspace` to other users and roles.                                                                                                                                                                                                                                                                                                                |
| `auto_commit`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with GrantWorkspacePriv , which grants workspace-level Workspace Manager privileges on workspaces other than multiparent graph workspaces.

If a user gets a privilege from more than one source and if any of those sources has the grant option for that privilege, the user has the grant option for the privilege. For example, assume that user `SCOTT` has been granted the `ACCESS_WORKSPACE` privilege with `grant_option` as `NO`, but that the `PUBLIC` user group has been granted the `ACCESS_WORKSPACE` privilege with `grant_option` as `YES`. Because user `SCOTT` is a member of `PUBLIC`, user `SCOTT` has the `ACCESS_WORKSPACE` privilege with the grant option.

The `WM_ADMIN_ROLE `role has all Workspace Manager privileges with the grant option. The `WM_ADMIN_ROLE` role is automatically given to the `DBA` role.

The `ACCESS_WORKSPACE` or `ACCESS_ANY_WORKSPACE` privilege is needed for all other Workspace Manager privileges.

To revoke workspace-level privileges on multiparent graph workspaces, use the RevokeGraphPriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You do not have the privilege to grant `priv_types`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example enables user `Smith` to access all types of nodes in the directed acyclic graph in which the `NEWWORKSPACE` workspace is the leaf workspace and to merge changes in these workspaces, and it allows `Smith` to grant the two specified privileges on the leaf workspace to other users.

    DBMS_WM.GrantGraphPriv ('ACCESS_WORKSPACE, MERGE_WORKSPACE', 'NEWWORKSPACE', 'Smith', 'YES');

**Parent topic:** DBMS_WM Package: Reference

### 4.48 GrantPrivsOnPolicy

Grants the privileges required to call the EnableVersioning procedure on a table that contains the specified Oracle Label Security (OLS) policy.

#### Syntax

    DBMS_WM.GrantPrivsOnPolicy(
       policy_name  IN VARCHAR2);

#### Parameters

Table 4-39 GrantPrivsOnPolicy Procedure Parameters

| Parameter     | Description                                                 |
|:--------------|:------------------------------------------------------------|
| `policy_name` | Name of the policy for which privileges need to be granted. |

#### Usage Notes

This procedure grants the necessary privileges on an OLS policy to the WMSYS schema. These privileges are required when executing workspace operations. If multiple tables protected by the same policy need to be version-enabled, this procedure only needs to be executed once.

#### Examples

The following grants the necessary privileges on a policy named `my_policy`.

    EXECUTE DBMS_WM.GrantPrivsOnPolicy('my_policy');

**Parent topic:** DBMS_WM Package: Reference

### 4.49 GrantSystemPriv

Grants system-level privileges (not restricted to a particular workspace) to users and roles. The `grant_option` parameter enables the grantee to grant the specified privileges to other users and roles.

#### Syntax

    DBMS_WM.GrantSystemPriv(
       priv_types    IN VARCHAR2,
       grantee       IN VARCHAR2,
       grant_option  IN VARCHAR2 DEFAULT 'NO',
       auto_commit   IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-40 GrantSystemPriv Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`   | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_ANY_WORKSPACE`, `MERGE_ANY_WORKSPACE`, `CREATE_ANY_WORKSPACE`, `REMOVE_ANY_WORKSPACE`, `ROLLBACK_ANY_WORKSPACE`, and `FREEZE_ANY_WORKSPACE`.                                                                                                                                                                               |
| `grantee`      | Name of the user (can be the `PUBLIC` user group) or role to which to grant `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `grant_option` | Specify `YES` to enable the grant option for grantee, or `NO` (the default) to disable the grant option for grantee. The grant option allows `grantee` to grant the privileges specified in `priv_types` to other users and roles.                                                                                                                                                                                                                                                                                                                                                               |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with GrantWorkspacePriv , which grants workspace-level Workspace Manager privileges with keywords that do not contain `ANY` and which has a `workspace` parameter.

If a user gets a privilege from more than one source and if any of those sources has the grant option for that privilege, the user has the grant option for the privilege. For example, assume that user `SCOTT` has been granted the `ACCESS_ANY_WORKSPACE` privilege with `grant_option` as `NO`, but that the `PUBLIC` user group has been granted the `ACCESS_ANY_WORKSPACE` privilege with `grant_option` as `YES`. Because user `SCOTT` is a member of `PUBLIC`, user `SCOTT` has the `ACCESS_ANY_WORKSPACE` privilege with the grant option.

The `WM_ADMIN_ROLE` role has all Workspace Manager privileges with the grant option. The `WM_ADMIN_ROLE` role is automatically given to the `DBA` role.

The `ACCESS_WORKSPACE` or `ACCESS_ANY_WORKSPACE` privilege is needed for all other Workspace Manager privileges.

To see which users have been granted Workspace Manager system-level privileges, examine the [DBA_WM_SYS_PRIVS](workspace-manager-views.md) metadata view, which is described in [DBA_WM_SYS_PRIVS](workspace-manager-views.md).

To revoke system-level privileges, use the RevokeSystemPriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You do not have the privilege togrant `priv_types`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example enables user `Smith` to access any workspace in the database, but does not allow `Smith` to grant the `ACCESS_ANY_WORKSPACE` privilege to other users.

    EXECUTE DBMS_WM.GrantSystemPriv ('ACCESS_ANY_WORKSPACE', 'Smith', 'NO');

**Parent topic:** DBMS_WM Package: Reference

### 4.50 GrantWorkspacePriv

Grants workspace-level privileges to users and roles. The `grant_option` parameter enables the grantee to grant the specified privileges to other users and roles.

#### Syntax

    DBMS_WM.GrantWorkspacePriv(
       priv_types    IN VARCHAR2,
       workspace     IN VARCHAR2,
       grantee       IN VARCHAR2,
       grant_option  IN VARCHAR2 DEFAULT 'NO',
       auto_commit   IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-41 GrantWorkspacePriv Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`   | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, `CREATE_WORKSPACE`, `REMOVE_WORKSPACE`, `ROLLBACK_WORKSPACE`, and `FREEZE_WORKSPACE`.                                                                                                                                                                                                       |
| `workspace`    | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `grantee`      | Name of the user (can be the `PUBLIC` user group) or role to which to grant `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `grant_option` | Specify `YES` to enable the grant option for grantee, or `NO` (the default) to disable the grant option for grantee. The grant option allows `grantee` to grant the privileges specified in `priv_types` on the workspace specified in `workspace` to other users and roles.                                                                                                                                                                                                                                                                                                                     |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with GrantSystemPriv, which grants system-level Workspace Manager privileges with keywords in the form xxx\_ANY_WORKSPACE (`ACCESS_ANY_WORKSPACE`, `MERGE_ANY_WORKSPACE`, and so on). Contrast this procedure also with GrantGraphPriv, which grants privileges on multiparent graph workspaces to users and roles.

If a user gets a privilege from more than one source and if any of those sources has the grant option for that privilege, the user has the grant option for the privilege. For example, assume that user `SCOTT` has been granted the `ACCESS_WORKSPACE` privilege with `grant_option` as `NO`, but that the `PUBLIC` user group has been granted the `ACCESS_WORKSPACE` privilege with `grant_option` as `YES`. Because user `SCOTT` is a member of `PUBLIC`, user `SCOTT` has the `ACCESS_WORKSPACE` privilege with the grant option.

The `WM_ADMIN_ROLE` role has all Workspace Manager privileges with the grant option. The `WM_ADMIN_ROLE` role is automatically given to the `DBA` role.

The `ACCESS_WORKSPACE` or `ACCESS_ANY_WORKSPACE` privilege is needed for all other Workspace Manager privileges.

To revoke workspace-level privileges, use the RevokeWorkspacePriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You do not have the privilege to grant `priv_types`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example enables user `Smith` to access the `NEWWORKSPACE` workspace and merge changes in that workspace, and allows `Smith` to grant the two specified privileges on `NEWWORKSPACE` to other users.

    DBMS_WM.GrantWorkspacePriv ('ACCESS_WORKSPACE, MERGE_WORKSPACE', 'NEWWORKSPACE', 'Smith', 'YES');

**Parent topic:** DBMS_WM Package: Reference

### 4.51 Import

Imports data from a staging table (all rows, or as limited by any combination of several parameters) into a version-enabled table in a specified workspace.

#### Syntax

    DBMS_WM.Import(
       staging_table   IN VARCHAR2,
       to_table        IN VARCHAR2,
       to_workspace    IN VARCHAR2,
       from_workspace  IN VARCHAR2 DEFAULT NULL,
       where_clause    IN VARCHAR2 DEFAULT NULL,
       import_scope    IN VARCHAR2 DEFAULT DBMS_WM.IMPORT_ALL_DATA,
       ancestor_savepoint_workspace  IN VARCHAR2 DEFAULT NULL,
       ancestor_savepoint_name       IN VARCHAR2 DEFAULT NULL,
       apply_locks     IN BOOLEAN DEFAULT FALSE,
       enforceUCFlag   IN BOOLEAN DEFAULT TRUE,
       enforceRICFlag  IN BOOLEAN DEFAULT TRUE,
       auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-42 Import Procedure Parameters

| Parameter                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `staging_table`                | Name of the table that holds the data that had previously been exported using the Export procedure. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `to_table`                     | Name of the table into which to import the data. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `to_workspace`                 | Name of the workspace in which to import the data. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `from_workspace`               | Name of the workspace from which to import the data. The name is case-sensitive. If the staging table contains versioning information, you must specify `from_workspace`.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `where_clause`                 | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be imported. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `staging_table` are imported.                                                                                                                                                                    |
| `import_scope`                 | The scope (amount of data) for the import operation.<br>`DBMS_WM.IMPORT_ALL_DATA` (the default) imports all relevant data.<br>`DBMS_WM.IMPORT_MODIFIED_DATA_ONLY` imports only relevant data that has been inserted, updated, or deleted in `from_workspace`.                                                                                                                                                                                                                                                                                                                                    |
| `ancestor_savepoint_workspace` | Name of the workspace containing the ancestor savepoint specified in `ancestor_savepoint_name`. For the current release, if you specify `ancestor_savepoint_workspace`, the value must be `LIVE`.<br>If you specify this parameter, you must also specify `ancestor_savepoint_name`.                                                                                                                                                                                                                                                                                                             |
| `ancestor_savepoint_name`      | Name of a savepoint in `ancestor_savepoint_workspace`. All data that was ancestor data at the time of the export operation (see the Usage Notes for the Export procedure) is imported to the specified savepoint. For the current version, if you specify `ancestor_savepoint_name`, the value must be `DBMS_WM.ROOT_VERSION`.<br>If you specify this parameter, you must also specify `ancestor_savepoint_workspace`.                                                                                                                                                                           |
| `apply_locks`                  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes any locks that were present on the exported data to be applied to the data when importing, unless a more restrictive lock mode is in effect for the current session.<br>`FALSE` (the default) ignores any locks on rows in the staging table, but instead always uses the lock mode is in effect for the current session.                                                                                                                                                                                                                  |
| `enforceUCFlag`                | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) enforces any unique constraints defined on `to_table`, ensuring that the import operation does not violate any such constraints.<br>`FALSE` does not enforce any unique constraints defined on `to_table` for the import operation.                                                                                                                                                                                                                                                                                                 |
| `enforceRICFlag`               | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) enforces any referential integrity constraints defined on `to_table`, ensuring that the import operation does not violate any such constraints.<br>`FALSE` does not enforce any referential integrity constraints defined on `to_table` for the import operation.                                                                                                                                                                                                                                                                   |
| `auto_commit`                  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

All data that satisfies the `where_clause` parameter value in the staging table named `staging_table` and the `import_scope` parameter value is imported into the version-enabled table named `to_table`.

The data must have been previously exported to the staging table using the Export procedure.

Each row of data to be imported is considered to be one of the following: inserted, updated, or deleted in `from_workspace` (that is, modified data); or data that was not modified in `from_workspace` but can be seen in it (that is, ancestor data). If data is exported from the `LIVE` workspace, it is all modified data.

An exception is raised if one or more of the following apply:

- A specified table or workspace does not exist.

- `staging_table` is not in a valid format for the import operation.

- `to_table` is not a version-enabled table, or does not have an appropriate definition (for example, contains columns not in the staging table).

- `from_workspace` is null and `staging_table` contains versioning information.

- `ancestor_savepoint_name` is not a valid savepoint in `ancestor_savepoint_workspace`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

See also [Import and Export Considerations](introduction-to-workspace-manager.md).

#### Examples

The following example imports modified data from the staging table `COLA_MARKETING_BUDGET_STG` in workspace `B_focus_2` into the `COLA_MARKETING_BUDGET` table in workspace `B_Focus_1`. (The `EXECUTE` statement is actually on a single line.)

    EXECUTE DBMS_WM.Import(staging_table => 'COLA_MARKETING_BUDGET_STG',
      to_table => 'COLA_MARKETING_BUDGET', to_workspace => 'B_focus_1',
      from_workspace => 'B_focus_2');

**Parent topic:** DBMS_WM Package: Reference

### 4.52 Import_Schemas

Imports the entire Workspace Manager installation from a dump file that had been created by the Export_Schemas procedure. Uses the Oracle Data Pump Import utility.

#### Syntax

    DBMS_WM.Import_Schemas(
       job_name           IN VARCHAR2,
       alt_schema         IN VARCHAR2 DEFAULT 'WMSYS_N',
       ignore_last_error  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-43 Import_Schemas Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `job_name`          | Name of the Data Pump job to be used for the import operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `alt_schema`        | Name of the database schema to be used for temporary storage of Workspace Manager metadata. The default is `WMSYS_N`. This schema must not already exist when the procedure is called, and it is automatically dropped when the procedure completes successfully.                                                                                                                                                                                                                                                                                                              |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the Import_Schemas procedure. Information about the last error is stored in the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view, which is described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the Import_Schemas procedure. |

#### Usage Notes

This procedure uses a dump file that had been created using the Export_Schemas procedure. There must be no existing version-enabled tables or workspaces, other than `LIVE`, before you call this procedure. All objects of the schemas contained in the dump file are imported. If any system or workspace privileges or any privileges on version-enabled tables were granted to users that were not contained in the generated dump file, those schemas must be created before you call this procedure; otherwise, the grants will be lost.

This procedure makes use of an already existing Data Pump Import job. When you create this job using the `DBMS_DATAPUMP.OPEN` procedure, the `operation` parameter must be set to `IMPORT` and the `mode` parameter must be set to `FULL`. The dump file(s) and log file should also be specified before you call this procedure. No procedures that modify or limit what gets imported (such as `DBMS_DATAPUMP.METADATA_FILTER`) should be executed on this job. . The Data Pump job should not be created while using SYSDBA privileges.

The schema specified by the `alt_schema` parameter cannot exist before you call this procedure. It must also be the same schema as specified for `alt_schema` when you called the Export_Schemas procedure.

For information about using the Data Pump Utility, see [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md).

If a call to the Import_Schemas procedure fails, you should try to fix the cause of the error. Examine the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view where the STATE column is equal to `IMPORT` to see the SQL statement and error message. Fix the cause of the error, and then call the Import_Schemas procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you can ignore the error by calling the Import_Schemas procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

If the Import_Schemas procedure fails and if you must execute the procedure again, and if a row for this procedure exists in the [DBA_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary view, the procedure will continue to use the original Data Pump job that was specified (you do not need to create a new job). However, if the SQL statements being executed attempt to use the original job but that job no longer exists, you must set the `ignore_last_error` parameter to `TRUE` and execute the Import_Schemas procedure again.

An exception is raised if one or more of the following apply:

- `job_name` does not exist.

- `alt_schema` already exists.

- The executing user does not have the DATAPUMP_IMP_FULL_DATABASE role.

- Errors exist in the `WMSYS` or user schemas.

See also [Import and Export Considerations](introduction-to-workspace-manager.md).

#### Examples

The following example imports the Workspace Manager metadata using the Oracle Data Pump job named `IMPORT_OWM_SCHEMAS`.

    DECLARE
      job_name varchar2(128) := upper('IMPORT_OWM_SCHEMAS') ;
      dpj number ;
    BEGIN
      dpj := dbms_datapump.open('IMPORT', 'FULL', null, job_name, 'COMPATIBLE') ;
      dbms_datapump.add_file(dpj, 'owm_schema.dmp', 'DUMP_DIR') ;
      dbms_datapump.add_file(dpj, 'owm_schema_import.log', 'DUMP_DIR', filetype=>dbms_datapump.KU$_FILE_TYPE_LOG_FILE) ;
      dbms_wm.import_schemas(job_name) ;
      dbms_datapump.detach(dpj);

    exception when others then
      dbms_datapump.detach(dpj);
      raise ;
    END;
    /

The following example imports the Workspace Manager metadata from the Oracle Cloud Infrastructure Object Storage using the `dbms_datapump` API job. The example uses a pre-authenticated request URL to access the `owm_test.dmp` dump file in the Object Storage. Ensure that Oracle Workspace Manager is enabled on your Autonomous Database instance. See [Enable Oracle Workspace Manager on Autonomous Database](http://www.oracle.com/pls/topic/lookup?ctx=en/cloud/paas/autonomous-database&id=GUID-EE7225CC-6EB1-44F5-BA39-272BBAD03448) for more information.

**Note:**

Oracle Workspace Manager is enabled on Autonomous Database Serverless only in selected cloud regions. The following table lists the cloud regions that support Oracle Workspace Manager:

Table 4-44 Supported Cloud Regions for Oracle Workspace Manager

| Region Name                         | Region Identifier |
|:------------------------------------|:------------------|
| Singapore (Singapore)               | ap-singapore-1    |
| France South (Marseille)            | eu-marseille-1    |
| UAE Central (Abu Dhabi)             | me-abudhabi-1     |
| Italy Northwest (Milan)             | eu-milan-1        |
| Sweden Central (Stockholm)          | eu-stockholm-1    |
| South Africa Central (Johannesburg) | af-johannesburg-1 |
| France Central (Paris)              | eu-paris-1        |

    DECLARE
      hdl          NUMBER;         -- Datapump handle
      dumpFile     VARCHAR2(1024)  := 'https://objectstorage.<region>.oraclecloud.com/p/<encrypted_string>/n/<namespace-string>/b/<bucket_name>/o/owm_test.dmp';
      dumpType     NUMBER          := dbms_datapump.ku$_file_type_uridump_file;
      credName     VARCHAR2(1024)  := 'CRED_NAME';
      logFile      VARCHAR2(1024)  := 'import_test.log';
      logDir       VARCHAR2(20)    := 'DATA_PUMP_DIR';
      logType      NUMBER          := dbms_datapump.ku$_file_type_log_file;
      job_name      VARCHAR2(128)   := DBMS_SCHEDULER.GENERATE_JOB_NAME('IMP_SD_' );
    BEGIN
      hdl := dbms_datapump.open('IMPORT', 'FULL', null, job_name, 'COMPATIBLE');
      dbms_output.put_line(' LOCAL ' ||job_name);
      dbms_datapump.add_file(hdl, dumpFile, credName, null, dumpType);
      dbms_datapump.add_file(hdl, logfile, logdir, null, logType);
      dbms_wm.import_schemas('ADMIN.' ||   job_name, 'WMSYS_N') ;
    EXCEPTION
      WHEN OTHERS THEN
        dbms_output.put_line(SQLERRM);
        dbms_output.put_line( dbms_utility.format_error_backtrace );
    END;
    /

**Parent topic:** DBMS_WM Package: Reference

### 4.53 Initialize_After_Import

Creates (initializes) a version enabled topology that was imported from another database.

#### Format

    DBMS_WM.Add_Topo_Geometry_Layer(     
      topology        IN VARCHAR2,      
      tg_layer_owner  IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table 4-45 Initialize_After_Import Procedure Parameters

| Parameter        | Description                                                                                          |
|:-----------------|:-----------------------------------------------------------------------------------------------------|
| `topology`       | Topology that was imported from another database.                                                    |
| `tg_layer_owner` | Owner of the topology layer. If this parameter is null (the default), the current user is the owner. |

#### Usage Notes

This procedure creates the specified version-enabled topology and related database structures, adjusts the topology ID values in all feature tables, and creates the feature layers in the correct order. It also generates the necessary Workspace Manager metadata on the spatial topology index tables that get created. For information about Workspace Manager support for topologies, see [Spatial and Graph Topology Support](introduction-to-workspace-manager.md).

After importing a version-enabled topology using either a full database import or the DBMS_WM.Import_Schemas procedure, you must do the following (with the last step being to execute the DBMS_WM.Initialize_After_Import procedure):

1.  Connect to the target database, that is, the database in which to create a topology with the same name, structures, and data as the topology exported from the source database. Connect as the user for the schema that is to own the topology to be created.

2.  Ensure that the target database does not already contain a topology with the same name as the topology in the .dmp file.

3.  Perform the import using either a full database import or the DBMS.Import_Schemas procedure.

4.  Execute the DBMS_WM.Initialize_After_Import procedure. (Do not execute the SDO_TOPO.Initialize_After_Import procedure.)

#### Examples

The following example creates the topology named `CITY_DATA` using information from the imported tables, including CITY_DATA_EXP\$, which was created using the SDO_TOPO.Prepare_For_Export procedure.

    EXECUTE DBMS_WM.INITIALIZE_AFTER_IMPORT('CITY_DATA');

**Parent topic:** DBMS_WM Package: Reference

### 4.54 IsWorkspaceOccupied

Checks whether or not a workspace has any active sessions.

#### Syntax

    DBMS_WM.IsWorkspaceOccupied(
       workspace  IN VARCHAR2) RETURN VARCHAR2;

#### Parameters

Table 4-46 IsWorkspaceOccupied Function Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

This function returns `YES` if the workspace has any active sessions, and it returns `NO` if the workspace has no active sessions.

An exception is raised if the `LIVE` workspace is specified or if the user does not have the privilege to access the workspace.

#### Examples

The following example checks if any sessions are in the `B_focus_2` workspace.

    SELECT DBMS_WM.IsWorkspaceOccupied('B_focus_2') FROM DUAL;

    DBMS_WM.ISWORKSPACEOCCUPIED('B_FOCUS_2')
    --------------------------------------------------------------------------------
    YES

**Parent topic:** DBMS_WM Package: Reference

### 4.55 LockRows

Controls access to versioned rows in a specified table and to corresponding rows in the parent workspace.

#### Syntax

    DBMS_WM.LockRows(
       workspace     IN VARCHAR2,
       table_name    IN VARCHAR2,
       where_clause  IN VARCHAR2 DEFAULT '',
       lock_mode     IN VARCHAR2 DEFAULT 'E',
       Xmin          IN NUMBER DEFAULT NULL,
       Ymin          IN NUMBER DEFAULT NULL,
       Xmax          IN NUMBER DEFAULT NULL,
       Ymax          IN NUMBER DEFAULT NULL);

#### Parameters

Table 4-47 LockRows Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace. The latest versions of rows visible from the workspace are locked. If a row has not been modified in this workspace, the locked version could be in an ancestor workspace. The name is case-sensitive.<br>A value of `NONE` can be used if `lock_mode` is set to `VE` (version-exclusive). This causes the latest versions of rows to be locked, regardless of the workspaces from which they are visible.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `table_name`   | Name of the table or (if `Xmin`, `Ymin`, `Xmax`, and `Ymax` are specified) Spatial and Graph topology in which rows are to be locked. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `where_clause` | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be locked. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If `where_clause` is not specified, all rows in `table_name` are locked.<br>Do not specify the `where_clause` parameter if `table_name` specifies a Spatial and Graph topology name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `lock_mode`    | Mode with which to set the locks: `E` (exclusive), `WE` (workspace-exclusive), `VE` (version-exclusive), or `S` (shared). The default is `E`.<br>`E` (exclusive) mode locks the rows in the previous version and the corresponding rows in the current version; no other users in the workspace for either version can change any values.<br>`WE` (workspace-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values in the current workspace; however, other users in other workspaces can change the values.<br>`VE` (version-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values; no other users (in any workspace) can change the values.<br>`S` (shared) mode locks the rows in the previous version and the corresponding rows in the current version; however, other users in the workspace for the current version (but no users in the workspace for the previous version) can change values in these rows. |
| `Xmin, Ymin`   | For Oracle Spatial and Graph topologies only (see [Locking Considerations with Topologies](introduction-to-workspace-manager.md)), the X and Y coordinate values, respectively, of the lower-left corner of the window containing the rows to be locked.You must specify these parameters if you specified a topology name for `table_name`; otherwise, do not specify these parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `Xmax, Ymax`   | For Oracle Spatial and Graph topologies only (see [Locking Considerations with Topologies](introduction-to-workspace-manager.md)), the X and Y coordinate values, respectively, of the upper-right corner of the window containing the rows to be locked.You must specify these parameters if you specified a topology name for `table_name`; otherwise, do not specify these parameters.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

#### Usage Notes

This procedure affects Workspace Manager locking, which occurs in addition to any standard Oracle database locking. For an explanation of Workspace Manager locking, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).

This procedure does not affect whether Workspace Manager locking is set on or off (determined by the SetLockingON and SetLockingOFF procedures).

To unlock rows, use the UnlockRows procedure.

For information about Workspace Manager locking for tables in an Oracle Spatial and Graph topology, see [Locking Considerations with Topologies](introduction-to-workspace-manager.md).

#### Examples

The following example locks rows in the `EMPLOYEES` table where `last_name = 'Smith'` in the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.LockRows ('NEWWORKSPACE', 'employees', 'last_name = ''Smith''');

**Parent topic:** DBMS_WM Package: Reference

### 4.56 MergeTable

Applies changes to one or more tables (all rows or as specified in the `WHERE` clause) in a workspace to its parent workspace.

For a multiparent workspace (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)), applies changes to one or more tables (all rows or as specified in the `WHERE` clause) from all non-root workspaces in the directed acyclic graph to the multiparent root workspace.

#### Syntax

    DBMS_WM.MergeTable(
       workspace         IN VARCHAR2,
       table_id          IN VARCHAR2,
       where_clause      IN VARCHAR2 DEFAULT '',
       create_savepoint  IN BOOLEAN DEFAULT FALSE,
       remove_data       IN BOOLEAN DEFAULT FALSE,
       auto_commit       IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-48 MergeTable Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`        | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `table_id`         | Name of the table or tables containing rows to be merged into the parent workspace. To specify multiple tables, separate the names with commas (for example, `'table1, table2'`). The names are not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                              |
| `where_clause`     | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be merged into the parent workspace. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `table_name` are merged.                                                                                                                                                 |
| `create_savepoint` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` creates an implicit savepoint in the parent workspace before the merge operation. For a multiparent workspace, creates an implicit savepoint in the multiparent root workspace before the merge operation. (Implicit and explicit savepoints are described in [Using Savepoints](introduction-to-workspace-manager.md).)<br>`FALSE` (the default) does not create an implicit savepoint in the parent workspace before the merge operation.                                                                                                       |
| `remove_data`      | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` removes the data in the table (as specified by the `where_clause` parameter) in the child workspace. For a multiparent workspace, it removes the data in the table (as specified by the `where_clause` parameter) in the non-root workspaces in the directed acyclic graph. The `remove_data` option is permitted only if `workspace` has no child workspaces (that is, it is a leaf workspace).<br>`FALSE` (the default) does not remove the data in the table in the child workspace.                                                           |
| `auto_commit`      | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

All data that satisfies the `where_clause` parameter value in the version-enabled table named `table_name` in `workspace` is applied to the parent workspace of `workspace`.

If the `create_savepoint` parameter value is `true`, an implicit savepoint is created only if one does not already exist on the intended version. This intended version is the LATEST version in the parent workspace if that version contains modified rows.  Otherwise, this is the previous version to the LATEST version as long as the workspace has more than a single version.

Any locks that are held by rows being merged are released.

If there are conflicts between the workspace being merged and its parent workspace, the merge operation fails and the user must manually resolve conflicts using the \<table_name\>\_CONF view. (Conflict resolution is explained in [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).)

A table cannot be merged in the `LIVE` workspace (because that workspace has no parent workspace).

An exception is raised if one or more of the following apply:

- The user does not have access to `table_id`.

- The user does not have the `MERGE_WORKSPACE` privilege for `workspace` or the `MERGE_ANY_WORKSPACE` privilege.

- `remove_data` is `TRUE` and there are any child workspaces of any workspace to be removed.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The merge involving a multiparent workspace would cause the violation of a referential integrity constraint or unique constraint in any continually refreshed child workspace of the multiparent root workspace.

#### Examples

The following example merges changes to the `EMP` table (in the `USER3` schema) where `last_name = 'Smith'` in `NEWWORKSPACE` to its parent workspace.

    EXECUTE DBMS_WM.MergeTable ('NEWWORKSPACE', 'user3.emp', 'last_name = ''Smith''');

**Parent topic:** DBMS_WM Package: Reference

### 4.57 MergeWorkspace

Applies all changes in a workspace to its parent workspace, and optionally removes the workspace.

For a multiparent workspace (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)), applies all changes in the workspace to all other workspaces in the directed acyclic graph, and optionally removes the non-root workspaces in the directed acyclic graph.

#### Syntax

    DBMS_WM.MergeWorkspace(
       workspace         IN VARCHAR2,
       create_savepoint  IN BOOLEAN DEFAULT FALSE,
       remove_workspace  IN BOOLEAN DEFAULT FALSE,
       auto_commit       IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-49 MergeWorkspace Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`        | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `create_savepoint` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` creates an implicit savepoint in the parent workspace before the merge operation. (Implicit and explicit savepoints are described in [Using Savepoints](introduction-to-workspace-manager.md).)<br>`FALSE` (the default) does not create an implicit savepoint in the parent workspace before the merge operation.                                                                                                                                                                                                                                |
| `remove_workspace` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` removes `workspace` after the merge operation. For a multiparent workspace, all non-root workspaces in the directed acyclic graph are removed.<br>`FALSE` (the default) does not remove `workspace` after the merge operation; the workspace continues to exist.                                                                                                                                                                                                                                                                                  |
| `auto_commit`      | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

All data in all version-enabled tables in `workspace` is merged to the parent workspace of `workspace`, and `workspace` is removed if `remove_workspace` is `TRUE`.

If `workspace` is a continually refreshed child workspace, an exclusive lock is taken on the parent workspace. This exclusive lock blocks other operations on the parent workspace, such as GotoWorkspace, which would try to take a shared lock.

If the `create_savepoint` parameter value is `true`, an implicit savepoint is created only if one does not already exist on the intended version. This intended version is the LATEST version in the parent workspace if that version contains modified rows.  Otherwise, this is the previous version to the LATEST version as long as the workspace has more than a single version.

Only the current row version for any given row is merged into the parent workspace. To retain all intermediate row versions and historical copies in the child workspace, the value of `remove_workspace` must be `FALSE` (the default). For more information about how Workspace Manager creates row versions and manages historical copies, see [Creation of Row Versions and Historical Copies](introduction-to-workspace-manager.md).

While this procedure is executing, the current workspace is frozen in `NO_ACCESS` mode and the parent workspace is frozen in `READ_ONLY` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

If there are conflicts between the workspace being merged and its parent workspace, the merge operation fails and the user must manually resolve conflicts using the \<table_name\>\_CONF view. (Conflict resolution is explained in [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).)

If the `remove_workspace` parameter value is `TRUE`, the workspace to be merged must be a leaf workspace, that is, a workspace with no descendant workspaces. (For an explanation of workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).)

To update rows in the child workspace and merge those changes into the parent workspace in the same transaction, you must specify `autocommit=FALSE` and ensure that no other session (that is, other than the one performing the update transaction) is in the child workspace.

An exception is raised if one or more of the following apply:

- The user does not have the `MERGE_WORKSPACE` privilege for `workspace` or the `MERGE_ANY_WORKSPACE` privilege.

- The user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers).

- `auto_commit` is `TRUE` and there is an open database transaction in any workspace under `workspace` in the workspace hierarchy.

- `remove_workspace` is `TRUE` and there are any sessions in any workspaces under `workspace` in the workspace hierarchy.

- `remove_workspace` is `TRUE` and there are any child workspaces of any workspace to be removed.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- The merge of a multiparent workspace would cause the violation of a referential integrity constraint or unique constraint in any continually refreshed child workspace of the multiparent root workspace.

#### Examples

The following example merges changes in `NEWWORKSPACE` to its parent workspace.

    EXECUTE DBMS_WM.MergeWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.58 Move_Proc

Moves the Workspace Manager metadata to a specified tablespace.

#### Syntax

    DBMS_WM.Move_Proc(
       dest_tablespace  IN VARCHAR2 DEFAULT 'SYSAUX');

#### Parameters

Table 4-50 Move_Proc Procedure Parameters

| Parameter         | Description                                                                                                    |
|:------------------|:---------------------------------------------------------------------------------------------------------------|
| `dest_tablespace` | The table space to which to move the Workspace Manager metadata. The default value is the `SYSAUX` tablespace. |

#### Usage Notes

The Workspace Manager metadata (views, internal tables, and other objects) is by default stored in the default tablespace of the WMSYS user. You cannot directly control the size of the Workspace Manager metadata, but you can control its placement by using this procedure to move the metadata from its current tablespace to a different tablespace. If you call this procedure without specifying the `dest_tablespace` parameter, the Workspace manager metadata is moved to the SYSAUX tablespace.

Before you move the metadata, you can use the GetWMMetadataSpace function to determine the approximate minimum space that you will need to have available in the tablespace into which you are considering moving the Workspace Manager metadata.

#### Examples

The following example moves the Workspace Manager metadata to the `TBLSP_1` tablespace.

    EXECUTE DBMS_WM.Move_proc('TBLSP_1');

**Parent topic:** DBMS_WM Package: Reference

### 4.59 PurgeTable

Removes rows (all rows, or as limited by any combination of several parameters) from a version-enabled table, and optionally inserts them into an archive table.

#### Syntax

    DBMS_WM.PurgeTable(
       table_id       IN VARCHAR2,
       archive_table  IN VARCHAR2,
       where_clause   IN VARCHAR2,
       workspace      IN VARCHAR2 DEFAULT 'LIVE',
       savepoint_name IN VARCHAR2 DEFAULT NULL,
       instant        IN TIMESTAMP WITH TIME ZONE DEFAULT NULL,
       purgeAfter     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-51 PurgeTable Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_id`       | Name of the table containing the data to be exported. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                  |
| `archive_table`  | Name of the table into which to insert the purged rows. If this parameter is specified as NULL, purged rows are not archived. If this parameter is specified as other than NULL and if there is an open transaction, the transaction is committed before the table is created, and a new transaction is opened.                                                                                                        |
| `where_clause`   | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be purged. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `table_name` are purged. |
| `workspace`      | Name of the workspace from which to purge the data. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                        |
| `savepoint_name` | Name of a savepoint: only data in the workspace either after or before (depending on the `purgeAfter` value) the time the savepoint was created is purged.<br>You cannot specify both the `savepoint_name` and `instant` parameters.                                                                                                                                                                                   |
| `instant`        | Date/time specification: only data that was in the workspace either after or before (depending on the `purgeAfter` value) this time is purged.<br>You cannot specify both the `savepoint_name` and `instant` parameters.                                                                                                                                                                                               |
| `purgeAfter`     | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes rows in the workspace after any specified `savepoint_name` or `instant` value to be purged.<br>`FALSE` causes rows in the workspace before any specified `savepoint_name` or `instant` value to be purged.                                                                                                                                         |

#### Usage Notes

This procedure removes rows from a version-enabled table that is rooted at workspace. If the `purgeAfter` parameter value is `TRUE` (the default), applicable child rows rooted at the specified workspace are removed; if the `purgeAfter` parameter value is `FALSE`, applicable ancestor rows rooted at the specified workspace are removed.

You can use the `where_clause` parameter and the `savepoint_name` or `instant` parameter to limit the rows that are purged. For most uses of the procedure, you will probably want to specify a `where_clause` value to limit the rows to be purged; otherwise all rows are purged (unless limited by the `savepoint_name` or `instant` parameter).

An exclusive lock is obtained on the version-enabled table for the duration of the procedure.

#### Examples

The following example purges any rows where the `ID` (primary ley) column value is 20 in the `USER2.TEST` table of the `project` workspace and its descendent workspaces. (The `EXECUTE` statement is actually on a single line.)

    EXECUTE DBMS_WM.PurgeTable('user2.test', where_clause=>'id=20', workspace=>'project', purgeAfter=>TRUE);

**Parent topic:** DBMS_WM Package: Reference

### 4.60 RecoverAllMigratingTables

Attempts to complete the migration process on all tables that were left in an inconsistent state after the Workspace Manager migration procedure failed.

#### Syntax

    DBMS_WM.RecoverAllMigratingTables(
       ignore_last_error IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-52 RecoverAllMigratingTables Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the migration process. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the migration process. |

#### Usage Notes

If an error occurs while upgrading (migrating) to the current Workspace Manager release, one or more version-enabled tables can be left in an inconsistent state. If the upgrade procedure fails, you should try to fix the cause of the error (examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) or [ALL_WM_VT_ERRORS](workspace-manager-views.md) metadata view to see the SQL statement and error message), and then call the RecoverMigratingTable procedure (for a single table) or RecoverAllMigratingTables procedure (for all tables) with the default `ignore_last_error` parameter value of `FALSE`, to try to complete the upgrade process.

However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the RecoverMigratingTable or RecoverAllMigratingTables procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

#### Examples

The following example attempts to recover all version-enabled tables that were left in an inconsistent state when the upgrade procedure failed.

    EXECUTE DBMS_WM.RecoverAllMigratingTables;

The following example attempts to recover all version-enabled tables that were left in an inconsistent state when the upgrade procedure failed, and it ignores the last error that caused the upgrade procedure to fail.

    EXECUTE DBMS_WM.RecoverAllMigratingTables(TRUE);

**Parent topic:** DBMS_WM Package: Reference

### 4.61 RecoverFromDroppedUser

Performs necessary operations after the dropping of one or more database users that owned one or more version-enabled tables.

#### Syntax

    DBMS_WM.RecoverFromDroppedUser(
       ignore_last_error IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-53 RecoverFromDroppedUser Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the RecoverFromDroppedUser procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the RecoverFromDroppedUser procedure. |

#### Usage Notes

If a database user with one or more version-enabled tables is dropped, you must execute this procedure as soon as possible. This procedure removes any foreign key constraints in existing tables that depended on any of the version-enabled tables that were dropped as a result of dropping the user that owned these tables. This procedure also fixes any invalid database metadata.

If a call to the RecoverFromDroppedUser procedure fails, the table is left in an inconsistent state. If this occurs, you should try to fix the cause of the error (examine the [DBA_WM_VT_ERRORS](workspace-manager-views.md) metadata view to see the SQL statement and error message), and then call the RecoverFromDroppedUser procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the RecoverFromDroppedUser procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

To execute this procedure, you must connect to the database instance as a user with SYSDBA privileges.

#### Examples

The following drops a user named `HERMAN` that owns one or more version-enabled tables, and then performs the necessary operations after the drop operation.

    DROP USER herman CASCADE;
    EXECUTE DBMS_WM.RecoverFromDroppedUser;

**Parent topic:** DBMS_WM Package: Reference

### 4.62 RecoverMigratingTable

Attempts to complete the migration process on a table that was left in an inconsistent state after the Workspace Manager migration procedure failed.

#### Syntax

    DBMS_WM.RecoverMigratingTable(
       table_name        IN VARCHAR2,
       ignore_last_error IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-54 RecoverMigratingTable Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`        | Name of the version-enabled table to be recovered from the migration error. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the migration process. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the migration process. |

#### Usage Notes

If an error occurs while upgrading to the current Workspace Manager release, one or more version-enabled tables can be left in an inconsistent state. If the upgrade procedure fails, you should try to fix the cause of the error (examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) or [ALL_WM_VT_ERRORS](workspace-manager-views.md) metadata view to see the SQL statement and error message), and then call the RecoverMigratingTable procedure (for a single table) or RecoverAllMigratingTables procedure (for all tables) with the default `ignore_last_error` parameter value of `FALSE`, to try to complete the upgrade process.

However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the RecoverMigratingTable or RecoverAllMigratingTables procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

An exception is raised if `table_name` does not exist or is not version-enabled.

#### Examples

The following example attempts to recover the `COLA_MARKETING_BUDGET` table from the error that caused the upgrade procedure to fail.

    EXECUTE DBMS_WM.RecoverMigratingTable('COLA_MARKETING_BUDGET');

The following example attempts to recover the `COLA_MARKETING_BUDGET` table and ignores the last error that caused the upgrade procedure to fail.

    EXECUTE DBMS_WM.RecoverMigratingTable('COLA_MARKETING_BUDGET', TRUE);

**Parent topic:** DBMS_WM Package: Reference

### 4.63 RefreshTable

Applies to a workspace all changes made to a table (all rows or as specified in the `WHERE` clause) in its parent workspace.

For a multiparent workspace (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)), applies changes from the non-leaf workspaces in the directed acyclic graph to the specified leaf workspace for a specified table. (The table data in the intermediate workspaces is not changed.)

#### Syntax

    DBMS_WM.RefreshTable(
       workspace     IN VARCHAR2,
       table_id      IN VARCHAR2,
       where_clause  IN VARCHAR2 DEFAULT '',
       auto_commit   IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-55 RefreshTable Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `table_id`     | Name of the table containing the rows to be refreshed using values from the parent workspace. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `where_clause` | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be refreshed from the parent workspace. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If `the where_clause parameter` is not specified, all rows in `table_name` are refreshed.                                                                                                                                           |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

This procedure applies to `workspace` all changes in rows that satisfy the `where_clause` parameter value in the version-enabled table named `table_id` in the parent workspace since the time when `workspace` was created or last refreshed.

If there are conflicts between the workspace being refreshed and its parent workspace, the refresh operation fails and the user must manually resolve conflicts using the \<table_name\>\_CONF view. (Conflict resolution is explained in [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).)

This procedure is ignored if `workspace` is a continually refreshed workspace.

A table cannot be refreshed in the `LIVE` workspace (because that workspace has no parent workspace).

An exception is raised if the user does not have access to `table_id`, if the user does not have the `MERGE_WORKSPACE` privilege for `workspace` or the `MERGE_ANY_WORKSPACE` privilege, or if `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example refreshes `NEWWORKSPACE` by applying changes made to the `EMPLOYEES` table where `last_name = 'Smith'` in its parent workspace.

    EXECUTE DBMS_WM.RefreshTable ('NEWWORKSPACE', 'employees', 'last_name = ''Smith''');

**Parent topic:** DBMS_WM Package: Reference

### 4.64 RefreshWorkspace

Applies to a workspace all changes made in its parent workspace.

For a multiparent workspace (explained in [Multiparent Workspaces](introduction-to-workspace-manager.md)), applies changes from the non-leaf workspaces in the directed acyclic graph to the specified leaf workspace. The changes are propagated beginning with the multiparent root workspace and continuing with the intermediate workspaces.

#### Syntax

    DBMS_WM.RefreshWorkspace(
       workspace    IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE,
       copy_data    IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-56 RefreshWorkspace Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`   | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                           |
| `copy_data`   | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` causes all changes in the parent workspace since the creation or last refresh of the child workspace to be copied to the child workspace. No changes occur in any descendent of the child workspace, and the history of changes to the child workspace is preserved.<br>`FALSE` (the default) causes minimal data to be copied to the child workspace. The parent version of the child workspace is updated in order for the child workspace and its descendents to have access to the modified rows from the parent workspace. No history of changes to the child workspace is recorded for the operation. |

#### Usage Notes

This procedure applies to `workspace` all changes made to version-enabled tables in the parent workspace since the time when `workspace` was created or last refreshed.

If there are conflicts between the workspace being refreshed and its parent workspace, the refresh operation fails and the user must manually resolve conflicts using the \<table_name\>\_CONF view. (Conflict resolution is explained in [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).)

The specified workspace and the parent workspace are frozen in `READ_ONLY` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

The `LIVE` workspace cannot be refreshed (because it has no parent workspace).

This procedure is ignored if `workspace` is a continually refreshed workspace.

An exception is raised if the user does not have the `MERGE_WORKSPACE` privilege for `workspace` or the `MERGE_ANY_WORKSPACE` privilege, if the user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers), or if `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example refreshes `NEWWORKSPACE` by applying changes made in its parent workspace.

    EXECUTE DBMS_WM.RefreshWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.65 RemoveAsParentWorkspace

Removes a workspace as a parent workspace in a multiparent workspace environment.

#### Syntax

    DBMS_WM.RemoveAsParentWorkspace(
       mp_leafworkspace  IN VARCHAR2,
       parent_workspace  IN VARCHAR2,
       auto_commit       IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-57 RemoveAsParentWorkspace Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mp_leaf_workspace` | Name of the child workspace (multiparent leaf workspace) from which to remove `parent_workspace` as a parent workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `parent_workspace`  | Name of the workspace to remove as a parent workspace of `mp_leaf_workspace`. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `auto_commit`       | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

This procedure is part of the support for the multiparent workspaces feature, which is described in [Multiparent Workspaces](introduction-to-workspace-manager.md). This procedure must be used only on a parent workspace that was previously added to the child workspace using the AddAsParentWorkspace procedure.

This procedure does not remove any workspaces. It only makes `parent_workspace` no longer a parent workspace of `mp_leaf_workspace`.

An exception is raised if one or more of the following apply:

- `mp_leaf_workspace` or `parent_workspace` does not exist.

- `mp_leaf_workspace` has versioned any data in `parent_workspace` or an ancestor of `parent_workspace`, and this workspace would no longer be an ancestor of `mp_leaf_workspace` if the operation were to be performed.

- There are any sessions with open database transactions in `mp_leaf_workspace`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example removes `Workspace4` as a parent workspace of `Workspace3`. (See the hierarchy illustration in [Multiparent Workspaces](introduction-to-workspace-manager.md).)

    EXECUTE DBMS_WM.RemoveAsParentWorkspace ('Workspace3', 'Workspace4');

**Parent topic:** DBMS_WM Package: Reference

### 4.66 RemoveDeferredWorkspaces

Removes the rows and locks from any version enabled tables associated with workspaces that were removed by specifying either `FAST` or `REMOVE_LOCKS` for the `defer_option` parameter of the RemoveWorkspace or RemoveWorkspaceTree procedure.

#### Syntax

    DBMS_WM.RemoveDeferredWorkspaces(
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-58 RemoveWorkspace Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

After a workspace has been removed using RemoveWorkspace or RemoveWorkspaceTree and specifying `FAST` or `REMOVE_LOCKS` for the `defer_option` parameter, the only way to remove the rows associated with that workspace is to execute this procedure. In addition, if `FAST` was used, any locks that still remain will be released.

This procedure removes the rows and any remaining metadata for all workspaces that had deferred removal. It is not possible to specify a subset of the deferred workspaces to be removed. Any workspaces that need to removed after being deferred will appear in the DBA_WORKSPACES view with a `DEFERRED_REMOVAL` value for the FREEZE_MODE column. Until a workspace in this state is removed, it is not possible to create a new workspace using the same name.

WM_ADMIN privileges are necessary to execute this procedure.

#### Examples

The following example removes the rows and locks from any version enabled tables associated with workspaces that were removed by specifying either `FAST` or `REMOVE_LOCKS` for the `defer_option` parameter of the RemoveWorkspace or RemoveWorkspaceTree procedure.

    EXECUTE DBMS_WM.RemoveDeferredWorkspaces;

**Parent topic:** DBMS_WM Package: Reference

### 4.67 RemoveUserDefinedHint

Removes a user-defined hint: that is, causes the default optimizer hint to be used with SQL statements executed by the DBMS_WM package on a specified version-enabled table or all version-enabled tables.

#### Syntax

    DBMS_WM.RemoveUserDefinedHint(
       hint_id   IN NUMBER,
       table_id  IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table 4-59 RemoveUserDefinedHint Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `hint_id`  | Numeric ID that uniquely identifies the user-defined hint. Must match an existing hint ID previously specified in a call to the AddUserDefinedHint procedure.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `table_id` | Name of the table from which to remove the hint. The name is not case-sensitive.<br>If this value is null and if the `table_id` parameter was null in the call to the AddUserDefinedHint procedure that added the hint, the hint is no longer used with any version-enabled tables for any SQL statements that specify the hint ID.<br>However, if this value is null and if the `table_id` parameter was not null in the call to the AddUserDefinedHint procedure that added the hint, the `RemoveUserDefinedHint` procedure will not remove any hints that were defined for the originally specified tables. |

#### Usage Notes

Use this procedure only to remove or modify the effect of a user-defined hint that you previously specified using the AddUserDefinedHint procedure. (See the Usage Notes for that procedure.)

#### Examples

The following example removes, for the SCOTT.TABLE1 table, the user-defined hint from SQL statements associated with the hint with the hint ID 1101, and causes the default hint to be used instead.

    EXECUTE DBMS_WM.RemoveUSerDefinedHint (1101, 'scott.table1');

**Parent topic:** DBMS_WM Package: Reference

### 4.68 RemoveWorkspace

Discards all row versions associated with a workspace and deletes the workspace.

#### Syntax

    DBMS_WM.RemoveWorkspace(
       workspace    IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE,
       defer_option IN VARCHAR2 DEFAULT NULL;

#### Parameters

Table 4-60 RemoveWorkspace Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |
| `defer_option` | Specifies whether rows and locks associated with the workspace for version-enabled tables are removed or if the removal is to be deferred until later. This allows you to accept or override the value of the `REMOVEWORKSPACE_DEFERRED` system parameter.<br>The value can be null, `OFF`, `FAST`, or `REMOVE_LOCKS`. For an explanation of the `REMOVEWORKSPACE_DEFERRED` system parameter and its possible values, see [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).                                                                                       |

#### Usage Notes

The RemoveWorkspace operation can only be performed on leaf workspaces (the bottom-most workspaces in a branch in the hierarchy). For an explanation of database workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).

If the workspace being removed is a child workspace, its parent workspace is exclusively locked for the duration of the operation.

There must be no other users in the workspace being removed.

An exception is raised if the user does not have the `REMOVE_WORKSPACE` privilege for `workspace` or the `REMOVE_ANY_WORKSPACE` privilege, if the user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers), or if `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example removes the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.RemoveWorkspace('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.69 RemoveWorkspaceTree

Discards all row versions associated with a workspace and its descendant workspaces, and deletes the affected workspaces.

#### Syntax

    DBMS_WM.RemoveWorkspaceTree(
       workspace    IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE,
       defer_option IN VARCHAR2 DEFAULT NULL;

#### Parameters

Table 4-61 RemoveWorkspaceTree Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |
| `defer_option` | Specifies whether rows and locks associated with the workspace for version-enabled tables are removed or if the removal is to be deferred until later. This allows you to accept or override the value of the `REMOVEWORKSPACE_DEFERRED` system parameter.<br>The value can be null, `OFF`, `FAST`, or `REMOVE_LOCKS`. For an explanation of the `REMOVEWORKSPACE_DEFERRED` system parameter and its possible values, see [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).                                                                                       |

#### Usage Notes

The RemoveWorkspaceTree operation should be used with extreme caution, because it removes support structures and rolls back changes in a workspace and all its descendants down to the leaf workspace or workspaces. For example, in the hierarchy shown in [Workspace Hierarchy](introduction-to-workspace-manager.md), a RemoveWorkspaceTree operation specifying `Workspace1` removes `Workspace1`, `Workspace2`, and `Workspace3`. (For an explanation of database workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).)

There must be no other users in `workspace` or any of its descendant workspaces.

An exception is raised if the user does not have the `REMOVE_WORKSPACE` privilege for `workspace` or any of its descendant workspaces, if the user does not have sufficient privileges on all tables that need to be modified (including, for example, tables modified by triggers), or if `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example removes the `NEWWORKSPACE` workspace and all its descendant workspaces.

    EXECUTE DBMS_WM.RemoveWorkspaceTree('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.70 RenameSavepoint

Renames a savepoint in a specified workspace.

#### Syntax

    DBMS_WM.RenameSavepoint(
       workspace_name     IN VARCHAR2,
       savepoint_name     IN VARCHAR2;
       new_savepoint_name IN VARCHAR2;

#### Parameters

Table 4-62 RenameSavepoint Procedure Parameters

| Parameter            | Description                                                                                             |
|:---------------------|:--------------------------------------------------------------------------------------------------------|
| `workspace_name`     | Name of the existing workspace in which the savepoint to be renamed exists. The name is case-sensitive. |
| `savepoint_name`     | Name of the existing explicit savepoint to be renamed. (Must not be an implicit savepoint.)             |
| `new_savepoint_name` | New name to be given to the savepoint. Must not be the name of an existing savepoint.                   |

#### Usage Notes

An exception is raised if the user does not own the workspace or savepoint or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example renames savepoint `SP1` in the `LIVE` workspace to `2009 milestone`.

    EXECUTE DBMS_WM.RenameSavepoint('LIVE', 'SP11', '2009 milestone');

**Parent topic:** DBMS_WM Package: Reference

### 4.71 RenameWorkspace

Renames a workspace.

#### Syntax

    DBMS_WM.RenameWorkspace(
       workspace_name     IN VARCHAR2,
       new_workspace_name IN VARCHAR2;

#### Parameters

Table 4-63 RenameWorkspace Procedure Parameters

| Parameter            | Description                                                                                                                                                                                                                                                   |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace_name`     | Name of the existing workspace to be renamed. The name is case-sensitive.                                                                                                                                                                                     |
| `new_workspace_name` | New name to be given to the workspace. The new name must not be `LIVE` or the name of an existing workspace, and it must not contain any of the following characters: `"` (double quotes), `'` (single quote),``  ` `` (grave accent), or `|` (vertical bar). |

#### Usage Notes

This procedure automatically updates the metadata for existing version-enabled tables to refer to the new workspace name. The time required for the procedure to complete will depend on the number of version-enabled tables.

An exception is raised if the user does not own the workspace or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example renames workspace `WS1` to `Construction Project`.

    EXECUTE DBMS_WM.RenameWorkspace('WS1', 'Construction Project');

**Parent topic:** DBMS_WM Package: Reference

### 4.72 ResolveConflicts

Resolves conflicts between workspaces.

#### Syntax

    DBMS_WM.ResolveConflicts(
       workspace       IN VARCHAR2,
       table_name      IN VARCHAR2,
       where_clause    IN VARCHAR2,
       keep            IN VARCHAR2,
       resolve_base_ne IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-64 ResolveConflicts Procedure Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`        | Name of the workspace to check for conflicts with other workspaces. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `table_name`       | Name of the table to check for conflicts. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `where_clause`     | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be refreshed from the parent workspace. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `keep`             | Workspace in favor of which to resolve conflicts: `PARENT`, `CHILD`, or `BASE`.<br>`PARENT` causes the parent workspace rows to be copied to the child workspace.<br>`CHILD` does not cause the child workspace rows to be copied immediately to the parent workspace. However, the conflict is considered resolved, and the child workspace rows are copied to the parent workspace when the child workspace is merged.<br>`BASE` causes the base rows to be copied to the child workspace but not to the parent workspace. However, the conflict is considered resolved; and when the child workspace is merged, the base rows are copied to the parent workspace. Note that `BASE` is ignored for insert-insert conflicts where a base row does not exist; in this case, the `keep` parameter value must be `PARENT` or `CHILD`. |
| `resolve_bnase_ne` | A Boolean value (`TRUE` or `FALSE`). Applies only if the value of `keep` is `BASE`.<br>`TRUE` allows the resolution of conflicts in favor of the base row, even when the base row was nonexistent, as is the case in an insert-insert conflict.<br>`FALSE` (the default) disallows the resolution of conflicts in favor of nonexistent base rows. If a nonexistent base row is encountered while other conflicts are being resolved, the conflict is effectively ignored and will not be considered resolved.                                                                                                                                                                                                                                                                                                                       |

#### Usage Notes

This procedure checks the condition identified by the `table_name` and `where_clause` parameters, and it finds any conflicts between row values in `workspace` and its parent workspace. This procedure resolves conflicts by using the row values in the parent or child workspace, as specified in the `keep` parameter; however, the conflict resolution is not actually merged until you commit the transaction (standard database commit operation) and call the CommitResolve procedure to end the conflict resolution session. (For more information about conflict resolution, including an overall view of the process, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).)

For example, assume that for Department 20 (`DEPARTMENT_ID = 20`), the `MANAGER_NAME` in the `LIVE` and `Workspace1` workspaces is `Tom`. Then, the following operations occur:

1.  The `manager_name` for Department 20 is changed in the `LIVE` database workspace from `Tom` to `Mary`.

2.  The change is committed (a standard database commit operation).

3.  The `manager_name` for Department 20 is changed in `Workspace1` from `Tom` to `Franco`.

4.  The MergeWorkspace procedure is called to merge `Workspace1` changes to the `LIVE` workspace.

    At this point, however, a conflict exists with respect to `MANAGER_NAME` for Department 20 in `Workspace1` (`Franco`, which conflicts with `Mary` in the `LIVE` workspace), and therefore the call to MergeWorkspace does not succeed.

5.  The ResolveConflicts procedure is called with the following parameters: (`'Workspace1'`, `'department'`, `'department_id = 20'`, `'child'`).

    After the MergeWorkspace operation in step 7, the `MANAGER_NAME` value will be `Franco` in both the `Workspace1` and `LIVE` workspaces.

6.  The change is committed (a standard database commit operation).

7.  The MergeWorkspace procedure is called to merge `Workspace1` changes to the `LIVE` workspace.

The following considerations apply during a conflict resolution session:

- A ResolveConflicts operation prevents other workspace operations (such as a merge, refresh, or removal) on the target workspace or table until after the CommitResolve or RollbackResolve procedure is executed.

- Multiple sessions can perform ResolveConflicts operations and perform insert, update, and delete operations on the same table. However, during such operations, the target rows are locked. If more than one session attempts to perform an insert, update, or delete operation on the same row or to resolve a conflict affecting the same row, the first session is allowed to continue; and after that session executes the CommitResolve or RollbackResolve procedure, another session is allowed to proceed.

For more information about conflict resolution, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).

#### Examples

The following example resolves conflicts involving rows in the `DEPARTMENT` table in `Workspace1` where `DEPARTMENT_ID` is 20, and uses the values in the child workspace to resolve all such conflicts. It then merges the results of the conflict resolution by first committing the transaction (standard commit) and then calling the MergeWorkspace procedure.

    EXECUTE DBMS_WM.BeginResolve ('Workspace1');
    EXECUTE  DBMS_WM.ResolveConflicts ('Workspace1', 'department', 'department_id = 20', 'child');
    COMMIT;
    EXECUTE DBMS_WM.CommitResolve ('Workspace1');

**Parent topic:** DBMS_WM Package: Reference

### 4.73 RevokeGraphPriv

Revokes (removes) privileges on multiparent graph workspaces from users and roles for a specified leaf workspace.

#### Syntax

    DBMS_WM.RevokeGraphPriv(
       priv_types      IN VARCHAR2,
       leaf_workspace  IN VARCHAR2,
       grantee         IN VARCHAR2.
       node_types      IN VARCHAR2 DEFAULT '(''R'',''I'',''L'')',
       auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-65 RevokeGraphPriv Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`     | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, `CREATE_WORKSPACE`, `REMOVE_WORKSPACE`, and `ROLLBACK_WORKSPACE`.                                                                                                                                                                                                                           |
| `leaf_workspace` | Name of the leaf workspace in the directed acyclic graph. (Leaf workspaces, directed acyclic graphs, and other concepts related to multiparent workspaces are explained in [Multiparent Workspaces](introduction-to-workspace-manager.md).) The name is case-sensitive.                                                                                                                                                                                                                                                                                                                          |
| `grantee`        | Name of the user (can be the `PUBLIC` user group) or role from which to revoke `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `node_types`     | List of letters (in parentheses and comma-delimited) representing the types of nodes on which to revoke the privileges: `R` for the root of the graph, `I` for the specified intermediate node, `L` for the leaf of the graph. The default is all types of nodes.                                                                                                                                                                                                                                                                                                                                |
| `auto_commit`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with RevokeWorkspacePriv , which grants workspace-level Workspace Manager privileges on workspaces other than multiparent graph workspaces.

To grant workspace-level privileges on multiparent graph workspaces, use the GrantGraphPriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You were not the grantor of `priv_types` to `grantee`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example disallows user `Smith` from accessing all types of nodes in the directed acyclic graph in which the `NEWWORKSPACE` workspace is the leaf workspace and from merging changes in these workspaces.

    EXECUTE DBMS_WM.RevokeWorkspacePriv ('ACCESS_WORKSPACE, MERGE_WORKSPACE', 'NEWWORKSPACE', 'Smith');

**Parent topic:** DBMS_WM Package: Reference

### 4.74 RevokeSystemPriv

Revokes (removes) system-level privileges from users and roles.

#### Syntax

    DBMS_WM.RevokeSystemPriv(
       priv_types   IN VARCHAR2,
       grantee      IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-66 RevokeSystemPriv Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`  | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_ANY_WORKSPACE`, `MERGE_ANY_WORKSPACE`, `CREATE_ANY_WORKSPACE`, `REMOVE_ANY_WORKSPACE`, and `ROLLBACK_ANY_WORKSPACE`.                                                                                                                                                                                                       |
| `grantee`     | Name of the user (can be the `PUBLIC` user group) or role from which to revoke `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with RevokeWorkspacePriv , which revokes workspace-level Workspace Manager privileges with keywords in the form xxx\_WORKSPACE (`ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, and so on).

To grant system-level privileges, use the GrantSystemPriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You were not the grantor of `priv_types` to `grantee`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example disallows user `Smith` from accessing workspaces and merging changes in workspaces.

    EXECUTE DBMS_WM.RevokeSystemPriv ('ACCESS_ANY_WORKSPACE, MERGE_ANY_WORKSPACE', 'Smith');

**Parent topic:** DBMS_WM Package: Reference

### 4.75 RevokeWorkspacePriv

Revokes (removes) workspace-level privileges from users and roles for a specified workspace.

#### Syntax

    DBMS_WM.RevokeWorkspacePriv(
       priv_types   IN VARCHAR2,
       workspace    IN VARCHAR2,
       grantee      IN VARCHAR2.
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-67 RevokeWorkspacePriv Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `priv_types`  | A string of one or more keywords representing privileges. ([Privilege Management with Workspace Manager](introduction-to-workspace-manager.md) discusses Workspace Manager privileges.) Use commas to separate privilege keywords. The available keywords are `ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, `CREATE_WORKSPACE`, `REMOVE_WORKSPACE`, and `ROLLBACK_WORKSPACE`.                                                                                                                                                                                                                           |
| `workspace`   | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `grantee`     | Name of the user (can be the `PUBLIC` user group) or role from which to revoke `priv_types`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Contrast this procedure with RevokeSystemPriv , which revokes system-level Workspace Manager privileges with keywords in the form xxx\_ANY_WORKSPACE (`ACCESS_ANY_WORKSPACE`, `MERGE_ANY_WORKSPACE`, and so on). Also contrast this procedure with RevokeGraphPriv , which grants workspace-level Workspace Manager privileges on multiparent graph workspaces

To grant workspace-level privileges, use the GrantWorkspacePriv procedure.

An exception is raised if one or more of the following apply:

- `grantee` is not a valid user or role in the database.

- You were not the grantor of `priv_types` to `grantee`.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example disallows user `Smith` from accessing the `NEWWORKSPACE` workspace and merging changes in that workspace.

    EXECUTE DBMS_WM.RevokeWorkspacePriv ('ACCESS_WORKSPACE, MERGE_WORKSPACE', 'NEWWORKSPACE', 'Smith');

**Parent topic:** DBMS_WM Package: Reference

### 4.76 RollbackBulkLoading

Rolls back changes made to a version-enabled table during a bulk load operation.

#### Syntax

    DBMS_WM.RollbackBulkLoading(
       table_name         IN VARCHAR2,
       ignore_last_error  IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-68 RollbackBulkLoading Procedure Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`        | Name of the version-enabled table into which data will be bulk loaded. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `ignore_last_error` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` ignores the last error, if any, that occurred during the previous call to the RollbackBulkLoading procedure. Information about the last error is stored in the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views, which are described in [Workspace Manager Static Data Dictionary Views](workspace-manager-views.md) . See the Usage Notes for more information.<br>`FALSE` `(`the default) does not ignore the last error, if any, that occurred during the previous call to the RollbackBulkLoading procedure. |

#### Usage Notes

For information about the requirements for bulk loading data into version-enabled tables, see [Bulk Loading into Version-Enabled Tables](introduction-to-workspace-manager.md).

This procedure re-creates all the views that were dropped by the BeginBulkLoading procedure.

If a call to the RollbackBulkLoading procedure fails, you should try to fix the cause of the error. Examine the [USER_WM_VT_ERRORS](workspace-manager-views.md) and [ALL_WM_VT_ERRORS](workspace-manager-views.md) static data dictionary views to see the SQL statement and error message. Fix the cause of the error, and then call the RollbackBulkLoading procedure again with the default `ignore_last_error` parameter value of `FALSE`. However, if the call still fails and you cannot fix the cause of the error, and if you are sure that it is safe and appropriate to ignore this error, then you have the option to ignore the error by calling the RollbackBulkLoading procedure with the `ignore_last_error` parameter value of `TRUE`. Note that you are responsible for ensuring that it is safe and appropriate to ignore the error.

An exception is raised if one or more of the following apply:

- `table_name` does not exist.

- `table_name` is not version-enabled.

- The BeginBulkLoading procedure has not been called on the table.

- The user does not own the table or does not have the `WM_ADMIN` system privilege.

#### Examples

The following example rolls back changes made to `EMP` table during a bulk load operation.

    EXECUTE DBMS_WM.RollbackBulkLoading ('EMP');

**Parent topic:** DBMS_WM Package: Reference

### 4.77 RollbackDDL

Rolls back (cancels) DDL (data definition language) changes made during a DDL session for a specified table, and ends the DDL session.

#### Syntax

    DBMS_WM.RollbackDDL(
       table_name  IN VARCHAR2);

#### Parameters

Table 4-69 RollbackDDL Procedure Parameters

| Parameter    | Description                                                        |
|:-------------|:-------------------------------------------------------------------|
| `table_name` | Name of the version-enabled table. The name is not case-sensitive. |

#### Usage Notes

This procedure rolls back (cancels) changes that were made to a version-enabled table and to any indexes and triggers based on the version-enabled table during a DDL session. It also deletes the \<table-name\>\_LTS skeleton table that was created by the BeginDDL procedure.

For detailed information about performing DDL operations related to version-enabled tables, see [DDL Operations Related to Version-Enabled Tables](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- `table_name` does not exist or is not version-enabled.

- An open DDL session does not exist for `table_name`. (That is, the BeginDDL procedure has not been called specifying this table, or the CommitDDL or RollbackDDL procedure was already called specifying this table.)

#### Examples

The following example begins a DDL session, adds a column named `COMMENTS` to the `COLA_MARKETING_BUDGET` table by using the skeleton table named `COLA_MARKETING_BUDGET_LTS`, and ends the DDL session by canceling the change.

    EXECUTE DBMS_WM.BeginDDL('COLA_MARKETING_BUDGET');
    ALTER TABLE cola_marketing_budget_lts ADD (comments VARCHAR2(100));
    EXECUTE DBMS_WM.RollbackDDL('COLA_MARKETING_BUDGET');

**Parent topic:** DBMS_WM Package: Reference

### 4.78 RollbackResolve

Quits a conflict resolution session and discards all changes in the workspace since the BeginResolve procedure was executed.

#### Syntax

    DBMS_WM.RollbackResolve(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-70 RollbackResolve Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

This procedure quits the current conflict resolution session (started by the BeginResolve procedure), and discards all changes in the workspace since the start of the conflict resolution session. Contrast this procedure with CommitResolve, which saves all changes.

While the conflict resolution session is being rolled back, the workspace is frozen in `1WRITER` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

For more information about conflict resolution, see [Resolving Conflicts Before a Merge or Refresh Operation](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- There are one or more open database transactions in `workspace`.

- The procedure was called by a user that does not have the `WM_ADMIN` system privilege or that did not execute the BeginResolve procedure on `workspace`.

#### Examples

The following example quits the conflict resolution session in `Workspace1` and discards all changes.

    EXECUTE  DBMS_WM.RollbackResolve ('Workspace1');

**Parent topic:** DBMS_WM Package: Reference

### 4.79 RollbackTable

Discards all changes made in the workspace to a specified table (all rows or as specified in the `WHERE` clause).

#### Syntax

    DBMS_WM.RollbackTable(
       workspace     IN VARCHAR2,
       table_id      IN VARCHAR2,
       sp_name       IN VARCHAR2 DEFAULT '',
       where_clause  IN VARCHAR2 DEFAULT '',
       remove_locks  IN BOOLEAN DEFAULT TRUE,
       auto_commit   IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-71 RollbackTable Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `table_id`     | Name of the table containing rows to be discarded. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `sp_name`      | Name of the savepoint to which to roll back. The name is case-sensitive. The default is to discard all changes (that is, ignore any savepoints).                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `where_clause` | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be discarded. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If `the where_clause parameter` is not specified, all rows that meet the criteria of the other parameters are discarded.                                                                                                                                      |
| `remove_locks` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) releases those locks on rows in the parent workspace that satisfy the condition in `the where_clause parameter` and that were not versioned in the child workspace. This option has no effect if a savepoint is specified (`sp_name` parameter).<br>`FALSE` does not release any locks in the parent workspace.                                                                                                                                                                                                                     |
| `auto_commit`  | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

You cannot roll back to a savepoint if any implicit savepoints were created since the specified savepoint, unless you first merge or remove the descendant workspaces that caused the implicit savepoints to be created. For example, referring to [Figure 1-2](introduction-to-workspace-manager.md) in [Using Savepoints](introduction-to-workspace-manager.md), the user in Workspace1 cannot roll back to savepoint SP1 until Workspace3 (which caused implicit savepoint SPc to be created) is merged or removed.

An exception is raised if one or more of the following apply:

- `workspace` does not exist.

- You do not have the privilege to roll back `workspace` or any affected table.

- A database transaction affecting `table_id` is open in any workspace.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

#### Examples

The following example rolls back all changes made to the `EMP` table (in the `USER3` schema) in the `NEWWORKSPACE` workspace since that workspace was created.

    EXECUTE DBMS_WM.RollbackTable ('NEWWORKSPACE', 'user3.emp');

**Parent topic:** DBMS_WM Package: Reference

### 4.80 RollbackToSP

Discards all data changes made in the workspace to version-enabled tables since the specified savepoint.

#### Syntax

    DBMS_WM.RollbackToSP(
       workspace       IN VARCHAR2,
       savepoint_name  IN VARCHAR2,
       auto_commit     IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-72 RollbackToSP Procedure Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`      | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `savepoint_name` | Name of the savepoint to which to roll back changes. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `auto_commit`    | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

While this procedure is executing, the workspace is frozen in `NO_ACCESS` mode.

Contrast this procedure with RollbackWorkspace, which rolls back all changes made since the creation of the workspace.

You cannot roll back to a savepoint if any implicit savepoints were created since the specified savepoint, unless you first merge or remove the descendant workspaces that caused the implicit savepoints to be created. For example, referring to [Figure 1-2](introduction-to-workspace-manager.md) in [Using Savepoints](introduction-to-workspace-manager.md), the user in `Workspace1` cannot roll back to savepoint `SP1` until `Workspace3` (which caused implicit savepoint `SPc` to be created) is merged or removed.

An exception is raised if one or more of the following apply:

- `workspace` does not exist.

- `savepoint_name` does not exist.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- One or more implicit savepoints were created in `workspace` after `savepoint_name`, and the descendant workspaces that caused the implicit savepoints to be created still exist.

- You do not have the privilege to roll back `workspace` or any affected table.

- Any sessions are in `workspace`.

#### Examples

The following example rolls back any changes made in the `NEWWORKSPACE` workspace to all tables since the creation of `Savepoint1`.

    EXECUTE DBMS_WM.RollbackToSP ('NEWWORKSPACE', 'Savepoint1');

**Parent topic:** DBMS_WM Package: Reference

### 4.81 RollbackWorkspace

Discards all data changes made in the workspace to version-enabled tables.

#### Syntax

    DBMS_WM.RollbackWorkspace(
       workspace    IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-73 RollbackWorkspace Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`   | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

Only leaf workspaces can be rolled back. That is, a workspace cannot be rolled back if it has any descendant workspaces. (For an explanation of workspace hierarchy, see [Workspace Hierarchy](introduction-to-workspace-manager.md).)

Contrast this procedure with RollbackToSP, which rolls back changes to a specified savepoint.

Like the RemoveWorkspace procedure, RollbackWorkspace deletes the data in the workspace; however, unlike the RemoveWorkspace procedure, RollbackWorkspace does not delete the Workspace Manager workspace structure.

While this procedure is executing, the specified workspace is frozen in `NO_ACCESS` mode, as explained in [Freezing and Unfreezing Workspaces](introduction-to-workspace-manager.md).

An exception is raised if one or more of the following apply:

- `workspace` has any descendant workspaces.

- `workspace` does not exist.

- `auto_commit` is `TRUE` and an open transaction exists in a parent or child workspace of any table that needs to be modified.

- You do not have the privilege to roll back `workspace` or any affected table.

- Any sessions are in `workspace`.

#### Examples

The following example rolls back any changes made in the `NEWWORKSPACE` workspace since that workspace was created.

    EXECUTE DBMS_WM.RollbackWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.82 SetCaptureEvent

Enables or disables the capture of all Workspace Manager events or events of a specific type.

#### Syntax

    DBMS_WM.SetCaptureEvent(
       event_name  IN VARCHAR2,
       capture     IN VARCHAR2 DEFAULT 'ON');

#### Parameters

Table 4-74 SetCaptureEvent Procedure Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `event_name` | One of the following values: `ALL_EVENTS`, `TABLE_MERGE_W_REMOVE_DATA`, `TABLE_MERGE_WO_REMOVE_DATA`, `TABLE_REFRESH`, `TABLE_ROLLBACK`, `WORKSPACE_COMPRESS`, `WORKSPACE_CREATE`, `WORKSPACE_MERGE_W_REMOVE`, `WORKSPACE_MERGE_WO_REMOVE`, `WORKSPACE_REFRESH`, `WORKSPACE_REMOVE`, `WORKSPACE_ROLLBACK`, `WORKSPACE_VERSION`.<br>`ALL_EVENTS` includes all Workspace Manager events. The other values reflect specific event types, which are listed and explained in [List of Workspace Manager Events](workspace-manager-events.md). |
| `capture`    | `ON` (the default) enables the capture of `event_name` events.<br>`OFF` disables the capture of `event_name` events.                                                                                                                                                                                                                                                                                                                                                                                                                     |

#### Usage Notes

For information about Workspace Manager events, see [Workspace Manager Events](workspace-manager-events.md).

This procedure requires that the Workspace Manager system parameter `ALLOW_CAPTURE_EVENTS` be set to `ON`. To check the value of a Workspace Manager system parameter, use the GetSystemParameter procedure; to set a Workspace Manager system parameter, use the SetSystemParameter procedure.

You can use this procedure to control which types of events are captured. For example, you can enable the capture of all events, and then disable the capture of a few types of events; or you can disable the capture of all events, and then enable the capture of a few types of events.

To see which types of events are currently being captured, examine the [WM_EVENTS_INFO](workspace-manager-views.md) metadata view, which is described in [WM_EVENTS_INFO](workspace-manager-views.md).

If this procedure completes successfully, it commits the caller's open database transaction.

An exception is raised if one or more of the following apply:

- You do not have the `WM_ADMIN` system privilege.

- The value of the `ALLOW_CAPTURE_EVENTS` system parameter is `OFF` and you are trying to set `event_name` to `ON` (the default value for that parameter).

- `event_name` is not valid.

#### Examples

The following example captures all Workspace Manager events except workspace compression events, by first specifying that all events are to be captured, and then excluding workspace compression events.

    -- Allow Workspace Manager events to be captured. (Required for SetCaptureEvent)
    EXECUTE DBMS_WM.SetSystemParameter ('ALLOW_CAPTURE_EVENTS', 'ON');
    -- Start capturing all Workspace Manager events.
    EXECUTE DBMS_WM.SetCaptureEvent ('ALL_EVENTS','ON');
    -- Exclude workspace compression events.
    EXECUTE DBMS_WM.SetCaptureEvent ('WORKSPACE_COMPRESS','OFF');

**Parent topic:** DBMS_WM Package: Reference

### 4.83 SetCompressWorkspace

Creates rows in the [WM_COMPRESSIBLE_TABLES](workspace-manager-views.md) metadata view with information about version-enabled tables that need to be compressed if workspace compression operations are performed.

#### Syntax

    DBMS_WM.SetCompressWorkspace(
       workspace  IN VARCHAR2,
       firstSP    IN VARCHAR2 DEFAULT NULL,
       secondSP   IN VARCHAR2 DEFAULT NULL);

#### Parameters

Table 4-75 SetCompressWorkspace Procedure Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `firstSP`   | Savepoint on the first version of the compression range. Savepoint names are case-sensitive.<br>If only `workspace` and `firstSP` are specified, all rows in version-enabled tables affected between workspace creation and `firstSP` are checked to see if they need to be compressed in a workspace compression operation is performed.<br>If `workspace`, `firstSP`, and `secondSP` are specified, all rows in version-enabled tables affected between `firstSP` and `secondSP` are checked.<br>If only `workspace` is specified (no savepoints), all rows in version-enabled tables are checked. |
| `secondSP`  | Savepoint on the first version of the compression range. All rows in version-enabled tables from `firstSP` to `secondSP` are checked to see if they need to be compressed in a workspace compression operation is performed. Savepoint names are case-sensitive.                                                                                                                                                                                                                                                                                                                                     |

#### Usage Notes

You can (but do not need to) use this procedure before calling the CompressWorkspace or CompressWorkspaceTree procedure.

This procedure creates rows in the [WM_COMPRESSIBLE_TABLES](workspace-manager-views.md) metadata view (described in [WM_COMPRESSIBLE_TABLES](workspace-manager-views.md)) only for version-enabled tables that would need to be compressed during a workspace compression operation.

#### Examples

The following example creates rows in the [WM_COMPRESSIBLE_TABLES](workspace-manager-views.md) metadata view for any version-enabled tables that would need to be compressed during an operation that compressed the `B_focus_1` workspace.

    EXECUTE DBMS_WM.SetCompressWorkspace ('B_focus_1');

**Parent topic:** DBMS_WM Package: Reference

### 4.84 SetConflictWorkspace

Determines whether or not conflicts exist between a workspace and its parent.

#### Syntax

    DBMS_WM.SetConflictWorkspace(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-76 SetConflictWorkspace Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

This procedure checks for any conflicts between `workspace` and its parent workspace, and it modifies the content of the \<table_name\>\_CONF views (explained in [xxx_CONF Views](workspace-manager-views.md)) as needed.

A `SELECT` operation from the \<table_name\>\_CONF views for all tables modified in a workspace displays all rows in the workspace that are in conflict with the parent workspace. (To obtain a list of tables that have conflicts for the current conflict workspace setting, use the SQL statement `SELECT * FROM ALL_WM_VERSIONED_TABLES WHERE conflict = 'YES';`. The SQL statement `SELECT * FROM <table_name>_CONF` displays conflicts for \<table_name\> between the current workspace and its parent workspace.)

Any conflicts must be resolved before a workspace can be merged or refreshed. To resolve a conflict, you must use the ResolveConflicts procedure, and then merge the result of the resolution by using the MergeWorkspace procedure.

#### Examples

The following example checks for any conflicts between `B_focus_2` and its parent workspace, and modifies the contents of the \<table_name\>\_CONF views as needed.

    EXECUTE DBMS_WM.SetConflictWorkspace ('B_focus_2');

**Parent topic:** DBMS_WM Package: Reference

### 4.85 SetDiffVersions

Finds differences in values in version-enabled tables for two savepoints and their common ancestor (base). It modifies the contents of the differences views that describe these differences.

#### Syntax

    DBMS_WM.SetDiffVersions(
       workspace1   IN VARCHAR2,
       workspace2   IN VARCHAR2,
       onlyModified IN BOOLEAN DEFAULT FALSE);

or

    DBMS_WM.SetDiffVersions(
       workspace1   IN VARCHAR2,
       savepoint1   IN VARCHAR2,
       workspace2   IN VARCHAR2,
       savepoint2   IN VARCHAR2,
       onlyModified IN BOOLEAN DEFAULT FALSE);

#### Parameters

Table 4-77 SetDiffVersions Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace1`   | Name of the first workspace to be checked for differences in version-enabled tables. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                              |
| `savepoint1`   | Name of the savepoint in `workspace1` for which values are to be checked. The name is case-sensitive.<br>If `savepoint1` and `savepoint2` are not specified, the rows in version-enabled tables for the `LATEST` savepoint in each workspace are checked. (The `LATEST` savepoint is explained in [Using Savepoints](introduction-to-workspace-manager.md).)                                                                                                                                                                  |
| `workspace2`   | Name of the second workspace to be checked for differences in version-enabled tables. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                             |
| `savepoint2`   | Name of the savepoint in `workspace2` for which values are to be checked. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `onlyModified` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` removes from the \_DIFF any rows that have a `NC` (no change) or `NE` (nonexistent) value for the WM_CODE column. This improves the performance of the view when these rows are not needed. As such, each primary key can have from one through three rows, instead of the usual three.<br>`FALSE` (the default) causes queries on the \_DIFF view to always return three rows for each primary key value: one for the base row, and one for each of the specified savepoints. |

#### Usage Notes

This procedure modifies the contents of the differences views (xxx\_DIFF), which are described in [xxx_DIFF Views](workspace-manager-views.md). Each call to the procedure populates one or more sets of three rows, each set consisting of:

- Values for the common ancestor

- Values for `workspace1` (`savepoint1` or `LATEST` savepoint values)

- Values for `workspace2` (`savepoint2` or `LATEST` savepoint values)

You can then select rows from the appropriate xxx\_DIFF view or views to check comparable table values in the two savepoints and their common ancestor. The common ancestor (or base) is identified as `DiffBase` in xxx\_DIFF view rows.

#### Examples

The following example checks the differences in version-enabled tables for the `B_focus_1` and `B_focus_2` workspaces. (The output has been reformatted for readability.)

    -- Add rows to difference view: COLA_MARKETING_BUDGET_DIFF
    EXECUTE DBMS_WM.SetDiffVersions ('B_focus_1', 'B_focus_2');

    -- View the rows that were just added.
    SELECT * from COLA_MARKETING_BUDGET_DIFF;

    PRODUCT_ID  PRODUCT_NAME  MANAGER  BUDGET  WM_DIFFVER          WMCODE
    ----------  ------------  -------  ------  -----------         --------
           1        cola_a    Alvarez   2      DiffBase            NC
           1        cola_a    Alvarez   1.5    B_focus_1, LATEST   U
           1        cola_a    Alvarez   2      B_focus_2, LATEST   NC
           2        cola_b    Burton    2      DiffBase            NC
           2        cola_b    Beasley   3      B_focus_1, LATEST   U
           2        cola_b    Burton    2.5    B_focus_2, LATEST   U
           3        cola_c    Chen      1.5    DiffBase            NC
           3        cola_c    Chen      1      B_focus_1, LATEST   U
           3        cola_c    Chen      1.5    B_focus_2, LATEST   NC
           4        cola_d    Davis     3.5    DiffBase            NC
           4        cola_d    Davis     3      B_focus_1, LATEST   U
           4        cola_d    Davis     2.5    B_focus_2, LATEST   U

    12 rows selected.

[xxx_DIFF Views](workspace-manager-views.md) explains how to interpret and use the information in the differences (xxx\_DIFF) views.

**Parent topic:** DBMS_WM Package: Reference

### 4.86 SetLockingOFF

Disables Workspace Manager locking for the current session.

#### Syntax

    DBMS_WM.SetLockingOFF();

#### Parameters

None.

#### Usage Notes

This procedure turns off Workspace Manager locking that was set on by the SetLockingON procedure. Existing locks applied by this session remain locked. All new changes by this session are not locked.

#### Examples

The following example sets locking off for the session.

    EXECUTE DBMS_WM.SetLockingOFF;

**Parent topic:** DBMS_WM Package: Reference

### 4.87 SetLockingON

Enables Workspace Manager locking for the current session.

#### Syntax

    DBMS_WM.SetLockingON(
       lockmode  IN VARCHAR2);

#### Parameters

Table 4-78 SetLockingON Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `lockmode` | Locking mode. Must be `E`, `WE`, `VE`, `S`, or `C`.<br>`E` (exclusive) mode locks the rows in the previous version and the corresponding rows in the current version; no other users in the workspace for either version can change any values.<br>`WE` (workspace-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values in the current workspace; however, other users in other workspaces can change the values.<br>`VE` (version-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values; no other users (in any workspace) can change the values.<br>`S` (shared) mode locks the rows in the previous version and the corresponding rows in the current version; however, other users in the workspace for the current version (but no users in the workspace for the previous version) can change values in these rows.<br>`C` (carry-forward) mode locks rows in the current workspace with the same locking mode as the corresponding rows in the previous version. (If a row is not locked in the previous version, its corresponding row in the current version is not locked.) |

#### Usage Notes

This procedure affects Workspace Manager locking, which occurs in addition to any standard Oracle database locking. Workspace Manager locks can be used to prevent conflicts. When a user locks a row, the corresponding row in the parent workspace is also locked. Thus, when this workspace merges with the parent at merge time, it is guaranteed that this row will not have a conflict.

For information about Workspace Manager lock management, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).

Exclusive locking (`lockmode` value of `E`) prevents the use of what-if scenarios in which different values for one or more columns are tested. Thus, plan any testing of scenarios when exclusive locking is not in effect.

Locking is enabled at the user session level, and the locking mode stays in effect until any of the following occurs:

- The session goes to another workspace or connects to the database, in which case the locking mode is set to `C` (carry-forward) unless another locking mode has been specified using the SetWorkspaceLockModeON procedure.

- The session executes the SetLockingOFF procedure.

The locks remain in effect for the duration of the workspace, unless unlocked by the UnlockRows procedure. (Existing locks are not affected by the SetLockingOFF procedure.)

There are no specific privileges associated with locking. Any session that can go to a workspace can set locking on.

#### Examples

The following example sets exclusive locking on for the session.

    EXECUTE DBMS_WM.SetLockingON ('E');

All rows locked by this user remain locked until the workspace is merged or rolled back.

**Parent topic:** DBMS_WM Package: Reference

### 4.88 SetMultiWorkspaces

Makes the specified workspace or workspaces visible in the multiworkspace views for version-enabled tables.

#### Syntax

    DBMS_WM.SetMultiWorkspaces(
       workspaces  IN VARCHAR2);

#### Parameters

Table 4-79 SetMultiWorkspaces Procedure Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                     |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspaces` | The workspace or workspaces for which information is to be added to the multiworkspace views (described in [xxx_MW Views](workspace-manager-views.md)). The workspace names are case-sensitive.<br>To specify more than one workspace (but no more than eight), use a comma to separate workspace names. For example: `'workspace1,workspace2'` |

#### Usage Notes

This procedure adds rows to the multiworkspace views (xxx\_MW). See [xxx_MW Views](workspace-manager-views.md) for information about the contents and uses of these views.

To see the names of workspaces visible in the multiworkspace views, use the GetMultiWorkspaces function.

An exception is raised if one or more of the following apply:

- The user does not have the privilege to go to one or more of the workspaces named in `workspaces`.

- A workspace named in `workspaces` is not valid.

#### Examples

The following example adds information to the multiworkspace views for version-enabled tables in the `B_focus_1` workspace.

    EXECUTE DBMS_WM.SetMultiWorkspaces ('B_focus_1');

The following example shows the use of the SetMultiWorkspaces procedure to view information without leaving the current workspace, and the use of the GotoWorkspace procedure to view the same information.

    -- These two pairs of statements select the same information.
    EXECUTE DBMS_WM.SetMultiWorkspaces ('myworkspace');
    SELECT * from mytable_mw;

    EXECUTE DBMS_WM.GotoWorkspace ('myworkspace');
    SELECT * from mytable;

To select only the rows modified in `myworkspace`, change the first `SELECT` statement in the preceding example to the following:

    SELECT * from mytable_mw WHERE wm_modified_by = 'myworkspace';

The following example shows the latest rows in the combined ancestor versions of the workspaces named `myworkspace` and `yourworkspace`. If the same row is selected from more than workspace, that row is shown only once. Note that there may be more than one row for a primary key because different workspaces might be selecting different versions of the primary key.

    EXECUTE DBMS_WM.SetMultiWorkspaces ('myworkspace,yourworkspace');
    SELECT * from mytable_mw;

**Parent topic:** DBMS_WM Package: Reference

### 4.89 SetSystemParameter

Sets the value of a Workspace Manager system parameter.

#### Syntax

    DBMS_WM.SetSystemParameter(
       name   IN VARCHAR2,
       value  IN VARCHAR2);

#### Parameters

Table 4-80 SetSystemParameter Procedure Parameters

| Parameter | Description                                                                                                                                                                                                                    |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | Name of the Workspace Manager system parameter for which to set the value. The name must be one of the parameter names listed in the table in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md). |
| `value`   | Value for the specified Workspace Manager system parameter, as explained in the table in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).                                                      |

#### Usage Notes

For information about Workspace Manager system parameters, see [System Parameters for Workspace Manager](introduction-to-workspace-manager.md).

If this procedure completes successfully, it commits the caller's open database transaction.

An exception is raised if one or more of the following apply:

- The user does not have the `WM_ADMIN` system privilege.

- The system parameter name is not valid.

- The value is not valid for the system parameter.

- You tried to disallow capturing of events, and one or more types of events were being captured. You must first disable the capturing of all events (for example, by calling the SetCaptureEvent procedure and specifying `ALL_EVENTS` for `event_type `and `OFF` for `capture`).

- You tried to disallow multiparent workspaces, and one or more multiparent workspaces already existed. You must first ensure that all workspaces have no more than one parent workspace (for example, by calling the RemoveAsParentWorkspace procedure as needed).

- You tried to disallow nested table columns, and one or more tables with a nested table column were version-enabled. You must first disable versioning on all tables with nested table columns.

- You tried to change `CR_WORKSPACE_MODE` or `NONCR_WORKSPACE_MODE` to `PESSIMISTIC_LOCKING`, and data exists in a non-`LIVE` workspace for the corresponding type of workspace (continually refreshed or not continually refreshed).

#### Examples

The following example allows multiparent workspaces (described in [Multiparent Workspaces](introduction-to-workspace-manager.md)) to be created.

    EXECUTE DBMS_WM.SetSystemParameter ('ALLOW_MULTI_PARENT_WORKSPACES', 'ON');

**Parent topic:** DBMS_WM Package: Reference

### 4.90 SetTriggerEvents

Enables the execution of a trigger for a specified set of triggering events. The trigger will not be executed for events not specified

#### Syntax

    DBMS_WM.SetTriggerEvents(
       triggerName    IN VARCHAR2,
       triggerEvents  IN VARCHAR2);

#### Parameters

Table 4-81 SetTriggerEvents Procedure Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `triggerName`   | Name of the trigger for which to set one or more events.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `triggerEvents` | A comma-delimited list of trigger event names, where each trigger event name is one of the following string constants:<br>`DBMS_WM.DML`: Only for DML operations.<br>`DBMS_WM.TABLE_IMPORT`: Import table (using the Import procedure).<br>`DBMS_WM.TABLE_MERGE_W_REMOVE_DATA`: Merge table and remove data.<br>`DBMS_WM.TABLE_MERGE_WO_REMOVE_DATA`: Merge table without removing data.<br>`DBMS_WM.WORKSPACE_MERGE_W_REMOVE`: Merge workspace and remove the workspace<br>`DBMS_WM.WORKSPACE_MERGE_WO_REMOVE`: Merge workspace without removing the workspace. |

#### Usage Notes

For information about using triggers with Workspace Manager, see [Triggers on Version-Enabled Tables](introduction-to-workspace-manager.md).

By default, user-defined triggers are executed for both DML and workspace events, unless the default behavior is changed by using the Workspace Manager system parameter `FIRE_TRIGGERS_FOR_NONDML_EVENTS` (described in [System Parameters for Workspace Manager](introduction-to-workspace-manager.md)). You can use the `SetTriggerEvents` procedure to override the current `FIRE_TRIGGERS_FOR_NONDML_EVENTS` setting for specific triggers; however, if you later change the value of the `FIRE_TRIGGERS_FOR_NONDML_EVENTS` system parameter, this new value overrides any setting previously specified using the `SetTriggerEvents` procedure.

If this procedure completes successfully, it commits the caller's open database transaction.

An exception is raised if one or more of the following apply:

- The user is not the trigger owner or does not have the `WM_ADMIN` system privilege.

- `triggerName` does not exist.

- one or more `triggerEvents` values are not valid.

#### Examples

The following example enables the trigger `SCOTT.InsertTrigger` only for DML events.

    EXECUTE DBMS_WM.setTriggerEvents('SCOTT.InsertTrigger', DBMS_WM.DML);

The following example enables the trigger `SCOTT.InsertTrigger` for DML events and table merge operations.

    EXECUTE DBMS_WM.setTriggerEvents('SCOTT.InsertTrigger', dbms_wm.DML || ',' ||
                             dbms_wm.TABLE_MERGE_WO_REMOVE_DATA || ',' ||
                             dbms_wm.TABLE_MERGE_W_REMOVE_DATA);

**Parent topic:** DBMS_WM Package: Reference

### 4.91 SetValidTime

Sets the session valid time period. (Valid time support is described in [Workspace Manager Valid Time Support](valid-time-support.md).)

#### Syntax

    DBMS_WM.SetValidTime(
       validFrom IN TIMESTAMP WITH TIME ZONE DEFAULT DBMS_WM.CURRENT_TIME,
       validTill IN TIMESTAMP WITH TIME ZONE DEFAULT DBMS_WM.UNTIL_CHANGED);

#### Parameters

Table 4-82 SetValidTime Procedure Parameters

| Parameter   | Description                                                                                                                   |
|:------------|:------------------------------------------------------------------------------------------------------------------------------|
| `validFrom` | The start of the session valid time period. The default value is the current timestamp value.                                 |
| `validTill` | The end of the session valid time period. The default is that the time remains valid until the session valid time is changed. |

#### Usage Notes

For information about Workspace Manager valid time support, see [Workspace Manager Valid Time Support](valid-time-support.md). [WM_PERIOD Data Type](valid-time-support.md) explains how `validFrom` and `validTill` values are interpreted.

If this procedure is not invoked in the session or if it is invoked with no parameters, all rows that are valid at the current time are considered valid, and the valid time period is considered to be from the current time forward without limit.

#### Examples

The following example sets the session valid time to include all of the year 2003.

    EXECUTE DBMS_WM.SetValidTime(TO_DATE('01-01-2003', 'MM-DD-YYYY'), TO_DATE('01-01-2004', 'MM-DD-YYYY'));

**Parent topic:** DBMS_WM Package: Reference

### 4.92 SetValidTimeFilterOFF

Removes the valid time filter for the current session.

#### Syntax

    DBMS_WM.SetValidTimeFilterOFF();

#### Parameters

None.

#### Usage Notes

This procedure reverses the effect of theSetValidTimeFilterON procedure, and causes the previously defined valid time filter to be ignored for queries against tables with valid time support. Workspace Manager valid time support is explained in [Workspace Manager Valid Time Support](valid-time-support.md).

See also the Usage Notes for the SetValidTimeFilterON procedure.

#### Examples

The following example removes the valid time filter for the current session.

    EXECUTE DBMS_WM.SetValidTimeFilterOFF;

**Parent topic:** DBMS_WM Package: Reference

### 4.93 SetValidTimeFilterON

Sets a valid time filter for the current session (that is, a time to be applied to version-enabled tables.

#### Syntax

    DBMS_WM.SetValidTimeFilterON(
       filtertime  IN TIMESTAMP WITH TIME ZONE DEFAULT NULL);

#### Parameters

Table 4-83 SetValidTimeFilterON Procedure Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                   |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `filtertime` | Date to be used as a filter when querying version-enabled tables that have valid time support.<br>The default value is the current time; that is, each select operation on a version-enabled table with valid time support returns data that is valid as of the current time. |

#### Usage Notes

A valid time filter is a time that is applied to queries against version-enabled tables that have valid time support. When a valid time filter is set for the current session, only rows that are valid for the specified time are returned. Workspace Manager valid time support is explained in [Workspace Manager Valid Time Support](valid-time-support.md).

The purpose for setting a valid time filter is usually to work with only one row for a given primary key value. For example, assume that for the current valid time period, the session has two rows for employee Adams: the first row is valid from 01-Mar-2004 to 30-Apr-2005, and the second row is valid from 01-May-2005 until it is changed. If you set the valid time filter to 01-Jan-2005 and select all rows for Adams, only the first row (the one valid from 01-Mar-2004 to 30-Apr-2005) is returned. If you remove the valid time filter and select all rows for Adams, both rows are returned.

The `filtertime` value must be in the valid time range for the session. You can set the valid time range using the SetValidTime procedure.

#### Examples

The following example sets a valid time filter so that for queries against version-enabled tables with valid time support, only rows that are valid on January 1, 2005 are returned.

    EXECUTE DBMS_WM.SetValidTimeFilterOn(TO_DATE('2005-01-01', 'yyyy-mm-dd'));

**Parent topic:** DBMS_WM Package: Reference

### 4.94 SetWMValidUpdateModeOFF

Disables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support.

#### Syntax

    DBMS_WM.SetWMValidUpdateModeOFF();

#### Parameters

None.

#### Usage Notes

This procedure disables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support. Workspace Manager valid time support is explained in [Workspace Manager Valid Time Support](valid-time-support.md); sequenced and nonsequenced update operations and sequenced delete operations are explained in [Update Operations](valid-time-support.md).

When sequenced update and delete operations are enabled, when an update or delete operation is performed on a table with valid time support, the session's current valid time period is used so that only rows valid during that period are updated or deleted. However, calling the SetWMValidUpdateModeOFF procedure enables all row data to be updated or deleted, regardless of the valid time period, and causes WM_VALID column values in the table not to be updated. (This procedure does not affect insert or query operations on tables with valid time support.)

See also the Usage Notes for the SetWMValidUpdateModeON procedure.

#### Examples

The following example disables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support.

    EXECUTE DBMS_WM.SetWMValidUpdateModeOFF;

**Parent topic:** DBMS_WM Package: Reference

### 4.95 SetWMValidUpdateModeON

Enables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support.

#### Syntax

    DBMS_WM.SetWMValidUpdateModeON();

#### Parameters

None.

#### Usage Notes

This procedure enables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support. Sequenced update and delete operations are enabled when a table is version-enabled with valid time support or when valid time support is added to a version-enabled table; however, sequenced update and delete operations can be disabled using the SetWMValidUpdateModeOFF procedure.

Workspace Manager valid time support is explained in [Workspace Manager Valid Time Support](valid-time-support.md); sequenced and nonsequenced update operations and sequenced delete operations are explained in [Insert Operations](valid-time-support.md).

#### Examples

The following example enables sequenced and nonsequenced update operations and sequenced delete operations on tables that have valid time support. It reverses the effect of the SetWMValidUpdateModeOFF procedure.

    EXECUTE DBMS_WM.SetWMValidUpdateModeON;

**Parent topic:** DBMS_WM Package: Reference

### 4.96 SetWoOverwriteOFF

Disables the `VIEW_WO_OVERWRITE` history option that was enabled by the EnableVersioning or SetWoOverwriteON procedure, changing the option to `VIEW_W_OVERWRITE` (with overwrite).

#### Syntax

    DBMS_WM.SetWoOverwriteOFF();

#### Parameters

None.

#### Usage Notes

This procedure affects the recording of history information in the views named \<table_name\>\_HIST by changing the `VIEW_WO_OVERWRITE` option to `VIEW_W_OVERWRITE`. That is, from this point forward, the views show only the most recent modifications to the same version of the table. A history of modifications to the version is not maintained; that is, subsequent changes to a row in the same version overwrite earlier changes.

This procedure affects only tables that were version-enabled with the `hist` parameter set to `VIEW_WO_OVERWRITE` in the call to the EnableVersioning procedure.

The \<table_name\>\_HIST views are described in [xxx_HIST Views](workspace-manager-views.md). The `VIEW_WO_OVERWRITE` and `VIEW_W_OVERWRITE` options are further described in the description of the EnableVersioning procedure.

The history option affects the behavior of the GotoDate procedure. See the Usage Notes for that procedure.

The result of the SetWoOverwriteOFF procedure remains in effect only for the duration of the current session. To reverse the effect of this procedure, use the SetWoOverwriteON procedure.

#### Examples

The following example disables the `VIEW_WO_OVERWRITE` history option.

    EXECUTE DBMS_WM.SetWoOverwriteOFF;

**Parent topic:** DBMS_WM Package: Reference

### 4.97 SetWoOverwriteON

Enables the `VIEW_WO_OVERWRITE` history option that was disabled by the SetWoOverwriteOFF procedure.

#### Syntax

    DBMS_WM.SetWoOverwriteON();

#### Parameters

None.

#### Usage Notes

This procedure affects the recording of history information in the views named \<table_name\>\_HIST by changing the `VIEW_W_OVERWRITE` option to `VIEW_WO_OVERWRITE` (without overwrite). That is, from this point forward, the views show all modifications to the same version of the table. A history of modifications to the version is maintained; that is, subsequent changes to a row in the same version do not overwrite earlier changes.

This procedure affects only tables that were affected by a previous call to the SetWoOverwriteOFF procedure.

The \<table_name\>\_HIST views are described in [xxx_HIST Views](workspace-manager-views.md). The `VIEW_WO_OVERWRITE` and `VIEW_W_OVERWRITE` options are further described in the description of the EnableVersioning procedure.

The `VIEW_WO_OVERWRITE` history option can be overridden when a workspace is compressed by specifying the `compress_view_wo_overwrite` parameter as `TRUE` with the CompressWorkspace or CompressWorkspaceTree procedure.

The history option affects the behavior of the GotoDate procedure. See the Usage Notes for that procedure.

To reverse the effect of this procedure, use the SetWoOverwriteOFF procedure.

#### Examples

The following example enables the `VIEW_WO_OVERWRITE` history option.

    EXECUTE DBMS_WM.SetWoOverwriteON;

**Parent topic:** DBMS_WM Package: Reference

### 4.98 SetWorkspaceLockModeOFF

Disables Workspace Manager locking for the specified workspace.

#### Syntax

    DBMS_WM.SetWorkspaceLockModeOFF(
       workspace    IN VARCHAR2,
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-84 SetWorkspaceLockModeOFF Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`   | Name of the workspace for which to set the locking mode off. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md). |

#### Usage Notes

This procedure turns off Workspace Manager locking that was set on by the SetWorkspaceLockModeON procedure. Existing locks applied by this session remain locked. All new changes by this session or a subsequent session are not locked, unless the session turns locking on by executing the SetLockingON procedure.

An exception is raised if any of the following occurs:

- The user does not have the `WM_ADMIN` system privilege or is not the owner of `workspace`.

- `auto_commit` is `TRUE` and an open transaction exists.

#### Examples

The following example sets locking off for the workspace named `NEWWORKSPACE`.

    EXECUTE DBMS_WM.SetWorkspaceLockModeOFF('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.99 SetWorkspaceLockModeON

Enables Workspace Manager locking for the specified workspace.

#### Syntax

    DBMS_WM.SetWorkspaceLockModeON(
       workspace    IN VARCHAR2,
       lockmode     IN VARCHAR2,
       override     IN BOOLEAN DEFAULT FALSE,
       auto_commit  IN BOOLEAN DEFAULT TRUE);

#### Parameters

Table 4-85 SetWorkspaceLockModeON Procedure Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`   | Name of the workspace for which to enable Workspace Manager locking. The name is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `lockmode`    | Default locking mode for row-level locking. Must be `E`, `WE`, `VE`, `S`, `C`, or `D`.<br>`E` (exclusive) mode locks the rows in the parent workspace and the corresponding rows in the current workspace; no other users in either workspace can change any values.<br>`WE` (workspace-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values in the current workspace; however, other users in other workspaces can change the values.<br>`VE` (version-exclusive) mode locks the rows in the previous version and the corresponding rows in the current version such that only the user that set the lock can change the values; no other users (in any workspace) can change the values.<br>`S` (shared) mode locks the rows in the parent workspace and the corresponding rows in the current workspace; however, other users in the current workspace (but no users in the parent workspace) can change values in these rows.<br>`C` (carry-forward) mode locks rows in the current workspace with the same locking mode as the corresponding rows in the parent workspace. (If a row is not locked in the parent workspace, its corresponding row in the child workspace is not locked.)<br>`D` (disregard) mode disregards all locks. Any row can be updated in the workspace, even if it is locked by another workspace or the workspace is within a pessimistic setting. The consequences of using this mode are: (1) The workspace for which this mode is set cannot have its lockmode turned off (using SetLockingOFF) or changed (using SetLockingON) after rows have been modified. (2) The workspace cannot be merged. (3) The workspace cannot be refreshed. (4) The `override` option must be set to `false`. (5) When any child workspace is created from this workspace, the new workspace will inherit this same lockmode along with its restrictions. |
| `override`    | A Boolean value (`TRUE` or `FALSE`)<br>`TRUE` allows a session in the workspace to change the `lockmode` value by using the SetLockingON and SetLockingOFF procedures.<br>`FALSE` (the default) prevents a session in the workspace from changing the `lockmode` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `auto_commit` | A Boolean value (`TRUE` or `FALSE`).<br>`TRUE` (the default) causes the operation to be executed as an autonomous database transaction that will be committed when it finishes.<br>`FALSE` causes the operation to be executed as part of the caller's open database transaction (if one exists). If there is no open database transaction, the operation is executed in a new database transaction. In either case, the caller is responsible for committing the transaction. For more information, see [Autocommitting of Workspace Manager Operations](introduction-to-workspace-manager.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

#### Usage Notes

This procedure affects Workspace Manager locking, which occurs in addition to any standard Oracle database locking. Workspace Manager locks can be used to prevent conflicts. When a user locks a row, the corresponding row in the parent workspace is also locked. Thus, when this workspace merges with the parent at merge time, it is guaranteed that this row will not have a conflict.

For information about Workspace Manager lock management, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).

The main use for the"Disregard" locking mode (`lockmode` value of `D`) is so that a workspace can be completely isolated from the rest of the workspaces in the system and is free to update any rows it wants. It turns the workspace into a test ("sandbox") workspace where anything can be tested, but because it cannot merge or refresh, the workspace is unable to propagate its changes to other workspaces. It is meant for testing only, after which the workspace can be removed.

Exclusive locking (`lockmode` value of `E`) prevents the use of what-if scenarios in which different values for one or more columns are tested. Thus, plan any testing of scenarios when exclusive locking is not in effect.

If the override parameter value is `TRUE`, locking can also be enabled and disabled at the user session level with the SetLockingON and SetLockingOFF procedures, respectively.

All new changes by this session or a subsequent session are locked, unless the session turns locking off by executing the SetLockingOFF procedure.

An exception is raised if any of the following occurs:

- The user does not have the `WM_ADMIN` system privilege or is not the owner of `workspace`.

- `auto_commit` is `TRUE` and an open transaction exists.

- `lockmode` is `D` and the workspace either is continually refreshed or is the `LIVE` workspace.

#### Examples

The following example sets exclusive locking on for the workspace named `NEWWORKSPACE`.

    EXECUTE DBMS_WM.SetWorkspaceLockModeON ('NEWWORKSPACE', 'E');

All locked rows remain locked until the workspace is merged or rolled back.

**Parent topic:** DBMS_WM Package: Reference

### 4.100 UnfreezeWorkspace

Enables access and changes to a workspace, reversing the effect of the FreezeWorkspace procedure.

#### Syntax

    DBMS_WM.UnfreezeWorkspace(
       workspace  IN VARCHAR2);

#### Parameters

Table 4-86 UnfreezeWorkspace Procedure Parameters

| Parameter   | Description                                        |
|:------------|:---------------------------------------------------|
| `workspace` | Name of the workspace. The name is case-sensitive. |

#### Usage Notes

The operation fails if any sessions are in `workspace`.

You can unfreeze a workspace only if one or more of the following apply:

- You are the owner of the specified workspace.

- You have the `WM_ADMIN` system privilege, the `FREEZE_ANY_WORKSPACE` privilege, or the `FREEZE_WORKSPACE` privilege for the specified workspace.

#### Examples

The following example unfreezes the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.UnfreezeWorkspace ('NEWWORKSPACE');

**Parent topic:** DBMS_WM Package: Reference

### 4.101 UnlockRows

Enables access to versioned rows in a specified table and to corresponding rows in the parent workspace.

#### Syntax

    DBMS_WM.UnlockRows(
       workspace     IN VARCHAR2,
       table_name    IN VARCHAR2,
       where_clause  IN VARCHAR2 DEFAULT '',
       all_or_user   IN VARCHAR2 DEFAULT 'USER',
       lock_mode     IN VARCHAR2 DEFAULT 'ES',
       Xmin          IN NUMBER DEFAULT NULL,
       Ymin          IN NUMBER DEFAULT NULL,
       Xmax          IN NUMBER DEFAULT NULL,
       Ymax          IN NUMBER DEFAULT NULL);

#### Parameters

Table 4-87 UnlockRows Procedure Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `workspace`    | Name of the workspace: locked rows in this workspace and corresponding rows in the parent workspace will be unlocked, as specified in the remaining parameters. The name is case-sensitive.<br>A value of `NONE` can be used if `lock_mode` is set to `VE` (version-exclusive). This causes rows locked by any workspace to be unlocked.                                                                                                                                                                                                      |
| `table_name`   | Name of the table or (if `Xmin`, `Ymin`, `Xmax`, and `Ymax` are specified) Spatial and Graph topology in which rows are to be unlocked. The name is not case-sensitive.                                                                                                                                                                                                                                                                                                                                                                       |
| `where_clause` | The `WHERE` clause (excluding the `WHERE` keyword) identifying the rows to be unlocked. Example: `'department_id = 20'`<br>Only primary key columns can be specified in the `WHERE` clause, except in a subquery. The subquery can refer to columns that are not primary keys, but it cannot refer to a version-enabled table.<br>If the `where_clause` parameter is not specified, all rows in `table_name` are made accessible.<br>Do not specify the `where_clause` parameter if `table_name` specifies a Spatial and Graph topology name. |
| `all_or_user`  | Scope of the request: `ALL` or `USER`.<br>`ALL`: All locks accessible by the user in the specified workspace are considered.<br>`USER` (default): Only locks owned by the user in the specified workspace are considered.                                                                                                                                                                                                                                                                                                                     |
| `lock_mode`    | Locking mode: `E`, `WE`, `VE`, `S`, or `ES` (default).<br>`E` (exclusive): Only exclusive mode locks are considered.<br>`WE` (workspace-exclusive): Only workspace-exclusive mode locks are considered.<br>`VE` (version-exclusive): Only version-exclusive mode locks are considered.<br>`S` (shared): Only shared mode locks are considered.<br>`ES` (exclusive and shared: the default): Both exclusive mode and shared mode locks are considered.                                                                                         |
| `Xmin, Ymin`   | For Oracle Spatial and Graph topologies only (see [Locking Considerations with Topologies](introduction-to-workspace-manager.md)), the X and Y coordinate values, respectively, of the lower-left corner of the window containing the rows to be locked.You must specify these parameters if you specified a topology name for `table_name`; otherwise, do not specify these parameters.                                                                                                                                                      |
| `Xmax, Ymax`   | For Oracle Spatial and Graph topologies only (see [Locking Considerations with Topologies](introduction-to-workspace-manager.md)), the X and Y coordinate values, respectively, of the upper-right corner of the window containing the rows to be locked.You must specify these parameters if you specified a topology name for `table_name`; otherwise, do not specify these parameters.                                                                                                                                                     |

#### Usage Notes

This procedure affects Workspace Manager locking, which occurs in addition to any standard Oracle database locking. For an explanation of Workspace Manager locking, see [Lock Management with Workspace Manager](introduction-to-workspace-manager.md).

This procedure unlocks rows that were previously locked (see the LockRows procedure). It does not affect whether Workspace Manager locking is set on or off (determined by the SetLockingON and SetLockingOFF procedures).

For information about Workspace Manager locking for tables in an Oracle Spatial and Graph topology, see [Locking Considerations with Topologies](introduction-to-workspace-manager.md).

#### Examples

The following example unlocks the `EMPLOYEES` table where `last_name = 'Smith'` in the `NEWWORKSPACE` workspace.

    EXECUTE DBMS_WM.UnlockRows ('employees', 'NEWWORKSPACE', 'last_name = ''Smith''');

**Parent topic:** DBMS_WM Package: Reference

### 4.102 UseDefaultValuesForNulls

Determines whether or not Workspace Manager, for the current session, uses the default value for a column when the user either specifies a null value or does not specify any value for the column in an insert operation on a version-enabled table.

#### Syntax

    DBMS_WM.UseDefaultValuesForNulls(
       mode_var IN VARCHAR2);

#### Parameters

Table 4-88 UseDefaultValuesForNulls Procedure Parameters

| Parameter  | Description                                                                                                                                                                                                                     |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `mode_var` | Mode for handling the insertion of null values: `OFF` or `ON`.<br>`OFF`: A null value is inserted into the column. (This is the normal Oracle behavior.)<br>`ON`: The default value for the column is inserted into the column. |

#### Usage Notes

This procedure affects what Workspace Manager does only if an INSERT statement into a version-enabled table explicitly specifies NULL for a column when the column has been defined as having a default value or leaves the column unspecified. For example, assume the following table definition:

    CREATE TABLE players (name VARCHAR2(20) primary key, rating NUMBER DEFAULT 10);

If the `PLAYERS` table is version-enabled and if you have executed this procedure with a `mode_var` parameter value of `OFF`, either of the following statements would insert a row for `Smith` with a null `RATING` value:

    INSERT INTO players VALUES ('Smith', NULL);
    INSERT INTO players(name) VALUES ('Smith');

However, if you have executed the UseDefaultValuesForNulls procedure with a `mode_var` parameter value of `ON`, both statements insert a row for `Smith` with a `RATING` value of 10. If this procedure is not executed in a session, the default behavior is the same as if `mode_var` was specified as `ON`.

#### Examples

The following example causes the column default value to be used during the rest of the current session whenever an INSERT statement into a version-enabled table specifies a null value for a column that has a default value or the column is left unspecified.

    EXECUTE DBMS_WM.UseDefaultValuesForNulls('ON');

**Parent topic:** DBMS_WM Package: Reference
