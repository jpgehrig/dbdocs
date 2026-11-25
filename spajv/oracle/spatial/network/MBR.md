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

- [Prev Class](LinkCostFunction.md)
- [Next Class](MDPoint.md)

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

## Interface MBR

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface MBR
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines the Minimum Bounding Rectangle (MBR) interface. An MBR is represented by a low point and a high point.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                       |
    |-----------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `boolean`                               | `contains``(double[] pt)`<br>Checks if the point is contained in the MBR.                                    |
    | `boolean`                               | `contains``(double[] pt, double tolerance)`<br>Checks if the point is contained in the MBR.                  |
    | `boolean`                               | `contains``(MBR mbr)`<br>Checks if the MBR is contained in the specified MBR.                                |
    | `boolean`                               | `contains``(MBR mbr, double tolerance)`<br>Checks if the MBR is contained in the specified MBR.              |
    | `boolean`                               | `contains``(`[`MDPoint`](MDPoint.md)` pt)`<br>Checks if the point is contained in the MBR.                   |
    | `boolean`                               | `contains``(`[`MDPoint`](MDPoint.md)` pt, double tolerance)`<br>Checks if the point is contained in the MBR. |
    | [`MDPoint`](MDPoint.md)                 | `getHigh``()`<br>Returns the high point.                                                                     |
    | `double`                                | `getHigh``(int index)`<br>Returns the specified ordinate from the high point.                                |
    | [`MDPoint`](MDPoint.md)                 | `getLength``()`<br>Returns the lengths in an MDPoint.                                                        |
    | `double`                                | `getLength``(int index)`<br>Returns the length of the specified dimension.                                   |
    | [`MDPoint`](MDPoint.md)                 | `getLow``()`<br>Returns the low point.                                                                       |
    | `double`                                | `getLow``(int index)`<br>Returns the specified ordinate from the low point.                                  |
    | `int`                                   | `getNoOfDims``()`<br>Returns the number of dimensiosns.                                                      |
    | `boolean`                               | `interacts``(MBR mbr)`<br>Checks if the MBR interacts with the specified MBR.                                |
    | `boolean`                               | `interacts``(MBR mbr, double tolerance)`<br>Checks if the MBR interacts with the specified MBR.              |
    | `MBR`                                   | `intersect``(MBR mbr)`<br>Creates a new MBR by intersecting with the specified MBR.                          |
    | `void`                                  | `setHigh``(int index, double high)`<br>Sets the specified ordinate of the high point.                        |
    | `void`                                  | `setHigh``(`[`MDPoint`](MDPoint.md)` high)`<br>Sets the high point.                                          |
    | `void`                                  | `setLow``(int index, double low)`<br>Sets the specified ordinate of the low point.                           |
    | `void`                                  | `setLow``(`[`MDPoint`](MDPoint.md)` low)`<br>Sets the low point.                                             |
    | [`JGeometry`](../geometry/JGeometry.md) | `toGeometry``(int srid)`<br>Return a JGeometry.                                                              |
    | `java.lang.String`                      | `toSDOGeometry``(int srid)`<br>Retunrs a String for constructing an SDO_GEOMETRY in the database.            |
    | `MBR`                                   | `unite``(MBR mbr)`<br>Creates a new MBR by uniting with the specified MBR.                                   |

<!-- -->

- - ### Method Detail

    - #### getNoOfDims

          int getNoOfDims()

      Returns the number of dimensiosns.

    <!-- -->

    - #### getLow

          MDPoint getLow()

      Returns the low point.
      See Also:
      [`MDPoint`](MDPoint.md)

    <!-- -->

    - #### getLow

          double getLow(int index)

      Returns the specified ordinate from the low point.
      Parameters:
      `index` - the specified dimension index (starting from zero)

    <!-- -->

    - #### getHigh

          MDPoint getHigh()

      Returns the high point.
      See Also:
      [`MDPoint`](MDPoint.md)

    <!-- -->

    - #### getHigh

          double getHigh(int index)

      Returns the specified ordinate from the high point.
      Parameters:
      `index` - the specified dimension index (starting from zero)

    <!-- -->

    - #### getLength

          MDPoint getLength()

      Returns the lengths in an MDPoint. Each length represents the length for each dimension.

    <!-- -->

    - #### getLength

          double getLength(int index)

      Returns the length of the specified dimension.
      Parameters:
      `index` - the specified dimension index (starting from zero)

    <!-- -->

    - #### setLow

          void setLow(MDPoint low)

      Sets the low point.
      Parameters:
      `low` - the low point to be set

    <!-- -->

    - #### setLow

          void setLow(int index,
                      double low)

      Sets the specified ordinate of the low point.
      Parameters:
      `index` - the ordinate index

      `low` - the ordinate value to be set

    <!-- -->

    - #### setHigh

          void setHigh(MDPoint high)

      Sets the high point.
      Parameters:
      `high` - the high point to be set

    <!-- -->

    - #### setHigh

          void setHigh(int index,
                       double high)

      Sets the specified ordinate of the high point.
      Parameters:
      `index` - the ordinate index

      `high` - the ordinate value to be set

    <!-- -->

    - #### contains

          boolean contains(MBR mbr,
                           double tolerance)

      Checks if the MBR is contained in the specified MBR.
      Parameters:
      `mbr` - the specified MBR

      `tolerance` - the tolerance value for comparison

    <!-- -->

    - #### contains

          boolean contains(MBR mbr)

      Checks if the MBR is contained in the specified MBR.
      Parameters:
      `mbr` - the specified MBR

    <!-- -->

    - #### contains

          boolean contains(MDPoint pt,
                           double tolerance)

      Checks if the point is contained in the MBR.
      Parameters:
      `pt` - the specified point

      `tolerance` - the tolerance value for comparison

    <!-- -->

    - #### contains

          boolean contains(MDPoint pt)

      Checks if the point is contained in the MBR.
      Parameters:
      `pt` - the specified point

    <!-- -->

    - #### contains

          boolean contains(double[] pt,
                           double tolerance)

      Checks if the point is contained in the MBR.
      Parameters:
      `pt` - the specified point

      `tolerance` - the tolerance value for comparison

    <!-- -->

    - #### contains

          boolean contains(double[] pt)

      Checks if the point is contained in the MBR.
      Parameters:
      `pt` - the specified point

    <!-- -->

    - #### interacts

          boolean interacts(MBR mbr,
                            double tolerance)

      Checks if the MBR interacts with the specified MBR.
      Parameters:
      `mbr` - the specified MBR

      `tolerance` - the tolerance value for comparison

    <!-- -->

    - #### interacts

          boolean interacts(MBR mbr)

      Checks if the MBR interacts with the specified MBR.
      Parameters:
      `mbr` - the specified MBR

    <!-- -->

    - #### intersect

          MBR intersect(MBR mbr)

      Creates a new MBR by intersecting with the specified MBR.
      Parameters:
      `mbr` - the specified MBR

    <!-- -->

    - #### unite

          MBR unite(MBR mbr)

      Creates a new MBR by uniting with the specified MBR.
      Parameters:
      `mbr` - the specified MBR

    <!-- -->

    - #### toSDOGeometry

          java.lang.String toSDOGeometry(int srid)

      Retunrs a String for constructing an SDO_GEOMETRY in the database.
      Parameters:
      `srid` - the SRID of the geometry

    <!-- -->

    - #### toGeometry

          JGeometry toGeometry(int srid)

      Return a JGeometry.
      Parameters:
      `srid` - the SRID of the geometry

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

- [Prev Class](LinkCostFunction.md)
- [Next Class](MDPoint.md)

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
