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

- [Prev Class](Las2SqlLdr.md)
- [Next Class](Las2SqlLdr.PointData.md)

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

## Class Las2SqlLdr.LasFileStream

- java.lang.Object

- - oracle.spatial.util.Las2SqlLdr.LasFileStream

<!-- -->

- Enclosing class:
  [Las2SqlLdr](Las2SqlLdr.md)

  ------------------------------------------------------------------------



      public static class Las2SqlLdr.LasFileStream
      extends java.lang.Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `long`            | `m_totalReadingTime`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                        |
    |----------------------------------------------------|
    | `LasFileStream``(java.io.DataInputStream dis)`     |
    | `LasFileStream``(java.lang.String sourceLasFile)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                        |
    |-------------------|-------------------------------------------------------------------------------|
    | `boolean`         | `addPoints``(`[`Las2SqlLdr.PointData`](Las2SqlLdr.PointData.md)` pointData)`  |
    | `boolean`         | `hasMore``()`                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### m_totalReadingTime

          public long m_totalReadingTime

  <!-- -->

  - ### Constructor Detail

    - #### LasFileStream

          public LasFileStream(java.lang.String sourceLasFile)
                        throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### LasFileStream

          public LasFileStream(java.io.DataInputStream dis)
                        throws java.io.IOException

      Throws:
      `java.io.IOException`

  <!-- -->

  - ### Method Detail

    - #### addPoints

          public boolean addPoints(Las2SqlLdr.PointData pointData)
                            throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### hasMore

          public boolean hasMore()

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

- [Prev Class](Las2SqlLdr.md)
- [Next Class](Las2SqlLdr.PointData.md)

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
