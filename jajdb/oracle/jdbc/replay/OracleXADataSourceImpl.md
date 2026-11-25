Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](ReplayableConnection.md)

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

oracle.jdbc.replay

## Class OracleXADataSourceImpl

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.replay.OracleDataSourceImpl](OracleDataSourceImpl.md)

  - - [oracle.jdbc.replay.OracleConnectionPoolDataSourceImpl](OracleConnectionPoolDataSourceImpl.md)

    - - oracle.jdbc.replay.OracleXADataSourceImpl

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true), [Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true), [ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true), [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [ConnectionPoolDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [XADataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true), [OracleCommonDataSource](../datasource/OracleCommonDataSource.md), [OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md), [OracleDataSource](../datasource/OracleDataSource.md), [OracleXADataSource](../datasource/OracleXADataSource.md)

  ------------------------------------------------------------------------



      public class OracleXADataSourceImpl
      extends OracleConnectionPoolDataSourceImpl
      implements oracle.jdbc.replay.internal.OracleXADataSource, Serializable, Referenceable, ObjectFactory

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.jdbc.replay.[OracleDataSourceImpl](OracleDataSourceImpl.md)

      [`CHECKSUM_PROPERTY`](OracleDataSourceImpl.md)`, `[`clientChecksum11203x`](OracleDataSourceImpl.md)`, `[`clientChecksum12x`](OracleDataSourceImpl.md)`, `[`connectionProperties`](OracleDataSourceImpl.md)`, `[`doneDumpOnMemoryPressure`](OracleDataSourceImpl.md)`, `[`FAILOVER_RESTORE_AUTO`](OracleDataSourceImpl.md)`, `[`FAILOVER_RESTORE_LEVEL1`](OracleDataSourceImpl.md)`, `[`FAILOVER_RESTORE_NONE`](OracleDataSourceImpl.md)`, `[`FAILOVER_RESTORE_PROPERTY`](OracleDataSourceImpl.md)`, `[`FAILOVER_TYPE_AUTO`](OracleDataSourceImpl.md)`, `[`FAILOVER_TYPE_PROPERTY`](OracleDataSourceImpl.md)`, `[`FAILOVER_TYPE_TRANSACTION`](OracleDataSourceImpl.md)`, `[`IGNORE_AC_CONTEXT_PROPERTY`](OracleDataSourceImpl.md)`, `[`INITIATION_TIMEOUT_PROPERTY`](OracleDataSourceImpl.md)`, `[`isAutoACEnabled`](OracleDataSourceImpl.md)`, `[`isFirstConnection`](OracleDataSourceImpl.md)`, `[`isReplayInDynamicMode`](OracleDataSourceImpl.md)`, `[`isStateRestorationAuto`](OracleDataSourceImpl.md)`, `[`isTransactionReplayEnabled`](OracleDataSourceImpl.md)`, `[`ods`](OracleDataSourceImpl.md)`, `[`odsReconnectOnly`](OracleDataSourceImpl.md)`, `[`password`](OracleDataSourceImpl.md)`, `[`RECONNECT_DELAY_PROPERTY`](OracleDataSourceImpl.md)`, `[`RECONNECT_RETRIES_PROPERTY`](OracleDataSourceImpl.md)`, `[`reconnectDelay`](OracleDataSourceImpl.md)`, `[`reconnectionProperties`](OracleDataSourceImpl.md)`, `[`reconnectRetries`](OracleDataSourceImpl.md)`, `[`replayInitiationTimeout`](OracleDataSourceImpl.md)`, `[`REQUEST_SIZE_LIMIT_PROPERTY`](OracleDataSourceImpl.md)`, `[`SESSION_STATE_CONSISTENCY_STATIC`](OracleDataSourceImpl.md)`, `[`SESSION_STATE_PROPERTY`](OracleDataSourceImpl.md)`, `[`stateRestorationType`](OracleDataSourceImpl.md)`, `[`user`](OracleDataSourceImpl.md)

    <!-- -->

    - ### Fields inherited from interface oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)

      [`CONNECTION_PROPERTIES`](OracleDataSource.md)`, `[`DATA_SOURCE_NAME`](OracleDataSource.md)`, `[`DATABASE_NAME`](OracleDataSource.md)`, `[`DESCRIPTION`](OracleDataSource.md)`, `[`EXPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`IMPLICIT_CACHING_ENABLED`](OracleDataSource.md)`, `[`MAX_STATEMENTS`](OracleDataSource.md)`, `[`NETWORK_PROTOCOL`](OracleDataSource.md)`, `[`PASSWORD`](OracleDataSource.md)`, `[`PORT_NUMBER`](OracleDataSource.md)`, `[`ROLE_NAME`](OracleDataSource.md)`, `[`SERVER_NAME`](OracleDataSource.md)`, `[`URL`](OracleDataSource.md)`, `[`USER`](OracleDataSource.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `OracleXADataSourceImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                           |
    |--------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md)                                          | `createXAConnectionBuilder``()`<br>Creates a new Oracle XA ConnectionBuilder instance                                                                                                                                                                                                                                                                                                                                            |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``()`                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` props)`                                                                                                                                                                                                                                                                                               |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` usr, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pwd)`<br>Attempts to obtain a database connection with the specified user and password.                                                                                                                |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | `getConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` usr, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` pwd, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` props)`                                                                                 |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getPhysicalConnection``()`<br>Gets a physical connection with default url, user name, and password.                                                                                                                                                                                                                                                                                                                             |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getPhysicalConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Gets a physical connection with the default URL and given user name and password.                                                                                               |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | `getPhysicalConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _url, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` _passwd)`<br>Gets a physical connection with the given url, user name, and password. |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true)        | `getXAConnection``()`<br>Attempts to establish a database connection that can be used in a distributed transaction.                                                                                                                                                                                                                                                                                                              |
    | [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true)        | `getXAConnection``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` passwd)`<br>Attempts to establish a database connection that can be used in a distributed transaction.                                                                                              |

    - ### Methods inherited from class oracle.jdbc.replay.[OracleConnectionPoolDataSourceImpl](OracleConnectionPoolDataSourceImpl.md)

      [`createPooledConnectionBuilder`](OracleConnectionPoolDataSourceImpl.md)`, `[`getPooledConnection`](OracleConnectionPoolDataSourceImpl.md)`, `[`getPooledConnection`](OracleConnectionPoolDataSourceImpl.md)`, `[`getPooledConnection`](OracleConnectionPoolDataSourceImpl.md)

    <!-- -->

    - ### Methods inherited from class oracle.jdbc.replay.[OracleDataSourceImpl](OracleDataSourceImpl.md)

      [`clearDoneDumpOnMemoryPressure`](OracleDataSourceImpl.md)`, `[`clearReplayStatistics`](OracleDataSourceImpl.md)`, `[`createConnectionBuilder`](OracleDataSourceImpl.md)`, `[`enableACAndProxifyIfNecessary`](OracleDataSourceImpl.md)`, `[`getConnection`](OracleDataSourceImpl.md)`, `[`getConnectionInitializationCallback`](OracleDataSourceImpl.md)`, `[`getConnectionNoProxy`](OracleDataSourceImpl.md)`, `[`getConnectionProperties`](OracleDataSourceImpl.md)`, `[`getConnectionProperty`](OracleDataSourceImpl.md)`, `[`getDatabaseName`](OracleDataSourceImpl.md)`, `[`getDataSourceName`](OracleDataSourceImpl.md)`, `[`getDescription`](OracleDataSourceImpl.md)`, `[`getExplicitCachingEnabled`](OracleDataSourceImpl.md)`, `[`getImplicitCachingEnabled`](OracleDataSourceImpl.md)`, `[`getLoginTimeout`](OracleDataSourceImpl.md)`, `[`getLogWriter`](OracleDataSourceImpl.md)`, `[`getMaxStatements`](OracleDataSourceImpl.md)`, `[`getNetworkProtocol`](OracleDataSourceImpl.md)`, `[`getObjectInstance`](OracleDataSourceImpl.md)`, `[`getParentLogger`](OracleDataSourceImpl.md)`, `[`getPortNumber`](OracleDataSourceImpl.md)`, `[`getProxyFactory`](OracleDataSourceImpl.md)`, `[`getReference`](OracleDataSourceImpl.md)`, `[`getReplayStatistics`](OracleDataSourceImpl.md)`, `[`getReplayStatisticsString`](OracleDataSourceImpl.md)`, `[`getRequestSizeLimit`](OracleDataSourceImpl.md)`, `[`getRoleName`](OracleDataSourceImpl.md)`, `[`getServerName`](OracleDataSourceImpl.md)`, `[`getURL`](OracleDataSourceImpl.md)`, `[`getUser`](OracleDataSourceImpl.md)`, `[`isWrapperFor`](OracleDataSourceImpl.md)`, `[`registerConnectionInitializationCallback`](OracleDataSourceImpl.md)`, `[`setConnectionProperties`](OracleDataSourceImpl.md)`, `[`setConnectionProperty`](OracleDataSourceImpl.md)`, `[`setDatabaseName`](OracleDataSourceImpl.md)`, `[`setDataSourceName`](OracleDataSourceImpl.md)`, `[`setDescription`](OracleDataSourceImpl.md)`, `[`setExplicitCachingEnabled`](OracleDataSourceImpl.md)`, `[`setImplicitCachingEnabled`](OracleDataSourceImpl.md)`, `[`setLoginTimeout`](OracleDataSourceImpl.md)`, `[`setLogWriter`](OracleDataSourceImpl.md)`, `[`setMaxStatements`](OracleDataSourceImpl.md)`, `[`setNetworkProtocol`](OracleDataSourceImpl.md)`, `[`setPassword`](OracleDataSourceImpl.md)`, `[`setPortNumber`](OracleDataSourceImpl.md)`, `[`setRoleName`](OracleDataSourceImpl.md)`, `[`setServerName`](OracleDataSourceImpl.md)`, `[`setSSLContext`](OracleDataSourceImpl.md)`, `[`setTokenSupplier`](OracleDataSourceImpl.md)`, `[`setupACSpecificProperties`](OracleDataSourceImpl.md)`, `[`setURL`](OracleDataSourceImpl.md)`, `[`setUser`](OracleDataSourceImpl.md)`, `[`unregisterConnectionInitializationCallback`](OracleDataSourceImpl.md)`, `[`unwrap`](OracleDataSourceImpl.md)`, `[`updateReplayStatistics`](OracleDataSourceImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.replay.[OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md)

      [`getPooledConnection`](OracleConnectionPoolDataSource.md)`, `[`getPooledConnection`](OracleConnectionPoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleConnectionPoolDataSource](../datasource/OracleConnectionPoolDataSource.md)

      [`createPooledConnectionBuilder`](../datasource/OracleConnectionPoolDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.replay.internal.OracleDataSource

      `clearDoneDumpOnMemoryPressure, getConnectionNoProxy, getProxyFactory, getReplayStatisticsString, getRequestSizeLimit, updateReplayStatistics`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.replay.[OracleDataSource](OracleDataSource.md)

      [`clearReplayStatistics`](OracleDataSource.md)`, `[`getConnectionInitializationCallback`](OracleDataSource.md)`, `[`getConnectionProperty`](OracleDataSource.md)`, `[`getExplicitCachingEnabled`](OracleDataSource.md)`, `[`getImplicitCachingEnabled`](OracleDataSource.md)`, `[`getMaxStatements`](OracleDataSource.md)`, `[`getReplayStatistics`](OracleDataSource.md)`, `[`getRoleName`](OracleDataSource.md)`, `[`registerConnectionInitializationCallback`](OracleDataSource.md)`, `[`setConnectionProperty`](OracleDataSource.md)`, `[`setExplicitCachingEnabled`](OracleDataSource.md)`, `[`setImplicitCachingEnabled`](OracleDataSource.md)`, `[`setMaxStatements`](OracleDataSource.md)`, `[`setRoleName`](OracleDataSource.md)`, `[`unregisterConnectionInitializationCallback`](OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OracleDataSource](../datasource/OracleDataSource.md)

      [`createConnectionBuilder`](../datasource/OracleDataSource.md)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

    <!-- -->

    - ### Methods inherited from interface javax.naming.[Referenceable](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true)

      [`getReference`](http://download.oracle.com/javase/8/docs/api/javax/naming/Referenceable.html?is-external=true#getReference__)

    <!-- -->

    - ### Methods inherited from interface javax.naming.spi.[ObjectFactory](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true)

      [`getObjectInstance`](http://download.oracle.com/javase/8/docs/api/javax/naming/spi/ObjectFactory.html?is-external=true#getObjectInstance_java_lang_Object_javax_naming_Name_javax_naming_Context_java_util_Hashtable_)

<!-- -->

- - ### Constructor Detail

    - #### OracleXADataSourceImpl

          public OracleXADataSourceImpl()

  <!-- -->

  - ### Method Detail

    - #### getXAConnection

          public XAConnection getXAConnection()
                                       throws SQLException

      Attempts to establish a database connection that can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection__) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Returns:
      An XAConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getXAConnection

          public XAConnection getXAConnection(String user,
                                              String passwd)
                                       throws SQLException

      Attempts to establish a database connection that can be used in a distributed transaction.
      Specified by:
      [`getXAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true#getXAConnection_java_lang_String_java_lang_String_) in interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true)

      Parameters:
      `user` - The database user on whose behalf the Connection is being made.

      `passwd` - The user's password

      Returns:
      An XAConnection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### createXAConnectionBuilder

          public OracleXAConnectionBuilderImpl createXAConnectionBuilder()

      Creates a new Oracle XA ConnectionBuilder instance
      Specified by:
      [`createXAConnectionBuilder`](../datasource/OracleXADataSource.md) in interface [`OracleXADataSource`](../datasource/OracleXADataSource.md)

      Returns:
      The XA ConnectionBuilder instance that was created

    <!-- -->

    - #### getConnection

          public Connection getConnection()
                                   throws SQLException

      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Overrides:
      [`getConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnection

          public Connection getConnection(String usr,
                                          String pwd)
                                   throws SQLException

      Description copied from class: [`OracleDataSourceImpl`](OracleDataSourceImpl.md)
      Attempts to obtain a database connection with the specified user and password.
      Specified by:
      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_) in interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      Overrides:
      [`getConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Parameters:
      `usr` - The database user on whose behalf the connection is being made.

      `pwd` - The user's password.

      Returns:
      A Connection to the database.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getConnection

          public Connection getConnection(Properties props)
                                   throws SQLException

      Overrides:
      [`getConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getConnection

          public Connection getConnection(String usr,
                                          String pwd,
                                          Properties props)
                                   throws SQLException

      Overrides:
      [`getConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection()
                                              throws SQLException

      Gets a physical connection with default url, user name, and password.
      Overrides:
      [`getPhysicalConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Returns:
      A Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection(String _url,
                                                     String _user,
                                                     String _passwd)
                                              throws SQLException

      Gets a physical connection with the given url, user name, and password.
      Overrides:
      [`getPhysicalConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Parameters:
      `_url` - The connect url.

      `_user` - The database user on whose behalf the connection is being made.

      `_passwd` - The user's password

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

    <!-- -->

    - #### getPhysicalConnection

          protected Connection getPhysicalConnection(String _user,
                                                     String _passwd)
                                              throws SQLException

      Gets a physical connection with the default URL and given user name and password.
      Overrides:
      [`getPhysicalConnection`](OracleConnectionPoolDataSourceImpl.md) in class [`OracleConnectionPoolDataSourceImpl`](OracleConnectionPoolDataSourceImpl.md)

      Parameters:
      `_user` - The database user on whose behalf the connection is being made.

      `_passwd` - The user's password

      Returns:
      a Connection to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXADataSourceImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSource.md)
- [Next Class](ReplayableConnection.md)

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
