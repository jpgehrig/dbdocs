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

- [Prev Class](NFEBasicFeatureClass.md)
- [Next Class](NFEBasicFeatureLayer.md)

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

## Class NFEBasicFeatureElement

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.feature.NFEFeatureElement](NFEFeatureElement.md)

    - - oracle.spatial.network.nfe.model.feature.NFEBasicFeatureElement

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFEBasicFeatureElement
      extends NFEFeatureElement

  The default implementation of [`NFEFeatureElement`](NFEFeatureElement.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.feature.[NFEFeatureElement](NFEFeatureElement.md)

      [`KEY_VAL_SEPARATOR`](NFEFeatureElement.md)`, `[`PROP_END_PERCENTAGE`](NFEFeatureElement.md)`, `[`PROP_FEATURE`](NFEFeatureElement.md)`, `[`PROP_KEY`](NFEFeatureElement.md)`, `[`PROP_NETWORK_ELEMENT`](NFEFeatureElement.md)`, `[`PROP_SEQUENCE`](NFEFeatureElement.md)`, `[`PROP_START_PERCENTAGE`](NFEFeatureElement.md)`, `[`PROP_TYPE`](NFEFeatureElement.md)`, `[`UNKNOWN_KEY_VAL`](NFEFeatureElement.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `NFEBasicFeatureElement``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                        | Method and Description                                                                                                                                       |
    |------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEFeatureElement`](NFEFeatureElement.md)                                              | `createCopy``()`<br>Returns object copy.                                                                                                                     |
    | `double`                                                                                 | `getEndPercentage``()`<br>Gets the line feature element's end point relative to its link's length.                                                           |
    | [`NFEFeature`](NFEFeature.md)                                                            | `getFeature``()`<br>Gets the feature element's feature                                                                                                       |
    | [`NFEFeatureLayer`](NFEFeatureLayer.md)                                                  | `getFeatureLayer``()`<br>Gets the feature element's feature layer.                                                                                           |
    | `java.lang.String`                                                                       | `getKey``()`<br>Gets the feature element's key which is used to uniquely identify a feature element in an NFEModel                                           |
    | [`NFENetworkElement`](../network/NFENetworkElement.md)                                   | `getNetworkElement``()`<br>Gets the network element where the feature element resides                                                                        |
    | `long`                                                                                   | `getSequence``()`<br>Gets the feature element's sequence number                                                                                              |
    | `double`                                                                                 | `getStartPercentage``()`<br>Gets the position of the feature element's relative to its link's length.                                                        |
    | [`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md) | `getType``()`<br>Gest the type of the feature element.                                                                                                       |
    | `void`                                                                                   | `setEndPercentage``(double endPercentage)`<br>Sets the line feature element's end point relative to its link's length.                                       |
    | `void`                                                                                   | `setFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Sets the feature which contains the feature element                                               |
    | `void`                                                                                   | `setNetworkElement``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` networkElement)`<br>Sets the network element where the feature element resides |
    | `void`                                                                                   | `setSequence``(long sequence)`<br>Sets the feature element's sequence number                                                                                 |
    | `void`                                                                                   | `setStartPercentage``(double startPercentage)`<br>Sets the feature element's position relative to its link's length.                                         |
    | `void`                                                                                   | `setType``(`[`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md)` type)`<br>Sets the type of the feature element.        |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.feature.[NFEFeatureElement](NFEFeatureElement.md)

      [`createKey`](NFEFeatureElement.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicFeatureElement

          public NFEBasicFeatureElement()

  <!-- -->

  - ### Method Detail

    - #### getKey

          public java.lang.String getKey()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the feature element's key which is used to uniquely identify a feature element in an NFEModel
      Specified by:
      [`getKey`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a feature element's key

    <!-- -->

    - #### setFeature

          public void setFeature(NFEFeature feature)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the feature which contains the feature element
      Specified by:
      [`setFeature`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `feature` - a feature instance

    <!-- -->

    - #### getFeature

          public NFEFeature getFeature()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the feature element's feature
      Specified by:
      [`getFeature`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a feature instance

    <!-- -->

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the feature element's feature layer. It is a shorthand for NFEFeatureElement.getFeature().getFeatureLayer()
      Specified by:
      [`getFeatureLayer`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a feature layer instance

    <!-- -->

    - #### setNetworkElement

          public void setNetworkElement(NFENetworkElement networkElement)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the network element where the feature element resides
      Specified by:
      [`setNetworkElement`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `networkElement` - a network element instance (node or link)

    <!-- -->

    - #### getNetworkElement

          public NFENetworkElement getNetworkElement()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the network element where the feature element resides
      Specified by:
      [`getNetworkElement`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a network element instance (node or link)

    <!-- -->

    - #### setType

          public void setType(FeatureElement.FeatureElementType type)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the type of the feature element. This type determines if the element can be placed over a link or node.
      Specified by:
      [`setType`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `type` - a feature element type

    <!-- -->

    - #### getType

          public FeatureElement.FeatureElementType getType()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gest the type of the feature element.
      Specified by:
      [`getType`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a feature element type

    <!-- -->

    - #### setStartPercentage

          public void setStartPercentage(double startPercentage)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the feature element's position relative to its link's length. For line feature elements this value sets the start of the line. This property is not used when a feature element is set over a node
      Specified by:
      [`setStartPercentage`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `startPercentage` - a value between 0 and 1

    <!-- -->

    - #### getStartPercentage

          public double getStartPercentage()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the position of the feature element's relative to its link's length. This property is not used when a feature element is set over a node
      Specified by:
      [`getStartPercentage`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a value between 0 and 1

    <!-- -->

    - #### setEndPercentage

          public void setEndPercentage(double endPercentage)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the line feature element's end point relative to its link's length. This property is not used for point feature elements.
      Specified by:
      [`setEndPercentage`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `endPercentage` - a value between 0 and 1

    <!-- -->

    - #### getEndPercentage

          public double getEndPercentage()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the line feature element's end point relative to its link's length. This property is not used for point feature elements.
      Specified by:
      [`getEndPercentage`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      a value between 0 and 1

    <!-- -->

    - #### setSequence

          public void setSequence(long sequence)

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Sets the feature element's sequence number
      Specified by:
      [`setSequence`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Parameters:
      `sequence` - the feature element's sequence

    <!-- -->

    - #### getSequence

          public long getSequence()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Gets the feature element's sequence number
      Specified by:
      [`getSequence`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

      Returns:
      the feature element's sequence

    <!-- -->

    - #### createCopy

          public NFEFeatureElement createCopy()

      Description copied from class: [`NFEFeatureElement`](NFEFeatureElement.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEFeatureElement.md) in class [`NFEFeatureElement`](NFEFeatureElement.md)

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

- [Prev Class](NFEBasicFeatureClass.md)
- [Next Class](NFEBasicFeatureLayer.md)

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
