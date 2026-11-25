Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionInitializationCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleConnectionPoolDataSource.md)

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

## Interface ConnectionInitializationCallback

-

  ------------------------------------------------------------------------



      public interface ConnectionInitializationCallback

  This callback allows applications to re-establish session initial starting point after a failover and before replay starts. This callback is registered on the Replay Data Source. It is executed every time the Replay Data Source gets a new physical connection at failover. There is a requirement that the initialization be idempotent or make a decision that the connection is already initialized and does not repeat itself. The callback execution must not leave an open local transaction without committing it or rolling it back. If this is violated, an exception is thrown. If a callback invocation fails, replay is disabled on the related connection.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                             |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `initialize``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` connection)`<br>Initializes the connection. |

<!-- -->

- - ### Method Detail

    - #### initialize

          void initialize(Connection connection)
                   throws SQLException

      Initializes the connection. This typically involves establishing NTSS (Non-Transactional Session State) outside database transactions, such as NLS parameters, cursor state, PL/SQL package variables, and auto-commit mode. For failover, the connection passed in is usually a new physical connection, although a connection pool or application framework utilizing this can provide the callback uniformly for all checked-out connections.
      Parameters:
      `connection` - The connection to be initialized.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionInitializationCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev Class
- [Next Class](OracleConnectionPoolDataSource.md)

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
