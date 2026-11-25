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

- [Prev Class](PartitionBlob.md)
- [Next Class](PartitionBlobTranslator11g.md)

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

## Interface PartitionBlobTranslator

- All Known Implementing Classes:
  [PartitionBlobTranslator11g](PartitionBlobTranslator11g.md), [PartitionBlobTranslator11gR2](PartitionBlobTranslator11gR2.md)

  ------------------------------------------------------------------------



      public interface PartitionBlobTranslator

  This interface defines methods supported by a partition blob translator. In addition to these methods, a PartitionBlobTranslator implementation class must be a singleton, with a static method 'getPartitionBlobTranslator', whose signature must be
         public static PartitionBlobTranslator getPartitionBlobTranslator();


  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                           |
    |-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LogicalPartition`](LogicalPartition.md) | `blobToPartition``(java.lang.String networkName, int partitionId, int partitionLevel, java.io.InputStream is, boolean loadUserData)`<br>Reads a partition BLOB from the specified input stream and translates it into a LogicalPartition object. |
    | `boolean`                                 | `partitionToBlob``(`[`LogicalPartition`](LogicalPartition.md)` partition, java.io.OutputStream os, boolean includeUserData)`<br>Translates the LogicalPartition object into a partition BLOB, and outputs it into the specified output stream.   |

<!-- -->

- - ### Method Detail

    - #### blobToPartition

          LogicalPartition blobToPartition(java.lang.String networkName,
                                           int partitionId,
                                           int partitionLevel,
                                           java.io.InputStream is,
                                           boolean loadUserData)
                                    throws LODNetworkException

      Reads a partition BLOB from the specified input stream and translates it into a LogicalPartition object.
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

          boolean partitionToBlob(LogicalPartition partition,
                                  java.io.OutputStream os,
                                  boolean includeUserData)
                           throws LODNetworkException

      Translates the LogicalPartition object into a partition BLOB, and outputs it into the specified output stream.
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

- [Prev Class](PartitionBlob.md)
- [Next Class](PartitionBlobTranslator11g.md)

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
