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

- [Prev Class](PartitionBlobTranslator.md)
- [Next Class](PartitionBlobTranslator11gR2.md)

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

## Class PartitionBlobTranslator11g

- java.lang.Object

- - oracle.spatial.network.lod.PartitionBlobTranslator11g

<!-- -->

- All Implemented Interfaces:
  [PartitionBlobTranslator](PartitionBlobTranslator.md)

  ------------------------------------------------------------------------



      public class PartitionBlobTranslator11g
      extends java.lang.Object
      implements PartitionBlobTranslator

  The class to translate a network partition BLOB to a LogicalPartition object, or vice versa.
  Structure of a BLOB:

  A partition BLOB consists of 3 sections:

  header: summary info about the partition
  nodes (internal and external): number of nodes and list of nodes
  Each node consists of the following fields: node id, node cost, is_active, node partition id, userdata
  links: number of links and list of links
  Each link consists of the following fields: link id, link level, start node id, end node id, link cost, is_bidirected, is_active, userdata
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `PartitionBlobTranslator11g``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                           |
    |------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LogicalPartition`](LogicalPartition.md)                        | `blobToPartition``(java.lang.String networkName, int partitionId, int partitionLevel, java.io.InputStream is, boolean loadUserData)`<br>Reads a partition BLOB from the specified input stream and translates it into a LogicalPartition object. |
    | `static `[`PartitionBlobTranslator`](PartitionBlobTranslator.md) | `getPartitionBlobTranslator``()`                                                                                                                                                                                                                 |
    | `boolean`                                                        | `partitionToBlob``(`[`LogicalPartition`](LogicalPartition.md)` partition, java.io.OutputStream os, boolean includeUserData)`<br>Translates the LogicalPartition object into a partition BLOB, and outputs it into the specified output stream.   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PartitionBlobTranslator11g

          public PartitionBlobTranslator11g()

  <!-- -->

  - ### Method Detail

    - #### getPartitionBlobTranslator

          public static PartitionBlobTranslator getPartitionBlobTranslator()

    <!-- -->

    - #### blobToPartition

          public LogicalPartition blobToPartition(java.lang.String networkName,
                                                  int partitionId,
                                                  int partitionLevel,
                                                  java.io.InputStream is,
                                                  boolean loadUserData)
                                           throws LODNetworkException

      Description copied from interface: [`PartitionBlobTranslator`](PartitionBlobTranslator.md)
      Reads a partition BLOB from the specified input stream and translates it into a LogicalPartition object.
      Specified by:
      [`blobToPartition`](PartitionBlobTranslator.md) in interface [`PartitionBlobTranslator`](PartitionBlobTranslator.md)

      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      `partitionLevel` - link level for the partition

      `is` - input stream

      `loadUserData` - whether to include the user data into the returned LogicalPartition object

      Returns:
      logical partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### partitionToBlob

          public boolean partitionToBlob(LogicalPartition partition,
                                         java.io.OutputStream os,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Description copied from interface: [`PartitionBlobTranslator`](PartitionBlobTranslator.md)
      Translates the LogicalPartition object into a partition BLOB, and outputs it into the specified output stream.
      Specified by:
      [`partitionToBlob`](PartitionBlobTranslator.md) in interface [`PartitionBlobTranslator`](PartitionBlobTranslator.md)

      Parameters:
      `partition` - logical partition

      `os` - output stream

      `includeUserData` - whether to include user data in the generated partition BLOB

      Returns:
      whether user data is included in the generated partition BLOB. User data is includes in the partition BLOB if the input logical partition contains users data and the input includeUserData flag is set to true.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

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

- [Prev Class](PartitionBlobTranslator.md)
- [Next Class](PartitionBlobTranslator11gR2.md)

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
