Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishPreparedStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishGenericProxy.md)
- [Next Class](BabelfishStatement.md)

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

## Class BabelfishPreparedStatement

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.babelfish.BabelfishGenericProxy](BabelfishGenericProxy.md)

  - - [oracle.jdbc.babelfish.BabelfishStatement](BabelfishStatement.md)

    - - oracle.jdbc.babelfish.BabelfishPreparedStatement

<!-- -->

- Direct Known Subclasses:
  [BabelfishCallableStatement](BabelfishCallableStatement.md)

  ------------------------------------------------------------------------



      public abstract class BabelfishPreparedStatement
      extends BabelfishStatement

  Proxy Superclass for java.sql.PreparedStatement interface. It is used by the Oracle JDBC proxy library to proxify java.sql.PreparedStatement objects to support the auto translation features.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `BabelfishPreparedStatement``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getCreator``()`                                                                                                                                                                                                                                                                                                                                                                          |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getDelegate``()`                                                                                                                                                                                                                                                                                                                                                                         |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `post_Methods``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` result)`<br>Post Methods interceptor.                                                                                                                      |
    | `protected abstract `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `proxify``(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` d, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` creator)`                                                                                                                                                               |
    | `void`                                                                                                               | `setArray``(int parameterIndex, `[`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setArray(int, java.sql.Array)                                                                                                                                                    |
    | `void`                                                                                                               | `setAsciiStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream)                                                                                                                        |
    | `void`                                                                                                               | `setAsciiStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream, int)                                                                                                       |
    | `void`                                                                                                               | `setAsciiStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream, long)                                                                                                     |
    | `void`                                                                                                               | `setBigDecimal``(int parameterIndex, `[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBigDecimal(int, java.math.BigDecimal)                                                                                                                         |
    | `void`                                                                                                               | `setBinaryStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream)                                                                                                                      |
    | `void`                                                                                                               | `setBinaryStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream, int)                                                                                                     |
    | `void`                                                                                                               | `setBinaryStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream, long)                                                                                                   |
    | `void`                                                                                                               | `setBlob``(int parameterIndex, `[`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.sql.Blob)                                                                                                                                                         |
    | `void`                                                                                                               | `setBlob``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.io.InputStream)                                                                                                                                      |
    | `void`                                                                                                               | `setBlob``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.io.InputStream, long)                                                                                                                   |
    | `void`                                                                                                               | `setBoolean``(int parameterIndex, boolean x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBoolean(int, boolean)                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `setByte``(int parameterIndex, byte x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setByte(int, byte)                                                                                                                                                                                                                                                          |
    | `void`                                                                                                               | `setBytes``(int parameterIndex, byte[] x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setBytes(int, byte\[\])                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `setCharacterStream``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader)                                                                                                                          |
    | `void`                                                                                                               | `setCharacterStream``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, int length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader, int)                                                                                                         |
    | `void`                                                                                                               | `setCharacterStream``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader, long)                                                                                                       |
    | `void`                                                                                                               | `setClob``(int parameterIndex, `[`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.sql.Clob)                                                                                                                                                         |
    | `void`                                                                                                               | `setClob``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.io.Reader)                                                                                                                                                |
    | `void`                                                                                                               | `setClob``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.io.Reader, long)                                                                                                                             |
    | `void`                                                                                                               | `setDate``(int parameterIndex, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setDate(int, java.sql.Date)                                                                                                                                                         |
    | `void`                                                                                                               | `setDate``(int parameterIndex, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Translation compliant implementation of java.sql.PreparedStatement#setDate(int, java.sql.Date, java.util.Calendar)                          |
    | `void`                                                                                                               | `setDouble``(int parameterIndex, double x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setDouble(int, double)                                                                                                                                                                                                                                                  |
    | `void`                                                                                                               | `setFloat``(int parameterIndex, float x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setFloat(int, float)                                                                                                                                                                                                                                                      |
    | `void`                                                                                                               | `setInt``(int parameterIndex, int x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setInt(int, int)                                                                                                                                                                                                                                                              |
    | `void`                                                                                                               | `setLong``(int parameterIndex, long x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setLong(int, long)                                                                                                                                                                                                                                                          |
    | `void`                                                                                                               | `setNCharacterStream``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNCharacterStream(int, java.io.Reader)                                                                                                                        |
    | `void`                                                                                                               | `setNCharacterStream``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNCharacterStream(int, java.io.Reader, long)                                                                                                     |
    | `void`                                                                                                               | `setNClob``(int parameterIndex, `[`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.sql.NClob)                                                                                                                                                    |
    | `void`                                                                                                               | `setNClob``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.io.Reader)                                                                                                                                              |
    | `void`                                                                                                               | `setNClob``(int parameterIndex, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.io.Reader, long)                                                                                                                           |
    | `void`                                                                                                               | `setNString``(int parameterIndex, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNString(int, java.lang.String)                                                                                                                                           |
    | `void`                                                                                                               | `setNull``(int parameterIndex, int sqltype)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNull(int, int)                                                                                                                                                                                                                                                      |
    | `void`                                                                                                               | `setNull``(int parameterIndex, int sqltype, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Translation compliant implementation of java.sql.PreparedStatement#setNull(int, int, java.lang.String)                                                                                                                        |
    | `void`                                                                                                               | `setObject``(int parameterIndex, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object)                                                                                                                                             |
    | `void`                                                                                                               | `setObject``(int parameterIndex, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x, int targetSqlType)`<br>Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object, int)                                                                                                                     |
    | `void`                                                                                                               | `setObject``(int parameterIndex, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x, int targetSqlType, int scaleOrLength)`<br>Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object, int, int)                                                                                             |
    | `void`                                                                                                               | `setRef``(int parameterIndex, `[`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setRef(int, java.sql.Ref)                                                                                                                                                              |
    | `void`                                                                                                               | `setRowId``(int parameterIndex, `[`RowId`](http://download.oracle.com/javase/8/docs/api/java/sql/RowId.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setRowId(int, java.sql.RowId)                                                                                                                                                    |
    | `void`                                                                                                               | `setShort``(int parameterIndex, short x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setShort(int, short)                                                                                                                                                                                                                                                      |
    | `void`                                                                                                               | `setSQLXML``(int parameterIndex, `[`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setSQLXML(int, java.sql.SQLXML)                                                                                                                                               |
    | `void`                                                                                                               | `setString``(int parameterIndex, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setString(int, java.lang.String)                                                                                                                                             |
    | `void`                                                                                                               | `setTime``(int parameterIndex, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setTime(int, java.sql.Time)                                                                                                                                                         |
    | `void`                                                                                                               | `setTime``(int parameterIndex, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Translation compliant implementation of java.sql.PreparedStatement#setTime(int, java.sql.Time, java.util.Calendar)                          |
    | `void`                                                                                                               | `setTimestamp``(int parameterIndex, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setTimestamp(int, java.sql.Timestamp)                                                                                                                                |
    | `void`                                                                                                               | `setTimestamp``(int parameterIndex, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Translation compliant implementation of java.sql.PreparedStatement#setTimestamp(int, java.sql.Timestamp, java.util.Calendar) |
    | `void`                                                                                                               | `setUnicodeStream``(int parameterIndex, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int length)`<br>Translation compliant implementation of java.sql.PreparedStatement#setUnicodeStream(int, java.io.InputStream, int)                                                                                                   |
    | `void`                                                                                                               | `setURL``(int parameterIndex, `[`URL`](http://download.oracle.com/javase/8/docs/api/java/net/URL.html?is-external=true)` x)`<br>Translation compliant implementation of java.sql.PreparedStatement#setURL(int, java.net.URL)                                                                                                                                                              |
    | `protected `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)          | `translateError``(`[`Method`](http://download.oracle.com/javase/8/docs/api/java/lang/reflect/Method.html?is-external=true)` m, `[`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)` ex)`<br>Error interceptor.                                                                                                                    |

    - ### Methods inherited from class oracle.jdbc.babelfish.[BabelfishStatement](BabelfishStatement.md)

      [`addBatch`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`execute`](BabelfishStatement.md)`, `[`executeQuery`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)`, `[`executeUpdate`](BabelfishStatement.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### BabelfishPreparedStatement

          public BabelfishPreparedStatement()

  <!-- -->

  - ### Method Detail

    - #### getCreator

          protected abstract Object getCreator()

      Specified by:

      [`getCreator`](BabelfishStatement.md) in class [`BabelfishStatement`](BabelfishStatement.md)

      Returns:

    <!-- -->

    - #### getDelegate

          protected abstract Object getDelegate()

      Specified by:

      [`getDelegate`](BabelfishStatement.md) in class [`BabelfishStatement`](BabelfishStatement.md)

      Returns:

    <!-- -->

    - #### proxify

          protected abstract Object proxify(Object d,
                                            Object creator)

      Specified by:
      [`proxify`](BabelfishStatement.md) in class [`BabelfishStatement`](BabelfishStatement.md)

    <!-- -->

    - #### translateError

          protected Object translateError(Method m,
                                          SQLException ex)
                                   throws SQLException

      Error interceptor. Handles error translation in case of exception
      Overrides:
      [`translateError`](BabelfishStatement.md) in class [`BabelfishStatement`](BabelfishStatement.md)

      Parameters:
      `m` -

      `ex` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### post_Methods

          protected Object post_Methods(Method m,
                                        Object result)

      Post Methods interceptor. Sets the translator in the returning object if the returning object is a child of BabelfishGenericProxy
      Overrides:

      [`post_Methods`](BabelfishStatement.md) in class [`BabelfishStatement`](BabelfishStatement.md)

      Parameters:

      `m` -

      `result` -

      Returns:

    <!-- -->

    - #### setArray

          public void setArray(int parameterIndex,
                               Array x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setArray(int, java.sql.Array)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setArray(int, java.sql.Array)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setArray_int_java_sql_Array_)

    <!-- -->

    - #### setAsciiStream

          public void setAsciiStream(int parameterIndex,
                                     InputStream x)
                              throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setAsciiStream(int, java.io.InputStream)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_)

    <!-- -->

    - #### setAsciiStream

          public void setAsciiStream(int parameterIndex,
                                     InputStream x,
                                     int length)
                              throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setAsciiStream(int, java.io.InputStream, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_int_)

    <!-- -->

    - #### setAsciiStream

          public void setAsciiStream(int parameterIndex,
                                     InputStream x,
                                     long length)
                              throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setAsciiStream(int, java.io.InputStream, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setAsciiStream(int, java.io.InputStream, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_long_)

    <!-- -->

    - #### setBigDecimal

          public void setBigDecimal(int parameterIndex,
                                    BigDecimal x)
                             throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBigDecimal(int, java.math.BigDecimal)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBigDecimal(int, java.math.BigDecimal)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBigDecimal_int_java_math_BigDecimal_)

    <!-- -->

    - #### setBinaryStream

          public void setBinaryStream(int parameterIndex,
                                      InputStream x)
                               throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBinaryStream(int, java.io.InputStream)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_)

    <!-- -->

    - #### setBinaryStream

          public void setBinaryStream(int parameterIndex,
                                      InputStream x,
                                      int length)
                               throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBinaryStream(int, java.io.InputStream, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_int_)

    <!-- -->

    - #### setBinaryStream

          public void setBinaryStream(int parameterIndex,
                                      InputStream x,
                                      long length)
                               throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBinaryStream(int, java.io.InputStream, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBinaryStream(int, java.io.InputStream, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_long_)

    <!-- -->

    - #### setBlob

          public void setBlob(int parameterIndex,
                              Blob x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.sql.Blob)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBlob(int, java.sql.Blob)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_sql_Blob_)

    <!-- -->

    - #### setBlob

          public void setBlob(int parameterIndex,
                              InputStream x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.io.InputStream)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBlob(int, java.io.InputStream)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_io_InputStream_)

    <!-- -->

    - #### setBlob

          public void setBlob(int parameterIndex,
                              InputStream x,
                              long length)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBlob(int, java.io.InputStream, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBlob(int, java.io.InputStream, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_io_InputStream_long_)

    <!-- -->

    - #### setBoolean

          public void setBoolean(int parameterIndex,
                                 boolean x)
                          throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBoolean(int, boolean)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBoolean(int, boolean)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBoolean_int_boolean_)

    <!-- -->

    - #### setByte

          public void setByte(int parameterIndex,
                              byte x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setByte(int, byte)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setByte(int, byte)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setByte_int_byte_)

    <!-- -->

    - #### setBytes

          public void setBytes(int parameterIndex,
                               byte[] x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setBytes(int, byte\[\])
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setBytes(int, byte[])`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBytes_int_byte_A_)

    <!-- -->

    - #### setCharacterStream

          public void setCharacterStream(int parameterIndex,
                                         Reader reader)
                                  throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setCharacterStream(int, java.io.Reader)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_)

    <!-- -->

    - #### setCharacterStream

          public void setCharacterStream(int parameterIndex,
                                         Reader reader,
                                         int length)
                                  throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setCharacterStream(int, java.io.Reader, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_int_)

    <!-- -->

    - #### setCharacterStream

          public void setCharacterStream(int parameterIndex,
                                         Reader reader,
                                         long length)
                                  throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setCharacterStream(int, java.io.Reader, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setCharacterStream(int, java.io.Reader, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_long_)

    <!-- -->

    - #### setClob

          public void setClob(int parameterIndex,
                              Clob x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.sql.Clob)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setClob(int, java.sql.Clob)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_sql_Clob_)

    <!-- -->

    - #### setClob

          public void setClob(int parameterIndex,
                              Reader reader)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.io.Reader)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setClob(int, java.io.Reader)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_io_Reader_)

    <!-- -->

    - #### setClob

          public void setClob(int parameterIndex,
                              Reader reader,
                              long length)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setClob(int, java.io.Reader, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setClob(int, java.io.Reader, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_io_Reader_long_)

    <!-- -->

    - #### setDate

          public void setDate(int parameterIndex,
                              Date x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setDate(int, java.sql.Date)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setDate(int, java.sql.Date)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDate_int_java_sql_Date_)

    <!-- -->

    - #### setDate

          public void setDate(int parameterIndex,
                              Date x,
                              Calendar cal)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setDate(int, java.sql.Date, java.util.Calendar)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setDate(int, java.sql.Date, java.util.Calendar)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDate_int_java_sql_Date_java_util_Calendar_)

    <!-- -->

    - #### setDouble

          public void setDouble(int parameterIndex,
                                double x)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setDouble(int, double)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setDouble(int, double)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDouble_int_double_)

    <!-- -->

    - #### setFloat

          public void setFloat(int parameterIndex,
                               float x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setFloat(int, float)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setFloat(int, float)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setFloat_int_float_)

    <!-- -->

    - #### setInt

          public void setInt(int parameterIndex,
                             int x)
                      throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setInt(int, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setInt(int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setInt_int_int_)

    <!-- -->

    - #### setLong

          public void setLong(int parameterIndex,
                              long x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setLong(int, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setLong(int, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setLong_int_long_)

    <!-- -->

    - #### setNCharacterStream

          public void setNCharacterStream(int parameterIndex,
                                          Reader reader)
                                   throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNCharacterStream(int, java.io.Reader)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNCharacterStream(int, java.io.Reader)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNCharacterStream_int_java_io_Reader_)

    <!-- -->

    - #### setNCharacterStream

          public void setNCharacterStream(int parameterIndex,
                                          Reader reader,
                                          long length)
                                   throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNCharacterStream(int, java.io.Reader, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNCharacterStream(int, java.io.Reader, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNCharacterStream_int_java_io_Reader_long_)

    <!-- -->

    - #### setNClob

          public void setNClob(int parameterIndex,
                               NClob x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.sql.NClob)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNClob(int, java.sql.NClob)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_sql_NClob_)

    <!-- -->

    - #### setNClob

          public void setNClob(int parameterIndex,
                               Reader reader)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.io.Reader)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNClob(int, java.io.Reader)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_io_Reader_)

    <!-- -->

    - #### setNClob

          public void setNClob(int parameterIndex,
                               Reader reader,
                               long length)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNClob(int, java.io.Reader, long)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNClob(int, java.io.Reader, long)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_io_Reader_long_)

    <!-- -->

    - #### setNString

          public void setNString(int parameterIndex,
                                 String x)
                          throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNString(int, java.lang.String)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNString(int, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNString_int_java_lang_String_)

    <!-- -->

    - #### setNull

          public void setNull(int parameterIndex,
                              int sqltype)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNull(int, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNull(int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNull_int_int_)

    <!-- -->

    - #### setNull

          public void setNull(int parameterIndex,
                              int sqltype,
                              String typeName)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setNull(int, int, java.lang.String)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setNull(int, int, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNull_int_int_java_lang_String_)

    <!-- -->

    - #### setObject

          public void setObject(int parameterIndex,
                                Object x)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setObject(int, java.lang.Object)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_)

    <!-- -->

    - #### setObject

          public void setObject(int parameterIndex,
                                Object x,
                                int targetSqlType)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setObject(int, java.lang.Object, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_int_)

    <!-- -->

    - #### setObject

          public void setObject(int parameterIndex,
                                Object x,
                                int targetSqlType,
                                int scaleOrLength)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setObject(int, java.lang.Object, int, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setObject(int, java.lang.Object, int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_int_int_)

    <!-- -->

    - #### setRef

          public void setRef(int parameterIndex,
                             Ref x)
                      throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setRef(int, java.sql.Ref)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setRef(int, java.sql.Ref)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setRef_int_java_sql_Ref_)

    <!-- -->

    - #### setRowId

          public void setRowId(int parameterIndex,
                               RowId x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setRowId(int, java.sql.RowId)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setRowId(int, java.sql.RowId)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setRowId_int_java_sql_RowId_)

    <!-- -->

    - #### setShort

          public void setShort(int parameterIndex,
                               short x)
                        throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setShort(int, short)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setShort(int, short)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setShort_int_short_)

    <!-- -->

    - #### setSQLXML

          public void setSQLXML(int parameterIndex,
                                SQLXML x)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setSQLXML(int, java.sql.SQLXML)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setSQLXML(int, java.sql.SQLXML)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setSQLXML_int_java_sql_SQLXML_)

    <!-- -->

    - #### setString

          public void setString(int parameterIndex,
                                String x)
                         throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setString(int, java.lang.String)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setString(int, java.lang.String)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setString_int_java_lang_String_)

    <!-- -->

    - #### setTime

          public void setTime(int parameterIndex,
                              Time x)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setTime(int, java.sql.Time)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setTime(int, java.sql.Time)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTime_int_java_sql_Time_)

    <!-- -->

    - #### setTime

          public void setTime(int parameterIndex,
                              Time x,
                              Calendar cal)
                       throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setTime(int, java.sql.Time, java.util.Calendar)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setTime(int, java.sql.Time, java.util.Calendar)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTime_int_java_sql_Time_java_util_Calendar_)

    <!-- -->

    - #### setTimestamp

          public void setTimestamp(int parameterIndex,
                                   Timestamp x)
                            throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setTimestamp(int, java.sql.Timestamp)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setTimestamp(int, java.sql.Timestamp)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTimestamp_int_java_sql_Timestamp_)

    <!-- -->

    - #### setTimestamp

          public void setTimestamp(int parameterIndex,
                                   Timestamp x,
                                   Calendar cal)
                            throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setTimestamp(int, java.sql.Timestamp, java.util.Calendar)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setTimestamp(int, java.sql.Timestamp, java.util.Calendar)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTimestamp_int_java_sql_Timestamp_java_util_Calendar_)

    <!-- -->

    - #### setUnicodeStream

          public void setUnicodeStream(int parameterIndex,
                                       InputStream x,
                                       int length)
                                throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setUnicodeStream(int, java.io.InputStream, int)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setUnicodeStream(int, java.io.InputStream, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setUnicodeStream_int_java_io_InputStream_int_)

    <!-- -->

    - #### setURL

          public void setURL(int parameterIndex,
                             URL x)
                      throws SQLException

      Translation compliant implementation of java.sql.PreparedStatement#setURL(int, java.net.URL)
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      [`PreparedStatement.setURL(int, java.net.URL)`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setURL_int_java_net_URL_)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BabelfishPreparedStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BabelfishGenericProxy.md)
- [Next Class](BabelfishStatement.md)

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
