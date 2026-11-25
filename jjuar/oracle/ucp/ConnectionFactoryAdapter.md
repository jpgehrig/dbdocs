Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionFactoryAdapter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionAffinityCallback.AffinityPolicy.md)
- [Next Class](ConnectionHarvestingCallback.md)

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

oracle.ucp

## Interface ConnectionFactoryAdapter

-

  ------------------------------------------------------------------------



      public interface ConnectionFactoryAdapter

  The connection factory adapter is responsible for creating and closing connections for a specific resource (such as, JDBC or JCA). When a connection is created, the connection factory adapter uses the information in the connection retrieval info object to create a connection. For example, if the resource is JDBC, the connection retrieval info object contains a user and password that the connection factory adapter uses to ask the JDBC resource for a connection.
  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                    |
    |-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                      | `closeConnection``(java.lang.Object connection)`<br>Closes the given connection.                                                                                                          |
    | `java.lang.Object`                                          | `createConnection``(`[`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)` connectionRequestInfo)`<br>Creates a connection.                                                            |
    | [`UniversalPooledConnection`](UniversalPooledConnection.md) | `createPooledConnection``(java.lang.Object connection, `[`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)` connectionRequestInfo)`<br>Creates a UniversalPooledConnection object.   |
    | `void`                                                      | `setUniversalConnectionPool``(`[`UniversalConnectionPool`](UniversalConnectionPool.md)` connectionPool)`<br>Sets the connection pool that interacts with this connection factory adapter. |

<!-- -->

- - ### Method Detail

    - #### createConnection

          java.lang.Object createConnection(ConnectionRetrievalInfo connectionRequestInfo)
                                     throws UniversalConnectionPoolException

      Creates a connection.
      Parameters:
      `connectionRequestInfo` - The information to use to create the connection.

      Returns:
      A connection. `null` if a connection could not be created.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs while creating the connection.

    <!-- -->

    - #### closeConnection

          void closeConnection(java.lang.Object connection)
                        throws UniversalConnectionPoolException

      Closes the given connection.
      Parameters:
      `connection` - The connection to close.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs while closing the connection.

    <!-- -->

    - #### createPooledConnection

          UniversalPooledConnection createPooledConnection(java.lang.Object connection,
                                                           ConnectionRetrievalInfo connectionRequestInfo)
                                                    throws UniversalConnectionPoolException

      Creates a UniversalPooledConnection object.
      Parameters:
      `connection` - The physical connection that this pooled connection decorates.

      `connectionRequestInfo` - The connection retrieval info object used to create the decorated connection.

      Returns:
      The `created UniversalPooledConnection` object.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs while creating the `UniversalPooledConnection` object.

    <!-- -->

    - #### setUniversalConnectionPool

          void setUniversalConnectionPool(UniversalConnectionPool connectionPool)
                                   throws UniversalConnectionPoolException

      Sets the connection pool that interacts with this connection factory adapter.
      Parameters:
      `connectionPool` - The connection pool that interacts with this connection factory adapter. Cannot be `null`.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if the connection pool is `null`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionFactoryAdapter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionAffinityCallback.AffinityPolicy.md)
- [Next Class](ConnectionHarvestingCallback.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
