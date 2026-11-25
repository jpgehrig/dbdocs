Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

# Serialized Form

- ## Package oracle.jdbc

  - ## Class [oracle.jdbc.LogicalTransactionIdEvent](oracle/jdbc/LogicalTransactionIdEvent.md) extends [EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true) implements Serializable

  - ## Class [oracle.jdbc.OracleDatabaseException](oracle/jdbc/OracleDatabaseException.md) extends [Exception](http://download.oracle.com/javase/8/docs/api/java/lang/Exception.html?is-external=true) implements Serializable

    serialVersionUID:
    1L

    - ## Serialized Fields

      - #### errorPosition

            int errorPosition

        Error position of the sql statement when execution failed. Internal APIs return short value for error position, but having the type as integer to maintain the backward compatibilty of public APIs.

      - #### oracleErrorNumber

            int oracleErrorNumber

        oracle error number for this failure

      - #### sql

            String sql

        failed sql statement

      - #### originalSql

            String originalSql

        failed sql statement before processing

  - ## Class [oracle.jdbc.OracleSQLPermission](oracle/jdbc/OracleSQLPermission.md) extends [BasicPermission](http://download.oracle.com/javase/8/docs/api/java/security/BasicPermission.html?is-external=true) implements Serializable

- ## Package oracle.jdbc.aq

  - ## Class [oracle.jdbc.aq.AQNotificationEvent](oracle/jdbc/aq/AQNotificationEvent.md) extends [EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true) implements Serializable

- ## Package oracle.jdbc.dcn

  - ## Class [oracle.jdbc.dcn.DatabaseChangeEvent](oracle/jdbc/dcn/DatabaseChangeEvent.md) extends [EventObject](http://download.oracle.com/javase/8/docs/api/java/util/EventObject.html?is-external=true) implements Serializable

- ## Package oracle.jdbc.pool

  - ## Class [oracle.jdbc.pool.OracleConnectionPoolDataSource](oracle/jdbc/pool/OracleConnectionPoolDataSource.md) extends [OracleDataSource](oracle/jdbc/pool/OracleDataSource.md) implements Serializable

  - ## Class [oracle.jdbc.pool.OracleDataSource](oracle/jdbc/pool/OracleDataSource.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    3349652938965166731L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException,
                                    SQLException

        This restores the PooledConnection Object. The properties of the Physical connection is restored and not the properties of logical Connection.
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

        [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        The method serializes the OracleConnectionPool object and the properties of the Physical Connection.
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### logWriter

            PrintWriter logWriter

      - #### loginTimeout

            int loginTimeout

      - #### databaseName

            String databaseName

      - #### serviceName

            String serviceName

      - #### dataSourceName

            String dataSourceName

      - #### description

            String description

      - #### networkProtocol

            String networkProtocol

      - #### portNumber

            int portNumber

      - #### user

            String user

      - #### password

            oracle.jdbc.internal.OpaqueString password

      - #### serverName

            String serverName

      - #### url

            String url

      - #### driverType

            String driverType

      - #### tnsEntry

            String tnsEntry

      - #### maxStatements

            int maxStatements

      - #### implicitCachingEnabled

            boolean implicitCachingEnabled

      - #### explicitCachingEnabled

            boolean explicitCachingEnabled

      - #### maxStatementsSet

            boolean maxStatementsSet

      - #### implicitCachingEnabledSet

            boolean implicitCachingEnabledSet

      - #### explicitCachingEnabledSet

            boolean explicitCachingEnabledSet

      - #### connCacheName

            String connCacheName

      - #### connCacheProperties

            Properties connCacheProperties

      - #### connectionProperties

            Properties connectionProperties

      - #### connCachingEnabled

            boolean connCachingEnabled

      - #### fastConnFailover

            boolean fastConnFailover

      - #### onsConfigStr

            String onsConfigStr

      - #### isOracleDataSource

            boolean isOracleDataSource

      - #### roleName

            String roleName

      - #### urlExplicit

            boolean urlExplicit

      - #### useDefaultConnection

            boolean useDefaultConnection

      - #### sslContext

            SSLContext sslContext

        SSLContext used in the network layer of connections established with this datasource. This field may be null if an instance has not been specified via `#setSSLContext(SSLContext`. Instances should be initialized with TLS certificates by user code before establishing a connection with this datasource. However, this field may still reference an uninitialized instance if this data source has not yet established a connection.

      - #### tokenSupplier

            java.util.function.Supplier<T> tokenSupplier

        Supplies instances of [`AccessToken`](oracle/jdbc/AccessToken.md) each time this datasource creates a connection. This field is set to a non-null value by [`OracleDataSource.setTokenSupplier(Supplier)`](oracle/jdbc/pool/OracleDataSource.md). If the setter method is never called, then this field is null.

  - ## Class [oracle.jdbc.pool.OracleOCIConnectionPool](oracle/jdbc/pool/OracleOCIConnectionPool.md) extends [OracleDataSource](oracle/jdbc/pool/OracleDataSource.md) implements Serializable

    - ## Serialized Fields

      - #### m_connection_pool

            oracle.jdbc.oci.OracleOCIConnection m_connection_pool

      - #### m_conn_min_limit

            int m_conn_min_limit

      - #### m_conn_max_limit

            int m_conn_max_limit

      - #### m_conn_increment

            int m_conn_increment

      - #### m_conn_active_size

            int m_conn_active_size

      - #### m_conn_pool_size

            int m_conn_pool_size

      - #### m_conn_timeout

            int m_conn_timeout

      - #### m_conn_nowait

            String m_conn_nowait

      - #### m_is_transactions_distributed

            int m_is_transactions_distributed

      - #### m_lconnections

            Hashtable<K,V> m_lconnections

      - #### lifecycle

            oracle.jdbc.pool.OracleOCIConnectionPool.Lifecycle lifecycle

      - #### m_oracleDriver

            oracle.jdbc.driver.OracleDriver m_oracleDriver

      - #### m_stmtCacheSize

            int m_stmtCacheSize

      - #### m_stmtClearMetaData

            boolean m_stmtClearMetaData

  - ## Class [oracle.jdbc.pool.OraclePooledConnection](oracle/jdbc/pool/OraclePooledConnection.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    -203725628718322873L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException,
                                    SQLException

        This restores the PooledConnection Object. The properties of the Physical connection is restored and not the properties of logical Connection.
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

        [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        The method serializes the OracleConnectionPool object and the properties of the Physical Connection.
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### eventListeners

            Hashtable<K,V> eventListeners

      - #### sqlException

            SQLException sqlException

      - #### autoCommit

            boolean autoCommit

      - #### iccEventListener

            ConnectionEventListener iccEventListener

      - #### connectionProperty

            Hashtable<K,V> connectionProperty

      - #### cachedConnectionAttributes

            Properties cachedConnectionAttributes

      - #### unMatchedCachedConnAttr

            Properties unMatchedCachedConnAttr

      - #### closeOption

            int closeOption

      - #### pcKey

            String pcKey

      - #### closeCallback

            oracle.jdbc.driver.OracleCloseCallback closeCallback

      - #### privateData

            Object privateData

      - #### lastAccessedTime

            long lastAccessedTime

      - #### dataSourceInstanceNameKey

            String dataSourceInstanceNameKey

      - #### dataSourceHostNameKey

            String dataSourceHostNameKey

      - #### dataSourceDbUniqNameKey

            String dataSourceDbUniqNameKey

      - #### connectionMarkedDown

            boolean connectionMarkedDown

      - #### needToAbort

            boolean needToAbort

      - #### localTxnCommitOnClose

            boolean localTxnCommitOnClose

- ## Package oracle.jdbc.replay

  - ## Class [oracle.jdbc.replay.OracleConnectionPoolDataSourceImpl](oracle/jdbc/replay/OracleConnectionPoolDataSourceImpl.md) extends [OracleDataSourceImpl](oracle/jdbc/replay/OracleDataSourceImpl.md) implements Serializable

  - ## Class [oracle.jdbc.replay.OracleDataSourceImpl](oracle/jdbc/replay/OracleDataSourceImpl.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    5634196469087099680L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException,
                                    SQLException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

        [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### ods

            OracleDataSource ods

      - #### odsReconnectOnly

            OracleDataSource odsReconnectOnly

      - #### user

            String user

      - #### password

            oracle.jdbc.internal.OpaqueString password

      - #### url

            String url

      - #### serverName

            String serverName

      - #### portNumber

            int portNumber

      - #### databaseName

            String databaseName

      - #### dataSourceName

            String dataSourceName

      - #### description

            String description

      - #### networkProtocol

            String networkProtocol

      - #### roleName

            String roleName

      - #### connectionProperties

            Properties connectionProperties

      - #### reconnectionProperties

            Properties reconnectionProperties

      - #### maxStatements

            int maxStatements

      - #### implicitCachingEnabled

            boolean implicitCachingEnabled

      - #### explicitCachingEnabled

            boolean explicitCachingEnabled

      - #### connectionInitializationCallback

            oracle.jdbc.replay.internal.ConnectionInitializationCallback connectionInitializationCallback

      - #### isFirstConnection

            AtomicBoolean isFirstConnection

      - #### reconnectDelay

            int reconnectDelay

      - #### reconnectRetries

            int reconnectRetries

      - #### isTransactionReplayEnabled

            boolean isTransactionReplayEnabled

      - #### isAutoACEnabled

            boolean isAutoACEnabled

      - #### isReplayInDynamicMode

            boolean isReplayInDynamicMode

      - #### stateRestorationType

            oracle.jdbc.replay.internal.ReplayableConnection.StateRestorationType stateRestorationType

      - #### isStateRestorationAuto

            boolean isStateRestorationAuto

      - #### replayInitiationTimeout

            int replayInitiationTimeout

      - #### clientChecksum12x

            String clientChecksum12x

      - #### clientChecksum11203x

            String clientChecksum11203x

      - #### acStatistics

            LinkedList<E> acStatistics

      - #### sslContext

            SSLContext sslContext

        SSLContext used in the network layer of connections established with this datasource. This field may be null if an instance has not been specified via `#setSSLContext(SSLContext`. Instances should be initialized with TLS certificates by user code before establishing a connection with this datasource. However, this field may still reference an uninitialized instance if this data source has not yet established a connection.

      - #### doneDumpOnMemoryPressure

            AtomicBoolean doneDumpOnMemoryPressure

  - ## Class [oracle.jdbc.replay.OracleXADataSourceImpl](oracle/jdbc/replay/OracleXADataSourceImpl.md) extends [OracleConnectionPoolDataSourceImpl](oracle/jdbc/replay/OracleConnectionPoolDataSourceImpl.md) implements Serializable

- ## Package oracle.jdbc.xa

  - ## Class [oracle.jdbc.xa.OracleXAConnection](oracle/jdbc/xa/OracleXAConnection.md) extends [OraclePooledConnection](oracle/jdbc/pool/OraclePooledConnection.md) implements Serializable

    - ## Serialized Fields

      - #### xaResource

            XAResource xaResource

  - ## Class [oracle.jdbc.xa.OracleXADataSource](oracle/jdbc/xa/OracleXADataSource.md) extends [OracleConnectionPoolDataSource](oracle/jdbc/pool/OracleConnectionPoolDataSource.md) implements Serializable

    - ## Serialized Fields

      - #### useNativeXA

            boolean useNativeXA

  - ## Class [oracle.jdbc.xa.OracleXAException](oracle/jdbc/xa/OracleXAException.md) extends [XAException](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true) implements Serializable

    serialVersionUID:
    -1286190807520675784L

    - ## Serialized Fields

      - #### xaError

            int xaError

      - #### primary

            int primary

      - #### secondary

            int secondary

  - ## Class [oracle.jdbc.xa.OracleXid](oracle/jdbc/xa/OracleXid.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    - ## Serialized Fields

      - #### formatId

            int formatId

      - #### gtrid

            byte[] gtrid

      - #### bqual

            byte[] bqual

      - #### txctx

            byte[] txctx

      - #### m_hashCode

            int m_hashCode

      - #### state

            int state

- ## Package oracle.jdbc.xa.client

  - ## Class [oracle.jdbc.xa.client.OracleXAConnection](oracle/jdbc/xa/client/OracleXAConnection.md) extends [OracleXAConnection](oracle/jdbc/xa/OracleXAConnection.md) implements Serializable

    - ## Serialized Fields

      - #### isXAResourceTransLoose

            boolean isXAResourceTransLoose

  - ## Class [oracle.jdbc.xa.client.OracleXADataSource](oracle/jdbc/xa/client/OracleXADataSource.md) extends [OracleXADataSource](oracle/jdbc/xa/OracleXADataSource.md) implements Serializable

    - ## Serialized Fields

      - #### rmid

            int rmid

      - #### xaOpenString

            String xaOpenString

      - #### driverCharSetIdString

            String driverCharSetIdString

      - #### oldTnsEntry

            String oldTnsEntry

  - ## Class [oracle.jdbc.xa.client.OracleXAHeteroConnection](oracle/jdbc/xa/client/OracleXAHeteroConnection.md) extends [OracleXAConnection](oracle/jdbc/xa/client/OracleXAConnection.md) implements Serializable

    - ## Serialized Fields

      - #### rmid

            int rmid

      - #### xaCloseString

            String xaCloseString

- ## Package oracle.sql

  - ## Class [oracle.sql.ARRAY](oracle/sql/ARRAY.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleArray target

        Deprecated. 

      - #### ojiOracleArray

            oracle.jdbc.internal.OracleArray ojiOracleArray

        Deprecated. 

  - ## Class [oracle.sql.ArrayDescriptor](oracle/sql/ArrayDescriptor.md) extends [TypeDescriptor](oracle/sql/TypeDescriptor.md) implements Serializable

    serialVersionUID:
    3838105394346513809L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

  - ## Class [oracle.sql.BFILE](oracle/sql/BFILE.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleBfile target

        Deprecated. 

      - #### ojiOracleBfile

            oracle.jdbc.internal.OracleBfile ojiOracleBfile

        Deprecated. 

  - ## Class [oracle.sql.BINARY_DOUBLE](oracle/sql/BINARY_DOUBLE.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    6718338151847341754L

  - ## Class [oracle.sql.BINARY_FLOAT](oracle/sql/BINARY_FLOAT.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    -4231112037190700631L

  - ## Class [oracle.sql.BLOB](oracle/sql/BLOB.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleBlob target

        Deprecated. 

      - #### ojiOracleBlob

            oracle.jdbc.internal.OracleBlob ojiOracleBlob

        Deprecated. 

  - ## Class [oracle.sql.CHAR](oracle/sql/CHAR.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    5559010489982176244L

    - ## Serialized Fields

      - #### charSet

            CharacterSet charSet

        The character set to be used in interpreting the bytes.

      - #### oracleId

            int oracleId

        This is provided primarily so that the Aurora native code can built a CHAR using only primitive values. I.e. without creating a charSet. It does so by creating a CHAR with null CharSet, and the correct oracleId. There isn't any constructor for this, although maybe there should be.

      - #### variableLength

            boolean variableLength

        Indicates if an instance of this class should be treated as a CHAR or VARCHAR.

  - ## Class [oracle.sql.CLOB](oracle/sql/CLOB.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleClob target

        Deprecated. 

      - #### ojiOracleClob

            oracle.jdbc.internal.OracleClob ojiOracleClob

        Deprecated. 

  - ## Class [oracle.sql.DATE](oracle/sql/DATE.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    5229717576495161269L

  - ## Class [oracle.sql.Datum](oracle/sql/Datum.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    4645732484621936751L

    - ## Serialized Fields

      - #### data

            byte[] data

      - #### targetDatum

            Datum targetDatum

      - #### ojiOracleDatumWithConnection

            oracle.jdbc.internal.OracleDatumWithConnection ojiOracleDatumWithConnection

  - ## Class [oracle.sql.DatumWithConnection](oracle/sql/DatumWithConnection.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    - ## Serialization Methods

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws exception if serialized
        Throws:
        [`NotSerializableException`](http://download.oracle.com/javase/8/docs/api/java/io/NotSerializableException.html?is-external=true)

        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### physicalConnection

            oracle.jdbc.internal.OracleConnection physicalConnection

      - #### targetDatumWithConnection

            DatumWithConnection targetDatumWithConnection

  - ## Class [oracle.sql.INTERVALDS](oracle/sql/INTERVALDS.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    7164731704878764759L

  - ## Class [oracle.sql.INTERVALYM](oracle/sql/INTERVALYM.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    8393284561907159296L

  - ## Class [oracle.sql.JAVA_STRUCT](oracle/sql/JAVA_STRUCT.md) extends [STRUCT](oracle/sql/STRUCT.md) implements Serializable

    serialVersionUID:
    2211611973003094149L

  - ## Class [oracle.sql.NCLOB](oracle/sql/NCLOB.md) extends [CLOB](oracle/sql/CLOB.md) implements Serializable

  - ## Class [oracle.sql.NUMBER](oracle/sql/NUMBER.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    -1656085588913430059L

  - ## Class [oracle.sql.OPAQUE](oracle/sql/OPAQUE.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### descriptor

            OpaqueDescriptor descriptor

        Deprecated. 

      - #### value

            byte[] value

        Deprecated. 

      - #### imageOffset

            long imageOffset

        Deprecated. 

      - #### imageLength

            long imageLength

        Deprecated. 

      - #### acProxy

            Object acProxy

        Deprecated. 

  - ## Class [oracle.sql.OpaqueDescriptor](oracle/sql/OpaqueDescriptor.md) extends [TypeDescriptor](oracle/sql/TypeDescriptor.md) implements Serializable

    serialVersionUID:
    1013921343538311063L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

  - ## Class [oracle.sql.RAW](oracle/sql/RAW.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    -3298750557928937840L

  - ## Class [oracle.sql.REF](oracle/sql/REF.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleRef target

        Deprecated. 

      - #### ojiOracleRef

            oracle.jdbc.internal.OracleRef ojiOracleRef

        Deprecated. 

  - ## Class [oracle.sql.ROWID](oracle/sql/ROWID.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    5629736369998199486L

    - ## Serialized Fields

      - #### acProxy

            Object acProxy

  - ## Class oracle.sql.SQLName extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    2266340348729491526L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream arg0)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream arg0)
                              throws IOException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### name

            String name

      - #### schema

            String schema

      - #### simple

            String simple

      - #### version

            int version

      - #### synonym

            boolean synonym

  - ## Class [oracle.sql.STRUCT](oracle/sql/STRUCT.md) extends [DatumWithConnection](oracle/sql/DatumWithConnection.md) implements Serializable

    - ## Serialized Fields

      - #### target

            oracle.jdbc.driver.OracleStruct target

        Deprecated. 

      - #### ojiOracleStruct

            oracle.jdbc.internal.OracleStruct ojiOracleStruct

        Deprecated. 

  - ## Class [oracle.sql.StructDescriptor](oracle/sql/StructDescriptor.md) extends [TypeDescriptor](oracle/sql/TypeDescriptor.md) implements Serializable

    serialVersionUID:
    1013921343538311063L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Deprecated. 
        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

  - ## Class [oracle.sql.TIMESTAMP](oracle/sql/TIMESTAMP.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    -7964732752952728545L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

  - ## Class [oracle.sql.TIMESTAMPLTZ](oracle/sql/TIMESTAMPLTZ.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    2045880772054757133L

  - ## Class [oracle.sql.TIMESTAMPTZ](oracle/sql/TIMESTAMPTZ.md) extends [Datum](oracle/sql/Datum.md) implements Serializable

    serialVersionUID:
    6708361144588335769L

  - ## Class [oracle.sql.TypeDescriptor](oracle/sql/TypeDescriptor.md) extends [Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) implements Serializable

    serialVersionUID:
    2022598722047823723L

    - ## Serialization Methods

      - #### readObject

            private void readObject(ObjectInputStream in)
                             throws IOException,
                                    ClassNotFoundException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

        [`ClassNotFoundException`](http://download.oracle.com/javase/8/docs/api/java/lang/ClassNotFoundException.html?is-external=true)

      - #### writeObject

            private void writeObject(ObjectOutputStream out)
                              throws IOException

        Throws:
        [`IOException`](http://download.oracle.com/javase/8/docs/api/java/io/IOException.html?is-external=true)

    - ## Serialized Fields

      - #### sqlName

            oracle.sql.SQLName sqlName

      - #### pickler

            oracle.jdbc.oracore.OracleNamedType pickler

      - #### internalTypeCode

            short internalTypeCode

      - #### isTransient

            boolean isTransient

      - #### toid

            byte[] toid

      - #### toidVersion

            int toidVersion

      - #### precision

            long precision

      - #### scale

            byte scale

      - #### transientImage

            byte[] transientImage

      - #### attributesDescriptor

            AttributeDescriptor[] attributesDescriptor

      - #### typeNameByUser

            String typeNameByUser

      - #### acProxy

            Object acProxy

Skip navigation links

- [Overview](overview-summary.md)
- Package
- Class
- Use
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
