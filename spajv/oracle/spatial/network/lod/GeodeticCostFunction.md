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

- [Prev Class](FilePairwisePathResultIO.md)
- [Next Class](GeodeticPairwiseCostCalculator.md)

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

## Class GeodeticCostFunction

- java.lang.Object

- - oracle.spatial.network.lod.GeodeticCostFunction

<!-- -->

- All Implemented Interfaces:
  [HeuristicCostFunction](HeuristicCostFunction.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class GeodeticCostFunction
      extends java.lang.Object
      implements HeuristicCostFunction, XMLConfigurable

  This class implements the heuristic cost as the 2D geodetic distance in meters between the current node and the goal node.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                             |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeodeticCostFunction``()`                                                                                                                                              |
    | `GeodeticCostFunction``(int userDataCategory, int geometryUserDataIndex)`<br>Creates a GeodeticCostFunction instance.                                                   |
    | `GeodeticCostFunction``(int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex)`<br>Creates a GeodeticCostFunction instance.                            |
    | `GeodeticCostFunction``(int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex, int geometryUserDataIndex)`<br>Creates a GeodeticCostFunction instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                      |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`           | `getHeuristicCost``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)` currentPoint, `[`HeavyPointOnNet`](HeavyPointOnNet.md)` goalPoint)`<br>Returns the heuristic cost between the current node and the goal node. |
    | `double`           | `getHeuristicCost``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)` currentPoint, `[`LogicalNode`](LogicalNode.md)` goalNode)`<br>Returns the heuristic cost between the current node and the goal node.          |
    | `double`           | `getHeuristicCost``(`[`LogicalNode`](LogicalNode.md)` currentNode, `[`HeavyPointOnNet`](HeavyPointOnNet.md)` goalPoint)`<br>Returns the heuristic cost between the current node and the goal node.          |
    | `double`           | `getHeuristicCost``(`[`LogicalNode`](LogicalNode.md)` currentNode, `[`LogicalNode`](LogicalNode.md)` goalNode)`<br>Returns the heuristic cost between the current node and the goal node.                   |
    | `int[]`            | `getUserDataCategories``()`                                                                                                                                                                                 |
    | `java.lang.String` | `getXMLSchema``()`                                                                                                                                                                                          |
    | `void`             | `init``(org.w3c.dom.Element parameter)`                                                                                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[HeuristicCostFunction](HeuristicCostFunction.md)

      [`getHeuristicCost`](HeuristicCostFunction.md)`, `[`getUserDataCategories`](HeuristicCostFunction.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md)

      [`getXMLSchema`](XMLConfigurable.md)`, `[`init`](XMLConfigurable.md)

<!-- -->

- - ### Constructor Detail

    - #### GeodeticCostFunction

          public GeodeticCostFunction()

    <!-- -->

    - #### GeodeticCostFunction

          public GeodeticCostFunction(int userDataCategory,
                                      int xCoordUserDataIndex,
                                      int yCoordUserDataIndex,
                                      int geometryUserDataIndex)

      Creates a GeodeticCostFunction instance. The input parameters are interpreted as follows:
      If neither xCoordUserDataName nor yCoordUserDataIndex is -1, then the the heuristic cost is computed using the x and y coordinates stored as user data of the nodes;
      Else if geometryUserDataIndex is not -1, then the heuristic cost is computed using the JGeometry object stored as user data of the nodes.
      Parameters:
      `userDataCategory` - user data category

      `xCoordUserDataIndex` - user data index registered for x coordinates of the nodes or points on link

      `yCoordUserDataIndex` - user data index registered for y coordinates of the nodes or points on link

      `geometryUserDataIndex` - user date index registered for geometries of the nodes or points on link

    <!-- -->

    - #### GeodeticCostFunction

          public GeodeticCostFunction(int userDataCategory,
                                      int xCoordUserDataIndex,
                                      int yCoordUserDataIndex)

      Creates a GeodeticCostFunction instance.
      Parameters:
      `userDataCategory` - user data category

      `xCoordUserDataIndex` - user data index registered for x coordinates of the nodes or points on link

      `yCoordUserDataIndex` - user data index registered for y coordinates of the nodes or points on link

    <!-- -->

    - #### GeodeticCostFunction

          public GeodeticCostFunction(int userDataCategory,
                                      int geometryUserDataIndex)

      Creates a GeodeticCostFunction instance.
      Parameters:
      `userDataCategory` - user data category

      `geometryUserDataIndex` - user date index registered for geometries of the nodes or points on link

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(org.w3c.dom.Element parameter)

    <!-- -->

    - #### getXMLSchema

          public java.lang.String getXMLSchema()

    <!-- -->

    - #### getHeuristicCost

          public double getHeuristicCost(HeavyPointOnNet currentPoint,
                                         HeavyPointOnNet goalPoint)

      Returns the heuristic cost between the current node and the goal node.
      Parameters:

      `currentPoint` - current point

      `goalPoint` - goal point

      Returns:

    <!-- -->

    - #### getHeuristicCost

          public double getHeuristicCost(LogicalNode currentNode,
                                         LogicalNode goalNode)

      Returns the heuristic cost between the current node and the goal node.
      Parameters:

      `currentNode` - current node

      `goalNode` - goal node

      Returns:

    <!-- -->

    - #### getHeuristicCost

          public double getHeuristicCost(LogicalNode currentNode,
                                         HeavyPointOnNet goalPoint)

      Returns the heuristic cost between the current node and the goal node.
      Parameters:

      `currentNode` - current node

      `goalPoint` - goal point

      Returns:

    <!-- -->

    - #### getHeuristicCost

          public double getHeuristicCost(HeavyPointOnNet currentPoint,
                                         LogicalNode goalNode)

      Returns the heuristic cost between the current node and the goal node.
      Parameters:

      `currentPoint` - current point

      `goalNode` - goal node

      Returns:

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

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

- [Prev Class](FilePairwisePathResultIO.md)
- [Next Class](GeodeticPairwiseCostCalculator.md)

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
