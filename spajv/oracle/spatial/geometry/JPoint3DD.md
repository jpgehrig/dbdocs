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

- [Prev Class](JPoint2DD.md)
- [Next Class](LRSGeometryG3D.md)

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

oracle.spatial.geometry

## Class JPoint3DD

- java.lang.Object

- - oracle.spatial.geometry.JPoint3DD

<!-- -->

- Direct Known Subclasses:
  [UnitSphere](UnitSphere.md)

  ------------------------------------------------------------------------



      public class JPoint3DD
      extends java.lang.Object

  Immutable 3D point or vector.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                 |
    |-----------------------------------------------------------------------------|
    | `JPoint3DD``()`<br>Creata the zero vector.                                  |
    | `JPoint3DD``(double x, double y, double z)`<br>Create a 3D point or vector. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                         |
    |--------------------|--------------------------------------------------------------------------------|
    | `static JPoint3DD` | `cross``(JPoint3DD a, JPoint3DD b)`<br>Return the cross product (a x b).       |
    | `static double`    | `dot``(JPoint3DD a, JPoint3DD b)`<br>Return the dot product of two 3D vectors. |
    | `boolean`          | `equals``(java.lang.Object obj)`                                               |
    | `double`           | `getX``()`<br>Get x.                                                           |
    | `double`           | `getY``()`<br>Get y.                                                           |
    | `double`           | `getZ``()`<br>Get z.                                                           |
    | `int`              | `hashCode``()`                                                                 |
    | `boolean`          | `isZero``()`<br>Test if all three values x, y, and z are zero.                 |
    | `double`           | `length``()`<br>Return the length of the vector.                               |
    | `java.lang.String` | `toString``()`                                                                 |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JPoint3DD

          public JPoint3DD()

      Creata the zero vector.

    <!-- -->

    - #### JPoint3DD

          public JPoint3DD(double x,
                           double y,
                           double z)

      Create a 3D point or vector.
      Parameters:
      `x` -

      `y` -

      `z` -

  <!-- -->

  - ### Method Detail

    - #### getX

          public final double getX()

      Get x.
      Returns:
      x value

    <!-- -->

    - #### getY

          public final double getY()

      Get y.
      Returns:
      y value

    <!-- -->

    - #### getZ

          public final double getZ()

      Get z.
      Returns:
      z value

    <!-- -->

    - #### length

          public final double length()

      Return the length of the vector.
      Returns:
      cartesian length

    <!-- -->

    - #### isZero

          public final boolean isZero()

      Test if all three values x, y, and z are zero.
      Returns:
      true if this is the zero vector.

    <!-- -->

    - #### cross

          public static final JPoint3DD cross(JPoint3DD a,
                                              JPoint3DD b)

      Return the cross product (a x b).
      Parameters:
      `a` -

      `b` -

      Returns:
      cross product

    <!-- -->

    - #### dot

          public static final double dot(JPoint3DD a,
                                         JPoint3DD b)

      Return the dot product of two 3D vectors.
      Parameters:
      `a` -

      `b` -

      Returns:
      dot product

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](JPoint2DD.md)
- [Next Class](LRSGeometryG3D.md)

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
