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

- **Prev Class**
- **[Next Class](PooledXQConnection.md)**

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

## **Interface ConnectionPoolXQDataSource**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ConnectionPoolXQDataSource

  **A factory for `PooledXQConnection` objects. An object that implements this interface will typically be registered with a JNDI based naming service.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                           |
    |-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                         | `getLoginTimeout``()`<br>Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database.                                                                                               |
    | `java.io.PrintWriter`                         | `getLogWriter``()`<br>Retrieves the log writer for this datasource object.                                                                                                                                                       |
    | [`PooledXQConnection`](PooledXQConnection.md) | `getPooledConnection``()`<br>Attempts to establish a physical connection to an XML datasource that can be used as a pooled connection.                                                                                           |
    | [`PooledXQConnection`](PooledXQConnection.md) | `getPooledConnection``(java.lang.String user, java.lang.String password)`<br>Attempts to establish a physical connection to an XML datasource using the supplied username and password, that can be used as a pooled connection. |
    | `java.lang.String`                            | `getProperty``(java.lang.String name)`<br>Returns the current value of the named property if set, else `null`.                                                                                                                   |
    | `java.lang.String[]`                          | `getSupportedPropertyNames``()`<br>Returns an array containing the property names supported by this datasource.                                                                                                                  |
    | `void`                                        | `setLoginTimeout``(int seconds)`<br>Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database.                                                                                   |
    | `void`                                        | `setLogWriter``(java.io.PrintWriter out)`<br>Sets the log writer for this datasource object to the given `java.io.PrintWriter` object.                                                                                           |
    | `void`                                        | `setProperties``(java.util.Properties props)`<br>Sets the data source properties from the specified `Properties` instance.                                                                                                       |
    | `void`                                        | `setProperty``(java.lang.String name, java.lang.String value)`<br>Sets the named property to the specified value.                                                                                                                |

<!-- -->

- - ### Method Detail

    - #### getPooledConnection

          PooledXQConnection getPooledConnection()
                                          throws XQException

      Attempts to establish a physical connection to an XML datasource that can be used as a pooled connection.
      Returns:
      a `PooledXQConnection` object that is a physical connection to the XML datasource that this `ConnectionPoolXQDataSource` object represents

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getPooledConnection

          PooledXQConnection getPooledConnection(java.lang.String user,
                                                 java.lang.String password)
                                          throws XQException

      Attempts to establish a physical connection to an XML datasource using the supplied username and password, that can be used as a pooled connection.
      Parameters:
      `user` - the user on whose behalf the connection is being made

      `password` - the user's password

      Returns:
      a `PooledXQConnection` object that is a physical connection to the XML datasource that this `ConnectionPoolXQDataSource` object represents

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLoginTimeout

          int getLoginTimeout()
                       throws XQException

      Gets the maximum time in seconds that this datasource can wait while attempting to connect to a database. A value of zero means that the timeout is the default system timeout if there is one; otherwise, it means that there is no timeout. When a datasource object is created, the login timeout is initially zero. It is implementation-defined whether the returned login timeout is actually used by the data source implementation.
      Returns:
      the datasource login time limit

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLogWriter

          java.io.PrintWriter getLogWriter()
                                    throws XQException

      Retrieves the log writer for this datasource object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a datasource object is created, the log writer is initially `null`; in other words, the default is for logging to be disabled.
      Returns:
      the log writer for this datasource or `null` if logging is disabled

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getSupportedPropertyNames

          java.lang.String[] getSupportedPropertyNames()

      Returns an array containing the property names supported by this datasource.
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
      [`XQException`](XQException.md) - if (1) the given property is not recognized, or (2) the value for the given property is determined to be invalid

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
      [`XQException`](XQException.md) - if a given property is not supported

    <!-- -->

    - #### setProperties

          void setProperties(java.util.Properties props)
                      throws XQException

      Sets the data source properties from the specified `Properties` instance. Properties set before this call will still apply but those with the same name as any of these properties will be replaced. Properties set after this call also apply and may replace properties set during this call.
      If the implementation does not support one or more of the given property names, or if it can determine that the value given for a specific property is invalid, then an exception is thrown. If an exception is thrown, then no previous value is overwritten. is invalid, then an exception is raised.

      Parameters:
      `props` - the list of properties to set

      Throws:
      [`XQException`](XQException.md) - if (1) a given property is not recognized, or (2) the value for a given property is determined to be invalid

    <!-- -->

    - #### setLoginTimeout

          void setLoginTimeout(int seconds)
                        throws XQException

      Sets the maximum time in seconds that this datasource will wait while attempting to connect to a database. A value of zero specifies that the timeout is the default system timeout if there is one; otherwise, it specifies that there is no timeout. When a datasource object is created, the login timeout is initially zero. It is implementation-defined whether the specified login timeout is actually used by the data source implementation.
      Parameters:
      `seconds` - the datasource login time limit

      Throws:
      [`XQException`](XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### setLogWriter

          void setLogWriter(java.io.PrintWriter out)
                     throws XQException

      Sets the log writer for this datasource object to the given `java.io.PrintWriter` object. The log writer is a character output stream to which all logging and tracing messages for this datasource will be printed. This includes messages printed by the methods of this object, messages printed by methods of other objects manufactured by this object, and so on. When a datasource object is created the log writer is initially `null`; in other words, the default is for logging to be disabled.
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

- **Prev Class**
- **[Next Class](PooledXQConnection.md)**

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
