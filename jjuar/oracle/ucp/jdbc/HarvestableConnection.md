Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/HarvestableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionWithTimeToLiveTimeout.md)
- [Next Class](JDBCConnectionPoolStatistics.md)

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

## Interface HarvestableConnection

-

  ------------------------------------------------------------------------



      public interface HarvestableConnection

  Interface supporting Connection Harvesting for JDBC `java.sql.Connections`.
  Connection Harvesting allows the Universal Connection Pool to actively return borrowed connections to the pool when a user-specified threshold for harvesting is met or when the pool has reached its max capacity yet all connections in the pool are borrowed.

  Users have the option for specifying whether a borrowed connection is harvestable, as well as providing customized cleanup actions on harvestable connections.

  Applications use this interface along with the harvesting properties and callbacks for complete connection harvesting functions.

  See Also:
  [`PoolDataSource`](PoolDataSource.md), [`ConnectionHarvestingCallback`](../ConnectionHarvestingCallback.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `isConnectionHarvestable``()`<br>Specifies whether this connection is harvestable.                                                                                                         |
    | `void`            | `registerConnectionHarvestingCallback``(`[`ConnectionHarvestingCallback`](../ConnectionHarvestingCallback.md)` cbk)`<br>Registers a ConnectionHarvestingCallback with the this connection. |
    | `void`            | `removeConnectionHarvestingCallback``()`<br>Removes the ConnectionHarvestingCallback object registered with this connection, if any.                                                       |
    | `void`            | `setConnectionHarvestable``(boolean isConnectionHarvestable)`<br>Specifies whether this connection is harvestable.                                                                         |

<!-- -->

- - ### Method Detail

    - #### setConnectionHarvestable

          void setConnectionHarvestable(boolean isConnectionHarvestable)
                                 throws java.sql.SQLException

      Specifies whether this connection is harvestable.
      Parameters:
      `isConnectionHarvestable` - Whether this connection is harvestable.

      Throws:
      `java.sql.SQLException` - If this connection was closed.

    <!-- -->

    - #### isConnectionHarvestable

          boolean isConnectionHarvestable()
                                   throws java.sql.SQLException

      Specifies whether this connection is harvestable.
      Returns:
      A boolean indicating whether this connection is harvestable. `True` if so and `false` otherwise.

      Throws:
      `java.sql.SQLException` - If an error occurs.

    <!-- -->

    - #### registerConnectionHarvestingCallback

          void registerConnectionHarvestingCallback(ConnectionHarvestingCallback cbk)
                                             throws java.sql.SQLException

      Registers a ConnectionHarvestingCallback with the this connection.
      Parameters:
      `cbk` - The ConnectionHarvestingCallback object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeConnectionHarvestingCallback

          void removeConnectionHarvestingCallback()
                                           throws java.sql.SQLException

      Removes the ConnectionHarvestingCallback object registered with this connection, if any.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/HarvestableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionWithTimeToLiveTimeout.md)
- [Next Class](JDBCConnectionPoolStatistics.md)

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
