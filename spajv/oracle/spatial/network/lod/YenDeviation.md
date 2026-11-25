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

- [Prev Class](XMLConfigurable.md)
- Next Class

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

## Class YenDeviation

- java.lang.Object

- - oracle.spatial.network.lod.YenDeviation

<!-- -->

- All Implemented Interfaces:
  [KShortestPaths](KShortestPaths.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class YenDeviation
      extends java.lang.Object
      implements KShortestPaths, XMLConfigurable

  This class implements Yen's Deviation Algorithm for finding the k shortest loopless paths. Reference: J.Y.Yen. Finding the k shortest loopless paths in a network. Management Science 17:712-716, 1971.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `YenDeviation``()`<br>Default constructor.                                                                                                                                                                                       |
    | `YenDeviation``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`ShortestPath`](ShortestPath.md)` spAlgorithm)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                                                                                               |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                        | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                                                                                                                                                                                                                                                                |
    | `void`                                    | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter.                                                                                                                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]` | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter, int direction)`<br>Returns the k shortest paths from the start point to the end point.                              |
    | `void`                                    | `setLinkLevelSelector``(`[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Sets link level selector.                                                                                                                                                                                                                                             |
    | `void`                                    | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this k shortest paths algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### YenDeviation

          public YenDeviation()

      Default constructor. After this object is created using this default constructor, method init(Element) should be called to initialize it.

    <!-- -->

    - #### YenDeviation

          public YenDeviation(NetworkExplorer ne,
                              LinkCostCalculator[] lccs,
                              NodeCostCalculator[] nccs,
                              ShortestPath spAlgorithm)

  <!-- -->

  - ### Method Detail

    - #### setLinkLevelSelector

          public void setLinkLevelSelector(LinkLevelSelector lls)

      Description copied from interface: [`KShortestPaths`](KShortestPaths.md)
      Sets link level selector.
      Specified by:
      [`setLinkLevelSelector`](KShortestPaths.md) in interface [`KShortestPaths`](KShortestPaths.md)

      Parameters:
      `lls` - link level selector

    <!-- -->

    - #### kShortestPaths

          public LogicalSubPath[] kShortestPaths(PointOnNet[] startPoints,
                                                 PointOnNet[] endPoints,
                                                 int k,
                                                 LODNetworkConstraint constraint,
                                                 PathFilter pathFilter,
                                                 int direction)
                                          throws LODNetworkException

      Description copied from interface: [`KShortestPaths`](KShortestPaths.md)
      Returns the k shortest paths from the start point to the end point.
      Specified by:
      [`kShortestPaths`](KShortestPaths.md) in interface [`KShortestPaths`](KShortestPaths.md)

      Parameters:
      `startPoints` - candidate start points

      `endPoints` - candidate end points

      `k` - max number of paths to be returned

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`KShortestPaths`](KShortestPaths.md)
      This method allows caller to pass the network analyst object to this k shortest paths algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](KShortestPaths.md) in interface [`KShortestPaths`](KShortestPaths.md)

    <!-- -->

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

- [Prev Class](XMLConfigurable.md)
- Next Class

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
