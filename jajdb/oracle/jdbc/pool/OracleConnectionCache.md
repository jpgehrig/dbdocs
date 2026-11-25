Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCache.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionBuilderImpl.md)
- [Next Class](OracleConnectionCacheCallback.md)

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

oracle.jdbc.pool

## Interface OracleConnectionCache

- All Superinterfaces:
  [CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true), [DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  ------------------------------------------------------------------------



      public interface OracleConnectionCache
      extends DataSource

  An OracleConnectionCache is an interface one needs to implement if they like to reuse OracleConnectionEventListener and implement their own version of Connection Caching.

  By extending DataSource, we would like to leverage the DataSource features such as JNDI and the concept of factory for Connection objects.

  Simplifies the design of Cache implementation by shielding the necessity to understand the complexities of JDBC 2.0 Connection pooling 'hooks'. Here are the few basic steps a ConnectionCache class should do to complete the loop:

  1\) Create a new OracleConnectionEventListener and register the connection Cache as it's argument.

  Ex: m_ocel = new OracleConnectionEventListener (this);

  2\) Register this event listener with new PooledConnections.

  Ex: pc.addConnectionEventListener(m_ocel);

  3\) Deregister the listener when closing the PooledConnection

  Ex: pc.removeConnectionEventListener(m_ocel);

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                               |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Close the connection cache.                                                                                                                                                                                                                                                                                           |
    | `void`            | `closePooledConnection``(`[`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)` pc)`<br>Invoked by the ConnectionEventListener when an error occurs on a PooledConnection/LogicalConnection signaling that it is no longer good to be used and can be closed.         |
    | `void`            | `reusePooledConnection``(`[`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true)` pc)`<br>Invoked by the ConnectionEventListener instance when Logical connection handles are closed signaling that the PooledConnection can be recycled into the pool for further use. |

    - ### Methods inherited from interface javax.sql.[DataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true)

      [`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection__)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true#getConnection_java_lang_String_java_lang_String_)

    <!-- -->

    - ### Methods inherited from interface javax.sql.[CommonDataSource](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true)

      [`getLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLoginTimeout__)`, `[`getLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getLogWriter__)`, `[`getParentLogger`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#getParentLogger__)`, `[`setLoginTimeout`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLoginTimeout_int_)`, `[`setLogWriter`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true#setLogWriter_java_io_PrintWriter_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Method Detail

    - #### reusePooledConnection

          void reusePooledConnection(PooledConnection pc)
                              throws SQLException

      Invoked by the ConnectionEventListener instance when Logical connection handles are closed signaling that the PooledConnection can be recycled into the pool for further use.

      Parameters:
      `PooledConnection` - The pooled connection object that needs to be recylced.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - error in recycling the PooledConnection.

    <!-- -->

    - #### closePooledConnection

          void closePooledConnection(PooledConnection pc)
                              throws SQLException

      Invoked by the ConnectionEventListener when an error occurs on a PooledConnection/LogicalConnection signaling that it is no longer good to be used and can be closed.

      Parameters:
      `PooledConnection` - The pooled connection object that has to be closed because of an error.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - error in closing the PooledConnection

    <!-- -->

    - #### close

          void close()
              throws SQLException

      Close the connection cache. All the pooled connections have to be closed.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if error occurs closing the cache.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleConnectionCache.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleConnectionBuilderImpl.md)
- [Next Class](OracleConnectionCacheCallback.md)

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
