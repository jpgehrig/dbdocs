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

- [Prev Class](Las2SqlLdr.LasFileStream.md)
- [Next Class](Las2SqlLdr.PointData.MBR.md)

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

## Class Las2SqlLdr.PointData

- java.lang.Object

- - oracle.spatial.util.Las2SqlLdr.PointData

<!-- -->

- Enclosing class:
  [Las2SqlLdr](Las2SqlLdr.md)

  ------------------------------------------------------------------------



      public static class Las2SqlLdr.PointData
      extends java.lang.Object

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                      |
    |-------------------|----------------------------------------------------------------------------|
    | `static class `   | [`Las2SqlLdr.PointData.MBR`](Las2SqlLdr.PointData.MBR.md)                  |
    | `static class `   | [`Las2SqlLdr.PointData.SinglePoint`](Las2SqlLdr.PointData.SinglePoint.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type                                         | Field and Description            |
    |-----------------------------------------------------------|----------------------------------|
    | [`Las2SqlLdr.LasFileStream`](Las2SqlLdr.LasFileStream.md) | `m_lasFileStream`                |
    | `boolean`                                                 | `m_morePointsToReadFromLasFile`  |
    | `long`                                                    | `m_totalSortingTime`             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `PointData``(int pointCapacity, java.lang.String sourceLasFile)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addPoint``(double x, double y, double z, long hilbert)`                                                               |
    | `int`             | `getNumPointsFree``()`                                                                                                 |
    | `int`             | `getNumPointsRemaining``()`                                                                                            |
    | `void`            | `loadMoreFromLas``()`                                                                                                  |
    | `void`            | `subtractPointWithLowestHilbert``(`[`Las2SqlLdr.PointData.SinglePoint`](Las2SqlLdr.PointData.SinglePoint.md)` point)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### m_morePointsToReadFromLasFile

          public boolean m_morePointsToReadFromLasFile

    <!-- -->

    - #### m_lasFileStream

          public final Las2SqlLdr.LasFileStream m_lasFileStream

    <!-- -->

    - #### m_totalSortingTime

          public long m_totalSortingTime

  <!-- -->

  - ### Constructor Detail

    - #### PointData

          public PointData(int pointCapacity,
                           java.lang.String sourceLasFile)
                    throws java.io.IOException

      Throws:
      `java.io.IOException`

  <!-- -->

  - ### Method Detail

    - #### getNumPointsRemaining

          public int getNumPointsRemaining()

    <!-- -->

    - #### getNumPointsFree

          public int getNumPointsFree()

    <!-- -->

    - #### loadMoreFromLas

          public void loadMoreFromLas()
                               throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### addPoint

          public void addPoint(double x,
                               double y,
                               double z,
                               long hilbert)

    <!-- -->

    - #### subtractPointWithLowestHilbert

          public void subtractPointWithLowestHilbert(Las2SqlLdr.PointData.SinglePoint point)

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

- [Prev Class](Las2SqlLdr.LasFileStream.md)
- [Next Class](Las2SqlLdr.PointData.MBR.md)

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
