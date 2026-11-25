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

- Prev Class
- [Next Class](ConfigManager.md)

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

oracle.spatial.network.lod.config

## Class CachingPolicy

- java.lang.Object

- - oracle.spatial.network.lod.config.CachingPolicy

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable

  ------------------------------------------------------------------------



      public class CachingPolicy
      extends java.lang.Object
      implements java.lang.Cloneable

  The caching policy for a network at certain link level.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description     |
    |---------------------------|---------------------------|
    | `static java.lang.String` | `HANDLER_CLASS_NAME_LRU`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `CachingPolicy``()`<br>Creates a default caching policy instance, whose caching handler is `oracle.spatial.network.lod.LRUCachingHandler`, and the maximum number of nodes allowed in the cache is 500000. |
    | `CachingPolicy``(CachingPolicy policy)`<br>Copy constructor                                                                                                                                                |
    | `CachingPolicy``(org.w3c.dom.Element elem)`<br>Constructs a caching policy instance according to the configuration specified in the xml element.                                                           |
    | `CachingPolicy``(java.lang.String cachingHandlerClassName, int maxNodes)`<br>Constructs a caching policy instance.                                                                                         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                         |
    |------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                   | `addResidentPartition``(int partitionId)`<br>Adds a resident partition to the caching policy.                                  |
    | `java.lang.Object`                       | `clone``()`<br>Supports clone().                                                                                               |
    | [`CachingHandler`](../CachingHandler.md) | `getCachingHandler``()`<br>Returns the caching handler object.                                                                 |
    | `int`                                    | `getMaxNumberOfNodes``()`<br>Returns the maximum number of nodes allowed in the cache for this network level.                  |
    | `int[]`                                  | `getResidentPartitionArray``()`<br>Returns the resident partition ID array.                                                    |
    | `java.util.HashSet<java.lang.Integer>`   | `getResidentPartitions``()`<br>Returns the resident partition IDs.                                                             |
    | `boolean`                                | `isResidentPartition``(int partitionId)`<br>Checks whether the specified partition is a resident partition.                    |
    | `void`                                   | `setCachingHandler``(`[`CachingHandler`](../CachingHandler.md)` cachingHander)`<br>Sets the caching handler.                   |
    | `void`                                   | `setCachingHandler``(java.lang.String cachingHandlerClassName)`<br>Sets the caching handler.                                   |
    | `void`                                   | `setMaxNumberOfNodes``(int maxNumberOfNodes)`<br>Sets the maximum number of nodes allowed in the cache for this network level. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### HANDLER_CLASS_NAME_LRU

          public static final java.lang.String HANDLER_CLASS_NAME_LRU

      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### CachingPolicy

          public CachingPolicy()

      Creates a default caching policy instance, whose caching handler is `oracle.spatial.network.lod.LRUCachingHandler`, and the maximum number of nodes allowed in the cache is 500000.

    <!-- -->

    - #### CachingPolicy

          public CachingPolicy(java.lang.String cachingHandlerClassName,
                               int maxNodes)

      Constructs a caching policy instance.
      Parameters:
      `cachingHandlerClassName` - caching handler class name

      `maxNodes` - maximum number of nodes allowed in the cache before some partitions must be flushed out

    <!-- -->

    - #### CachingPolicy

          public CachingPolicy(CachingPolicy policy)

      Copy constructor
      Parameters:
      `policy` - caching policy

    <!-- -->

    - #### CachingPolicy

          public CachingPolicy(org.w3c.dom.Element elem)
                        throws LODConfigException

      Constructs a caching policy instance according to the configuration specified in the xml element.
      Parameters:
      `elem` - xml element containing the caching policy configuration

      Throws:
      [`LODConfigException`](LODConfigException.md)

  <!-- -->

  - ### Method Detail

    - #### setCachingHandler

          public void setCachingHandler(java.lang.String cachingHandlerClassName)

      Sets the caching handler.
      Parameters:
      `cachingHandlerClassName` - full class name, including the package names, of the caching handler

    <!-- -->

    - #### setCachingHandler

          public void setCachingHandler(CachingHandler cachingHander)

      Sets the caching handler.
      Parameters:
      `cachingHander` - caching handler

    <!-- -->

    - #### getCachingHandler

          public CachingHandler getCachingHandler()

      Returns the caching handler object.
      Returns:
      caching handler

    <!-- -->

    - #### isResidentPartition

          public boolean isResidentPartition(int partitionId)

      Checks whether the specified partition is a resident partition. A resident partition is a partition that never gets flushed out of the cache once loaded.
      Parameters:
      `partitionId` - partition ID

      Returns:
      true, if the partition is a resident partition; false, otherwise.

    <!-- -->

    - #### getMaxNumberOfNodes

          public int getMaxNumberOfNodes()

      Returns the maximum number of nodes allowed in the cache for this network level. Some partitions will be flushed out of the cache when the number of nodes in the cache exceeds the maximum allowed number of nodes.
      Returns:
      the maximum number of nodes allowed in the cache

    <!-- -->

    - #### setMaxNumberOfNodes

          public void setMaxNumberOfNodes(int maxNumberOfNodes)

      Sets the maximum number of nodes allowed in the cache for this network level.
      Parameters:
      `maxNumberOfNodes` -

    <!-- -->

    - #### getResidentPartitions

          public java.util.HashSet<java.lang.Integer> getResidentPartitions()

      Returns the resident partition IDs.
      Returns:
      resident partition IDs

    <!-- -->

    - #### getResidentPartitionArray

          public int[] getResidentPartitionArray()

      Returns the resident partition ID array.
      Returns:
      resident partition IDs

    <!-- -->

    - #### addResidentPartition

          public void addResidentPartition(int partitionId)

      Adds a resident partition to the caching policy.
      Parameters:
      `partitionId` - ID of the resident partition

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Supports clone().
      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      a copy of this caching policy.

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

- Prev Class
- [Next Class](ConfigManager.md)

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
