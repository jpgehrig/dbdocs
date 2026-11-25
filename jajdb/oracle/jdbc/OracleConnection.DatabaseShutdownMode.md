Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.DatabaseShutdownMode.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.ConnectionValidation.md)
- [Next Class](OracleConnection.DatabaseStartupMode.md)

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

oracle.jdbc

## Enum OracleConnection.DatabaseShutdownMode

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<OracleConnection.DatabaseShutdownMode\>

  - - oracle.jdbc.OracleConnection.DatabaseShutdownMode

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleConnection.DatabaseShutdownMode\>

  <!-- -->

  Enclosing interface:
  [OracleConnection](OracleConnection.md)

  ------------------------------------------------------------------------



      public static enum OracleConnection.DatabaseShutdownMode
      extends Enum<OracleConnection.DatabaseShutdownMode>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                        |
    |------------------------------------------------------------------------------------------------------|
    | `ABORT`<br>Does not wait for current calls to complete or users to disconnect from the database.     |
    | `CONNECT`<br>Further connects are prohibited.                                                        |
    | `FINAL`<br>Shuts down the database.                                                                  |
    | `IMMEDIATE`<br>Does not wait for current calls to complete or users to disconnect from the database. |
    | `TRANSACTIONAL`<br>Further connects are prohibited and no new transactions are allowed.              |
    | `TRANSACTIONAL_LOCAL`<br>Further connects are prohibited and no new transactions are allowed.        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                 |
    |--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                            | `getMode``()`<br>Implementation detail (for internal use only).                                                                                                                        |
    | `static OracleConnection.DatabaseShutdownMode`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static OracleConnection.DatabaseShutdownMode[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### CONNECT

          public static final OracleConnection.DatabaseShutdownMode CONNECT

      Further connects are prohibited. Waits for users to disconnect from the database.

    <!-- -->

    - #### TRANSACTIONAL

          public static final OracleConnection.DatabaseShutdownMode TRANSACTIONAL

      Further connects are prohibited and no new transactions are allowed. Waits for active transactions to complete.

    <!-- -->

    - #### TRANSACTIONAL_LOCAL

          public static final OracleConnection.DatabaseShutdownMode TRANSACTIONAL_LOCAL

      Further connects are prohibited and no new transactions are allowed. Waits only for local transactions to complete.

    <!-- -->

    - #### IMMEDIATE

          public static final OracleConnection.DatabaseShutdownMode IMMEDIATE

      Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and rolled back.

    <!-- -->

    - #### ABORT

          public static final OracleConnection.DatabaseShutdownMode ABORT

      Does not wait for current calls to complete or users to disconnect from the database. All uncommitted transactions are terminated and are not rolled back. This is the fastest possible way to shut down the database, but the next database startup may require instance recovery. Therefore, this option should be used only in unusual circumstances: if a background process terminates abnormally.

    <!-- -->

    - #### FINAL

          public static final OracleConnection.DatabaseShutdownMode FINAL

      Shuts down the database. Should be used only in the second call to shutdown() after the database is closed and dismounted.

  <!-- -->

  - ### Method Detail

    - #### values

          public static OracleConnection.DatabaseShutdownMode[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OracleConnection.DatabaseShutdownMode c : OracleConnection.DatabaseShutdownMode.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OracleConnection.DatabaseShutdownMode valueOf(String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      [`IllegalArgumentException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if this enum type has no constant with the specified name

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if the argument is null

    <!-- -->

    - #### getMode

          public final int getMode()

      Implementation detail (for internal use only).

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.DatabaseShutdownMode.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.ConnectionValidation.md)
- [Next Class](OracleConnection.DatabaseStartupMode.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
