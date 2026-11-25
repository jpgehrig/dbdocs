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

- [Prev Class](NFEBasicFeatureElement.md)
- [Next Class](NFEBasicPredefinedConnectedPoint.md)

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

## Class NFEBasicFeatureLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.model.feature.NFEFeatureLayer](NFEFeatureLayer.md)

  - - oracle.spatial.network.nfe.model.feature.NFEBasicFeatureLayer

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEBasicFeatureLayer
      extends NFEFeatureLayer

  The default implementation of [`NFEFeatureLayer`](NFEFeatureLayer.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.feature.[NFEFeatureLayer](NFEFeatureLayer.md)

      [`PROP_Z_ORDER`](NFEFeatureLayer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicFeatureLayer``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                              | Method and Description                                                                                                                                                               |
    |----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                         | `addAttributeDescriptor``(`[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)` attrDescriptor)`<br>Sets an attribute descriptor for the given attribute's name                    |
    | `boolean`                                                                                                      | `addFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Adds a feature to the feature layer.                                                                                      |
    | `boolean`                                                                                                      | `addFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` featureClass)`<br>Adds a Feature Class instance to the Feature Layer.                                                   |
    | `void`                                                                                                         | `addFeatures``(java.util.Collection<`[`NFEFeature`](NFEFeature.md)`> features)`<br>Adds all the features in the collection to the feature layer                                      |
    | `void`                                                                                                         | `addModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`                                                                                                  |
    | `boolean`                                                                                                      | `containsFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Tells whether the feature layer contains the given feature                                                           |
    | [`NFEFeatureLayer`](NFEFeatureLayer.md)                                                                        | `createCopy``()`<br>Returns object copy.                                                                                                                                             |
    | [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)                                                          | `getAttributeDescriptor``(java.lang.String attrName)`<br>Gets the attribute descriptor for the given attribute's name                                                                |
    | `java.util.Collection<`[`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)`>`                                | `getAttributeDescriptors``()`<br>Gets all the attribute descriptors of the feature layer                                                                                             |
    | [`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`>` | `getEventDispatcher``()`<br>Returns the event dispatcher.                                                                                                                            |
    | [`NFEFeature`](NFEFeature.md)                                                                                  | `getFeature``(long featureId)`<br>Gets a feature identified by the given ID contained in the feature layer                                                                           |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                                                                        | `getFeatureClass``(long featureClassId)`<br>Gets a feature class which belongs on this feature layer.                                                                                |
    | `java.util.Collection<`[`NFEFeatureClass`](NFEFeatureClass.md)`>`                                              | `getFeatureClasses``()`<br>Gets the feature classes defined for this feature layer                                                                                                   |
    | `java.util.Collection<`[`NFEFeatureClass`](NFEFeatureClass.md)`>`                                              | `getFeatureClasses``(`[`NFEFeatureShape`](NFEFeatureShape.md)` shape)`<br>Gets all the feature classes matching the given shape from the feature layer                               |
    | `java.util.Collection<`[`NFEFeature`](NFEFeature.md)`>`                                                        | `getFeatures``()`<br>Gets all the features in the feature layer.                                                                                                                     |
    | `java.util.Collection<`[`NFEFeature`](NFEFeature.md)`>`                                                        | `getFeatures``(long featureClassId)`<br>Gets all the features with the given Feature Class in the Feature Layer.                                                                     |
    | `int`                                                                                                          | `getHierarchyLevel``()`<br>Gets the hierarchy level of the feature layer                                                                                                             |
    | `long`                                                                                                         | `getId``()`<br>Gets the id of the feature layer                                                                                                                                      |
    | [`NFEFeatureLayerMetadata`](NFEFeatureLayerMetadata.md)                                                        | `getMetadata``()`<br>Gets the feature layer's metadata                                                                                                                               |
    | `java.lang.String`                                                                                             | `getName``()`<br>Gets the name of the feature layer                                                                                                                                  |
    | [`NFENetwork`](../network/NFENetwork.md)                                                                       | `getNetwork``()`<br>Gets the feature layer's network                                                                                                                                 |
    | [`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md)               | `getType``()`<br>Gets the feature layer type                                                                                                                                         |
    | `int`                                                                                                          | `getZOrder``()`<br>Gets the Z order of the feature layer                                                                                                                             |
    | [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)                                                          | `removeAttributeDescriptor``(java.lang.String attrName)`<br>Removes the attribute descriptor with the given attribute's name                                                         |
    | [`NFEFeature`](NFEFeature.md)                                                                                  | `removeFeature``(long featureId)`<br>Removes a feature identified by the given ID from the feature layer                                                                             |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                                                                        | `removeFeatureClass``(long featureClassId)`<br>Removes a feature class identified by the given ID from the feature layer                                                             |
    | `void`                                                                                                         | `removeModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`                                                                                               |
    | `void`                                                                                                         | `setEventDispatcher``(`[`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`> eventDispatcher)`<br>Sets the event dispatcher. |
    | `void`                                                                                                         | `setHierarchyLevel``(int hierarchyLevel)`<br>Sets the Hierarchy Level of the feature layer                                                                                           |
    | `void`                                                                                                         | `setId``(long id)`<br>Sets the ID of the feature layer                                                                                                                               |
    | `void`                                                                                                         | `setMetadata``(`[`NFEFeatureLayerMetadata`](NFEFeatureLayerMetadata.md)` metadata)`<br>Sets the feature layer's metadata                                                             |
    | `void`                                                                                                         | `setName``(java.lang.String name)`<br>Sets the name of the feature layer                                                                                                             |
    | `void`                                                                                                         | `setNetwork``(`[`NFENetwork`](../network/NFENetwork.md)` network)`<br>Sets the feature layer's network                                                                               |
    | `void`                                                                                                         | `setType``(`[`FeatureLayerMetadata.FeatureLayerType`](../../../lod/FeatureLayerMetadata.FeatureLayerType.md)` type)`<br>Sets the feature layer type                                  |
    | `void`                                                                                                         | `setZOrder``(int zOrder)`<br>Sets the Z order for the feature layer.                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicFeatureLayer

          public NFEBasicFeatureLayer()

  <!-- -->

  - ### Method Detail

    - #### setId

          public void setId(long id)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the ID of the feature layer
      Specified by:
      [`setId`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `id` - the feature layer's ID

    <!-- -->

    - #### getId

          public long getId()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the id of the feature layer
      Specified by:
      [`getId`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the feature layer's ID

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the name of the feature layer
      Specified by:
      [`setName`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `name` - the feature layer's name

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the name of the feature layer
      Specified by:
      [`getName`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the feature layer's name

    <!-- -->

    - #### setNetwork

          public void setNetwork(NFENetwork network)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the feature layer's network
      Specified by:
      [`setNetwork`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `network` - a network instance

    <!-- -->

    - #### getNetwork

          public NFENetwork getNetwork()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the feature layer's network
      Specified by:
      [`getNetwork`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      a network instance

    <!-- -->

    - #### setMetadata

          public void setMetadata(NFEFeatureLayerMetadata metadata)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the feature layer's metadata
      Specified by:
      [`setMetadata`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `metadata` - the feature layer's metadata

    <!-- -->

    - #### getMetadata

          public NFEFeatureLayerMetadata getMetadata()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the feature layer's metadata
      Specified by:
      [`getMetadata`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the feature layer's metadata

    <!-- -->

    - #### setType

          public void setType(FeatureLayerMetadata.FeatureLayerType type)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the feature layer type
      Specified by:
      [`setType`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `type` - feature layer type

    <!-- -->

    - #### getType

          public FeatureLayerMetadata.FeatureLayerType getType()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the feature layer type
      Specified by:
      [`getType`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the feature layer type

    <!-- -->

    - #### setZOrder

          public void setZOrder(int zOrder)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the Z order for the feature layer. The Z order can be used by a renderer to determine the sequence the Feature Layers should be rendered.
      Specified by:
      [`setZOrder`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `zOrder` - Z order value

    <!-- -->

    - #### getZOrder

          public int getZOrder()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the Z order of the feature layer
      Specified by:
      [`getZOrder`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      Z order value

    <!-- -->

    - #### setEventDispatcher

          public void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the event dispatcher.
      Specified by:
      [`setEventDispatcher`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `eventDispatcher` - event dispatcher

    <!-- -->

    - #### getEventDispatcher

          public NFEEventDispatcher<NFEModelListener> getEventDispatcher()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Returns the event dispatcher.
      Specified by:
      [`getEventDispatcher`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      event dispatcher

    <!-- -->

    - #### setHierarchyLevel

          public void setHierarchyLevel(int hierarchyLevel)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets the Hierarchy Level of the feature layer
      Specified by:
      [`setHierarchyLevel`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `hierarchyLevel` - the feature layer's hierarchy level

    <!-- -->

    - #### getHierarchyLevel

          public int getHierarchyLevel()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the hierarchy level of the feature layer
      Specified by:
      [`getHierarchyLevel`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the feature layer's hierarchy level

    <!-- -->

    - #### getAttributeDescriptors

          public java.util.Collection<NFEAttributeDescriptor> getAttributeDescriptors()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets all the attribute descriptors of the feature layer
      Specified by:
      [`getAttributeDescriptors`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      a collection containing all the feature layer's attribute descriptors

    <!-- -->

    - #### getAttributeDescriptor

          public NFEAttributeDescriptor getAttributeDescriptor(java.lang.String attrName)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the attribute descriptor for the given attribute's name
      Specified by:
      [`getAttributeDescriptor`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `attrName` - a name of a feature layer's attribute

      Returns:
      an attribute descriptor instance

    <!-- -->

    - #### addAttributeDescriptor

          public void addAttributeDescriptor(NFEAttributeDescriptor attrDescriptor)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Sets an attribute descriptor for the given attribute's name
      Specified by:
      [`addAttributeDescriptor`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `attrDescriptor` - an attribute descriptor instance

    <!-- -->

    - #### removeAttributeDescriptor

          public NFEAttributeDescriptor removeAttributeDescriptor(java.lang.String attrName)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Removes the attribute descriptor with the given attribute's name
      Specified by:
      [`removeAttributeDescriptor`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `attrName` - a name of a feature layer's attribute

      Returns:
      an instance of an attribute descriptor or null if the feature layer does not contain such attribute

    <!-- -->

    - #### getFeatures

          public java.util.Collection<NFEFeature> getFeatures()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets all the features in the feature layer.
      Specified by:
      [`getFeatures`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      a collection containing features

    <!-- -->

    - #### getFeatures

          public java.util.Collection<NFEFeature> getFeatures(long featureClassId)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets all the features with the given Feature Class in the Feature Layer.
      Specified by:

      [`getFeatures`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:

    <!-- -->

    - #### addFeature

          public boolean addFeature(NFEFeature feature)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Adds a feature to the feature layer.
      Specified by:
      [`addFeature`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `feature` - a feature instance

    <!-- -->

    - #### addFeatures

          public void addFeatures(java.util.Collection<NFEFeature> features)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Adds all the features in the collection to the feature layer
      Parameters:
      `features` - a collection of feature instances

    <!-- -->

    - #### containsFeature

          public boolean containsFeature(NFEFeature feature)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Tells whether the feature layer contains the given feature
      Specified by:
      [`containsFeature`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `feature` - a feature instance

      Returns:
      true if the feature layer contains the feature

    <!-- -->

    - #### getFeature

          public NFEFeature getFeature(long featureId)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets a feature identified by the given ID contained in the feature layer
      Specified by:
      [`getFeature`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `featureId` - a feature ID

      Returns:
      a feature instance or null if the feature was not found

    <!-- -->

    - #### removeFeature

          public NFEFeature removeFeature(long featureId)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Removes a feature identified by the given ID from the feature layer
      Specified by:
      [`removeFeature`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `featureId` - a feature ID

      Returns:
      the removed feature instance or null if the feature could not be removed or was not found

    <!-- -->

    - #### getFeatureClasses

          public java.util.Collection<NFEFeatureClass> getFeatureClasses()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets the feature classes defined for this feature layer
      Specified by:
      [`getFeatureClasses`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      a collection of feature classes

    <!-- -->

    - #### getFeatureClass

          public NFEFeatureClass getFeatureClass(long featureClassId)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets a feature class which belongs on this feature layer.
      Specified by:
      [`getFeatureClass`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `featureClassId` - a feature class ID

      Returns:
      a feature class instance or null if the feature class was not found

    <!-- -->

    - #### addFeatureClass

          public boolean addFeatureClass(NFEFeatureClass featureClass)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Adds a Feature Class instance to the Feature Layer. A Feature Class must only be related to one Feature Layer
      Specified by:
      [`addFeatureClass`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `featureClass` - a feature class instance

    <!-- -->

    - #### removeFeatureClass

          public NFEFeatureClass removeFeatureClass(long featureClassId)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Removes a feature class identified by the given ID from the feature layer
      Specified by:
      [`removeFeatureClass`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Returns:
      the removed feature class or null if it could be removed or was not found

    <!-- -->

    - #### getFeatureClasses

          public java.util.Collection<NFEFeatureClass> getFeatureClasses(NFEFeatureShape shape)

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Gets all the feature classes matching the given shape from the feature layer
      Specified by:
      [`getFeatureClasses`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

      Parameters:
      `shape` - a feature shape type

      Returns:
      a collection of feature class instances

    <!-- -->

    - #### addModelListener

          public void addModelListener(NFEModelListener listener)

      Specified by:
      [`addModelListener`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

    <!-- -->

    - #### removeModelListener

          public void removeModelListener(NFEModelListener listener)

      Specified by:
      [`removeModelListener`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

    <!-- -->

    - #### createCopy

          public NFEFeatureLayer createCopy()

      Description copied from class: [`NFEFeatureLayer`](NFEFeatureLayer.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEFeatureLayer.md) in class [`NFEFeatureLayer`](NFEFeatureLayer.md)

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

- [Prev Class](NFEBasicFeatureElement.md)
- [Next Class](NFEBasicPredefinedConnectedPoint.md)

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
