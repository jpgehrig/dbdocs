Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](Intersection.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial.interaction

## Enum BinaryInteraction

- java.lang.Object

- - java.lang.Enum\<BinaryInteraction\>

  - - oracle.spatial.network.nfe.model.spatial.interaction.BinaryInteraction

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<BinaryInteraction\>

  ------------------------------------------------------------------------



      public enum BinaryInteraction
      extends java.lang.Enum<BinaryInteraction>

  Defines different types of interactions between two elements

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                      |
    |--------------------------------------------------------------------|
    | `ANY`<br>Any interaction                                           |
    | `CROSS`<br>Two elements crossing                                   |
    | `TOUCH`<br>One element touching any point of another element       |
    | `TOUCH_END_POINT`<br>One element touching one end point of a line  |
    | `TOUCH_MID_POINT`<br>One element touching some mid point of a line |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type            | Method and Description                                                                                       |
    |------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `int`                        | `getOrdinal``()`                                                                                             |
    | `static BinaryInteraction`   | `valueOf``(int value)`                                                                                       |
    | `static BinaryInteraction`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static BinaryInteraction[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### CROSS

          public static final BinaryInteraction CROSS

      Two elements crossing

    <!-- -->

    - #### TOUCH_END_POINT

          public static final BinaryInteraction TOUCH_END_POINT

      One element touching one end point of a line

    <!-- -->

    - #### TOUCH_MID_POINT

          public static final BinaryInteraction TOUCH_MID_POINT

      One element touching some mid point of a line

    <!-- -->

    - #### TOUCH

          public static final BinaryInteraction TOUCH

      One element touching any point of another element

    <!-- -->

    - #### ANY

          public static final BinaryInteraction ANY

      Any interaction

  <!-- -->

  - ### Method Detail

    - #### values

          public static BinaryInteraction[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (BinaryInteraction c : BinaryInteraction.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static BinaryInteraction valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

    <!-- -->

    - #### getOrdinal

          public int getOrdinal()

    <!-- -->

    - #### valueOf

          public static BinaryInteraction valueOf(int value)

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](Intersection.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
