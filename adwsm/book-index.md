Symbols  A  B  C  D  E  F  G  H  I  J  L  M  N  O  P  R  S  T  U  V  W  

------------------------------------------------------------------------

## Symbols

- \_LT tables
  - created for Workspace Manager infrastructure [1.1.11](introduction-to-workspace-manager.md)
  - getting name of [4.35](DBMS_WM-reference.md)

------------------------------------------------------------------------

## A

- Add_Topo_Geometry_Layer procedure [4.1](DBMS_WM-reference.md)
- AddAsParentWorkspace procedure [4.2](DBMS_WM-reference.md)
- AddUserDefinedHint procedure [4.3](DBMS_WM-reference.md)
- Advanced Queuing
  - and Workspace Manager events [2](workspace-manager-events.md)
- ALL_MP_GRAPH_WORKSPACES view [5.1](workspace-manager-views.md)
- ALL_MP_PARENT_WORKSPACES view [5.2](workspace-manager-views.md)
- ALL_REMOVED_WORKSPACES view [5.3](workspace-manager-views.md)
- ALL_VERSION_HVIEW view [5.4](workspace-manager-views.md)
- ALL_WM_CONS_COLUMNS view [5.5](workspace-manager-views.md)
- ALL_WM_CONSTRAINT_VIOLATIONS view [5.6](workspace-manager-views.md)
- ALL_WM_CONSTRAINTS view [5.7](workspace-manager-views.md)
- ALL_WM_IND_COLUMNS view [5.8](workspace-manager-views.md)
- ALL_WM_IND_EXPRESSIONS view [5.9](workspace-manager-views.md)
- ALL_WM_LOCKED_TABLES view [5.10](workspace-manager-views.md)
- ALL_WM_MODIFIED_TABLES view [5.11](workspace-manager-views.md)
- ALL_WM_POLICIES view [5.12](workspace-manager-views.md)
- ALL_WM_RIC_INFO view [5.13](workspace-manager-views.md)
- ALL_WM_TAB_TRIGGERS view [5.14](workspace-manager-views.md)
- ALL_WM_VERSIONED_TABLES view [5.15](workspace-manager-views.md)
- ALL_WM_VT_ERRORS view [5.16](workspace-manager-views.md)
- ALL_WORKSPACE_PRIVS view [5.17](workspace-manager-views.md)
- ALL_WORKSPACE_SAVEPOINTS view [5.18](workspace-manager-views.md)
- ALL_WORKSPACES view [5.19](workspace-manager-views.md)
- ALLOW_CAPTURE_EVENTS system parameter [2.3](workspace-manager-events.md)
- altering
  - savepoint description [4.4](DBMS_WM-reference.md)
  - version-enabled table to add valid time support [4.5](DBMS_WM-reference.md)
  - workspace description [4.6](DBMS_WM-reference.md)
- AlterSavepoint procedure [4.4](DBMS_WM-reference.md)
- AlterVersionedTable procedure [4.5](DBMS_WM-reference.md)
- AlterWorkspace procedure [4.6](DBMS_WM-reference.md)
- asynchronous notification for Workspace Manager events [2.4.5](workspace-manager-events.md)
- auditing modifications
  - EnableVersioning history option [4.23](DBMS_WM-reference.md)
  - history views (xxx_HIST) [5.53](workspace-manager-views.md)
- auto_commit parameter [1.1.8](introduction-to-workspace-manager.md)
- autocommitting of operations [1.1.8](introduction-to-workspace-manager.md)

------------------------------------------------------------------------

## B

- base row [1.1.4](introduction-to-workspace-manager.md)
- BeginBulkLoading procedure [4.7](DBMS_WM-reference.md)
- BeginDDL procedure [4.8](DBMS_WM-reference.md)
- BeginResolve procedure [4.9](DBMS_WM-reference.md)
- bulk loading [1.7](introduction-to-workspace-manager.md)
  - BeginBulkLoading procedure [4.7](DBMS_WM-reference.md)
  - CommitBulkLoading procedure [4.11](DBMS_WM-reference.md)
  - RollbackBulkLoading procedure [4.76](DBMS_WM-reference.md)

------------------------------------------------------------------------

## C

- ChangeWorkspaceType procedure [4.10](DBMS_WM-reference.md)
- child row [1.1.4](introduction-to-workspace-manager.md)
- child workspace [1.1.1](introduction-to-workspace-manager.md)
  - as alternative to creating savepoint [1.1.2.1](introduction-to-workspace-manager.md)
  - merging [4.57](DBMS_WM-reference.md)
  - refreshing [4.63](DBMS_WM-reference.md), [4.64](DBMS_WM-reference.md)
  - removing [4.69](DBMS_WM-reference.md)
- CommitBulkLoading procedure [4.11](DBMS_WM-reference.md)
- CommitDDL procedure [4.12](DBMS_WM-reference.md)
- CommitResolve procedure [4.13](DBMS_WM-reference.md)
- compressing
  - workspaces [4.14](DBMS_WM-reference.md), [4.15](DBMS_WM-reference.md)
- compression (Workspace Manager)
  - SetCompressWorkspace procedure [4.83](DBMS_WM-reference.md)
  - WM_COMPRESS_BATCH_SIZES view [5.47](workspace-manager-views.md)
  - WM_COMPRESSIBLE_TABLES view [5.48](workspace-manager-views.md)
- CompressWorkspace procedure [4.14](DBMS_WM-reference.md)
- CompressWorkspaceTree procedure [4.15](DBMS_WM-reference.md)
- conflict management [1.16.6](introduction-to-workspace-manager.md), [4.72](DBMS_WM-reference.md)
  - beginning resolution [4.9](DBMS_WM-reference.md)
  - committing resolution [4.13](DBMS_WM-reference.md)
  - rolling back resolution [4.78](DBMS_WM-reference.md)
  - showing conflicts [4.84](DBMS_WM-reference.md)
- conflict resolution
  - example [5.51](workspace-manager-views.md)
- conflict views (xxx_CONF) [5.51](workspace-manager-views.md)
- constraints
  - maximum name length for Workspace Manager [1.1.11](introduction-to-workspace-manager.md)
  - support with Workspace Manager [1.9](introduction-to-workspace-manager.md)
- context (session) [1.2](introduction-to-workspace-manager.md)
  - GetSessionInfo function [4.37](DBMS_WM-reference.md)
- context of current operation
  - getting [4.33](DBMS_WM-reference.md)
- continually refreshed workspaces [1.1.9](introduction-to-workspace-manager.md)
  - changing workspace type [4.10](DBMS_WM-reference.md)
  - creating [4.19](DBMS_WM-reference.md)
- CopyForUpdate procedure [4.16](DBMS_WM-reference.md)
- copying
  - workspace [4.17](DBMS_WM-reference.md)
- CopyWorkspace procedure [4.17](DBMS_WM-reference.md)
- CreateSavepoint procedure [4.18](DBMS_WM-reference.md)
- CreateWorkspace procedure [4.19](DBMS_WM-reference.md)
- creating
  - savepoints [4.18](DBMS_WM-reference.md)
  - workspaces [4.19](DBMS_WM-reference.md)

------------------------------------------------------------------------

## D

- DBA_REMOVED_WORKSPACES view [5.20](workspace-manager-views.md)
- DBA_WM_SYS_PRIVS view [5.21](workspace-manager-views.md)
- DBA_WM_VERSIONED_TABLES view [5.22](workspace-manager-views.md)
- DBA_WM_VT_ERRORS view [5.23](workspace-manager-views.md)
- DBA_WORKSPACE_PRIVS view [5.24](workspace-manager-views.md)
- DBA_WORKSPACE_SAVEPOINTS view [5.25](workspace-manager-views.md)
- DBA_WORKSPACE_SESSIONS view [5.26](workspace-manager-views.md)
- DBA_WORKSPACES view [5.27](workspace-manager-views.md)
- DBMS_WM package [1.1.13](introduction-to-workspace-manager.md)
  - Add_Topo_Geometry_Layer [4.1](DBMS_WM-reference.md)
  - AddAsParentWorkspace [4.2](DBMS_WM-reference.md)
  - AddUserDefinedHint [4.3](DBMS_WM-reference.md)
  - AlterSavepoint [4.4](DBMS_WM-reference.md)
  - AlterVersionedTable [4.5](DBMS_WM-reference.md)
  - AlterWorkspace [4.6](DBMS_WM-reference.md)
  - BeginBulkLoading [4.7](DBMS_WM-reference.md)
  - BeginDDL [4.8](DBMS_WM-reference.md)
  - BeginResolve [4.9](DBMS_WM-reference.md)
  - ChangeWorkspaceType [4.10](DBMS_WM-reference.md)
  - CommitBulkLoading [4.11](DBMS_WM-reference.md)
  - CommitDDL [4.12](DBMS_WM-reference.md)
  - CommitResolve [4.13](DBMS_WM-reference.md)
  - CompressWorkspace [4.14](DBMS_WM-reference.md)
  - CompressWorkspaceTree [4.15](DBMS_WM-reference.md)
  - CopyForUpdate [4.16](DBMS_WM-reference.md)
  - CopyWorkspace [4.17](DBMS_WM-reference.md)
  - CreateSavepoint [4.18](DBMS_WM-reference.md)
  - CreateWorkspace [4.19](DBMS_WM-reference.md)
  - Delete_Topo_Geometry_Layer [4.20](DBMS_WM-reference.md)
  - DeleteSavepoint [4.21](DBMS_WM-reference.md)
  - DisableVersioning [4.22](DBMS_WM-reference.md)
  - EnableVersioning [4.23](DBMS_WM-reference.md)
  - Export [4.24](DBMS_WM-reference.md)
  - Export_Schemas [4.25](DBMS_WM-reference.md)
  - FindRICSet [4.26](DBMS_WM-reference.md)
  - FreezeWorkspace [4.27](DBMS_WM-reference.md)
  - GetBulkLoadVersion [4.28](DBMS_WM-reference.md)
  - GetConflictWorkspace [4.29](DBMS_WM-reference.md)
  - GetDiffVersions [4.30](DBMS_WM-reference.md)
  - GetLockMode [4.31](DBMS_WM-reference.md)
  - GetMultiWorkspaces [4.32](DBMS_WM-reference.md)
  - GetOpContext [4.33](DBMS_WM-reference.md)
  - GetOriginalDDL [4.34](DBMS_WM-reference.md)
  - GetPhysicalTableName [4.35](DBMS_WM-reference.md)
  - GetPrivs [4.36](DBMS_WM-reference.md)
  - GetSessionInfo [4.37](DBMS_WM-reference.md)
  - GetSystemParameter [4.38](DBMS_WM-reference.md)
  - GetValidFrom [4.39](DBMS_WM-reference.md)
  - GetValidTill [4.40](DBMS_WM-reference.md)
  - GetVersion [4.41](DBMS_WM-reference.md)
  - GetWMMetadataSpace [4.42](DBMS_WM-reference.md)
  - GetWorkspace [4.43](DBMS_WM-reference.md)
  - GotoDate [4.44](DBMS_WM-reference.md)
  - GotoSavepoint [4.45](DBMS_WM-reference.md)
  - GotoWorkspace [4.46](DBMS_WM-reference.md)
  - GrantGraphPriv [4.47](DBMS_WM-reference.md)
  - GrantPrivsOnPolicy [4.48](DBMS_WM-reference.md)
  - GrantSystemPriv [4.49](DBMS_WM-reference.md)
  - GrantWorkspacePriv [4.50](DBMS_WM-reference.md)
  - Import [4.51](DBMS_WM-reference.md)
  - Import_Schemas [4.52](DBMS_WM-reference.md)
  - Initialize_After_Import [4.53](DBMS_WM-reference.md)
  - IsWorkspaceOccupied [4.54](DBMS_WM-reference.md)
  - LockRows [4.55](DBMS_WM-reference.md)
  - MergeTable [4.56](DBMS_WM-reference.md)
  - MergeWorkspace [4.57](DBMS_WM-reference.md)
  - Move_Proc [4.58](DBMS_WM-reference.md)
  - PurgeTable [4.59](DBMS_WM-reference.md)
  - RecoverAllMigratingTables [4.60](DBMS_WM-reference.md)
  - RecoverFromDroppedUser [4.61](DBMS_WM-reference.md)
  - RecoverMigratingTable [4.62](DBMS_WM-reference.md)
  - RefreshTable [4.63](DBMS_WM-reference.md)
  - RefreshWorkspace [4.64](DBMS_WM-reference.md)
  - RemoveAsParentWorkspace [4.65](DBMS_WM-reference.md)
  - RemoveDeferredWorkspaces [4.66](DBMS_WM-reference.md)
  - RemoveUserDefinedHint [4.67](DBMS_WM-reference.md)
  - RemoveWorkspace [4.68](DBMS_WM-reference.md)
  - RemoveWorkspaceTree [4.69](DBMS_WM-reference.md)
  - RenameSavepoint [4.70](DBMS_WM-reference.md)
  - RenameWorkspace [4.71](DBMS_WM-reference.md)
  - ResolveConflicts [4.72](DBMS_WM-reference.md)
  - RevokeGraphPriv [4.73](DBMS_WM-reference.md)
  - RevokeSystemPriv [4.74](DBMS_WM-reference.md)
  - RevokeWorkspacePriv [4.75](DBMS_WM-reference.md)
  - RollbackBulkLoading [4.76](DBMS_WM-reference.md)
  - RollbackDDL [4.77](DBMS_WM-reference.md)
  - RollbackResolve [4.78](DBMS_WM-reference.md)
  - RollbackTable [4.79](DBMS_WM-reference.md)
  - RollbackToSP [4.80](DBMS_WM-reference.md)
  - RollbackWorkspace [4.81](DBMS_WM-reference.md)
  - SetCaptureEvent [4.82](DBMS_WM-reference.md)
  - SetCompressWorkspace [4.83](DBMS_WM-reference.md)
  - SetConflictWorkspace [4.84](DBMS_WM-reference.md)
  - SetDiffVersions [4.85](DBMS_WM-reference.md)
  - SetLockingOFF [4.86](DBMS_WM-reference.md)
  - SetLockingON [4.87](DBMS_WM-reference.md)
  - SetMultiWorkspaces [4.88](DBMS_WM-reference.md)
  - SetSystemParameter [4.89](DBMS_WM-reference.md)
  - SetTriggerEvents [4.90](DBMS_WM-reference.md)
  - SetValidTime [4.91](DBMS_WM-reference.md)
  - SetValidTimeFilterOFF [4.92](DBMS_WM-reference.md)
  - SetValidTimeFilterON [4.93](DBMS_WM-reference.md)
  - SetWMValidUpdateModeOFF [4.94](DBMS_WM-reference.md)
  - SetWMValidUpdateModeON [4.95](DBMS_WM-reference.md)
  - SetWoOverwriteOFF [4.96](DBMS_WM-reference.md)
  - SetWoOverwriteON [4.97](DBMS_WM-reference.md)
  - SetWorkspaceLockModeOFF [4.98](DBMS_WM-reference.md)
  - SetWorkspaceLockModeON [4.99](DBMS_WM-reference.md)
  - UnfreezeWorkspace [4.100](DBMS_WM-reference.md)
  - UnlockRows [4.101](DBMS_WM-reference.md)
  - UseDefaultValuesForNulls [4.102](DBMS_WM-reference.md)
- DDL (data definition language) operations
  - requirements and restrictions [1.8](introduction-to-workspace-manager.md)
- Delete_Topo_Geometry_Layer procedure [4.20](DBMS_WM-reference.md)
- DeleteSavepoint procedure [4.21](DBMS_WM-reference.md)
- deleting
  - deferred workspace [4.66](DBMS_WM-reference.md)
  - savepoints [4.21](DBMS_WM-reference.md)
  - workspace [1.1.6](introduction-to-workspace-manager.md), [4.68](DBMS_WM-reference.md)
- difference views (xxx_DIFF) [5.52](workspace-manager-views.md)
- DisableVersioning procedure [4.22](DBMS_WM-reference.md)
- disabling
  - workspace changes [4.27](DBMS_WM-reference.md)

------------------------------------------------------------------------

## E

- effective dating
  - See: valid time support
- EnableVersioning procedure [4.23](DBMS_WM-reference.md)
- event parameters [2.2](workspace-manager-events.md)
- events (Workspace Manager) [2](workspace-manager-events.md)
  - ALLOW_CAPTURE_EVENTS system parameter [2.3](workspace-manager-events.md)
  - asynchronous notification [2.4.5](workspace-manager-events.md)
  - capturing [4.82](DBMS_WM-reference.md)
  - event parameters [2.2](workspace-manager-events.md)
  - listening for [2.4.4](workspace-manager-events.md)
  - list of events [2.1](workspace-manager-events.md)
  - WM_EVENTS_INFO view [5.49](workspace-manager-views.md)
- example
  - conflict resolution [5.51](workspace-manager-views.md)
  - using Workspace Manager (Oracle sample schemas) [1.17.2](introduction-to-workspace-manager.md)
- exclusive locks [1.3](introduction-to-workspace-manager.md), [4.87](DBMS_WM-reference.md)
- explicit savepoints [1.1.2](introduction-to-workspace-manager.md)
- Export_Schemas procedure [4.25](DBMS_WM-reference.md)
- export considerations [1.6](introduction-to-workspace-manager.md)
- Export procedure [4.24](DBMS_WM-reference.md)

------------------------------------------------------------------------

## F

- FindRICSet procedure [4.26](DBMS_WM-reference.md)
- foreign keys with version-enabled tables [1.9.1](introduction-to-workspace-manager.md)
- FreezeWorkspace procedure [4.27](DBMS_WM-reference.md)
- freezing
  - workspace changes [1.1.5](introduction-to-workspace-manager.md), [4.27](DBMS_WM-reference.md)

------------------------------------------------------------------------

## G

- GetBulkLoadVersion function [4.28](DBMS_WM-reference.md)
- GetConflictWorkspace function [4.29](DBMS_WM-reference.md)
- GetDiffVersions function [4.30](DBMS_WM-reference.md)
- GetLockMode function [4.31](DBMS_WM-reference.md)
- GetMultiWorkspaces function [4.32](DBMS_WM-reference.md)
- GetOpContext function [4.33](DBMS_WM-reference.md)
- GetOriginalDDL procedure [4.34](DBMS_WM-reference.md)
- GetPhysicalTableName function [4.35](DBMS_WM-reference.md)
- GetPrivs function [4.36](DBMS_WM-reference.md)
- GetSessionInfo procedure [4.37](DBMS_WM-reference.md)
- GetSystemParameter function [4.38](DBMS_WM-reference.md)
- GetValidFrom function [4.39](DBMS_WM-reference.md)
- GetValidTill function [4.40](DBMS_WM-reference.md)
- GetVersion function [4.41](DBMS_WM-reference.md)
- GetWMMetadataSpace function [4.42](DBMS_WM-reference.md)
- GetWorkspace function [4.43](DBMS_WM-reference.md)
- GotoDate procedure [4.44](DBMS_WM-reference.md)
- GotoSavepoint procedure [4.45](DBMS_WM-reference.md)
- GotoWorkspace procedure [4.46](DBMS_WM-reference.md)
- GrantGraphPriv procedure [4.47](DBMS_WM-reference.md)
- granting
  - Workspace Manager privileges
    - multiparent graph workspaces [4.47](DBMS_WM-reference.md)
    - OLS-related [4.48](DBMS_WM-reference.md)
    - system [4.49](DBMS_WM-reference.md)
    - workspace [4.50](DBMS_WM-reference.md)
- grant option [1.4](introduction-to-workspace-manager.md)
- GrantPrivsOnPolicy procedure [4.48](DBMS_WM-reference.md)
- GrantSystemPriv procedure [4.49](DBMS_WM-reference.md)
- GrantWorkspacePriv procedure [4.50](DBMS_WM-reference.md)

------------------------------------------------------------------------

## H

- hierarchy
  - removing [4.69](DBMS_WM-reference.md)
  - workspaces [1.1.1](introduction-to-workspace-manager.md)
- historical data [1.1.12](introduction-to-workspace-manager.md)
- history option
  - EnableVersioning procedure [4.23](DBMS_WM-reference.md)
- history views (xxx_HIST) [5.53](workspace-manager-views.md)

------------------------------------------------------------------------

## I

- implicit savepoints [1.1.2](introduction-to-workspace-manager.md)
- Import_Schemas procedure [4.52](DBMS_WM-reference.md)
- import considerations [1.6](introduction-to-workspace-manager.md)
- Import procedure [4.51](DBMS_WM-reference.md)
- infrastructure for version-enabling of tables [1.1.11](introduction-to-workspace-manager.md)
- Initialize_After_Import procedure [4.53](DBMS_WM-reference.md)
- invisible index
  - supported on version-enabled table [1.8](introduction-to-workspace-manager.md)
- IsWorkspaceOccupied function [4.54](DBMS_WM-reference.md)

------------------------------------------------------------------------

## J

- join index
  - cannot be created or dropped on version-enabled table [1.8](introduction-to-workspace-manager.md)

------------------------------------------------------------------------

## L

- LATEST savepoint [1.1.2](introduction-to-workspace-manager.md)
- length of object names
  - maximums for Workspace Manager [1.1.11](introduction-to-workspace-manager.md)
- LOB columns with versioned tables [4.16](DBMS_WM-reference.md)
- locking table rows [4.55](DBMS_WM-reference.md)
- lock management [1.3](introduction-to-workspace-manager.md), [1.16.5](introduction-to-workspace-manager.md)
  - with DML operations on tables with referential integrity constraints [1.9.1.1](introduction-to-workspace-manager.md)
- lock mode
  - getting [4.31](DBMS_WM-reference.md)
- LockRows procedure [4.55](DBMS_WM-reference.md)
- locks
  - disabling [4.86](DBMS_WM-reference.md)
  - enabling [4.87](DBMS_WM-reference.md)
  - exclusive [1.3](introduction-to-workspace-manager.md)
  - shared [1.3](introduction-to-workspace-manager.md)
  - version-exclusive [1.3](introduction-to-workspace-manager.md)
  - workspace-exclusive [1.3](introduction-to-workspace-manager.md)
- lock views (xxx_LOCK) [5.54](workspace-manager-views.md)
- logging of modifications
  - EnableVersioning history option [4.23](DBMS_WM-reference.md)
  - history views (xxx_HIST) [5.53](workspace-manager-views.md)
- long transactions [1](introduction-to-workspace-manager.md)
- LT tables
  - created for Workspace Manager infrastructure [1.1.11](introduction-to-workspace-manager.md)
  - getting name of \_LT (physical) table [4.35](DBMS_WM-reference.md)

------------------------------------------------------------------------

## M

- materialized views
  - version management with [1.13](introduction-to-workspace-manager.md)
- MergeTable procedure [4.56](DBMS_WM-reference.md)
- MergeWorkspace procedure [4.57](DBMS_WM-reference.md)
- merging
  - table changes [4.56](DBMS_WM-reference.md)
  - workspaces [1.1.3](introduction-to-workspace-manager.md), [4.57](DBMS_WM-reference.md)
- metadata space
  - getting [4.42](DBMS_WM-reference.md)
- Move_Proc procedure [4.58](DBMS_WM-reference.md)
- multilevel referential integrity constraints [1.9.1](introduction-to-workspace-manager.md)
- multiparent workspaces [1.1.10](introduction-to-workspace-manager.md)
- multiworkspace views (xxx_MW) [5.55](workspace-manager-views.md)

------------------------------------------------------------------------

## N

- name length of database objects
  - maximums for Workspace Manager [1.1.11](introduction-to-workspace-manager.md)
- nonsequenced update operations [3.6.2.1](valid-time-support.md)
- null values
  - using default values for [4.102](DBMS_WM-reference.md)

------------------------------------------------------------------------

## O

- OE.WAREHOUSES table
  - Workspace Manager example [1.17.2](introduction-to-workspace-manager.md)
- OLS (Oracle Label Security)
  - DDL operations on version-enabled tables [1.8](introduction-to-workspace-manager.md)
  - granting privileges related to [4.48](DBMS_WM-reference.md)
- operation context
  - getting [4.33](DBMS_WM-reference.md)
- operators for valid time support [3.5](valid-time-support.md)
  - WM_CONTAINS [3.5.1](valid-time-support.md)
  - WM_EQUALS [3.5.2](valid-time-support.md)
  - WM_GREATERTHAN [3.5.3](valid-time-support.md)
  - WM_INTERSECTION [3.5.4](valid-time-support.md)
  - WM_LDIFF [3.5.5](valid-time-support.md)
  - WM_LESSTHAN [3.5.6](valid-time-support.md)
  - WM_MEETS [3.5.7](valid-time-support.md)
  - WM_OVERLAPS [3.5.8](valid-time-support.md)
  - WM_RDIFF [3.5.9](valid-time-support.md)
- Oracle Label Security (OLS)
  - DDL operations on version-enabled tables [1.8](introduction-to-workspace-manager.md)
  - granting privileges related to [4.48](DBMS_WM-reference.md)
- Oracle sample schemas
  - Workspace Manager example [1.17.2](introduction-to-workspace-manager.md)
- OWM_VERSION
  - Workspace Manager version number [5.50](workspace-manager-views.md)

------------------------------------------------------------------------

## P

- parent row [1.1.4](introduction-to-workspace-manager.md)
- parent workspace [1.1.1](introduction-to-workspace-manager.md)
  - conflicts with [4.84](DBMS_WM-reference.md)
- partitioned index
  - cannot be created or dropped on version-enabled table [1.8](introduction-to-workspace-manager.md)
- physical table name
  - and Workspace Manager infrastructure [1.1.11](introduction-to-workspace-manager.md)
  - getting [4.35](DBMS_WM-reference.md)
- privilege management [1.16.4](introduction-to-workspace-manager.md)
- privileges
  - description [1.4](introduction-to-workspace-manager.md)
  - getting [4.36](DBMS_WM-reference.md)
  - granted to PUBLIC user group [1.1.13](introduction-to-workspace-manager.md)
  - granting [4.49](DBMS_WM-reference.md), [4.50](DBMS_WM-reference.md)
    - multiparent graph workspaces [4.47](DBMS_WM-reference.md)
    - OLS-related [4.48](DBMS_WM-reference.md)
  - grant option [1.4](introduction-to-workspace-manager.md)
  - managing [1.4](introduction-to-workspace-manager.md)
  - revoking [1.4](introduction-to-workspace-manager.md), [4.74](DBMS_WM-reference.md), [4.75](DBMS_WM-reference.md)
    - multiparent graph workspaces [4.73](DBMS_WM-reference.md)
  - viewing users having Workspace Manager system-level privileges [5.21](workspace-manager-views.md)
- PurgeTable procedure [4.59](DBMS_WM-reference.md)

------------------------------------------------------------------------

## R

- RecoverAllMigratingTables procedure [4.60](DBMS_WM-reference.md)
- RecoverFromDroppedUser procedure [4.61](DBMS_WM-reference.md)
- RecoverMigratingTable procedure [4.62](DBMS_WM-reference.md)
- referential integrity constraints
  - finding affected tables [4.26](DBMS_WM-reference.md)
  - lock management with DML operations [1.9.1.1](introduction-to-workspace-manager.md)
- referential integrity support [1.9.1](introduction-to-workspace-manager.md)
  - multilevel constraints [1.9.1](introduction-to-workspace-manager.md)
- refreshing
  - tables [4.63](DBMS_WM-reference.md)
  - workspaces [4.64](DBMS_WM-reference.md)
- RefreshTable procedure [4.63](DBMS_WM-reference.md)
- RefreshWorkspace procedure [4.64](DBMS_WM-reference.md)
- removable savepoints [1.1.2](introduction-to-workspace-manager.md)
- RemoveAsParentWorkspace procedure [4.65](DBMS_WM-reference.md)
- RemoveDeferredWorkspaces procedure [4.66](DBMS_WM-reference.md)
- RemoveUserDefinedHint procedure [4.67](DBMS_WM-reference.md)
- RemoveWorkspace procedure [4.68](DBMS_WM-reference.md)
- RemoveWorkspaceTree procedure [4.69](DBMS_WM-reference.md)
- removing deferred workspaces [4.66](DBMS_WM-reference.md)
- removing workspaces [1.1.6](introduction-to-workspace-manager.md), [4.68](DBMS_WM-reference.md)
- RenameSavepoint procedure [4.70](DBMS_WM-reference.md)
- RenameWorkspace procedure [4.71](DBMS_WM-reference.md)
- renaming
  - savepoint [4.70](DBMS_WM-reference.md)
  - workspace [4.71](DBMS_WM-reference.md)
- reserved words and characters with Workspace Manager [1.15](introduction-to-workspace-manager.md)
- ResolveConflicts procedure [4.72](DBMS_WM-reference.md)
- resolving conflicts [4.72](DBMS_WM-reference.md)
  - beginning [4.9](DBMS_WM-reference.md)
  - committing [4.13](DBMS_WM-reference.md)
  - rolling back [4.78](DBMS_WM-reference.md)
- RETURNING clause
  - not supported for INSERT or UPDATE on version-enabled tables [1.1.11](introduction-to-workspace-manager.md)
- reverse index
  - supported on version-enabled table [1.8](introduction-to-workspace-manager.md)
- RevokeGraphPriv procedure [4.73](DBMS_WM-reference.md)
- RevokeSystemPriv procedure [4.74](DBMS_WM-reference.md)
- RevokeWorkspacePriv procedure [4.75](DBMS_WM-reference.md)
- revoking privileges [1.4](introduction-to-workspace-manager.md), [4.74](DBMS_WM-reference.md), [4.75](DBMS_WM-reference.md)
  - multiparent graph workspaces [4.73](DBMS_WM-reference.md)
- ROLE_WM_PRIVS view [5.28](workspace-manager-views.md)
- RollbackBulkLoading procedure [4.76](DBMS_WM-reference.md)
- RollbackDDL procedure [4.77](DBMS_WM-reference.md)
- RollbackResolve procedure [4.78](DBMS_WM-reference.md)
- RollbackTable procedure [4.79](DBMS_WM-reference.md)
- RollbackToSP procedure [4.80](DBMS_WM-reference.md)
- RollbackWorkspace procedure [4.81](DBMS_WM-reference.md)
- rolling back
  - changes in a table [4.79](DBMS_WM-reference.md)
  - workspace changes [1.1.3](introduction-to-workspace-manager.md), [4.81](DBMS_WM-reference.md)
  - workspaces to savepoint [4.80](DBMS_WM-reference.md)
- row-level security (VPD)
  - Workspace Manager considerations [1.11](introduction-to-workspace-manager.md)
- rows
  - locking [4.55](DBMS_WM-reference.md)
  - unlocking [4.101](DBMS_WM-reference.md)
- row versions
  - creation of [1.1.12](introduction-to-workspace-manager.md)
- rule-based subscription for Workspace Manager events [2.4.3](workspace-manager-events.md)

------------------------------------------------------------------------

## S

- sample schemas
  - Workspace Manager example [1.17.2](introduction-to-workspace-manager.md)
- savepoint management [1.16.3](introduction-to-workspace-manager.md)
- savepoints [1.1](introduction-to-workspace-manager.md)
  - altering description of [4.4](DBMS_WM-reference.md)
  - as alternative to creating child workspaces [1.1.2.1](introduction-to-workspace-manager.md)
  - creating [4.18](DBMS_WM-reference.md)
  - deleting [4.21](DBMS_WM-reference.md)
  - explicit [1.1.2](introduction-to-workspace-manager.md)
  - going to [4.45](DBMS_WM-reference.md)
  - implicit [1.1.2](introduction-to-workspace-manager.md)
  - removable [1.1.2](introduction-to-workspace-manager.md)
  - renaming [4.70](DBMS_WM-reference.md)
  - rolling back to [4.80](DBMS_WM-reference.md)
- sequenced delete operations [3.6.2.1](valid-time-support.md)
  - disabling [4.94](DBMS_WM-reference.md)
  - enabling [4.95](DBMS_WM-reference.md)
- sequenced update operations [3.6.2.1](valid-time-support.md)
  - disabling [4.94](DBMS_WM-reference.md)
  - enabling [4.95](DBMS_WM-reference.md)
- session context [1.2](introduction-to-workspace-manager.md)
  - GetSessionInfo function [4.37](DBMS_WM-reference.md)
- SetCaptureEvent procedure [4.82](DBMS_WM-reference.md)
- SetCompressWorkspace procedure [4.83](DBMS_WM-reference.md)
- SetConflictWorkspace procedure [4.84](DBMS_WM-reference.md)
- SetDiffVersions procedure [4.85](DBMS_WM-reference.md)
- SetLockingOFF procedure [4.86](DBMS_WM-reference.md)
- SetLockingON procedure [4.87](DBMS_WM-reference.md)
- SetMultiWorkspaces procedure [4.88](DBMS_WM-reference.md)
- SET NULL constraints
  - not supported for version-enabled tables [1.9.3](introduction-to-workspace-manager.md)
- SetSystemParameter procedure [4.89](DBMS_WM-reference.md)
- SetTriggerEvents procedure [4.90](DBMS_WM-reference.md)
- SetValidTimeFilterOFF procedure [4.92](DBMS_WM-reference.md)
- SetValidTimeFilterON procedure [4.93](DBMS_WM-reference.md)
- SetValidTime procedure [4.91](DBMS_WM-reference.md)
- SetWMValidUpdateModeOFF procedure [4.94](DBMS_WM-reference.md)
- SetWMValidUpdateModeON procedure [4.95](DBMS_WM-reference.md)
- SetWoOverwriteOFF procedure [4.96](DBMS_WM-reference.md)
- SetWoOverwriteON procedure [4.97](DBMS_WM-reference.md)
- SetWorkspaceLockModeOFF procedure [4.98](DBMS_WM-reference.md)
- SetWorkspaceLockModeON procedure [4.99](DBMS_WM-reference.md)
- shared locks [1.3](introduction-to-workspace-manager.md), [4.87](DBMS_WM-reference.md)
- skeleton tables [1.8](introduction-to-workspace-manager.md)
- spatial topologies
  - version management with [1.14](introduction-to-workspace-manager.md)
- subscription (rule-based) for Workspace Manager events [2.4.3](workspace-manager-events.md)
- synonyms
  - support for [1.12](introduction-to-workspace-manager.md)
- system parameters
  - for Workspace Manager [1.5](introduction-to-workspace-manager.md)
  - shown in WM_INSTALLATION view [5.50](workspace-manager-views.md)
- system privileges [4.49](DBMS_WM-reference.md)
  - viewing users having Workspace Manager system-level privileges [5.21](workspace-manager-views.md)

------------------------------------------------------------------------

## T

- table management [1.16.1](introduction-to-workspace-manager.md)
- table name
  - and Workspace Manager infrastructure [1.1.11](introduction-to-workspace-manager.md)
  - getting physical table name [4.35](DBMS_WM-reference.md)
  - maximum length for Workspace Manager [1.1.11](introduction-to-workspace-manager.md)
- table synonyms [1.12](introduction-to-workspace-manager.md)
- topologies
  - version management with [1.14](introduction-to-workspace-manager.md)
- topology geometry layer
  - adding [4.1](DBMS_WM-reference.md)
  - deleting [4.20](DBMS_WM-reference.md)
- trigger events
  - setting [4.90](DBMS_WM-reference.md)
- triggers on version-enabled tables [1.10](introduction-to-workspace-manager.md)

------------------------------------------------------------------------

## U

- UnfreezeWorkspace procedure [4.100](DBMS_WM-reference.md)
- unfreezing
  - workspaces [1.1.5](introduction-to-workspace-manager.md), [4.100](DBMS_WM-reference.md)
- unique constraints
  - support with Workspace Manager [1.9.2](introduction-to-workspace-manager.md)
- unlocking
  - table rows [4.101](DBMS_WM-reference.md)
- UnlockRows procedure [4.101](DBMS_WM-reference.md)
- UseDefaultValuesForNulls procedure [4.102](DBMS_WM-reference.md)
- USER_MP_GRAPH_WORKSPACES view [5.29](workspace-manager-views.md)
- USER_MP_PARENT_WORKSPACES view [5.30](workspace-manager-views.md)
- USER_REMOVED_WORKSPACES view [5.31](workspace-manager-views.md)
- USER_WM_CONS_COLUMNS view [5.32](workspace-manager-views.md)
- USER_WM_CONSTRAINTS view [5.33](workspace-manager-views.md)
- USER_WM_IND_COLUMNS view [5.34](workspace-manager-views.md)
- USER_WM_IND_EXPRESSIONS view [5.35](workspace-manager-views.md)
- USER_WM_LOCKED_TABLES view [5.36](workspace-manager-views.md)
- USER_WM_MODIFIED_TABLES view [5.37](workspace-manager-views.md)
- USER_WM_POLICIES view [5.38](workspace-manager-views.md)
- USER_WM_PRIVS view [5.39](workspace-manager-views.md)
- USER_WM_RIC_INFO view [5.40](workspace-manager-views.md)
- USER_WM_TAB_TRIGGERS view [5.41](workspace-manager-views.md)
- USER_WM_VERSIONED_TABLES view [5.42](workspace-manager-views.md)
- USER_WM_VT_ERRORS view [5.43](workspace-manager-views.md)
- USER_WORKSPACE_PRIVS view [5.44](workspace-manager-views.md)
- USER_WORKSPACE_SAVEPOINTS view [5.45](workspace-manager-views.md)
- USER_WORKSPACES view [5.46](workspace-manager-views.md)
- user-defined hints
  - adding [4.3](DBMS_WM-reference.md)
  - removing [4.67](DBMS_WM-reference.md)

------------------------------------------------------------------------

## V

- valid time filter
  - removing [4.92](DBMS_WM-reference.md)
  - setting [4.93](DBMS_WM-reference.md)
- valid time support [3](valid-time-support.md)
  - altering version-enabled table to add valid time support [4.5](DBMS_WM-reference.md)
  - operators [3.5](valid-time-support.md)
  - setting valid time for session [4.91](DBMS_WM-reference.md)
- version-enabled tables
  - definition [1.1](introduction-to-workspace-manager.md)
  - maximum name length for Workspace Manager [1.1.11](introduction-to-workspace-manager.md)
- version-exclusive locks [1.3](introduction-to-workspace-manager.md)
- versioning
  - disabling [4.22](DBMS_WM-reference.md)
  - enabling [4.23](DBMS_WM-reference.md)
  - infrastructure created for [1.1.11](introduction-to-workspace-manager.md)
- version number
  - Workspace Manager (OWM_VERSION) [5.50](workspace-manager-views.md)
- VIEW_WO_OVERWRITE mode
  - disabling [4.96](DBMS_WM-reference.md)
  - enabling [4.97](DBMS_WM-reference.md)
- virtual private databases
  - with Workspace Manager [1.11](introduction-to-workspace-manager.md)
- VPD (virtual private database)
  - with Workspace Manager [1.11](introduction-to-workspace-manager.md)

------------------------------------------------------------------------

## W

- WM_ADMIN_ROLE role [1.4](introduction-to-workspace-manager.md)
- WM_COMPRESS_BATCH_SIZES view [5.47](workspace-manager-views.md)
- WM_COMPRESSIBLE_TABLES view [5.48](workspace-manager-views.md)
- WM_CONTAINS operator [3.5.1](valid-time-support.md)
- WM_EQUALS operator [3.5.2](valid-time-support.md)
- WM_EVENTS_INFO view [5.49](workspace-manager-views.md)
- WM_GREATERTHAN operator [3.5.3](valid-time-support.md)
- WM_INSTALLATION view [5.50](workspace-manager-views.md)
- WM_INTERSECTION operator [3.5.4](valid-time-support.md)
- WM_LDIFF operator [3.5.5](valid-time-support.md)
- WM_LESSTHAN operator [3.5.6](valid-time-support.md)
- WM_MEETS operator [3.5.7](valid-time-support.md)
- WM_OVERLAPS operator [3.5.8](valid-time-support.md)
- WM_RDIFF operator [3.5.9](valid-time-support.md)
- WMSYS schema and user [1.1.13](introduction-to-workspace-manager.md)
- workspace-exclusive locks [1.3](introduction-to-workspace-manager.md)
- workspace lock mode
  - disabling [4.98](DBMS_WM-reference.md)
  - enabling [4.99](DBMS_WM-reference.md)
- Workspace Manager metadata space
  - getting [4.42](DBMS_WM-reference.md)
- Workspace Manager version
  - getting [4.41](DBMS_WM-reference.md)
- workspaces
  - altering description of [4.6](DBMS_WM-reference.md)
  - changing type [4.10](DBMS_WM-reference.md)
  - child
    - as alternative to creating savepoints [1.1.2.1](introduction-to-workspace-manager.md)
  - compressing [4.14](DBMS_WM-reference.md), [4.15](DBMS_WM-reference.md)
  - continually refreshed [1.1.9](introduction-to-workspace-manager.md), [4.10](DBMS_WM-reference.md), [4.19](DBMS_WM-reference.md)
  - copying [4.17](DBMS_WM-reference.md)
  - creating [4.19](DBMS_WM-reference.md)
  - freezing [1.1.5](introduction-to-workspace-manager.md), [4.27](DBMS_WM-reference.md)
  - getting [4.43](DBMS_WM-reference.md)
  - going to [4.46](DBMS_WM-reference.md)
  - hierarchy [1.1.1](introduction-to-workspace-manager.md)
  - management of [1.1](introduction-to-workspace-manager.md), [1.16.2](introduction-to-workspace-manager.md)
  - merging [1.1.3](introduction-to-workspace-manager.md)
  - multiparent [1.1.10](introduction-to-workspace-manager.md)
  - renaming [4.71](DBMS_WM-reference.md)
  - rolling back [1.1.3](introduction-to-workspace-manager.md)
  - unfreezing [1.1.5](introduction-to-workspace-manager.md), [4.100](DBMS_WM-reference.md)
