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

- [Prev Class](DummyLinkCostCalculator.md)
- [Next Class](DummyNodeCostCalculator.md)

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

## Class DummyLinkLevelSelector

- java.lang.Object

- - oracle.spatial.network.lod.DummyLinkLevelSelector

<!-- -->

- All Implemented Interfaces:
  [LinkLevelSelector](LinkLevelSelector.md)

  ------------------------------------------------------------------------



      public class DummyLinkLevelSelector
      extends java.lang.Object
      implements LinkLevelSelector

  This implementation of LinkLevelSelector always returns the fixed link level specified in the constructor.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                |
    |--------------------------------------------|
    | `DummyLinkLevelSelector``()`               |
    | `DummyLinkLevelSelector``(int linkLevel)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                   |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getLinkLevelToExpand``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` ai)`<br>Returns the link level for the next node to expand on.                                                                                                                                                                                                         |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                                                |
    | `boolean`         | `requiresAnalysisInfo``()`<br>Whether analysis info is required.                                                                                                                                                                                                                                                                         |
    | `void`            | `reset``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)`[][] points)`<br>Resets the attributes of this link level selector according to the input points of interest.                                                                                                                                                                          |
    | `void`            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this link level selector, so that the link level selector can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DummyLinkLevelSelector

          public DummyLinkLevelSelector()

    <!-- -->

    - #### DummyLinkLevelSelector

          public DummyLinkLevelSelector(int linkLevel)

  <!-- -->

  - ### Method Detail

    - #### getLinkLevelToExpand

          public int getLinkLevelToExpand(LODAnalysisInfo ai)

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Returns the link level for the next node to expand on.
      Specified by:

      [`getLinkLevelToExpand`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Parameters:

      `ai` - analysis information

      Returns:

    <!-- -->

    - #### requiresAnalysisInfo

          public boolean requiresAnalysisInfo()

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Whether analysis info is required.
      Specified by:
      [`requiresAnalysisInfo`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Returns:
      true is analysis info cannot be null; false, otherwise.

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Returns the required user data categories.
      Specified by:

      [`getUserDataCategories`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Returns:

    <!-- -->

    - #### reset

          public void reset(HeavyPointOnNet[][] points)

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Resets the attributes of this link level selector according to the input points of interest.
      Specified by:
      [`reset`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Parameters:
      `points` - points of interest. Each member of the array is an array of equivalent points. For example, in a road network, equivalent points can be the points on either side of a two way road.

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      This method allows caller to pass the network analyst object to this link level selector, so that the link level selector can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the link level selector, the link level selector can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

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

- [Prev Class](DummyLinkCostCalculator.md)
- [Next Class](DummyNodeCostCalculator.md)

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
