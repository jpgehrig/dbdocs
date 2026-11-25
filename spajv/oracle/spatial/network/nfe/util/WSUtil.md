Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](StringUtils.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network.nfe.util

## Class WSUtil

- java.lang.Object

- - oracle.spatial.network.nfe.util.WSUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class WSUtil
      extends java.lang.Object

  Provides static methods related to the workspace management.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                             |
    |---------------------------|---------------------------------------------------|
    | `static java.lang.String` | `PARENT_ATTR`<br>Hierarchy parent attribute name. |
    | `static java.lang.String` | `SHAPE_ATTR`<br>Shape attribute name.             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `WSUtil``()`                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                                          |
    |-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                                               | `checkConstraintsConsistencies``(java.sql.Connection conn, java.lang.String childWorkspace, java.lang.String parentWorkspace, `[`NFENetworkMetadata`](../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata, `[`NFEEditionMode`](../model/NFEEditionMode.md)` nfeEditionMode)`<br>Inserts the nodes that were deleted in the parent workspace and child workspace.        |
    | `static void`                                                               | `disableVersioning``(java.sql.Connection conn, java.lang.String table, boolean force, boolean ignoreLastError, boolean isTopology)`<br>Disables versioning with SQL procedure dbms_wm.DisableVersioning.                                                                                                                                                                        |
    | `static void`                                                               | `enableVersioning``(java.sql.Connection conn, java.lang.String dataName, java.lang.String historyMode, boolean isTopology, java.lang.String undoSpace)`<br>Enables versioning with SQL procedure dbms_wm.EnableVersioning.                                                                                                                                                      |
    | `static java.util.List<java.lang.Long>`                                     | `getModifiedLinks``(java.sql.Connection conn, java.lang.String childWorkspace, java.lang.String parentWorkspace, java.lang.String linkTable, `[`NFEEditionMode`](../model/NFEEditionMode.md)` nfeEditionMode)`<br>Returns the links that are different in child workspace and parent workspace.                                                                                 |
    | `static `[`NFEConflictsDescriptor`](../workspace/NFEConflictsDescriptor.md) | `getWorkspaceConflicts``(java.sql.Connection conn, java.lang.String childWorkspace, java.lang.String parentWorkspace, `[`NFEModel`](../model/NFEModel.md)` nfeModel)`<br>Returns the workspace's conflicts.                                                                                                                                                                     |
    | `static void`                                                               | `gotoWorkspace``(java.sql.Connection conn, java.lang.String workspaceName)`<br>Goes to a Workspace given (`workspaceName`) in the DB connection given (`conn`).                                                                                                                                                                                                                 |
    | `static void`                                                               | `mergeWorkspace``(java.sql.Connection conn, java.lang.String workspace)`<br>Applies all workspace changes to its parent workspace,.                                                                                                                                                                                                                                             |
    | `static void`                                                               | `refreshWorkspace``(java.sql.Connection conn, java.lang.String workspace)`<br>Applies to a workspace all changes made in its parent workspace.                                                                                                                                                                                                                                  |
    | `static void`                                                               | `removeDanglingFeatureElements``(java.sql.Connection conn, java.lang.String workspace, `[`NFEModel`](../model/NFEModel.md)` model)`<br>Deletes feature elements that are not referencing existing features.                                                                                                                                                                     |
    | `static void`                                                               | `removeDanglingNetworkElements``(java.sql.Connection conn, java.lang.String workspace, `[`NFENetworkMetadata`](../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata, `[`NFEEditionMode`](../model/NFEEditionMode.md)` nfeEditionMode)`<br>Deletes the network elements that are not referenced by any feature in any feature layer.                                      |
    | `static void`                                                               | `removeDanglingRulesElements``(java.sql.Connection conn, java.lang.String workspace, `[`NFEModel`](../model/NFEModel.md)` model)`<br>Deletes rules elements that are not referencing existing features.                                                                                                                                                                         |
    | `static void`                                                               | `resolveConflicts``(java.sql.Connection conn, java.util.List<`[`FeatureAttributeDescriptor`](../workspace/FeatureAttributeDescriptor.md)`> featureAttributeDescriptorList, java.lang.String childWorkspace, java.lang.String parentWorkspace, java.lang.String choosenWorkspace, `[`NFEModel`](../model/NFEModel.md)` nfeModel)`<br>Resolves the specified workspace conflicts. |
    | `static void`                                                               | `resolveWSConflicts``(java.sql.Connection conn, java.lang.String childWorkspace, java.lang.String table)`<br>Resolves the conflicts with child workspace changes using SQL procedure dbms_wm.ResolveConflicts.                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### SHAPE_ATTR

          public static final java.lang.String SHAPE_ATTR

      Shape attribute name.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### PARENT_ATTR

          public static final java.lang.String PARENT_ATTR

      Hierarchy parent attribute name.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### WSUtil

          public WSUtil()

  <!-- -->

  - ### Method Detail

    - #### gotoWorkspace

          public static void gotoWorkspace(java.sql.Connection conn,
                                           java.lang.String workspaceName)
                                    throws InvalidDBConnectionException

      Goes to a Workspace given (`workspaceName`) in the DB connection given (`conn`).
      Parameters:
      `conn` - connection

      `workspaceName` - workspace name

      Throws:
      [`InvalidDBConnectionException`](../io/InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### refreshWorkspace

          public static void refreshWorkspace(java.sql.Connection conn,
                                              java.lang.String workspace)
                                       throws java.lang.Exception

      Applies to a workspace all changes made in its parent workspace.
      Parameters:
      `conn` - connection

      `workspace` - workspace

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### mergeWorkspace

          public static void mergeWorkspace(java.sql.Connection conn,
                                            java.lang.String workspace)
                                     throws java.lang.Exception

      Applies all workspace changes to its parent workspace,.
      Parameters:
      `conn` - connection

      `workspace` - child workspace

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### getWorkspaceConflicts

          public static NFEConflictsDescriptor getWorkspaceConflicts(java.sql.Connection conn,
                                                                     java.lang.String childWorkspace,
                                                                     java.lang.String parentWorkspace,
                                                                     NFEModel nfeModel)
                                                              throws java.lang.Exception

      Returns the workspace's conflicts.
      Parameters:
      `conn` - connection

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `nfeModel` - model

      Returns:
      conflict descriptor

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### resolveConflicts

          public static void resolveConflicts(java.sql.Connection conn,
                                              java.util.List<FeatureAttributeDescriptor> featureAttributeDescriptorList,
                                              java.lang.String childWorkspace,
                                              java.lang.String parentWorkspace,
                                              java.lang.String choosenWorkspace,
                                              NFEModel nfeModel)
                                       throws java.lang.Exception

      Resolves the specified workspace conflicts.
      Parameters:
      `conn` - connection

      `featureAttributeDescriptorList` - attributes in conflict

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `choosenWorkspace` - chosen workspace

      `nfeModel` - model

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### removeDanglingNetworkElements

          public static void removeDanglingNetworkElements(java.sql.Connection conn,
                                                           java.lang.String workspace,
                                                           NFENetworkMetadata nfeNetworkMetadata,
                                                           NFEEditionMode nfeEditionMode)
                                                    throws java.lang.Exception

      Deletes the network elements that are not referenced by any feature in any feature layer.
      Parameters:
      `conn` - connection

      `workspace` - workspace in which to remove the dangling network elements

      `nfeNetworkMetadata` - network metadata

      `nfeEditionMode` - model edition mode

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### removeDanglingRulesElements

          public static void removeDanglingRulesElements(java.sql.Connection conn,
                                                         java.lang.String workspace,
                                                         NFEModel model)
                                                  throws java.lang.Exception

      Deletes rules elements that are not referencing existing features.
      Parameters:
      `conn` - connection

      `workspace` - workspace in which to remove the dangling rules elements

      `model` - model

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### removeDanglingFeatureElements

          public static void removeDanglingFeatureElements(java.sql.Connection conn,
                                                           java.lang.String workspace,
                                                           NFEModel model)
                                                    throws java.lang.Exception

      Deletes feature elements that are not referencing existing features.
      Parameters:
      `conn` - connection

      `workspace` - workspace in which to remove the dangling feature elements

      `model` - model

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### resolveWSConflicts

          public static void resolveWSConflicts(java.sql.Connection conn,
                                                java.lang.String childWorkspace,
                                                java.lang.String table)
                                         throws java.lang.Exception

      Resolves the conflicts with child workspace changes using SQL procedure dbms_wm.ResolveConflicts.
      Parameters:
      `conn` - connection

      `childWorkspace` - child workspace

      `table` - table in which the conflicts will be resolved

      `keyList` - The key of the map is the key column name and the value is the value of the key. If empty all the conflicts of the tables are resolved.

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### checkConstraintsConsistencies

          public static void checkConstraintsConsistencies(java.sql.Connection conn,
                                                           java.lang.String childWorkspace,
                                                           java.lang.String parentWorkspace,
                                                           NFENetworkMetadata nfeNetworkMetadata,
                                                           NFEEditionMode nfeEditionMode)
                                                    throws java.lang.Exception

      Inserts the nodes that were deleted in the parent workspace and child workspace. It will avoid links pointing to non existing start or end nodes after to merge workspaces.
      Parameters:
      `conn` - connection

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `nfeNetworkMetadata` - network metadata

      `nfeEditionMode` - model edition mode

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### getModifiedLinks

          public static java.util.List<java.lang.Long> getModifiedLinks(java.sql.Connection conn,
                                                                        java.lang.String childWorkspace,
                                                                        java.lang.String parentWorkspace,
                                                                        java.lang.String linkTable,
                                                                        NFEEditionMode nfeEditionMode)
                                                                 throws java.lang.Exception

      Returns the links that are different in child workspace and parent workspace. The links are in workspace manager table linkTable_diff.
      Parameters:
      `conn` - connection

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `linkTable` - link table

      `nfeEditionMode` - model edition mode

      Returns:
      identifiers of the links

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### enableVersioning

          public static void enableVersioning(java.sql.Connection conn,
                                              java.lang.String dataName,
                                              java.lang.String historyMode,
                                              boolean isTopology,
                                              java.lang.String undoSpace)
                                       throws java.lang.Exception

      Enables versioning with SQL procedure dbms_wm.EnableVersioning. Table must have a primary key in order to be versioned.
      Parameters:
      `conn` - connection

      `dataName` - table name or topology name if it is a topology

      `historyMode` - to store modifications or not: NONE (default), VIEW_W_OVERWRITE, or VIEW_WO_OVERWRITE. If null, then default NONE is used.

      `isTopology` - if table belongs to topology (TRUE or FALSE).

      `undoSpace` - number representing the maximum number of bytes available for undo space. For example: "1048576" for 1 megabyte. If not defined, then means UNLIMITED undo space.

      Throws:
      `java.lang.Exception` - if an exception is thrown

    <!-- -->

    - #### disableVersioning

          public static void disableVersioning(java.sql.Connection conn,
                                               java.lang.String table,
                                               boolean force,
                                               boolean ignoreLastError,
                                               boolean isTopology)
                                        throws java.lang.Exception

      Disables versioning with SQL procedure dbms_wm.DisableVersioning.
      Parameters:
      `conn` - connection

      `table` - table name or topology name if it is topology

      `force` - true forces all data in workspaces other than LIVE to be discarded before versioning is disabled. False prevents versioning from being disabled if table_name was modified in any workspace other than LIVE and if the workspace that modified table_name still exists.

      `ignoreLastError` - true ignores the last error, if any, that occurred during the previous call to the DisableVersioning procedure. Information about the last error is stored in the USER_WM_VT_ERRORS and ALL_WM_VT_ERRORS static data dictionary views. False does not ignore the last error, if any, that occurred during the previous call to the DisableVersioning procedure.

      `isTopology` - if table belongs to topology (TRUE or FALSE)

      Throws:
      `java.lang.Exception` - if an exception is thrown

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](StringUtils.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
