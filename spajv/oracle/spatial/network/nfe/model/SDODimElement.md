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

- [Prev Class](NFEWorkspaceInfo.md)
- Next Class

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

## Class SDODimElement

- java.lang.Object

- - oracle.spatial.network.nfe.model.SDODimElement

<!-- -->

-

  ------------------------------------------------------------------------



      public class SDODimElement
      extends java.lang.Object

  This class contains information regarding a spatial dimension such as boundaries and tolerance.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SDODimElement``(java.lang.String dimName, double lowerBound, double upperBound, double tolerance)`<br>Allocates a new instance initialized with the given values. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                      |
    |--------------------|-----------------------------------------------------------------------------|
    | `SDODimElement`    | `createCopy``()`<br>Returns a copy of the object.                           |
    | `boolean`          | `equals``(java.lang.Object anObj)`                                          |
    | `java.lang.String` | `getDimName``()`<br>Gets the dimension's name                               |
    | `double`           | `getLowerBound``()`<br>Gets the dimension's lower boundary                  |
    | `double`           | `getTolerance``()`<br>Gets the dimension's tolerance value                  |
    | `double`           | `getUpperBound``()`<br>Gets the dimension's upper boundary                  |
    | `void`             | `setDimName``(java.lang.String dimName)`<br>Sets the dimension's name       |
    | `void`             | `setLowerBound``(double lowerBound)`<br>Sets the dimension's lower boundary |
    | `void`             | `setTolerance``(double tolerance)`<br>Sets the dimension's tolerance value  |
    | `void`             | `setUpperBound``(double upperBound)`<br>Sets the dimension's upper boundary |
    | `java.lang.String` | `toString``()`                                                              |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SDODimElement

          public SDODimElement(java.lang.String dimName,
                               double lowerBound,
                               double upperBound,
                               double tolerance)

      Allocates a new instance initialized with the given values.
      Parameters:
      `dimName` - the dimension name

      `lowerBound` - the dimension lower boundary

      `upperBound` - the dimension upper boundary

      `tolerance` - the tolerance

  <!-- -->

  - ### Method Detail

    - #### getDimName

          public java.lang.String getDimName()

      Gets the dimension's name
      Returns:
      the dimension's name

    <!-- -->

    - #### setDimName

          public void setDimName(java.lang.String dimName)

      Sets the dimension's name
      Parameters:
      `dimName` - the dimension's name

    <!-- -->

    - #### getLowerBound

          public double getLowerBound()

      Gets the dimension's lower boundary
      Returns:
      the dimension's lower boundary

    <!-- -->

    - #### setLowerBound

          public void setLowerBound(double lowerBound)

      Sets the dimension's lower boundary
      Parameters:
      `lowerBound` - the dimension's lower boundary

    <!-- -->

    - #### getUpperBound

          public double getUpperBound()

      Gets the dimension's upper boundary
      Returns:
      the dimension's upper boundary

    <!-- -->

    - #### setUpperBound

          public void setUpperBound(double upperBound)

      Sets the dimension's upper boundary
      Parameters:
      `upperBound` - the dimension's upper boundary

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Gets the dimension's tolerance value
      Returns:
      the dimension's tolerance value

    <!-- -->

    - #### setTolerance

          public void setTolerance(double tolerance)

      Sets the dimension's tolerance value
      Parameters:
      `tolerance` - the dimension's tolerance value

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### createCopy

          public SDODimElement createCopy()

      Returns a copy of the object.
      Returns:
      copy of the object

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object anObj)

      Overrides:
      `equals` in class `java.lang.Object`

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

- [Prev Class](NFEWorkspaceInfo.md)
- Next Class

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
