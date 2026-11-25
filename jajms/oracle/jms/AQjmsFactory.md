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

- [Prev Class](AQjmsException.md)
- [Next Class](AQjmsMapMessage.md)

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

## Class AQjmsFactory

- java.lang.Object

- - oracle.jms.AQjmsFactory

<!-- -->

-

  ------------------------------------------------------------------------



      public class AQjmsFactory
      extends java.lang.Object

  Class `AQjmsFactory` is an adaptor for accessing Oracle JMS administered objects. This class is provider (Oracle) specific and is not a part of standard JMS specifications.
  This class provides methods for looking up connection factories in the Oracle JMS namespace. For each type of connection factory, there are a number of methods available:

  **Methods for Getting Connection Factories**

  |    Connection Factory Type | Caller-Provided Parameters |                                   |                            |                  |     |
  |---------------------------:|:--------------------------:|-----------------------------------|----------------------------|:----------------:|:---:|
  |                Data Source |       XA Data Source       | Data Source + XA Resource Factory | Driver + Host + Port + SID | URL + Properties |     |
  |        `ConnectionFactory` |             X              |                                   | X                          |        X         |     |
  |   `QueueConnectionFactory` |             X              | X                                 | X                          |                  |     |
  |   `TopicConnectionFactory` |             X              | X                                 | X                          |                  |     |
  |      `XAConnectionFactory` |                            | X                                 | X                          |        X         |  X  |
  | `XAQueueConnectionFactory` |             X              | X                                 | X                          |        X         |     |
  | `XATopicConnectionFactory` |             X              | X                                 | X                          |        X         |     |

  This class also provides methods for registering connection factories:

  **Methods for Registering Connection Factories**

  | Connection Type Caller-Provided Parameters | Database Access Caller-Provided Parameters |     |
  |--------------------------------------------|:------------------------------------------:|:---:|
  | Driver + Host + Port + SID                 |              URL + Properties              |     |
  | JDBC Connection                            |                     X                      |  X  |
  | LDAP Environment                           |                     X                      |  X  |

  This class also provides methods for unregistering connection factories:

  **Methods for Unregistering Connection Factories**

  | Connection Type Caller-Provided Parameters |     |
  |--------------------------------------------|:---:|
  | JDBC Connection                            |  X  |
  | LDAP Environment                           |  X  |

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                |
    |------------------------------------------------------------|
    | `AQjmsFactory``()`<br>Creates a new `AQjmsFactory` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                  | Method and Description                                                                                                                                                                                                                                                                                           |
    |------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`ConnectionFactory`](../../javax/jms/ConnectionFactory.md)               | `getConnectionFactory``(javax.sql.DataSource dataSource)`<br>Gets a `ConnectionFactory` using provided datasource.                                                                                                                                                                                               |
    | `static `[`ConnectionFactory`](../../javax/jms/ConnectionFactory.md)               | `getConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets a `ConnectionFactory` using provided URL/properties.                                                                                                                                                                       |
    | `static `[`ConnectionFactory`](../../javax/jms/ConnectionFactory.md)               | `getConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets a `ConnectionFactory` using provided driver/host/port/SID.                                                                                                                      |
    | `static `[`QueueConnectionFactory`](../../javax/jms/QueueConnectionFactory.md)     | `getQueueConnectionFactory``(javax.sql.DataSource dataSource)`<br>Gets a `QueueConnectionFactory` using provided datasource.                                                                                                                                                                                     |
    | `static `[`QueueConnectionFactory`](../../javax/jms/QueueConnectionFactory.md)     | `getQueueConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets a `QueueConnectionFactory` using provided URL/properties.                                                                                                                                                             |
    | `static `[`QueueConnectionFactory`](../../javax/jms/QueueConnectionFactory.md)     | `getQueueConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets a `QueueConnectionFactory` using provided driver/host/port/SID.                                                                                                            |
    | `static `[`TopicConnectionFactory`](../../javax/jms/TopicConnectionFactory.md)     | `getTopicConnectionFactory``(javax.sql.DataSource dataSource)`<br>Gets a `TopicConnectionFactory` using provided datasource.                                                                                                                                                                                     |
    | `static `[`TopicConnectionFactory`](../../javax/jms/TopicConnectionFactory.md)     | `getTopicConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets a `TopicConnectionFactory` using provided URL/properties.                                                                                                                                                             |
    | `static `[`TopicConnectionFactory`](../../javax/jms/TopicConnectionFactory.md)     | `getTopicConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets a `TopicConnectionFactory` using provided driver/host/port/SID.                                                                                                            |
    | `static `[`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)           | `getXAConnectionFactory``(javax.sql.DataSource dataSource, oracle.jms.AQjmsXAResourceFactory xaresFactory)`<br>Gets an `XAConnectionFactory` using provided datasource and XA resource factory.                                                                                                                  |
    | `static `[`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)           | `getXAConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets an `XAConnectionFactory` using provided URL/properties.                                                                                                                                                                  |
    | `static `[`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)           | `getXAConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets an `XAConnectionFactory` using provided driver/host/port/SID.                                                                                                                 |
    | `static `[`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)           | `getXAConnectionFactory``(javax.sql.XADataSource xadataSource)`<br>Gets an `XAConnectionFactory` using provided XA datasource.                                                                                                                                                                                   |
    | `static `[`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md) | `getXAQueueConnectionFactory``(javax.sql.DataSource dataSource, oracle.jms.AQjmsXAResourceFactory xaresFactory)`<br>Gets an `XAQueueConnectionFactory` using provided datasource and XA resource factory.                                                                                                        |
    | `static `[`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md) | `getXAQueueConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets an `XAQueueConnectionFactory` using provided URL/properties.                                                                                                                                                        |
    | `static `[`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md) | `getXAQueueConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets an `XAQueueConnectionFactory` using provided driver/host/port/SID.                                                                                                       |
    | `static `[`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md) | `getXAQueueConnectionFactory``(javax.sql.XADataSource xadataSource)`<br>Gets an `XAQueueConnectionFactory` using provided XA datasource.                                                                                                                                                                         |
    | `static `[`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md) | `getXATopicConnectionFactory``(javax.sql.DataSource dataSource, oracle.jms.AQjmsXAResourceFactory xaresFactory)`<br>Gets an `XATopicConnectionFactory` using provided datasource and XA resource factory.                                                                                                        |
    | `static `[`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md) | `getXATopicConnectionFactory``(java.lang.String jdbcURL, java.util.Properties info)`<br>Gets an `XATopicConnectionFactory` using provided URL/properties.                                                                                                                                                        |
    | `static `[`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md) | `getXATopicConnectionFactory``(java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver)`<br>Gets an `XATopicConnectionFactory` using provided driver/host/port/SID.                                                                                                       |
    | `static `[`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md) | `getXATopicConnectionFactory``(javax.sql.XADataSource xadataSource)`<br>Gets an `XATopicConnectionFactory` using provided XA datasource.                                                                                                                                                                         |
    | `static int`                                                                       | `registerConnectionFactory``(java.sql.Connection connection, java.lang.String connName, java.lang.String jdbcURL, java.util.Properties info, java.lang.String type)`<br>Registers a connection factory to LDAP using provided JDBC connection + URL/properties.                                                  |
    | `static int`                                                                       | `registerConnectionFactory``(java.sql.Connection connection, java.lang.String connName, java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver, java.lang.String type)`<br>Registers a connection factory to LDAP using provided JDBC connection + driver/host/port/SID. |
    | `static int`                                                                       | `registerConnectionFactory``(java.util.Hashtable env, java.lang.String connName, java.lang.String jdbcURL, java.util.Properties info, java.lang.String type)`<br>Registers a connection factory to LDAP using provided environment + URL/properties.                                                             |
    | `static int`                                                                       | `registerConnectionFactory``(java.util.Hashtable env, java.lang.String connName, java.lang.String hostName, java.lang.String oracleSID, int portNumber, java.lang.String driver, java.lang.String type)`<br>Registers a connection factory to LDAP using provided environment + driver/host/port/SID.            |
    | `static int`                                                                       | `unregisterConnectionFactory``(java.sql.Connection connection, java.lang.String connName)`<br>Unregisters a connection factory from LDAP using provided JDBC connection.                                                                                                                                         |
    | `static int`                                                                       | `unregisterConnectionFactory``(java.util.Hashtable env, java.lang.String connName)`<br>Unregisters a connection factory from LDAP using provided environment.                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsFactory

          public AQjmsFactory()

      Creates a new `AQjmsFactory` object.
      Do not use this constructor - do not create `AQjmsFactory` objects. `AQjmsFactory` objects are not required as all of the methods in this class are `static`.

  <!-- -->

  - ### Method Detail

    - #### getConnectionFactory

          public static ConnectionFactory getConnectionFactory(javax.sql.DataSource dataSource)
                                                        throws JMSException

      Gets a `ConnectionFactory` using provided datasource.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      Returns:
      a `ConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not retrieved due to some error.

    <!-- -->

    - #### getConnectionFactory

          public static ConnectionFactory getConnectionFactory(java.lang.String hostName,
                                                               java.lang.String oracleSID,
                                                               int portNumber,
                                                               java.lang.String driver)
                                                        throws JMSException

      Gets a `ConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      a `ConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not retrieved due to some error.

    <!-- -->

    - #### getConnectionFactory

          public static ConnectionFactory getConnectionFactory(java.lang.String jdbcURL,
                                                               java.util.Properties info)
                                                        throws JMSException

      Gets a `ConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      a `ConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not retrieved due to some error.

    <!-- -->

    - #### getQueueConnectionFactory

          public static QueueConnectionFactory getQueueConnectionFactory(javax.sql.DataSource dataSource)
                                                                  throws JMSException

      Gets a `QueueConnectionFactory` using provided datasource.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      Returns:
      a `QueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getQueueConnectionFactory

          public static QueueConnectionFactory getQueueConnectionFactory(java.lang.String hostName,
                                                                         java.lang.String oracleSID,
                                                                         int portNumber,
                                                                         java.lang.String driver)
                                                                  throws JMSException

      Gets a `QueueConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      a `QueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getQueueConnectionFactory

          public static QueueConnectionFactory getQueueConnectionFactory(java.lang.String jdbcURL,
                                                                         java.util.Properties info)
                                                                  throws JMSException

      Gets a `QueueConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      a `QueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getTopicConnectionFactory

          public static TopicConnectionFactory getTopicConnectionFactory(javax.sql.DataSource dataSource)
                                                                  throws JMSException

      Gets a `TopicConnectionFactory` using provided datasource.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      Returns:
      a `TopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getTopicConnectionFactory

          public static TopicConnectionFactory getTopicConnectionFactory(java.lang.String hostName,
                                                                         java.lang.String oracleSID,
                                                                         int portNumber,
                                                                         java.lang.String driver)
                                                                  throws JMSException

      Gets a `TopicConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      a `TopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getTopicConnectionFactory

          public static TopicConnectionFactory getTopicConnectionFactory(java.lang.String jdbcURL,
                                                                         java.util.Properties info)
                                                                  throws JMSException

      Gets a `TopicConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      a `TopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAConnectionFactory

          public static XAConnectionFactory getXAConnectionFactory(javax.sql.XADataSource xadataSource)
                                                            throws JMSException

      Gets an `XAConnectionFactory` using provided XA datasource.
      Parameters:
      `xadataSource` - indicates the database to which the connection factory creates connections

      Returns:
      an `XAConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAConnectionFactory

          public static XAConnectionFactory getXAConnectionFactory(javax.sql.DataSource dataSource,
                                                                   oracle.jms.AQjmsXAResourceFactory xaresFactory)
                                                            throws JMSException

      Gets an `XAConnectionFactory` using provided datasource and XA resource factory.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      `xaresFactory` - `AQjmsXAResourceFactory` used to create customized `XAResource`

      Returns:
      an `XAConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAConnectionFactory

          public static XAConnectionFactory getXAConnectionFactory(java.lang.String hostName,
                                                                   java.lang.String oracleSID,
                                                                   int portNumber,
                                                                   java.lang.String driver)
                                                            throws JMSException

      Gets an `XAConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      an `XAConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAConnectionFactory

          public static XAConnectionFactory getXAConnectionFactory(java.lang.String jdbcURL,
                                                                   java.util.Properties info)
                                                            throws JMSException

      Gets an `XAConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      an `XAConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAQueueConnectionFactory

          public static XAQueueConnectionFactory getXAQueueConnectionFactory(javax.sql.XADataSource xadataSource)
                                                                      throws JMSException

      Gets an `XAQueueConnectionFactory` using provided XA datasource.
      Parameters:
      `xadataSource` - indicates the database to which the connection factory creates connections

      Returns:
      an `XAQueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAQueueConnectionFactory

          public static XAQueueConnectionFactory getXAQueueConnectionFactory(javax.sql.DataSource dataSource,
                                                                             oracle.jms.AQjmsXAResourceFactory xaresFactory)
                                                                      throws JMSException

      Gets an `XAQueueConnectionFactory` using provided datasource and XA resource factory.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      `xaresFactory` - `AQjmsXAResourceFactory` used to create customized `XAResource`

      Returns:
      an `XAQueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAQueueConnectionFactory

          public static XAQueueConnectionFactory getXAQueueConnectionFactory(java.lang.String hostName,
                                                                             java.lang.String oracleSID,
                                                                             int portNumber,
                                                                             java.lang.String driver)
                                                                      throws JMSException

      Gets an `XAQueueConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      an `XAQueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXAQueueConnectionFactory

          public static XAQueueConnectionFactory getXAQueueConnectionFactory(java.lang.String jdbcURL,
                                                                             java.util.Properties info)
                                                                      throws JMSException

      Gets an `XAQueueConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      an `XAQueueConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA queue connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXATopicConnectionFactory

          public static XATopicConnectionFactory getXATopicConnectionFactory(javax.sql.XADataSource xadataSource)
                                                                      throws JMSException

      Gets an `XATopicConnectionFactory` using provided XA datasource.
      Parameters:
      `xadataSource` - indicates the database to which the connection factory creates connections

      Returns:
      an `XATopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXATopicConnectionFactory

          public static XATopicConnectionFactory getXATopicConnectionFactory(javax.sql.DataSource dataSource,
                                                                             oracle.jms.AQjmsXAResourceFactory xaresFactory)
                                                                      throws JMSException

      Gets an `XATopicConnectionFactory` using provided datasource and XA resource factory.
      Parameters:
      `dataSource` - indicates the database to which the connection factory creates connections

      `xaresFactory` - `AQjmsXAResourceFactory` used to create customized `XAResource`

      Returns:
      an `XATopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXATopicConnectionFactory

          public static XATopicConnectionFactory getXATopicConnectionFactory(java.lang.String hostName,
                                                                             java.lang.String oracleSID,
                                                                             int portNumber,
                                                                             java.lang.String driver)
                                                                      throws JMSException

      Gets an `XATopicConnectionFactory` using provided driver/host/port/SID. The provided parameters indicate the database to which the connection factory creates connections.
      Parameters:
      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      Returns:
      an `XATopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### getXATopicConnectionFactory

          public static XATopicConnectionFactory getXATopicConnectionFactory(java.lang.String jdbcURL,
                                                                             java.util.Properties info)
                                                                      throws JMSException

      Gets an `XATopicConnectionFactory` using provided URL/properties.
      Parameters:
      `jdbcURL` - indicates the database to which the connection factory creates connections

      `info` - database connection properties

      Returns:
      an `XATopicConnectionFactory`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an XA topic connection factory is not retrieved due to some error.

    <!-- -->

    - #### registerConnectionFactory

          public static int registerConnectionFactory(java.sql.Connection connection,
                                                      java.lang.String connName,
                                                      java.lang.String hostName,
                                                      java.lang.String oracleSID,
                                                      int portNumber,
                                                      java.lang.String driver,
                                                      java.lang.String type)
                                               throws JMSException

      Registers a connection factory to LDAP using provided JDBC connection + driver/host/port/SID.
      Parameters:
      `connection` - the JDBC connection used to perform the registration operation

      `connName` - the name of the to-be-registered connection factory

      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      `type` - `"QUEUE"` or `"TOPIC"`

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not registered due to some error.

    <!-- -->

    - #### registerConnectionFactory

          public static int registerConnectionFactory(java.sql.Connection connection,
                                                      java.lang.String connName,
                                                      java.lang.String jdbcURL,
                                                      java.util.Properties info,
                                                      java.lang.String type)
                                               throws JMSException

      Registers a connection factory to LDAP using provided JDBC connection + URL/properties.
      Parameters:
      `connection` - the JDBC connection used to perform the registration operation

      `connName` - the name of the to-be-registered connection factory

      `jdbcURL` - URL to connect to

      `info` - database connection properties (`"user"`/`"password"`)

      `type` - `"QUEUE"` or `"TOPIC"`

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not registered due to some error.

    <!-- -->

    - #### registerConnectionFactory

          public static int registerConnectionFactory(java.util.Hashtable env,
                                                      java.lang.String connName,
                                                      java.lang.String hostName,
                                                      java.lang.String oracleSID,
                                                      int portNumber,
                                                      java.lang.String driver,
                                                      java.lang.String type)
                                               throws JMSException

      Registers a connection factory to LDAP using provided environment + driver/host/port/SID.
      Parameters:
      `env` - the environment of LDAP connection

      `connName` - the name of the to-be-registered connection factory

      `hostName` - the name of the host running oracle

      `oracleSID` - the oracle system identifier

      `portNumber` - the port number

      `driver` - the type of jdbc driver

      `type` - `"QUEUE"` or `"TOPIC"`

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not registered due to some error.

    <!-- -->

    - #### registerConnectionFactory

          public static int registerConnectionFactory(java.util.Hashtable env,
                                                      java.lang.String connName,
                                                      java.lang.String jdbcURL,
                                                      java.util.Properties info,
                                                      java.lang.String type)
                                               throws JMSException

      Registers a connection factory to LDAP using provided environment + URL/properties.
      Parameters:
      `env` - the environment of LDAP connection

      `connName` - the name of the to-be-registered connection factory

      `jdbcURL` - URL to connect to

      `info` - database connection properties (`"user"`/`"password"`)

      `type` - `"QUEUE"` or `"TOPIC"`

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not registered due to some error.

    <!-- -->

    - #### unregisterConnectionFactory

          public static int unregisterConnectionFactory(java.sql.Connection connection,
                                                        java.lang.String connName)
                                                 throws JMSException

      Unregisters a connection factory from LDAP using provided JDBC connection.
      Parameters:
      `connection` - the JDBC connection used to perform the unregistration operation

      `connName` - the name of the to-be-unregistered connection factory

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not unregistered due to some error.

    <!-- -->

    - #### unregisterConnectionFactory

          public static int unregisterConnectionFactory(java.util.Hashtable env,
                                                        java.lang.String connName)
                                                 throws JMSException

      Unregisters a connection factory from LDAP using provided environment.
      Parameters:
      `env` - the environment of LDAP connection

      `connName` - the name of the to-be-unregistered connection factory

      Returns:
      an LDAP error code in case of error, `LDAP_SUCCESS` if succeeded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a connection factory is not unregistered due to some error.

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

- [Prev Class](AQjmsException.md)
- [Next Class](AQjmsMapMessage.md)

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
