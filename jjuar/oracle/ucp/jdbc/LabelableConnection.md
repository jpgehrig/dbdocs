Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LabelableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](JDBCConnectionPoolStatistics.md)
- [Next Class](PoolDataSource.md)

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

oracle.ucp.jdbc

## Interface LabelableConnection

-

  ------------------------------------------------------------------------



      public interface LabelableConnection

  Interface supporting Connection Labeling for JDBC `java.sql.Connections`.
  The Connection Labeling mechanism is application-driven. Labels can be applied on and removed from a borrowed connection, with each connection label defined as a (key, value) pair. Connection labels are used for connection matching purposes. Any number of connection labels may be applied on a borrowed connection. It is also possible to obtain all the labels currently applied on a borrowed connection, as well as all the unmatched labels within application-requested labels for each connection-borrowing request.

  Applications use this interface along with the `getConnection(...)` methods (with labels parameter) and the labeling callbacks for complete connection labeling functions.

  See Also:
  [`PoolDataSource`](PoolDataSource.md), [`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type      | Method and Description                                                                                                                                                                                               |
    |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                 | `applyConnectionLabel``(java.lang.String key, java.lang.String value)`<br>Applies connection labels on a borrowed connection while the connection is open.                                                           |
    | `java.util.Properties` | `getConnectionLabels``()`<br>Retrieves all the connection labels applied on this connection.                                                                                                                         |
    | `java.util.Properties` | `getUnmatchedConnectionLabels``(java.util.Properties requestedLabels)`<br>Obtains all the requested labels that did not match the applied labels on this connection when this connection was borrowed from the pool. |
    | `void`                 | `removeConnectionLabel``(java.lang.String key)`<br>Removes the connection label with the given key from the connection labels applied on this connection.                                                            |

<!-- -->

- - ### Method Detail

    - #### applyConnectionLabel

          void applyConnectionLabel(java.lang.String key,
                                    java.lang.String value)
                             throws java.sql.SQLException

      Applies connection labels on a borrowed connection while the connection is open. Applying connection labels is cumulative; the supplied key/value pair is added to those connection labels already applied each time this method is called. However, for each particular label key, only the last applied value is retained. Applying connection labels on a closed connection throws a `UniversalConnectionPoolException`.
      Parameters:
      `key` - The key of the connection label to be applied. Cannot be `null` or an empty string.

      `value` - The value of the connection label to be applied. Can be `null` or an empty string.

      Throws:
      `java.sql.SQLException` - If this connection was closed or the key is `null` or an empty string.

    <!-- -->

    - #### removeConnectionLabel

          void removeConnectionLabel(java.lang.String key)
                              throws java.sql.SQLException

      Removes the connection label with the given key from the connection labels applied on this connection. This method does nothing if there is no applied label with the specified key.
      Parameters:
      `key` - The key of the connection label to be removed. Cannot be `null` or an empty string.

      Throws:
      `java.sql.SQLException` - If this connection was closed or the key is `null` or an empty string.

    <!-- -->

    - #### getConnectionLabels

          java.util.Properties getConnectionLabels()
                                            throws java.sql.SQLException

      Retrieves all the connection labels applied on this connection. Any change to the result Properties object does not affect the labels applied to this connection.
      Returns:
      A `java.util.Properties` object storing all the applied labels as key/value pairs. Returns null if there are no applied labels on this connection.

      Throws:
      `java.sql.SQLException` - If this connection was closed.

    <!-- -->

    - #### getUnmatchedConnectionLabels

          java.util.Properties getUnmatchedConnectionLabels(java.util.Properties requestedLabels)
                                                     throws java.sql.SQLException

      Obtains all the requested labels that did not match the applied labels on this connection when this connection was borrowed from the pool.
      This method is typically used to verify which labels in the requested labels are matched and which labels are not.

      Parameters:
      `requestedLabels` - The requested labels that borrowed this connection from the pool.

      Returns:
      A `java.util.Properties` object storing all the requested labels that did not match the labels applied on this connection. Returns null if there are none.

      Throws:
      `java.sql.SQLException` - If this connection was closed.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/LabelableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](JDBCConnectionPoolStatistics.md)
- [Next Class](PoolDataSource.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
