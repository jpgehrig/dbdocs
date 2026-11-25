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

- [Prev Class](NetworkIO.md)
- [Next Class](NetworkUpdate.md)

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

## Class NetworkSearch

- java.lang.Object

- - oracle.spatial.network.lod.NetworkSearch

<!-- -->

- Direct Known Subclasses:
  [BreadthFirstSearch](BreadthFirstSearch.md)

  ------------------------------------------------------------------------



      public class NetworkSearch
      extends java.lang.Object

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NetworkSearch``()`                                                                                                                                                                                                                                                                                                 |
    | `NetworkSearch``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls, `[`PriorityQueue`](PriorityQueue.md)`<`[`VisitedNode`](VisitedNode.md)`> queue)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                                                                                                                                                                      |
    |----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Feature`](Feature.md)`[]`                              | `findConnectedFeatures``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int[] featureLayers, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter, int direction)`<br>Returns the features within the given cost and the paths to/from them. |
    | [`LinkCostCalculator`](LinkCostCalculator.md)`[]`        | `getLinkCostCalculators``()`                                                                                                                                                                                                                                                                                |
    | [`LinkLevelSelector`](LinkLevelSelector.md)              | `getLinkLevelSelector``()`                                                                                                                                                                                                                                                                                  |
    | [`NodeCostCalculator`](NodeCostCalculator.md)`[]`        | `getNodeCostCalculators``()`                                                                                                                                                                                                                                                                                |
    | `java.lang.String`                                       | `getXMLSchema``()`                                                                                                                                                                                                                                                                                          |
    | `void`                                                   | `init``(org.w3c.dom.Element parameter)`                                                                                                                                                                                                                                                                     |
    | `oracle.spatial.network.lod.NetworkSearch.TmpSearchData` | `initSearch``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`                                                                                                                   |
    | `static `[`PathFeature`](PathFeature.md)                 | `preparePathFeature``(`[`LogicalSubPath`](LogicalSubPath.md)` subPath, long pathId)`                                                                                                                                                                                                                        |
    | `void`                                                   | `reset``()`                                                                                                                                                                                                                                                                                                 |
    | `void`                                                   | `setInitialAnalysisInfo``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`                                                                                                                                                                                                                          |
    | `void`                                                   | `setLinkCostCalculators``(`[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs)`                                                                                                                                                                                                                          |
    | `void`                                                   | `setLinkLevelSelector``(`[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`                                                                                                                                                                                                                                 |
    | `void`                                                   | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`                                                                                                                                                                                                                                      |
    | `void`                                                   | `setNetworkExplorer``(`[`NetworkExplorer`](NetworkExplorer.md)` ne)`                                                                                                                                                                                                                                        |
    | `void`                                                   | `setNodeCostCalculators``(`[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs)`                                                                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkSearch

          public NetworkSearch()

    <!-- -->

    - #### NetworkSearch

          public NetworkSearch(NetworkExplorer ne,
                               LinkCostCalculator[] lccs,
                               NodeCostCalculator[] nccs,
                               LinkLevelSelector lls,
                               PriorityQueue<VisitedNode> queue)

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(org.w3c.dom.Element parameter)

    <!-- -->

    - #### getXMLSchema

          public java.lang.String getXMLSchema()

    <!-- -->

    - #### setNetworkExplorer

          public void setNetworkExplorer(NetworkExplorer ne)

    <!-- -->

    - #### setInitialAnalysisInfo

          public void setInitialAnalysisInfo(LODAnalysisInfo analysisInfo)

    <!-- -->

    - #### initSearch

          public oracle.spatial.network.lod.NetworkSearch.TmpSearchData initSearch(PointOnNet[] startPoints,
                                                                                   PointOnNet[] endPoints,
                                                                                   LODNetworkConstraint constraint,
                                                                                   int direction)
                                                                            throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getLinkLevelSelector

          public LinkLevelSelector getLinkLevelSelector()

    <!-- -->

    - #### setLinkLevelSelector

          public void setLinkLevelSelector(LinkLevelSelector lls)

    <!-- -->

    - #### getLinkCostCalculators

          public LinkCostCalculator[] getLinkCostCalculators()

    <!-- -->

    - #### setLinkCostCalculators

          public void setLinkCostCalculators(LinkCostCalculator[] lccs)

    <!-- -->

    - #### getNodeCostCalculators

          public NodeCostCalculator[] getNodeCostCalculators()

    <!-- -->

    - #### setNodeCostCalculators

          public void setNodeCostCalculators(NodeCostCalculator[] nccs)

    <!-- -->

    - #### preparePathFeature

          public static PathFeature preparePathFeature(LogicalSubPath subPath,
                                                       long pathId)
                                                throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

    <!-- -->

    - #### reset

          public void reset()

    <!-- -->

    - #### findConnectedFeatures

          public Feature[] findConnectedFeatures(PointOnNet[] startPoints,
                                                 int[] featureLayers,
                                                 LODNetworkConstraint constraint,
                                                 FeatureFilter featureFilter,
                                                 int direction)
                                          throws LODNetworkException

      Returns the features within the given cost and the paths to/from them.
      Parameters:
      `startPoints` -

      `featureLayers` -

      `direction` -

      `constraint` -

      `featureFilter` -

      Returns:
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

- [Prev Class](NetworkIO.md)
- [Next Class](NetworkUpdate.md)

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
