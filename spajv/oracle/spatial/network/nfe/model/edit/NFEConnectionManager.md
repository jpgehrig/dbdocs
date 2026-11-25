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

- [Prev Class](NFEConnectionDescriptor.md)
- [Next Class](NFEEditionManager.md)

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

## Class NFEConnectionManager

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEConnectionManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEConnectionManager
      extends java.lang.Object

  Component in charge of connecting/disconnecting network/feature elements.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEConnectionManager``(`[`NFEModel`](../NFEModel.md)` model)`<br>Allocates a new connection manager instance for the given model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                          | Method and Description                                                                                                                                                                                                                                                                   |
    |--------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.Map<java.lang.String,`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>` | `connect``(`[`NFEConnectionDescriptor`](NFEConnectionDescriptor.md)`<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`,`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> connDesc)`<br>Perform the connections described by the given connection descriptor instance.     |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                                     | `connect``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEConnectableEdge`](NFEConnectableEdge.md)`<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> connEdge, double tolerance)`<br>Connects a point feature element to a line feature element. |
    | `boolean`                                                                                  | `connectionExists``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem1, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem2)`<br>Tells whether two feature elements are directly connected.                                                               |
    | `boolean`                                                                                  | `disconnect``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` targetFeatElem, java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`> connFeatElems, boolean merge)`<br>Disconnects one or more feature elements from the target feature element.        |
    | `boolean`                                                                                  | `disconnect``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem1, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem2, boolean merge)`<br>Disconnects two connected feature elements.                                                                     |
    | `java.util.Collection<`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)`>`           | `getConnectedElements``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Gets all the feature elements adjacent to the given feature element.                                                                                                                      |
    | `int`                                                                                      | `getInConnectionCount``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem, long lineFeatLayerId, long lineFeatClassId)`<br>Gets the count of the incoming connected lines with the specified feature layer and feature class.                                       |
    | `int`                                                                                      | `getInConnectionsCount``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem)`<br>Gets the incoming connected lines count                                                                                                                                             |
    | `int`                                                                                      | `getOutConnectionCount``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem, long lineFeatLayerId, long lineFeatClassId)`<br>Gets the count of the outgoing connected lines with the specified feature layer and feature class.                                      |
    | `int`                                                                                      | `getOutConnectionsCount``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem)`<br>Gets the outgoing connected lines count                                                                                                                                            |
    | `boolean`                                                                                  | `inConnectionExists``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Tells whether the line feature element is an incoming line connected to the point feature element               |
    | `boolean`                                                                                  | `isDanglingNode``(`[`NFENode`](../network/NFENode.md)` node)`<br>Tells whether a node is a dangling node, that is, there are no feature elements over the node nor is connected to any link                                                                                              |
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md)                                     | `merge``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` lineFeatElem1, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` lineFeatElem2)`<br>Merges two line feature elements into one single line feature element.                                                      |
    | `boolean`                                                                                  | `outConnectionExists``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` pointFeatElem, `[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` lineFeatElem)`<br>Tells whether the line feature element is an outgoing line connected to the point feature element              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEConnectionManager

          public NFEConnectionManager(NFEModel model)

      Allocates a new connection manager instance for the given model.
      Parameters:
      `model` - an nfe model instance

  <!-- -->

  - ### Method Detail

    - #### connect

          public java.util.Map<java.lang.String,NFEFeatureElement> connect(NFEConnectionDescriptor<NFEFeatureElement,NFEFeatureElement> connDesc)

      Perform the connections described by the given connection descriptor instance.
      Parameters:
      `connDesc` - the connection descriptor

      Returns:
      a relation between the connectable edges' keys and the newly created line features if any

    <!-- -->

    - #### connect

          public NFEFeatureElement connect(NFEFeatureElement pointFeatElem,
                                           NFEConnectableEdge<NFEFeatureElement> connEdge,
                                           double tolerance)

      Connects a point feature element to a line feature element. The line and the connection specific information is given by the connectable edge instance.
      Parameters:

      `pointFeatElem` - a point feature element to be connected

      `connEdge` - a connectable edge instance containing the line feature element and how the line must be connected

      `tolerance` - tolerance used to determine the line connection location

      Returns:

    <!-- -->

    - #### isDanglingNode

          public boolean isDanglingNode(NFENode node)

      Tells whether a node is a dangling node, that is, there are no feature elements over the node nor is connected to any link
      Parameters:
      `node` - a node instance

      Returns:
      true if it is a dangling node

    <!-- -->

    - #### connectionExists

          public boolean connectionExists(NFEFeatureElement featElem1,
                                          NFEFeatureElement featElem2)

      Tells whether two feature elements are directly connected. Two feature elements are directly connected if both underlying network elements are adjacent.
      Parameters:
      `featElem1` - a line or point feature element

      `featElem2` - a line or point feature element

      Returns:
      true if both feature elements are directly connected

    <!-- -->

    - #### inConnectionExists

          public boolean inConnectionExists(NFEFeatureElement pointFeatElem,
                                            NFEFeatureElement lineFeatElem)

      Tells whether the line feature element is an incoming line connected to the point feature element
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line's underlying link is a incoming link of the point underlying node

    <!-- -->

    - #### outConnectionExists

          public boolean outConnectionExists(NFEFeatureElement pointFeatElem,
                                             NFEFeatureElement lineFeatElem)

      Tells whether the line feature element is an outgoing line connected to the point feature element
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatElem` - a line feature element

      Returns:
      true if the line's underlying link is a outgoing link of the point underlying node

    <!-- -->

    - #### getConnectedElements

          public java.util.Collection<NFEFeatureElement> getConnectedElements(NFEFeatureElement featElem)

      Gets all the feature elements adjacent to the given feature element. If it is a point, all the lines connected to the point are returned. For a line, the line end points are returned.
      Parameters:
      `featElem` - a line or point feature element

      Returns:
      a collection containing all the connected feature elements

    <!-- -->

    - #### getInConnectionsCount

          public int getInConnectionsCount(NFEFeatureElement pointFeatElem)

      Gets the incoming connected lines count
      Parameters:
      `pointFeatElem` - a point feature element

      Returns:
      the incoming connected lines count

    <!-- -->

    - #### getOutConnectionsCount

          public int getOutConnectionsCount(NFEFeatureElement pointFeatElem)

      Gets the outgoing connected lines count
      Parameters:
      `pointFeatElem` - a point feature element

      Returns:
      the outgoing connected lines count

    <!-- -->

    - #### getInConnectionCount

          public int getInConnectionCount(NFEFeatureElement pointFeatElem,
                                          long lineFeatLayerId,
                                          long lineFeatClassId)

      Gets the count of the incoming connected lines with the specified feature layer and feature class.
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatLayerId` - the feature layer ID of the incoming lines.

      `lineFeatClassId` - the feature class ID of the incoming lines.

      Returns:
      the filtered incoming connected lines count

    <!-- -->

    - #### getOutConnectionCount

          public int getOutConnectionCount(NFEFeatureElement pointFeatElem,
                                           long lineFeatLayerId,
                                           long lineFeatClassId)

      Gets the count of the outgoing connected lines with the specified feature layer and feature class.
      Parameters:
      `pointFeatElem` - a point feature element

      `lineFeatLayerId` - the feature layer ID of the incoming lines.

      `lineFeatClassId` - the feature class ID of the incoming lines.

      Returns:
      the filtered outgoing connected lines count

    <!-- -->

    - #### disconnect

          public boolean disconnect(NFEFeatureElement targetFeatElem,
                                    java.util.Collection<NFEFeatureElement> connFeatElems,
                                    boolean merge)

      Disconnects one or more feature elements from the target feature element. Optionally, the disconnected line feature elements are merged into one feature element if both feature element were one single line before the current connection was done.
      Parameters:
      `targetFeatElem` - a feature element connected to the feature elements of the collection parameter

      `connFeatElems` - a collection of feature elements to be disconnected from the target feature element

      `merge` - whether split line feature elements must be merged once disconnected.

      Returns:
      true if all the element were successfully disconnected

    <!-- -->

    - #### disconnect

          public boolean disconnect(NFEFeatureElement featElem1,
                                    NFEFeatureElement featElem2,
                                    boolean merge)

      Disconnects two connected feature elements. Optionally, merges a split line feature element.
      Parameters:
      `featElem1` - a line or point feature element

      `featElem2` - a line or point feature element

      `whether` - split line feature elements must be merged once disconnected.

      Returns:
      true if the elements were successfully disconnected

    <!-- -->

    - #### merge

          public NFEFeatureElement merge(NFEFeatureElement lineFeatElem1,
                                         NFEFeatureElement lineFeatElem2)

      Merges two line feature elements into one single line feature element. If the merge is performed, the first line parameter remains in the model, the other line feature element is erased
      Parameters:
      `lineFeatElem1` - a line feature element

      `lineFeatElem2` - a line feature element. If merge is performed, this line is disposed

      Returns:
      the merged line feature element or null if the lines could not be merged.

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

- [Prev Class](NFEConnectionDescriptor.md)
- [Next Class](NFEEditionManager.md)

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
