Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnection.DRCPState.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.DatabaseStartupMode.md)
- [Next Class](OracleConnectionBuilder.md)

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

## Enum OracleConnection.DRCPState

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<OracleConnection.DRCPState\>

  - - oracle.jdbc.OracleConnection.DRCPState

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleConnection.DRCPState\>

  <!-- -->

  Enclosing interface:
  [OracleConnection](OracleConnection.md)

  ------------------------------------------------------------------------



      public static enum OracleConnection.DRCPState
      extends Enum<OracleConnection.DRCPState>

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                                                                  |
    |----------------------------------------------------------------------------------------------------------------|
    | `ATTACHED_EXPLICIT`<br>The connection is attached after making an explict request for a tagged server process. |
    | `ATTACHED_IMPLICIT`<br>The connection is attached after making an implicit request for a server process.       |
    | `DETACHED`<br>The connection is not attached to a server process.                                              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                     | Method and Description                                                                                                                                                                 |
    |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static OracleConnection.DRCPState`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static OracleConnection.DRCPState[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### DETACHED

          public static final OracleConnection.DRCPState DETACHED

      The connection is not attached to a server process.

    <!-- -->

    - #### ATTACHED_IMPLICIT

          public static final OracleConnection.DRCPState ATTACHED_IMPLICIT

      The connection is attached after making an implicit request for a server process.
      An implicit request occurs when a detached connection makes a round trip to the database.

      Note that a connection can remain detached even after calling [`OracleConnection.attachServerConnection()`](OracleConnection.md). attachServerConnection only performs an explict attach when a tag has been set via [`OracleConnection.detachServerConnection(java.lang.String)`](OracleConnection.md) or [`OracleConnection.CONNECTION_PROPERTY_DRCP_TAG_NAME`](OracleConnection.md)

    <!-- -->

    - #### ATTACHED_EXPLICIT

          public static final OracleConnection.DRCPState ATTACHED_EXPLICIT

      The connection is attached after making an explict request for a tagged server process.

  <!-- -->

  - ### Method Detail

    - #### values

          public static OracleConnection.DRCPState[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OracleConnection.DRCPState c : OracleConnection.DRCPState.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OracleConnection.DRCPState valueOf(String name)

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
- [Use](class-use/OracleConnection.DRCPState.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnection.DatabaseStartupMode.md)
- [Next Class](OracleConnectionBuilder.md)

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
