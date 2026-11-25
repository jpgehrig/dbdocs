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

- [Prev Class](TSP.md)
- [Next Class](Tsp2Opt.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Enum TSP.TourFlag

- java.lang.Object

- - java.lang.Enum\<TSP.TourFlag\>

  - - oracle.spatial.network.lod.TSP.TourFlag

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<TSP.TourFlag\>

  <!-- -->

  Enclosing interface:
  [TSP](TSP.md)

  ------------------------------------------------------------------------



      public static enum TSP.TourFlag
      extends java.lang.Enum<TSP.TourFlag>

  Enumeration whose values indicate whether a tsp tour is open or closed, and if open, whether the tour have fixed start and/or end point.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `CLOSED`                      |
    | `OPEN`                        |
    | `OPEN_FIXED_END`              |
    | `OPEN_FIXED_START`            |
    | `OPEN_FIXED_START_END`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                       |
    |-------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static TSP.TourFlag`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static TSP.TourFlag[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### CLOSED

          public static final TSP.TourFlag CLOSED

    <!-- -->

    - #### OPEN

          public static final TSP.TourFlag OPEN

    <!-- -->

    - #### OPEN_FIXED_START

          public static final TSP.TourFlag OPEN_FIXED_START

    <!-- -->

    - #### OPEN_FIXED_END

          public static final TSP.TourFlag OPEN_FIXED_END

    <!-- -->

    - #### OPEN_FIXED_START_END

          public static final TSP.TourFlag OPEN_FIXED_START_END

  <!-- -->

  - ### Method Detail

    - #### values

          public static TSP.TourFlag[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (TSP.TourFlag c : TSP.TourFlag.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static TSP.TourFlag valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

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

- [Prev Class](TSP.md)
- [Next Class](Tsp2Opt.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
