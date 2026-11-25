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

- [Prev Class](FastJGeometry.FastOp.md)
- [Next Class](J3D_Geometry.md)

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

## Enum FastJGeometry.PPStatus

- java.lang.Object

- - java.lang.Enum\<FastJGeometry.PPStatus\>

  - - oracle.spatial.geometry.FastJGeometry.PPStatus

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<FastJGeometry.PPStatus\>

  <!-- -->

  Enclosing class:
  [FastJGeometry](FastJGeometry.md)

  ------------------------------------------------------------------------



      public static enum FastJGeometry.PPStatus
      extends java.lang.Enum<FastJGeometry.PPStatus>

  Whether a particular operation is PREPROCESSed, should NEVER be preprocessed, or may be AUTOmatcially done at the discretion of the implementation.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `AUTO`                        |
    | `NEVER`                       |
    | `PREPROCESS`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                       |
    |-----------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static FastJGeometry.PPStatus`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static FastJGeometry.PPStatus[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### AUTO

          public static final FastJGeometry.PPStatus AUTO

    <!-- -->

    - #### NEVER

          public static final FastJGeometry.PPStatus NEVER

    <!-- -->

    - #### PREPROCESS

          public static final FastJGeometry.PPStatus PREPROCESS

  <!-- -->

  - ### Method Detail

    - #### values

          public static FastJGeometry.PPStatus[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (FastJGeometry.PPStatus c : FastJGeometry.PPStatus.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static FastJGeometry.PPStatus valueOf(java.lang.String name)

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

- [Prev Class](FastJGeometry.FastOp.md)
- [Next Class](J3D_Geometry.md)

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
