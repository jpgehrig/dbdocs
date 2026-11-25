Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SubPath.md)
- [Next Class](Tree.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Class SystemConstraint

- java.lang.Object

- - oracle.spatial.network.SystemConstraint

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, [NetworkConstraint](NetworkConstraint.md)

  ------------------------------------------------------------------------



      public class SystemConstraint
      extends java.lang.Object
      implements NetworkConstraint

  This class defines the common network constraints for network analysis. It contains the must-avoid nodes and must-avoid links, the maximum cost, the maximun duration, the maximum distance, the maximum search depth (no of links in the path!), and a bounding MBR. This class implements NetworkConstraint interface.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SystemConstraint``(`[`Network`](Network.md)` network)`<br>Constructs an empty system constraint.                                                                                                                                                |
    | `SystemConstraint``(`[`Network`](Network.md)` network, double maxCost)`<br>Constructs a network constraint with the maximum cost.                                                                                                                |
    | `SystemConstraint``(`[`Network`](Network.md)` network, int[] mustAvoidNodes)`<br>Constructs a system constraint containing the must-avoid nodes .                                                                                                |
    | `SystemConstraint``(`[`Network`](Network.md)` network, int[] mustAvoidNodes, int[] mustAvoidLinks)`<br>Constructs a network constraint with the following constraints: the must-avoid nodes, and the must-avoid links.                           |
    | `SystemConstraint``(`[`Network`](Network.md)` network, java.util.Vector mustAvoidNodes)`<br>Constructs a network constraint with the must-avoid nodes.                                                                                           |
    | `SystemConstraint``(`[`Network`](Network.md)` network, java.util.Vector mustAvoidNodes, java.util.Vector mustAvoidLinks)`<br>Constructs a network constraint with the following constraint items: the must-avoid nodes and the must-avoid links. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                      |
    |-------------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `double`                | `getMaxCost``()`<br>Returns the maximum cost constraint.                                                                    |
    | `int`                   | `getMaxDepth``()`<br>Returns the maximum depth constraint.                                                                  |
    | `double`                | `getMaxDistance``()`<br>Returns the maximum distance constraint.                                                            |
    | `double`                | `getMaxDuration``()`                                                                                                        |
    | [`MBR`](MBR.md)         | `getMaxMBR``()`<br>Returns the maximum MBR constraint.                                                                      |
    | `java.util.Vector`      | `getMustAvoidLinks``()`<br>Returns the must-avoid links as a Vector                                                         |
    | `java.util.Vector`      | `getMustAvoidNodes``()`<br>Returns the must-avoid nodes as a Vector                                                         |
    | [`Network`](Network.md) | `getNetwork``()`<br>Returns the network that contains the consatrint.                                                       |
    | `boolean`               | `isSatisfied``(`[`AnalysisInfo`](AnalysisInfo.md)` info)`<br>Check if the system constraint is satisfied during the search. |
    | `boolean`               | `maxCostExists``()`<br>Checks if the maximum cost constraint exists.                                                        |
    | `boolean`               | `maxDepthExists``()`<br>Checks if the maximum path depth constraint exists.                                                 |
    | `boolean`               | `maxDistanceExists``()`<br>Checks if the maximum distance constraint exists.                                                |
    | `boolean`               | `maxDurationExists``()`<br>Checks if the maximum duration constraint exists.                                                |
    | `boolean`               | `maxMBRExists``()`<br>Checks if the maximum MBR constraint exists.                                                          |
    | `boolean`               | `requiresPathLinks``()`<br>Chceks if the constraint requires some or all path information.                                  |
    | `void`                  | `setMaxCost``(double maxCost)`<br>Sets the maximum cost constraint.                                                         |
    | `void`                  | `setMaxDepth``(int maxDepth)`<br>Sets the maximum depth constraint.                                                         |
    | `void`                  | `setMaxDistance``(double maxDist)`<br>Sets the maximum distance constraint.                                                 |
    | `void`                  | `setMaxDuration``(double maxDuration)`                                                                                      |
    | `void`                  | `setMaxMBR``(`[`MBR`](MBR.md)` mbr)`<br>Sets the maximum MBR constraint.                                                    |
    | `void`                  | `setMustAvoidLinks``(java.util.Vector links)`<br>Sets the must-avoid links.                                                 |
    | `void`                  | `setMustAvoidNodes``(java.util.Vector nodes)`<br>Sets the must-avoid nodes.                                                 |
    | `java.lang.String`      | `toString``()`                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SystemConstraint

          public SystemConstraint(Network network)

      Constructs an empty system constraint.
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### SystemConstraint

          public SystemConstraint(Network network,
                                  double maxCost)

      Constructs a network constraint with the maximum cost.
      Parameters:
      `network` - the specified network

      `maxCost` - the maximum cost

    <!-- -->

    - #### SystemConstraint

          public SystemConstraint(Network network,
                                  java.util.Vector mustAvoidNodes,
                                  java.util.Vector mustAvoidLinks)

      Constructs a network constraint with the following constraint items: the must-avoid nodes and the must-avoid links.
      Parameters:
      `network` - the specified network

      `mustAvoidNodes` - the must-avoid nodes in a Vector

      `mustAvoidLinks` - the must-avoid links in a Vector

    <!-- -->

    - #### SystemConstraint

          public SystemConstraint(Network network,
                                  java.util.Vector mustAvoidNodes)

      Constructs a network constraint with the must-avoid nodes.
      Parameters:
      `network` - the specified network

      `mustAvoidNodes` - the must-avoid nodes in a Vector

    <!-- -->

    - #### SystemConstraint

          public SystemConstraint(Network network,
                                  int[] mustAvoidNodes,
                                  int[] mustAvoidLinks)
                           throws NetworkDataException

      Constructs a network constraint with the following constraints: the must-avoid nodes, and the must-avoid links.
      Parameters:
      `network` - the specified network

      `mustAvoidNodes` - the array of the must-avoid node IDs

      `mustAvoidLinks` - the array of the must-avoid link IDs

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### SystemConstraint

          public SystemConstraint(Network network,
                                  int[] mustAvoidNodes)
                           throws NetworkDataException

      Constructs a system constraint containing the must-avoid nodes .
      Parameters:
      `network` - the specified network

      `mustAvoidNodes` - the array of the must-avoid node IDs

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

  <!-- -->

  - ### Method Detail

    - #### setMustAvoidNodes

          public void setMustAvoidNodes(java.util.Vector nodes)

      Sets the must-avoid nodes.
      Parameters:
      `nodes` - the must-avoid nodes as a Vector

    <!-- -->

    - #### setMustAvoidLinks

          public void setMustAvoidLinks(java.util.Vector links)

      Sets the must-avoid links.
      Parameters:
      `links` - the must-avoid links as a Vector

    <!-- -->

    - #### setMaxDepth

          public void setMaxDepth(int maxDepth)

      Sets the maximum depth constraint.
      Parameters:
      `maxDepth` - the maximum depth

    <!-- -->

    - #### setMaxCost

          public void setMaxCost(double maxCost)

      Sets the maximum cost constraint.
      Parameters:
      `maxCost` - the maximum cost

    <!-- -->

    - #### setMaxDistance

          public void setMaxDistance(double maxDist)

      Sets the maximum distance constraint.
      Parameters:
      `maxDist` - the maximum distance

    <!-- -->

    - #### setMaxMBR

          public void setMaxMBR(MBR mbr)

      Sets the maximum MBR constraint.
      Parameters:
      `mbr` - the MBR constraint

    <!-- -->

    - #### getNetwork

          public Network getNetwork()

      Returns the network that contains the consatrint.

    <!-- -->

    - #### getMustAvoidNodes

          public java.util.Vector getMustAvoidNodes()

      Returns the must-avoid nodes as a Vector

    <!-- -->

    - #### getMustAvoidLinks

          public java.util.Vector getMustAvoidLinks()

      Returns the must-avoid links as a Vector

    <!-- -->

    - #### maxCostExists

          public boolean maxCostExists()

      Checks if the maximum cost constraint exists.

    <!-- -->

    - #### maxDurationExists

          public boolean maxDurationExists()

      Checks if the maximum duration constraint exists.

    <!-- -->

    - #### maxDistanceExists

          public boolean maxDistanceExists()

      Checks if the maximum distance constraint exists.

    <!-- -->

    - #### maxMBRExists

          public boolean maxMBRExists()

      Checks if the maximum MBR constraint exists.

    <!-- -->

    - #### maxDepthExists

          public boolean maxDepthExists()

      Checks if the maximum path depth constraint exists.

    <!-- -->

    - #### getMaxCost

          public double getMaxCost()

      Returns the maximum cost constraint.

    <!-- -->

    - #### getMaxDistance

          public double getMaxDistance()

      Returns the maximum distance constraint.

    <!-- -->

    - #### getMaxMBR

          public MBR getMaxMBR()

      Returns the maximum MBR constraint.

    <!-- -->

    - #### getMaxDepth

          public int getMaxDepth()

      Returns the maximum depth constraint.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### setMaxDuration

          public void setMaxDuration(double maxDuration)

    <!-- -->

    - #### getMaxDuration

          public double getMaxDuration()

    <!-- -->

    - #### requiresPathLinks

          public boolean requiresPathLinks()

      Chceks if the constraint requires some or all path information.
      Specified by:
      [`requiresPathLinks`](NetworkConstraint.md) in interface [`NetworkConstraint`](NetworkConstraint.md)

    <!-- -->

    - #### isSatisfied

          public boolean isSatisfied(AnalysisInfo info)

      Check if the system constraint is satisfied during the search.
      Specified by:
      [`isSatisfied`](NetworkConstraint.md) in interface [`NetworkConstraint`](NetworkConstraint.md)

      Parameters:
      `info` - the analysis information for the network constraint

      See Also:
      [`AnalysisInfo`](AnalysisInfo.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](SubPath.md)
- [Next Class](Tree.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
