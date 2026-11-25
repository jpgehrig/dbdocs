Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureLayerImpl.md)
- [Next Class](FeatureLayerMetadata.FeatureLayerType.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class FeatureLayerMetadata

- java.lang.Object

- - oracle.spatial.network.lod.FeatureLayerMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureLayerMetadata
      extends java.lang.Object

  Metadata information for a feature layer.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                       |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`FeatureLayerMetadata.FeatureLayerType`](FeatureLayerMetadata.FeatureLayerType.md)<br>A list of valid feature layer types. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureLayerMetadata``(java.lang.String networkName, int featureLayerId, java.lang.String featureLayerName, `[`FeatureLayerMetadata.FeatureLayerType`](FeatureLayerMetadata.FeatureLayerType.md)` featureLayerType, java.lang.String featureTableName, java.lang.String relationTableName, java.lang.String hierarchyTableName)`<br>Constructs a feature layer metadata instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                            | Method and Description                                                                                                                                                  |
    |----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                        | `getFeatureLayerId``()`<br>Returns the ID of the feature layer.                                                                                                         |
    | `java.lang.String`                                                                           | `getFeatureLayerName``()`<br>Returns the name of the feature layer.                                                                                                     |
    | [`FeatureLayerMetadata.FeatureLayerType`](FeatureLayerMetadata.FeatureLayerType.md)          | `getFeatureLayerType``()`<br>Returns the type of the feature layer.                                                                                                     |
    | `java.lang.String`                                                                           | `getFeatureTableName``()`<br>Returns the name of the feature table.                                                                                                     |
    | `java.lang.String`                                                                           | `getHierarchyTableName``()`<br>Returns the name of the hierarchy table.                                                                                                 |
    | `java.lang.String`                                                                           | `getNetworkName``()`<br>Returns the network name for the feature layer.                                                                                                 |
    | `java.lang.String`                                                                           | `getRelationTableName``()`<br>Returns the name of the relation table.                                                                                                   |
    | `static `[`FeatureElement.FeatureElementType`](FeatureElement.FeatureElementType.md)         | `numberToFeatureElementType``(int type)`<br>This method maps the number used to represent feature element type in the database to the feature element type java object. |
    | `static `[`FeatureLayerMetadata.FeatureLayerType`](FeatureLayerMetadata.FeatureLayerType.md) | `numberToFeatureLayerType``(int type)`<br>This method maps the number used to represent feature layer type in the database to the feature layer type java object.       |
    | `static `[`Feature.FeatureType`](Feature.FeatureType.md)                                     | `numberToFeatureType``(int type)`<br>This method maps the number used to represent feature type in the database to the feature type java object.                        |
    | `void`                                                                                       | `setFeatureLayerId``(int featureLayerId)`<br>Sets the ID of the feature layer.                                                                                          |
    | `void`                                                                                       | `setFeatureLayerName``(java.lang.String featureLayerName)`<br>Sets the name of the feature layer.                                                                       |
    | `void`                                                                                       | `setFeatureLayerType``(`[`FeatureLayerMetadata.FeatureLayerType`](FeatureLayerMetadata.FeatureLayerType.md)` featureLayerType)`<br>Sets the type of the feature layer.  |
    | `void`                                                                                       | `setFeatureTableName``(java.lang.String featureTableName)`<br>Sets the name of the feature table.                                                                       |
    | `void`                                                                                       | `setHierarchyTableName``(java.lang.String hierarchyTableName)`<br>Sets the name of the hierarchy table.                                                                 |
    | `void`                                                                                       | `setNetworkName``(java.lang.String networkName)`<br>Sets the network name for the feature layer.                                                                        |
    | `void`                                                                                       | `setRelationTableName``(java.lang.String relationTableName)`<br>Sets the name of the relation table.                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureLayerMetadata

          public FeatureLayerMetadata(java.lang.String networkName,
                                      int featureLayerId,
                                      java.lang.String featureLayerName,
                                      FeatureLayerMetadata.FeatureLayerType featureLayerType,
                                      java.lang.String featureTableName,
                                      java.lang.String relationTableName,
                                      java.lang.String hierarchyTableName)

      Constructs a feature layer metadata instance.
      Parameters:
      `networkName` - network name

      `featureLayerId` - feature layer ID

      `featureLayerName` - feature layer name

      `featureLayerType` - feature layer type

      `featureTableName` - feature table name

      `relationTableName` - relation table name

      `hierarchyTableName` - hierarchy table name

  <!-- -->

  - ### Method Detail

    - #### setNetworkName

          public void setNetworkName(java.lang.String networkName)

      Sets the network name for the feature layer.
      Parameters:
      `networkName` -

    <!-- -->

    - #### getNetworkName

          public java.lang.String getNetworkName()

      Returns the network name for the feature layer.
      Returns:

    <!-- -->

    - #### setFeatureLayerName

          public void setFeatureLayerName(java.lang.String featureLayerName)

      Sets the name of the feature layer.
      Parameters:
      `featureLayerName` -

    <!-- -->

    - #### getFeatureLayerName

          public java.lang.String getFeatureLayerName()

      Returns the name of the feature layer.
      Returns:

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(int featureLayerId)

      Sets the ID of the feature layer.
      Parameters:
      `featureLayerId` -

    <!-- -->

    - #### getFeatureLayerId

          public int getFeatureLayerId()

      Returns the ID of the feature layer.
      Returns:

    <!-- -->

    - #### setFeatureLayerType

          public void setFeatureLayerType(FeatureLayerMetadata.FeatureLayerType featureLayerType)

      Sets the type of the feature layer.
      Parameters:
      `featureLayerType` -

    <!-- -->

    - #### getFeatureLayerType

          public FeatureLayerMetadata.FeatureLayerType getFeatureLayerType()

      Returns the type of the feature layer.
      Returns:

    <!-- -->

    - #### setFeatureTableName

          public void setFeatureTableName(java.lang.String featureTableName)

      Sets the name of the feature table.
      Parameters:
      `featureTableName` -

    <!-- -->

    - #### getFeatureTableName

          public java.lang.String getFeatureTableName()

      Returns the name of the feature table.
      Returns:

    <!-- -->

    - #### setRelationTableName

          public void setRelationTableName(java.lang.String relationTableName)

      Sets the name of the relation table.
      Parameters:
      `relationTableName` -

    <!-- -->

    - #### getRelationTableName

          public java.lang.String getRelationTableName()

      Returns the name of the relation table.
      Returns:

    <!-- -->

    - #### setHierarchyTableName

          public void setHierarchyTableName(java.lang.String hierarchyTableName)

      Sets the name of the hierarchy table.
      Parameters:
      `hierarchyTableName` -

    <!-- -->

    - #### getHierarchyTableName

          public java.lang.String getHierarchyTableName()

      Returns the name of the hierarchy table.
      Returns:

    <!-- -->

    - #### numberToFeatureLayerType

          public static FeatureLayerMetadata.FeatureLayerType numberToFeatureLayerType(int type)

      This method maps the number used to represent feature layer type in the database to the feature layer type java object.
      Parameters:

      `type` -

      Returns:

    <!-- -->

    - #### numberToFeatureType

          public static Feature.FeatureType numberToFeatureType(int type)

      This method maps the number used to represent feature type in the database to the feature type java object.
      Parameters:

      `type` -

      Returns:

    <!-- -->

    - #### numberToFeatureElementType

          public static FeatureElement.FeatureElementType numberToFeatureElementType(int type)

      This method maps the number used to represent feature element type in the database to the feature element type java object.
      Parameters:

      `type` -

      Returns:

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureLayerImpl.md)
- [Next Class](FeatureLayerMetadata.FeatureLayerType.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
