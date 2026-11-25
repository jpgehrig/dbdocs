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

- [Prev Class](NFEFeatureElement.md)
- [Next Class](NFEFeatureLayerMetadata.md)

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

oracle.spatial.network.nfe.model.feature

## Class NFEFeatureLayer

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEFeatureLayer

<!-- -->

- Direct Known Subclasses:
  [NFEBasicFeatureLayer](NFEBasicFeatureLayer.md)

  ------------------------------------------------------------------------



      public abstract class NFEFeatureLayer
      extends java.lang.Object

  This class represents a feature layer in memory. A feature layer is a first level model object which is directly contained in an NFEModel instance and is related with one network instance. A feature layer contains zero to many features and one to many feature class definitions. Any user intersected on receiving notifications about changes in the feature layer or objects contained in the feature layer must be added as a model listener.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description              |
    |---------------------------|------------------------------------|
    | `static java.lang.String` | `PROP_Z_ORDER`<br>Z order property |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEFeatureLayer``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                         | Method and Description                                                                                                                                                               |
    |---------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract void`                                                                                                           | `addAttributeDescriptor``(`[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)` attrDescriptor)`<br>Sets an attribute descriptor for the given attribute's name                    |
    | `abstract boolean`                                                                                                        | `addFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Adds a feature to the feature layer.                                                                                      |
    | `abstract boolean`                                                                                                        | `addFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` featureClass)`<br>Adds a Feature Class instance to the Feature Layer.                                                   |
    | `abstract void`                                                                                                           | `addModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`                                                                                                  |
    | `abstract boolean`                                                                                                        | `containsFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Tells whether the feature layer contains the given feature                                                           |
    | `abstract NFEFeatureLayer`                                                                                                | `createCopy``()`<br>Returns object copy.                                                                                                                                             |
    | `abstract `[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)                                                          | `getAttributeDescriptor``(java.lang.String attrName)`<br>Gets the attribute descriptor for the given attribute's name                                                                |
    | `abstract java.util.Collection<`[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)`>`                                  | `getAttributeDescriptors``()`<br>Gets all the attribute descriptors of the feature layer                                                                                             |
    | `abstract `[`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`>` | `getEventDispatcher``()`<br>Returns the event dispatcher.                                                                                                                            |
    | `abstract `[`NFEFeature`](NFEFeature.md)                                                                                  | `getFeature``(long featureId)`<br>Gets a feature identified by the given ID contained in the feature layer                                                                           |
    | `abstract `[`NFEFeatureClass`](NFEFeatureClass.md)                                                                        | `getFeatureClass``(long featureClassId)`<br>Gets a feature class which belongs on this feature layer.                                                                                |
    | `abstract java.util.Collection<`[`NFEFeatureClass`](NFEFeatureClass.md)`>`                                                | `getFeatureClasses``()`<br>Gets the feature classes defined for this feature layer                                                                                                   |
    | `abstract java.util.Collection<`[`NFEFeatureClass`](NFEFeatureClass.md)`>`                                                | `getFeatureClasses``(`[`NFEFeatureShape`](NFEFeatureShape.md)` shape)`<br>Gets all the feature classes matching the given shape from the feature layer                               |
    | `abstract java.util.Collection<`[`NFEFeature`](NFEFeature.md)`>`                                                          | `getFeatures``()`<br>Gets all the features in the feature layer.                                                                                                                     |
    | `abstract java.util.Collection<`[`NFEFeature`](NFEFeature.md)`>`                                                          | `getFeatures``(long featureClassId)`<br>Gets all the features with the given Feature Class in the Feature Layer.                                                                     |
    | `abstract int`                                                                                                            | `getHierarchyLevel``()`<br>Gets the hierarchy level of the feature layer                                                                                                             |
    | `abstract long`                                                                                                           | `getId``()`<br>Gets the id of the feature layer                                                                                                                                      |
    | `abstract `[`NFEFeatureLayerMetadata`](NFEFeatureLayerMetadata.md)                                                        | `getMetadata``()`<br>Gets the feature layer's metadata                                                                                                                               |
    | `abstract java.lang.String`                                                                                               | `getName``()`<br>Gets the name of the feature layer                                                                                                                                  |
    | `abstract `[`NFENetwork`](../network/NFENetwork.md)                                                                       | `getNetwork``()`<br>Gets the feature layer's network                                                                                                                                 |
    | `abstract `[`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md)               | `getType``()`<br>Gets the feature layer type                                                                                                                                         |
    | `abstract int`                                                                                                            | `getZOrder``()`<br>Gets the Z order of the feature layer                                                                                                                             |
    | `abstract `[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)                                                          | `removeAttributeDescriptor``(java.lang.String attrName)`<br>Removes the attribute descriptor with the given attribute's name                                                         |
    | `abstract `[`NFEFeature`](NFEFeature.md)                                                                                  | `removeFeature``(long featureId)`<br>Removes a feature identified by the given ID from the feature layer                                                                             |
    | `abstract `[`NFEFeatureClass`](NFEFeatureClass.md)                                                                        | `removeFeatureClass``(long featureClassId)`<br>Removes a feature class identified by the given ID from the feature layer                                                             |
    | `abstract void`                                                                                                           | `removeModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`                                                                                               |
    | `abstract void`                                                                                                           | `setEventDispatcher``(`[`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`> eventDispatcher)`<br>Sets the event dispatcher. |
    | `abstract void`                                                                                                           | `setHierarchyLevel``(int hierarchyLevel)`<br>Sets the Hierarchy Level of the feature layer                                                                                           |
    | `abstract void`                                                                                                           | `setId``(long id)`<br>Sets the ID of the feature layer                                                                                                                               |
    | `abstract void`                                                                                                           | `setMetadata``(`[`NFEFeatureLayerMetadata`](NFEFeatureLayerMetadata.md)` metadata)`<br>Sets the feature layer's metadata                                                             |
    | `abstract void`                                                                                                           | `setName``(java.lang.String name)`<br>Sets the name of the feature layer                                                                                                             |
    | `abstract void`                                                                                                           | `setNetwork``(`[`NFENetwork`](../network/NFENetwork.md)` network)`<br>Sets the feature layer's network                                                                               |
    | `abstract void`                                                                                                           | `setType``(`[`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md)` type)`<br>Sets the feature layer type                                  |
    | `abstract void`                                                                                                           | `setZOrder``(int zOrder)`<br>Sets the Z order for the feature layer.                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROP_Z_ORDER

          public static final java.lang.String PROP_Z_ORDER

      Z order property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFEFeatureLayer

          public NFEFeatureLayer()

  <!-- -->

  - ### Method Detail

    - #### setId

          public abstract void setId(long id)

      Sets the ID of the feature layer
      Parameters:
      `id` - the feature layer's ID

    <!-- -->

    - #### getId

          public abstract long getId()

      Gets the id of the feature layer
      Returns:
      the feature layer's ID

    <!-- -->

    - #### setName

          public abstract void setName(java.lang.String name)

      Sets the name of the feature layer
      Parameters:
      `name` - the feature layer's name

    <!-- -->

    - #### getName

          public abstract java.lang.String getName()

      Gets the name of the feature layer
      Returns:
      the feature layer's name

    <!-- -->

    - #### setNetwork

          public abstract void setNetwork(NFENetwork network)

      Sets the feature layer's network
      Parameters:
      `network` - a network instance

    <!-- -->

    - #### getNetwork

          public abstract NFENetwork getNetwork()

      Gets the feature layer's network
      Returns:
      a network instance

    <!-- -->

    - #### getMetadata

          public abstract NFEFeatureLayerMetadata getMetadata()

      Gets the feature layer's metadata
      Returns:
      the feature layer's metadata

    <!-- -->

    - #### setMetadata

          public abstract void setMetadata(NFEFeatureLayerMetadata metadata)

      Sets the feature layer's metadata
      Parameters:
      `metadata` - the feature layer's metadata

    <!-- -->

    - #### setType

          public abstract void setType(FeatureLayerMetadata.FeatureLayerType type)

      Sets the feature layer type
      Parameters:
      `type` - feature layer type

    <!-- -->

    - #### getType

          public abstract FeatureLayerMetadata.FeatureLayerType getType()

      Gets the feature layer type
      Returns:
      the feature layer type

    <!-- -->

    - #### setZOrder

          public abstract void setZOrder(int zOrder)

      Sets the Z order for the feature layer. The Z order can be used by a renderer to determine the sequence the Feature Layers should be rendered.
      Parameters:
      `zOrder` - Z order value

    <!-- -->

    - #### getZOrder

          public abstract int getZOrder()

      Gets the Z order of the feature layer
      Returns:
      Z order value

    <!-- -->

    - #### setEventDispatcher

          public abstract void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

      Sets the event dispatcher.
      Parameters:
      `eventDispatcher` - event dispatcher

    <!-- -->

    - #### getEventDispatcher

          public abstract NFEEventDispatcher<NFEModelListener> getEventDispatcher()

      Returns the event dispatcher.
      Returns:
      event dispatcher

    <!-- -->

    - #### getHierarchyLevel

          public abstract int getHierarchyLevel()

      Gets the hierarchy level of the feature layer
      Returns:
      the feature layer's hierarchy level

    <!-- -->

    - #### setHierarchyLevel

          public abstract void setHierarchyLevel(int hierarchyLevel)

      Sets the Hierarchy Level of the feature layer
      Parameters:
      `hierarchyLevel` - the feature layer's hierarchy level

    <!-- -->

    - #### getAttributeDescriptors

          public abstract java.util.Collection<NFEAttributeDescriptor> getAttributeDescriptors()

      Gets all the attribute descriptors of the feature layer
      Returns:
      a collection containing all the feature layer's attribute descriptors

    <!-- -->

    - #### getAttributeDescriptor

          public abstract NFEAttributeDescriptor getAttributeDescriptor(java.lang.String attrName)

      Gets the attribute descriptor for the given attribute's name
      Parameters:
      `attrName` - a name of a feature layer's attribute

      Returns:
      an attribute descriptor instance

    <!-- -->

    - #### addAttributeDescriptor

          public abstract void addAttributeDescriptor(NFEAttributeDescriptor attrDescriptor)

      Sets an attribute descriptor for the given attribute's name
      Parameters:
      `attrDescriptor` - an attribute descriptor instance

    <!-- -->

    - #### removeAttributeDescriptor

          public abstract NFEAttributeDescriptor removeAttributeDescriptor(java.lang.String attrName)

      Removes the attribute descriptor with the given attribute's name
      Parameters:
      `attrName` - a name of a feature layer's attribute

      Returns:
      an instance of an attribute descriptor or null if the feature layer does not contain such attribute

    <!-- -->

    - #### getFeatures

          public abstract java.util.Collection<NFEFeature> getFeatures()

      Gets all the features in the feature layer.
      Returns:
      a collection containing features

    <!-- -->

    - #### getFeatures

          public abstract java.util.Collection<NFEFeature> getFeatures(long featureClassId)

      Gets all the features with the given Feature Class in the Feature Layer.
      Parameters:

      `featureClassId` -

      Returns:

    <!-- -->

    - #### addFeature

          public abstract boolean addFeature(NFEFeature feature)

      Adds a feature to the feature layer.
      Parameters:
      `feature` - a feature instance

    <!-- -->

    - #### containsFeature

          public abstract boolean containsFeature(NFEFeature feature)

      Tells whether the feature layer contains the given feature
      Parameters:
      `feature` - a feature instance

      Returns:
      true if the feature layer contains the feature

    <!-- -->

    - #### getFeature

          public abstract NFEFeature getFeature(long featureId)

      Gets a feature identified by the given ID contained in the feature layer
      Parameters:
      `featureId` - a feature ID

      Returns:
      a feature instance or null if the feature was not found

    <!-- -->

    - #### removeFeature

          public abstract NFEFeature removeFeature(long featureId)

      Removes a feature identified by the given ID from the feature layer
      Parameters:
      `featureId` - a feature ID

      Returns:
      the removed feature instance or null if the feature could not be removed or was not found

    <!-- -->

    - #### getFeatureClasses

          public abstract java.util.Collection<NFEFeatureClass> getFeatureClasses()

      Gets the feature classes defined for this feature layer
      Returns:
      a collection of feature classes

    <!-- -->

    - #### getFeatureClass

          public abstract NFEFeatureClass getFeatureClass(long featureClassId)

      Gets a feature class which belongs on this feature layer.
      Parameters:
      `featureClassId` - a feature class ID

      Returns:
      a feature class instance or null if the feature class was not found

    <!-- -->

    - #### addFeatureClass

          public abstract boolean addFeatureClass(NFEFeatureClass featureClass)

      Adds a Feature Class instance to the Feature Layer. A Feature Class must only be related to one Feature Layer
      Parameters:
      `featureClass` - a feature class instance

    <!-- -->

    - #### removeFeatureClass

          public abstract NFEFeatureClass removeFeatureClass(long featureClassId)

      Removes a feature class identified by the given ID from the feature layer
      Parameters:
      `featureClassId` -

      Returns:
      the removed feature class or null if it could be removed or was not found

    <!-- -->

    - #### getFeatureClasses

          public abstract java.util.Collection<NFEFeatureClass> getFeatureClasses(NFEFeatureShape shape)

      Gets all the feature classes matching the given shape from the feature layer
      Parameters:
      `shape` - a feature shape type

      Returns:
      a collection of feature class instances

    <!-- -->

    - #### addModelListener

          public abstract void addModelListener(NFEModelListener listener)

    <!-- -->

    - #### removeModelListener

          public abstract void removeModelListener(NFEModelListener listener)

    <!-- -->

    - #### createCopy

          public abstract NFEFeatureLayer createCopy()

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

- [Prev Class](NFEFeatureElement.md)
- [Next Class](NFEFeatureLayerMetadata.md)

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
