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

- [Prev Class](NFENetwork.md)
- [Next Class](NFENetworkMetadata.md)

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

oracle.spatial.network.nfe.model.network

## Class NFENetworkElement

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - oracle.spatial.network.nfe.model.network.NFENetworkElement

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFELink](NFELink.md), [NFENode](NFENode.md)

  ------------------------------------------------------------------------



      public abstract class NFENetworkElement
      extends NFEBasicModelObject

  This is the base class for nodes and links. It contains methods and properties common to both types of network elements.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                |
    |---------------------------|--------------------------------------|
    | `static java.lang.String` | `PROP_ACTIVE`<br>Active property     |
    | `static java.lang.String` | `PROP_COST`<br>Cost property         |
    | `static java.lang.String` | `PROP_GEOMETRY`<br>Geometry property |
    | `static java.lang.String` | `PROP_ID`<br>ID property             |
    | `static java.lang.String` | `PROP_NAME`<br>Name property         |

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFENetworkElement``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                              |
    |--------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
    | `abstract NFENetworkElement`                     | `createCopy``()`<br>Returns object copy.                                                                            |
    | `double`                                         | `getCost``()`<br>Gets the cost of the network element                                                               |
    | [`JGeometry`](../../../../geometry/JGeometry.md) | `getGeometry``()`<br>gets the network element's geometry                                                            |
    | `long`                                           | `getId``()`<br>Gets the ID of the network element                                                                   |
    | `abstract java.lang.String`                      | `getKey``()`<br>Gets the network element's key.                                                                     |
    | `java.lang.String`                               | `getName``()`<br>Gets the network element's name                                                                    |
    | [`NFENetwork`](NFENetwork.md)                    | `getNetwork``()`<br>Gets the network to which the network element belongs                                           |
    | `boolean`                                        | `isActive``()`<br>Tells whether the network element is active or not                                                |
    | `abstract boolean`                               | `isLink``()`<br>Tells whether the network element is a link or not                                                  |
    | `abstract boolean`                               | `isNode``()`<br>Tells whether the network element is a node or not                                                  |
    | `void`                                           | `setActive``(boolean active)`<br>Sets the network element as active or inactive                                     |
    | `void`                                           | `setCost``(double cost)`<br>Sets the cost of the network element                                                    |
    | `void`                                           | `setGeometry``(`[`JGeometry`](../../../../geometry/JGeometry.md)` geometry)`<br>Sets the network element's geometry |
    | `void`                                           | `setId``(long id)`<br>Sets the ID of the network element                                                            |
    | `void`                                           | `setName``(java.lang.String name)`<br>Sets the name of the network element                                          |
    | `void`                                           | `setNetwork``(`[`NFENetwork`](NFENetwork.md)` network)`<br>Sets the network to which the network element belongs    |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROP_NAME

          public static final java.lang.String PROP_NAME

      Name property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_ID

          public static final java.lang.String PROP_ID

      ID property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_ACTIVE

          public static final java.lang.String PROP_ACTIVE

      Active property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_GEOMETRY

          public static final java.lang.String PROP_GEOMETRY

      Geometry property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_COST

          public static final java.lang.String PROP_COST

      Cost property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFENetworkElement

          public NFENetworkElement()

  <!-- -->

  - ### Method Detail

    - #### setId

          public void setId(long id)

      Sets the ID of the network element
      Parameters:
      `id` - a node or link ID

    <!-- -->

    - #### getId

          public long getId()

      Gets the ID of the network element
      Returns:
      a node or link ID

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Sets the name of the network element
      Parameters:
      `name` - the network element's name

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the network element's name
      Returns:
      the network element's name

    <!-- -->

    - #### setActive

          public void setActive(boolean active)

      Sets the network element as active or inactive
      Parameters:
      `active` - a boolean value indicating whether the network element is active or not

    <!-- -->

    - #### isActive

          public boolean isActive()

      Tells whether the network element is active or not
      Returns:
      a boolean value indicating whether the network element is active or not

    <!-- -->

    - #### setCost

          public void setCost(double cost)

      Sets the cost of the network element
      Parameters:
      `cost` - the network element's cost

    <!-- -->

    - #### getCost

          public double getCost()

      Gets the cost of the network element
      Returns:
      the network element's cost

    <!-- -->

    - #### setGeometry

          public void setGeometry(JGeometry geometry)

      Sets the network element's geometry
      Parameters:
      `geometry` - a line string geometry for links, a point geometry for nodes

    <!-- -->

    - #### getGeometry

          public JGeometry getGeometry()

      gets the network element's geometry
      Returns:
      a line string geometry for links, a point geometry for nodes

    <!-- -->

    - #### setNetwork

          public void setNetwork(NFENetwork network)

      Sets the network to which the network element belongs
      Parameters:
      `network` - a network instance

    <!-- -->

    - #### getNetwork

          public NFENetwork getNetwork()

      Gets the network to which the network element belongs
      Returns:
      a network instance or null the network element does not belong to any network

    <!-- -->

    - #### isNode

          public abstract boolean isNode()

      Tells whether the network element is a node or not
      Returns:
      true if the network element is a node

    <!-- -->

    - #### isLink

          public abstract boolean isLink()

      Tells whether the network element is a link or not
      Returns:
      true if the network element is a link

    <!-- -->

    - #### getKey

          public abstract java.lang.String getKey()

      Gets the network element's key. The key is a unique value to differentiate a network element among other network elements in the same network. There could be a node and a link with the same ID but cannot exist two network elements (node or links) with the same key
      Returns:
      the network element's key

    <!-- -->

    - #### createCopy

          public abstract NFENetworkElement createCopy()

      Returns object copy.
      Returns:
      object copy

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

- [Prev Class](NFENetwork.md)
- [Next Class](NFENetworkMetadata.md)

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
