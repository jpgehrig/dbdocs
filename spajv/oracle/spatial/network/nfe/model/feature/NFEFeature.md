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

- [Prev Class](NFECatalogValue.md)
- [Next Class](NFEFeatureClass.md)

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

## Class NFEFeature

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - oracle.spatial.network.nfe.model.feature.NFEFeature

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEBasicFeature](NFEBasicFeature.md)

  ------------------------------------------------------------------------



      public abstract class NFEFeature
      extends NFEBasicModelObject

  This is the base class for representing a single network feature in memory. A feature must belong to a feature layer, otherwise, it is considered a standalone feature. When a feature belongs to a feature layer, any change to a feature property is notified to its parent feature layer. Also, any change notified from a feature's feature element, is notified to the feature layer.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                 |
    |---------------------------|-----------------------------------------------------------------------|
    | `static java.lang.String` | `PROP_PARENT_FEATURE_ID`<br>Feature's parent feature ID property      |
    | `static java.lang.String` | `PROP_PARENT_FEATURE_LAYER_ID`<br>Feature's feature layer ID property |

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEFeature``()`            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                |
    |--------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract boolean`                                                       | `addFeatureElement``(`[`NFEFeatureElement`](NFEFeatureElement.md)` featureElement)`<br>Adds a feature element to the feature                                                          |
    | `abstract void`                                                          | `addFeatureElements``(java.util.List<`[`NFEFeatureElement`](NFEFeatureElement.md)`> featureElements)`<br>Adds all the feature elements in the collection to the feature               |
    | `abstract NFEFeature`                                                    | `createCopy``()`<br>Returns object copy.                                                                                                                                              |
    | `abstract java.lang.Object`                                              | `getAttribute``(java.lang.String attributeName)`<br>Gets the value of the attribute with the given name                                                                               |
    | `abstract `[`NFEFeatureClass`](NFEFeatureClass.md)                       | `getFeatureClass``()`<br>Gets the feature class of the feature                                                                                                                        |
    | `abstract java.util.List<`[`NFEFeatureElement`](NFEFeatureElement.md)`>` | `getFeatureElements``()`<br>Gets all the feature elements in the feature                                                                                                              |
    | `abstract `[`NFEFeatureLayer`](NFEFeatureLayer.md)                       | `getFeatureLayer``()`<br>Gets the feature's feature layer                                                                                                                             |
    | `abstract long`                                                          | `getId``()`<br>Gets the feature's ID                                                                                                                                                  |
    | `abstract java.lang.String`                                              | `getKey``()`<br>Returns the feature's key.                                                                                                                                            |
    | `abstract long`                                                          | `getParentFeatureId``()`<br>Gets the feature's parent feature ID (if any)                                                                                                             |
    | `abstract long`                                                          | `getParentFeatureLayerId``()`<br>Gets the feature layer ID of the feature's parent feature                                                                                            |
    | `abstract boolean`                                                       | `removeFeatureElement``(`[`NFEFeatureElement`](NFEFeatureElement.md)` featureElement)`<br>Removes the given feature element from the feature                                          |
    | `abstract void`                                                          | `removeFeatureElements``(java.util.Collection<`[`NFEFeatureElement`](NFEFeatureElement.md)`> featureElements)`<br>Removes from the feature all the feature elements in the collection |
    | `abstract void`                                                          | `setAttribute``(java.lang.String attributeName, java.lang.Object attributeValue)`<br>Sets the value of the attribute with the given name                                              |
    | `abstract void`                                                          | `setFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` featureClass)`<br>Sets the feature class of the feature                                                                  |
    | `abstract void`                                                          | `setFeatureLayer``(`[`NFEFeatureLayer`](NFEFeatureLayer.md)` featureLayer)`<br>Sets the feature's feature layer                                                                       |
    | `abstract void`                                                          | `setId``(long id)`<br>Sets the feature's ID                                                                                                                                           |
    | `abstract void`                                                          | `setParentFeatureId``(long parentFeatureId)`<br>Sets the feature's parent feature ID                                                                                                  |
    | `abstract void`                                                          | `setParentFeatureLayerId``(long parentFeatureLayerId)`<br>Sets the feature layer ID of the feature's parent feature.                                                                  |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROP_PARENT_FEATURE_ID

          public static final java.lang.String PROP_PARENT_FEATURE_ID

      Feature's parent feature ID property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_PARENT_FEATURE_LAYER_ID

          public static final java.lang.String PROP_PARENT_FEATURE_LAYER_ID

      Feature's feature layer ID property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFEFeature

          public NFEFeature()

  <!-- -->

  - ### Method Detail

    - #### setFeatureLayer

          public abstract void setFeatureLayer(NFEFeatureLayer featureLayer)

      Sets the feature's feature layer
      Parameters:
      `featureLayer` - a feature layer instance

    <!-- -->

    - #### getFeatureLayer

          public abstract NFEFeatureLayer getFeatureLayer()

      Gets the feature's feature layer
      Returns:
      a feature layer instance

    <!-- -->

    - #### setId

          public abstract void setId(long id)

      Sets the feature's ID
      Parameters:
      `id` - a feature ID

    <!-- -->

    - #### getId

          public abstract long getId()

      Gets the feature's ID
      Returns:
      a feature ID

    <!-- -->

    - #### setParentFeatureId

          public abstract void setParentFeatureId(long parentFeatureId)

      Sets the feature's parent feature ID
      Parameters:
      `parentFeatureId` - a feature ID

    <!-- -->

    - #### getParentFeatureId

          public abstract long getParentFeatureId()

      Gets the feature's parent feature ID (if any)
      Returns:
      a feature ID or -1 if the feature does not have a parent feature

    <!-- -->

    - #### setParentFeatureLayerId

          public abstract void setParentFeatureLayerId(long parentFeatureLayerId)

      Sets the feature layer ID of the feature's parent feature. The parent can be from a higher hierarchy feature layer or from a feature layer in another model.
      Parameters:
      `parentFeatureLayerId` - a feature layer ID

    <!-- -->

    - #### getParentFeatureLayerId

          public abstract long getParentFeatureLayerId()

      Gets the feature layer ID of the feature's parent feature
      Returns:
      a feature layer ID

    <!-- -->

    - #### setFeatureClass

          public abstract void setFeatureClass(NFEFeatureClass featureClass)

      Sets the feature class of the feature
      Parameters:
      `featureClass` - a feature class instance

    <!-- -->

    - #### getFeatureClass

          public abstract NFEFeatureClass getFeatureClass()

      Gets the feature class of the feature
      Returns:
      a feature class instance

    <!-- -->

    - #### getKey

          public abstract java.lang.String getKey()

      Returns the feature's key. The key is a unique identifier among features of any Feature Layer. It has the following format: FeatureLayerId_FeautureId
      Returns:
      Returns the Feature's key

    <!-- -->

    - #### getAttribute

          public abstract java.lang.Object getAttribute(java.lang.String attributeName)

      Gets the value of the attribute with the given name
      Parameters:
      `attributeName` - an attribute name

      Returns:
      the value of the attribute or null if the attribute does not exist or has not been set

    <!-- -->

    - #### setAttribute

          public abstract void setAttribute(java.lang.String attributeName,
                                            java.lang.Object attributeValue)

      Sets the value of the attribute with the given name
      Parameters:
      `attributeName` - an attribute name

      `attributeValue` - the value of the attribute

    <!-- -->

    - #### addFeatureElement

          public abstract boolean addFeatureElement(NFEFeatureElement featureElement)

      Adds a feature element to the feature
      Parameters:
      `featureElement` - a feature element instance

      Returns:
      true if the feature could be added to the feature

    <!-- -->

    - #### addFeatureElements

          public abstract void addFeatureElements(java.util.List<NFEFeatureElement> featureElements)

      Adds all the feature elements in the collection to the feature
      Parameters:
      `featureElements` - a collection of feature element instances

    <!-- -->

    - #### getFeatureElements

          public abstract java.util.List<NFEFeatureElement> getFeatureElements()

      Gets all the feature elements in the feature
      Returns:
      a list of feature element instances.

    <!-- -->

    - #### removeFeatureElement

          public abstract boolean removeFeatureElement(NFEFeatureElement featureElement)

      Removes the given feature element from the feature
      Parameters:
      `featureElement` - a feature element instance

      Returns:
      true if the feature element was removed

    <!-- -->

    - #### removeFeatureElements

          public abstract void removeFeatureElements(java.util.Collection<NFEFeatureElement> featureElements)

      Removes from the feature all the feature elements in the collection
      Parameters:
      `featureElements` - a collection of feature element instances

    <!-- -->

    - #### createCopy

          public abstract NFEFeature createCopy()

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

- [Prev Class](NFECatalogValue.md)
- [Next Class](NFEFeatureClass.md)

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
