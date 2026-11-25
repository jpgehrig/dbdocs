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

- [Prev Class](NFEFeatureClass.md)
- [Next Class](NFEFeatureLayer.md)

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

## Class NFEFeatureElement

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - oracle.spatial.network.nfe.model.feature.NFEFeatureElement

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEBasicFeatureElement](NFEBasicFeatureElement.md)

  ------------------------------------------------------------------------



      public abstract class NFEFeatureElement
      extends NFEBasicModelObject

  Base class for representing a feature element. Feature elements are contained in features. A feature element only may belong to one feature. The way used to differentiate a feature element is the key property. A feature element always lays over a network element. The type of the feature element determines if it can lay over a node or a link.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description    |
    |---------------------------|--------------------------|
    | `static java.lang.String` | `KEY_VAL_SEPARATOR`      |
    | `static java.lang.String` | `PROP_END_PERCENTAGE`    |
    | `static java.lang.String` | `PROP_FEATURE`           |
    | `static java.lang.String` | `PROP_KEY`               |
    | `static java.lang.String` | `PROP_NETWORK_ELEMENT`   |
    | `static java.lang.String` | `PROP_SEQUENCE`          |
    | `static java.lang.String` | `PROP_START_PERCENTAGE`  |
    | `static java.lang.String` | `PROP_TYPE`              |
    | `static java.lang.String` | `UNKNOWN_KEY_VAL`        |

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEFeatureElement``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                   | Method and Description                                                                                                                                       |
    |-----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract NFEFeatureElement`                                                                        | `createCopy``()`<br>Returns object copy.                                                                                                                     |
    | `static java.lang.String`                                                                           | `createKey``(long featLayerId, long featureId, long netElemId, long sequence)`                                                                               |
    | `abstract double`                                                                                   | `getEndPercentage``()`<br>Gets the line feature element's end point relative to its link's length.                                                           |
    | `abstract `[`NFEFeature`](NFEFeature.md)                                                            | `getFeature``()`<br>Gets the feature element's feature                                                                                                       |
    | `abstract `[`NFEFeatureLayer`](NFEFeatureLayer.md)                                                  | `getFeatureLayer``()`<br>Gets the feature element's feature layer.                                                                                           |
    | `abstract java.lang.String`                                                                         | `getKey``()`<br>Gets the feature element's key which is used to uniquely identify a feature element in an NFEModel                                           |
    | `abstract `[`NFENetworkElement`](../network/NFENetworkElement.md)                                   | `getNetworkElement``()`<br>Gets the network element where the feature element resides                                                                        |
    | `abstract long`                                                                                     | `getSequence``()`<br>Gets the feature element's sequence number                                                                                              |
    | `abstract double`                                                                                   | `getStartPercentage``()`<br>Gets the position of the feature element's relative to its link's length.                                                        |
    | `abstract `[`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md) | `getType``()`<br>Gest the type of the feature element.                                                                                                       |
    | `abstract void`                                                                                     | `setEndPercentage``(double endPercentage)`<br>Sets the line feature element's end point relative to its link's length.                                       |
    | `abstract void`                                                                                     | `setFeature``(`[`NFEFeature`](NFEFeature.md)` feature)`<br>Sets the feature which contains the feature element                                               |
    | `abstract void`                                                                                     | `setNetworkElement``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` networkElement)`<br>Sets the network element where the feature element resides |
    | `abstract void`                                                                                     | `setSequence``(long sequence)`<br>Sets the feature element's sequence number                                                                                 |
    | `abstract void`                                                                                     | `setStartPercentage``(double startPercentage)`<br>Sets the feature element's position relative to its link's length.                                         |
    | `abstract void`                                                                                     | `setType``(`[`FeatureElement.FeatureElementType`](../../../lod/FeatureElement.FeatureElementType.md)` type)`<br>Sets the type of the feature element.        |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### UNKNOWN_KEY_VAL

          public static final java.lang.String UNKNOWN_KEY_VAL

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### KEY_VAL_SEPARATOR

          public static final java.lang.String KEY_VAL_SEPARATOR

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_TYPE

          public static final java.lang.String PROP_TYPE

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_KEY

          public static final java.lang.String PROP_KEY

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_START_PERCENTAGE

          public static final java.lang.String PROP_START_PERCENTAGE

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_END_PERCENTAGE

          public static final java.lang.String PROP_END_PERCENTAGE

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_NETWORK_ELEMENT

          public static final java.lang.String PROP_NETWORK_ELEMENT

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_FEATURE

          public static final java.lang.String PROP_FEATURE

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_SEQUENCE

          public static final java.lang.String PROP_SEQUENCE

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFEFeatureElement

          public NFEFeatureElement()

  <!-- -->

  - ### Method Detail

    - #### getKey

          public abstract java.lang.String getKey()

      Gets the feature element's key which is used to uniquely identify a feature element in an NFEModel
      Returns:
      a feature element's key

    <!-- -->

    - #### setFeature

          public abstract void setFeature(NFEFeature feature)

      Sets the feature which contains the feature element
      Parameters:
      `feature` - a feature instance

    <!-- -->

    - #### getFeature

          public abstract NFEFeature getFeature()

      Gets the feature element's feature
      Returns:
      a feature instance

    <!-- -->

    - #### getFeatureLayer

          public abstract NFEFeatureLayer getFeatureLayer()

      Gets the feature element's feature layer. It is a shorthand for NFEFeatureElement.getFeature().getFeatureLayer()
      Returns:
      a feature layer instance

    <!-- -->

    - #### setNetworkElement

          public abstract void setNetworkElement(NFENetworkElement networkElement)

      Sets the network element where the feature element resides
      Parameters:
      `networkElement` - a network element instance (node or link)

    <!-- -->

    - #### getNetworkElement

          public abstract NFENetworkElement getNetworkElement()

      Gets the network element where the feature element resides
      Returns:
      a network element instance (node or link)

    <!-- -->

    - #### setType

          public abstract void setType(FeatureElement.FeatureElementType type)

      Sets the type of the feature element. This type determines if the element can be placed over a link or node.
      Parameters:
      `type` - a feature element type

    <!-- -->

    - #### getType

          public abstract FeatureElement.FeatureElementType getType()

      Gest the type of the feature element.
      Returns:
      a feature element type

    <!-- -->

    - #### setStartPercentage

          public abstract void setStartPercentage(double startPercentage)

      Sets the feature element's position relative to its link's length. For line feature elements this value sets the start of the line. This property is not used when a feature element is set over a node
      Parameters:
      `startPercentage` - a value between 0 and 1

    <!-- -->

    - #### getStartPercentage

          public abstract double getStartPercentage()

      Gets the position of the feature element's relative to its link's length. This property is not used when a feature element is set over a node
      Returns:
      a value between 0 and 1

    <!-- -->

    - #### setEndPercentage

          public abstract void setEndPercentage(double endPercentage)

      Sets the line feature element's end point relative to its link's length. This property is not used for point feature elements.
      Parameters:
      `endPercentage` - a value between 0 and 1

    <!-- -->

    - #### getEndPercentage

          public abstract double getEndPercentage()

      Gets the line feature element's end point relative to its link's length. This property is not used for point feature elements.
      Returns:
      a value between 0 and 1

    <!-- -->

    - #### setSequence

          public abstract void setSequence(long sequence)

      Sets the feature element's sequence number
      Parameters:
      `sequence` - the feature element's sequence

    <!-- -->

    - #### getSequence

          public abstract long getSequence()

      Gets the feature element's sequence number
      Returns:
      the feature element's sequence

    <!-- -->

    - #### createCopy

          public abstract NFEFeatureElement createCopy()

      Returns object copy.
      Returns:
      object copy

    <!-- -->

    - #### createKey

          public static java.lang.String createKey(long featLayerId,
                                                   long featureId,
                                                   long netElemId,
                                                   long sequence)

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

- [Prev Class](NFEFeatureClass.md)
- [Next Class](NFEFeatureLayer.md)

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
