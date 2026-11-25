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

- [Prev Class](DummyNodeCostCalculator.md)
- [Next Class](EuclideanCostFunction.md)

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

## Class DynamicLinkLevelSelector

- java.lang.Object

- - oracle.spatial.network.lod.DynamicLinkLevelSelector

<!-- -->

- All Implemented Interfaces:
  [LinkLevelSelector](LinkLevelSelector.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class DynamicLinkLevelSelector
      extends java.lang.Object
      implements LinkLevelSelector, XMLConfigurable

  This implementation of LinkLevelSelector dynamically assigns link level to the next node according to the distance from the next node to the start/end point.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `UNKNOWN_LINK_LEVEL`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DynamicLinkLevelSelector``()`<br>Default constructor.                                                                                                                                                                                                                                                                                                   |
    | `DynamicLinkLevelSelector``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst, int maxLinkLevel, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` costFunction, double[] costThresholds, int numHighLevelNeighbors, double costMultiplier, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns a dynamic link level selector. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                                                                                   |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getLinkLevelToExpand``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` ai)`<br>Returns the link level for the next node to expand on.                                                                                                                                                                                                         |
    | `int[]`            | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                                                |
    | `java.lang.String` | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                                                                                                                                                                                                                                                    |
    | `void`             | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter.                                                                                                                                                                                                                             |
    | `boolean`          | `requiresAnalysisInfo``()`<br>Whether analysis info is required.                                                                                                                                                                                                                                                                         |
    | `void`             | `reset``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)`[][] points)`<br>Resets the attributes of this link level selector according to the input points of interest.                                                                                                                                                                          |
    | `void`             | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this link level selector, so that the link level selector can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### UNKNOWN_LINK_LEVEL

          public static final int UNKNOWN_LINK_LEVEL

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### DynamicLinkLevelSelector

          public DynamicLinkLevelSelector()

      Default constructor. After this object is created using this default constructor, method init(Element) should be called to initialize it.

    <!-- -->

    - #### DynamicLinkLevelSelector

          public DynamicLinkLevelSelector(NetworkAnalyst analyst,
                                          int maxLinkLevel,
                                          HeuristicCostFunction costFunction,
                                          double[] costThresholds,
                                          int numHighLevelNeighbors,
                                          double costMultiplier,
                                          LODNetworkConstraint constraint)
                                   throws LODNetworkException

      Returns a dynamic link level selector.
      Parameters:
      `maxLinkLevel` - maximum link level to expand on

      `costFunction` - heuristic cost function

      `costThresholds` - cost threshold. If the heuristic cost from the start node to the end node is less than the costThresholds\[i\], then the link level to expand on is set to the link level i+1.

      `numHighLevelNeighbors` - number of high level nodes to consider while computing the start and end cost threshold. The higher the value of this parameter, the more low level expansion will be used.

      `costMultiplier` - cost multiplier used to compute the start and end cost threshold. The higher the value of this parameter, the more low level expansions will be used.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(org.w3c.dom.Element parameter)

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Initializes the XML configurable object with the input parameter.
      Specified by:
      [`init`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

      Parameters:
      `parameter` - an XML element containing the necessary information to initialize the object.

    <!-- -->

    - #### getXMLSchema

          public java.lang.String getXMLSchema()

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Returns the XML schema for the input parameter.
      Specified by:

      [`getXMLSchema`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

      Returns:

    <!-- -->

    - #### reset

          public void reset(HeavyPointOnNet[][] points)
                     throws LODNetworkException

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Resets the attributes of this link level selector according to the input points of interest.
      Specified by:
      [`reset`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Parameters:
      `points` - points of interest. Each member of the array is an array of equivalent points. For example, in a road network, equivalent points can be the points on either side of a two way road.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getLinkLevelToExpand

          public int getLinkLevelToExpand(LODAnalysisInfo ai)
                                   throws LODNetworkException

      Description copied from interface: [`LinkLevelSelector`](LinkLevelSelector.md)
      Returns the link level for the next node to expand on.
      Specified by:
      [`getLinkLevelToExpand`](LinkLevelSelector.md) in interface [`LinkLevelSelector`](LinkLevelSelector.md)

      Parameters:
      `ai` - analysis information

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

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

- [Prev Class](DummyNodeCostCalculator.md)
- [Next Class](EuclideanCostFunction.md)

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
