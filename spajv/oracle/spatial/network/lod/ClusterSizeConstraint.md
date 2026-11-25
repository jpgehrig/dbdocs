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

- [Prev Class](ClusterResult.md)
- [Next Class](Constraint.md)

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

## Class ClusterSizeConstraint

- java.lang.Object

- - oracle.spatial.network.lod.ClusterSizeConstraint

<!-- -->

- All Implemented Interfaces:
  [ClusteringConstraint](ClusteringConstraint.md)

  ------------------------------------------------------------------------



      public class ClusterSizeConstraint
      extends java.lang.Object
      implements ClusteringConstraint

  Since:
  12.2

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                          |
    |------------------------------------------------------|
    | `ClusterSizeConstraint``(int minSize, int maxSize)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                             |
    |-------------------|--------------------------------------------------------------------|
    | `int`             | `getMaxSize``()`                                                   |
    | `int`             | `getMinSize``()`                                                   |
    | `boolean`         | `isSatisfied``(`[`ClusterResult`](ClusterResult.md)` currResult)`  |
    | `void`            | `setMaxSize``(int maxSize)`                                        |
    | `void`            | `setMinSize``(int minSize)`                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ClusterSizeConstraint

          public ClusterSizeConstraint(int minSize,
                                       int maxSize)

  <!-- -->

  - ### Method Detail

    - #### isSatisfied

          public boolean isSatisfied(ClusterResult currResult)

      Specified by:
      [`isSatisfied`](ClusteringConstraint.md) in interface [`ClusteringConstraint`](ClusteringConstraint.md)

    <!-- -->

    - #### setMinSize

          public void setMinSize(int minSize)

    <!-- -->

    - #### getMinSize

          public int getMinSize()

    <!-- -->

    - #### setMaxSize

          public void setMaxSize(int maxSize)

    <!-- -->

    - #### getMaxSize

          public int getMaxSize()

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

- [Prev Class](ClusterResult.md)
- [Next Class](Constraint.md)

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
