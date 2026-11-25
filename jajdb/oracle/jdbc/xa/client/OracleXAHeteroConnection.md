Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAHeteroConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAHeteroCloseCallback.md)
- [Next Class](OracleXAHeteroResource.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.jdbc.xa.client

## Class OracleXAHeteroConnection

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.jdbc.pool.OraclePooledConnection](../../pool/OraclePooledConnection.md)

  - - [oracle.jdbc.xa.OracleXAConnection](../OracleXAConnection.md)

    - - [oracle.jdbc.xa.client.OracleXAConnection](OracleXAConnection.md)

      - - oracle.jdbc.xa.client.OracleXAHeteroConnection

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true), [XAConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true), [OraclePooledConnection](../../datasource/OraclePooledConnection.md), [OracleXAConnection](../../datasource/OracleXAConnection.md)

  ------------------------------------------------------------------------



      public class OracleXAHeteroConnection
      extends OracleXAConnection

  A factory for Connection objects. An object that implements the XAConnection interface provides support for distributed transactions. An XAConnection may be enlisted in a distributed transaction by means of an XAResource object.
  This class implements oracle.jdbc.xa.OracleXAConnection and works for both pre- and post-8.1.6 Oracle backends. OracleXAConnection is the alternative implementation that talks to only 8.1.6 and post-8.1.6 backends.

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.jdbc.xa.client.[OracleXAConnection](OracleXAConnection.md)

      [`isXAResourceTransLoose`](OracleXAConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.jdbc.xa.[OracleXAConnection](../OracleXAConnection.md)

      [`xaResource`](../OracleXAConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.jdbc.pool.[OraclePooledConnection](../../pool/OraclePooledConnection.md)

      [`autoCommit`](../../pool/OraclePooledConnection.md)`, `[`cachedConnectionAttributes`](../../pool/OraclePooledConnection.md)`, `[`close_callback_string`](../../pool/OraclePooledConnection.md)`, `[`closeOption`](../../pool/OraclePooledConnection.md)`, `[`connect_auto_commit_string`](../../pool/OraclePooledConnection.md)`, `[`connection_properties_string`](../../pool/OraclePooledConnection.md)`, `[`connectionMarkedDown`](../../pool/OraclePooledConnection.md)`, `[`dataSourceDbUniqNameKey`](../../pool/OraclePooledConnection.md)`, `[`dataSourceHostNameKey`](../../pool/OraclePooledConnection.md)`, `[`dataSourceInstanceNameKey`](../../pool/OraclePooledConnection.md)`, `[`event_listener_string`](../../pool/OraclePooledConnection.md)`, `[`explicit_caching_enabled`](../../pool/OraclePooledConnection.md)`, `[`ExplicitStatementCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`implicit_caching_enabled`](../../pool/OraclePooledConnection.md)`, `[`ImplicitStatementCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`isClearMetaData`](../../pool/OraclePooledConnection.md)`, `[`logicalHandle`](../../pool/OraclePooledConnection.md)`, `[`LoginTimeout`](../../pool/OraclePooledConnection.md)`, `[`needToAbort`](../../pool/OraclePooledConnection.md)`, `[`NO_IMPLICIT_BEGIN_REQUEST_PROPERTY`](../../pool/OraclePooledConnection.md)`, `[`object_type_map`](../../pool/OraclePooledConnection.md)`, `[`oracleDriver`](../../pool/OraclePooledConnection.md)`, `[`physicalConn`](../../pool/OraclePooledConnection.md)`, `[`pool_auto_commit_string`](../../pool/OraclePooledConnection.md)`, `[`private_data`](../../pool/OraclePooledConnection.md)`, `[`replayConn`](../../pool/OraclePooledConnection.md)`, `[`sql_exception_string`](../../pool/OraclePooledConnection.md)`, `[`statement_cache_size`](../../pool/OraclePooledConnection.md)`, `[`transaction_isolation`](../../pool/OraclePooledConnection.md)`, `[`unMatchedCachedConnAttr`](../../pool/OraclePooledConnection.md)`, `[`url_string`](../../pool/OraclePooledConnection.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OracleXAHeteroConnection``()`<br>Constructor.                                                                                                                                              |
    | `OracleXAHeteroConnection``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` pc)`<br>Constructor that takes a Connection parameter. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                  | Method and Description                                            |
    |--------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|
    | [`XAResource`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html?is-external=true) | `getXAResource``()`<br>Return an XAResource object to the caller. |

    - ### Methods inherited from class oracle.jdbc.xa.[OracleXAConnection](../OracleXAConnection.md)

      [`getConnection`](../OracleXAConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.jdbc.pool.[OraclePooledConnection](../../pool/OraclePooledConnection.md)

      [`addConnectionEventListener`](../../pool/OraclePooledConnection.md)`, `[`addStatementEventListener`](../../pool/OraclePooledConnection.md)`, `[`close`](../../pool/OraclePooledConnection.md)`, `[`debug`](../../pool/OraclePooledConnection.md)`, `[`getCallWithKey`](../../pool/OraclePooledConnection.md)`, `[`getConnectionDuringExceptionHandling`](../../pool/OraclePooledConnection.md)`, `[`getExplicitCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`getImplicitCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`getLastAccessedTime`](../../pool/OraclePooledConnection.md)`, `[`getLogicalHandle`](../../pool/OraclePooledConnection.md)`, `[`getPhysicalHandle`](../../pool/OraclePooledConnection.md)`, `[`getStatementCacheSize`](../../pool/OraclePooledConnection.md)`, `[`getStatementWithKey`](../../pool/OraclePooledConnection.md)`, `[`getStmtCacheSize`](../../pool/OraclePooledConnection.md)`, `[`isStatementCacheInitialized`](../../pool/OraclePooledConnection.md)`, `[`purgeExplicitCache`](../../pool/OraclePooledConnection.md)`, `[`purgeImplicitCache`](../../pool/OraclePooledConnection.md)`, `[`registerImplicitCacheConnectionEventListener`](../../pool/OraclePooledConnection.md)`, `[`removeConnectionEventListener`](../../pool/OraclePooledConnection.md)`, `[`removeStatementEventListener`](../../pool/OraclePooledConnection.md)`, `[`setConnection`](../../pool/OraclePooledConnection.md)`, `[`setExplicitCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`setImplicitCachingEnabled`](../../pool/OraclePooledConnection.md)`, `[`setLastAccessedTime`](../../pool/OraclePooledConnection.md)`, `[`setProperties`](../../pool/OraclePooledConnection.md)`, `[`setShardingKey`](../../pool/OraclePooledConnection.md)`, `[`setShardingKeyIfValid`](../../pool/OraclePooledConnection.md)`, `[`setStatementCacheSize`](../../pool/OraclePooledConnection.md)`, `[`setStmtCacheSize`](../../pool/OraclePooledConnection.md)`, `[`setStmtCacheSize`](../../pool/OraclePooledConnection.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.datasource.[OraclePooledConnection](../../datasource/OraclePooledConnection.md)

      [`getCallWithKey`](../../datasource/OraclePooledConnection.md)`, `[`getExplicitCachingEnabled`](../../datasource/OraclePooledConnection.md)`, `[`getImplicitCachingEnabled`](../../datasource/OraclePooledConnection.md)`, `[`getLastAccessedTime`](../../datasource/OraclePooledConnection.md)`, `[`getLogicalHandle`](../../datasource/OraclePooledConnection.md)`, `[`getStatementCacheSize`](../../datasource/OraclePooledConnection.md)`, `[`getStatementWithKey`](../../datasource/OraclePooledConnection.md)`, `[`purgeExplicitCache`](../../datasource/OraclePooledConnection.md)`, `[`purgeImplicitCache`](../../datasource/OraclePooledConnection.md)`, `[`registerCloseCallback`](../../datasource/OraclePooledConnection.md)`, `[`registerImplicitCacheConnectionEventListener`](../../datasource/OraclePooledConnection.md)`, `[`setExplicitCachingEnabled`](../../datasource/OraclePooledConnection.md)`, `[`setImplicitCachingEnabled`](../../datasource/OraclePooledConnection.md)`, `[`setLastAccessedTime`](../../datasource/OraclePooledConnection.md)`, `[`setShardingKey`](../../datasource/OraclePooledConnection.md)`, `[`setShardingKeyIfValid`](../../datasource/OraclePooledConnection.md)`, `[`setStatementCacheSize`](../../datasource/OraclePooledConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[PooledConnection](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)

      [`addConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`addStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#addStatementEventListener_javax_sql_StatementEventListener_)`, `[`close`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#close__)`, `[`removeConnectionEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeConnectionEventListener_javax_sql_ConnectionEventListener_)`, `[`removeStatementEventListener`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true#removeStatementEventListener_javax_sql_StatementEventListener_)

<!-- -->

- - ### Constructor Detail

    - #### OracleXAHeteroConnection

          public OracleXAHeteroConnection()
                                   throws XAException

      Constructor. Creates an OracleXAHeteroConnection object.
      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

    <!-- -->

    - #### OracleXAHeteroConnection

          public OracleXAHeteroConnection(Connection pc)
                                   throws XAException

      Constructor that takes a Connection parameter. Create an OracleXAHeteroConnection object.
      Parameters:
      `pc` - A physical connection object.

      Throws:
      [`XAException`](http://download.oracle.com/javase/8/docs/api/javax/transaction/xa/XAException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getXAResource

          public XAResource getXAResource()

      Return an XAResource object to the caller.
      Specified by:
      [`getXAResource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true#getXAResource__) in interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true)

      Specified by:
      [`getXAResource`](../../datasource/OraclePooledConnection.md) in interface [`OraclePooledConnection`](../../datasource/OraclePooledConnection.md)

      Overrides:
      [`getXAResource`](OracleXAConnection.md) in class [`OracleXAConnection`](OracleXAConnection.md)

      Returns:
      the XAResource

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleXAHeteroConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAHeteroCloseCallback.md)
- [Next Class](OracleXAHeteroResource.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
