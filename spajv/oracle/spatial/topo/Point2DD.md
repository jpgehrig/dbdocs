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

- [Prev Class](Node.md)
- [Next Class](TopoDataException.md)

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

oracle.spatial.topo

## Class Point2DD

- java.lang.Object

- - oracle.spatial.topo.Point2DD

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class Point2DD
      extends java.lang.Object
      implements java.io.Serializable

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `double`          | `x`                   |
    | `double`          | `y`                   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `Point2DD``()`                    |
    | `Point2DD``(double x, double y)`  |
    | `Point2DD``(Point2DD p)`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                               |
    |--------------------|------------------------------------------------------|
    | `boolean`          | `equals``(Point2DD p)`                               |
    | `boolean`          | `equalsWithinBasin``(Point2DD p)`                    |
    | `boolean`          | `equalsWithinBasin``(Point2DD p, double tolerance)`  |
    | `double[]`         | `getArray``()`                                       |
    | `double`           | `getX``()`                                           |
    | `double`           | `getY``()`                                           |
    | `void`             | `setX``(double x)`                                   |
    | `void`             | `setY``(double y)`                                   |
    | `java.lang.String` | `toString``()`                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### x

          public double x

    <!-- -->

    - #### y

          public double y

  <!-- -->

  - ### Constructor Detail

    - #### Point2DD

          public Point2DD()

    <!-- -->

    - #### Point2DD

          public Point2DD(double x,
                          double y)

    <!-- -->

    - #### Point2DD

          public Point2DD(Point2DD p)

  <!-- -->

  - ### Method Detail

    - #### getArray

          public double[] getArray()

    <!-- -->

    - #### getX

          public double getX()

    <!-- -->

    - #### getY

          public double getY()

    <!-- -->

    - #### setX

          public void setX(double x)

    <!-- -->

    - #### setY

          public void setY(double y)

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### equals

          public boolean equals(Point2DD p)

    <!-- -->

    - #### equalsWithinBasin

          public boolean equalsWithinBasin(Point2DD p)

    <!-- -->

    - #### equalsWithinBasin

          public boolean equalsWithinBasin(Point2DD p,
                                           double tolerance)

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

- [Prev Class](Node.md)
- [Next Class](TopoDataException.md)

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
