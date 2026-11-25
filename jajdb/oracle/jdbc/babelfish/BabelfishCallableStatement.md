Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishCallableStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](BabelfishConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc.babelfish

## Class BabelfishCallableStatement

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.babelfish.BabelfishGenericProxy](BabelfishGenericProxy.md)

  - - [oracle.jdbc.babelfish.BabelfishStatement](BabelfishStatement.md)

    - - [oracle.jdbc.babelfish.BabelfishPreparedStatement](BabelfishPreparedStatement.md)

      - - oracle.jdbc.babelfish.BabelfishCallableStatement

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class BabelfishCallableStatement
      extends BabelfishPreparedStatement

  Proxy Superclass for java.sql.CallableStatement interface. It is used by the Oracle JDBC proxy library to proxify java.sql.CallableStatement objects to support the auto translation features.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `BabelfishCallableStatement``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getCreator``()`                                                                                                                                                                                                                                                                             |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getDelegate``()`                                                                                                                                                                                                                                                                            |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `post_Methods``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` result)`<br>Post interceptor.                                 |
    | `void`                                                                                                               | `registerOutParameter``(int parameterIndex, int sqlType)`<br>Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int)                                                                                                                               |
    | `void`                                                                                                               | `registerOutParameter``(int parameterIndex, int sqlType, int scale)`<br>Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int, int)                                                                                                               |
    | `void`                                                                                                               | `registerOutParameter``(int parameterIndex, int sqlType, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int, java.lang.String) |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `translateError``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` ex)`<br>Interceptor for translation of errors.   |

    - ### Methods inherited from class oracle.jdbc.babelfish.[BabelfishPreparedStatement](BabelfishPreparedStatement.md)

      [`proxify`](BabelfishPreparedStatement.md)`, `[`setArray`](BabelfishPreparedStatement.md)`, `[`setAsciiStream`](BabelfishPreparedStatement.md)`, `[`setAsciiStream`](BabelfishPreparedStatement.md)`, `[`setAsciiStream`](BabelfishPreparedStatement.md)`, `[`setBigDecimal`](BabelfishPreparedStatement.md)`, `[`setBinaryStream`](BabelfishPreparedStatement.md)`, `[`setBinaryStream`](BabelfishPreparedStatement.md)`, `[`setBinaryStream`](BabelfishPreparedStatement.md)`, `[`setBlob`](BabelfishPreparedStatement.md)`, `[`setBlob`](BabelfishPreparedStatement.md)`, `[`setBlob`](BabelfishPreparedStatement.md)`, `[`setBoolean`](BabelfishPreparedStatement.md)`, `[`setByte`](BabelfishPreparedStatement.md)`, `[`setBytes`](BabelfishPreparedStatement.md)`, `[`setCharacterStream`](BabelfishPreparedStatement.md)`, `[`setCharacterStream`](BabelfishPreparedStatement.md)`, `[`setCharacterStream`](BabelfishPreparedStatement.md)`, `[`setClob`](BabelfishPreparedStatement.md)`, `[`setClob`](BabelfishPreparedStatement.md)`, `[`setClob`](BabelfishPreparedStatement.md)`, `[`setDate`](BabelfishPreparedStatement.md)`, `[`setDate`](BabelfishPreparedStatement.md)`, `[`setDouble`](BabelfishPreparedStatement.md)`, `[`setFloat`](BabelfishPreparedStatement.md)`, `[`setInt`](BabelfishPreparedStatement.md)`, `[`setLong`](BabelfishPreparedStatement.md)`, `[`setNCharacterStream`](BabelfishPreparedStatement.md)`, `[`setNCharacterStream`](BabelfishPreparedStatement.md)`, `[`setNClob`](BabelfishPreparedStatement.md)`, `[`setNClob`](BabelfishPreparedStatement.md)`, `[`setNClob`](BabelfishPreparedStatement.md)`, `[`setNString`](BabelfishPreparedStatement.md)`, `[`setNull`](BabelfishPreparedStatement.md)`, `[`setNull`](BabelfishPreparedStatement.md)`, `[`setObject`](BabelfishPreparedStatement.md)`, `[`setObject`](BabelfishPreparedStatement.md)`, `[`setObject`](BabelfishPreparedStatement.md)`, `[`setRef`](BabelfishPreparedStatement.md)`, `[`setRowId`](BabelfishPreparedStatement.md)`, `[`setShort`](BabelfishPreparedStatement.md)`, `[`setSQLXML`](BabelfishPreparedStatement.md)`, `[`setString`](BabelfishPreparedStatement.md)`, `[`setTime`](BabelfishPreparedStatement.md)`, `[`setTime`](BabelfishPreparedStatement.md)`, `[`setTimestamp`](BabelfishPreparedStatement.md)`, `[`setTimestamp`](BabelfishPreparedStatement.md)`, `[`setUnicodeStream`](BabelfishPreparedStatement.md)`, `[`setURL`](BabelfishPreparedStatement.md)

    <!-- -->

    - ### Methods inherited from class oracle.jdbc.babelfish.[BabelfishStatement](BabelfishStatement.md)

      [`addBatch`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`executeQuery`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### BabelfishCallableStatement

          public BabelfishCallableStatement()

  <!-- -->

  - ### Method Detail

    - #### getCreator

          protected abstract Object getCreator()

      Specified by:

      [`getCreator`](BabelfishPreparedStatement.md) in class [`BabelfishPreparedStatement`](BabelfishPreparedStatement.md)

      Returns:

    <!-- -->

    - #### getDelegate

          protected abstract Object getDelegate()

      Specified by:

      [`getDelegate`](BabelfishPreparedStatement.md) in class [`BabelfishPreparedStatement`](BabelfishPreparedStatement.md)

      Returns:

    <!-- -->

    - #### translateError

          protected Object translateError(Method m,
                                          SQLException ex)
                                   throws SQLException

      Interceptor for translation of errors.
      Overrides:
      [`translateError`](BabelfishPreparedStatement.md) in class [`BabelfishPreparedStatement`](BabelfishPreparedStatement.md)

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### post_Methods

          protected Object post_Methods(Method m,
                                        Object result)

      Post interceptor. sets up the translator in relevant objects required for handling error translation in those objects.
      Overrides:

      [`post_Methods`](BabelfishPreparedStatement.md) in class [`BabelfishPreparedStatement`](BabelfishPreparedStatement.md)

      Returns:

    <!-- -->

    - #### registerOutParameter

          public void registerOutParameter(int parameterIndex,
                                           int sqlType)
                                    throws SQLException

      Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int)
      Parameters:
      `parameterIndex` -

      `sqlType` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`CallableStatement.registerOutParameter(int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_)

    <!-- -->

    - #### registerOutParameter

          public void registerOutParameter(int parameterIndex,
                                           int sqlType,
                                           int scale)
                                    throws SQLException

      Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int, int)
      Parameters:
      `parameterIndex` -

      `sqlType` -

      `scale` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`CallableStatement.registerOutParameter(int, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_int_)

    <!-- -->

    - #### registerOutParameter

          public void registerOutParameter(int parameterIndex,
                                           int sqlType,
                                           String typeName)
                                    throws SQLException

      Translation compliant implementation of java.sql.CallableStatement#registerOutParameter(int, int, java.lang.String)
      Parameters:
      `parameterIndex` -

      `sqlType` -

      `typeName` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`CallableStatement.registerOutParameter(int, int, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_java_lang_String_)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishCallableStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](BabelfishConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
