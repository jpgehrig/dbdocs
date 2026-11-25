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

- [Prev Class](NFEFeatureLayer.md)
- [Next Class](NFEFeatureShape.md)

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

oracle.spatial.network.nfe.model.feature

## Class NFEFeatureLayerMetadata

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEMetadata](../NFEMetadata.md)

  - - oracle.spatial.network.nfe.model.feature.NFEFeatureLayerMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEFeatureLayerMetadata
      extends NFEMetadata

  This class holds metadata for an NFE Feature Layer.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `NFEFeatureLayerMetadata``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                | Method and Description                                                                                                                                                       |
    |--------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEFeatureLayerMetadata`                                                                        | `createCopy``()`<br>Returns a copy of the feature layer metadata.                                                                                                            |
    | `long`                                                                                           | `getFeatureLayerId``()`<br>Returns the feature layer id.                                                                                                                     |
    | `java.lang.String`                                                                               | `getFeatureLayerName``()`<br>Returns the feature layer name.                                                                                                                 |
    | [`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md) | `getFeatureLayerType``()`<br>Returns the feature layer type.                                                                                                                 |
    | `java.lang.String`                                                                               | `getFeatureTable``()`<br>Returns the feature table.                                                                                                                          |
    | `java.lang.String`                                                                               | `getHierarchyTable``()`<br>Returns the hierarchy table.                                                                                                                      |
    | `java.lang.String`                                                                               | `getNetworkName``()`<br>Returns the network name.                                                                                                                            |
    | `java.lang.String`                                                                               | `getRelationTable``()`<br>Returns the relation table.                                                                                                                        |
    | `void`                                                                                           | `setFeatureLayerId``(long featureLayerId)`<br>Sets the feature layer id.                                                                                                     |
    | `void`                                                                                           | `setFeatureLayerName``(java.lang.String featureLayerName)`<br>Sets the feature layer name                                                                                    |
    | `void`                                                                                           | `setFeatureLayerType``(`[`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md)` featureLayerType)`<br>Sets the feature layer type. |
    | `void`                                                                                           | `setFeatureTable``(java.lang.String featureTable)`<br>Sets the feature table.                                                                                                |
    | `void`                                                                                           | `setHierarchyTable``(java.lang.String hierarchyTable)`<br>Sets the hierarchy table.                                                                                          |
    | `void`                                                                                           | `setNetworkName``(java.lang.String networkName)`<br>Sets network name.                                                                                                       |
    | `void`                                                                                           | `setRelationTable``(java.lang.String relationTable)`<br>Sets the relation table                                                                                              |
    | `java.lang.String`                                                                               | `toString``()`                                                                                                                                                               |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEMetadata](../NFEMetadata.md)

      [`getTableSequence`](../NFEMetadata.md)`, `[`getTablesWithSequence`](../NFEMetadata.md)`, `[`hasSequence`](../NFEMetadata.md)`, `[`setTableSequence`](../NFEMetadata.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEFeatureLayerMetadata

          public NFEFeatureLayerMetadata()

  <!-- -->

  - ### Method Detail

    - #### getNetworkName

          public java.lang.String getNetworkName()

      Returns the network name.
      Returns:
      network name

    <!-- -->

    - #### setNetworkName

          public void setNetworkName(java.lang.String networkName)

      Sets network name.
      Parameters:
      `networkName` - network name

    <!-- -->

    - #### getFeatureLayerName

          public java.lang.String getFeatureLayerName()

      Returns the feature layer name.
      Returns:
      feature layer name

    <!-- -->

    - #### setFeatureLayerName

          public void setFeatureLayerName(java.lang.String featureLayerName)

      Sets the feature layer name
      Parameters:
      `featureLayerName` - feature layer name

    <!-- -->

    - #### getFeatureLayerId

          public long getFeatureLayerId()

      Returns the feature layer id.
      Returns:
      feature layer id

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(long featureLayerId)

      Sets the feature layer id.
      Parameters:
      `featureLayerId` - feature layer id

    <!-- -->

    - #### getFeatureLayerType

          public FeatureLayerMetadata.FeatureLayerType getFeatureLayerType()

      Returns the feature layer type.
      Returns:
      feature layer type

    <!-- -->

    - #### setFeatureLayerType

          public void setFeatureLayerType(FeatureLayerMetadata.FeatureLayerType featureLayerType)

      Sets the feature layer type.
      Parameters:
      `featureLayerType` - feature layer type

    <!-- -->

    - #### getFeatureTable

          public java.lang.String getFeatureTable()

      Returns the feature table.
      Returns:
      feature table

    <!-- -->

    - #### setFeatureTable

          public void setFeatureTable(java.lang.String featureTable)

      Sets the feature table.
      Parameters:
      `featureTable` - feature table

    <!-- -->

    - #### getRelationTable

          public java.lang.String getRelationTable()

      Returns the relation table.
      Returns:
      relation table

    <!-- -->

    - #### setRelationTable

          public void setRelationTable(java.lang.String relationTable)

      Sets the relation table
      Parameters:
      `relationTable` - relation table

    <!-- -->

    - #### getHierarchyTable

          public java.lang.String getHierarchyTable()

      Returns the hierarchy table.
      Returns:
      hierarchy table

    <!-- -->

    - #### setHierarchyTable

          public void setHierarchyTable(java.lang.String hierarchyTable)

      Sets the hierarchy table.
      Parameters:
      `hierarchyTable` - hierarchy table

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### createCopy

          public NFEFeatureLayerMetadata createCopy()

      Returns a copy of the feature layer metadata.
      Returns:
      copy of the feature layer metadata

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

- [Prev Class](NFEFeatureLayer.md)
- [Next Class](NFEFeatureShape.md)

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
