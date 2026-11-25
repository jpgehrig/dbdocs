Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeEvent.EventType.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeEvent.AdditionalEventType.md)
- [Next Class](DatabaseChangeListener.md)

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

oracle.jdbc.dcn

## Enum DatabaseChangeEvent.EventType

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<DatabaseChangeEvent.EventType\>

  - - oracle.jdbc.dcn.DatabaseChangeEvent.EventType

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<DatabaseChangeEvent.EventType\>

  <!-- -->

  Enclosing class:
  [DatabaseChangeEvent](DatabaseChangeEvent.md)

  ------------------------------------------------------------------------



      public static enum DatabaseChangeEvent.EventType
      extends Enum<DatabaseChangeEvent.EventType>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                          |
    |----------------------------------------------------------------------------------------|
    | `DEREG`<br>Event type: unregistered or timed out.                                      |
    | `NONE`<br>Event type: no further information about the change notification.            |
    | `OBJCHANGE`<br>Event type: Object change notification.                                 |
    | `QUERYCHANGE`<br>Event type: Query change notification.                                |
    | `SHUTDOWN`<br>Event type: instance shutdown.                                           |
    | `SHUTDOWN_ANY`<br>Event type: any instance shutdown - Real Application Clusters (RAC). |
    | `STARTUP`<br>Event type: database startup.                                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                                                                                 |
    |------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                    | `getCode``()`<br>Implementation detail (for internal use only).                                                                                                                        |
    | `static DatabaseChangeEvent.EventType`   | `getEventType``(int code)`<br>Implementation detail (for internal use only).                                                                                                           |
    | `static DatabaseChangeEvent.EventType`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static DatabaseChangeEvent.EventType[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### NONE

          public static final DatabaseChangeEvent.EventType NONE

      Event type: no further information about the change notification.

    <!-- -->

    - #### STARTUP

          public static final DatabaseChangeEvent.EventType STARTUP

      Event type: database startup.

    <!-- -->

    - #### SHUTDOWN

          public static final DatabaseChangeEvent.EventType SHUTDOWN

      Event type: instance shutdown.

    <!-- -->

    - #### SHUTDOWN_ANY

          public static final DatabaseChangeEvent.EventType SHUTDOWN_ANY

      Event type: any instance shutdown - Real Application Clusters (RAC).

    <!-- -->

    - #### DEREG

          public static final DatabaseChangeEvent.EventType DEREG

      Event type: unregistered or timed out.

    <!-- -->

    - #### OBJCHANGE

          public static final DatabaseChangeEvent.EventType OBJCHANGE

      Event type: Object change notification.

    <!-- -->

    - #### QUERYCHANGE

          public static final DatabaseChangeEvent.EventType QUERYCHANGE

      Event type: Query change notification.

  <!-- -->

  - ### Method Detail

    - #### values

          public static DatabaseChangeEvent.EventType[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (DatabaseChangeEvent.EventType c : DatabaseChangeEvent.EventType.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static DatabaseChangeEvent.EventType valueOf(String name)

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

    <!-- -->

    - #### getEventType

          public static final DatabaseChangeEvent.EventType getEventType(int code)

      Implementation detail (for internal use only).

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/DatabaseChangeEvent.EventType.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](DatabaseChangeEvent.AdditionalEventType.md)
- [Next Class](DatabaseChangeListener.md)

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
