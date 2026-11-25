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

- [Prev Class](NFERuleHandler.md)
- Next Class

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

## Interface NFERuleHandlerContext

- All Known Implementing Classes:
  [NFEMemoryRuleHandlerContext](NFEMemoryRuleHandlerContext.md)

  ------------------------------------------------------------------------



      public interface NFERuleHandlerContext

  A rule handler context is a service used by a rule handler implementation. This service provides information about the model's state. Additionally, the context keeps track of the rule handler's own state. The handler's state includes which connections have been determined by the handler.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                                                                                             | Method and Description                                                                                                                                                                                                                                                                                            |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                                                                                                     | `connectionExists``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem1, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featElem2)`<br>Tells whether the given feature elements are connected.                                                                                     |
    | [`NFEConnectableEdge`](../../edit/NFEConnectableEdge.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>`                                                                       | `createConnectableEdge``(`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` lineFeatElem, java.awt.geom.Point2D connPoint, `[`IntersectionLocation`](../../spatial/interaction/IntersectionLocation.md)` connInterLoc)`<br>Creates a new connectable edge which will be used by a connection descriptor. |
    | [`NFEConnectionDescriptor`](../../edit/NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`>` | `createConnectionDescriptor``()`<br>Creates a new connection descriptor instance                                                                                                                                                                                                                                  |
    | `NFERuleHandlerContext`                                                                                                                                                                       | `createContext``(`[`NFELinePointRule`](../NFELinePointRule.md)` lpRule)`<br>Creates a new nested context for the line-point rule.                                                                                                                                                                                 |
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

<!-- -->

- - ### Method Detail

    - #### getAvailableConnections

          int[] getAvailableConnections(NFEFeatureElement pointFeatElem)

      Gets the number of available connections for the given point feature element. The number of available connections are calculated based on the cardinality defined for the point's feature class. Virtual connections made by the handler are considered as actual connections.
      Parameters:
      `pointFeatElem` - a point feature element

      Returns:
      a two-element array with the number of available in and out connections at the position 0 and 1 respectively

    <!-- -->

    - #### getUsedConnections

          int[] getUsedConnections(NFEFeatureElement pointFeatElem,
                                   long lineFeatLayerId,
                                   long lineFeatClassId)

      Gets the number of in an out connections the given point contains with lines of the specified feature layer and feature class. Virtual connections performed by the handler are considered.
      Parameters:
      `pointFeatElem` -

      `lineFeatLayerId` -

      `lineFeatClassId` -

      Returns:
      a two-element array with the number of used in and out connections at the position 0 and 1 respectively

    <!-- -->

    - #### connectionExists

          boolean connectionExists(NFEFeatureElement featElem1,
                                   NFEFeatureElement featElem2)

      Tells whether the given feature elements are connected. A Line and point are considered connected when their underlying link and node are connected. Points are considered connected if they are connected to the same underlying link. Lines are considered connected if they are connected to the same underlying node.
      Parameters:
      `featElem1` - a feature element

      `featElem2` - a feature element

      Returns:
      true if the elements are connected

    <!-- -->

    - #### inConnectionExists

          boolean inConnectionExists(NFEFeatureElement pointFeatElem,
                                     NFEFeatureElement lineFeatElem)

      Tells whether the line feature element is an incoming connection of the point feature element
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line is an in-connection

    <!-- -->

    - #### outConnectionExists

          boolean outConnectionExists(NFEFeatureElement pointFeatElem,
                                      NFEFeatureElement lineFeatElem)

      Tells whether the line feature element is an outgoing connection of the point feature element
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line is an out-connection

    <!-- -->

    - #### getHandler

          NFERuleHandler getHandler(NFEConnectivityRule rule)

      Gets the handler assigned to the given connectivity rule
      Parameters:
      `rule` - a connectivity rule object

      Returns:
      a rule handler instance

    <!-- -->

    - #### reserveInConnection

          boolean reserveInConnection(NFEFeatureElement pointFeatElem,
                                      NFEFeatureElement lineFeatElem)

      Creates a virtual in connection between the point and line feature element. A virtual connection only exists in the handler context. No rule handler can see virtual connections made by another handler, unless, the contexts are nested due to nested handler calls.
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the virtual connection could be performed.

    <!-- -->

    - #### reserveOutConnection

          boolean reserveOutConnection(NFEFeatureElement pointFeatElem,
                                       NFEFeatureElement lineFeatElem)

      Creates a virtual out connection between the point and line feature element. A virtual connection only exists in the handler context. No rule handler can see virtual connections made by another handler, unless, the contexts are nested due to nested handler calls.
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the virtual connection could be performed.

    <!-- -->

    - #### requestDefaultPointFeatureElement

          NFEFeatureElement requestDefaultPointFeatureElement(JGeometry pointGeom)

      Creates a new standalone point feature element with the given point geometry. The new only can be created if the handler's rule is allowed to create a default point. The characteristics of the new point such as feature layer and feature class are also given by the handler's rule. The created point is considered standalone, that is, it is not included in any of the model's feature layers.
      Parameters:
      `pointGeom` - a point geometry

      Returns:
      a new standalone point feature element or null if the rule does not specify the creation of a default point

    <!-- -->

    - #### isStandaloneFeatureElement

          boolean isStandaloneFeatureElement(NFEFeatureElement featElem)

      Thells whether the feature element is standalone. A feature element is standalone if it is not included in any of the model's feature layers
      Parameters:
      `featElem` - a feature element

      Returns:
      true if the feature element is standalone

    <!-- -->

    - #### createContext

          NFERuleHandlerContext createContext(NFELinePointRule lpRule)

      Creates a new nested context for the line-point rule. The new context will be able to see information from the current context.
      Parameters:
      `lpRule` - a line-point rule object

      Returns:
      a new handler context

    <!-- -->

    - #### createConnectionDescriptor

          NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement> createConnectionDescriptor()

      Creates a new connection descriptor instance
      Returns:
      a feature element connection descriptor instance

    <!-- -->

    - #### createConnectableEdge

          NFEConnectableEdge<NFEFeatureElement> createConnectableEdge(NFEFeatureElement lineFeatElem,
                                                                      java.awt.geom.Point2D connPoint,
                                                                      IntersectionLocation connInterLoc)

      Creates a new connectable edge which will be used by a connection descriptor.
      Parameters:
      `lineFeatElem` - a line feature element

      `connPoint` - the point on the line where the line will be connected

      `connInterLoc` - the location of the line where the connection will be performed

      Returns:
      a new connectable edge

    <!-- -->

    - #### createLeftHandLinePointHandlerParam

          NFELinePointRuleHandlerParam createLeftHandLinePointHandlerParam(NFELineLineRuleHandlerParam llhParam)

      Creates a new parameter for a line-line rule's left hand side line-point rule
      Parameters:
      `llhParam` - a line-line rule handler parameter object

      Returns:
      a new line-point rule handler parameter

    <!-- -->

    - #### createRighttHandLinePointHandlerParam

          NFELinePointRuleHandlerParam createRighttHandLinePointHandlerParam(NFELineLineRuleHandlerParam llhParam)

      Creates a new parameter for a line-line rule's right hand side line-point rule
      Parameters:
      `llhParam` - a line-line rule handler parameter object

      Returns:
      a new line-point rule handler parameter

    <!-- -->

    - #### getSRID

          int getSRID()

      Gets the current NFE model's SRID
      Returns:
      an srid

    <!-- -->

    - #### reset

          void reset()

      Resets the state of the context

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

- [Prev Class](NFERuleHandler.md)
- Next Class

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
