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

- [Prev Class](NFEBasicCatalog.md)
- [Next Class](NFEBasicFeatureClass.md)

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

## Class NFEBasicFeature

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.feature.NFEFeature](NFEFeature.md)

    - - oracle.spatial.network.nfe.model.feature.NFEBasicFeature

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFEBasicFeature
      extends NFEFeature

  The default implementation of [`NFEFeature`](NFEFeature.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.feature.[NFEFeature](NFEFeature.md)

      [`PROP_PARENT_FEATURE_ID`](NFEFeature.md)`, `[`PROP_PARENT_FEATURE_LAYER_ID`](NFEFeature.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicFeature``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                |
    |-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                       | `addFeatureElement``(`[`NFEFeatureElement`](NFEFeatureElement.md)` featureElement)`<br>Adds a feature element to the feature                                                          |
    | `void`                                                          | `addFeatureElements``(java.util.List<`[`NFEFeatureElement`](NFEFeatureElement.md)`> featureElements)`<br>Adds all the feature elements in the collection to the feature               |
    | [`NFEFeature`](NFEFeature.md)                                   | `createCopy``()`<br>Returns object copy.                                                                                                                                              |
    | `java.lang.Object`                                              | `getAttribute``(java.lang.String attributeName)`<br>Gets the value of the attribute with the given name                                                                               |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                         | `getFeatureClass``()`<br>Gets the feature class of the feature                                                                                                                        |
    | `java.util.List<`[`NFEFeatureElement`](NFEFeatureElement.md)`>` | `getFeatureElements``()`<br>Gets all the feature elements in the feature                                                                                                              |
    | [`NFEFeatureLayer`](NFEFeatureLayer.md)                         | `getFeatureLayer``()`<br>Gets the feature's feature layer                                                                                                                             |
    | `long`                                                          | `getId``()`<br>Gets the feature's ID                                                                                                                                                  |
    | `java.lang.String`                                              | `getKey``()`<br>Returns the feature's key.                                                                                                                                            |
    | `long`                                                          | `getParentFeatureId``()`<br>Gets the feature's parent feature ID (if any)                                                                                                             |
    | `long`                                                          | `getParentFeatureLayerId``()`<br>Gets the feature layer ID of the feature's parent feature                                                                                            |
    | `boolean`                                                       | `removeFeatureElement``(`[`NFEFeatureElement`](NFEFeatureElement.md)` featureElement)`<br>Removes the given feature element from the feature                                          |
    | `void`                                                          | `removeFeatureElements``(java.util.Collection<`[`NFEFeatureElement`](NFEFeatureElement.md)`> featureElements)`<br>Removes from the feature all the feature elements in the collection |
    | `void`                                                          | `setAttribute``(java.lang.String attributeName, java.lang.Object attributeValue)`<br>Sets the value of the attribute with the given name                                              |
    | `void`                                                          | `setFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` featureClass)`<br>Sets the feature class of the feature                                                                  |
    | `void`                                                          | `setFeatureLayer``(`[`NFEFeatureLayer`](NFEFeatureLayer.md)` featureLayer)`<br>Sets the feature's feature layer                                                                       |
    | `void`                                                          | `setId``(long id)`<br>Sets the feature's ID                                                                                                                                           |
    | `void`                                                          | `setParentFeatureId``(long parentFeatId)`<br>Sets the feature's parent feature ID                                                                                                     |
    | `void`                                                          | `setParentFeatureLayerId``(long parentFeatLayerId)`<br>Sets the feature layer ID of the feature's parent feature.                                                                     |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicFeature

          public NFEBasicFeature()

  <!-- -->

  - ### Method Detail

    - #### setFeatureLayer

          public void setFeatureLayer(NFEFeatureLayer featureLayer)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the feature's feature layer
      Specified by:
      [`setFeatureLayer`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureLayer` - a feature layer instance

    <!-- -->

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the feature's feature layer
      Specified by:
      [`getFeatureLayer`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a feature layer instance

    <!-- -->

    - #### setId

          public void setId(long id)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the feature's ID
      Specified by:
      [`setId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `id` - a feature ID

    <!-- -->

    - #### getId

          public long getId()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the feature's ID
      Specified by:
      [`getId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a feature ID

    <!-- -->

    - #### setParentFeatureId

          public void setParentFeatureId(long parentFeatId)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the feature's parent feature ID
      Specified by:
      [`setParentFeatureId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `parentFeatId` - a feature ID

    <!-- -->

    - #### getParentFeatureId

          public long getParentFeatureId()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the feature's parent feature ID (if any)
      Specified by:
      [`getParentFeatureId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a feature ID or -1 if the feature does not have a parent feature

    <!-- -->

    - #### setParentFeatureLayerId

          public void setParentFeatureLayerId(long parentFeatLayerId)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the feature layer ID of the feature's parent feature. The parent can be from a higher hierarchy feature layer or from a feature layer in another model.
      Specified by:
      [`setParentFeatureLayerId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `parentFeatLayerId` - a feature layer ID

    <!-- -->

    - #### getParentFeatureLayerId

          public long getParentFeatureLayerId()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the feature layer ID of the feature's parent feature
      Specified by:
      [`getParentFeatureLayerId`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a feature layer ID

    <!-- -->

    - #### setFeatureClass

          public void setFeatureClass(NFEFeatureClass featureClass)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the feature class of the feature
      Specified by:
      [`setFeatureClass`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureClass` - a feature class instance

    <!-- -->

    - #### getFeatureClass

          public NFEFeatureClass getFeatureClass()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the feature class of the feature
      Specified by:
      [`getFeatureClass`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a feature class instance

    <!-- -->

    - #### getKey

          public java.lang.String getKey()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Returns the feature's key. The key is a unique identifier among features of any Feature Layer. It has the following format: FeatureLayerId_FeautureId
      Specified by:
      [`getKey`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      Returns the Feature's key

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String attributeName,
                                   java.lang.Object attributeValue)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Sets the value of the attribute with the given name
      Specified by:
      [`setAttribute`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `attributeName` - an attribute name

      `attributeValue` - the value of the attribute

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String attributeName)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets the value of the attribute with the given name
      Specified by:
      [`getAttribute`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `attributeName` - an attribute name

      Returns:
      the value of the attribute or null if the attribute does not exist or has not been set

    <!-- -->

    - #### addFeatureElement

          public boolean addFeatureElement(NFEFeatureElement featureElement)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Adds a feature element to the feature
      Specified by:
      [`addFeatureElement`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureElement` - a feature element instance

      Returns:
      true if the feature could be added to the feature

    <!-- -->

    - #### addFeatureElements

          public void addFeatureElements(java.util.List<NFEFeatureElement> featureElements)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Adds all the feature elements in the collection to the feature
      Specified by:
      [`addFeatureElements`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureElements` - a collection of feature element instances

    <!-- -->

    - #### getFeatureElements

          public java.util.List<NFEFeatureElement> getFeatureElements()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Gets all the feature elements in the feature
      Specified by:
      [`getFeatureElements`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Returns:
      a list of feature element instances.

    <!-- -->

    - #### removeFeatureElement

          public boolean removeFeatureElement(NFEFeatureElement featureElement)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Removes the given feature element from the feature
      Specified by:
      [`removeFeatureElement`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureElement` - a feature element instance

      Returns:
      true if the feature element was removed

    <!-- -->

    - #### removeFeatureElements

          public void removeFeatureElements(java.util.Collection<NFEFeatureElement> featureElements)

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Removes from the feature all the feature elements in the collection
      Specified by:
      [`removeFeatureElements`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

      Parameters:
      `featureElements` - a collection of feature element instances

    <!-- -->

    - #### createCopy

          public NFEFeature createCopy()

      Description copied from class: [`NFEFeature`](NFEFeature.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEFeature.md) in class [`NFEFeature`](NFEFeature.md)

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

- [Prev Class](NFEBasicCatalog.md)
- [Next Class](NFEBasicFeatureClass.md)

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
