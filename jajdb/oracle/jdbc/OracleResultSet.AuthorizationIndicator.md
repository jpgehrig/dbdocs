Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleResultSet.AuthorizationIndicator.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleResultSet.md)
- [Next Class](OracleResultSetMetaData.md)

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

## Enum OracleResultSet.AuthorizationIndicator

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [java.lang.Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)\<OracleResultSet.AuthorizationIndicator\>

  - - oracle.jdbc.OracleResultSet.AuthorizationIndicator

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Comparable](http://download.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)\<OracleResultSet.AuthorizationIndicator\>

  <!-- -->

  Enclosing interface:
  [OracleResultSet](OracleResultSet.md)

  ------------------------------------------------------------------------



      public static enum OracleResultSet.AuthorizationIndicator
      extends Enum<OracleResultSet.AuthorizationIndicator>

  eXtensible Data Security (XDS) authorization indicator.

<!-- -->

- - ### Enum Constant Summary

    **Enum Constants**

    | Enum Constant and Description                                               |
    |-----------------------------------------------------------------------------|
    | `NONE`<br>The access to the data is authorized.                             |
    | `UNAUTHORIZED`<br>The access to the data isn't authorized (data is hidden). |
    | `UNKNOWN`<br>Part of the value returned for this column may be hidden.      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                 |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static OracleResultSet.AuthorizationIndicator`   | `valueOf``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns the enum constant of this type with the specified name. |
    | `static OracleResultSet.AuthorizationIndicator[]` | `values``()`<br>Returns an array containing the constants of this enum type, in the order they are declared.                                                                           |

    - ### Methods inherited from class java.lang.[Enum](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#clone__)`, `[`compareTo`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#compareTo_E_)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#finalize__)`, `[`getDeclaringClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#getDeclaringClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#hashCode__)`, `[`name`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#name__)`, `[`ordinal`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#ordinal__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#toString__)`, `[`valueOf`](http://download.oracle.com/javase/8/docs/api/java/lang/Enum.html?is-external=true#valueOf_java_lang_Class_java_lang_String_)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Enum Constant Detail

    - #### NONE

          public static final OracleResultSet.AuthorizationIndicator NONE

      The access to the data is authorized. Note that for a table that doesn't have any security attribute the access to the data is always authorized.

    <!-- -->

    - #### UNAUTHORIZED

          public static final OracleResultSet.AuthorizationIndicator UNAUTHORIZED

      The access to the data isn't authorized (data is hidden).
      The authorization indicator is evaluated based on the enabled attribute security policy when the column value is retrieved. If a base table column value is not authorized to the user, a null value will be returned to the application along with the authentication indicator, `AuthorizationIndicator.UNAUTHORIZED`. If there is a column expression on top of the unauthorized base column(s), the evaluated value will be returned to the application along with the `AuthorizationIndicator.UNAUTHORIZED` indicator. Application should examine authorization indicator before interpreting the returned data.

    <!-- -->

    - #### UNKNOWN

          public static final OracleResultSet.AuthorizationIndicator UNKNOWN

      Part of the value returned for this column may be hidden.
      Sometimes, the authorization indicator for a select item cannot be determined due to functionality limitations or performance constrains of the server. For example, this is possible when column expression is involved in the query and the server cannot or would not compute whether the top operator is supposed to be authorized. In such case authorization indicator, `AuthorizationIndicator.UNKNOWN` will be returned to the application and the returned value can be null or not null depending on how the column expression operates on the underlying column value.
      Note that the server can always determine whether an underlying table data column value is authorized to the user. If it is not authorized, a null value is always returned for further column expression evaluation, which can then result in a null or a non-null value. Therefore, if the application sees an "unknown" authorization indictor, it should determine whether or not the returned value should be access. If the query and its column expressions are designed to handle unauthorized nulls from the underlying columns, then the application can use the returned value. Otherwise the application may have to take appropriate actions for the returned value, which be not be the expected results.

  <!-- -->

  - ### Method Detail

    - #### values

          public static OracleResultSet.AuthorizationIndicator[] values()

      Returns an array containing the constants of this enum type, in the order they are declared. This method may be used to iterate over the constants as follows:
          for (OracleResultSet.AuthorizationIndicator c : OracleResultSet.AuthorizationIndicator.values())
              System.out.println(c);

      Returns:
      an array containing the constants of this enum type, in the order they are declared

    <!-- -->

    - #### valueOf

          public static OracleResultSet.AuthorizationIndicator valueOf(String name)

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
- [Use](class-use/OracleResultSet.AuthorizationIndicator.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleResultSet.md)
- [Next Class](OracleResultSetMetaData.md)

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
