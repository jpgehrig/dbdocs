Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEEditionManager.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.edit

## Interface NFEManipulator

- All Known Implementing Classes:
  [NFEBasicModelManipulator](NFEBasicModelManipulator.md)

  ------------------------------------------------------------------------



      public interface NFEManipulator

  An NFEManipulator implementation should ease in-memory edition tasks such as adding, removing and moving features. It aids on enforcing connectivity rules and constraints by calling the components in charge of such tasks automatically when an edition activity is performed.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                  |
    |----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                           | `applyFeatureClass``(`[`NFEFeature`](../feature/NFEFeature.md)` feature, `[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass)`<br>Enforces all the attribute constraints defined in the feature class to the given feature                                                                                                                                   |
    | [`NFEFeature`](../feature/NFEFeature.md)                                         | `createFeature``(`[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass)`<br>Creates an empty Feature (with no Feature Element) of the specified Feature Class                                                                                                                                                                                                  |
    | [`NFEFeature`](../feature/NFEFeature.md)                                         | `createLineFeature``(`[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass, `[`JGeometry`](../../../../geometry/JGeometry.md)` lineGeom, boolean enforceRules, double tolerance)`<br>Creates a new line feature and its corresponding feature element(s) and network elements.                                                                                 |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                           | `createLineFeatureElement``(`[`NFELink`](../network/NFELink.md)` link, double startPos, double endPos, long featureLayerId, long sequence)`<br>Creates a new feature containing one line feature element.                                                                                                                                                               |
    | [`NFELink`](../network/NFELink.md)                                               | `createLink``(`[`NFENode`](../network/NFENode.md)` startNode, `[`NFENode`](../network/NFENode.md)` endNode)`<br>Creates a new link.                                                                                                                                                                                                                                     |
    | [`NFELink`](../network/NFELink.md)                                               | `createLink``(`[`NFENode`](../network/NFENode.md)` startNode, `[`NFENode`](../network/NFENode.md)` endNode, `[`JGeometry`](../../../../geometry/JGeometry.md)` geom)`<br>Creates a new link.                                                                                                                                                                            |
    | [`NFENode`](../network/NFENode.md)                                               | `createNode``(double[] pointOrds)`<br>Creates a new node.                                                                                                                                                                                                                                                                                                               |
    | [`NFENode`](../network/NFENode.md)                                               | `createNode``(`[`JGeometry`](../../../../geometry/JGeometry.md)` geom)`<br>Creates a new node.                                                                                                                                                                                                                                                                          |
    | [`NFEFeature`](../feature/NFEFeature.md)                                         | `createPointFeature``(`[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass, `[`JGeometry`](../../../../geometry/JGeometry.md)` pointGeom, boolean enforceRules, double tolerance)`<br>Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node.                                                     |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                           | `createPOLFeatureElement``(`[`NFELink`](../network/NFELink.md)` link, double pos, long featureLayerId, long sequence)`<br>Creates a new feature containing one PointOnLink feature element.                                                                                                                                                                             |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                           | `createPONFeatureElement``(`[`NFENode`](../network/NFENode.md)` node, long featureLayerId, long sequence)`<br>Creates a new feature containing one PointOnNode feature element.                                                                                                                                                                                         |
    | `java.util.List<`[`NFEFeature`](../feature/NFEFeature.md)`>`                     | `createPredefinedConnectedPointFeatures``(java.util.Collection<`[`NFEPredefinedConnectedPoint`](../feature/NFEPredefinedConnectedPoint.md)`> predefConnPoints, `[`JGeometry`](../../../../geometry/JGeometry.md)` lineGeom)`<br>Creates the predefined points defined in the line feature class along a line geometry using the predefined points position percentages. |
    | [`NFEFeature`](../feature/NFEFeature.md)                                         | `createStandalonePointFeature``(`[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featClass, `[`JGeometry`](../../../../geometry/JGeometry.md)` pointGeom)`<br>Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node.                                                                                   |
    | `void`                                                                           | `enforceRules``(java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> featElems, double tolerance)`<br>Detect interactions and enforces rules if needed for the given feature elements                                                                                                                                                         |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `getAdjacentFeatureElements``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem, int depth)`<br>Gets all the feature elements connected to the given feature element                                                                                                                                                                                    |
    | [`NFEConnectionManager`](NFEConnectionManager.md)                                | `getConnectionManager``()`<br>Gets the connection manager used by the current NFEModel                                                                                                                                                                                                                                                                                  |
    | [`NFEInteractionEngine`](../spatial/interaction/NFEInteractionEngine.md)         | `getInteractionEngine``()`<br>Gets the current interaction engine instance                                                                                                                                                                                                                                                                                              |
    | [`NFERulesEngine`](../rule/NFERulesEngine.md)                                    | `getRulesEngine``()`<br>Gets the rules engine instance that is currently used by the model                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                        | `isAllowedPoint``(double x, double y)`<br>Tells whether a point is inside the boundaries defined by the model.                                                                                                                                                                                                                                                          |
    | `boolean`                                                                        | `isAllowedPoint``(java.awt.geom.Point2D point)`<br>Tells whether a point is inside the boundaries defined by the model.                                                                                                                                                                                                                                                 |
    | `boolean`                                                                        | `isAllowedRectangle``(double x, double y, double w, double h)`<br>Tells whether a rectangle is inside the boundaries defined by the model.                                                                                                                                                                                                                              |
    | `boolean`                                                                        | `isAllowedRectangle``(java.awt.geom.Rectangle2D rectangle)`<br>Tells whether a rectangle is inside the boundaries defined by the model.                                                                                                                                                                                                                                 |
    | `boolean`                                                                        | `isValidPoint``(double x, double y)`<br>Returns true if the point location is valid, false otherwise.                                                                                                                                                                                                                                                                   |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                           | `moveFeatureElementToNetworkElement``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem, `[`NFENetworkElement`](../network/NFENetworkElement.md)` destNetElem, double destStartPos)`<br>Changes a feature element's underlying network element                                                                                                          |
    | `java.util.Collection<`[`NFENetworkElement`](../network/NFENetworkElement.md)`>` | `removedDanglingNetworkElements``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` fromNetElem)`<br>Removes any dangling network element connected to the given network element (including the passed network element if it is itself a dangling element).                                                                                                      |
    | `boolean`                                                                        | `removeFeature``(`[`NFEFeature`](../feature/NFEFeature.md)` feature)`<br>Removes a feature from the model along with its feature elements and network elements                                                                                                                                                                                                          |
    | `boolean`                                                                        | `removeFeatureElement``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Removes a feature element from its feature along with the network element where the feature element is placed.                                                                                                                                                           |
    | `void`                                                                           | `reverseLineFeatureDirection``(`[`NFEFeature`](../feature/NFEFeature.md)` lineFeature)`<br>Reverse the direction of all the links containing feature elements of the given feature                                                                                                                                                                                      |
    | `void`                                                                           | `reverseLinkDirection``(`[`NFELink`](../network/NFELink.md)` link)`<br>Changes the direction of a link by changing the order of its line ordinates                                                                                                                                                                                                                      |
    | `void`                                                                           | `setFeatureActive``(`[`NFEFeature`](../feature/NFEFeature.md)` feature, boolean active)`<br>Sets the feature's active property                                                                                                                                                                                                                                          |
    | `void`                                                                           | `setFeatureBidirected``(`[`NFEFeature`](../feature/NFEFeature.md)` feature, boolean bidirected)`<br>Sets whether a feature is bidirected or not                                                                                                                                                                                                                         |
    | `void`                                                                           | `setNetworkElementGeometry``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` netElem, `[`JGeometry`](../../../../geometry/JGeometry.md)` newGeom)`<br>Sets a new geometry to the specified network element.                                                                                                                                                    |
    | `void`                                                                           | `setNetworkElementsGeometries``(`[`NFENetworkElement`](../network/NFENetworkElement.md)`[] netElems, `[`JGeometry`](../../../../geometry/JGeometry.md)`[] newGeoms, boolean enforceRules, double tolerance)`<br>Changes geometries to a group of network elements.                                                                                                      |
    | `void`                                                                           | `updateLinkGeometry``(`[`NFELink`](../network/NFELink.md)` link)`<br>Updates the link's geometry to reflect the position of its start and end points.                                                                                                                                                                                                                   |

<!-- -->

- - ### Method Detail

    - #### getConnectionManager

          NFEConnectionManager getConnectionManager()

      Gets the connection manager used by the current NFEModel
      Returns:
      a connection manager instance

    <!-- -->

    - #### getInteractionEngine

          NFEInteractionEngine getInteractionEngine()

      Gets the current interaction engine instance
      Returns:
      an interaction engine instance

    <!-- -->

    - #### isAllowedPoint

          boolean isAllowedPoint(java.awt.geom.Point2D point)

      Tells whether a point is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Parameters:
      `point` - a java point instance

      Returns:
      true if the point is inside the model boundaries

    <!-- -->

    - #### isAllowedPoint

          boolean isAllowedPoint(double x,
                                 double y)

      Tells whether a point is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Parameters:
      `x` - the point's x ordinate

      `y` - the point's y ordinate

      Returns:
      true if the point is inside the model boundaries

    <!-- -->

    - #### isAllowedRectangle

          boolean isAllowedRectangle(java.awt.geom.Rectangle2D rectangle)

      Tells whether a rectangle is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Parameters:
      `rectangle` - a java rectangle instance

      Returns:
      true if the rectangle is inside the model boundaries

    <!-- -->

    - #### isAllowedRectangle

          boolean isAllowedRectangle(double x,
                                     double y,
                                     double w,
                                     double h)

      Tells whether a rectangle is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Parameters:

      `x` - the rectangle's lower left corner x ordinate

      `y` - the rectangle's lower left corner y ordinate

      `w` - the rectangle's width

      `h` - the rectangle's height

      Returns:

    <!-- -->

    - #### isValidPoint

          boolean isValidPoint(double x,
                               double y)

      Returns true if the point location is valid, false otherwise. A point location is consider invalid if the location is outside the model boundaries.
      Parameters:
      `x` - the x of the point

      `y` - the y of the point

      Returns:
      true if the point location is valid, false otherwise

    <!-- -->

    - #### removedDanglingNetworkElements

          java.util.Collection<NFENetworkElement> removedDanglingNetworkElements(NFENetworkElement fromNetElem)

      Removes any dangling network element connected to the given network element (including the passed network element if it is itself a dangling element). In FromScratch mode, a network element is considered a dangling element if it is a link without features or an unconnected node without features.
      Parameters:
      `fromNetElem` - the network element from where the search begins

      Returns:
      a collection containing all the removed dangling points

    <!-- -->

    - #### reverseLinkDirection

          void reverseLinkDirection(NFELink link)

      Changes the direction of a link by changing the order of its line ordinates
      Parameters:
      `link` - a link instance

    <!-- -->

    - #### setNetworkElementGeometry

          void setNetworkElementGeometry(NFENetworkElement netElem,
                                         JGeometry newGeom)

      Sets a new geometry to the specified network element. All the connected network elements' geometries are updated accordingly.
      Parameters:
      `netElem` - the network which geometry will be changed

      `newGeom` - the new network element's geometry

    <!-- -->

    - #### setNetworkElementsGeometries

          void setNetworkElementsGeometries(NFENetworkElement[] netElems,
                                            JGeometry[] newGeoms,
                                            boolean enforceRules,
                                            double tolerance)

      Changes geometries to a group of network elements. Optionally enforces rules. Tolerance is only required is enforce rules is true.
      Parameters:
      `netElems` - An array of network elements which geometries will be changed

      `newGeoms` - An array of new geometries. The length of this array must be equal than the netElems array.

      `enforceRules` - if true, rules will be executed for the changed elements

      `tolerance` - tolerance used for detecting interactions if rules are enforced

    <!-- -->

    - #### removeFeature

          boolean removeFeature(NFEFeature feature)

      Removes a feature from the model along with its feature elements and network elements
      Parameters:
      `feature` - a feature instance

      Returns:
      true if the feature was removed successfully

    <!-- -->

    - #### removeFeatureElement

          boolean removeFeatureElement(NFEFeatureElement featElem)

      Removes a feature element from its feature along with the network element where the feature element is placed.
      Parameters:
      `featElem` - a feature element instance

      Returns:
      true if the feature element was removed successfully

    <!-- -->

    - #### applyFeatureClass

          void applyFeatureClass(NFEFeature feature,
                                 NFEFeatureClass featClass)

      Enforces all the attribute constraints defined in the feature class to the given feature
      Parameters:
      `feature` - a feature instance

      `featClass` - a feature class instance

    <!-- -->

    - #### setFeatureActive

          void setFeatureActive(NFEFeature feature,
                                boolean active)

      Sets the feature's active property
      Parameters:
      `feature` - a feature instance

      `active` - the active property value

    <!-- -->

    - #### setFeatureBidirected

          void setFeatureBidirected(NFEFeature feature,
                                    boolean bidirected)

      Sets whether a feature is bidirected or not
      Parameters:
      `feature` - a feature instance

      `bidirected` - true for bidirected

    <!-- -->

    - #### reverseLineFeatureDirection

          void reverseLineFeatureDirection(NFEFeature lineFeature)

      Reverse the direction of all the links containing feature elements of the given feature
      Parameters:
      `lineFeature` - a line feature instance

    <!-- -->

    - #### moveFeatureElementToNetworkElement

          NFEFeatureElement moveFeatureElementToNetworkElement(NFEFeatureElement featElem,
                                                               NFENetworkElement destNetElem,
                                                               double destStartPos)

      Changes a feature element's underlying network element
      Parameters:
      `featElem` - the feature element to be modified

      `destNetElem` - the new underlying network element

      `destStartPos` - destination start position (in percent)

      Returns:
      moved feature element

    <!-- -->

    - #### updateLinkGeometry

          void updateLinkGeometry(NFELink link)

      Updates the link's geometry to reflect the position of its start and end points. If the link's geometry has not been set (it's null), it creates a straight line from the start to the end node.
      Parameters:
      `link` - a link instance

    <!-- -->

    - #### createFeature

          NFEFeature createFeature(NFEFeatureClass featClass)

      Creates an empty Feature (with no Feature Element) of the specified Feature Class
      Parameters:
      `featClass` - A Feature Class instance. It is expected to be a well formed instance, containing a reference to the Feature Layer it belongs to.

      Returns:
      a new empty feature instance

    <!-- -->

    - #### createPointFeature

          NFEFeature createPointFeature(NFEFeatureClass featClass,
                                        JGeometry pointGeom,
                                        boolean enforceRules,
                                        double tolerance)

      Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node.
      Parameters:
      `featClass` - a point feature class instance

      `pointGeom` - a java point instance

      `enforceRules` - if true, rules will be executed for this new point feature

      `tolerance` - tolerance used for detecting interactions if rules are enforced

      Returns:
      a new feature containing a point feature element

    <!-- -->

    - #### createStandalonePointFeature

          NFEFeature createStandalonePointFeature(NFEFeatureClass featClass,
                                                  JGeometry pointGeom)

      Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node. Neither, the feature or the network element are added to a feature layer nor the network
      Parameters:

      `featClass` - a point feature class

      `pointGeom` - a java point instance

      Returns:

    <!-- -->

    - #### createLineFeature

          NFEFeature createLineFeature(NFEFeatureClass featClass,
                                       JGeometry lineGeom,
                                       boolean enforceRules,
                                       double tolerance)

      Creates a new line feature and its corresponding feature element(s) and network elements. If the feature class contains predefined point features they are created too. Feature elements are created accordingly.
      Parameters:
      `featClass` - a line feature class

      `lineGeom` - a line string geometry

      `enforceRules` - whether rules must be enforced after creating the feature

      `tolerance` - tolerance used for detecting interactions if rules are enforced

      Returns:
      a new feature containing one line feature element

    <!-- -->

    - #### createPredefinedConnectedPointFeatures

          java.util.List<NFEFeature> createPredefinedConnectedPointFeatures(java.util.Collection<NFEPredefinedConnectedPoint> predefConnPoints,
                                                                            JGeometry lineGeom)

      Creates the predefined points defined in the line feature class along a line geometry using the predefined points position percentages.
      Parameters:
      `predefConnPoints` - a collection predefined connected point descriptors

      `lineGeom` - the line geometry where the points will be placed

      Returns:
      a list of point features

    <!-- -->

    - #### getAdjacentFeatureElements

          java.util.Collection<NFEFeatureElement> getAdjacentFeatureElements(NFEFeatureElement featElem,
                                                                             int depth)

      Gets all the feature elements connected to the given feature element
      Parameters:
      `featElem` - a feature element

      `depth` - for how many levels connected elements must be retrieved

      Returns:
      a collection of connected feature elements

    <!-- -->

    - #### createNode

          NFENode createNode(double[] pointOrds)

      Creates a new node. The node is added automatically to the network
      Parameters:
      `pointOrds` - a point ordinates.

      Returns:
      a new node instance

    <!-- -->

    - #### createNode

          NFENode createNode(JGeometry geom)

      Creates a new node. The node is added automatically to the network
      Parameters:
      `geom` - a point geometry

      Returns:
      a new node instance

    <!-- -->

    - #### createLink

          NFELink createLink(NFENode startNode,
                             NFENode endNode)

      Creates a new link. The links geometry will be a straight line from startNode to endNode. The link is added automatically to the network.
      Parameters:
      `startNode` - the link's start node. The node must exist in the network.

      `endNode` - the link's end node. The node must exist in the network.

      Returns:
      a new link instance

    <!-- -->

    - #### createLink

          NFELink createLink(NFENode startNode,
                             NFENode endNode,
                             JGeometry geom)

      Creates a new link. The link is added automatically to the network.
      Parameters:
      `startNode` - the link's start node. The node must exist in the network.

      `endNode` - the link's end node. The node must exist in the network.

      `geom` - a line string geometry

      Returns:
      a new link instance

    <!-- -->

    - #### createPONFeatureElement

          NFEFeatureElement createPONFeatureElement(NFENode node,
                                                    long featureLayerId,
                                                    long sequence)

      Creates a new feature containing one PointOnNode feature element. The feature is added automatically to its feature layer.
      Parameters:
      `node` - the underlying node

      `featureLayerId` - the ID of feature Layer where the feature belongs

      `sequence` - the feature element's sequence number

      Returns:
      a new feature element instance

    <!-- -->

    - #### createPOLFeatureElement

          NFEFeatureElement createPOLFeatureElement(NFELink link,
                                                    double pos,
                                                    long featureLayerId,
                                                    long sequence)

      Creates a new feature containing one PointOnLink feature element. The feature is added automatically to its feature layer.
      Parameters:
      `link` - the underlying link

      `pos` - position of the POL feature element. Relative to the link's length

      `featureLayerId` - the ID of feature Layer where the feature belongs

      `sequence` - the feature element's sequence number

      Returns:
      a new feature element instance

    <!-- -->

    - #### createLineFeatureElement

          NFEFeatureElement createLineFeatureElement(NFELink link,
                                                     double startPos,
                                                     double endPos,
                                                     long featureLayerId,
                                                     long sequence)

      Creates a new feature containing one line feature element. The feature is added automatically to its feature layer.
      Parameters:
      `link` - the underlying link

      `startPos` - start position of the line feature element. Relative to the link's length

      `endPos` - end position of the line feature element. Relative to the link's length

      `featureLayerId` - the ID of the feature layer the feature belongs

      `sequence` - the feature element's sequence number

      Returns:
      a new feature element instance

    <!-- -->

    - #### getRulesEngine

          NFERulesEngine getRulesEngine()

      Gets the rules engine instance that is currently used by the model
      Returns:
      a rules engine instance

    <!-- -->

    - #### enforceRules

          void enforceRules(java.util.Collection<NFEFeatureElement> featElems,
                            double tolerance)

      Detect interactions and enforces rules if needed for the given feature elements
      Parameters:
      `featElems` - a collection of feature elements

      `tolerance` - tolerance use for detecting interactions

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEEditionManager.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
