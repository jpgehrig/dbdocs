Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](AQjmsConnection.md)
- [Next Class](AQjmsConnectionMetaData.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.jms

## Class AQjmsConnectionFactory

- java.lang.Object

- - oracle.jms.AQjmsConnectionFactory

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [ConnectionFactory](../../javax/jms/ConnectionFactory.md), javax.naming.spi.ObjectFactory

  <!-- -->

  Direct Known Subclasses:
  [AQjmsQueueConnectionFactory](AQjmsQueueConnectionFactory.md), [AQjmsTopicConnectionFactory](AQjmsTopicConnectionFactory.md), [AQjmsXAConnectionFactory](AQjmsXAConnectionFactory.md)

  ------------------------------------------------------------------------



      public class AQjmsConnectionFactory
      extends java.lang.Object
      implements javax.naming.spi.ObjectFactory, ConnectionFactory, java.io.Serializable

  This is an Oracle class which implements `javax.jms.ConnectionFactory` and `javax.naming.spi.ObjectFactory`.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                            |
    |------------------------------------------------------------------------|
    | `AQjmsConnectionFactory``()`<br>Constructs a ConnectionFactory object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                                              |
    |-----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Connection`](../../javax/jms/Connection.md) | `createConnection``()`<br>Creates a connection with the default user identity.                                                                                      |
    | [`Connection`](../../javax/jms/Connection.md) | `createConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a connection using the specified user identity.                               |
    | `javax.sql.DataSource`                        | `getDataSource``()`<br>Returns the DataSource property of the connection factory object                                                                             |
    | `java.lang.String`                            | `getJdbcURL``()`<br>Returns the JdbcURL property of the connection factory object                                                                                   |
    | `java.lang.Object`                            | `getObjectInstance``(java.lang.Object obj, javax.naming.Name name, javax.naming.Context nameCtx, java.util.Hashtable environment)`<br>Creates a connection factory. |
    | `java.lang.String`                            | `getUsername``()`<br>Returns the Username property of the connection factory object                                                                                 |
    | `void`                                        | `setDatasource``(javax.sql.DataSource dataSource)`<br>Sets the Datasource property for the connection factory object                                                |
    | `void`                                        | `setJdbcURL``(java.lang.String jdbcURL)`<br>Sets the JdbcURL property for the connection factory object                                                             |
    | `void`                                        | `setPassword``(java.lang.String password)`<br>Sets the Password property for the connection factory object                                                          |
    | `void`                                        | `setUsername``(java.lang.String user)`<br>Sets the Username property for the connection factory object                                                              |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsConnectionFactory

          public AQjmsConnectionFactory()

      Constructs a ConnectionFactory object. Before using the new factory object to create connections, initializes it by setting its properties.

  <!-- -->

  - ### Method Detail

    - #### setJdbcURL

          public void setJdbcURL(java.lang.String jdbcURL)
                          throws JMSException

      Sets the JdbcURL property for the connection factory object
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory object creates connections

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getJdbcURL

          public java.lang.String getJdbcURL()

      Returns the JdbcURL property of the connection factory object
      Returns:
      the JdbcURL property

    <!-- -->

    - #### setUsername

          public void setUsername(java.lang.String user)
                           throws JMSException

      Sets the Username property for the connection factory object
      Parameters:
      `user` - the database user's name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getUsername

          public java.lang.String getUsername()

      Returns the Username property of the connection factory object
      Returns:
      the Username property

    <!-- -->

    - #### setPassword

          public void setPassword(java.lang.String password)
                           throws JMSException

      Sets the Password property for the connection factory object
      Parameters:
      `password` - the database user's password

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### setDatasource

          public void setDatasource(javax.sql.DataSource dataSource)
                             throws JMSException

      Sets the Datasource property for the connection factory object
      Parameters:
      `dataSource` - indicates the database to which the connection factory object creates connections

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getDataSource

          public javax.sql.DataSource getDataSource()

      Returns the DataSource property of the connection factory object
      Returns:
      the DataSource property

    <!-- -->

    - #### getObjectInstance

          public java.lang.Object getObjectInstance(java.lang.Object obj,
                                                    javax.naming.Name name,
                                                    javax.naming.Context nameCtx,
                                                    java.util.Hashtable environment)
                                             throws JMSException

      Creates a connection factory. The connection factory is created using database connection attributes obtained using `name` and `nameCtx`.
      Specified by:
      `getObjectInstance` in interface `javax.naming.spi.ObjectFactory`

      Parameters:
      `obj` - a `javax.naming.Reference` indicating the connection factory class

      `name` - the location containing the database connection attributes

      `nameCtx` - a `javax.naming.directory.DirContext` containing the above location

      `environment` - (not used - parameter required by `javax.naming.spi.ObjectFactory` interface)

      Returns:
      a new connection factory object, or `null` if `obj` is invalid or looking up the provided `name` in the provided `nameCtx` returns a `null` result

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not created for any reason other than those listed above (which result in a `null` return value)

    <!-- -->

    - #### createConnection

          public Connection createConnection()
                                      throws JMSException

      Creates a connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Specified by:
      [`createConnection`](../../javax/jms/ConnectionFactory.md) in interface [`ConnectionFactory`](../../javax/jms/ConnectionFactory.md)

      Returns:
      a newly created connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the connection is not created due to some error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

      Since:
      1.1

    <!-- -->

    - #### createConnection

          public Connection createConnection(java.lang.String userName,
                                             java.lang.String password)
                                      throws JMSException

      Creates a connection using the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Specified by:
      [`createConnection`](../../javax/jms/ConnectionFactory.md) in interface [`ConnectionFactory`](../../javax/jms/ConnectionFactory.md)

      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the connection is not created due to some error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

      Since:
      1.1

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](AQjmsConnection.md)
- [Next Class](AQjmsConnectionMetaData.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
