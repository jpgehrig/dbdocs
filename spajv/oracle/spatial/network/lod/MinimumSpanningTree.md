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

- [Prev Class](MethodNotSupportedException.md)
- [Next Class](NetworkAnalyst.md)

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

## Interface MinimumSpanningTree

-

  ------------------------------------------------------------------------



      public interface MinimumSpanningTree

  This interface defines methods supported by a minimum-spanning-tree algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                       |
    |-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`SpanningTree`](SpanningTree.md) | `minimumSpanningTree``(int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns the link IDs of the minimum-spanning-tree. |

<!-- -->

- - ### Method Detail

    - #### minimumSpanningTree

          SpanningTree minimumSpanningTree(int linkLevel,
                                           LODNetworkConstraint constraint)
                                    throws LODNetworkException

      Returns the link IDs of the minimum-spanning-tree.
      Parameters:
      `linkLevel` - link level

      Returns:
      link IDs of the minimum-spanning-tree

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

- [Prev Class](MethodNotSupportedException.md)
- [Next Class](NetworkAnalyst.md)

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
