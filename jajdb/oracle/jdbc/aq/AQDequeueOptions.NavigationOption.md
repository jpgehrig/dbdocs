Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQDequeueOptions.NavigationOption.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQDequeueOptions.DequeueMode.md)
- [Next Class](AQDequeueOptions.VisibilityOption.md)

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

oracle.jdbc.aq

## Enum AQDequeueOptions.NavigationOption

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<AQDequeueOptions.NavigationOption\>

  - - oracle.jdbc.aq.AQDequeueOptions.NavigationOption

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<AQDequeueOptions.NavigationOption\>

  <!-- -->

  Enclosing class:
  [AQDequeueOptions](AQDequeueOptions.md)

  ------------------------------------------------------------------------



      public static enum AQDequeueOptions.NavigationOption
      extends Enum<AQDequeueOptions.NavigationOption>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FIRST_MESSAGE`<br>Retrieve the first available message that matches the search criterion.                                                         |
    | `NEXT_MESSAGE`<br>Retrieve the next available message that matches the search criterion.                                                           |
    | `NEXT_TRANSACTION`<br>Skips the remainder of the current transaction group (if any) and retrieves the first message of the next transaction group. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                 |
    |----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                        | `getCode``()`<br>Implementation detail (for internal use only).                                                                                                                        |
    | `static AQDequeueOptions.NavigationOption`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static AQDequeueOptions.NavigationOption[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### FIRST_MESSAGE

          public static final AQDequeueOptions.NavigationOption FIRST_MESSAGE

      Retrieve the first available message that matches the search criterion. This will reset the position to the beginning of the queue.

    <!-- -->

    - #### NEXT_MESSAGE

          public static final AQDequeueOptions.NavigationOption NEXT_MESSAGE

      Retrieve the next available message that matches the search criterion. If the previous message belongs to a message group, AQ will retrieve the next available message which matches the search criterion and belongs to the message group. This is the default.

    <!-- -->

    - #### NEXT_TRANSACTION

          public static final AQDequeueOptions.NavigationOption NEXT_TRANSACTION

      Skips the remainder of the current transaction group (if any) and retrieves the first message of the next transaction group. This option can only be used if message grouping is enabled for the current queue.

  <!-- -->

  - ### Method Detail

    - #### values

          public static AQDequeueOptions.NavigationOption[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (AQDequeueOptions.NavigationOption c : AQDequeueOptions.NavigationOption.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static AQDequeueOptions.NavigationOption valueOf(String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      [`IllegalArgumentException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if this enum type has no constant with the specified name

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if the argument is null

    <!-- -->

    - #### getCode

          public final int getCode()

      Implementation detail (for internal use only).

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AQDequeueOptions.NavigationOption.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AQDequeueOptions.DequeueMode.md)
- [Next Class](AQDequeueOptions.VisibilityOption.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
