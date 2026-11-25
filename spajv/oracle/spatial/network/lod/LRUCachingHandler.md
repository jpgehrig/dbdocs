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

- [Prev Class](LongLinkedHashMap.md)
- [Next Class](Matrix.md)

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

## Class LRUCachingHandler

- java.lang.Object

- - oracle.spatial.network.lod.LRUCachingHandler

<!-- -->

- All Implemented Interfaces:
  [CachingHandler](CachingHandler.md)

  ------------------------------------------------------------------------



      public class LRUCachingHandler
      extends java.lang.Object
      implements CachingHandler

  This class implements the Least Recently Used (LRU) caching handler.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `LRUCachingHandler``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                     |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `clone``()`<br>Creates and returns a copy of this CachingHandler object.                                                                                                   |
    | `int[]`            | `getPartitionsToFlushOut``(java.util.Collection<java.lang.Integer> residentPartitions, int minNumNodesToFlushOut)`<br>Returns the IDs of the partitions to be flushed out. |
    | `void`             | `updateRank``(`[`LogicalPartition`](LogicalPartition.md)` partition)`<br>Updates the rank of the partition in the cache.                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LRUCachingHandler

          public LRUCachingHandler()

  <!-- -->

  - ### Method Detail

    - #### getPartitionsToFlushOut

          public int[] getPartitionsToFlushOut(java.util.Collection<java.lang.Integer> residentPartitions,
                                               int minNumNodesToFlushOut)
                                        throws LODNetworkException

      Description copied from interface: [`CachingHandler`](CachingHandler.md)
      Returns the IDs of the partitions to be flushed out.
      Specified by:
      [`getPartitionsToFlushOut`](CachingHandler.md) in interface [`CachingHandler`](CachingHandler.md)

      Parameters:
      `residentPartitions` - resident partitions, which are the partitions to be excluded from the returned list.

      Returns:
      IDs of the partitions to be flushed out.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### updateRank

          public void updateRank(LogicalPartition partition)

      Description copied from interface: [`CachingHandler`](CachingHandler.md)
      Updates the rank of the partition in the cache. The rank will be used to determine which partitions to be flushed out of the cache when getPartitionsToFlushOut() is called.
      Specified by:
      [`updateRank`](CachingHandler.md) in interface [`CachingHandler`](CachingHandler.md)

      Parameters:
      `partition` - the partition object whose rank is to be updated

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Description copied from interface: [`CachingHandler`](CachingHandler.md)
      Creates and returns a copy of this CachingHandler object.
      Specified by:

      [`clone`](CachingHandler.md) in interface [`CachingHandler`](CachingHandler.md)

      Overrides:

      `clone` in class `java.lang.Object`

      Returns:

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

- [Prev Class](LongLinkedHashMap.md)
- [Next Class](Matrix.md)

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
