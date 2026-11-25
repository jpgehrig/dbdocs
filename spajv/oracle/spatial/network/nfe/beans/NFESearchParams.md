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

- [Prev Class](NFENearestNeighbors.md)
- [Next Class](NFEShortestPath.md)

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

oracle.spatial.network.nfe.beans

## Class NFESearchParams

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFESearchParams

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFESearchParams
      extends java.lang.Object

  Provides parameters to search features in the database. The featureLayerId is mandatory, the parameters featureClassId, featureId and conditionString are optional. The optional parameters set to null are ignored. The conditionString parameter will be added to the where clause of the search query on the feature table.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFESearchParams``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                              |
    |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object obj)`                                                                                                                    |
    | `java.lang.Long`   | `getFeatureClassId``()`<br>Returns the feature class id parameter.                                                                                  |
    | `java.lang.Long`   | `getFeatureId``()`<br>Returns the feature id parameter.                                                                                             |
    | `java.lang.Long`   | `getFeatureLayerId``()`<br>Returns the feature layer id parameter.                                                                                  |
    | `java.lang.String` | `getSqlCondition``()`<br>Returns the SQL that will be added to the where clause of the search query on the feature table.                           |
    | `int`              | `hashCode``()`                                                                                                                                      |
    | `void`             | `setFeatureClassId``(java.lang.Long featureClassId)`<br>Sets the feature class id parameter.                                                        |
    | `void`             | `setFeatureId``(java.lang.Long featureId)`<br>Sets the feature id parameter.                                                                        |
    | `void`             | `setFeatureLayerId``(java.lang.Long featureLayerId)`<br>Sets the feature layer id parameter.                                                        |
    | `void`             | `setSqlCondition``(java.lang.String sqlCondition)`<br>Sets the SQL that will be added to the where clause of the search query on the feature table. |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFESearchParams

          public NFESearchParams()

  <!-- -->

  - ### Method Detail

    - #### getSqlCondition

          public java.lang.String getSqlCondition()

      Returns the SQL that will be added to the where clause of the search query on the feature table. If null the parameter is ignored.
      Returns:
      SQL condition

    <!-- -->

    - #### setSqlCondition

          public void setSqlCondition(java.lang.String sqlCondition)

      Sets the SQL that will be added to the where clause of the search query on the feature table.
      Parameters:
      `sqlCondition` - SQL condition

    <!-- -->

    - #### getFeatureClassId

          public java.lang.Long getFeatureClassId()

      Returns the feature class id parameter. If null the parameter is ignored.
      Returns:
      feature class id

    <!-- -->

    - #### setFeatureClassId

          public void setFeatureClassId(java.lang.Long featureClassId)

      Sets the feature class id parameter.
      Parameters:
      `featureClassId` - feature class id

    <!-- -->

    - #### getFeatureId

          public java.lang.Long getFeatureId()

      Returns the feature id parameter. If null the parameter is ignored.
      Returns:
      feature id

    <!-- -->

    - #### setFeatureId

          public void setFeatureId(java.lang.Long featureId)

      Sets the feature id parameter.
      Parameters:
      `featureId` - feature id

    <!-- -->

    - #### getFeatureLayerId

          public java.lang.Long getFeatureLayerId()

      Returns the feature layer id parameter.
      Returns:
      feature layer id

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(java.lang.Long featureLayerId)

      Sets the feature layer id parameter.
      Parameters:
      `featureLayerId` - feature layer id

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

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

- [Prev Class](NFENearestNeighbors.md)
- [Next Class](NFEShortestPath.md)

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
