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

- [Prev Class](SDODoubleGeneralPath.md)
- [Next Class](SegY2SqlLdr.md)

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

## Class SdoPointInPolygon

- java.lang.Object

- - oracle.spatial.util.SdoPointInPolygon

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoPointInPolygon
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `SdoPointInPolygon``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                  |
    |-------------------|---------------------------------------------------------|
    | `static void`     | `deregisterPolygon``(int polygonId)`                    |
    | `static int`      | `isWithinPolygon``(int polygonId, double x, double y)`  |
    | `static int`      | `registerPolygon``(java.sql.Struct polygonStruct)`      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoPointInPolygon

          public SdoPointInPolygon()

  <!-- -->

  - ### Method Detail

    - #### registerPolygon

          public static int registerPolygon(java.sql.Struct polygonStruct)

    <!-- -->

    - #### deregisterPolygon

          public static void deregisterPolygon(int polygonId)

    <!-- -->

    - #### isWithinPolygon

          public static int isWithinPolygon(int polygonId,
                                            double x,
                                            double y)

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

- [Prev Class](SDODoubleGeneralPath.md)
- [Next Class](SegY2SqlLdr.md)

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
