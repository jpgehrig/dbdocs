Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFELinePointRuleHandlerParam.md)
- [Next Class](NFERuleHandler.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.rule.handler

## Class NFEMemoryRuleHandlerContext

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.handler.NFEMemoryRuleHandlerContext

<!-- -->

- All Implemented Interfaces:
  [NFERuleHandlerContext](NFERuleHandlerContext.md)

  ------------------------------------------------------------------------



      public class NFEMemoryRuleHandlerContext
      extends java.lang.Object
      implements NFERuleHandlerContext

  In-memory implementation of a rule handler context. Internally it uses the current NFE model instance to perform most of its tasks.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEMemoryRuleHandlerContext``(`[`NFEModel`](../../NFEModel.md)` model, `[`NFEConnectivityRule`](../NFEConnectivityRule.md)` rule)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                                                                                                             | Method and Description                                                                                                                                                                                                                                                                                            |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                                                                                                     | `connectionExists``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem1, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem2)`<br>Tells whether the given feature elements are connected.                                                                                     |
    | [`NFEConnectableEdge`](../../edit/NFEConnectableEdge.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                                       | `createConnectableEdge``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem, java.awt.geom.Point2D connPoint, `[`IntersectionLocation`](../../spatial/interaction/IntersectionLocation.md)` connInterLoc)`<br>Creates a new connectable edge which will be used by a connection descriptor. |
    | [`NFEConnectionDescriptor`](../../edit/NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `createConnectionDescriptor``()`<br>Creates a new connection descriptor instance                                                                                                                                                                                                                                  |
    | [`NFERuleHandlerContext`](NFERuleHandlerContext.md)                                                                                                                                           | `createContext``(`[`NFELinePointRule`](../NFELinePointRule.md)` lpRule)`<br>Creates a new nested context for the line-point rule.                                                                                                                                                                                 |
    | [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)                                                                                                                             | `createLeftHandLinePointHandlerParam``(`[`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)` llhParam)`<br>Creates a new parameter for a line-line rule's left hand side line-point rule                                                                                                              |
    | [`NFELinePointRuleHandlerParam`](NFELinePointRuleHandlerParam.md)                                                                                                                             | `createRighttHandLinePointHandlerParam``(`[`NFELineLineRuleHandlerParam`](NFELineLineRuleHandlerParam.md)` llhParam)`<br>Creates a new parameter for a line-line rule's right hand side line-point rule                                                                                                           |
    | `int[]`                                                                                                                                                                                       | `getAvailableConnections``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem)`<br>Gets the number of available connections for the given point feature element.                                                                                                                           |
    | [`NFERuleHandler`](NFERuleHandler.md)                                                                                                                                                         | `getHandler``(`[`NFEConnectivityRule`](../NFEConnectivityRule.md)` rule)`<br>Gets the handler assigned to the given connectivity rule                                                                                                                                                                             |
    | `int`                                                                                                                                                                                         | `getSRID``()`<br>Gets the current NFE model's SRID                                                                                                                                                                                                                                                                |
    | `int[]`                                                                                                                                                                                       | `getUsedConnections``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem, long lineFeatLayerId, long lineFeatClassId)`<br>Gets the number of in an out connections the given point contains with lines of the specified feature layer and feature class.                                   |
    | `boolean`                                                                                                                                                                                     | `inConnectionExists``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Tells whether the line feature element is an incoming connection of the point feature element                                      |
    | `boolean`                                                                                                                                                                                     | `isStandaloneFeatureElement``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem)`<br>Thells whether the feature element is standalone.                                                                                                                                                         |
    | `boolean`                                                                                                                                                                                     | `outConnectionExists``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Tells whether the line feature element is an outgoing connection of the point feature element                                     |
    | [`NFEFeatureElement`](../../feature/NFEFeatureElement.md)                                                                                                                                     | `requestDefaultPointFeatureElement``(`[`JGeometry`](../../../../../geometry/JGeometry.md)` pointGeom)`<br>Creates a new standalone point feature element with the given point geometry.                                                                                                                           |
    | `boolean`                                                                                                                                                                                     | `reserveInConnection``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Creates a virtual in connection between the point and line feature element.                                                       |
    | `boolean`                                                                                                                                                                                     | `reserveOutConnection``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Creates a virtual out connection between the point and line feature element.                                                     |
    | `void`                                                                                                                                                                                        | `reset``()`<br>Resets the state of the context                                                                                                                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEMemoryRuleHandlerContext

          public NFEMemoryRuleHandlerContext(NFEModel model,
                                             NFEConnectivityRule rule)

  <!-- -->

  - ### Method Detail

    - #### getAvailableConnections

          public int[] getAvailableConnections(NFEFeatureElement pointFeatElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Gets the number of available connections for the given point feature element. The number of available connections are calculated based on the cardinality defined for the point's feature class. Virtual connections made by the handler are considered as actual connections.
      Specified by:
      [`getAvailableConnections`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointFeatElem` - a point feature element

      Returns:
      a two-element array with the number of available in and out connections at the position 0 and 1 respectively

    <!-- -->

    - #### getUsedConnections

          public int[] getUsedConnections(NFEFeatureElement pointFeatElem,
                                          long lineFeatLayerId,
                                          long lineFeatClassId)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Gets the number of in an out connections the given point contains with lines of the specified feature layer and feature class. Virtual connections performed by the handler are considered.
      Specified by:
      [`getUsedConnections`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Returns:
      a two-element array with the number of used in and out connections at the position 0 and 1 respectively

    <!-- -->

    - #### connectionExists

          public boolean connectionExists(NFEFeatureElement featElem1,
                                          NFEFeatureElement featElem2)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Tells whether the given feature elements are connected. A Line and point are considered connected when their underlying link and node are connected. Points are considered connected if they are connected to the same underlying link. Lines are considered connected if they are connected to the same underlying node.
      Specified by:
      [`connectionExists`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `featElem1` - a feature element

      `featElem2` - a feature element

      Returns:
      true if the elements are connected

    <!-- -->

    - #### inConnectionExists

          public boolean inConnectionExists(NFEFeatureElement pointFeatElem,
                                            NFEFeatureElement lineFeatElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Tells whether the line feature element is an incoming connection of the point feature element
      Specified by:
      [`inConnectionExists`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line is an in-connection

    <!-- -->

    - #### outConnectionExists

          public boolean outConnectionExists(NFEFeatureElement pointFeatElem,
                                             NFEFeatureElement lineFeatElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Tells whether the line feature element is an outgoing connection of the point feature element
      Specified by:
      [`outConnectionExists`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line is an out-connection

    <!-- -->

    - #### getHandler

          public NFERuleHandler getHandler(NFEConnectivityRule rule)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Gets the handler assigned to the given connectivity rule
      Specified by:
      [`getHandler`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `rule` - a connectivity rule object

      Returns:
      a rule handler instance

    <!-- -->

    - #### reserveInConnection

          public boolean reserveInConnection(NFEFeatureElement pointFeatElem,
                                             NFEFeatureElement lineFeatElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a virtual in connection between the point and line feature element. A virtual connection only exists in the handler context. No rule handler can see virtual connections made by another handler, unless, the contexts are nested due to nested handler calls.
      Specified by:
      [`reserveInConnection`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the virtual connection could be performed.

    <!-- -->

    - #### reserveOutConnection

          public boolean reserveOutConnection(NFEFeatureElement pointFeatElem,
                                              NFEFeatureElement lineFeatElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a virtual out connection between the point and line feature element. A virtual connection only exists in the handler context. No rule handler can see virtual connections made by another handler, unless, the contexts are nested due to nested handler calls.
      Specified by:
      [`reserveOutConnection`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the virtual connection could be performed.

    <!-- -->

    - #### requestDefaultPointFeatureElement

          public NFEFeatureElement requestDefaultPointFeatureElement(JGeometry pointGeom)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new standalone point feature element with the given point geometry. The new only can be created if the handler's rule is allowed to create a default point. The characteristics of the new point such as feature layer and feature class are also given by the handler's rule. The created point is considered standalone, that is, it is not included in any of the model's feature layers.
      Specified by:
      [`requestDefaultPointFeatureElement`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `pointGeom` - a point geometry

      Returns:
      a new standalone point feature element or null if the rule does not specify the creation of a default point

    <!-- -->

    - #### isStandaloneFeatureElement

          public boolean isStandaloneFeatureElement(NFEFeatureElement featElem)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Thells whether the feature element is standalone. A feature element is standalone if it is not included in any of the model's feature layers
      Specified by:
      [`isStandaloneFeatureElement`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `featElem` - a feature element

      Returns:
      true if the feature element is standalone

    <!-- -->

    - #### reset

          public void reset()

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Resets the state of the context
      Specified by:
      [`reset`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

    <!-- -->

    - #### getSRID

          public int getSRID()

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Gets the current NFE model's SRID
      Specified by:
      [`getSRID`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Returns:
      an srid

    <!-- -->

    - #### createContext

          public NFERuleHandlerContext createContext(NFELinePointRule lpRule)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new nested context for the line-point rule. The new context will be able to see information from the current context.
      Specified by:
      [`createContext`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `lpRule` - a line-point rule object

      Returns:
      a new handler context

    <!-- -->

    - #### createConnectionDescriptor

          public NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement> createConnectionDescriptor()

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new connection descriptor instance
      Specified by:
      [`createConnectionDescriptor`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Returns:
      a feature element connection descriptor instance

    <!-- -->

    - #### createConnectableEdge

          public NFEConnectableEdge<NFEFeatureElement> createConnectableEdge(NFEFeatureElement lineFeatElem,
                                                                             java.awt.geom.Point2D connPoint,
                                                                             IntersectionLocation connInterLoc)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new connectable edge which will be used by a connection descriptor.
      Specified by:
      [`createConnectableEdge`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `lineFeatElem` - a line feature element

      `connPoint` - the point on the line where the line will be connected

      `connInterLoc` - the location of the line where the connection will be performed

      Returns:
      a new connectable edge

    <!-- -->

    - #### createLeftHandLinePointHandlerParam

          public NFELinePointRuleHandlerParam createLeftHandLinePointHandlerParam(NFELineLineRuleHandlerParam llhParam)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new parameter for a line-line rule's left hand side line-point rule
      Specified by:
      [`createLeftHandLinePointHandlerParam`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `llhParam` - a line-line rule handler parameter object

      Returns:
      a new line-point rule handler parameter

    <!-- -->

    - #### createRighttHandLinePointHandlerParam

          public NFELinePointRuleHandlerParam createRighttHandLinePointHandlerParam(NFELineLineRuleHandlerParam llhParam)

      Description copied from interface: [`NFERuleHandlerContext`](NFERuleHandlerContext.md)
      Creates a new parameter for a line-line rule's right hand side line-point rule
      Specified by:
      [`createRighttHandLinePointHandlerParam`](NFERuleHandlerContext.md) in interface [`NFERuleHandlerContext`](NFERuleHandlerContext.md)

      Parameters:
      `llhParam` - a line-line rule handler parameter object

      Returns:
      a new line-point rule handler parameter

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFELinePointRuleHandlerParam.md)
- [Next Class](NFERuleHandler.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
