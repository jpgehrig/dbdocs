Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-files/index-1.md)
- [Help](help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package oracle.ucp

  - ## Class [oracle.ucp.NoAvailableConnectionsException](oracle/ucp/NoAvailableConnectionsException.md) extends [UniversalConnectionPoolException](oracle/ucp/UniversalConnectionPoolException.md) implements Serializable

  - ## Class [oracle.ucp.UniversalConnectionPoolException](oracle/ucp/UniversalConnectionPoolException.md) extends java.lang.Exception implements Serializable

    - ## Serialized Fields

      - #### errorCode

            int errorCode

- ## Package oracle.ucp.jdbc

  - ## Class [oracle.ucp.jdbc.PoolDataSourceImpl](oracle/ucp/jdbc/PoolDataSourceImpl.md) extends java.lang.Object implements Serializable

    - ## Serialization Methods

      - #### readObject

            private void readObject(java.io.ObjectInputStream in)
                             throws java.io.IOException,
                                    java.lang.ClassNotFoundException,
                                    java.sql.SQLException

        Throws:
        `java.io.IOException`

        `java.lang.ClassNotFoundException`

        `java.sql.SQLException`

      - #### writeObject

            private void writeObject(java.io.ObjectOutputStream out)
                              throws java.io.IOException

        Throws:
        `java.io.IOException`

    - ## Serialized Fields

      - #### m_autoProperties

            java.util.List<E> m_autoProperties

      - #### m_user

            java.lang.String m_user

      - #### m_password

            oracle.ucp.util.OpaqueString m_password

      - #### m_url

            java.lang.String m_url

      - #### m_serverName

            java.lang.String m_serverName

      - #### m_portNumber

            int m_portNumber

      - #### m_databaseName

            java.lang.String m_databaseName

      - #### serviceName

            java.lang.String serviceName

      - #### pdbRoles

            java.util.Properties pdbRoles

      - #### sslContext

            javax.net.ssl.SSLContext sslContext

      - #### isXmlUsed

            java.util.concurrent.atomic.AtomicBoolean isXmlUsed

      - #### disableAPI

            java.util.concurrent.atomic.AtomicBoolean disableAPI

      - #### isConfigureNewDS

            java.util.concurrent.atomic.AtomicBoolean isConfigureNewDS

      - #### tokenSupplier

            java.util.function.Supplier<T> tokenSupplier

        Supplies instances of `AccessToken` each time the `#connectionFactory` creates a connection. This field is set to a non-null value by [`PoolDataSourceImpl.setTokenSupplier(Supplier)`](oracle/ucp/jdbc/PoolDataSourceImpl.md). If the setter method is never called, then this field is null.

        UCP does not invoke the `get` method of this `Supplier`. UCP only passes this `Supplier` on to the `connectionFactory`. The `connectionFactory` is implemented to invoke the `get` method when creating a new `Connection`.

        Oracle JDBC data sources that implement `OracleCommonDataSource` are the only connection factory classes that support a token `Supplier`.

      - #### m_dataSourceName

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_dataSourceName

      - #### m_description

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_description

      - #### m_networkProtocol

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_networkProtocol

      - #### m_roleName

            java.lang.String m_roleName

      - #### m_connectionProperties

            java.util.Properties m_connectionProperties

      - #### m_connectionFactoryProperties

            java.util.Properties m_connectionFactoryProperties

      - #### m_connectionFactoryClassName

            java.lang.String m_connectionFactoryClassName

      - #### connectionPoolFactoryClassNameWasSet

            java.util.concurrent.atomic.AtomicBoolean connectionPoolFactoryClassNameWasSet

      - #### m_isDriverFactory

            boolean m_isDriverFactory

      - #### m_connectionFactory

            java.lang.Object m_connectionFactory

      - #### m_connectionPoolName

            java.util.concurrent.atomic.AtomicReference<V> m_connectionPoolName

      - #### m_validateConnectionOnBorrow

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_validateConnectionOnBorrow

      - #### m_SQLForValidateConnection

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_SQLForValidateConnection

      - #### m_initialPoolSize

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_initialPoolSize

      - #### m_minPoolSize

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_minPoolSize

      - #### m_maxPoolSize

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_maxPoolSize

      - #### maxConnectionsPerService

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> maxConnectionsPerService

      - #### m_abandonedConnectionTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_abandonedConnectionTimeout

      - #### m_timeToLiveConnectionTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_timeToLiveConnectionTimeout

      - #### m_inactiveConnectionTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_inactiveConnectionTimeout

      - #### m_timeoutCheckInterval

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_timeoutCheckInterval

      - #### m_maxStatements

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_maxStatements

      - #### m_connectionWaitTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionWaitTimeout

      - #### m_maxConnectionReuseTime

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_maxConnectionReuseTime

      - #### m_maxConnectionReuseCount

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_maxConnectionReuseCount

      - #### m_connectionLabelingCallback

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionLabelingCallback

      - #### m_connectionAffinityCallback

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionAffinityCallback

      - #### m_connectionHarvestTriggerCount

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionHarvestTriggerCount

      - #### m_connectionHarvestMaxCount

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionHarvestMaxCount

      - #### m_fastConnectionFailoverEnabled

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_fastConnectionFailoverEnabled

      - #### m_onsConfigurationString

            java.lang.String m_onsConfigurationString

      - #### m_connectionInitializationCallback

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_connectionInitializationCallback

      - #### connectionLabelingHighCost

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> connectionLabelingHighCost

      - #### highCostConnectionReuseThreshold

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> highCostConnectionReuseThreshold

      - #### isPoolShareable

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> isPoolShareable

      - #### repurposeThreshold

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> repurposeThreshold

      - #### m_secondsToTrustIdleConnection

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> m_secondsToTrustIdleConnection

      - #### loginTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> loginTimeout

      - #### connectionValidationTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> connectionValidationTimeout

      - #### acActive

            java.lang.Boolean acActive

      - #### m_pendingDSRequestsCount

            java.util.concurrent.atomic.AtomicInteger m_pendingDSRequestsCount

      - #### queryTimeout

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> queryTimeout

      - #### maxConnectionsPerShard

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> maxConnectionsPerShard

      - #### shardingMode

            oracle.ucp.jdbc.PoolDataSourceImpl.AutoProperty<T> shardingMode

  - ## Class [oracle.ucp.jdbc.PoolXADataSourceImpl](oracle/ucp/jdbc/PoolXADataSourceImpl.md) extends [PoolDataSourceImpl](oracle/ucp/jdbc/PoolDataSourceImpl.md) implements Serializable

    - ## Serialized Fields

      - #### m_xaDataSource

            javax.sql.XADataSource m_xaDataSource

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-files/index-1.md)
- [Help](help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
