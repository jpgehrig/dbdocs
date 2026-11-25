Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SpatialDAO.md)
- Next Class

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc.dao

## Class WorkspaceDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.WorkspaceDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class WorkspaceDAO
      extends AbstractDAO

  The WorkspaceDAO data access object provides methods related to the model workspace management. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `WorkspaceDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a WorkspaceDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                    | Method and Description                                                                                                                                                                                                                                                  |
    |--------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                               | `createModelWorkspaceRel``(`[`NFEWorkspace`](../../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Creates a record in the model workspace relationship table USER_NFE_NFE_MODEL_WORKSPACE.                                                                                |
    | `void`                                                                               | `createWorkspace``(java.lang.String parentWorkspace, java.lang.String newWorkspaceName)`<br>Creates a workspace in the database with the specified workspace name.                                                                                                      |
    | `void`                                                                               | `deleteWorkspaceRel``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, java.lang.String workspace)`<br>Deletes the record related to the specified workspace in the table USER_SDO_NFE_MODEL_WORKSPACE.                                     |
    | `java.util.List<`[`NFEWorkspace`](../../../beans/NFEWorkspace.md)`>`                 | `getModelWorkspaces``(long modelId)`<br>Returns the workspaces that belongs to the model                                                                                                                                                                                |
    | `java.util.List<`[`ConflictDescriptor`](../../../workspace/ConflictDescriptor.md)`>` | `getWorkspaceConflicts``(java.lang.String table, java.lang.String childWorkspace, java.lang.String parentWorkspace, java.util.List<java.lang.String> keyColumnList)`<br>Returns the workspace conflicts between the child and parent workspace for specified the table. |
    | `java.util.List<java.lang.String>`                                                   | `getWorkspaces``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata)`<br>Returns a list with the names of the workspaces related to the model.                                                                                                 |
    | `void`                                                                               | `removeLeafWorkspace``(java.lang.String workspace)`<br>Discards all row versions associated with a workspace and its descendant workspaces, and deletes the affected workspaces.                                                                                        |
    | `void`                                                                               | `removeWorkspace``(java.lang.String workspace)`<br>Discards all row versions associated with a workspace and deletes the workspace.                                                                                                                                     |
    | `void`                                                                               | `updateModelWorkspaceRel``(`[`NFEWorkspace`](../../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Updates the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the nfeWorkspace object.                                                                                |
    | `void`                                                                               | `updateVersiongForProject``(boolean isVersionable)`<br>Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable.                                                                                                                     |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### WorkspaceDAO

          public WorkspaceDAO(java.sql.Connection conn,
                              NFEModel model)

      Creates a WorkspaceDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### getWorkspaceConflicts

          public java.util.List<ConflictDescriptor> getWorkspaceConflicts(java.lang.String table,
                                                                          java.lang.String childWorkspace,
                                                                          java.lang.String parentWorkspace,
                                                                          java.util.List<java.lang.String> keyColumnList)
                                                                   throws NFEIOException

      Returns the workspace conflicts between the child and parent workspace for specified the table.
      Parameters:
      `table` - the table

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `keyColumnList` - a list with the name of the key columns of the table

      Returns:
      list of conflict descriptors.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getWorkspaces

          public java.util.List<java.lang.String> getWorkspaces(NFEModelMetadata nfeModelMetadata)
                                                         throws NFEIOException

      Returns a list with the names of the workspaces related to the model.
      Parameters:
      `nfeModelMetadata` - model metadata

      Returns:
      list with the names of the workspaces related to the model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removeLeafWorkspace

          public void removeLeafWorkspace(java.lang.String workspace)
                                   throws NFEIOException

      Discards all row versions associated with a workspace and its descendant workspaces, and deletes the affected workspaces.
      Parameters:
      `workspace` - workspace name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteWorkspaceRel

          public void deleteWorkspaceRel(NFEModelMetadata nfeModelMetadata,
                                         java.lang.String workspace)
                                  throws NFEIOException

      Deletes the record related to the specified workspace in the table USER_SDO_NFE_MODEL_WORKSPACE.
      Parameters:
      `nfeModelMetadata` - model metadata

      `workspace` - workspace name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getModelWorkspaces

          public java.util.List<NFEWorkspace> getModelWorkspaces(long modelId)
                                                          throws NFEIOException

      Returns the workspaces that belongs to the model
      Parameters:
      `modelId` - model identifier

      Returns:
      model workspaces

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateVersiongForProject

          public void updateVersiongForProject(boolean isVersionable)
                                        throws NFEIOException

      Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable. This method will not version enable any table.
      Parameters:
      `isVersionable` - true if the model is versionable, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createWorkspace

          public void createWorkspace(java.lang.String parentWorkspace,
                                      java.lang.String newWorkspaceName)
                               throws NFEIOException

      Creates a workspace in the database with the specified workspace name.
      Parameters:
      `parentWorkspace` - the parent workspace of the new workspace

      `newWorkspaceName` - new workspace name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createModelWorkspaceRel

          public void createModelWorkspaceRel(NFEWorkspace nfeWorkspace)
                                       throws NFEIOException

      Creates a record in the model workspace relationship table USER_NFE_NFE_MODEL_WORKSPACE.
      Parameters:
      `nfeWorkspace` - workspace data

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removeWorkspace

          public void removeWorkspace(java.lang.String workspace)
                               throws NFEIOException

      Discards all row versions associated with a workspace and deletes the workspace.
      Parameters:
      `workspace` - workspace to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateModelWorkspaceRel

          public void updateModelWorkspaceRel(NFEWorkspace nfeWorkspace)
                                       throws NFEIOException

      Updates the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the nfeWorkspace object.
      Parameters:
      `nfeWorkspace` - workspace data

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SpatialDAO.md)
- Next Class

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
