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

- [Prev Class](GML3.md)
- [Next Class](GML3g.md)

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

oracle.spatial.util

## Enum GML3.GMLVersion

- java.lang.Object

- - java.lang.Enum\<GML3.GMLVersion\>

  - - oracle.spatial.util.GML3.GMLVersion

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<GML3.GMLVersion\>

  <!-- -->

  Enclosing class:
  [GML3](GML3.md)

  ------------------------------------------------------------------------



      public static enum GML3.GMLVersion
      extends java.lang.Enum<GML3.GMLVersion>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `GML3_1_1`                    |
    | `GML3_2_1`                    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type          | Method and Description                                                                                       |
    |----------------------------|--------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`         | `getNamespace``()`                                                                                           |
    | `static GML3.GMLVersion`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static GML3.GMLVersion[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### GML3_1_1

          public static final GML3.GMLVersion GML3_1_1

    <!-- -->

    - #### GML3_2_1

          public static final GML3.GMLVersion GML3_2_1

  <!-- -->

  - ### Method Detail

    - #### values

          public static GML3.GMLVersion[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (GML3.GMLVersion c : GML3.GMLVersion.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static GML3.GMLVersion valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

    <!-- -->

    - #### getNamespace

          public java.lang.String getNamespace()

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

- [Prev Class](GML3.md)
- [Next Class](GML3g.md)

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
