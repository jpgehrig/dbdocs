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

- [Prev Class](Intersection.md)
- [Next Class](IntersectionMember.md)

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

## Enum IntersectionLocation

- java.lang.Object

- - java.lang.Enum\<IntersectionLocation\>

  - - oracle.spatial.network.nfe.model.spatial.interaction.IntersectionLocation

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<IntersectionLocation\>

  ------------------------------------------------------------------------



      public enum IntersectionLocation
      extends java.lang.Enum<IntersectionLocation>

  Defines different line locations

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                      |
    |----------------------------------------------------------------------------------------------------|
    | `FIRST_POINT`<br>A line's first point                                                              |
    | `LAST_POINT`<br>A line's last point                                                                |
    | `MID_POINT`<br>Some point in the middle of a line's segment                                        |
    | `SEGMENT_POINT`<br>Some start or end segment point in a line except the start and end line's point |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type                                | Field and Description                                                     |
    |--------------------------------------------------|---------------------------------------------------------------------------|
    | `static java.util.EnumSet<IntersectionLocation>` | `EXTREMEPOINT_INTERSECTIONS`<br>Locations at the extreme points of a line |
    | `static java.util.EnumSet<IntersectionLocation>` | `MIDPOINT_INTERSECTIONS`<br>Locations in middle points of a line          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                       |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static IntersectionLocation`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static IntersectionLocation[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### FIRST_POINT

          public static final IntersectionLocation FIRST_POINT

      A line's first point

    <!-- -->

    - #### LAST_POINT

          public static final IntersectionLocation LAST_POINT

      A line's last point

    <!-- -->

    - #### SEGMENT_POINT

          public static final IntersectionLocation SEGMENT_POINT

      Some start or end segment point in a line except the start and end line's point

    <!-- -->

    - #### MID_POINT

          public static final IntersectionLocation MID_POINT

      Some point in the middle of a line's segment

  <!-- -->

  - ### Field Detail

    - #### EXTREMEPOINT_INTERSECTIONS

          public static final java.util.EnumSet<IntersectionLocation> EXTREMEPOINT_INTERSECTIONS

      Locations at the extreme points of a line

    <!-- -->

    - #### MIDPOINT_INTERSECTIONS

          public static final java.util.EnumSet<IntersectionLocation> MIDPOINT_INTERSECTIONS

      Locations in middle points of a line

  <!-- -->

  - ### Method Detail

    - #### values

          public static IntersectionLocation[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (IntersectionLocation c : IntersectionLocation.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static IntersectionLocation valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- [Prev Class](Intersection.md)
- [Next Class](IntersectionMember.md)

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
