Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LongHashTable.md)
- [Next Class](NFEResources.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.util

## Class NFEFeatureUtils

- java.lang.Object

- - oracle.spatial.network.nfe.util.NFEFeatureUtils

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEFeatureUtils
      extends java.lang.Object

  Provides some utilities functions related to the features.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                             |
    |---------------------------|---------------------------------------------------|
    | `static java.lang.Double` | `ARROW_MARKER_HEIGHT`<br>Arrow marker height.     |
    | `static java.lang.String` | `ARROW_MARKER_NAME`<br>Arrow marker name.         |
    | `static java.lang.Double` | `ARROW_MARKER_POSITION`<br>Arrow marker position. |
    | `static java.lang.Double` | `ARROW_MARKER_WIDTH`<br>Arrow marker width.       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEFeatureUtils``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                                                      |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `calculateFeatureElementGeometry``(`[`NFEFeatureElement`](../model/feature/NFEFeatureElement.md)` featElem, `[`JGeometry`](../../../geometry/JGeometry.md)` netElemGeom)`<br>Returns the feature element geometry considering the start and end percentage. |
    | `static StyleMarker`                                   | `getArrowStyle``(`[`NFELink`](../model/network/NFELink.md)` nfeLink, boolean isPath, boolean isNetworkDirected)`<br>Returns the arrow marker style for the link.                                                                                            |
    | `static StyleMarker`                                   | `getBiDirectionalArrow``()`<br>Returns the arrow marker style for a bidirectional arrow.                                                                                                                                                                    |
    | `static int`                                           | `getFeatureElementType``(`[`FeatureElement.FeatureElementType`](../../lod/FeatureElement.FeatureElementType.md)` type)`<br>Returns the feature element type identifier.                                                                                     |
    | `static int`                                           | `getFeatureLayerType``(`[`FeatureLayerMetadata.FeatureLayerType`](../../lod/FeatureLayerMetadata.FeatureLayerType.md)` featureLayerType)`<br>Returns the feature layer type identifier.                                                                     |
    | `static StyleMarker`                                   | `getSimpleArrow``()`<br>Returns the arrow marker style for an unidirectional arrow.                                                                                                                                                                         |
    | `static void`                                          | `setBiDirectionalArrow``(StyleMarker biDirectionalArrow)`<br>Sets the arrow marker style for a bidirectional arrow.                                                                                                                                         |
    | `static void`                                          | `setSimpleArrow``(StyleMarker simpleArrow)`<br>Sets the arrow marker style for an unidirectional arrow.                                                                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ARROW_MARKER_NAME

          public static final java.lang.String ARROW_MARKER_NAME

      Arrow marker name.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ARROW_MARKER_HEIGHT

          public static final java.lang.Double ARROW_MARKER_HEIGHT

      Arrow marker height.

    <!-- -->

    - #### ARROW_MARKER_WIDTH

          public static final java.lang.Double ARROW_MARKER_WIDTH

      Arrow marker width.

    <!-- -->

    - #### ARROW_MARKER_POSITION

          public static final java.lang.Double ARROW_MARKER_POSITION

      Arrow marker position. (0 means at line start, 0.5 in the middle, 1 at line end)

  <!-- -->

  - ### Constructor Detail

    - #### NFEFeatureUtils

          public NFEFeatureUtils()

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayerType

          public static int getFeatureLayerType(FeatureLayerMetadata.FeatureLayerType featureLayerType)

      Returns the feature layer type identifier.
      Parameters:
      `featureLayerType` - feature layer type

      Returns:
      feature layer type identifier

    <!-- -->

    - #### getFeatureElementType

          public static int getFeatureElementType(FeatureElement.FeatureElementType type)

      Returns the feature element type identifier.
      Parameters:
      `type` - feature element type

      Returns:
      feature element type identifier

    <!-- -->

    - #### calculateFeatureElementGeometry

          public static JGeometry calculateFeatureElementGeometry(NFEFeatureElement featElem,
                                                                  JGeometry netElemGeom)

      Returns the feature element geometry considering the start and end percentage.
      Parameters:
      `featElem` - feature element

      `netElemGeom` - network element geometry

      Returns:
      feature element geometry

    <!-- -->

    - #### getArrowStyle

          public static StyleMarker getArrowStyle(NFELink nfeLink,
                                                  boolean isPath,
                                                  boolean isNetworkDirected)

      Returns the arrow marker style for the link.
      Parameters:
      `nfeLink` - link

      `isPath` - true if the link is a path, false otherwise

      `isNetworkDirected` - true if the network is directed, false otherwise.

      Returns:
      arrow marker style

    <!-- -->

    - #### getSimpleArrow

          public static StyleMarker getSimpleArrow()

      Returns the arrow marker style for an unidirectional arrow.
      Returns:
      arrow marker style for an unidirectional arrow

    <!-- -->

    - #### setSimpleArrow

          public static void setSimpleArrow(StyleMarker simpleArrow)

      Sets the arrow marker style for an unidirectional arrow.
      Parameters:
      `simpleArrow` - arrow marker style for an unidirectional arrow

    <!-- -->

    - #### getBiDirectionalArrow

          public static StyleMarker getBiDirectionalArrow()

      Returns the arrow marker style for a bidirectional arrow.
      Returns:
      arrow marker style for a bidirectional arrow

    <!-- -->

    - #### setBiDirectionalArrow

          public static void setBiDirectionalArrow(StyleMarker biDirectionalArrow)

      Sets the arrow marker style for a bidirectional arrow.
      Parameters:
      `biDirectionalArrow` - arrow marker style for a bidirectional arrow

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LongHashTable.md)
- [Next Class](NFEResources.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
