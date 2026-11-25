Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEAbstractDataSource.md)
- [Next Class](SQLValidator.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc

## Interface NFEConnectionDataSource

- All Superinterfaces:
  [NFEDataSource](../NFEDataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [JdbcDataSource](JdbcDataSource.md)

  ------------------------------------------------------------------------



      public interface NFEConnectionDataSource
      extends NFEDataSource

  This interface defines methods related to the Connection handling.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                         |
    |-------------------|----------------------------------------------------------------------------------------------------------------|
    | `void`            | `initDatasource``()`<br>Initializes the data source to be able to serve DB connections.                        |
    | `void`            | `setConnectionData``(`[`DbConnectionData`](DbConnectionData.md)` connectionData)`<br>Sets the connection data. |
    | `void`            | `testConnection``()`<br>Tests a connection to the database.                                                    |

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.[NFEDataSource](../NFEDataSource.md)

      [`getActiveWorkspace`](../NFEDataSource.md)`, `[`getConnection`](../NFEDataSource.md)`, `[`setActiveWorkspace`](../NFEDataSource.md)

<!-- -->

- - ### Method Detail

    - #### setConnectionData

          void setConnectionData(DbConnectionData connectionData)

      Sets the connection data.
      Parameters:
      `connectionData` - the data for the connection

    <!-- -->

    - #### initDatasource

          void initDatasource()
                       throws InvalidDBConnectionException

      Initializes the data source to be able to serve DB connections.
      Throws:
      [`InvalidDBConnectionException`](../InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### testConnection

          void testConnection()
                       throws java.lang.Exception

      Tests a connection to the database.
      Throws:
      `java.lang.Exception` - thrown if something goes wrong with the test.

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEAbstractDataSource.md)
- [Next Class](SQLValidator.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
