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

- [Prev Class](NFEIdManager.md)
- [Next Class](NFEModel.md)

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

oracle.spatial.network.nfe.model

## Class NFEMetadata

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEMetadata

<!-- -->

- Direct Known Subclasses:
  [NFEFeatureLayerMetadata](feature/NFEFeatureLayerMetadata.md), [NFEModelMetadata](NFEModelMetadata.md), [NFENetworkMetadata](network/NFENetworkMetadata.md)

  ------------------------------------------------------------------------



      public abstract class NFEMetadata
      extends java.lang.Object

  Parent class for all classes that hold metadata of any First Class Model Object such as NFEModel, NFENetwork or NFEFeatureLayer. This class contains convenient methods that may be used by any sub class

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEMetadata``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                              |
    |------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                       | `getTableSequence``(java.lang.String tableName)`<br>Gets the name of the sequence associated to the given table name                |
    | `java.util.Collection<java.lang.String>` | `getTablesWithSequence``()`<br>Returns all the table names that are associated to a sequence name                                   |
    | `boolean`                                | `hasSequence``(java.lang.String tableName)`<br>Tells whether the table name is associated to a sequence                             |
    | `void`                                   | `setTableSequence``(java.lang.String tableName, java.lang.String sequenceName)`<br>Associates a sequence name to a given table name |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEMetadata

          public NFEMetadata()

  <!-- -->

  - ### Method Detail

    - #### setTableSequence

          public void setTableSequence(java.lang.String tableName,
                                       java.lang.String sequenceName)

      Associates a sequence name to a given table name
      Parameters:
      `tableName` - a database table name

      `sequenceName` - a database sequence name

    <!-- -->

    - #### getTableSequence

          public java.lang.String getTableSequence(java.lang.String tableName)

      Gets the name of the sequence associated to the given table name
      Parameters:
      `tableName` - a database table name

      Returns:
      a name of a sequence or null if the table is not associated to any sequence

    <!-- -->

    - #### hasSequence

          public boolean hasSequence(java.lang.String tableName)

      Tells whether the table name is associated to a sequence
      Parameters:
      `tableName` - a database table name

      Returns:
      true if the table is associated to a sequence.

    <!-- -->

    - #### getTablesWithSequence

          public java.util.Collection<java.lang.String> getTablesWithSequence()

      Returns all the table names that are associated to a sequence name
      Returns:
      a collection containing table names as strings

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

- [Prev Class](NFEIdManager.md)
- [Next Class](NFEModel.md)

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
