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

- [Prev Class](LODNetworkManager.md)
- [Next Class](LODUserDataIO.md)

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

## Class LODNetworkWrapper

- java.lang.Object

- - oracle.spatial.network.lod.LODNetworkWrapper

<!-- -->

-

  ------------------------------------------------------------------------



      public class LODNetworkWrapper
      extends java.lang.Object

  This is the wrapper class containing LOD related java stored procedures used by SDO_NET package.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `LEVEL_DEBUG`         |
    | `static int`      | `LEVEL_ERROR`         |
    | `static int`      | `LEVEL_FATAL`         |
    | `static int`      | `LEVEL_FINEST`        |
    | `static int`      | `LEVEL_INFO`          |
    | `static int`      | `LEVEL_WARN`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `findConnectedComponents``(java.lang.String networkName, int linkLevel, java.lang.String componentTable)`<br>Finds the connected components and writes the node component relationship into component table.                                                                                          |
    | `static int`      | `findConnectedComponentsInPartition``(java.lang.String networkName, int linkLevel, int partitionId, int startComponentId, java.sql.Array[] nodeArray, java.sql.Array[] componentArray)`<br>Find the connected components within a partition, with all the external nodes and boundary links included. |
    | `static void`     | `generatePartitionBlob``(java.lang.String networkName, int linkLevel, int partitionId, boolean includeUserData)`<br>Writes partition BLOBs into partition blob table.                                                                                                                                 |
    | `static void`     | `generatePartitionBlob``(java.lang.String networkName, int linkLevel, int partitionId, boolean includeUserData, boolean performDeltaUpdate)`<br>Writes partition BLOBs into partition blob table.                                                                                                     |
    | `static void`     | `generatePartitionBlobs``(java.lang.String networkName, int linkLevel, java.lang.String partitionBlobTable, boolean includeUserData, boolean commitForEachBlob)`<br>Writes partition BLOBs into partition blob table.                                                                                 |
    | `static void`     | `generatePartitionBlobs``(java.lang.String networkName, int linkLevel, java.lang.String partitionBlobTable, boolean includeUserData, boolean commitForEachBlob, boolean performDeltaUpdate)`<br>Writes partition BLOBs into partition blob table.                                                     |
    | `static void`     | `generatePartitionBlobs``(java.lang.String networkName, java.lang.String partitionBlobTable, boolean includeUserData, boolean commitForEachBlob, boolean performDeltaUpdate)`<br>Writes partition BLOBs into partition blob table.                                                                    |
    | `static long`     | `getPartitionSize``(java.lang.String networkName, int partitionId, int linkLevel, boolean includeUserData, boolean includeSpatialData)`<br>Returns the approximated size of a network partition in bytes                                                                                              |
    | `static void`     | `loadConfig``(java.sql.Clob configXml)`<br>Reloads the configuration xml.                                                                                                                                                                                                                             |
    | `static void`     | `setConnection``(java.sql.Connection conn)`<br>Sets the JDBC connection to the database.                                                                                                                                                                                                              |
    | `static void`     | `setLoggingLevel``(int level)`<br>Sets java global logging level.                                                                                                                                                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LEVEL_FATAL

          public static final int LEVEL_FATAL

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_ERROR

          public static final int LEVEL_ERROR

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_WARN

          public static final int LEVEL_WARN

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_INFO

          public static final int LEVEL_INFO

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_DEBUG

          public static final int LEVEL_DEBUG

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_FINEST

          public static final int LEVEL_FINEST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public static void setConnection(java.sql.Connection conn)

      Sets the JDBC connection to the database.
      Parameters:
      `conn` - connection to the database. It must be an OracleConnection.

    <!-- -->

    - #### setLoggingLevel

          public static void setLoggingLevel(int level)

      Sets java global logging level.
      Parameters:
      `level` - LOD logging level, which can take the following values:

      LODNetworkWrapper.LEVEL_FATAL = 1;

      LODNetworkWrapper.LEVEL_ERROR = 2;

      LODNetworkWrapper.LEVEL_WARN = 3;

      LODNetworkWrapper.LEVEL_INFO = 4;

      LODNetworkWrapper.LEVEL_DEBUG = 5;

      LODNetworkWrapper.LEVEL_FINEST = 6;

    <!-- -->

    - #### loadConfig

          public static void loadConfig(java.sql.Clob configXml)
                                 throws LODNetworkException

      Reloads the configuration xml.
      Parameters:
      `configXml` - configuration xml

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlob

          public static void generatePartitionBlob(java.lang.String networkName,
                                                   int linkLevel,
                                                   int partitionId,
                                                   boolean includeUserData)
                                            throws LODNetworkException

      Writes partition BLOBs into partition blob table. The caller needs to make sure that the partition blob table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `linkLevel` - link level

      `partitionId` - partition ID

      `includeUserData` - is user defined data included in the BLOB

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlobs

          public static void generatePartitionBlobs(java.lang.String networkName,
                                                    int linkLevel,
                                                    java.lang.String partitionBlobTable,
                                                    boolean includeUserData,
                                                    boolean commitForEachBlob)
                                             throws LODNetworkException

      Writes partition BLOBs into partition blob table. The caller needs to make sure that the partition blob table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `linkLevel` - link level

      `partitionBlobTable` - partition BLOB table name

      `includeUserData` - is user defined data included in the BLOBs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlob

          public static void generatePartitionBlob(java.lang.String networkName,
                                                   int linkLevel,
                                                   int partitionId,
                                                   boolean includeUserData,
                                                   boolean performDeltaUpdate)
                                            throws LODNetworkException

      Writes partition BLOBs into partition blob table. The caller needs to make sure that the partition blob table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `linkLevel` - link level

      `partitionId` - partition ID

      `includeUserData` - is user defined data included in the BLOB

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### generatePartitionBlobs

          public static void generatePartitionBlobs(java.lang.String networkName,
                                                    java.lang.String partitionBlobTable,
                                                    boolean includeUserData,
                                                    boolean commitForEachBlob,
                                                    boolean performDeltaUpdate)
                                             throws LODNetworkException

      Writes partition BLOBs into partition blob table. The caller needs to make sure that the partition blob table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `partitionBlobTable` - partition BLOB table name

      `includeUserData` - is user defined data included in the BLOBs

      `commitForEachBlob` - whether to call commit after writing the BLOB for each partition

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### generatePartitionBlobs

          public static void generatePartitionBlobs(java.lang.String networkName,
                                                    int linkLevel,
                                                    java.lang.String partitionBlobTable,
                                                    boolean includeUserData,
                                                    boolean commitForEachBlob,
                                                    boolean performDeltaUpdate)
                                             throws LODNetworkException

      Writes partition BLOBs into partition blob table. The caller needs to make sure that the partition blob table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `linkLevel` - link level

      `partitionBlobTable` - partition BLOB table name

      `includeUserData` - is user defined data included in the BLOBs

      `commitForEachBlob` - whether to call commit after writing the BLOB for each partition

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### findConnectedComponents

          public static void findConnectedComponents(java.lang.String networkName,
                                                     int linkLevel,
                                                     java.lang.String componentTable)
                                              throws LODNetworkException

      Finds the connected components and writes the node component relationship into component table. The caller needs to make sure that the component table already exists before calling this method.
      Parameters:
      `networkName` - network name

      `linkLevel` - link level

      `componentTable` - connected component table name

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findConnectedComponentsInPartition

          public static int findConnectedComponentsInPartition(java.lang.String networkName,
                                                               int linkLevel,
                                                               int partitionId,
                                                               int startComponentId,
                                                               java.sql.Array[] nodeArray,
                                                               java.sql.Array[] componentArray)
                                                        throws LODNetworkException

      Find the connected components within a partition, with all the external nodes and boundary links included. This method writes the node id - component id assignment information into the input array, and returns the maximum component ID that has been used so far.
      Parameters:
      `networkName` - name of the network

      `linkLevel` - link level on which the connected component is computed

      `partitionId` - ID of the partition in which the connected component is computed

      `startComponentId` - start component ID to be used. All component IDs being assigned to the nodes in the partition must be no smaller than the start component ID.

      `nodeArray` - empty array where the result node IDs are written into

      `componentArray` - empty array where the result component IDs are written into

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getPartitionSize

          public static long getPartitionSize(java.lang.String networkName,
                                              int partitionId,
                                              int linkLevel,
                                              boolean includeUserData,
                                              boolean includeSpatialData)
                                       throws LODNetworkException,
                                              java.lang.Exception

      Returns the approximated size of a network partition in bytes
      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      `linkLevel` - link level

      `includeUserData` - is user defined data included in the partition

      `includeSpatialData` - is spatial information included in the partition

      Returns:
      partition size in bytes

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      `java.lang.Exception`

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

- [Prev Class](LODNetworkManager.md)
- [Next Class](LODUserDataIO.md)

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
