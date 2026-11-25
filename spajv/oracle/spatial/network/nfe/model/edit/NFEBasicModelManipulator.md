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

- Prev Class
- [Next Class](NFEChangesKeeper.md)

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

## Class NFEBasicModelManipulator

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEBasicModelManipulator

<!-- -->

- All Implemented Interfaces:
  [NFEManipulator](NFEManipulator.md)

  ------------------------------------------------------------------------



      public class NFEBasicModelManipulator
      extends java.lang.Object
      implements NFEManipulator

  The default implementation of NFEModelManipulator

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `NFEBasicModelManipulator``(`[`NFEModel`](../NFEModel.md)` model)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

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
    | `static boolean`                                                                 | `isFeatureElementCompatibleWithFeatureClass``(`[`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md)` feType, `[`NFEFeatureClass`](../feature/NFEFeatureClass.md)` featureClass)`                                                                                                                                                    |
    | `static boolean`                                                                 | `isFeatureElementCompatibleWithNetworkElement``(`[`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md)` feType, `[`NFENetworkElement`](../network/NFENetworkElement.md)` networkElement)`                                                                                                                                            |
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
    | `void`                                                                           | `updateLinkGeometry``(`[`NFELink`](../network/NFELink.md)` link)`<br>Updates the link's geometry so reflect the position of its start and end points.                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicModelManipulator

          public NFEBasicModelManipulator(NFEModel model)

  <!-- -->

  - ### Method Detail

    - #### getConnectionManager

          public NFEConnectionManager getConnectionManager()

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Gets the connection manager used by the current NFEModel
      Specified by:
      [`getConnectionManager`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Returns:
      a connection manager instance

    <!-- -->

    - #### getInteractionEngine

          public NFEInteractionEngine getInteractionEngine()

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Gets the current interaction engine instance
      Specified by:
      [`getInteractionEngine`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Returns:
      an interaction engine instance

    <!-- -->

    - #### isAllowedPoint

          public boolean isAllowedPoint(java.awt.geom.Point2D point)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Tells whether a point is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Specified by:
      [`isAllowedPoint`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `point` - a java point instance

      Returns:
      true if the point is inside the model boundaries

    <!-- -->

    - #### isAllowedPoint

          public boolean isAllowedPoint(double x,
                                        double y)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Tells whether a point is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Specified by:
      [`isAllowedPoint`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `x` - the point's x ordinate

      `y` - the point's y ordinate

      Returns:
      true if the point is inside the model boundaries

    <!-- -->

    - #### isAllowedRectangle

          public boolean isAllowedRectangle(java.awt.geom.Rectangle2D rectangle)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Tells whether a rectangle is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Specified by:
      [`isAllowedRectangle`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `rectangle` - a java rectangle instance

      Returns:
      true if the rectangle is inside the model boundaries

    <!-- -->

    - #### isAllowedRectangle

          public boolean isAllowedRectangle(double x,
                                            double y,
                                            double w,
                                            double h)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Tells whether a rectangle is inside the boundaries defined by the model. The boundaries are defined at the geometry descriptor when the model is created.
      Specified by:

      [`isAllowedRectangle`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:

      `x` - the rectangle's lower left corner x ordinate

      `y` - the rectangle's lower left corner y ordinate

      `w` - the rectangle's width

      `h` - the rectangle's height

      Returns:

    <!-- -->

    - #### isValidPoint

          public boolean isValidPoint(double x,
                                      double y)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Returns true if the point location is valid, false otherwise. A point location is consider invalid if the location is outside the model boundaries.
      Specified by:
      [`isValidPoint`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `x` - the x of the point

      `y` - the y of the point

      Returns:
      true if the point location is valid, false otherwise

    <!-- -->

    - #### removedDanglingNetworkElements

          public java.util.Collection<NFENetworkElement> removedDanglingNetworkElements(NFENetworkElement fromNetElem)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Removes any dangling network element connected to the given network element (including the passed network element if it is itself a dangling element). In FromScratch mode, a network element is considered a dangling element if it is a link without features or an unconnected node without features.
      Specified by:
      [`removedDanglingNetworkElements`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `fromNetElem` - the network element from where the search begins

      Returns:
      a collection containing all the removed dangling points

    <!-- -->

    - #### reverseLinkDirection

          public void reverseLinkDirection(NFELink link)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Changes the direction of a link by changing the order of its line ordinates
      Specified by:
      [`reverseLinkDirection`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `link` - a link instance

    <!-- -->

    - #### setNetworkElementGeometry

          public void setNetworkElementGeometry(NFENetworkElement netElem,
                                                JGeometry newGeom)

      Sets a new geometry to the specified network element. All the connected network elements' geometries are updated accordingly.
      Specified by:
      [`setNetworkElementGeometry`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `netElem` -

      `newGeom` -

    <!-- -->

    - #### setNetworkElementsGeometries

          public void setNetworkElementsGeometries(NFENetworkElement[] netElems,
                                                   JGeometry[] newGeoms,
                                                   boolean enforceRules,
                                                   double tolerance)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Changes geometries to a group of network elements. Optionally enforces rules. Tolerance is only required is enforce rules is true.
      Specified by:
      [`setNetworkElementsGeometries`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `netElems` - An array of network elements which geometries will be changed

      `newGeoms` - An array of new geometries. The length of this array must be equal than the netElems array.

      `enforceRules` - if true, rules will be executed for the changed elements

      `tolerance` - tolerance used for detecting interactions if rules are enforced

    <!-- -->

    - #### removeFeature

          public boolean removeFeature(NFEFeature feature)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Removes a feature from the model along with its feature elements and network elements
      Specified by:
      [`removeFeature`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `feature` - a feature instance

      Returns:
      true if the feature was removed successfully

    <!-- -->

    - #### removeFeatureElement

          public boolean removeFeatureElement(NFEFeatureElement featElem)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Removes a feature element from its feature along with the network element where the feature element is placed.
      Specified by:
      [`removeFeatureElement`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `featElem` - a feature element instance

      Returns:
      true if the feature element was removed successfully

    <!-- -->

    - #### applyFeatureClass

          public void applyFeatureClass(NFEFeature feature,
                                        NFEFeatureClass featClass)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Enforces all the attribute constraints defined in the feature class to the given feature
      Specified by:
      [`applyFeatureClass`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `feature` - a feature instance

      `featClass` - a feature class instance

    <!-- -->

    - #### setFeatureActive

          public void setFeatureActive(NFEFeature feature,
                                       boolean active)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Sets the feature's active property
      Specified by:
      [`setFeatureActive`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `feature` - a feature instance

      `active` - the active property value

    <!-- -->

    - #### setFeatureBidirected

          public void setFeatureBidirected(NFEFeature feature,
                                           boolean bidirected)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Sets whether a feature is bidirected or not
      Specified by:
      [`setFeatureBidirected`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `feature` - a feature instance

      `bidirected` - true for bidirected

    <!-- -->

    - #### reverseLineFeatureDirection

          public void reverseLineFeatureDirection(NFEFeature lineFeature)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Reverse the direction of all the links containing feature elements of the given feature
      Specified by:
      [`reverseLineFeatureDirection`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `lineFeature` - a line feature instance

    <!-- -->

    - #### moveFeatureElementToNetworkElement

          public NFEFeatureElement moveFeatureElementToNetworkElement(NFEFeatureElement featElem,
                                                                      NFENetworkElement destNetElem,
                                                                      double destStartPos)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Changes a feature element's underlying network element
      Specified by:
      [`moveFeatureElementToNetworkElement`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `featElem` - the feature element to be modified

      `destNetElem` - the new underlying network element

      `destStartPos` - destination start position (in percent)

      Returns:
      moved feature element

    <!-- -->

    - #### updateLinkGeometry

          public void updateLinkGeometry(NFELink link)

      Updates the link's geometry so reflect the position of its start and end points. If the link's geometry has not been set (it's null), it creates a straight line from the start to the end node.
      Specified by:
      [`updateLinkGeometry`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `link` -

    <!-- -->

    - #### isFeatureElementCompatibleWithFeatureClass

          public static boolean isFeatureElementCompatibleWithFeatureClass(FeatureElement.FeatureElementType feType,
                                                                           NFEFeatureClass featureClass)

    <!-- -->

    - #### isFeatureElementCompatibleWithNetworkElement

          public static boolean isFeatureElementCompatibleWithNetworkElement(FeatureElement.FeatureElementType feType,
                                                                             NFENetworkElement networkElement)

    <!-- -->

    - #### createFeature

          public NFEFeature createFeature(NFEFeatureClass featClass)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates an empty Feature (with no Feature Element) of the specified Feature Class
      Specified by:
      [`createFeature`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `featClass` - A Feature Class instance. It is expected to be a well formed instance, containing a reference to the Feature Layer it belongs to.

      Returns:
      a new empty feature instance

    <!-- -->

    - #### createPointFeature

          public NFEFeature createPointFeature(NFEFeatureClass featClass,
                                               JGeometry pointGeom,
                                               boolean enforceRules,
                                               double tolerance)

      Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node.
      Specified by:

      [`createPointFeature`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:

      `featClass` -

      `pointGeom` -

      `enforceRules` - if true, rules will be executed for this new point feature

      `tolerance` - tolerance used for detecting interactions if rules are enforced

      Returns:

    <!-- -->

    - #### createStandalonePointFeature

          public NFEFeature createStandalonePointFeature(NFEFeatureClass featClass,
                                                         JGeometry pointGeom)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new feature of the given feature class, containing only a PON feature element and its corresponding node. Neither, the feature or the network element are added to a feature layer nor the network
      Specified by:

      [`createStandalonePointFeature`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:

      `featClass` - a point feature class

      `pointGeom` - a java point instance

      Returns:

    <!-- -->

    - #### createLineFeature

          public NFEFeature createLineFeature(NFEFeatureClass featClass,
                                              JGeometry lineGeom,
                                              boolean enforceRules,
                                              double tolerance)

      Creates a new line feature and its corresponding feature element(s) and network elements. If the feature class contains predefined point features they are created too. Feature elements are created accordingly.
      Specified by:

      [`createLineFeature`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:

      `featClass` -

      `lineGeom` -

      `enforceRules` - whether rules must be enforced after creating the feature

      `tolerance` - tolerance used for detecting interactions if rules are enforced

      Returns:

    <!-- -->

    - #### createPredefinedConnectedPointFeatures

          public java.util.List<NFEFeature> createPredefinedConnectedPointFeatures(java.util.Collection<NFEPredefinedConnectedPoint> predefConnPoints,
                                                                                   JGeometry lineGeom)

      Creates the predefined points defined in the line feature class along a line geometry using the predefined points position percentages.
      Specified by:

      [`createPredefinedConnectedPointFeatures`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:

      `predefConnPoints` -

      `lineGeom` -

      Returns:

    <!-- -->

    - #### getAdjacentFeatureElements

          public java.util.Collection<NFEFeatureElement> getAdjacentFeatureElements(NFEFeatureElement featElem,
                                                                                    int depth)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Gets all the feature elements connected to the given feature element
      Specified by:
      [`getAdjacentFeatureElements`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `featElem` - a feature element

      `depth` - for how many levels connected elements must be retrieved

      Returns:
      a collection of connected feature elements

    <!-- -->

    - #### createNode

          public NFENode createNode(double[] pointOrds)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new node. The node is added automatically to the network
      Specified by:
      [`createNode`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `pointOrds` - a point ordinates.

      Returns:
      a new node instance

    <!-- -->

    - #### createNode

          public NFENode createNode(JGeometry geom)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new node. The node is added automatically to the network
      Specified by:
      [`createNode`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `geom` - a point geometry

      Returns:
      a new node instance

    <!-- -->

    - #### createLink

          public NFELink createLink(NFENode startNode,
                                    NFENode endNode)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new link. The links geometry will be a straight line from startNode to endNode. The link is added automatically to the network.
      Specified by:
      [`createLink`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `startNode` - the link's start node. The node must exist in the network.

      `endNode` - the link's end node. The node must exist in the network.

      Returns:
      a new link instance

    <!-- -->

    - #### createLink

          public NFELink createLink(NFENode startNode,
                                    NFENode endNode,
                                    JGeometry geom)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new link. The link is added automatically to the network.
      Specified by:
      [`createLink`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `startNode` - the link's start node. The node must exist in the network.

      `endNode` - the link's end node. The node must exist in the network.

      `geom` - a line string geometry

      Returns:
      a new link instance

    <!-- -->

    - #### createPONFeatureElement

          public NFEFeatureElement createPONFeatureElement(NFENode node,
                                                           long featureLayerId,
                                                           long sequence)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new feature containing one PointOnNode feature element. The feature is added automatically to its feature layer.
      Specified by:
      [`createPONFeatureElement`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `node` - the underlying node

      `featureLayerId` - the ID of feature Layer where the feature belongs

      `sequence` - the feature element's sequence number

      Returns:
      a new feature element instance

    <!-- -->

    - #### createPOLFeatureElement

          public NFEFeatureElement createPOLFeatureElement(NFELink link,
                                                           double pos,
                                                           long featureLayerId,
                                                           long sequence)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new feature containing one PointOnLink feature element. The feature is added automatically to its feature layer.
      Specified by:
      [`createPOLFeatureElement`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Parameters:
      `link` - the underlying link

      `pos` - position of the POL feature element. Relative to the link's length

      `featureLayerId` - the ID of feature Layer where the feature belongs

      `sequence` - the feature element's sequence number

      Returns:
      a new feature element instance

    <!-- -->

    - #### createLineFeatureElement

          public NFEFeatureElement createLineFeatureElement(NFELink link,
                                                            double startPos,
                                                            double endPos,
                                                            long featureLayerId,
                                                            long sequence)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Creates a new feature containing one line feature element. The feature is added automatically to its feature layer.
      Specified by:
      [`createLineFeatureElement`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

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

          public NFERulesEngine getRulesEngine()

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Gets the rules engine instance that is currently used by the model
      Specified by:
      [`getRulesEngine`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

      Returns:
      a rules engine instance

    <!-- -->

    - #### enforceRules

          public void enforceRules(java.util.Collection<NFEFeatureElement> featElems,
                                   double tolerance)

      Description copied from interface: [`NFEManipulator`](NFEManipulator.md)
      Detect interactions and enforces rules if needed for the given feature elements
      Specified by:
      [`enforceRules`](NFEManipulator.md) in interface [`NFEManipulator`](NFEManipulator.md)

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

- Prev Class
- [Next Class](NFEChangesKeeper.md)

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
