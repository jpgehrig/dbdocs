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

- [Prev Class](LinkCostCalculator.md)
- [Next Class](LinkNotFoundException.md)

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

## Interface LinkLevelSelector

- All Known Implementing Classes:
  [DummyLinkLevelSelector](DummyLinkLevelSelector.md), [DynamicLinkLevelSelector](DynamicLinkLevelSelector.md)

  ------------------------------------------------------------------------



      public interface LinkLevelSelector

  A LinkLevelSelector selects the link level for the next node to expand on.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                   |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getLinkLevelToExpand``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` ai)`<br>Returns the link level for the next node to expand on.                                                                                                                                                                                                         |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                                                |
    | `boolean`         | `requiresAnalysisInfo``()`<br>Whether analysis info is required.                                                                                                                                                                                                                                                                         |
    | `void`            | `reset``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)`[][] points)`<br>Resets the attributes of this link level selector according to the input points of interest.                                                                                                                                                                          |
    | `void`            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this link level selector, so that the link level selector can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

<!-- -->

- - ### Method Detail

    - #### getLinkLevelToExpand

          int getLinkLevelToExpand(LODAnalysisInfo ai)
                            throws LODNetworkException

      Returns the link level for the next node to expand on.
      Parameters:
      `ai` - analysis information

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### requiresAnalysisInfo

          boolean requiresAnalysisInfo()

      Whether analysis info is required.
      Returns:
      true is analysis info cannot be null; false, otherwise.

    <!-- -->

    - #### getUserDataCategories

          int[] getUserDataCategories()

      Returns the required user data categories.
      Returns:

    <!-- -->

    - #### reset

          void reset(HeavyPointOnNet[][] points)
              throws LODNetworkException

      Resets the attributes of this link level selector according to the input points of interest.
      Parameters:
      `points` - points of interest. Each member of the array is an array of equivalent points. For example, in a road network, equivalent points can be the points on either side of a two way road.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this link level selector, so that the link level selector can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the link level selector, the link level selector can choose to do nothing with this method.

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

- [Prev Class](LinkCostCalculator.md)
- [Next Class](LinkNotFoundException.md)

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
