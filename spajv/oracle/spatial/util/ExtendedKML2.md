Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DBMS.md)
- [Next Class](Generalization3D.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.util

## Class ExtendedKML2

- java.lang.Object

- - oracle.spatial.util.ExtendedKML2

<!-- -->

-

  ------------------------------------------------------------------------



      public class ExtendedKML2
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ExtendedKML2``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type            | Method and Description                                                                                                                                                                                                                                                                                                                                            |
    |------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.sql.Connection` | `getConnection``()`                                                                                                                                                                                                                                                                                                                                               |
    | `static void`                | `setConnection``(java.sql.Connection connctn)`                                                                                                                                                                                                                                                                                                                    |
    | `static java.lang.String`    | `to_KML``(java.util.ArrayList geoms, java.lang.String[] tableName, java.lang.String[] columnName, int geometryCount, java.lang.String[] label, java.lang.String[] lod, boolean[] is_leaf, java.lang.String[] serverName, int[] serverPort)`<br>Returns the full KML representation of 3D geometry (i.e., building) Each BBOX is divided into 4 subsequent BBOXes. |
    | `static java.lang.String`    | `to_KML``(`[`JGeometry`](../geometry/JGeometry.md)` geom, java.lang.String[] tableName, java.lang.String[] columnName, int geometryCount, java.lang.String[] label, java.lang.String[] lod, boolean[] is_leaf, java.lang.String[] serverName, int[] serverPort)`                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ExtendedKML2

          public ExtendedKML2()

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public static void setConnection(java.sql.Connection connctn)

    <!-- -->

    - #### getConnection

          public static java.sql.Connection getConnection()

    <!-- -->

    - #### to_KML

          public static java.lang.String to_KML(java.util.ArrayList geoms,
                                                java.lang.String[] tableName,
                                                java.lang.String[] columnName,
                                                int geometryCount,
                                                java.lang.String[] label,
                                                java.lang.String[] lod,
                                                boolean[] is_leaf,
                                                java.lang.String[] serverName,
                                                int[] serverPort)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                DataException,
                                                java.lang.Exception

      Returns the full KML representation of 3D geometry (i.e., building) Each BBOX is divided into 4 subsequent BBOXes.
      Parameters:
      `geoms` -

      `tableName` -

      `columnName` -

      `geometryCount` -

      `label` -

      `lod` -

      `is_leaf` -

      `serverName` -

      `serverPort` -

      Returns:
      extended KML

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### to_KML

          public static java.lang.String to_KML(JGeometry geom,
                                                java.lang.String[] tableName,
                                                java.lang.String[] columnName,
                                                int geometryCount,
                                                java.lang.String[] label,
                                                java.lang.String[] lod,
                                                boolean[] is_leaf,
                                                java.lang.String[] serverName,
                                                int[] serverPort)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                DataException,
                                                java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DBMS.md)
- [Next Class](Generalization3D.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
