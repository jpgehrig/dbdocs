Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.xquery.xqjdb**

## **Class OXQDDataSource**

- **java.lang.Object**

- - **oracle.xml.xquery.xqjdb.OXQDDataSource**

<!-- -->

- **All Implemented Interfaces:**
  **[XQDataSource](../../../../javax/xml/xquery/XQDataSource.md)**

  ------------------------------------------------------------------------

  **
  **

      public class OXQDDataSource
      extends java.lang.Object
      implements XQDataSource

  **This class is Oracle's concrete implementation of the [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md) interface, for use with Oracle XML DB. The following property names are required to be set via the setProperty method, or other alternative methods of this class in order to specify Oracle XML DB connection info.
  **
  | Property Name | Property Value                                                                   |
  |---------------|----------------------------------------------------------------------------------|
  | driver        | Only jdbc:oracle:thin is supported                                               |
  | dbusername    | Database schema (user) name                                                      |
  | dbpassword    | Password for database schema                                                     |
  | dbserver      | Hostname for database instance                                                   |
  | dbport        | Port number for database instance                                                |
  | dbname        | Database instance name (service id). Either dbname or serviceName should be used |
  | serviceName   | Service name. Either dbname or serviceName should be used                        |

  **
  For example:**
          OXQDDataSource oxqDS = new OXQDDataSource();

          oxqDS.setProperty("driver", "jdbc:oracle:thin");
          oxqDS.setProperty("dbusername", "oe");
          oxqDS.setProperty("dbpassword", "oe");
          oxqDS.setProperty("dbserver", "myMachine");
          oxqDS.setProperty("dbport", "6479");
          oxqDS.setProperty("serviceName", "myservice.oracle.com");


<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                    |
    |--------------------------------------------------------------------------------|
    | `OXQDDataSource``()`<br>Create a new `OXQDataSource` for connecting to XML DB. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                              | Method and Description                                                                                                                              |
    |----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQConnection`](../../../../javax/xml/xquery/XQConnection.md) | `getConnection``()`<br>Create a new `XQConnection` object representing an XQJ connection to Oracle XML DB.                                          |
    | [`XQConnection`](../../../../javax/xml/xquery/XQConnection.md) | `getConnection``(java.sql.Connection con)`<br>This method is not supported.                                                                         |
    | [`XQConnection`](../../../../javax/xml/xquery/XQConnection.md) | `getConnection``(java.lang.String username, java.lang.String passwd)`<br>Same as `getConnection()`.                                                 |
    | `java.lang.String`                                             | `getDBName``()`<br>Get the value of the db name property                                                                                            |
    | `java.lang.String`                                             | `getDBPassword``()`<br>Get the value of the db password property                                                                                    |
    | `java.lang.String`                                             | `getDBPort``()`<br>Get the value of the db port property                                                                                            |
    | `java.lang.String`                                             | `getDBServer``()`<br>Get the value of the db server property                                                                                        |
    | `java.lang.String`                                             | `getDBUserName``()`<br>Get the value of the db user name property                                                                                   |
    | `java.lang.String`                                             | `getDriver``()`<br>Get the value of the driver property                                                                                             |
    | `int`                                                          | `getLoginTimeout``()`<br>Login timeout is not supported by this implementation.                                                                     |
    | `java.io.PrintWriter`                                          | `getLogWriter``()`<br>Log writer is not supported by this implementation.                                                                           |
    | `java.lang.String`                                             | `getProperty``(java.lang.String name)`<br>Gets the value of a supported property returned by `getSupportedPropertyNames()`.                         |
    | `java.lang.String`                                             | `getServiceName``()`<br>Get the value of the service name property                                                                                  |
    | `java.lang.String[]`                                           | `getSupportedPropertyNames``()`<br>Returns all supported property names.                                                                            |
    | `void`                                                         | `setDBName``(java.lang.String dbname)`<br>Set the value of the db name property                                                                     |
    | `void`                                                         | `setDBPassword``(java.lang.String password)`<br>Set the value of the db password property                                                           |
    | `void`                                                         | `setDBPort``(java.lang.String port)`<br>Set the value of the db port property                                                                       |
    | `void`                                                         | `setDBServer``(java.lang.String server)`<br>Set the value of the db server property                                                                 |
    | `void`                                                         | `setDBUserName``(java.lang.String username)`<br>Set the value of the db user name property                                                          |
    | `void`                                                         | `setDriver``(java.lang.String driver)`<br>Set the value of the driver property                                                                      |
    | `void`                                                         | `setLoginTimeout``(int seconds)`<br>This method is not supported.                                                                                   |
    | `void`                                                         | `setLogWriter``(java.io.PrintWriter out)`<br>This method is not supported.                                                                          |
    | `void`                                                         | `setProperties``(java.util.Properties props)`<br>This method is not supported.                                                                      |
    | `void`                                                         | `setProperty``(java.lang.String name, java.lang.String value)`<br>Sets the value of a supported property returned by `getSupportedPropertyNames()`. |
    | `void`                                                         | `setServiceName``(java.lang.String serviceName)`<br>Set the value of the service name property                                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OXQDDataSource

          public OXQDDataSource()

      Create a new `OXQDataSource` for connecting to XML DB.
      Please note that all required connection properties must be set before a connection can be obtained via `getConnection()`.
      The required properties are driver, dbusername, dbpassword, dbserver, dbport, and either dbname or serviceName.

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public XQConnection getConnection()
                                     throws XQException

      Create a new `XQConnection` object representing an XQJ connection to Oracle XML DB.
      Please note that all required connection properties must be set before a connection can be obtained via `getConnection()`.
      The required properties are driver, dbusername, dbpassword, dbserver, dbport, and either dbname or serviceName.
      Specified by:
      [`getConnection`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getConnection

          public XQConnection getConnection(java.sql.Connection con)
                                     throws XQException

      This method is not supported.
      Specified by:
      [`getConnection`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `con` - an existing JDBC connection

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if (1) a datasource access error occurs, (2) the implementation does not support this method of getting an `XQConnection`, or (3) if the `con` parameter is `null`

    <!-- -->

    - #### getConnection

          public XQConnection getConnection(java.lang.String username,
                                            java.lang.String passwd)
                                     throws XQException

      Same as `getConnection()`. The parameters are silently ignored in this implementation.
      Specified by:
      [`getConnection`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `username` - the user on whose behalf the connection is being made

      `passwd` - the user's password

      Returns:
      a connection to the XML datasource

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLoginTimeout

          public int getLoginTimeout()
                              throws XQException

      Login timeout is not supported by this implementation.
      Specified by:
      [`getLoginTimeout`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      the datasource login time limit

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getLogWriter

          public java.io.PrintWriter getLogWriter()
                                           throws XQException

      Log writer is not supported by this implementation.
      Specified by:
      [`getLogWriter`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      the log writer for this datasource or `null` if logging is disabled

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getSupportedPropertyNames

          public java.lang.String[] getSupportedPropertyNames()

      Returns all supported property names. These properties are used for establishing a connection to Oracle XML DB.
      Specified by:
      [`getSupportedPropertyNames`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Returns:
      `String[]` containing supported property names

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String name,
                                  java.lang.String value)
                           throws XQException

      Sets the value of a supported property returned by `getSupportedPropertyNames()`. Properties contain the necessary information for establishing a connection to Oracle XML DB.
      Specified by:
      [`setProperty`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `name` - the name of the property. See `getSupportedPropertyNames()` for all supported properties.

      `value` - the value of the property.

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if (1) the given property is not recognized, (2) the value for the given property is determined to be invalid, or (3) the `name` parameter is `null`

    <!-- -->

    - #### getProperty

          public java.lang.String getProperty(java.lang.String name)
                                       throws XQException

      Gets the value of a supported property returned by `getSupportedPropertyNames()`. Properties contain the necessary information for establishing a connection to Oracle XML DB.
      Specified by:
      [`getProperty`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `name` - the name of the property whose value is needed

      Returns:
      the value of the property.

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if (1) a given property is not supported, or (2) the name parameter is `null`

    <!-- -->

    - #### setProperties

          public void setProperties(java.util.Properties props)
                             throws XQException

      This method is not supported.
      Specified by:
      [`setProperties`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `props` - the list of properties to set

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if (1) a given property is not recognized, (2) the value for a given property is determined to be invalid, or (3) the `props` parameter is `null`

    <!-- -->

    - #### setLoginTimeout

          public void setLoginTimeout(int seconds)
                               throws XQException

      This method is not supported.
      Specified by:
      [`setLoginTimeout`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `seconds` - the datasource login time limit

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### setLogWriter

          public void setLogWriter(java.io.PrintWriter out)
                            throws XQException

      This method is not supported.
      Specified by:
      [`setLogWriter`](../../../../javax/xml/xquery/XQDataSource.md) in interface [`XQDataSource`](../../../../javax/xml/xquery/XQDataSource.md)

      Parameters:
      `out` - the new log writer; to disable logging, set to `null`

      Throws:
      [`XQException`](../../../../javax/xml/xquery/XQException.md) - if a datasource access error occurs

    <!-- -->

    - #### getDriver

          public java.lang.String getDriver()

      Get the value of the driver property
      Returns:
      value of the driver property

    <!-- -->

    - #### setDriver

          public void setDriver(java.lang.String driver)

      Set the value of the driver property
      Parameters:
      `driver` - value of the driver property

    <!-- -->

    - #### getDBUserName

          public java.lang.String getDBUserName()

      Get the value of the db user name property
      Returns:
      value of the db user name property

    <!-- -->

    - #### setDBUserName

          public void setDBUserName(java.lang.String username)

      Set the value of the db user name property
      Parameters:
      `username` - value of the db user name property

    <!-- -->

    - #### getDBPassword

          public java.lang.String getDBPassword()

      Get the value of the db password property
      Returns:
      value of the db password property

    <!-- -->

    - #### setDBPassword

          public void setDBPassword(java.lang.String password)

      Set the value of the db password property
      Parameters:
      `password` - value of the db password property

    <!-- -->

    - #### getDBServer

          public java.lang.String getDBServer()

      Get the value of the db server property
      Returns:
      value of the db server property

    <!-- -->

    - #### setDBServer

          public void setDBServer(java.lang.String server)

      Set the value of the db server property
      Parameters:
      `server` - value of the db server property

    <!-- -->

    - #### getDBPort

          public java.lang.String getDBPort()

      Get the value of the db port property
      Returns:
      value of the db port property

    <!-- -->

    - #### setDBPort

          public void setDBPort(java.lang.String port)

      Set the value of the db port property
      Parameters:
      `port` - value of the db port property

    <!-- -->

    - #### getDBName

          public java.lang.String getDBName()

      Get the value of the db name property
      Returns:
      value of the db name property

    <!-- -->

    - #### setDBName

          public void setDBName(java.lang.String dbname)

      Set the value of the db name property
      Parameters:
      `dbname` - value of the db name property

    <!-- -->

    - #### getServiceName

          public java.lang.String getServiceName()

      Get the value of the service name property
      Returns:
      value of the db name property

    <!-- -->

    - #### setServiceName

          public void setServiceName(java.lang.String serviceName)

      Set the value of the service name property
      Parameters:
      `serviceName` - value of the service name property

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **Next Class**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
