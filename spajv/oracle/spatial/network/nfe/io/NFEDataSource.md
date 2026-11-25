Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](InvalidDBConnectionException.md)
- [Next Class](NFEIOException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io

## Interface NFEDataSource

- All Known Subinterfaces:
  [NFEConnectionDataSource](jdbc/NFEConnectionDataSource.md)

  <!-- -->

  All Known Implementing Classes:
  [JdbcDataSource](jdbc/JdbcDataSource.md), [NFEAbstractDataSource](jdbc/NFEAbstractDataSource.md)

  ------------------------------------------------------------------------



      public interface NFEDataSource

  This interface provides the database connection that will be used by the NFE services. It provides access methods for the workspace used by the Oracle Workspace Manager.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                   |
    |-----------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`    | `getActiveWorkspace``()`<br>Returns the active workspace.                                                                |
    | `java.sql.Connection` | `getConnection``()`<br>Returns a Connection and throws the appropriate exception if it can not do so.                    |
    | `void`                | `setActiveWorkspace``(java.lang.String workspaceName)`<br>Sets the active workspace that will be used by the connection. |

<!-- -->

- - ### Method Detail

    - #### getConnection

          java.sql.Connection getConnection()
                                     throws InvalidDBConnectionException

      Returns a Connection and throws the appropriate exception if it can not do so. The connection will use the active workspace.
      Returns:
      connection

      Throws:
      [`InvalidDBConnectionException`](InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### setActiveWorkspace

          void setActiveWorkspace(java.lang.String workspaceName)

      Sets the active workspace that will be used by the connection. Reload the model after to change the active workspace.
      Parameters:
      `workspaceName` - name of the workspace that will be used by the connection

    <!-- -->

    - #### getActiveWorkspace

          java.lang.String getActiveWorkspace()

      Returns the active workspace. The method should not return null. If the model is not version enabled then LIVE should be returned.
      Returns:
      active workspace

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](InvalidDBConnectionException.md)
- [Next Class](NFEIOException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
