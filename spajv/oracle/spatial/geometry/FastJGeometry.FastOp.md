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

- [Prev Class](FastJGeometry.md)
- [Next Class](FastJGeometry.PPStatus.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

oracle.spatial.geometry

## Enum FastJGeometry.FastOp

- java.lang.Object

- - java.lang.Enum\<FastJGeometry.FastOp\>

  - - oracle.spatial.geometry.FastJGeometry.FastOp

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<FastJGeometry.FastOp\>

  <!-- -->

  Enclosing class:
  [FastJGeometry](FastJGeometry.md)

  ------------------------------------------------------------------------



      public static enum FastJGeometry.FastOp
      extends java.lang.Enum<FastJGeometry.FastOp>

  Operations can be accelerated by doing preprocessing beforehand.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `ANYINTERACT`                 |
    | `DISTANCE`                    |
    | `ISINSIDE`                    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                       |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static FastJGeometry.FastOp`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static FastJGeometry.FastOp[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### ANYINTERACT

          public static final FastJGeometry.FastOp ANYINTERACT

    <!-- -->

    - #### DISTANCE

          public static final FastJGeometry.FastOp DISTANCE

    <!-- -->

    - #### ISINSIDE

          public static final FastJGeometry.FastOp ISINSIDE

  <!-- -->

  - ### Method Detail

    - #### values

          public static FastJGeometry.FastOp[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (FastJGeometry.FastOp c : FastJGeometry.FastOp.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static FastJGeometry.FastOp valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- [Prev Class](FastJGeometry.md)
- [Next Class](FastJGeometry.PPStatus.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Enum Constants \| 
- Field \| 
- Method

<!-- -->

- Detail: 
- Enum Constants \| 
- Field \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
