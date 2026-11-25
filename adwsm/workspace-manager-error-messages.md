This appendix lists the Workspace Manager error messages, including the cause and recommended user action for each.

WM_ERROR_1 name of column 'string' has more than 28 characters
Cause: An attempt was made to version-enable a table that had a column with a name that has more than 28 characters.

Action: Ensure that all column names for the table are 28 characters or less.

WM_ERROR_2 'string' is not allowed for workspace: 'string' frozen in 'string' mode
Cause: An operation was executed on a workspace that was frozen.

Action: Unfreeze the workspace before retrying the operation.

WM_ERROR_3 cannot modify primary key values for version-enabled table
Cause: A DML operation that modifies one or more values in columns in the primary key constraint was performed on a version-enabled table.

Action: Do not perform DML operations on columns in the primary key constraints of version-enabled tables.

WM_ERROR_4 There are open short transactions on this table.
Cause: DisableVersioning failed because there were open database transactions on the table to be version-disabled.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_5 integrity constraint ('string'.'string') violated - child record found
Cause: An attempt was made to delete or update a record in a parent table of a referential integrity constraint with the RESTRICT option, and there was a matching record in the child table of the integrity constraint. RESTRICT is a default property of a referential integrity constraint, the other being ON DELETE CASCADE, where the dependent rows in the child tables are deleted if corresponding rows in the parent table are deleted. The CASCADE option applies only to a deletion from the parent table. An update of the parent table always follows the RESTRICT option.

Action: Delete all matching records from the child table first.

WM_ERROR_6 integrity constraint ('string'.'string') violated - parent key not found
Cause: An attempt was made to insert or update a record in a child table of a referential integrity constraint, and there was no matching record in the parent table of the integrity constraint.

Action: Insert a matching record in the parent table first.

WM_ERROR_7 WM not found on the import platform
Cause: Import of a version-enabled database failed because the import platform did not have Workspace Manager installed.

Action: Install Workspace Manager on the import platform and retry.

WM_ERROR_8 the import platform cannot have any versioned tables
Cause: Import of a version-enabled database failed because the import platform already had one or more version-enabled tables.

Action: The import platform may not have any version-enabled tables. A clean install of Workspace Manager is needed on the import platform.

WM_ERROR_9 the import platform has non-"LIVE" workspaces or explicit savepoints
Cause: Import of a version-enabled database failed because the import platform had either non-`LIVE` workspaces in the workspace hierarchy or explicit savepoints in the `LIVE` workspace.

Action: The import platform may have only the `LIVE` workspace and there may be no explicit savepoints. A clean install of Workspace Manager is needed on the import platform.

WM_ERROR_10 unique key violation
Cause: An insert operation failed because it violated the table's primary key constraint.

Action: Ensure that the primary key is not violated by the insert operation in the current workspace.

WM_ERROR_11 need to be on the latest version to delete
Cause: A delete operation failed because the delete was being made in a non-`LATEST` version of a workspace.

Action: Ensure that the current session is on the `LATEST` version in the workspace by using the GotoWorkspace or GotoSavepoint procedures.

WM_ERROR_12 need to be on the latest version to insert
Cause: An insert operation failed because the insert was being made in a non-`LATEST` version of a workspace.

Action: Ensure that the current session is on the `LATEST` version in the workspace by using the GotoWorkspace or GotoSavepoint procedures.

WM_ERROR_13 need to be on the latest version to update
Cause: An update operation failed because the update was made in a non-`LATEST` version of a workspace.

Action: Ensure that the current session is on the `LATEST` version in the workspace by using the GotoWorkspace or GotoSavepoint procedures.

WM_ERROR_14 'string'.'string' has not been version enabled
Cause: This operation failed because it can only be invoked on a version-enabled table.

Action: Verify that the table is version-enabled.

WM_ERROR_15 "/" is not allowed in a workspace name
Cause: CreateWorkspace failed because the workspace name contained a "/".

Action: Choose another workspace name that does not contain a "/".

WM_ERROR_16 "WM_ADMIN" system privilege is required to version disable a table in another schema
Cause: DisableVersioning failed because only a user with the `WM_ADMIN` system privilege can version-disable a table in another schema.

Action: Ensure that the invoking user has the required privileges before attempting to version-disable this table. Otherwise, have the owner of the table version-disable it.

WM_ERROR_17 "WM_ADMIN" system privilege is required to version enable a table in another schema
Cause: EnableVersioning failed because only a user with the `WM_ADMIN` system privilege can version-enable a table in another schema.

Action: Ensure that the invoking user has the required privileges before attempting to version-enable this table. Otherwise, have the owner of the table version-enable it.

WM_ERROR_18 "WM_ADMIN" system privilege or ownership is required to alter workspace attributes
Cause: AlterWorkspace failed because only a user with the `WM_ADMIN` system privilege or the owner of the workspace can alter workspace attributes.

Action: Ensure that the invoking user has the required privileges before attempting to alter the workspace attributes. Otherwise, have the owner of the workspace alter the workspace attributes.

WM_ERROR_19 "WM_ADMIN" system privilege or ownership is required to freeze a workspace
Cause: FreezeWorkspace failed because only a user with the `WM_ADMIN` system privilege or the owner of the workspace can freeze a workspace.

Action: Ensure that the invoking user has the required privileges before attempting to freeze the workspace. Otherwise, have the owner of the workspace freeze it.

WM_ERROR_20 "WM_ADMIN" system privilege or ownership is required to set workspace lock mode
Cause: SetWorkspaceLockModeOn failed because only a user with the `WM_ADMIN` system privilege or the owner of the workspace can set the workspace lock mode.

Action: Ensure that the invoking user has the required privileges before attempting to set the workspace lock mode. Otherwise, have the owner of the workspace set the workspace lock mode.

WM_ERROR_21 insufficient privileges to change savepoint attributes
Cause: AlterSavepoint failed because only a user with the `WM_ADMIN` system privilege or the owner of the workspace or savepoint can alter the savepoint attributes.

Action: Ensure that the invoking user has the required privileges before attempting to alter the savepoint attributes. Otherwise, have the workspace owner or the savepoint owner alter the savepoint attributes.

WM_ERROR_22 insufficient privileges to delete savepoint
Cause: DeleteSavepoint failed because only a user with the `WM_ADMIN` system privilege or the owner of the workspace or savepoint can delete the savepoint.

Action: Ensure that the invoking user has the required privileges before attempting to delete the savepoint. Otherwise, have the workspace owner or the savepoint owner delete the savepoint.

WM_ERROR_23 a workspace already exists with the name: 'string'
Cause: CreateWorkspace failed because a workspace with the same name already existed in the system. Workspace Manager requires that workspace names be unique across the database.

Action: Choose another workspace name and retry.

WM_ERROR_24 a workspace cannot be rolled back over an implicit savepoint
Cause: A RollbackWorkspace operation was invoked on a non-leaf workspace across an implicit savepoint.

Action: Do not rollback over an implicit savepoint. To remove the implicit savepoint, merge or remove the descendant workspace.

WM_ERROR_25 a table cannot be merged from the "LIVE" workspace
Cause: MergeTable was invoked with the input workspace specified as the `LIVE` workspace. The `LIVE` workspace is the root workspace in the workspace hierarchy tree.

Action: Do not invoke MergeTable with the workspace parameter `LIVE`.

WM_ERROR_27 a table cannot be refreshed to the "LIVE" workspace
Cause: RefreshTable was invoked with the input workspace specified as the `LIVE` workspace. The `LIVE` workspace is the root workspace in the workspace hierarchy tree.

Action: Do not invoke RefreshTable with the workspace parameter `LIVE`.

WM_ERROR_28 a table cannot be rolled back over an implicit savepoint
Cause: A RollbackTable operation was invoked on a non-leaf workspace across an implicit savepoint.

Action: Do not rollback over an implicit savepoint. To remove the implicit savepoint, merge or remove the descendant workspace.

WM_ERROR_29 cannot rollback this table using RollbackTable
Cause: RollbackTable failed because the table to be rolled back is part of a referential integrity constraint.

Action: Use RollbackWorkspace or RollbackToSP instead.

WM_ERROR_30 cannot merge this table using MergeTable
Cause: MergeTable failed because the table to be merged is part of a referential integrity constraint.

Action: Use MergeWorkspace instead.

WM_ERROR_31 All version enabled tables owned by 'string' must be disabled first.
Cause: An attempt was made to drop a database user who owns one or more version-enabled tables.

Action: Ensure that all the version-enabled tables owned by the user have been explicitly disabled before attempting to drop the database user.

WM_ERROR_32 An index-organized table cannot be version enabled.
Cause: Workspace Manager does not support index-organized tables.

Action: Ensure the table to be version-enabled is not index-organized.

WM_ERROR_33 attempt to 'string' a row locked by: 'string' in workspace 'string'
Cause: A DML operation failed because the row was previously locked.

Action: Wait for the lock on the row to be released or have the lock owner use the UnlockRows procedure to unlock the row. Consult the table's \_LOCK view to see which rows in this table are locked.

WM_ERROR_34 attempt to 'string' a row locked by 'string' in workspace: 'string'
Cause: A DML operation failed because the row was previously locked.

Action: Wait for the lock on the row to be released or have the lock owner use the UnlockRows procedure to unlock the row. Consult the table's \_LOCK view to see which rows in this table are locked.

WM_ERROR_35 attempt to lock a row locked in workspace: 'string'
Cause: The operation failed because a lock could not be obtained on the row, since it was already locked.

Action: Wait for the lock on the row to be released or have the lock owner use the UnlockRows procedure to unlock the row. Consult the table's \_LOCK view to see which rows in this table are locked.

WM_ERROR_36 attempt to lock a row locked by 'string'
Cause: The operation failed because a lock could not be obtained on the row, since it was already locked.

Action: Wait for the lock on the row to be released or have the lock owner use the UnlockRows procedure to unlock the row. Consult the table's \_LOCK view to see which rows in this table are locked.

WM_ERROR_37 attempt to modify a WM generated procedure
Cause: An attempt to drop or re-create a database procedure failed because that procedure was created by Workspace Manager.

Action: Do not drop or re-create this procedure.

WM_ERROR_38 cannot disable version a table modified in non-LIVE workspaces
Cause: DisableVersioning failed because the table had been modified in non-`LIVE` workspaces.

Action: Remove or merge all workspaces that have modified this table. Otherwise, use the `FORCE` option of DisableVersioning.

WM_ERROR_39 cannot drop tables involved in foreign key relationships
Cause: An attempt to drop a database table failed because it was involved in a foreign key relationship with a version-enabled table.

Action: Consult the WM_RIC_INFO view and version-disable the table that is involved in the foreign key relationship before attempting to drop the table.

WM_ERROR_40 only grantor of a privilege may revoke it
Cause: An attempt was made to revoke a privilege that was not granted by the current user.

Action: Do not attempt to revoke this privilege.

WM_ERROR_41 unable to set workspace lock mode
Cause: SetWorkspaceLockModeOn failed because the workspace contained modifications from one or more version-enabled tables.

Action: Use SetLockingOn to set the session's lock mode. Use SetWorkspaceLockModeOn only for those workspaces that have not yet modified any version-enabled tables.

WM_ERROR_42 cannot version enable tables owned by 'string'
Cause: EnableVersioning failed because Workspace Manager cannot version-enable tables owned by the specified user.

Action: Do not invoke EnableVersioning on tables owned by that user.

WM_ERROR_43 A continually refreshed workspace must be a leaf workspace.
Cause: CreateWorkspace failed because the workspace to be created was to be a child of a continually refreshed workspace. Continually refreshed workspaces carry with them the restriction that they must be leaf workspaces.

Action: Do not create a workspace off of a continually refreshed workspace.

WM_ERROR_44 insufficient privileges to merge data
Cause: The merge operation failed because the user does not have both `ACCESS` and `MERGE` privileges on the workspace on which it was invoked; or, in a multiparent workspace environment, the user does not have both `ACCESS` and `MERGE` privileges on the non-root workspaces and `ACCESS` privilege on the root workspace of the multiparent workspace graph.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges.

WM_ERROR_45 merge operation requires ACCESS privileges on the parent workspace
Cause: The operation invoked failed because it required `ACCESS` privileges on the parent workspace of the workspace it was invoked on.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges on the parent workspace.

WM_ERROR_46 commit/rollback open short transactions before calling CommitResolve
Cause: CommitResolve failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_47 commit/rollback open short transactions before calling CompressWorkspace
Cause: CompressWorkspace failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_48 commit/rollback open short transactions before calling CompressWorkspaceTree
Cause: CompressWorkspaceTree failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_49 commit/rollback open short transactions before calling DeleteSavepoint
Cause: DeleteSavepoint failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard data

WM_ERROR_50 commit/rollback open short transactions before calling GotoWorkspace
Cause: GotoWorkspace failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_51 commit/rollback open short transactions before calling RollbackResolve
Cause: RollbackResolve failed because open database transactions existed.

Action: The user with the open database transaction should issue a standard database commit or rollback.

WM_ERROR_52 CommitResolve can be called only after BeginResolve has been invoked
Cause: CommitResolve failed because BeginResolve was not previously invoked.

Action: To resolve conflicts, first issue a BeginResolve, then issue ResolveConflicts, and finally issue CommitResolve.

WM_ERROR_53 CompressWorkspace operation requires ACCESS and MERGE privileges on the workspace
Cause: The operation invoked failed because it required both `ACCESS` and `MERGE` privileges on the workspace on which it was invoked.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges on the workspace.

WM_ERROR_54 CompressWorkspace operation requires ACCESS privilege on the workspace
Cause: The operation invoked failed because it required `ACCESS` privileges on the workspace on which it was invoked.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges on the workspace.

WM_ERROR_55 conflicts detected for workspace: 'string' in table: 'string'
Cause: An operation failed because there were conflicts detected for the table.

Action: To resolve conflicts, first issue a BeginResolve, then issue ResolveConflicts, and finally issue CommitResolve. Otherwise, refrain from calling this operation.

WM_ERROR_56 conflicts detected for workspace: 'string' in table: 'string'.'string'
Cause: An operation failed because there were conflicts detected for the table.

Action: To resolve conflicts, first issue a BeginResolve, then issue ResolveConflicts, and finally issue CommitResolve. Otherwise, refrain from calling this operation.

WM_ERROR_57 CreateSavepoint operation requires ACCESS privileges on the workspace
Cause: The operation invoked failed because it required `ACCESS` privileges on the workspace on which it was invoked.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges on the workspace.

WM_ERROR_58 RemoveWorkspace operation requires ACCESS and REMOVE privileges on the workspace
Cause: The operation invoked failed because it required both `ACCESS` and `REMOVE` privileges on the workspace on which it was invoked.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges on the workspace.

WM_ERROR_59 entry already exists in spatial metadata table for 'string'\_WM
Cause: EnableVersioning of the spatial table failed because the spatial metadata table already contained an entry for the table.

Action: Contact Oracle Support Services.

WM_ERROR_60 user must call BeginResolve or have "WM_ADMIN" system privilege to invoke RollbackResolve
Cause: RollbackResolve can be successful only if the user invoking it also invoked BeginResolve, or if the user invoking it had the `WM_ADMIN` system privilege.

Action: Ensure that the invoking user has the required privileges before attempting to invoke RollbackResolve. Otherwise, have the user that issued the BeginResolve operation invoke RollbackResolve.

WM_ERROR_61 versioned objects have to be version disabled before being dropped
Cause: An attempt to drop a database table or view failed because it was associated with a version-enabled table.

Action: version-disable the table first. In the case of a view, version-disable the table associated with the view.

WM_ERROR_62 versioned table: 'string' does not exist
Cause: The operation failed because the table passed in as input did not exist or was not version-enabled.

Action: Pass in an existing, version-enabled table as input.

WM_ERROR_63 need to be on the latest version to create a continually refreshed workspace.
Cause: CreateWorkspace failed because the session was in a non-`LATEST` version of the workspace.

Action: Ensure that the current session is on the `LATEST` version in the workspace by using the GotoWorkspace or GotoSavepoint procedures.

WM_ERROR_64 need to be on the latest version to create a savepoint
Cause: CreateSavepoint failed because the session was in a non-`LATEST` version of the workspace.

Action: Ensure that the current session is on the `LATEST` version in the workspace by using the GotoWorkspace or GotoSavepoint procedures.

WM_ERROR_65 grantor and grantee may not be the same user
Cause: An attempt was made to grant or revoke a privilege from or to the same user.

Action: Do not attempt to grant or revoke privileges from or to the same user. Privileges can only be granted or revoked between different users.

WM_ERROR_66 unable to version enable this table with history option
Cause: An attempt was made to version-enable a table with `VIEW_WO_OVERWRITE` or `VIEW_W_OVERWRITE` option and the cumulative length of the names of the primary key columns was greater than 600.

Action: Rename the primary key columns.

WM_ERROR_67 grantee must be an existing user, an existing role or PUBLIC
Cause: A grant operation was attempted with an invalid grantee parameter.

Action: The grantee may only be an existing user, role, or `PUBLIC`. Verify correct spelling of the grantee parameter.

WM_ERROR_68 input parameter grant_option must be "YES" or "NO"
Cause: An attempt was made to invoke the GrantWorkspacePriv or GrantSystemPriv procedure with an invalid input parameter.

Action: Ensure that the valid parameters are passed to the GrantWorkspacePriv or GrantSystemPriv procedure. The `grant_option` parameter may only be `YES` or `NO`.

WM_ERROR_69 invalid in_date time for GotoDate
Cause: GotoDate was invoked with an `in_date` time less than the create time of the current workspace.

Action: The `in_date` parameter for GotoDate must be greater than or equal to the create time for the current workspace.

WM_ERROR_70 insufficient privileges on 'string' to lock rows
Cause: An attempt was made to invoke the LockRows procedure on a versioned table without the required privileges on the table.

Action: Ensure that the invoking user has the required privileges before invoking the operation. The lockRows procedure requires the invoking user to have SELECT, INSERT, UPDATE and DELETE privileges on the versioned table.

WM_ERROR_71 insufficient privileges on 'string' to unlock rows
Cause: An attempt was made to invoke the UnlockRows procedure on a versioned table without the required privileges on the table.

Action: Ensure that the invoking user has the required privileges before invoking the operation. The UnlockRows procedure requires the invoking user to have `SELECT`, `INSERT`, `UPDATE` and `DELETE` privileges on the versioned table.

WM_ERROR_72 insufficient privileges on 'string'.'string'
Cause: An attempt was made to invoke the ResolveConflicts procedure on a versioned table without the required privileges on the table.

Action: Ensure that the invoking user has the required privileges before invoking the operation. The ResolveConflicts procedure requires the invoking user to have `SELECT`, `INSERT`, `UPDATE` and `DELETE` privileges on the versioned table being conflict resolved.

WM_ERROR_73 insufficient privileges to ACCESS the workspace: 'string'
Cause: An attempt was made to invoke an operation that required the specified privileges on the input workspace.

Action: Ensure that the invoking user has the required privileges before invoking the operation. Privileges can be granted using the GrantWorkspacePriv or the GrantSystemPriv procedures. Use the function GetPrivs to see which privileges you have on a workspace.

WM_ERROR_74 insufficient privileges to ACCESS the parent workspace: 'string'
Cause: An attempt was made to invoke an operation that required the specified privileges on the parent workspace of the input workspace.

Action: Ensure that the invoking user has the required privileges before invoking the operation. Privileges can be granted using the grantWorkspacePriv or the grantSystemPriv procedures. Use the function GetPrivs to see which privileges you have on a workspace.

WM_ERROR_75 insufficient privileges to create a child workspace of: 'string'
Cause: An attempt was made to invoke the CreateWorkspace procedure from a workspace without the required privileges on the workspace.

Action: Ensure that the invoking user has the required privileges before invoking the operation. The invoking user must have `CREATE` privileges on a workspace to be allowed to create a workspace off of it. Privileges can be granted using the grantWorkspacePriv or the grantSystemPriv procedures. Use the function GetPrivs to see which privileges you have on a workspace.

WM_ERROR_76 insufficient privileges to grant 'string'
Cause: An attempt was made to invoke the GrantWorkspacePriv or GrantSystemPriv procedure without the required privileges to do so.

Action: Ensure that the invoking user has the required privileges to grant the privilege. A user needs to have been granted a privilege with the `GRANT` option to be able to grant it to others.

WM_ERROR_77 insufficient privileges on the versioned table 'string'
Cause: An attempt was made to invoke a Workspace Manager procedure without the required privileges on the versioned table.

Action: Ensure that the invoking user has the required privileges before invoking the operation. All Workspace Manager workspace wide operations require the invoking user to have `SELECT`, `INSERT`, `UPDATE` and `DELETE` privileges on all versioned tables that were modified in the input workspace.

WM_ERROR_78 insufficient privileges on the versioned table: 'string'.'string'
Cause: An attempt was made to invoke a Workspace Manager procedure without the required privileges on the versioned table.

Action: Ensure that the invoking user has the required privileges before invoking the operation. All Workspace Manager workspace wide operations require the invoking user to have `SELECT`, `INSERT`, `UPDATE` and `DELETE` privileges on all versioned tables that were modified in the input workspace.

WM_ERROR_79 WM internal error \['string'\]
Cause: A Workspace Manager operation resulted in an internal error.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_80 invalid "hist" parameter for EnableVersioning
Cause: An invalid value was specified for the `hist` parameter of procedure EnableVersioning.

Action: Valid values for the `hist` parameter are `NONE`, `VIEW_W_OVERWRITE`, and `VIEW_WO_OVERWRITE`.

WM_ERROR_81 invalid column name specified in the where-clause
Cause: An attempt was made to invoke a Workspace Manager procedure with an invalid `where_clause` parameter as input.

Action: Ensure that the input `where_clause` parameter contains only valid column names and has proper syntax.

WM_ERROR_82 invalid privilege type: 'string' was specified as input
Cause: An attempt was made to invoke a Grant or Revoke Privilege procedure with an invalid priv_type parameter.

Action: Ensure that the valid parameters are passed to the Grant or Revoke Privilege operation. The valid privilege types are: `ACCESS_WORKSPACE`, `MERGE_WORKSPACE`, `ROLLBACK_WORKSPACE`, `REVOKE_WORKSPACE`, and `CREATE_WORKSPACE`.

WM_ERROR_83 invalid user specified for the freezewriter parameter
Cause: The FreezeWorkspace procedure was called with an invalid `freezewriter` parameter.

Action: Ensure that the freezewriter parameter passed in as input to the FreezeWorkspace procedure is an existing database user.

WM_ERROR_84 invalid value for lock_mode - "E" or "S" expected
Cause: An invalid value was specified for the `lock_mode` parameter of procedure LockRows.

Action: Specify a valid value for lock_mode. The valid values for `lock_mode` are `E` and `S` (default is `E`).

WM_ERROR_85 invalid value for the lock_mode argument - "E", "S" or "ES" expected
Cause: An invalid value has been specified for the `lock_mode` parameter (fifth parameter) of procedure UnlockRows.

Action: Specify a valid value for lock_mode. The valid values for `lock_mode` are `E`, `S`, and `ES` (default is `ES`).

WM_ERROR_86 invalid value for the all_or_user argument - "ALL" or "USER" expected
Cause: An invalid value has been specified for the `all_or_user` parameter (fourth parameter) of procedure UnlockRows.

Action: Specify a valid value for `all_or_user`. The valid values for `all_or_user` are `ALL` and `USER` (default is `USER`).

WM_ERROR_87 IsWorkspaceOccupied cannot be used for the 'string' workspace
Cause: A user attempted to invoke IsWorkspaceOccupied on the default workspace.

Action: Workspace Manager allows IsWorkspaceOccupied to be invoked only on workspaces that are not the default workspace. The default workspace, as defined by the DEFAULT_WORKSPACE system parameter, is not monitored by Workspace Manager for users in the workspace.  Do not invoke this method on the specified workspace.

WM_ERROR_88 IsWorkspaceOccupied requires ACCESS privilege on the workspace
Cause: IsWorkspaceOccupied was invoked for a workspace on which the user did not have `ACCESS` privilege.

Action: IsWorkspaceOccupied can only be invoked for a workspace on which the user has `ACCESS` privilege.

WM_ERROR_89 "LIVE" workspace can be frozen only in (READ_ONLY, 1WRITER, 1WRITER_SESSION, WM_ONLY) modes
Cause: An attempt was made to Freeze the `LIVE` workspace in `NO_ACCESS` mode. Workspace Manager does not support this mode for the `LIVE` workspace.

Action: Use one of (`READ_ONLY`, `1WRITER`, `1WRITER_SESSION`, `WM_ONLY`) modes to freeze the `LIVE` workspace.

WM_ERROR_90 lock operation requires ACCESS privilege on the parent workspace
Cause: LockRows was invoked for a workspace whose parent workspace was not accessible to the user.

Action: The user requires `ACCESS` privilege on the parent workspace of the workspace for which lockRows in invoked.

WM_ERROR_91 lock operation requires ACCESS privilege on the workspace
Cause: LockRows was invoked for a workspace on which the user did not have ACCESS privilege.

Action: The user requires `ACCESS` privilege on the workspace for which LockRows in invoked.

WM_ERROR_92 cannot 'string' because locking is on and row is already versioned
Cause: An attempt to place a shared or exclusive lock on a row in a versioned table failed because the row was already versioned in some other workspace.

Action: To update, delete, or insert a row that was already versioned in some other workspace, the current session must turn locking off. Consult the table's \_LOCK view to see which rows in this table are locked.

WM_ERROR_93 The multi-workspace view requires ACCESS privilege on the workspace : 'string'
Cause: SetMultiWorkspaces was invoked with the name of a workspace on which the user did not have `ACCESS` privilege.

Action: Names of only those workspaces for which the user has `ACCESS` privilege can be passed to SetMultiWorkspaces.

WM_ERROR_94 non-existent versioned table: 'string'.'string'
Cause: This operation was invoked on a non-version-enabled table.

Action: This operation can only be invoked on a version-enabled table. Verify that the table is version-enabled. The xxx\_VERSIONED_TABLES views show all the versioned tables in the database.

WM_ERROR_95 null savepoint name passed in as input
Cause: An attempt was made to invoke a Workspace Manager procedure with a null savepoint name parameter.

Action: Pass in a non-null savepoint parameter for this procedure to succeed

WM_ERROR_96 null workspace name passed in as input
Cause: A null value was passed in as input to a Workspace Manager operation

Action: Pass in a non-null workspace parameter for this operation to succeed

WM_ERROR_97 null table name parameter passed in
Cause: MergeTable was invoked with a null table name.

Action: Specify the name of the version-enabled table to be merged.

WM_ERROR_98 Number of workspaces in the multi-workspace view cannot be greater than 8.
Cause: SetMultiWorkspaces was invoked with more than 8 workspace names.

Action: Invoke SetMultiWorkspaces with 8 or fewer workspace names.

WM_ERROR_99 WM failed to install - system triggers not properly created
Cause: One of the Workspace Manager generated database triggers was not created properly.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_100 'string' is both parent and child tables of referential integrity constraints
Cause: An attempt was made to version-enable a table that was both parent and child tables of referential integrity constraints.

Action: Version-enable both tables (specifying a comma-delimited list of table names) in the same call to the [EnableVersioning](DBMS_WM-reference.md) procedure.

WM_ERROR_101 child table must be version enabled
Cause: An attempt was made to version-enable the parent table of a referential integrity constraint whose child table was not version-enabled.

Action: Before version-enabling a table, all tables that are child tables of referential integrity constraints (excluding self referential integrity constraints) that have this table as the parent table must be version-enabled.

WM_ERROR_102 cannot version enable this table
Cause: An attempt was made to version-enable a table that was the child table of a non-self referential integrity constraint with the CASCADE option and that had a self referential integrity constraint defined on it.

Action: If application semantics permit, change the CASCADE option to the RESTRICT option.

WM_ERROR_103 cannot version disable this table with force option
Cause: The FORCE option was specified while version-disabling a table that was the parent table of a referential integrity constraint.

Action: The FORCE option cannot be specified while version-disabling a table that is the parent table of a referential integrity constraint. Commit or roll back all changes done on this table in non-`LIVE` workspaces and then version-disable the table without the FORCE option.

WM_ERROR_104 cannot version disable this table
Cause: An attempt has been made to version-disable the child table of a referential integrity constraint whose parent table was still version-enabled.

Action: Version-disable the parent table before version-disabling this table.

WM_ERROR_105 owner of constraint ('string'.'string') must have select privilege on the parent
Cause: An attempt was made to version-enable a table that was the child table of a referential integrity constraint with another table, and the owner of the table to be version-enabled did not have `SELECT` privilege on the parent table.

Action: Workspace Manager requires that before version-enabling the child table of a integrity constraint, the child table owner must have `SELECT` privilege on the parent table. Grant the required privilege before version-enabling.

WM_ERROR_106 select and delete privileges needed on the child of constraint ('string'.'string')
Cause: An attempt was made to version-enable a table that was the parent table of a referential integrity constraint with another table and the owner of the table to be version-enabled did not have the specified privilege on the child table.

Action: Workspace Manager requires that before version-enabling the parent table of a referential integrity constraint, the parent table owner must have the specified privilege on the child table. Grant the privilege on the child table to the owner of the table being version-enabled.

WM_ERROR_107 select privilege needed on the child of constraint ('string'.'string')
Cause: An attempt was made to version-enable a table that was the parent table of a referential integrity constraint with another table and the owner of the table to be version-enabled did not have the specified privilege on the child table.

Action: Workspace Manager requires that before version-enabling the parent table of a referential integrity constraint, the parent table owner must have the specified privilege on the child table. Grant the privilege on the child table to the owner of the table being version-enabled.

WM_ERROR_108 triggering event 'string' not allowed
Cause: A triggering event of the form "insert OR update OR delete" was specified.

Action: Drop the trigger and re-create separate triggers (with identical bodies) for insert, update, and delete.

WM_ERROR_109 a table with unique constraints cannot be version enabled
Cause: An attempt was made to version-enable a table that had unique constraints defined on it.

Action: Drop the unique constraint on this table before version-enabling it. If the table needs to have a index for performance reasons, create a non-unique index on the relevant set of columns. Oracle will use the created index to optimize queries on the version-enabled table whenever appropriate.

WM_ERROR_112 insufficient privileges to refresh data
Cause: The refresh operation failed because the user does not have both `ACCESS` and `MERGE` privileges on the child workspace on which it was invoked; or, in a multiparent workspace environment, the user does not have both `ACCESS` and `MERGE` privileges on the non-root workspaces and `ACCESS` privilege on the root workspace of the multiparent workspace graph.

Action: Use the GetPrivs function to ensure that the user invoking this operation has the required privileges.

WM_ERROR_113 refresh operation requires ACCESS privileges on the parent workspace
Cause: An attempt was made to invoke RefreshTable or RefreshWorkspace and the user did not have `ACCESS` privilege on the parent workspace.

Action: Ensure that the invoking user has `ACCESS` privilege on the parent workspace before invoking RefreshTable or RefreshWorkspace. Privileges can be granted using the GrantWorkspacePriv or the GrantSystemPriv procedures. Use the GetPrivs function to see which privileges the current user has on a workspace.

WM_ERROR_114 Continually refreshed workspaces can be created only off of the "LIVE" workspace
Cause: An attempt was made to create a continually refreshed workspace off a non-`LIVE` workspace.

Action: Workspace Manager only supports creation of continually refreshed workspaces off the `LIVE` workspace. The user needs to be in the `LIVE` workspace before invoking CreateWorkspace for creating a continually refreshed workspace.

WM_ERROR_115 ResolveConflicts can be called only after BeginResolve is invoked
Cause: The ResolveConflicts procedure was invoked without calling the BeginResolve procedure first.

Action: Ensure that BeginResolve is invoked by the current user on a workspace before invoking ResolveConflicts for a version-enabled table in that workspace. (See the Resolving Conflicts section of the User Guide for details on the process of resolving conflicts for version-enabled tables.)

WM_ERROR_116 rollback operation requires ACCESS and ROLLBACK privileges on the workspace
Cause: An attempt was made to invoke RollbackTable or RollbackWorkspace and the user did not have ACCESS or ROLLBACK privilege on the workspace.

Action: Ensure that the invoking user has ACCESS and ROLLBACK privileges on the workspace before invoking RollbackTable or RollbackWorkspace. Privileges can be granted using the GrantWorkspacePriv or the GrantSystemPriv procedures. Use the function GetPrivs to see which privileges the current user has on a workspace.

WM_ERROR_117 RollbackResolve can be called only after BeginResolve has been invoked
Cause: RollbackResolve procedure was invoked without calling the BeginResolve procedure first.

Action: Ensure that BeginResolve is invoked before you invoke RollbackResolve. (See the Resolving Conflicts section of the User Guide for details on the process of resolving conflicts for version-enabled tables.)

WM_ERROR_118 savepoint names may not be longer than 30 characters
Cause: An attempt was made to create a savepoint whose name had more than 30 characters.

Action: Choose a shorter savepoint name.

WM_ERROR_119 savepoint names may not begin with \\ICP-\\
Cause: An attempt was made to create a savepoint whose name began with the string "ICP-".

Action: Choose a savepoint name that does not begin with the string "ICP-". Workspace Manager reserves names starting with "ICP-" for naming implicit savepoints.

WM_ERROR_120 savepoint: 'string' already exists in workspace: 'string'
Cause: An attempt was made to create a savepoint with the same name as an existing savepoint. Workspace Manager savepoint names must be unique within a workspace.

Action: Choose another savepoint name.

WM_ERROR_121 savepoint: 'string' does not exist in workspace: 'string'
Cause: An attempt was made to invoke a Workspace Manager operation on a savepoint that did not exist in the specified workspace.

Action: Verify that the savepoint name is spelled correctly and that it exists in the specified workspace. Workspace names and savepoint names are case-sensitive.

WM_ERROR_122 workspace 'string' does not exist
Cause: An attempt was made to invoke a Workspace Manager operation on a workspace that did not exist.

Action: Pass in an existing workspace name as input. Workspace names and savepoint names are case-sensitive.

WM_ERROR_123 workspace 'string' is currently frozen in 'string' mode
Cause: The user invoked a Workspace Manager operation that cannot proceed because the specified workspace has been frozen in the specified mode.

Action: Wait for the database session that holds the lock to release the lock. See the Workspace Manager documentation for a description of the Workspace Manager operations allowed for different workspace freeze modes. Consult the xxx\_WM_WORKSPACES view to see which workspaces are currently frozen.

WM_ERROR_124 workspace name may not be "BASE"
Cause: A user attempted to create a workspace with the name `BASE`.

Action: Workspace Manager considers "BASE" to be a reserved keyword. Therefore, Workspace Manager does not allow the workspace to be named `BASE`. Choose another workspace name.

WM_ERROR_125 workspace name may not be "LIVE"
Cause: A user attempted to create a workspace with the name `LIVE`.

Action: Workspace Manager considers "LIVE" to be a reserved keyword. Therefore, Workspace Manager does not allow new workspaces to be named `LIVE`. Choose another workspace name.

WM_ERROR_126 workspace name may not exceed 30 characters
Cause: A user attempted to create a workspace with the workspace name length greater than 30 characters.

Action: Workspace Manager limits workspace names to 30 characters. Choose a shorter workspace name.

WM_ERROR_127 workspace: 'string' is already being conflict resolved by user: 'string'
Cause: A user attempted to invoke BeginResolve on a workspace that was already being conflict resolved by some other user.

Action: Workspace Manager allows only one user to resolve conflicts for a workspace at the same time. Wait until the user is finished resolving conflicts in the workspace and verify that the conflicts you are attempting to resolve still exist. Use the xxx\_WORKSPACES views to check on the current resolve status of the workspace.

WM_ERROR_128 workspace: 'string' is temporarily frozen in an internal mode for a 'string' operation
Cause: A user attempted to invoke a Workspace Manager operation on a workspace that was frozen internally for another Workspace Manager operation.

Action: Workspace Manager acquires internal freezes on workspaces for the duration of various Workspace Manager operations. Wait until Workspace Manager releases the internal freeze on the workspace. See the User Guide for details on the freezes that Workspace Manager acquires for various workspace-wide operations. Use the xxx\_WORKSPACES views to check on the current freeze status of the workspace.

WM_ERROR_129 table 'string' does not exist
Cause: An attempt was made to invoke a Workspace Manager operation on a table that did not exist.

Action: Verify that the table exists.

WM_ERROR_130 table 'string' has been modified in an open transaction
Cause: An attempt was made to execute a Workspace Manager operation that required that there be no open database transactions on the table.

Action: Ensure that all open database transactions on the specified table have completed before invoking the Workspace Manager operation.

WM_ERROR_131 table 'string' is already version enabled
Cause: The specified table is already version-enabled.

Action: To version-disable it, execute the DisableVersioning procedure. The xxx\_VERSIONED_TABLES views show all the versioned tables in the database.

WM_ERROR_132 table 'string' is not version enabled
Cause: This operation can only be invoked on a version-enabled table.

Action: Verify that the specified table is version-enabled. The xxx\_VERSIONED_TABLES views show all the versioned tables in the database.

WM_ERROR_133 table 'string' needs to have a primary key
Cause: An attempt was made to version-enable a table that did not have a primary key defined on it. Workspace Manager requires that a primary key exist on a version-enabled table.

Action: Add a primary key constraint on this table before version-enabling it.

WM_ERROR_134 table 'string' is already being version disabled
Cause: An attempt was made to version-disable a table which another transaction was in the process of version-disabling.

Action: Wait until the other transaction finishes version-disabling the specified table. The xxx\_VERSIONED_TABLES views show all the versioned tables in the database.

WM_ERROR_135 table 'string' is being version enabled
Cause: An attempt was made to version-enable a table which another transaction was in the process of version-enabling.

Action: Wait until the other transaction finishes version-enabling the specified table. The xxx\_VERSIONED_TABLES views show all the versioned tables in the database.

WM_ERROR_136 table names are limited to 25 characters
Cause: An attempt was made to version-enable a table whose name was longer than 25 characters, or to perform another action (such as an export from a staging table) where the table name was longer than 25 characters.

Action: Rename the table to a shorter table name.

WM_ERROR_138 table: 'string' is in use in other sessions
Cause: An attempt to version-disable a table has failed due to the existence of database transaction locks on the table.

Action: To successfully version-disable this table, verify that there are no database transaction locks on the table.

WM_ERROR_140 invalid value for FreezeMode parameter
Cause: An attempt was made to invoke the FreezeWorkspace procedure with an invalid `freezemode` parameter.

Action: The freezemode parameter for the FreezeWorkspace procedure must be one of (`NO_ACCESS`, `READ_ONLY`, `1WRITER`, `1WRITER_SESSION`, `WM_ONLY`). Ensure that FreezeWorkspace is invoked with the correct parameters.

WM_ERROR_141 the parameter freezewriter can be non-null only for the 1WRITER mode
Cause: An attempt was made to invoke the FreezeWorkspace procedure with an invalid `freezewriter` parameter.

Action: The `freezewriter` parameter for the FreezeWorkspace procedure can be non-null only when the `freezemode` parameter is `1WRITER`. Ensure that FreezeWorkspace is invoked with the correct parameters.

WM_ERROR_142 the keep parameter must be one of ("PARENT","CHILD","BASE")
Cause: The ResolveConflicts procedure was called with an invalid `keep` parameter.

Action: Ensure that the `keep` parameter to the ResolveConflicts procedure is one of (`CHILD`,`PARENT`,`BASE`). This parameter is not case-sensitive. See the Resolving Conflicts section of the Workspace Manager documentation for details on the process of conflict resolution.

WM_ERROR_143 the "LIVE" workspace can only be rolled back to a savepoint
Cause: An attempt was made to rollback the entire `LIVE` workspace. Workspace Manager only supports the RollbackToSP operation for the `LIVE` workspace.

Action: Use RollbackToSP to achieve the desired result.

WM_ERROR_144 the "LIVE" workspace cannot be merged
Cause: A user attempted to invoke MergeWorkspace on the `LIVE` workspace.

Action: Workspace Manager disallows commit of the `LIVE` workspace. Do not invoke MergeWorkspace on the `LIVE` workspace.

WM_ERROR_145 the "LIVE" workspace cannot be removed
Cause: A user attempted to invoke RemoveWorkspace on the `LIVE` workspace.

Action: To rollback changes in the `LIVE` workspace, use the RollbackToSP operation. To remove descendants to the `LIVE` workspace, use the RemoveWorkspace operation on the child workspaces.

WM_ERROR_147 the "LIVE" workspace cannot be refreshed
Cause: A user attempted to invoke RefreshWorkspace on the `LIVE` workspace.

Action: Workspace Manager disallows the Refresh operation on the `LIVE` workspace. Do not invoke RefreshWorkspace on the `LIVE` workspace.

WM_ERROR_148 the lock mode is currently not set for this session
Cause: The user invoked a SetLockingOFF operation without having called SetLockingON earlier in the current session.

Action: A user can only execute SetLockingOff if the user had called SetLockingOn in the session. To see what the current lock mode is, use the GetLockMode function.

WM_ERROR_149 the lock mode must be one of ("C","D","E","S","VE","WE")
Cause: The user invoked a SetLockingON operation with an invalid `lockmode` parameter.

Action: Use a lock mode that Workspace Manager currently supports: `C`(carry-forward), `D` (disregard), `E` (exclusive), `S` (Shared), `VE` (version exclusive), or `WE` (workspace exclusive). For a discussion of the differences and similarities among these modes, see the Workspace Manager documentation.

WM_ERROR_150 the lock mode is already set for workspace: 'string'
Cause: An attempt was made to invoke the SetWorkspaceLockModeON operation for a workspace whose lock mode has already been set.

Action: To change the lock mode for a workspace, use the SetWorkspaceLockModeOFF procedure to first unset the lock mode.

WM_ERROR_151 the parent workspace 'string' is currently frozen in 'string'mode
Cause: An attempt was made to invoke a Workspace Manager operation that required the specified parent workspace to be unfrozen.

Action: Wait for the workspace to be unfrozen before invoking the Workspace Manager operation. The workspace can be unfrozen by the owner of the workspace, by a user with the `WM_ADMIN_ROLE`, or by a user with the `WM_ADMIN` system privilege using the UnfreezeWorkspace procedure.

WM_ERROR_152 the workspace 'string' is not a leaf workspace
Cause: A workspace wide operation was invoked on an intermediate workspace. Workspace Manager supports this operation only on leaf workspaces. A leaf workspace is one that does not have any descendants.

Action: Invoke the operation only on leaf workspaces.

WM_ERROR_153 the workspace: 'string' has savepoints in the branch specified
Cause: A CompressWorkspace or CompressWorkspaceTree operation resulted in this internal error.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_154 the workspaceLockMode for 'string' has been set to 'string' without override
Cause: An attempt was made to invoke the SetLockingON or the SetLockingOFF procedure while the current session was in a workspace whose lock mode was set without override.

Action: The lock mode can be changed by the current session only if the session is in a workspace whose lock mode has not been set or if the session is in a workspace whose lock mode has been set with the override option. Privileged users can change the lock mode for a workspace using the SetWorkspaceLockModeON and the SetWorkspaceLockModeOFF procedures.

WM_ERROR_155 the where-clause can involve only primary key columns
Cause: An attempt was made to invoke a Workspace Manager operation with an invalid `where_clause` parameter as input.

Action: Ensure that the input `where_clause` parameter contains only valid column names and has proper syntax. The `where_clause` parameter for this Workspace Manager operation can contain only columns that are part of the primary key.

WM_ERROR_156 there are active sessions using the workspace: 'string'
Cause: An attempt was made to invoke a Workspace Manager operation that required that there be no sessions in the specified workspace (or, in a multiparent workspace environment, in any non-root workspaces in the multiparent workspace graph).

Action: To successfully invoke the Workspace Manager operation on the specified workspace, ensure that there are no sessions in the workspace or workspaces involved. Privileged users can view all the sessions in a workspace using the DBA_WORKSPACE_SESSIONS view.

WM_ERROR_157 there are sessions on non-latest versions in the workspace: 'string'
Cause: An attempt was made to invoke CompressWorkspace with some sessions in the workspace being on non-`LATEST` savepoints in the workspace. CompressWorkspace requires that all sessions in the specified workspace be on the `LATEST` version of the workspace.

Action: All sessions in the specified workspace must either go to another workspace using GotoWorkspace or must go to the `LATEST` savepoint using GotoSavepoint. Privileged users can view all the sessions in a workspace using the DBA_WORKSPACE_USERS view.

WM_ERROR_158 this procedure cannot be invoked on the "LIVE" workspace
Cause: An attempt was made to invoke a Workspace Manager procedure on the `LIVE` workspace.

Action: Invoke this Workspace Manager procedure only on non-`LIVE` workspaces.

WM_ERROR_159 unable to exclusively lock table: 'string'.'string'
Cause: An attempt to version-disable a table failed due to the existence of database transaction locks on the table.

Action: To successfully version-disable this table, verify that there are no database transaction locks on the table.

WM_ERROR_160 unable to grant/revoke appropriate privileges
Cause: An attempt to version-disable a table failed due to an internal error in granting or revoking appropriate privileges on the table being version-enabled.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_161 unable to lock 'string': 'string' in 'string' mode
Cause: An attempt was made to invoke a Workspace Manager operation that failed because Workspace Manager was unable to acquire an exclusive lock on the specified resource.

Action: The specified resource may have been locked by some other database session performing a Workspace Manager operation. Wait for the lock on the resource to be released before proceeding with the Workspace Manager operation.

WM_ERROR_162 unlock operation requires ACCESS privilege on the workspace
Cause: The user attempted to invoke the UnlockRows operation on a workspace without `ACCESS` privileges on the workspace.

Action: The UnlockRows operation requires `ACCESS` privileges on the workspace. Invoke the UnlockRows operation only on workspaces that you have `ACCESS` privileges for.

WM_ERROR_163 use Commit/Rollback Resolve to unfreeze workspaces being conflict resolved
Cause: A user attempted to invoke UnfreezeWorkspace on a workspace undergoing conflict resolution. This workspace was frozen due to a user having issued a BeginResolve operation on it.

Action: To unfreeze the workspace, call the CommitResolve or a RollbackResolve procedure. Only a user with the `WM_ADMIN_ROLE` role or the `WM_ADMIN` system privilege, or the user who initiated the BeginResolve operation on the workspace, can issue a CommitResolve or RollbackResolve call for that workspace.

WM_ERROR_164 use the RemoveWorkspaceTree procedure to drop non-leaf workspaces
Cause: A user attempted to invoke RemoveWorkspace on an intermediate workspace. To prevent the occurrence of orphaned workspaces, RemoveWorkspace can only be invoked on leaf workspaces.

Action: Execute the RemoveWorkspaceTree procedure to remove the workspace and all its descendants.

WM_ERROR_165 use the force parameter to freeze a currently frozen workspace
Cause: An attempt was made to invoke the FreezeWorkspace procedure for a workspace that was already frozen.

Action: To freeze workspaces that are already frozen, use the FreezeWorkspace procedure with the `force` parameter.

WM_ERROR_166 only a BeginResolve invoker or a user with the "WM_ADMIN" system privilege can call CommitResolve
Cause: A user attempted to invoke CommitResolve without having initiated the BeginResolve operation earlier and without having the `WM_ADMIN` system privilege.

Action: CommitResolve can be invoked only by the user who initiated the BeginResolve operation or by a user who has the `WM_ADMIN` system privilege.

WM_ERROR_167 null lockMode parameter passed in
Cause: A user called a procedure that requires that the `lockMode` parameter have a non-null value.

Action: The user must pass in a non-null `lockmode` parameter for this operation to succeed.

WM_ERROR_168 Cannot disable workspace lockmode
Cause: An attempt was made to disable the workspace lock mode, but this is not supported.

Action: Do not attempt to turn off locking for this workspace.

WM_ERROR_169 "WM_ADMIN" system privilege or ownership is required to UnFreeze a workspace
Cause: UnfreezeWorkspace failed because only a user with the `WM_ADMIN_ROLE` role or `WM_ADMIN` system privilege or the owner of the workspace can unfreeze a frozen workspace.

Action: Ensure that the invoking user has the required privileges before attempting to unfreeze the workspace. Otherwise, have the owner of the workspace unfreeze it.

WM_ERROR_170 The row to be locked has already been versioned
Cause: LockRows failed because the row specified to be locked was already versioned.

Action: Do not attempt to lock rows that have already been versioned. Use the `where_clause` parameter of LockRows to specify those rows that have not already been versioned.

WM_ERROR_171 WM error: 'string'
Cause: A Workspace Manager error occurred.

Action: See the Workspace Manager documentation.

WM_ERROR_172 all version enabled tables have to be disabled before uninstalling
Cause: An attempt was made to uninstall Workspace Manager with existing version-enabled tables.

Action: Version-disable all version-enabled tables before attempting to uninstall Workspace Manager. Version-enabled tables can be disabled using the DisableVersioning procedure.

WM_ERROR_173 cannot create workspaces that are more than 30 levels deep
Cause: An attempt was made to create a workspace that is more than 30 levels in depth from the `LIVE` workspace.

Action: Do not create workspaces that are more than 30 levels in depth from the `LIVE` workspace.

WM_ERROR_174 table: 'string' contains columns with unsupported data types
Cause: An attempt was made to version-enable a table with one or more columns with an unsupported data type.

Action: Ensure that all the columns in the table being version-enabled are of supported data types. The currently unsupported data types for version-enabled tables are: LONG and LONG RAW.

WM_ERROR_175 cannot delete implicit savepoints with dependent child workspaces
Cause: An attempt was made to invoke the DeleteSavepoint procedure on an implicit savepoint with dependent child workspaces.

Action: Ensure that the savepoint being deleted is not implicit or it does not have any child workspaces created off of it. The xxx\_WORKSPACES views show the parent savepoints for all the workspaces in the system. Ensure that the savepoint being deleted is not a parent savepoint for some workspace.

WM_ERROR_176 A user-defined trigger defined on 'string'.'string' has compilation errors.
Cause: An attempt was made to version-enable a table that has a user-defined trigger with compilation errors defined on it.

Action: Ensure that all user-defined triggers on the table to be version-enabled have no compilation errors.

WM_ERROR_177 sum of length of all column names of 'string'.'string' exceeds 8250 characters
Cause: An attempt was made to version-enable a table where the sum of the column name lengths exceeded 8250 characters.

Action: Rename some of the table's columns to reduce the sum of the column name lengths.

WM_ERROR_178 user-defined trigger body defined on 'string'.'string' exceeds 28000 characters
Cause: An attempt was made to version-enable a table that has a user-defined trigger with a trigger body length of more than 28,000 characters defined on it.

Action: Ensure that all user-defined triggers on the table to be version-enabled have trigger body lengths that are less than 28,000 characters.

WM_ERROR_179 combination of column name sizes and user-defined trigger lengths too large
Cause: An attempt was made to version-enable a table where the length of all of the column names combined with the length of the largest trigger body defined on the table was too large.

Action: Reduce the length of the largest trigger body defined on this table, rename some of the table's columns to reduce the sum of the column name lengths, or do both.

WM_ERROR_180 table 'string'.'string' has too many primary key columns
Cause: An attempt was made to version-enable a table that has more than 31 primary key columns.

Action: Decrease the number of primary key columns on the table to 31, at most.

WM_ERROR_181 attempt to modify a WM generated trigger
Cause: An attempt to drop or re-create a database trigger failed because that trigger was created by Workspace Manager.

Action: Do not drop or re-create this trigger.

WM_ERROR_182 attempt to modify a WM generated view
Cause: An attempt to re-create a database view failed because it was associated with a version-enabled table.

Action: Do not re-create this view. The view will automatically be dropped when the table associated with it is version-disabled.

WM_ERROR_183 reserved column name found
Cause: An attempt to version-enable the table failed because it had a column whose name started with WM\$ or WM\_.

Action: Rename the column to a different name.

WM_ERROR_184 reserved index name found
Cause: An attempt to version-enable the table failed because it had an index on it with the index name being the name of the table (to version-enabled) with the prefix \_PKI\$ or \_TI\$.

Action: Re-create the index using a different name.

WM_ERROR_185 operation disallowed on workspace 'string' involved in a conflict resolution session
Cause: An attempt was made to execute an operation on a Workspace undergoing conflict resolution. A Workspace is under conflict resolution if BeginResolve method has been called on the workspace but CommitResolve or RollbackResolve has not been called yet.

Action: Wait for conflict resolution to either commit or rollback before trying the operation on the workspace.

WM_ERROR_186 the parameter freezewriter must be null when session_duration is true',
Cause: An attempt was made to invoke the FreezeWorkspace procedure with an invalid `freezewriter` parameter.

Action: The `freezewriter` parameter of the FreezeWorkspace procedure must be null whenever the `session_duration` parameter is TRUE. The `freezewriter` is implicitly assumed to be the currently connected session. Ensure that FreezeWorkspace is invoked with the correct parameters.

WM_ERROR_187 the parameter session_duration must be true for the 1WRITER_SESSION mod
Cause: An attempt was made to invoke the FreezeWorkspace procedure with an invalid `session_duration` parameter.

Action: The `session_duration` parameter of the FreezeWorkspace must be TRUE when attempting to freeze a workspace in 1WRITER_SESSION mode. Ensure that FreezeWorkspace is invoked with the correct parameters.

WM_ERROR_188 At least one table failed during lwDisableVersioning. Please query all_wm_vt_errors view to get the errors 'string'
Cause: If lightweight disable-versioning fails for some reason during the upgrade or downgrade.

Action: Contact Oracle Support Services with the upgrade or downgrade log.

WM_ERROR_189 workspaces, savepoints, or versioned tables cannot be present on the IMPORT platform
Cause: The instance you are importing Workspace Manager into has some savepoints, workspaces, or version-enabled tables.

Action: Clean up savepoints, workspaces and version-enabled tables, or reinstall Workspace Manager before importing other Workspace Manager data.

WM_ERROR_190 table 'string' is in mutating state, no structural operations can be performed
Cause: When a structural operation (for example, DisableVersioning) is in progress on a table, another structural operation (for example, BeginDDL) was invoked.

Action: Complete the ongoing operation before calling a new one.

WM_ERROR_191 LWDisableVersioning not called on the table 'string'
Cause: Internal error during the upgrade or downgrade.

Action: Contact Oracle Support Services with the upgrade or downgrade output log.

WM_ERROR_192 At least one table failed during temporary disable-versioning 'string'
Cause: Internal error during downgrade.

Action: Contact Oracle Support Services with downgrade output log.

WM_ERROR_194 At least one table failed during lwEnableVersioning. Please query all_wm_vt_errors view to get the errors 'string'
Cause: Lightweight enable-versioning failed for some reason during the upgrade or downgrade.

Action: Internal error: contact Oracle Support Services with the upgrade or downgrade output log.

WM_ERROR_195 Following tables with VIEW_WO_OVERWRITE failed during recreation of PRIMARY KEY constraint 'string'
Cause: The primary key constraint could not be re-created during the upgrade or downgrade.

Action: Internal error: contact Oracle Support Services with the upgrade or downgrade log.

WM_ERROR_196 'string' operation requires ''FREEZE_WORKSPACE'' privilege on the workspace or ''FREEZE_ANY_WORKSPACE'' or ''WM_ADMIN'' system privilege
Cause: Insufficient privilege for freezing or unfreezing a workspace.

Action: Grant `FREEZE_WORKSPACE` privilege on the workspace, or `FREEZE_ANY_WORKSPACE`, the `WM_ADMIN_ROLE` role, or the `WM_ADMIN` system privilege to the user trying the operation.

WM_ERROR_197 a ddl operation is being committed on 'string'
Cause: A DDL operation is in the process of being committed on the table.

Action: Wait until the DDL operation is complete and then retry the current operation.

WM_ERROR_198 primary key constraint of a version enabled table cannot be renamed
Cause: An attempt was made to rename the primary key constraint of the skeleton table associated with a version-enabled table.

Action: Rename the primary key constraint of the skeleton table to its original name and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_199 primary key columns cannot be added/dropped/modified/reordered for version enabled tables
Cause: An attempt was made to add, drop, modify, or reorder the primary key columns of the skeleton table associated with a version-enabled table.

Action: Restore the primary key columns to their original state and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_200 unsupported constraint 'string' detected
Cause: A check or unique constraint was detected on the skeleton table associated with a version-enabled table.

Action: Check or unique constraints cannot be defined on a version-enabled table. Remove the constraint from the skeleton table and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_201 creation of partitioned/join indexes on version enabled tables is not supported
Cause: A partitioned or join index was detected on the skeleton table associated with a version-enabled table.

Action: Drop all partitioned or join indexes on the skeleton table and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_202 index name 'string' is longer than 26 characters
Cause: An index name with more than 26 characters was detected on the skeleton table associated with a version-enabled table.

Action: Rename the index and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_203 enable/disable versioning or begin/commitDDL is being executed on 'string'
Cause: Versioning is being enabled or disabled, or BeginDDL or CommitDDL is being executed, on this table.

Action: Wait until the version-enabling, version-disabling, or BeginDDL or CommitDDL operation is complete, and then retry the current operation. The operation getting executed on the table can be found by querying the ALL_WM_VERSIONED_TABLES view.

WM_ERROR_204 beginDDL not called on 'string'
Cause: BeginDDL needs to executed on the table before the current operation can be performed.

Action: Call BeginDDL on the table and then perform the current operation again.

WM_ERROR_205 'string' contains data - cannot be modified
Cause: A column of the skeleton table associated with a version-enabled table was modified, and the versioned table contains non-null data in this column.

Action: Restore the column to its original state and call the [CommitDDL](DBMS_WM-reference.md) procedure again.

WM_ERROR_206 column reordering is not supported
Cause: Columns of the skeleton table associated with a version-enabled table were reordered.

Action: Restore the columns to their original state and call the [CommitDDL](DBMS_WM-reference.md) procedure again. Reordering of columns can be achieved by first dropping columns in a DDL session and then adding columns in a subsequent DDL session.

WM_ERROR_207 referential integrity constraint exists with a table not contained in the list of specified tables
Cause: A referential integrity constraint exists with a table not contained in the list of tables passed to the EnableVersioning or DisableVersioning procedure.

Action: Add the table to the list passed to enable or disable versioning. If you do not want to version-enable this table not contained in the list, you need to version-enable the tables one at a time.

WM_ERROR_208 cycle detected in referential integrity constraints on specified tables
Cause: A cycle exists in the referential integrity constraints between tables passed to enable or disable versioning or a new referential constraint added between two skeleton tables caused a cycle in the referential constraints.

Action: Drop one of the referential constraints in the cycle and implement it using user-defined triggers.

WM_ERROR_209 table 'string' has been modified in non-LIVE workspaces
Cause: DisableVersioning failed because the table had been modified in non-`LIVE` workspaces.

Action: Remove or merge all workspaces that have modified this table. Otherwise, use the `FORCE` option of DisableVersioning.

WM_ERROR_210 multi-level referential integrity constraint with cascade option detected
Cause: DisableVersioning failed because the table has a cascade referential constraint with a version-enabled child table that, in turn, is the parent table of another referential constraint.

Action: Version-disable the child and parent tables together.

WM_ERROR_211 DDL is being done on 'string'
Cause: A DDL session has already been started on the table.

Action: Wait until the previous DDL session has been committed or rolled back.

WM_ERROR_212 deferrable option not supported for integrity constraints
Cause: Deferrable option is not supported for referential integrity constraints defined on version-enabled tables.

Action: Re-create any referential constraints that have the deferrable option so that they do not have the deferrable option.

WM_ERROR_213 unsupported referential constraint with 'string' detected
Cause: The skeleton table associated with a version-enabled table has a referential constraint with a table that is not a skeleton table.

Action: Drop this referential constraint. You can only define referential constraints between two skeleton tables.

WM_ERROR_214 'string' has a cascade referential constraint with a non-version enabled table
Cause: A new referential integrity constraint was added between the skeleton tables of two version-enabled tables, but the parent table already had a cascading referential constraint with a table that is not version-enabled.

Action: Drop the new referential integrity constraint between the skeleton tables and perform the current operation again.

WM_ERROR_215 A savepoint cannot be created with the name "LATEST"
Cause: A savepoint cannot be named "LATEST".

Action: Choose another name for the savepoint.

WM_ERROR_220 Following tables failed during sentinel row adjustment 'string'
Cause: An error occurred when Workspace Manager was being migrated from one version to another.

Action: Examine the spool file to find the Oracle error that caused this error to occur. Correct the error and enter the following SQL statement while connected AS SYSDBA: `SQL> EXECUTE WMSYS.OWM_MIG_PKG.AllFixSentinelVersion;`

WM_ERROR_221 'string' could not be recovered from Migration Error: \['string'\]
Cause: An error occurred when Workspace Manager was being migrated from one version to another.

Action: The ALL_WM_VT_ERRORS view can be queried for more detailed information about the error. The RecoverMigratingTable or RecoverAllMigratingTables procedures can be used to recover one or more tables that were left in an inconsistent state.

WM_ERROR_222 Following tables could not be recovered from Migration Error: 'string'
Cause: An error occurred when Workspace Manager was being migrated from one version to another.

Action: The ALL_WM_VT_ERRORS view can be queried for more detailed information about the error. The RecoverMigratingTable or RecoverAllMigratingTables procedures can be used to recover one or more tables that were left in an inconsistent state.

WM_ERROR_223 "WM_ADMIN" system privilege is required to invoke this procedure
Cause: A Workspace Manager operation was invoked without the requisite privileges.

Action: The `WM_ADMIN` system privilege or `WM_ADMIN_ROLE` role is required to invoke this specific operation. Ensure that the current user has the required privileges to invoke this operation.

WM_ERROR_226 Nested Tables must have a primary key constraint
Cause: An attempt was made to execute EnableVersioning on a table that contained a nested table column that did not have a primary key.

Action: Add a primary key constraint to any nested table column contained in the table to be version-enabled.

WM_ERROR_228 this operation is not allowed for table 'string' with version state 'string'
Cause: An attempt was made to invoke a workspace operation on a table with a version state that is invalid.

Action: The table on which the operation was invoked has a version state that disallows the operation from being performed. Query the ALL_WM_VERSIONED_TABLES view to look up the version state for the specified table, and see the documentation for the ALL_WM_VERSIONED_TABLES view (in [ALL_WM_VERSIONED_TABLES](workspace-manager-views.md)) for a definition of the possible version state values.

WM_ERROR_229 statement 'string' failed during EnableVersioning. Error: string'
Cause: Version-enabling of the table failed due to some error. This may occur due to insufficient resources or some unexpected Oracle error.

Action: Retry the operation after fixing the cause of the error.

WM_ERROR_230 table 'string' failed during UndoEnableVersioning/DisableVersioning. Error: string'
Cause: If EnableVersioning fails for some reason, an attempt is made to bring back the table to original state. This error occurs when this undo attempt fails on the partially versioned tables.

Action: Check the ALL_WM_VT_ERRORS view to see the statement that failed and the error that occurred. After fixing the cause of the error, you can version-enable the table using [EnableVersioning](DBMS_WM-reference.md) or disable versioning on the table using [DisableVersioning](DBMS_WM-reference.md). (Be careful if you specify '`ignore_last_error => TRUE`' with DisableVersioning.)

WM_ERROR_231 table 'string' failed during DisableVersioning. Error: string'
Cause: DisableVersioning of the table failed due to some error. This may occur due to insufficient resources or some unexpected Oracle error.

Action: See the Usage Notes for the [DisableVersioning](DBMS_WM-reference.md) procedure for information about handling the error.

WM_ERROR_232 unique constraint 'string'.'string' violated'
Cause: The DML operation or workspace operation violated the unique constraint 'string'.'string' on a version-enabled table.

Action: Find the row that violates the constraint, and attempt the operation without the row.

WM_ERROR_233 deadlock detected when trying to acquire lock for 'string': 'string', session may have open database transactions'
Cause: The workspace operation with an `auto_commit` value of `TRUE` is invalid if the current session has an open database transaction on that workspace.

Action: Commit or roll back the current database transaction before invoking the procedure, or invoke the procedure with an `auto_commit` value of `FALSE`.

WM_ERROR_234 continually-refreshed workspaces may have only continually-refreshed workspaces as children
Cause: An attempt was made to create a workspace that is not continually refreshed as a child of a continually refreshed workspace

Action: Continually refreshed workspaces can have only continually refreshed workspaces as child workspaces.

WM_ERROR_235 invalid system parameter name or value
Cause: An invalid string was passed as a name or value for a parameter for GetSystemParameter or SetSystemParameter.

Action: Check the documentation for valid names and values of Workspace Manager system parameters.

WM_ERROR_236 system setting does not allow invocation of this procedure'
Cause: UnlockRows cannot be called if the Workspace Manager system parameter `NONCR_WORKSPACE_MODE` is set to `PESSIMISTIC_LOCKING`.

Action: If no data exists in workspaces that are not continually refreshed, you can set `NONCR_WORKSPACE_MODE` is set to `OPTIMISTIC_LOCKING`. To see the current Workspace Manager system parameter settings, use the WM_INSTALLATION metadata view.

WM_ERROR_237 integrity constraint ('string'.'string') violated in workspace 'string' or one of its descendants - child record found
Cause: An attempt was made to delete or update a record in a parent table of a referential integrity constraint with the RESTRICT option, and there was a matching record in the child table of the integrity constraint in the identified workspace or one of its continually refreshed descendant workspaces.

Action: Delete or roll back matching child table records first.

WM_ERROR_238 integrity constraint ('string'.'string') violated in workspace 'string' or one of its descendants - parent key not found
Cause: An attempt was made to insert or update a record in a child table of a referential integrity constraint, and there was no matching record in the parent table of the integrity constraint in the identified workspace or one its continually refreshed descendant workspaces.

Action: Insert a matching record in the parent table or roll back deleted matching parent table records first.

WM_ERROR_239 integrity constraint ('string'.'string') violated in a descendant workspace - parent key not found
Cause: An attempt was made to insert or update a record in a child table of a referential integrity constraint, and there was no matching record in the parent table of the integrity constraint in a continually refreshed descendant workspace of the current workspace.

Action: Insert a matching record in the parent table or roll back deleted matching parent table records first.

WM_ERROR_240 reserved character found in workspace name
Cause: The name of a workspace contains one or more of these characters: "/", "\*", ",", "\$", "#"

Action: Remove these characters or replace them with valid characters.

WM_ERROR_241 system parameter 'string' should be set to 'string' for multiparent functionality'
Cause: The Workspace Manager system parameter is not set correctly to allow multiparent workspaces.

Action: Check the documentation about Workspace Manager system parameters, and be sure that any values required for multiparent workspace support are set correctly.

WM_ERROR_242 'string' already in ancestor hierarchy of 'string'
Cause: The workspace that is being added as a parent workspace is already an ancestor of the (child) workspace.

Action: Ensure that a workspace is not already an ancestor of a workspace to which it is to be added as a parent workspace.

WM_ERROR_243 all workspaces under the root of multiparent graph must be same type'
Cause: In a multiparent workspace graph, all workspaces must be either continually refreshed or not continually refreshed.

Action: Ensure that the workspaces under the root of a multiparent graph are either all continually refreshed or all not continually refreshed. You can use the ChangeWorkspaceType procedure to change the workspace type between continually refreshed and not continually refreshed.

WM_ERROR_244 AddAsParentWorkspace operation requires ACCESS privilege on all nodes except root in the graph and CREATE privilege on the new parent workspace'
Cause: The user in the multiparent workspace environment does not have the specified privileges.

Action: Use the function GetPrivs to ensure that the user invoking this operation has the required privileges.

WM_ERROR_245 'string' is not multi-parent of 'string'
Cause: For a RemoveWorkspaceAsParent operation, the workspace to be removed was not previously added as a parent workspace.

Action: Ensure that you have specified the correct workspace.

WM_ERROR_246 'string' cannot be removed because data has been versioned from the workspace branch being removed
Cause: In a multiparent workspace environment, if data has been versioned in the multiparent leaf workspace from any of the workspaces that will be removed as ancestors by this operation, the operation is not allowed.

Action: Roll back the leaf workspace to remove the versioned data from the branch being removed.

WM_ERROR_247 the multi-parent graph formed by 'string' is not a leaf graph
Cause: In a multiparent workspace environment, there is a workspace that is a child of some non-root workspace of the multi-parent graph on which this operation was invoked.

Action: Remove all the workspaces that are children of non-root workspaces of the graph before performing this operation.

WM_ERROR_248 intermediate workspaces of a multiparent graph cannot be refreshed
Cause: In a multiparent workspace environment, only the leaf workspace of a multiparent graph can be refreshed.

Action: Ensure that you are refreshing the correct workspace.

WM_ERROR_249 primary key constraint violated for 'string.string'
Cause: In a multiparent workspace environment, the primary key constraint for the table is violated, as viewed from the leaf workspace of the multiparent graph.

Action: Delete or roll back one of the rows that is shown as a duplicate.

WM_ERROR_250 workspace name may not be "NULL"
Cause: An attempt was made to name a workspace "NULL".

Action: Choose another name for the workspace.

WM_ERROR_251 attempt to 'string' a row locked by 'string' in workspace 'string' in mode '"WE"
Cause: Only the user that locked the row in `WE` mode can further edit the row in the same workspace.

Action: The row cannot be edited by the current user until the locking user removes the lock on the row.

WM_ERROR_252 attempt to 'string' a row locked by 'string' in mode "VE"
Cause: Only the user who locked the row in `VE` mode can further edit the row.

Action: The row cannot be edited by the current user until the locking user removes the lock on the row.

WM_ERROR_253 lock_mode of only ''VE'' is allowed when workspace is "NONE"
Cause: A value of `NONE` for the `workspace` parameter is permitted only with `VE` as the value for `lock_mode`.

Action: Specify the name of an existing workspace when specifying a `lock_mode` value other than `VE`.

WM_ERROR_254 cannot 'string' because PESSIMISTIC_LOCKING is on and row is already versioned'
Cause: The DML operation cannot be executed because system parameter `CR_WORKSPACE_MODE` or `NONCR_WORKSPACE_MODE` is set to `PESSIMISTIC_LOCKING` and the DML operation violates the system setting.

Action: If data has not been versioned in non-`LIVE` workspaces, you can change the `PESSIMISTIC_LOCKING` setting to `OPTIMISTIC_LOCKING.` To see the current Workspace Manager system parameter settings, use the WM_INSTALLATION metadata view.

WM_ERROR_255 insufficient privileges \['string'\]
Cause: An attempt was made to invoke an import or export operation without the required privileges.

Action: Ensure that the user has the required privileges before invoking the operation. To import from or export to a staging table, the user must have privileges to select from and perform DML operations on the staging table.

WM_ERROR_256 'string' cannot be invoked with a null 'string' parameter
Cause: The specified parameter cannot be null.

Action: Reissue the operation using a non-null value for the specified parameter.

WM_ERROR_257 savepoint 'string' does not exist in 'string''s hierarchy
Cause: The ancestor savepoint for an import operation does not exist in the hierarchy of the workspace.

Action: Specify a savepoint that is contained in the workspace's hierarchy.

WM_ERROR_258 specified system where clause is invalid \['string''\]
Cause: An import or export operation was invoked with an invalid system `WHERE` clause.

Action: Ensure the compatibility of the system `WHERE` clause in conjunction with the parameters for the operation.

WM_ERROR_259 table 'string' is invalid \['string'\]
Cause: The staging table has been modified from its original state required for an import or export operation.

Action: Restore the staging table to its original state.

WM_ERROR_260 Export error \['string'\]
Cause: Unable to perform the export operation due to the specified error.

Action: Fix the error and retry the appropriate operation.

WM_ERROR_261 Import error \['string'\]
Cause: Unable to perform the import operation due to the specified error.

Action: Fix the error and retry the appropriate operation.

WM_ERROR_262 this parameter cannot be set to 'PESSIMISTIC_LOCKING' if data has been versioned in Non-LIVE workspaces'
Cause: This setting is not permitted if data exists in non-`LIVE` workspaces.

Action: If you want to use the PESSIMISTIC_LOCKING setting, ensure that there is no data versioned in non-`LIVE` workspaces for the workspace type (continually refreshed or not continually refreshed) for which the parameter is being set.

WM_ERROR_272 invalid event name: 'string'
Cause: An invalid Workspace Manager event name was passed as an argument to the function.

Action: Pass a valid event name. See the WM_EVENTS_INFO view for a list of all valid events.

WM_ERROR_273 set system parameter 'ALLOW_CAPTURE_EVENTS' to 'ON' for capturing events
Cause: An attempt was made to capture an event even though the Workspace Manager system parameter `ALLOW_CAPTURE_EVENTS` was set to `OFF`.

Action: Call SetSystemParameter to set `ALLOW_CAPTURE_EVENTS` to `ON`, and retry the operation.

WM_ERROR_274 this parameter cannot be set to 'OFF' when some events are set to be captured
Cause: An attempt was made to disallow the capture of Workspace Manager events while one or more types of events were set to be captured.

Action: Turn off event capture by calling `SetCaptureEvents('ALL_EVENTS','OFF')`, and retry the operation.

WM_ERROR_275 invalid value for capture - 'ON' or 'OFF' expected
Cause: The SetCaptureEvent procedure was called with an invalid value for the capture parameter.

Action: Specify either `ON` or `OFF` for the capture parameter.

WM_ERROR_276 this parameter cannot be set to 'OFF' when some multiparent workspaces exist
Cause: An attempt was made to set `ALLOW_MULTI_PARENT_WORKSPACES` to `OFF` when one or more multiparent workspaces existed in the system.

Action: Remove all multiparent workspaces by using any combination of the RemoveAsParentWorkspace, MergeWorkspace, and RemoveWorkspace procedures.

WM_ERROR_277 system parameter 'ALLOW_NESTED_TABLE_COLUMNS' cannot be set to 'OFF' when a version enabled table exists containing a nested table column
Cause: An attempt was made to set `ALLOW_NESTED_TABLE_COLUMNS` to `OFF` when one or more version-enabled tables contained a nested table column.

Action: Disable versioning on all tables that contain a nested table column.

WM_ERROR_278 'string' cannot be version enabled because system parameter 'ALLOW_NESTED_TABLE_COLUMNS' has been set to 'OFF'
Cause: An attempt was made to version-enable a table containing a nested table column and the Workspace Manager system parameter `ALLOW_NESTED_TABLE_COLUMNS` was set to `OFF`.

Action: Call DBMS_WM.SetSystemParameter to set `ALLOW_NESTED_TABLE_COLUMNS` to `ON`, and retry the operation.

WM_ERROR_279 histogram stats not found for table 'string.string' on column 'string'
Cause: Required histogram statistics have not been collected on the specified column.

Action: Use the DBMS_STATS.GATHER_TABLE_STATS procedure to collect the histogram statistics; then try the operation again.

WM_ERROR_280 datatype of column 'string' in table 'string.string' not supported for batch updates
Cause: The specified data type cannot be used for batches of `PRIMARY_KEY_RANGE`.

Action: Specify the batch size as `TABLE`.

WM_ERROR_281 batch_size parameter must be 'TABLE' or 'PRIMARY_KEY_RANGE'
Cause: The batch_size parameter value was invalid.

Action: Specify the `batch_size` parameter value as `TABLE` or `PRIMARY_KEY_RANGE`.

WM_ERROR_282 number of batches must be between 1 and 1000
Cause: The value specified for the Workspace Manager system parameter `NUMBER_OF_COMPRESS_BATCHES` was invalid.

Action: Specify a number from 1 to 1000 (inclusive).

WM_ERROR_283 invalid 'string' parameter specified
Cause: The value specified for the parameter was invalid.

Action: Specify a valid value for that parameter.

WM_ERROR_284 the length of the 'string' parameter cannot exceed 'string' characters
Cause: The value of a specified parameter exceeded the allowable length.

Action: Shorten the value to an allowable length.

WM_ERROR_285 the 'string' parameter must be set to 'string'
Cause: The value specified for the parameter was invalid.

Action: Set the parameter to the specified value.

WM_ERROR_286 quoted identifiers are not supported
Cause: A quoted identifier was used.

Action: Remove the quote from the table or dependent object and retry the operation.

WM_ERROR_287 the 'string' parameter must be specified
Cause: The specified parameter was omitted.

Action: Include the parameter when executing the operation.

WM_ERROR_288 'string' privilege(s) needed
Cause: The executing user did not have the specified privileges.

Action: Grant the necessary privilege or privileges to the user.

WM_ERROR_289 insufficient privileges on 'string'
Cause: The executing user did not have the necessary privileges on the object.

Action: Grant the necessary privilege or privileges on the object to the user.

WM_ERROR_290 only the table owner or a user with the "WM_ADMIN" system privilege can invoke this procedure
Cause: The procedure invoker had insufficient privileges.

Action: Either grant the `WM_ADMIN` system privilege or `WM_ADMIN_ROLE` role to the executing user, or execute the procedure as the owner of the table.

WM_ERROR_291 deadlock detected while trying to acquire lock on 'string'
Cause: A deadlock was encountered when acquiring a lock using the DBMS_LOCK package.

Action: Wait for the sessions that caused the deadlock to either roll back or commit their transactions.

WM_ERROR_292 error while trying to acquire lock on 'string', status='string'
Cause: A required lock could not be obtained when using the DBMS_LOCK package.

Action: The required action is dependent on the specified status: status=1: retry the operation; status=2: wait for the sessions that caused the deadlock to either roll back or commit their transactions; status=3 or status=5: contact Oracle Support Services to resolve the issue.

WM_ERROR_293 error while trying to release lock on 'string', status='string'
Cause: The required lock could not be released when using the DBMS_LOCK package.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_294 open short transaction exists on 'string'
Cause: An open transaction had a lock on the specified object.

Action: Commit or roll back any open transactions on the object.

WM_ERROR_295 the 'string' schema cannot contain dependent objects
Cause: The specified schema contained a dependent object when trying to version-enable a table.

Action: Drop the objects from the schema, and re-create them in a different schema.

WM_ERROR_296 topology 'string' does not exist
Cause: The specified topology did not exist.

Action: Specify the correct topology.

WM_ERROR_297 object 'string' already exists
Cause: A required object already exists.

Action: Drop the object.

WM_ERROR_298 object 'string' does not exist
Cause: The specified object did not exist.

Action: Create the necessary object if it does not exist; otherwise, check the spelling of the string.

WM_ERROR_299 tablespace 'string' does not exist
Cause: The specified tablespace did not exist.

Action: Execute the procedure with a valid tablespace name.

WM_ERROR_300 the 'string' workspace cannot be renamed
Cause: The specified workspace cannot be renamed.

Action: Do not attempt to rename the workspace.

WM_ERROR_301 workspace names cannot include the character 'string'
Cause: A workspace name contained the invalid specified character.

Action: Choose a different workspace name that does not contain the character.

WM_ERROR_302 the new name must be distinct from the old name
Cause: When renaming an object, the old name and the new name must be distinct.

Action: Choose a different new name for the object.

WM_ERROR_303 a workspace cannot be added as a parent workspace of itself
Cause: An attempt was made to add a workspace as a parent workspace of itself.

Action: Do not try to add a workspace as a parent of itself.

WM_ERROR_304 cannot add a parent workspace to LIVE
Cause: An attempt was made to add a workspace as a parent workspace of the `LIVE` workspace.

Action: Do not attempt to add a parent workspace to the `LIVE` workspace.

WM_ERROR_305 'string' cannot be called on a topology feature table
Cause: An invalid operation was attempted on a topology feature table.

Action: Do not execute the operation on the table.

WM_ERROR_306 MergeTable with remove_data on a parent table of a referential constraint is not supported for multi-parent workspacese
Cause: The MergeTable operation was executed on an unsupported table.

Action: Set the `remove_data` parameter to `false`, or do not execute the operation on the table for the specified workspace.

WM_ERROR_307 workspace 'string' has a crstatus that is not supported for this operation
Cause: The operation attempted to use a workspace that is not currently supported.

Action: Do not execute the operation for the specified workspace.

WM_ERROR_308 a 'string' with more than 'string' characters in its name was found - rename to a shorter name
Cause: The object's name exceeded the specified number of characters.

Action: Rename the object to have a shorter name.

WM_ERROR_309 some tables have already been version enabled with a different validtime option
Cause: An attempt was made to modify an topology feature table in an optimistic mode.

Action: Use the `validtime` parameter option that was originally specified.

WM_ERROR_310 a topology feature table can be modified only in pessimistic mode - set locking ON
Cause: An attempt was made to modify an topology feature table in an optimistic mode.

Action: Use a pessimistic setting when modifying this table.

WM_ERROR_311 feature tables cannot be deleted from this topology
Cause: An attempt was made to remove the last feature table from the topology.

Action: Do not remove the last feature table from a topology.

WM_ERROR_312 topology 'string' does not have a feature table
Cause: EnableVersioning was being executed on a topology without a feature table.

Action: Add a feature table to the topology.

WM_ERROR_313 the 'string' parameter is incompatible with the other options
Cause: The specified parameter was not compatible with the other parameters.

Action: Specify a valid value for the parameter. In the case of the PurgeTable procedure, do not specify non-null values for both the `instant` and `savepoint` parameters.

WM_ERROR_314 'string' is not a version-enabled topology
Cause: The topology specified has not been version-enabled.

Action: Only specify topologies that have been version-enabled.

WM_ERROR_315 this operation is not allowed during bulk loading
Cause: An unsupported operation was executed during bulk loading.

Action: Wait for the bulk loading of the workspace to complete before executing the operation.

WM_ERROR_316 wm_version column should not be specified when bulk loading
Cause: The `wm_version` column was specified in the control file.

Action: Remove the `wm_version` column.

WM_ERROR_317 cannot bulk load into a table with a self-referential integrity constraint
Cause: An attempt was made to bulk load into a table that contained a foreign key constraint that referenced a column in the same table.

Action: Either disable or remove the constraint from the table.

WM_ERROR_318 bulk loading into only the latest version of a workspace is supported
Cause: An attempt was made to bulk load into a version that is not supported.

Action: When bulk loading into the `LIVE` workspace, the `savepoint_name` parameter must be either '`LATEST`' or '`ROOT_VERSION`'. When bulk loading into any workspace other than `LIVE`, the `savepoint_name` parameter must be '`LATEST`'.

WM_ERROR_319 this operation is not supported while 'string' is in 'string' state
Cause: An operation was executed while the specified table was in an unsupported state.

Action: Revert the table to a supported state before retrying the operation.

WM_ERROR_320 Workspace Manager must first be uninstalled from CDB\$ROOT
Cause: An attempt was made to uninstall Workspace Manager from a PDB (pluggable database) before uninstalling it from the CDB\$ROOT.

Action: Uninstall Workspace Manager from CDB\$ROOT before the PDB.

WM_ERROR_321 nested tables cannot themselves contain a nested table
Cause: An attempt was made to version-enable a table that contained a nested table that also contained a nested table.

Action: Remove one of the nested table columns.

WM_ERROR_322 nested tables contained in objects are not supported
Cause: An attempt was made to version-enable a table that contained a column whose data type contained a nested table.

Action: Remove the nested table from the data type, or the column from the table.

WM_ERROR_323 system parameter 'string' must be set to 'string'
Cause: An operation was executed that required a system parameter to match a specific value.

Action: Modify the system parameter to the appropriate value.

WM_ERROR_324 the following index tables were unable to be DisableVersioned: 'string'
Cause: During a downgrade operation, there were errors when attempting to disable version the specified index table.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_325 the following index tables were unable to be EnableVersioned: 'string'
Cause: During an upgrade operation, there were errors when attempting to version-enable the specified index table.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_326 null value not allowed for a primary key column
Cause: A DML operation resulted in the primary key value being set to null.

Action: Do not use null values for primary key values.

WM_ERROR_327 the child table 'string' contains a record outside the specified valid time range
Cause: A constraint violation occurred as a result of adding the `validtime` option to a parent table in a foreign key relationship.

Action: Set the `validtime` range to encompass all child table rows.

WM_ERROR_328 all child tables must be valid-time enabled
Cause: An attempt was made to add the `validtime` option to a table that is the parent table in a foreign key constraint, without first adding the option to all child tables.

Action: Add the `validtime` option to the necessary child tables.

WM_ERROR_329 this index operation is not currently supported while 'string' is version enabled
Cause: An attempt was made to perform an unsupported DDL operation on an index due to the table being version-enabled

Action: Avoid issuing the DDL statement directly on the index. Use CommitDDL.

WM_ERROR_330 multi-transaction update not supported for a clustered table - specify 'UNLIMITED' undo space
Cause: An invalid `undo_space` parameter value was specified for a clustered table.

Action: Set the `undo_space` parameter to '`UNLIMITED`'.

WM_ERROR_331 object tables cannot be version enabled
Cause: An attempt was made to version-enable an object table.

Action: Do not execute EnableVersioning on an object table.

WM_ERROR_332 One of the rows in the lineage to be removed has a createtime greater than the specified instant
Cause: The PurgeTable procedure was unable to complete due to existing data.

Action: Specify an instant that is greater than all rows that are going to be purged.

WM_ERROR_333 teferential constraints on object attributes not supported
Cause: An attempt was made to version-enable a table that contained a referential integrity constraint on an object attribute.

Action: Drop the constraint before version-enabling the table.

WM_ERROR_334 savepoint names cannot include the character 'string'
Cause: A savepoint name contained the invalid specified character.

Action: Choose a different savepoint name that does not contain the character.

WM_ERROR_335 this operation is not currently supported while 'string' is version enabled
Cause: An unsupported DDL statement was executed while the table is version-enabled.

Action: Avoid issuing the DDL statement directly on the object. Use CommitDDL.

WM_ERROR_336 the index 'string' cannot be renamed
Cause: An attempt was made to rename an index that cannot be renamed.

Action: Do not rename the specified index.

WM_ERROR_337 this table can only be dropped by dbms_wm.rollbackDDL/commitDDL
Cause: An attempt was made to drop the skeleton table created by the BeginDDL procedure.

Action: Execute RollbackDDL or CommitDDL.

WM_ERROR_338 skeleton tables used by beginDDL/commitDDL cannot be version enabled
Cause: An attempt was made to version-enable the skeleton table created by the BeginDDL procedure.

Action: Do not execute the EnableVersioning procedure on this table.

WM_ERROR_339 this table is not available for queries and DML operations
Cause: An attempt as made to issue a DML statement on a table that is currently unavailable.

Action: Wait for the operation that caused the table to become unavailable to complete.

WM_ERROR_340 this table is used by Workspace Manager for referential integrity checking
Cause: An attempt was made to drop a table required by Workspace Manager for referential integrity checking.

Action: Do not attempt to drop the table.

WM_ERROR_341 check constraint 'string' violated
Cause: When executing CommitDDL, a check constraint was violated.

Action: Disable the constraint or remove the data that is violating the constraint.

WM_ERROR_342 trigger creation on this object is not supported
Cause: An attempt was made to create a trigger directly on the base table used by Workspace Manager.

Action: Avoid creating the trigger directly on the base table. Use CommitDDL.

WM_ERROR_343 types contained in versioned tables cannot be dropped
Cause: An attempt was made to drop a type required by a version-enabled table.

Action: Version-disable the table before dropping the type.

WM_ERROR_344 unable to create \_LCK table
Cause: An index necessary for the creation on the \_LCK table was unable to be created due to an existing object.

Action: Rename the index preventing the creation of the \_LCK table.

WM_ERROR_345 unable to support unique index due to naming conflict
Cause: An attempt was made to version-enable a table containing an index name that has a naming conflict.

Action: Rename the necessary index.

WM_ERROR_346 insufficient privileges to revoke 'string'
Cause: An attempt was made to invoke the RevokeWorkspacePriv or RevokeSystemPriv procedure without the required privileges to do so.

Action: Ensure that the invoking user has the required privileges to revoke the privilege. A user needs to have been granted a privilege with the GRANT option to be able to revoke it from others.

WM_ERROR_347 the object definition exceeds the maximum allowed length
Cause: The search_condition for a check constraints exceeded the supported length.

Action: Redefine the constraint to use a shorter constraint definition.

WM_ERROR_348 constraint 'string' exists on another table
Cause: A foreign key constraint was unable to be created due to the existence of another constraint with the same name.

Action: Choose a new name for the constraint.

WM_ERROR_349 constraint enforcement on existing versioned data not supported in the presence of multi-parent workspaces
Cause: Enforcement of a foreign key constraint was not possible due to the presence of a multiparent workspace.

Action: Drop or disable the constraint, or set the `enforce_ric` parameter to `false`.

WM_ERROR_350 hint cannot contain 'string'
Cause: An unsupported hint was specified when executing the AdduserDefinedHint procedure.

Action: Do not include the specified string within the hint.

WM_ERROR_351 implicit savepoints cannot be renamed
Cause: An attempt was made to rename an implicit savepoint.

Action: Do not rename an implicit savepoint.

WM_ERROR_352 'string' not granted to 'string'
Cause: An attempt was made to revoke privileges from a user that did not have them.

Action: Only revoke privileges from a user that has already had the privileges granted to them.

WM_ERROR_353 instant can be specified only for a table with history option
Cause: The `instant` parameter was not null for a table that did not have the `history` option.

Action: Set the `instant` parameter to be null.

WM_ERROR_354 only LATEST data is currently supported
Cause: An attempt was made to import or export non-LATEST data.

Action: Ensure the compatibility of the parameters specified for the operation.

WM_ERROR_355 overlapping periods found for column wm_valid of table 'string'
Cause: When version-enabling a table with `validtime`, a constraint violation was found within the table.

Action: Make sure that the primary key is unique for all time periods.

WM_ERROR_356 referential constraint 'string' exists with another parent table
Cause: A foreign key constraint was unable to be created due to the existence of another constraint with the same name.

Action: Choose a new name for the constraint.

WM_ERROR_357 referential constraint with a non-primary-key constraint 'string' detected
Cause: A referential integrity constraint was found within the table that referenced a column that was not part of the primary key.

Action: Disable the constraints or only include primary key columns.

WM_ERROR_359 incompatible options specified
Cause: Options were specified that are incompatible with each other.

Action: Remove one of the incompatible options.

WM_ERROR_360 this release only supports changing to the workspace type: DBMS_WM.CR_WORKSPACE_TYPE
Cause: An attempt was made to change a workspace into a non-continually refreshed workspace.

Action: Do not attempt to modify continually refreshed workspaces with the ChangeWorkspaceType procedure.

WM_ERROR_361 unable to import this table
Cause: An attempt was made to import a table that required unsupported operations.

Action: Do not specify either the `ancestor_savepoint_workspace` or `ancestor_savepoint_name` parameters when importing this table.

WM_ERROR_362 unsupported options specified while multi-parent workspaces exist
Cause: The parameters specified for the PurgeTable procedure are not supported when a multiparent workspace exists.

Action: When a multiparent workspace exists, the following parameters must be set when executing Purgetable: `workspace=>'LIVE'`, `PurgeAfter=>true`, `savepoint_name=>null`, `instant=>null`.

WM_ERROR_363 unable to create workspace with the same name as a workspace whose removal has been deferred
Cause: A workspace was removed using by specifying either 'FAST' or 'REMOVE_LOCKS' for the defer_option parameter. Until the workspace has been completely cleaned up, a new workspace with the same name cannot be created.

Action: Execute dbms_wm.RemoveDeferredWorkspaces before creating the workspace.

WM_ERROR_364 'string' not supported on a table with valid time
Cause: The operation was not supported for table with the `validtime` option.

Action: Do not execute the operation on a table that has the `validtime` option enabled.

WM_ERROR_365 'string' and 'string' have an identical column name
Cause: A nested table had a column with the same name as a column that is contained in its parent table.

Action: Rename either the column in the nested table or the column in the parent table.

WM_ERROR_366 'string' is already version enabled with valid time option
Cause: An attempt was made to add the validtime option to a table that already has the option enabled.

Action: Do not use the `ADD_VALID_TIME` option of alterVersionedTable for a version-enabled table that already has the `validtime` option enabled.

WM_ERROR_367 invalid active date for DML
Cause: An invalid time was specified when modifying a table.

Action: Contact Oracle Support Services to resolve the issue.

WM_ERROR_368 a referential integrity constraint will be violated between 'string' and 'string' in the workspace 'string' or one of its descendants - child record found
Cause: The operation could not be completed due to a constraint violation of a foreign key constraint in the specified workspace (or one of its descendants).

Action: Fix the constraint violation before executing the operation.

WM_ERROR_369 a referential integrity constraint will be violated between 'string' and 'string' in the workspace 'string' or one of its descendants - parent key not found
Cause: The operation could not be completed due to a constraint violation of a foreign key constraint in the specified workspace (or one of its descendants).

Action: Fix the constraint violation before executing the operation.

WM_ERROR_370 invalid values contained in the wm_valid column
Cause: When executing EnableVersioning, a row with an invalid `wm_valid` column was found.

Action: Fix all rows containing the `wm_valid` column so that the `validfrom` column is non-null and the `validtill` column is not less than the `validfrom` column.

WM_ERROR_371 privileges on 'string' policy must be granted using dbms_wm.grantPrivsOnPolicy
Cause: A table with an OLS policy was being version-enabled before executing the grantPrivsOnPolicy procedure for the table.

Action: Execute the grantPrivsOnPolicy procedure on the table before executing EnableVersioning.

WM_ERROR_372 Workspace Manager is not properly installed
Cause: An import operation was being performed with an invalid installation of Workspace Manager.

Action: Make sure that Workspace Manager is in a valid state before importing the data.

WM_ERROR_373 unsupported version of Workspace manager detected
Cause: An import operation was being performed with an incompatible version of Workspace Manager installed.

Action: Install a compatible version of Workspace Manager before importing the data.

WM_ERROR_374 Datapump job did not successfully complete
Cause: An error was encountered during the Oracle Data Pump job.

Action: See the Data Pump log files for more details on the error.

WM_ERROR_375 invalid datapump job specified
Cause: The specified Oracle Data Pump job could not be used for the operation due to incompatible options.

Action: Check the options specified when executing the dbms_datapump.open procedure.

WM_ERROR_376 the 'string' schema does not contain the necessary data
Cause: The schema contained in the dump file did not contain the necessary data to complete the import_schemas procedure.

Action: Only use dump files that have been generated by the export_schemas procedure.

WM_ERROR_377 Export and Import operations cannot be run simultaneously
Cause: An attempt was made to run simultaneous export and import operations.

Action: Only execute the export_schemas and import_schemas procedures so that they do not overlap.

WM_ERROR_378 Removing a workspace that was a parent of a workspace whose removal has been referred is not supported
Cause:An attempt was made to remove a workspace that has a child workspace that had its removal deferred.

Action:Execute the dbms_wm.RemoveDeferredWorkspaces procedure to finish the removal of the child workspace before removing its parent, or defer the removal of the parent workspace as well.

WM_ERROR_379 a workspace with a 'string' lockmode cannot be merged or refreshed
Cause: An attempt was made to merge or refresh a workspace with the specified lockmode.

Action: Do not attempt to merge or refresh this workspace with that lockmode.

WM_ERROR_380 the 'string' lockmode cannot be set for a continually refreshed workspace or the 'LIVE' workspace
Cause: An attempt was made to set the lockmode of a continually refreshed workspace or the 'LIVE' workspace to an unsupported mode.

Action: Do not set the lockmode of this workspace to an unsupported mode. Instead, specify one that is supported ('`E`', '`S`', '`VE`', '`WE`').

WM_ERROR_381 all child workspaces must have their lockmodes set to 'D'
Cause: An attempt was made to set the lockmode of the specified workspace to 'D', even though a child workspace of the specified workspace had a different lockmode.

Action: For any workspace with the lockmode set to 'D', all child workspaces must also have the same lockmode. So, either update the lockmode of all of the child workspaces of the specified workspace to 'D' before changing the lockmode of the specified workspace, or use a different lockmode for this workspace.

WM_ERROR_382 range partitioning is not supported for version enabled tables
Cause: An attempt was made to version-enable a table that uses range partitioning.

Action: Either do not attempt to version-enable this table, or use a different partitioning scheme.

WM_ERROR_383 Workspace Manager must first be uninstalled from each PDB prior to uninstalling from CDB\$ROOT
Cause: An attempt was made to uninstall Workspace Manager from CDB\$ROOT while it still exists in one or more PDBs.

Action: If Workspace Manager needs to be uninstalled, be sure to uninstall it in each PDB before attempting to uninstall it from CDB\$ROOT.

WM_ERROR_384 This operation cannot be executed while the DEFAULT_WORKSPACE system parameter is set to 'string'
Cause:An attempt was made to modify the workspace defined by the DEFAULT_WORKSPACE system parameter in an unsupported manner.

Action: Either change the DEFAULT_WORKSPACE system parameter to a different workspace, or avoid executing the procedure on this workspace.

WM_ERROR_385 The workspace 'string' must have the ACCESS_WORKSPACE privilege granted to PUBLIC
Cause: An attempt was made to change the DEFAULT_WORKSPACE system parameter to a workspace that lacked access by PUBLIC..

Action:Grant the ACCESS_WORKSPACE privilege to PUBLIC for the specified workspace, or choose a different workspace to be the default.

WM_ERROR_386 Invisible columns are not supported
Cause: An attempt was made to version-enable a table that contained an invisible column.

Action: Either drop the invisible column from the table, or do not attempt to version-enable the table.

WM_ERROR_387 This procedure has been deprecated
Cause:This procedure is no longer supported in this version of Workspace Manager.

Action:Do not use this procedure.

WM_ERROR_388 Column value has been improperly modified within a user-defined trigger
Cause: Either a primary key column value was being updated by a user-defined trigger in an unsupported manner, or a :NEW value was being modified in a delete trigger.

Action: Avoid doing such modifications, either by updating the trigger definition or by executing dbms_wm.SetTriggerEvents to specify when the trigger is executed.

WM_ERROR_389 Only identity columns defined as ''always'' or ''by default on null'' are supported
Cause: An attempt was made to version-enable a table that contained an identity column that was not one of the listed types. (For example, it might have been a “generated always” identity column, which is not supported for version-enabling.)

Action: Either change the type of identity column, or do not attempt to version-enable the table.

WM_ERROR_390 Redaction policies are not currently supported for version-enabled tables
Cause: An attempt was made to version-enable a table that has a redaction policy defined on it.

Action:Remove the redaction policy from the table, or do not attempt to version-enable the table.

WM_ERROR_391 The isTopology parameter is required for the 'string' table
Cause: Either enableversioning or disableversioning was executed on a table that is part of a topology.

Action:Set the `table_name` parameter to the name of the topology and the isTopology parameter to `true` in order to include this table.

WM_ERROR_392 A virtual column that is part of the primary key cannot reference non-primary key columns
Cause: EnableVersioning failed due to a virtual column that is included in the primary key and references unsupported columns.

Action:Either redefine the virtual column or remove the column as part of the primary key prior to executing EnableVersioning.

WM_ERROR_393 A virtual column that is part of the primary key cannot reference non-primary key columns
Cause: The LIVE workspace cannot be the source or target workspace Cause: When executing CopyWorkspace, either the source workspace or the target workspace parameters was set to the 'LIVE' workspace .

Action:Choose a different workspace.

WM_ERROR_394 Virtual column expression cannot be modified because a constraint is defined on the column
Cause: A DDL operation attempted to modify the virtual column expression of a column that has a referential integrity constraint defined on it.

Action:Remove the constraint or do not modify the virtual column expression.

WM_ERROR_395 Deferrable constraints are not supported
Cause:EnableVersioning or a DDL operation was executed on a table containing a deferrable constraint.

Action:Redefine the constraint so that it is no longer deferrable.

WM_ERROR_396 Deferrable constraints are not supported
Cause:When executing CopyWorkspace, both the source workspace and the target workspace parameters were specified to be the same workspace.

Action:Specify distinct workspaces for the source and target of a CopyWorkspace operation.
