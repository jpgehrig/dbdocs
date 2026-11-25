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

- [Prev Class](SpatialPath.md)
- [Next Class](SpatialSubPath.md)

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

## Interface SpatialSubNetwork

- All Superinterfaces:
  java.lang.Cloneable, [LogicalBasicNetwork](LogicalBasicNetwork.md), [LogicalSubNetwork](LogicalSubNetwork.md)

  ------------------------------------------------------------------------



      public interface SpatialSubNetwork
      extends LogicalSubNetwork

  A SpatialSubNetwork is a LogicalSubNetwork with geometry information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                               |
    |--------------------|--------------------------------------------------------------------------------------|
    | `void`             | `computeMBR``()`<br>Computes the Maximum Bounding Rectangle (MBR) of the subnetwork. |
    | [`MBR`](../MBR.md) | `getMBR``()`<br>Returns the Maximum Bounding Rectangle (MBR) of the subnetwork.      |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalSubNetwork](LogicalSubNetwork.md)

      [`addNode`](LogicalSubNetwork.md)`, `[`getBoundaryLinkIds`](LogicalSubNetwork.md)`, `[`getExternalNodeIds`](LogicalSubNetwork.md)`, `[`getIncomingLinkIds`](LogicalSubNetwork.md)`, `[`getInternalBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getInternalLinkIds`](LogicalSubNetwork.md)`, `[`getInternalNodeIds`](LogicalSubNetwork.md)`, `[`getInternalNonBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getNumberOfBoundaryLinks`](LogicalSubNetwork.md)`, `[`getNumberOfExternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfIncomingLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfOutgoingLinks`](LogicalSubNetwork.md)`, `[`getOutgoingLinkIds`](LogicalSubNetwork.md)`, `[`isIncomingLink`](LogicalSubNetwork.md)`, `[`isInternalLink`](LogicalSubNetwork.md)`, `[`isInternalNode`](LogicalSubNetwork.md)`, `[`isOutgoingLink`](LogicalSubNetwork.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalBasicNetwork](LogicalBasicNetwork.md)

      [`addFeatureLayer`](LogicalBasicNetwork.md)`, `[`addLink`](LogicalBasicNetwork.md)`, `[`addNode`](LogicalBasicNetwork.md)`, `[`addUserDataCategory`](LogicalBasicNetwork.md)`, `[`clone`](LogicalBasicNetwork.md)`, `[`getFeatureData`](LogicalBasicNetwork.md)`, `[`getLink`](LogicalBasicNetwork.md)`, `[`getLinkIds`](LogicalBasicNetwork.md)`, `[`getLinkLevel`](LogicalBasicNetwork.md)`, `[`getLinks`](LogicalBasicNetwork.md)`, `[`getName`](LogicalBasicNetwork.md)`, `[`getNode`](LogicalBasicNetwork.md)`, `[`getNodeIds`](LogicalBasicNetwork.md)`, `[`getNodes`](LogicalBasicNetwork.md)`, `[`getNumberOfLinks`](LogicalBasicNetwork.md)`, `[`getNumberOfNodes`](LogicalBasicNetwork.md)`, `[`getUserDataCategories`](LogicalBasicNetwork.md)`, `[`isFeatureLayerLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataCategoryLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataLoaded`](LogicalBasicNetwork.md)`, `[`removeLink`](LogicalBasicNetwork.md)`, `[`removeNode`](LogicalBasicNetwork.md)`, `[`setFeatureData`](LogicalBasicNetwork.md)`, `[`setIsUserDataLoaded`](LogicalBasicNetwork.md)

<!-- -->

- - ### Method Detail

    - #### computeMBR

          void computeMBR()

      Computes the Maximum Bounding Rectangle (MBR) of the subnetwork.

    <!-- -->

    - #### getMBR

          MBR getMBR()

      Returns the Maximum Bounding Rectangle (MBR) of the subnetwork.

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

- [Prev Class](SpatialPath.md)
- [Next Class](SpatialSubPath.md)

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
