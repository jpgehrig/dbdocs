Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEModelIOService.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.service

## Interface NFEWorkspaceIOService

- All Superinterfaces:
  [NFEIOService](NFEIOService.md)

  <!-- -->

  All Known Implementing Classes:
  [JDBCWorkspaceIOService](../jdbc/service/JDBCWorkspaceIOService.md)

  ------------------------------------------------------------------------



      public interface NFEWorkspaceIOService
      extends NFEIOService

  This interface defines methods related to model workspace management.
  Model general tables and feature layer tables can be versioned.
  The model general tables are: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).
  The feature layer tables are: feature table, relation table and hierarchy table.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                     | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                               |
    |-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                | `disableAllVersioning``()`<br>Disables the versioning for the model general tables and feature layers tables.                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                | `disableVersioningForFeatureLayers``(java.util.List<`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)`> featureLayersToVersionList)`<br>Disables the versioning for the feature layers table: feature table, relation table and hierarchy table.                                                                                                                                                                                          |
    | `void`                                                                | `disableVersioningForGeneralTables``()`<br>Disables the versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).                                                                                                                                                                                                                                                                      |
    | `void`                                                                | `enableAllVersioning``()`<br>Enables the versioning for the model general tables and feature layers tables.                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                | `enableVersioningForFeatureLayers``(java.util.List<`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)`> featureLayersToVersionList)`<br>Enables versioning for the feature layers table: feature table, relation table and hierarchy table.                                                                                                                                                                                                |
    | `void`                                                                | `enableVersioningForGeneralTables``()`<br>Enables versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).                                                                                                                                                                                                                                                                            |
    | `java.util.List<`[`NFEWorkspace`](../../beans/NFEWorkspace.md)`>`     | `getModelWorkspaces``(long modelId)`<br>Returns the workspaces and the data related to the workspaces work area for the specified model.                                                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                                                    | `getParentWorkspace``(java.lang.String workspaceName)`<br>Gets the parent workspace of the specified workspace.                                                                                                                                                                                                                                                                                                                                      |
    | [`NFEConflictsDescriptor`](../../workspace/NFEConflictsDescriptor.md) | `getWorkspaceConflicts``(java.lang.String childWorkspace, java.lang.String parentWorkspace)`<br>Returns the workspace conflicts.                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                | `mergeWorkspace``(java.lang.String workspaceName, java.lang.String parentWorkspace, boolean refreshLinkGeometries)`<br>Merges child and parent workspaces.                                                                                                                                                                                                                                                                                           |
    | `void`                                                                | `removeWorkspace``(java.lang.String workspace)`<br>Removes the workspace and the related record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.                                                                                                                                                                                                                                                                              |
    | `void`                                                                | `resolveConflicts``(java.util.List<`[`FeatureAttributeDescriptor`](../../workspace/FeatureAttributeDescriptor.md)`> featureAttributeDescriptorList, java.lang.String childWorkspace, java.lang.String parentWorkspace, java.lang.String chosenWorkspace)`<br>This function resolves workspace conflicts for the specified attributes by using the attributes values in the parent or child workspace as specified in the chosen workspace parameter. |
    | `void`                                                                | `saveWorkspace``(java.lang.String parentWorkspace, `[`NFEWorkspace`](../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Saves the workspace and create a record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.                                                                                                                                                                                                                 |
    | `void`                                                                | `updateVersioning``(boolean isVersionable)`<br>Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable.                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                | `updateWorkspace``(`[`NFEWorkspace`](../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Updates the workspace related record in the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the object NFEWorkspace.                                                                                                                                                                                                                                        |

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](NFEIOService.md)

      [`getDataSource`](NFEIOService.md)`, `[`getModel`](NFEIOService.md)`, `[`getServiceProvider`](NFEIOService.md)`, `[`setDataSource`](NFEIOService.md)`, `[`setModel`](NFEIOService.md)

<!-- -->

- - ### Method Detail

    - #### enableVersioningForFeatureLayers

          void enableVersioningForFeatureLayers(java.util.List<NFEFeatureLayer> featureLayersToVersionList)
                                         throws NFEIOException

      Enables versioning for the feature layers table: feature table, relation table and hierarchy table.
      Parameters:
      `featureLayersToVersionList` - feature layers

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableVersioningForGeneralTables

          void enableVersioningForGeneralTables()
                                         throws NFEIOException

      Enables versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableAllVersioning

          void enableAllVersioning()
                            throws NFEIOException

      Enables the versioning for the model general tables and feature layers tables.
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableVersioningForFeatureLayers

          void disableVersioningForFeatureLayers(java.util.List<NFEFeatureLayer> featureLayersToVersionList)
                                          throws NFEIOException

      Disables the versioning for the feature layers table: feature table, relation table and hierarchy table.
      Parameters:
      `featureLayersToVersionList` - feature layers

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableVersioningForGeneralTables

          void disableVersioningForGeneralTables()
                                          throws NFEIOException

      Disables the versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableAllVersioning

          void disableAllVersioning()
                             throws NFEIOException

      Disables the versioning for the model general tables and feature layers tables.
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### mergeWorkspace

          void mergeWorkspace(java.lang.String workspaceName,
                              java.lang.String parentWorkspace,
                              boolean refreshLinkGeometries)
                       throws NFEIOException

      Merges child and parent workspaces. Any conflicts must be resolved before a workspace can be merged. Reload the model after to execute this function.
      Parameters:
      `workspaceName` - child workspace to merge

      `parentWorkspace` - parent workspace to merge

      `refreshLinkGeometries` - if true refresh the modified link geometries to ensure that the start and end of the link are the same than the start and end node geometries of the link.

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### resolveConflicts

          void resolveConflicts(java.util.List<FeatureAttributeDescriptor> featureAttributeDescriptorList,
                                java.lang.String childWorkspace,
                                java.lang.String parentWorkspace,
                                java.lang.String chosenWorkspace)
                         throws NFEIOException

      This function resolves workspace conflicts for the specified attributes by using the attributes values in the parent or child workspace as specified in the chosen workspace parameter. The attributes in conflict can be loaded with the function getWorkspaceConflicts. Merge the workspace after to execute this function and reload the model.
      Parameters:
      `featureAttributeDescriptorList` - the conflicts involving the attributes in the list will resolved

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `chosenWorkspace` - chosen workspace

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getParentWorkspace

          java.lang.String getParentWorkspace(java.lang.String workspaceName)
                                       throws NFEIOException

      Gets the parent workspace of the specified workspace.
      Parameters:
      `workspaceName` - workspace

      Returns:
      parent workspace

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getWorkspaceConflicts

          NFEConflictsDescriptor getWorkspaceConflicts(java.lang.String childWorkspace,
                                                       java.lang.String parentWorkspace)
                                                throws NFEIOException

      Returns the workspace conflicts. The conflicts are described by the NFEConflictsDescriptor object.
      Parameters:
      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      Returns:
      conflict descriptor

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getModelWorkspaces

          java.util.List<NFEWorkspace> getModelWorkspaces(long modelId)
                                                   throws NFEIOException

      Returns the workspaces and the data related to the workspaces work area for the specified model.
      Parameters:
      `modelId` - model identifier

      Returns:
      model workspaces

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateVersioning

          void updateVersioning(boolean isVersionable)
                         throws NFEIOException

      Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable. This method will not version enable any table.
      Parameters:
      `isVersionable` - true if the model is versionable, false otherwise

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveWorkspace

          void saveWorkspace(java.lang.String parentWorkspace,
                             NFEWorkspace nfeWorkspace)
                      throws NFEIOException

      Saves the workspace and create a record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.
      Parameters:
      `parentWorkspace` - parent workspace of the saved workspace

      `nfeWorkspace` - workspace data

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removeWorkspace

          void removeWorkspace(java.lang.String workspace)
                        throws NFEIOException

      Removes the workspace and the related record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.
      Parameters:
      `workspace` - workspace to remove

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateWorkspace

          void updateWorkspace(NFEWorkspace nfeWorkspace)
                        throws NFEIOException

      Updates the workspace related record in the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the object NFEWorkspace.
      Parameters:
      `nfeWorkspace` - workspace data

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEModelIOService.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
