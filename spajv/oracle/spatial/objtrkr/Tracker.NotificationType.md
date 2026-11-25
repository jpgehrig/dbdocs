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

- [Prev Class](Tracker.Callback.md)
- [Next Class](Tracker.WorkerType.md)

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

## Enum Tracker.NotificationType

- java.lang.Object

- - java.lang.Enum\<Tracker.NotificationType\>

  - - oracle.spatial.objtrkr.Tracker.NotificationType

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<Tracker.NotificationType\>

  <!-- -->

  Enclosing class:
  [Tracker](Tracker.md)

  ------------------------------------------------------------------------



      public static enum Tracker.NotificationType
      extends java.lang.Enum<Tracker.NotificationType>

  The type of notifications that can be subscribed to

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `INSIDE`                      |
    | `OUTSIDE`                     |
    | `TRANSITION`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                       |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static Tracker.NotificationType`   | `get``(java.lang.String stateString)`<br>Convert a state string from database into INSIDE/OUTSIDE.           |
    | `char`                              | `getDbNotification``()`<br>The database command to get this type of notification                             |
    | `java.lang.String`                  | `getStateString``()`<br>The state string in a notification that corresponds to this state.                   |
    | `static Tracker.NotificationType`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static Tracker.NotificationType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### INSIDE

          public static final Tracker.NotificationType INSIDE

    <!-- -->

    - #### OUTSIDE

          public static final Tracker.NotificationType OUTSIDE

    <!-- -->

    - #### TRANSITION

          public static final Tracker.NotificationType TRANSITION

  <!-- -->

  - ### Method Detail

    - #### values

          public static Tracker.NotificationType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (Tracker.NotificationType c : Tracker.NotificationType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static Tracker.NotificationType valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

    <!-- -->

    - #### getDbNotification

          public char getDbNotification()

      The database command to get this type of notification
      Returns:
      a character to be passed to the database

    <!-- -->

    - #### getStateString

          public java.lang.String getStateString()

      The state string in a notification that corresponds to this state.
      Returns:
      the notification string from the database, or NULL for transition (database returns inside or outside only)

    <!-- -->

    - #### get

          public static Tracker.NotificationType get(java.lang.String stateString)

      Convert a state string from database into INSIDE/OUTSIDE.
      Parameters:
      `stateString` - the string to convert

      Returns:
      the corresponding enum

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

- [Prev Class](Tracker.Callback.md)
- [Next Class](Tracker.WorkerType.md)

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
