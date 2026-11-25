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

- [Prev Class](JDBCModelIOService.md)
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

oracle.spatial.network.nfe.io.jdbc.service

## Class JDBCWorkspaceIOService

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.service.JDBCAbstractIOService](JDBCAbstractIOService.md)

  - - oracle.spatial.network.nfe.io.jdbc.service.JDBCWorkspaceIOService

<!-- -->

- All Implemented Interfaces:
  [NFEIOService](../../service/NFEIOService.md), [NFEWorkspaceIOService](../../service/NFEWorkspaceIOService.md)

  ------------------------------------------------------------------------



      public class JDBCWorkspaceIOService
      extends JDBCAbstractIOService
      implements NFEWorkspaceIOService

  Provides the default implementation for the workspace service.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                    |
    |----------------------------------------------------------------------------------------------------------------|
    | `JDBCWorkspaceIOService``(`[`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)` serviceProvider)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |--------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                   | `disableAllVersioning``()`<br>Disables the versioning for the model general tables and feature layers tables.                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                   | `disableVersioningForFeatureLayers``(java.util.List<`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)`> featureLayersToVersionList)`<br>Disables the versioning for the feature layers table: feature table, relation table and hierarchy table.                                                                                                                                                                                           |
    | `void`                                                                   | `disableVersioningForGeneralTables``()`<br>Disables the versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).                                                                                                                                                                                                                                                                          |
    | `void`                                                                   | `enableAllVersioning``()`<br>Enables the versioning for the model general tables and feature layers tables.                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                   | `enableVersioningForFeatureLayers``(java.util.List<`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)`> featureLayersToVersionList)`<br>Enables versioning for the feature layers table: feature table, relation table and hierarchy table.                                                                                                                                                                                                 |
    | `void`                                                                   | `enableVersioningForGeneralTables``()`<br>Enables versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).                                                                                                                                                                                                                                                                                |
    | `java.util.List<`[`NFEWorkspace`](../../../beans/NFEWorkspace.md)`>`     | `getModelWorkspaces``(long modelId)`<br>Returns the workspaces and the data related to the workspaces work area for the specified model.                                                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`                                                       | `getParentWorkspace``(java.lang.String workspaceName)`<br>Gets the parent workspace of the specified workspace.                                                                                                                                                                                                                                                                                                                                          |
    | [`NFEConflictsDescriptor`](../../../workspace/NFEConflictsDescriptor.md) | `getWorkspaceConflicts``(java.lang.String childWorkspace, java.lang.String parentWorkspace)`<br>Returns the workspace conflicts.                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                   | `mergeWorkspace``(java.lang.String workspaceName, java.lang.String parentWorkspace, boolean refreshLinkGeometries)`<br>Merges child and parent workspaces.                                                                                                                                                                                                                                                                                               |
    | `void`                                                                   | `removeWorkspace``(java.lang.String workspace)`<br>Removes the workspace and the related record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.                                                                                                                                                                                                                                                                                  |
    | `void`                                                                   | `resolveConflicts``(java.util.List<`[`FeatureAttributeDescriptor`](../../../workspace/FeatureAttributeDescriptor.md)`> featureAttributeDescriptorList, java.lang.String childWorkspace, java.lang.String parentWorkspace, java.lang.String choosenWorkspace)`<br>This function resolves workspace conflicts for the specified attributes by using the attributes values in the parent or child workspace as specified in the chosen workspace parameter. |
    | `void`                                                                   | `saveWorkspace``(java.lang.String parentWorkspace, `[`NFEWorkspace`](../../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Saves the workspace and create a record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.                                                                                                                                                                                                                  |
    | `void`                                                                   | `updateVersioning``(boolean isVersionable)`<br>Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable.                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                   | `updateWorkspace``(`[`NFEWorkspace`](../../../beans/NFEWorkspace.md)` nfeWorkspace)`<br>Updates the workspace related record in the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the object NFEWorkspace.                                                                                                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.service.[JDBCAbstractIOService](JDBCAbstractIOService.md)

      [`getDataSource`](JDBCAbstractIOService.md)`, `[`getModel`](JDBCAbstractIOService.md)`, `[`getServiceProvider`](JDBCAbstractIOService.md)`, `[`setDataSource`](JDBCAbstractIOService.md)`, `[`setModel`](JDBCAbstractIOService.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](../../service/NFEIOService.md)

      [`getDataSource`](../../service/NFEIOService.md)`, `[`getModel`](../../service/NFEIOService.md)`, `[`getServiceProvider`](../../service/NFEIOService.md)`, `[`setDataSource`](../../service/NFEIOService.md)`, `[`setModel`](../../service/NFEIOService.md)

<!-- -->

- - ### Constructor Detail

    - #### JDBCWorkspaceIOService

          public JDBCWorkspaceIOService(NFEIOServiceProvider serviceProvider)

  <!-- -->

  - ### Method Detail

    - #### enableVersioningForFeatureLayers

          public void enableVersioningForFeatureLayers(java.util.List<NFEFeatureLayer> featureLayersToVersionList)
                                                throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Enables versioning for the feature layers table: feature table, relation table and hierarchy table.
      Specified by:
      [`enableVersioningForFeatureLayers`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `featureLayersToVersionList` - feature layers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableVersioningForGeneralTables

          public void enableVersioningForGeneralTables()
                                                throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Enables versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).
      Specified by:
      [`enableVersioningForGeneralTables`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableAllVersioning

          public void enableAllVersioning()
                                   throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Enables the versioning for the model general tables and feature layers tables.
      Specified by:
      [`enableAllVersioning`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableVersioningForFeatureLayers

          public void disableVersioningForFeatureLayers(java.util.List<NFEFeatureLayer> featureLayersToVersionList)
                                                 throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Disables the versioning for the feature layers table: feature table, relation table and hierarchy table.
      Specified by:
      [`disableVersioningForFeatureLayers`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `featureLayersToVersionList` - feature layers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableVersioningForGeneralTables

          public void disableVersioningForGeneralTables()
                                                 throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Disables the versioning for the model general tables: RULE_INSTANCE, FT_RULE_REL, FT_CLASS_REL and network tables (links and nodes).
      Specified by:
      [`disableVersioningForGeneralTables`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### disableAllVersioning

          public void disableAllVersioning()
                                    throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Disables the versioning for the model general tables and feature layers tables.
      Specified by:
      [`disableAllVersioning`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### mergeWorkspace

          public void mergeWorkspace(java.lang.String workspaceName,
                                     java.lang.String parentWorkspace,
                                     boolean refreshLinkGeometries)
                              throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Merges child and parent workspaces. Any conflicts must be resolved before a workspace can be merged. Reload the model after to execute this function.
      Specified by:
      [`mergeWorkspace`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `workspaceName` - child workspace to merge

      `parentWorkspace` - parent workspace to merge

      `refreshLinkGeometries` - if true refresh the modified link geometries to ensure that the start and end of the link are the same than the start and end node geometries of the link.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### resolveConflicts

          public void resolveConflicts(java.util.List<FeatureAttributeDescriptor> featureAttributeDescriptorList,
                                       java.lang.String childWorkspace,
                                       java.lang.String parentWorkspace,
                                       java.lang.String choosenWorkspace)
                                throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      This function resolves workspace conflicts for the specified attributes by using the attributes values in the parent or child workspace as specified in the chosen workspace parameter. The attributes in conflict can be loaded with the function getWorkspaceConflicts. Merge the workspace after to execute this function and reload the model.
      Specified by:
      [`resolveConflicts`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `featureAttributeDescriptorList` - the conflicts involving the attributes in the list will resolved

      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      `choosenWorkspace` - chosen workspace

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getParentWorkspace

          public java.lang.String getParentWorkspace(java.lang.String workspaceName)
                                              throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Gets the parent workspace of the specified workspace.
      Specified by:
      [`getParentWorkspace`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `workspaceName` - workspace

      Returns:
      parent workspace

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getWorkspaceConflicts

          public NFEConflictsDescriptor getWorkspaceConflicts(java.lang.String childWorkspace,
                                                              java.lang.String parentWorkspace)
                                                       throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Returns the workspace conflicts. The conflicts are described by the NFEConflictsDescriptor object.
      Specified by:
      [`getWorkspaceConflicts`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `childWorkspace` - child workspace

      `parentWorkspace` - parent workspace

      Returns:
      conflict descriptor

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getModelWorkspaces

          public java.util.List<NFEWorkspace> getModelWorkspaces(long modelId)
                                                          throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Returns the workspaces and the data related to the workspaces work area for the specified model.
      Specified by:
      [`getModelWorkspaces`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `modelId` - model identifier

      Returns:
      model workspaces

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateVersioning

          public void updateVersioning(boolean isVersionable)
                                throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Updates the column USER_SDO_NFE_MODEL_METADATA.VERSIONABLE_IND with the value isVersionable. This method will not version enable any table.
      Specified by:
      [`updateVersioning`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `isVersionable` - true if the model is versionable, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveWorkspace

          public void saveWorkspace(java.lang.String parentWorkspace,
                                    NFEWorkspace nfeWorkspace)
                             throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Saves the workspace and create a record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.
      Specified by:
      [`saveWorkspace`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `parentWorkspace` - parent workspace of the saved workspace

      `nfeWorkspace` - workspace data

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removeWorkspace

          public void removeWorkspace(java.lang.String workspace)
                               throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Removes the workspace and the related record in the model workspace relationship table USER_SDO_NFE_MODEL_WORKSPACE.
      Specified by:
      [`removeWorkspace`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

      Parameters:
      `workspace` - workspace to remove

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateWorkspace

          public void updateWorkspace(NFEWorkspace nfeWorkspace)
                               throws NFEIOException

      Description copied from interface: [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)
      Updates the workspace related record in the table USER_SDO_NFE_MODEL_WORKSPACE with the data in the object NFEWorkspace.
      Specified by:
      [`updateWorkspace`](../../service/NFEWorkspaceIOService.md) in interface [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md)

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

- [Prev Class](JDBCModelIOService.md)
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
