Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TreeNode.md)
- [Next Class](UserDataMetadata.md)

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

oracle.spatial.network

## Interface UserDataIO

-

  ------------------------------------------------------------------------



      public interface UserDataIO

  This interface defines methods for users to read and write user defined data from and to the database. User defined data can be associated with a metadata, a network, a node, a link, and a path. The setUserData() and getUserData() methods are used to set and get the user defined data from all network elements. The type of user data is java.lang.Object

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                         |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `readUserData``(java.sql.Connection conn, `[`Network`](Network.md)` network)`<br>Reads user defined data from the database and associates it with the network. |
    | `void`            | `writeUserData``(java.sql.Connection conn, `[`Network`](Network.md)` network)`<br>Writes the user defined data to the database.                                |

<!-- -->

- - ### Method Detail

    - #### readUserData

          void readUserData(java.sql.Connection conn,
                            Network network)

      Reads user defined data from the database and associates it with the network.
      Parameters:
      `conn` - the database connection

      `network` - the network with which the user's data is to be associated

    <!-- -->

    - #### writeUserData

          void writeUserData(java.sql.Connection conn,
                             Network network)

      Writes the user defined data to the database.
      Parameters:
      `conn` - the database connection

      `network` - the network with which the user defined data is to be associated.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TreeNode.md)
- [Next Class](UserDataMetadata.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
