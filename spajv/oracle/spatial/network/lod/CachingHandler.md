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

- [Prev Class](CachedNetworkIOWM.md)
- [Next Class](CategorizedUserData.md)

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

## Interface CachingHandler

- All Known Implementing Classes:
  [LRUCachingHandler](LRUCachingHandler.md)

  ------------------------------------------------------------------------



      public interface CachingHandler

  This interface defines methods supported by a caching handler.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                     |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `clone``()`<br>Creates and returns a copy of this CachingHandler object.                                                                                                   |
    | `int[]`            | `getPartitionsToFlushOut``(java.util.Collection<java.lang.Integer> residentPartitions, int minNumNodesToFlushOut)`<br>Returns the IDs of the partitions to be flushed out. |
    | `void`             | `updateRank``(`[`LogicalPartition`](LogicalPartition.md)` partition)`<br>Updates the rank of the partition in the cache.                                                   |

<!-- -->

- - ### Method Detail

    - #### getPartitionsToFlushOut

          int[] getPartitionsToFlushOut(java.util.Collection<java.lang.Integer> residentPartitions,
                                        int minNumNodesToFlushOut)
                                 throws LODNetworkException

      Returns the IDs of the partitions to be flushed out.
      Parameters:
      `residentPartitions` - resident partitions, which are the partitions to be excluded from the returned list.

      Returns:
      IDs of the partitions to be flushed out.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### updateRank

          void updateRank(LogicalPartition partition)

      Updates the rank of the partition in the cache. The rank will be used to determine which partitions to be flushed out of the cache when getPartitionsToFlushOut() is called.
      Parameters:
      `partition` - the partition object whose rank is to be updated

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Creates and returns a copy of this CachingHandler object.
      Returns:
      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](CachedNetworkIOWM.md)
- [Next Class](CategorizedUserData.md)

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
