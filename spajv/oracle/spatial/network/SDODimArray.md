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

- [Prev Class](Path.md)
- [Next Class](SubPath.md)

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

## Class SDODimArray

- java.lang.Object

- - oracle.spatial.network.SDODimArray

<!-- -->

-

  ------------------------------------------------------------------------



      public class SDODimArray
      extends java.lang.Object

  This class defines a Java representation for Oracle Spatial SDO_DIM_ARRAY object. An SDO_DIM_ARRAY is an array of SDO_DIM_ELEMENT which has the following attributes: SDO_DIMNAME, SDO_LB,SDO_UB, and SDO_TOLERANCE.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SDODimArray``(int noOfDims, double lowerBound, double upperBound, double tolerance)`<br>Constructs an SDODimArray object with the default dimension names ("X","Y","Z","M") and the given lower bounds, upper bounds ,and tolerances. |
    | `SDODimArray``(java.lang.String[] names, double[] lowerBounds, double[] upperBounds, double[] tolerances)`<br>Constructs an SDODimArray object.                                                                                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                     |
    |--------------------|--------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getDimName``(int index)`<br>Returns the specified dimension name.                         |
    | `double`           | `getLowerBound``(int index)`<br>Returns the specified lower bound.                         |
    | `int`              | `getNoOfDims``()`<br>Returns the number of dimensions.                                     |
    | `double`           | `getTolerance``(int index)`<br>Returns the specified tolerance                             |
    | `double`           | `getUpperBound``(int index)`<br>Returns the specified upper bound.                         |
    | `java.lang.String` | `toSQLString``()`<br>Returns a SQL string for constructing a database SDO_DIM_ARRAY object |
    | `java.lang.String` | `toString``()`                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SDODimArray

          public SDODimArray(java.lang.String[] names,
                             double[] lowerBounds,
                             double[] upperBounds,
                             double[] tolerances)

      Constructs an SDODimArray object.
      Parameters:
      `names` - the dimension names

      `lowerBounds` - the lower bounds for each dimension

      `upperBounds` - the upper bounds for each dimension

      `tolerances` - the tolerances for each dimension

    <!-- -->

    - #### SDODimArray

          public SDODimArray(int noOfDims,
                             double lowerBound,
                             double upperBound,
                             double tolerance)

      Constructs an SDODimArray object with the default dimension names ("X","Y","Z","M") and the given lower bounds, upper bounds ,and tolerances.
      Parameters:
      `noOfDims` - the number of dimensions

      `lowerBound` - the lower bound for each dimension

      `upperBound` - the upper bound for each dimension

      `tolerance` - the tolerance for each dimension

  <!-- -->

  - ### Method Detail

    - #### getNoOfDims

          public int getNoOfDims()

      Returns the number of dimensions.

    <!-- -->

    - #### getDimName

          public java.lang.String getDimName(int index)

      Returns the specified dimension name.

    <!-- -->

    - #### getUpperBound

          public double getUpperBound(int index)

      Returns the specified upper bound.

    <!-- -->

    - #### getLowerBound

          public double getLowerBound(int index)

      Returns the specified lower bound.

    <!-- -->

    - #### getTolerance

          public double getTolerance(int index)

      Returns the specified tolerance

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### toSQLString

          public java.lang.String toSQLString()

      Returns a SQL string for constructing a database SDO_DIM_ARRAY object

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

- [Prev Class](Path.md)
- [Next Class](SubPath.md)

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
