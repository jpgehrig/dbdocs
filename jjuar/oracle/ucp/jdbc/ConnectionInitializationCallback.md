Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionInitializationCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](ConnectionLabelingCallback.md)

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

## Interface ConnectionInitializationCallback

-

  ------------------------------------------------------------------------



      public interface ConnectionInitializationCallback

  This callback allows applications and frameworks to initialize connections retrieved from Universal Connection Pool using common actions, before the connections are put to use. The initialization actions vary and could include simple method calls making local state changes within the application, or database operations that require round trips over the network. For example, configuring user roles, NLS language setting, transaction isolation level, and invoking stored procedures. This callback is registered on an oracle.ucp.jdbc.PoolDataSource. It is executed at every connection checkout from the pool, as well as at each successful reconnect during failover. It is recommended that applications use connection labeling (including connection labeling callback) when pooling stateful connections. If both connection labeling callback and this callback are registered on the same connection pool instance, this callback is ignored and the connection labeling callback is used for connection initializations and reinitializations.
  See Also:
  [`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md), [`PoolDataSource`](PoolDataSource.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                             |
    |-------------------|------------------------------------------------------------------------------------|
    | `void`            | `initialize``(java.sql.Connection connection)`<br>Initialize the given connection. |

<!-- -->

- - ### Method Detail

    - #### initialize

          void initialize(java.sql.Connection connection)
                   throws java.sql.SQLException

      Initialize the given connection.
      Parameters:
      `connection` - The connection to initialize.

      Throws:
      `java.sql.SQLException`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionInitializationCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](ConnectionLabelingCallback.md)

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
