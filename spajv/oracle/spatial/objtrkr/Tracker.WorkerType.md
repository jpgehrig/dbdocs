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

- [Prev Class](Tracker.NotificationType.md)
- Next Class

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

oracle.spatial.objtrkr

## Enum Tracker.WorkerType

- java.lang.Object

- - java.lang.Enum\<Tracker.WorkerType\>

  - - oracle.spatial.objtrkr.Tracker.WorkerType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<Tracker.WorkerType\>

  <!-- -->

  Enclosing class:
  [Tracker](Tracker.md)

  ------------------------------------------------------------------------



      public static enum Tracker.WorkerType
      extends java.lang.Enum<Tracker.WorkerType>

  Types of worker threads that can be created

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------------------------|
    | `LOCATION_WORKER`<br>A worker that will send queued location information to the database                                                |
    | `NONE`<br>Not a worker thread                                                                                                           |
    | `NOTIFICATION_WORKER`<br>A worker that will send wait for notifications from the database and queue them or process them with callbacks |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                                       |
    |-------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static Tracker.WorkerType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static Tracker.WorkerType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### LOCATION_WORKER

          public static final Tracker.WorkerType LOCATION_WORKER

      A worker that will send queued location information to the database

    <!-- -->

    - #### NOTIFICATION_WORKER

          public static final Tracker.WorkerType NOTIFICATION_WORKER

      A worker that will send wait for notifications from the database and queue them or process them with callbacks

    <!-- -->

    - #### NONE

          public static final Tracker.WorkerType NONE

      Not a worker thread

  <!-- -->

  - ### Method Detail

    - #### values

          public static Tracker.WorkerType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (Tracker.WorkerType c : Tracker.WorkerType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static Tracker.WorkerType valueOf(java.lang.String name)

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

- [Prev Class](Tracker.NotificationType.md)
- Next Class

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
