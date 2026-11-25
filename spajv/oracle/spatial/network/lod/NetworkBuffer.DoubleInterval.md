Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkBuffer.md)
- [Next Class](NetworkBuffer.Elements.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class NetworkBuffer.DoubleInterval

- java.lang.Object

- - oracle.spatial.network.lod.NetworkBuffer.DoubleInterval

<!-- -->

- Enclosing class:
  [NetworkBuffer](NetworkBuffer.md)

  ------------------------------------------------------------------------



      public static class NetworkBuffer.DoubleInterval
      extends java.lang.Object

  This class defines a double interval.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                   |
    |-------------------------------------------------------------------------------|
    | `DoubleInterval``(double start, double end)`<br>Constructs a double interval. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                             |
    |-------------------|----------------------------------------------------------------------------------------------------|
    | `double`          | `getEnd``()`<br>Returns the end value of the interval.                                             |
    | `double`          | `getStart``()`<br>Returns the start value of the interval.                                         |
    | `boolean`         | `isBackward``()`                                                                                   |
    | `boolean`         | `isForward``()`<br>Returns true if the end value is greater than the start value; false otherwise. |
    | `boolean`         | `isPoint``()`                                                                                      |
    | `double`          | `length``()`<br>Returns the length of the interval.                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DoubleInterval

          public DoubleInterval(double start,
                                double end)

      Constructs a double interval.
      Parameters:
      `start` -

      `end` -

  <!-- -->

  - ### Method Detail

    - #### getStart

          public double getStart()

      Returns the start value of the interval.
      Returns:

    <!-- -->

    - #### getEnd

          public double getEnd()

      Returns the end value of the interval.
      Returns:

    <!-- -->

    - #### length

          public double length()

      Returns the length of the interval.
      Returns:

    <!-- -->

    - #### isForward

          public boolean isForward()

      Returns true if the end value is greater than the start value; false otherwise.
      Returns:

    <!-- -->

    - #### isBackward

          public boolean isBackward()

    <!-- -->

    - #### isPoint

          public boolean isPoint()

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkBuffer.md)
- [Next Class](NetworkBuffer.Elements.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
