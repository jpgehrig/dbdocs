Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](ServiceDownEvent.EventKind.md)
- [Next Class](ServiceDownEvent.ServiceMemberEvent.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.simplefan

## Enum ServiceDownEvent.Reason

- java.lang.Object

- - java.lang.Enum\<ServiceDownEvent.Reason\>

  - - oracle.simplefan.ServiceDownEvent.Reason

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<ServiceDownEvent.Reason\>

  <!-- -->

  Enclosing class:
  [ServiceDownEvent](ServiceDownEvent.md)

  ------------------------------------------------------------------------



      public static enum ServiceDownEvent.Reason
      extends java.lang.Enum<ServiceDownEvent.Reason>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `AUTOSTART`                   |
    | `BOOT`                        |
    | `DEPENDENCY`                  |
    | `FAILURE`                     |
    | `USER`                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                  | Method and Description                                                                                       |
    |------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static ServiceDownEvent.Reason`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static ServiceDownEvent.Reason[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### FAILURE

          public static final ServiceDownEvent.Reason FAILURE

    <!-- -->

    - #### DEPENDENCY

          public static final ServiceDownEvent.Reason DEPENDENCY

    <!-- -->

    - #### USER

          public static final ServiceDownEvent.Reason USER

    <!-- -->

    - #### AUTOSTART

          public static final ServiceDownEvent.Reason AUTOSTART

    <!-- -->

    - #### BOOT

          public static final ServiceDownEvent.Reason BOOT

  <!-- -->

  - ### Method Detail

    - #### values

          public static ServiceDownEvent.Reason[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (ServiceDownEvent.Reason c : ServiceDownEvent.Reason.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static ServiceDownEvent.Reason valueOf(java.lang.String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      `java.lang.IllegalArgumentException` - if this enum type has no constant with the specified name

      `java.lang.NullPointerException` - if the argument is null

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](ServiceDownEvent.EventKind.md)
- [Next Class](ServiceDownEvent.ServiceMemberEvent.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
