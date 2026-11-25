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

- [Prev Class](ModelDAO.md)
- [Next Class](NetworkDAO.md)

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

## Class ModelDAO.ModelFeatLayerRelation

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.dao.ModelDAO.ModelFeatLayerRelation

<!-- -->

- Enclosing class:
  [ModelDAO](ModelDAO.md)

  ------------------------------------------------------------------------



      public class ModelDAO.ModelFeatLayerRelation
      extends java.lang.Object

  Class that store information about the feature layers. The information is store in the table USER_SDO_NFE_MODEL_FTLAYER_REL.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `ModelFeatLayerRelation``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                           |
    |-------------------|----------------------------------------------------------------------------------|
    | `long`            | `getFeatureLayerId``()`<br>Returns the feature layer identifier.                 |
    | `int`             | `getHierarchyLevel``()`<br>Returns the hierarchy level.                          |
    | `int`             | `getzOrder``()`<br>Returns the feature layer Z-order.                            |
    | `void`            | `setFeatureLayerId``(long featureLayerId)`<br>Sets the feature layer identifier. |
    | `void`            | `setHierarchyLevel``(int hierarchyLevel)`<br>Sets the hierarchy level.           |
    | `void`            | `setzOrder``(int zOrder)`<br>Sets the feature layer Z-order.                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ModelFeatLayerRelation

          public ModelFeatLayerRelation()

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayerId

          public long getFeatureLayerId()

      Returns the feature layer identifier.
      Returns:
      feature layer identifier

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(long featureLayerId)

      Sets the feature layer identifier.
      Parameters:
      `featureLayerId` - feature layer identifier

    <!-- -->

    - #### getHierarchyLevel

          public int getHierarchyLevel()

      Returns the hierarchy level.
      Returns:
      hierarchy level

    <!-- -->

    - #### setHierarchyLevel

          public void setHierarchyLevel(int hierarchyLevel)

      Sets the hierarchy level.
      Parameters:
      `hierarchyLevel` - hierarchy level

    <!-- -->

    - #### getzOrder

          public int getzOrder()

      Returns the feature layer Z-order. The Z-order determines which feature layer appears on top of the other.
      Returns:
      feature layer Z-order. The Z-order determines which feature layer appears on top of the other.

    <!-- -->

    - #### setzOrder

          public void setzOrder(int zOrder)

      Sets the feature layer Z-order. The Z-order determines which feature layer appears on top of the other.
      Parameters:
      `zOrder` - feature layer Z-order. The Z-order determines which feature layer appears on top of the other.

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

- [Prev Class](ModelDAO.md)
- [Next Class](NetworkDAO.md)

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
