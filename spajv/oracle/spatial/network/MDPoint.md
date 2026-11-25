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

- [Prev Class](MBR.md)
- [Next Class](NDMTimer.md)

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

oracle.spatial.network

## Interface MDPoint

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  <!-- -->

  All Known Subinterfaces:
  [Node](Node.md)

  ------------------------------------------------------------------------



      public interface MDPoint
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines a mutilple dimension point.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                 |
    |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `double`                                | `distance``(MDPoint pt)`<br>Returns the Cartesian distance to the specified point.                                                     |
    | `double`                                | `geodeticDistanceInMeters``(MDPoint pt)`<br>Returns the geodetic distance to the specified point.                                      |
    | `int`                                   | `getNoOfDims``()`<br>Returns the number of dimensions.                                                                                 |
    | `double[]`                              | `getOrd``()`<br>Returns the ordinates as an array.                                                                                     |
    | `double`                                | `getOrd``(int index)`<br>Gets the specified ordinate.                                                                                  |
    | `int`                                   | `getSrid``()`<br>Returns the SRID.                                                                                                     |
    | `boolean`                               | `inside``(MDPoint pt, double radius)`<br>Checks if the point is inside the specified range represented by the point and the radius.    |
    | `boolean`                               | `inside``(MDPoint low, MDPoint high)`<br>Checks if the point is inside the specified range represented by the low and the high points. |
    | `void`                                  | `setOrd``(int index, double value)`<br>Sets the specified ordinate.                                                                    |
    | `void`                                  | `setSrid``(int srid)`<br>Sets the SRID.                                                                                                |
    | `double[]`                              | `toArray``()`<br>Returns the ordinates in an array.                                                                                    |
    | [`JGeometry`](../geometry/JGeometry.md) | `toGeometry``()`<br>Returns a point geometry (JGeometry).                                                                              |
    | `java.lang.String`                      | `toSDOGeometry``(int srid)`<br>Retunrs a String for constructing a point SDO_GEOMETRY in the database.                                 |

<!-- -->

- - ### Method Detail

    - #### getNoOfDims

          int getNoOfDims()

      Returns the number of dimensions.

    <!-- -->

    - #### getOrd

          double[] getOrd()

      Returns the ordinates as an array.

    <!-- -->

    - #### setOrd

          void setOrd(int index,
                      double value)

      Sets the specified ordinate.
      Parameters:
      `index` - the specified dimension (starting from zero)

      `value` - the value to be set

    <!-- -->

    - #### getOrd

          double getOrd(int index)

      Gets the specified ordinate.
      Parameters:
      `index` - the specified dimension

    <!-- -->

    - #### getSrid

          int getSrid()

      Returns the SRID.

    <!-- -->

    - #### setSrid

          void setSrid(int srid)

      Sets the SRID.
      Parameters:
      `srid` - the SRID of the point

    <!-- -->

    - #### distance

          double distance(MDPoint pt)

      Returns the Cartesian distance to the specified point.
      Parameters:
      `pt` - the specified point

    <!-- -->

    - #### geodeticDistanceInMeters

          double geodeticDistanceInMeters(MDPoint pt)

      Returns the geodetic distance to the specified point.
      Parameters:
      `pt` - the specified point

    <!-- -->

    - #### toArray

          double[] toArray()

      Returns the ordinates in an array.

    <!-- -->

    - #### inside

          boolean inside(MDPoint low,
                         MDPoint high)

      Checks if the point is inside the specified range represented by the low and the high points.
      Parameters:
      `low` - the low point of the range

      `high` - the high point of the range

    <!-- -->

    - #### inside

          boolean inside(MDPoint pt,
                         double radius)

      Checks if the point is inside the specified range represented by the point and the radius.
      Parameters:
      `pt` - the center point of the range

      `radius` - the radius of the range

    <!-- -->

    - #### toGeometry

          JGeometry toGeometry()

      Returns a point geometry (JGeometry).

    <!-- -->

    - #### toSDOGeometry

          java.lang.String toSDOGeometry(int srid)

      Retunrs a String for constructing a point SDO_GEOMETRY in the database.
      Parameters:
      `srid` - the SRID of the point geometry

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

- [Prev Class](MBR.md)
- [Next Class](NDMTimer.md)

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
