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

- [Prev Class](LODConfigException.md)
- [Next Class](NetworkIOConfig.md)

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

## Class NetworkAnalysisConfig

- java.lang.Object

- - oracle.spatial.network.lod.config.NetworkAnalysisConfig

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkAnalysisConfig
      extends java.lang.Object

  Configuration for network analysis.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                        |
    |--------------------------------------------------------------------|
    | `NetworkAnalysisConfig``(org.w3c.dom.Element analysisConfigElem)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                           |
    |-------------------------|------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`      | `clone``()`                                                                                                      |
    | `org.w3c.dom.Element[]` | `getGoalNodeFilters``()`                                                                                         |
    | `org.w3c.dom.Element`   | `getKShortestPathsAlgorithm``()`                                                                                 |
    | `org.w3c.dom.Element[]` | `getLinkCostCalculators``()`                                                                                     |
    | `org.w3c.dom.Element`   | `getLinkLevelSelector``()`                                                                                       |
    | `org.w3c.dom.Element`   | `getNetworkAnalysisElement``()`                                                                                  |
    | `org.w3c.dom.Element[]` | `getNetworkConstraints``()`                                                                                      |
    | `org.w3c.dom.Element[]` | `getNodeCostCalculators``()`                                                                                     |
    | `org.w3c.dom.Element`   | `getPairwiseCostCalculator``()`                                                                                  |
    | `org.w3c.dom.Element`   | `getPairwiseShortestPathsAlgorithm``()`                                                                          |
    | `org.w3c.dom.Element`   | `getShortestPathAlgorithm``()`                                                                                   |
    | `org.w3c.dom.Element`   | `getTspAlgorithm``()`                                                                                            |
    | `double`                | `getWithinCostPolygonTolerance``()`                                                                              |
    | `void`                  | `setGoalNodeFilters``(org.w3c.dom.Element[] goalNodeFilters)`                                                    |
    | `void`                  | `setKspAlgorithm``(org.w3c.dom.Element kspAlgorithm)`                                                            |
    | `void`                  | `setLinkCostCalculators``(org.w3c.dom.Element[] linkCostCalculators)`                                            |
    | `void`                  | `setLinkLevelSelector``(org.w3c.dom.Element linkLevelSelector)`                                                  |
    | `void`                  | `setNetworkConstraints``(org.w3c.dom.Element[] networkConstraints)`                                              |
    | `void`                  | `setNodeCostCalculators``(org.w3c.dom.Element[] nodeCostCalculators)`                                            |
    | `void`                  | `setPwcc``(org.w3c.dom.Element pwcc)`                                                                            |
    | `void`                  | `setPwspAlgorithm``(org.w3c.dom.Element pwspAlgorithm)`                                                          |
    | `void`                  | `setSpAlgorithm``(org.w3c.dom.Element spAlgorithm)`                                                              |
    | `void`                  | `setTspAlgorithm``(org.w3c.dom.Element tspAlgorithm)`                                                            |
    | `void`                  | `setWithinCostPolygonTolerance``(double withinCostPolygonTolerance)`                                             |
    | `void`                  | `updateNetworkAnalysisElement``()`<br>Update the networkIO element to reflect the current status of this object. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkAnalysisConfig

          public NetworkAnalysisConfig(org.w3c.dom.Element analysisConfigElem)

  <!-- -->

  - ### Method Detail

    - #### getNetworkAnalysisElement

          public org.w3c.dom.Element getNetworkAnalysisElement()

    <!-- -->

    - #### getLinkLevelSelector

          public org.w3c.dom.Element getLinkLevelSelector()

    <!-- -->

    - #### getNetworkConstraints

          public org.w3c.dom.Element[] getNetworkConstraints()

    <!-- -->

    - #### getGoalNodeFilters

          public org.w3c.dom.Element[] getGoalNodeFilters()

    <!-- -->

    - #### getLinkCostCalculators

          public org.w3c.dom.Element[] getLinkCostCalculators()

    <!-- -->

    - #### getNodeCostCalculators

          public org.w3c.dom.Element[] getNodeCostCalculators()

    <!-- -->

    - #### getShortestPathAlgorithm

          public org.w3c.dom.Element getShortestPathAlgorithm()

    <!-- -->

    - #### getKShortestPathsAlgorithm

          public org.w3c.dom.Element getKShortestPathsAlgorithm()

    <!-- -->

    - #### getPairwiseShortestPathsAlgorithm

          public org.w3c.dom.Element getPairwiseShortestPathsAlgorithm()

    <!-- -->

    - #### getPairwiseCostCalculator

          public org.w3c.dom.Element getPairwiseCostCalculator()

    <!-- -->

    - #### getTspAlgorithm

          public org.w3c.dom.Element getTspAlgorithm()

    <!-- -->

    - #### getWithinCostPolygonTolerance

          public double getWithinCostPolygonTolerance()

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### setGoalNodeFilters

          public void setGoalNodeFilters(org.w3c.dom.Element[] goalNodeFilters)

    <!-- -->

    - #### setLinkCostCalculators

          public void setLinkCostCalculators(org.w3c.dom.Element[] linkCostCalculators)

    <!-- -->

    - #### setNodeCostCalculators

          public void setNodeCostCalculators(org.w3c.dom.Element[] nodeCostCalculators)

    <!-- -->

    - #### setLinkLevelSelector

          public void setLinkLevelSelector(org.w3c.dom.Element linkLevelSelector)

    <!-- -->

    - #### setNetworkConstraints

          public void setNetworkConstraints(org.w3c.dom.Element[] networkConstraints)

    <!-- -->

    - #### setSpAlgorithm

          public void setSpAlgorithm(org.w3c.dom.Element spAlgorithm)

    <!-- -->

    - #### setKspAlgorithm

          public void setKspAlgorithm(org.w3c.dom.Element kspAlgorithm)

    <!-- -->

    - #### setPwspAlgorithm

          public void setPwspAlgorithm(org.w3c.dom.Element pwspAlgorithm)

    <!-- -->

    - #### setPwcc

          public void setPwcc(org.w3c.dom.Element pwcc)

    <!-- -->

    - #### setTspAlgorithm

          public void setTspAlgorithm(org.w3c.dom.Element tspAlgorithm)

    <!-- -->

    - #### setWithinCostPolygonTolerance

          public void setWithinCostPolygonTolerance(double withinCostPolygonTolerance)

    <!-- -->

    - #### updateNetworkAnalysisElement

          public void updateNetworkAnalysisElement()

      Update the networkIO element to reflect the current status of this object.

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

- [Prev Class](LODConfigException.md)
- [Next Class](NetworkIOConfig.md)

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
