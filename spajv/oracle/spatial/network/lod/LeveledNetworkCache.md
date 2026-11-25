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

- [Prev Class](KShortestPathsBfs.md)
- [Next Class](LinkCostCalculator.md)

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

## Class LeveledNetworkCache

- java.lang.Object

- - oracle.spatial.network.lod.LeveledNetworkCache

<!-- -->

-

  ------------------------------------------------------------------------



      public class LeveledNetworkCache
      extends java.lang.Object

  An instance of this class contains the cache for all link levels of a network.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                         | `clear``()`<br>Clears network cache for all link levels.                                                                                                      |
    | `void`                                                                         | `clear``(int linkLevel)`<br>Clears network cache for the specified link level.                                                                                |
    | `void`                                                                         | `flushPartition``(int partitionId, int linkLevel)`<br>Removes the partition from the cache.                                                                   |
    | `int`                                                                          | `getNumberOfLinkLevels``()`                                                                                                                                   |
    | `int`                                                                          | `getNumberOfNodesInMemory``(int linkLevel)`<br>Return the number of nodes in memory for the specified link level.                                             |
    | `int`                                                                          | `getNumberOfPartitions``(int linkLevel)`<br>Returns the number of network partitions in the cache for the specified link level.                               |
    | `int[]`                                                                        | `getPartitionIds``(int linkLevel)`                                                                                                                            |
    | [`LongHashMap`](LongHashMap.md)`<`[`LogicalPartition`](LogicalPartition.md)`>` | `getPartitions``(int linkLevel)`<br>Returns all the network partitions in the cache for the specified link level.                                             |
    | `void`                                                                         | `setPartition``(int partitionId, `[`LogicalPartition`](LogicalPartition.md)` partition, int linkLevel)`<br>Adds or replaces a network partition in the cache. |
    | `java.lang.String`                                                             | `toString``()`                                                                                                                                                |
    | `void`                                                                         | `update``(int linkLevel, `[`NetworkUpdate`](NetworkUpdate.md)` networkUpdate)`<br>Updates the network cache.                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getNumberOfLinkLevels

          public int getNumberOfLinkLevels()

    <!-- -->

    - #### getPartitions

          public LongHashMap<LogicalPartition> getPartitions(int linkLevel)

      Returns all the network partitions in the cache for the specified link level.
      Parameters:

      `linkLevel` - link level

      Returns:

    <!-- -->

    - #### getNumberOfNodesInMemory

          public int getNumberOfNodesInMemory(int linkLevel)

      Return the number of nodes in memory for the specified link level.
      Parameters:

      `linkLevel` - link level

      Returns:

    <!-- -->

    - #### getNumberOfPartitions

          public int getNumberOfPartitions(int linkLevel)

      Returns the number of network partitions in the cache for the specified link level.
      Parameters:

      `linkLevel` - link level

      Returns:

    <!-- -->

    - #### getPartitionIds

          public int[] getPartitionIds(int linkLevel)

    <!-- -->

    - #### setPartition

          public void setPartition(int partitionId,
                                   LogicalPartition partition,
                                   int linkLevel)
                            throws LODNetworkException

      Adds or replaces a network partition in the cache.
      Parameters:
      `partitionId` -

      `partition` -

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### flushPartition

          public void flushPartition(int partitionId,
                                     int linkLevel)

      Removes the partition from the cache.
      Parameters:
      `partitionId` -

      `linkLevel` -

    <!-- -->

    - #### clear

          public void clear(int linkLevel)

      Clears network cache for the specified link level.
      Parameters:
      `linkLevel` - link level

    <!-- -->

    - #### clear

          public void clear()

      Clears network cache for all link levels.

    <!-- -->

    - #### update

          public void update(int linkLevel,
                             NetworkUpdate networkUpdate)
                      throws LODNetworkException

      Updates the network cache.
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](KShortestPathsBfs.md)
- [Next Class](LinkCostCalculator.md)

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
