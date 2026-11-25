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

- [Prev Class](ServiceUpEvent.md)
- [Next Class](ServiceUpEvent.Reason.md)

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

## Enum ServiceUpEvent.EventKind

- java.lang.Object

- - java.lang.Enum\<ServiceUpEvent.EventKind\>

  - - oracle.simplefan.ServiceUpEvent.EventKind

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Comparable\<ServiceUpEvent.EventKind\>

  <!-- -->

  Enclosing class:
  [ServiceUpEvent](ServiceUpEvent.md)

  ------------------------------------------------------------------------



      public static enum ServiceUpEvent.EventKind
      extends java.lang.Enum<ServiceUpEvent.EventKind>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description |
    |-------------------------------|
    | `BOTH`                        |
    | `COMPOSITE`                   |
    | `MEMBER`                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                       |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------|
    | `static ServiceUpEvent.EventKind`   | `valueOf``(java.lang.String name)`<br>Returns the enum constant of this type with the specified name.        |
    | `static ServiceUpEvent.EventKind[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared. |

    - ### Methods inherited from class java.lang.Enum

      `compareTo, equals, getDeclaringClass, hashCode, name, ordinal, toString, valueOf`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Enum Constant Detail

    - #### MEMBER

          public static final ServiceUpEvent.EventKind MEMBER

    <!-- -->

    - #### COMPOSITE

          public static final ServiceUpEvent.EventKind COMPOSITE

    <!-- -->

    - #### BOTH

          public static final ServiceUpEvent.EventKind BOTH

  <!-- -->

  - ### Method Detail

    - #### values

          public static ServiceUpEvent.EventKind[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (ServiceUpEvent.EventKind c : ServiceUpEvent.EventKind.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static ServiceUpEvent.EventKind valueOf(java.lang.String name)

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

- [Prev Class](ServiceUpEvent.md)
- [Next Class](ServiceUpEvent.Reason.md)

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
