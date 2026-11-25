Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQDataFactory.md)**
- **[Next Class](XQDynamicContext.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.xquery**

## **Interface XQDataSource**

- **All Known Implementing Classes:**
  **[OXQDataSource](../../../oracle/xml/xquery/OXQDataSource.md), [OXQDDataSource](../../../oracle/xml/xquery/xqjdb/OXQDDataSource.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQDataSource

  **An `XQDataSource` is a factory for `XQConnection` objects. The datasource may be obtained from a JNDI source or through other means.
  The XQuery connection (`XQConnection`) objects may be created using an existing JDBC connection. This is an optional feature that may not be supported by all implementations. If the implementation supports this mechanism, then the XQuery connection may inherit some of the JDBC connection's properties, such as login timeout, log writer etc.
  **

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                     |
    |-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQConnection`](XQConnection.md) | `getConnection``()`<br>Attempts to create a connection to an XML datasource.                                                                                               |
    | [`XQConnection`](XQConnection.md) | `getConnection``(java.sql.Connection con)`<br>Attempts to create a connection to an XML datasource using an existing JDBC connection.                                      |
    | [`XQConnection`](XQConnection.md) | `getConnection``(java.lang.String username, java.lang.String passwd)`<br>Attempts to establish a connection to an XML datasource using the supplied username and password. |
    | `int`                             | `getLoginTimeout``()`<br>Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database.                                         |
    | `java.io.PrintWriter`             | `getLogWriter``()`<br>Retrieves the log writer for this `XQDataSource` object.                                                                                             |
    | `java.lang.String`                | `getProperty``(java.lang.String name)`<br>Returns the current value of the named property if set, else `null`.                                                             |
    | `java.lang.String[]`              | `getSupportedPropertyNames``()`<br>Returns an array containing the property names supported by this `XQDataSource`.                                                        |
    | `void`                            | `setLoginTimeout``(int seconds)`<br>Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database.                             |
    | `void`                            | `setLogWriter``(java.io.PrintWriter out)`<br>Sets the log writer for this `XQDataSource` object to the given `java.io.PrintWriter` object.                                 |
    | `void`                            | `setProperties``(java.util.Properties props)`<br>Sets the data source properties from the specified `Properties` instance.                                                 |
    | `void`                            | `setProperty``(java.lang.String name, java.lang.String value)`<br>Sets the named property to the specified value.                                                          |

<!-- -->

- - ### Method Detail

    - #### getConnection

          XQConnection getConnection()
                              throws XQException

      Attempts to create a connection to an XML datasource.
      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getConnection

          XQConnection getConnection(java.sql.Connection con)
                              throws XQException

      Attempts to create a connection to an XML datasource using an existing JDBC connection. An XQJ implementation is not required to support this method. If it is not supported, then an exception (`XQException`) is thrown. The XQJ and JDBC connections will operate under the same transaction context.
      Parameters:
      `con` - an existing JDBC connection

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](XQException.md) - if (1) a datasource access error occurs, (2) the implementation does not support this method of getting an `XQConnection`, or (3) if the `con` parameter is `null`

    <!-- -->

    - #### getConnection

          XQConnection getConnection(java.lang.String username,
                                     java.lang.String passwd)
                              throws XQException

      Attempts to establish a connection to an XML datasource using the supplied username and password.
      Parameters:
      `username` - the user on whose behalf the connection is being made

      `passwd` - the user's password

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLoginTimeout

          int getLoginTimeout()
                       throws XQException

      Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database. A value of zero means that the timeout is the default system timeout if there is one; otherwise, it means that there is no timeout. When a XQDataSource object is created, the login timeout is initially zero. It is implementation-defined whether the returned login timeout is actually used by the data source implementation.
      Returns:
      the datasource login time limit

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLogWriter

          java.io.PrintWriter getLogWriter()
                                    throws XQException

      Retrieves the log writer for this `XQDataSource` object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a `XQDataSource` object is created, the log writer is initially `null`; in other words, the default is for logging to be disabled.
      Returns:
      the log writer for this datasource or `null` if logging is disabled

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getSupportedPropertyNames

          java.lang.String[] getSupportedPropertyNames()

      Returns an array containing the property names supported by this `XQDataSource`. Implementations that support user name and password must recognize the user name and password properties listed below.

      |            |                                                |
      |------------|------------------------------------------------|
      | `user`     | the user name to use for creating a connection |
      | `password` | the password to use for creating a connection  |


      Any additional properties are implementation-defined.
      Returns:
      `String[]` an array of property names supported by this implementation

    <!-- -->

    - #### setProperty

          void setProperty(java.lang.String name,
                           java.lang.String value)
                    throws XQException

      Sets the named property to the specified value. If a property with the same name was already set, then this method will override the old value for that property with the new value.
      If the implementation does not support the given property or if it can determine that the value given for this property is invalid, then an exception is thrown. If an exception is thrown, then no previous value is overwritten.

      Parameters:
      `name` - the name of the property to set

      `value` - the value of the named property

      Throws:
      [`XQException`](XQException.md) - if (1) the given property is not recognized, (2) the value for the given property is determined to be invalid, or (3) the `name` parameter is `null`

    <!-- -->

    - #### getProperty

          java.lang.String getProperty(java.lang.String name)
                                throws XQException

      Returns the current value of the named property if set, else `null`. If the implementation does not support the given property then an exception is raised.
      Parameters:
      `name` - the name of the property whose value is needed

      Returns:
      `String` representing the value of the required property if set, else `null`

      Throws:
      [`XQException`](XQException.md) - if (1) a given property is not supported, or (2) the name parameter is `null`

    <!-- -->

    - #### setProperties

          void setProperties(java.util.Properties props)
                      throws XQException

      Sets the data source properties from the specified `Properties` instance. Properties set before this call will still apply but those with the same name as any of these properties will be replaced. Properties set after this call also apply and may replace properties set during this call.
      If the implementation does not support one or more of the given property names, or if it can determine that the value given for a specific property is invalid, then an exception is thrown. If an exception is thrown, then no previous value is overwritten. is invalid, then an exception is raised.

      Parameters:
      `props` - the list of properties to set

      Throws:
      [`XQException`](XQException.md) - if (1) a given property is not recognized, (2) the value for a given property is determined to be invalid, or (3) the `props` parameter is `null`

    <!-- -->

    - #### setLoginTimeout

          void setLoginTimeout(int seconds)
                        throws XQException

      Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database. A value of zero specifies that the timeout is the default system timeout if there is one; otherwise, it specifies that there is no timeout. When a `XQDataSource` object is created, the login timeout is initially zero. It is implementation-defined whether the specified login timeout is actually used by the data source implementation. If the connection is created over an existing JDBC connection, then the login timeout value from the underlying JDBC connection may be used.
      Parameters:
      `seconds` - the datasource login time limit

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### setLogWriter

          void setLogWriter(java.io.PrintWriter out)
                     throws XQException

      Sets the log writer for this `XQDataSource` object to the given `java.io.PrintWriter` object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a `XQDataSource` object is created the log writer is initially `null`; in other words, the default is for logging to be disabled.
      Parameters:
      `out` - the new log writer; to disable logging, set to `null`

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQDataFactory.md)**
- **[Next Class](XQDynamicContext.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
