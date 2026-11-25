Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionLabelingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionHarvestingCallback.md)
- [Next Class](ConnectionRetrievalInfo.md)

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

## Interface ConnectionLabelingCallback

- All Known Subinterfaces:
  [ConnectionLabelingCallback](jdbc/ConnectionLabelingCallback.md)

  ------------------------------------------------------------------------



      public interface ConnectionLabelingCallback

  The callback interface for connection labeling support. Applications using the connection labeling feature must provide an implementation of this interface.
  The callback object is registered with the Universal Connection Pool allowing applications to configure connections based on requested labels, as well as calculating the cost of such configuration that sets the connections to the desired states.

  The `cost(...)` method projects the cost of configuring connections considering label-matching differences. Upon a connection-borrowing request, the connection pool uses this method to select a connection with the least reconfiguration cost and returns that connection to the application. The cost is represented in the form of an integer value.

  The `configure(...)` method is called by the connection pool on the selected connection before returning it to the application.

  It is an error to register more than one connection labeling callback with the connection pool. Any such attempt results in a `UniversalConnectionPoolException` at the pool layer or an exception specific to the type of a Universal Connection Pool Adapter (for example, JDBC, JCA, and so forth).

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`PoolDataSource`](jdbc/PoolDataSource.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                             |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `configure``(java.util.Properties requestedLabels, java.lang.Object connection)`<br>Configures the selected connection for a borrowing request before returning the connection to the application. |
    | `int`             | `cost``(java.util.Properties requestedLabels, java.util.Properties currentLabels)`<br>Projects the cost of configuring connections considering label-matching differences.                         |

<!-- -->

- - ### Method Detail

    - #### cost

          int cost(java.util.Properties requestedLabels,
                   java.util.Properties currentLabels)

      Projects the cost of configuring connections considering label-matching differences. Upon a connection-borrowing request, the connection pool uses this method to select a connection with the least reconfiguration cost and returns that connection to the application. The cost is represented in the form of an integer value.
      Parameters:
      `requestedLabels` - The desired labels on a connection request.

      `currentLabels` - The current labels associated with a connection.

      Returns:
      The projected cost for reconfiguring a connection based on label difference.

    <!-- -->

    - #### configure

          boolean configure(java.util.Properties requestedLabels,
                            java.lang.Object connection)

      Configures the selected connection for a borrowing request before returning the connection to the application. This method is called by the connection pool.
      A Universal Connection Pool Adapter passes in a resource-specific connection appropriate for the Adapter type. For example, a JDBC Adapter could pass in a `java.sql.Connection`. **Note:** This method should contain non-transactional SQL calls only. Invoking transactional calls is not supported.

      Parameters:
      `requestedLabels` - The desired labels on a connection request.

      `connection` - The connection chosen by the pool to return to the application.

      Returns:
      If the configuration is successful, return `true`; otherwise, return `false`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionLabelingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionHarvestingCallback.md)
- [Next Class](ConnectionRetrievalInfo.md)

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
