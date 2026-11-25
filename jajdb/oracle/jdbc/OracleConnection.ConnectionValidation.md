Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.ConnectionValidation.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.CommitOption.md)
- [Next Class](OracleConnection.DatabaseShutdownMode.md)

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

## Enum OracleConnection.ConnectionValidation

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<OracleConnection.ConnectionValidation\>

  - - oracle.jdbc.OracleConnection.ConnectionValidation

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleConnection.ConnectionValidation\>

  <!-- -->

  Enclosing interface:
  [OracleConnection](OracleConnection.md)

  ------------------------------------------------------------------------



      public static enum OracleConnection.ConnectionValidation
      extends Enum<OracleConnection.ConnectionValidation>

  Specifiers for how much effort to put into validating a [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true). The amount of effort put into checking should be non-decreasing from NONE (least effort) to COMPLETE (most effort). Exactly what is checked is implementation dependent.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `COMPLETE`<br>everything that can be checked is working.                                                                                              |
    | `LOCAL`<br>`NONE` plus check local resources.                                                                                                         |
    | `NETWORK`<br>`SOCKET` plus the network is intact (network PING).                                                                                      |
    | `NONE`<br>isValid fails only if the [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) is closed. |
    | `SERVER`<br>`NETWORK` plus significant server processes are running.                                                                                  |
    | `SOCKET`<br>`LOCAL` plus the server isn't obviously unreachable (dead socket).                                                                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                 |
    |--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static OracleConnection.ConnectionValidation`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static OracleConnection.ConnectionValidation[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### NONE

          public static final OracleConnection.ConnectionValidation NONE

      isValid fails only if the [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) is closed.

    <!-- -->

    - #### LOCAL

          public static final OracleConnection.ConnectionValidation LOCAL

      `NONE` plus check local resources. Oracle Database same as isUsable.

    <!-- -->

    - #### SOCKET

          public static final OracleConnection.ConnectionValidation SOCKET

      `LOCAL` plus the server isn't obviously unreachable (dead socket). Oracle Database JDBC does a lightweight socket check. (ZLD)

    <!-- -->

    - #### NETWORK

          public static final OracleConnection.ConnectionValidation NETWORK

      `SOCKET` plus the network is intact (network PING). Oracle Database JDBC does a minimum round trip. (OPING)

    <!-- -->

    - #### SERVER

          public static final OracleConnection.ConnectionValidation SERVER

      `NETWORK` plus significant server processes are running. Oracle Database JDBC does "SELECT 'x' FROM DUAL".

    <!-- -->

    - #### COMPLETE

          public static final OracleConnection.ConnectionValidation COMPLETE

      everything that can be checked is working. At least `SERVER`. Oracle Database JDBC same as SERVER.

  <!-- -->

  - ### Method Detail

    - #### values

          public static OracleConnection.ConnectionValidation[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OracleConnection.ConnectionValidation c : OracleConnection.ConnectionValidation.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OracleConnection.ConnectionValidation valueOf(String name)

      Returns the enum constant of this type with the specified name. The string must match *exactly* an identifier used to declare an enum constant in this type. (Extraneous whitespace characters are not permitted.)
      Parameters:
      `name` - the name of the enum constant to be returned.

      Returns:
      the enum constant with the specified name

      Throws:
      [`IllegalArgumentException`](http://download.oracle.com/javase/8/docs/api/java/lang/IllegalArgumentException.html?is-external=true) - if this enum type has no constant with the specified name

      [`NullPointerException`](http://download.oracle.com/javase/8/docs/api/java/lang/NullPointerException.html?is-external=true) - if the argument is null

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.ConnectionValidation.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.CommitOption.md)
- [Next Class](OracleConnection.DatabaseShutdownMode.md)

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
