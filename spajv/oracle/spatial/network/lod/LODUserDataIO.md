Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkWrapper.md)
- [Next Class](LODUserDataIOSDO.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Interface LODUserDataIO

- All Known Implementing Classes:
  [LODUserDataIOSDO](LODUserDataIOSDO.md)

  ------------------------------------------------------------------------



      public interface LODUserDataIO

  This interface defines methods to read and write user defined data from and to the database. Each user data category should have its own LODUserDataIO object.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                          | Method and Description                                                                                                                    |
    |--------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                      | `getCategoryId``()`                                                                                                                       |
    | `IDataSource`                              | `getDataSource``()`                                                                                                                       |
    | [`NetworkMetadata`](../NetworkMetadata.md) | `getNetworkMetadata``()`                                                                                                                  |
    | `void`                                     | `readUserData``(`[`LogicalPartition`](LogicalPartition.md)` partition)`                                                                   |
    | [`UserData`](UserData.md)`[]`              | `readUserData``(java.lang.String type, long[] ids)`<br>Reads user defined data from the database.                                         |
    | `void`                                     | `setCategoryId``(int categoryId)`                                                                                                         |
    | `void`                                     | `setDataSource``(IDataSource dataSource)`                                                                                                 |
    | `void`                                     | `setNetworkMetadata``(`[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                             |
    | `boolean`                                  | `shareNetworkDataSource``()`                                                                                                              |
    | `void`                                     | `writeUserData``(`[`LogicalPartition`](LogicalPartition.md)` partition)`                                                                  |
    | `void`                                     | `writeUserData``(java.lang.String type, long[] ids, `[`UserData`](UserData.md)`[] userData)`<br>Writes user defined data to the database. |

<!-- -->

- - ### Method Detail

    - #### shareNetworkDataSource

          boolean shareNetworkDataSource()

    <!-- -->

    - #### getDataSource

          IDataSource getDataSource()

    <!-- -->

    - #### setDataSource

          void setDataSource(IDataSource dataSource)

    <!-- -->

    - #### getNetworkMetadata

          NetworkMetadata getNetworkMetadata()

    <!-- -->

    - #### setNetworkMetadata

          void setNetworkMetadata(NetworkMetadata metadata)

    <!-- -->

    - #### getCategoryId

          int getCategoryId()

    <!-- -->

    - #### setCategoryId

          void setCategoryId(int categoryId)

    <!-- -->

    - #### readUserData

          UserData[] readUserData(java.lang.String type,
                                  long[] ids)

      Reads user defined data from the database.
      Parameters:
      `type` - user data type, which can take the following values:
      - UserDataMetadata.NODE_TABLE_TYPE
      - UserDataMetadata.LINK_TABLE_TYPE
      - UserDataMetadata.PATH_TABLE_TYPE
      - Feature Layer Name

      `ids` - the IDs of the objects for which the user data are read

      Returns:
      array of user data maps, each corresponding to an ID of the same index in the ID array.

    <!-- -->

    - #### writeUserData

          void writeUserData(java.lang.String type,
                             long[] ids,
                             UserData[] userData)

      Writes user defined data to the database.
      Parameters:
      `type` - user data type, which can take the following values:
      - UserDataMetadata.NODE_TABLE_TYPE
      - UserDataMetadata.LINK_TABLE_TYPE
      - UserDataMetadata.PATH_TABLE_TYPE

      `ids` - the IDs of the objects for which the user data are written out

      `userData` - array of user data maps, each corresponding to an ID of the same index in the ID array.

    <!-- -->

    - #### readUserData

          void readUserData(LogicalPartition partition)

    <!-- -->

    - #### writeUserData

          void writeUserData(LogicalPartition partition)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkWrapper.md)
- [Next Class](LODUserDataIOSDO.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
