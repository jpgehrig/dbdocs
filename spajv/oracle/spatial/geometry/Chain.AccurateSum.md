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

- [Prev Class](Chain.md)
- [Next Class](Chain.CenterPoint.md)

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

## Class Chain.AccurateSum

- java.lang.Object

- - oracle.spatial.geometry.Chain.AccurateSum

<!-- -->

- Enclosing class:
  [Chain](Chain.md)

  ------------------------------------------------------------------------



      public static final class Chain.AccurateSum
      extends java.lang.Object

  Accurately accumulate a summation. This is an implementation of the Kahan summation algorithm a.k.a. compensated summation.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AccurateSum``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                      |
    |-------------------|---------------------------------------------|
    | `void`            | `add``(double v)`<br>Add to the running sum |
    | `double`          | `get``()`<br>Return the accumulated sum     |
    | `void`            | `reset``()`<br>Reset the sum to zero        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AccurateSum

          public AccurateSum()

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Reset the sum to zero

    <!-- -->

    - #### add

          public void add(double v)

      Add to the running sum
      Parameters:
      `v` - the value to add

    <!-- -->

    - #### get

          public double get()

      Return the accumulated sum
      Returns:
      the sum

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

- [Prev Class](Chain.md)
- [Next Class](Chain.CenterPoint.md)

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
