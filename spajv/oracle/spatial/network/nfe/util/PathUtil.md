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

- [Prev Class](NFEUtil.md)
- [Next Class](SpatialUtils.md)

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

## Class PathUtil

- java.lang.Object

- - oracle.spatial.network.nfe.util.PathUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class PathUtil
      extends java.lang.Object

  Provides static methods related to the NFE paths.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `PathUtil``()`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                            |
    |-----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.util.Map<java.lang.String,java.lang.String>` | `getPathColors``()`<br>Returns the possible path colors and the XML style representation.                                                         |
    | `static boolean`                                          | `isFeaturePath``(`[`NFEFeature`](../model/feature/NFEFeature.md)` nfeFeature)`<br>Returns true if the feature is a path, false otherwise.         |
    | `static void`                                             | `setPathColors``(java.util.Map<java.lang.String,java.lang.String> pathColors)`<br>Sets the possible path colors and the XML style representation. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PathUtil

          public PathUtil()

  <!-- -->

  - ### Method Detail

    - #### getPathColors

          public static java.util.Map<java.lang.String,java.lang.String> getPathColors()

      Returns the possible path colors and the XML style representation. By default: PATH_COLOR_BLUE, PATH_COLOR_RED, PATH_COLOR_GREEN and PATH_COLOR_ORANGE.
      Returns:
      path colors

    <!-- -->

    - #### setPathColors

          public static void setPathColors(java.util.Map<java.lang.String,java.lang.String> pathColors)

      Sets the possible path colors and the XML style representation. By default: PATH_COLOR_BLUE, PATH_COLOR_RED, PATH_COLOR_GREEN and PATH_COLOR_ORANGE.
      Parameters:
      `pathColors` - path colors

    <!-- -->

    - #### isFeaturePath

          public static boolean isFeaturePath(NFEFeature nfeFeature)

      Returns true if the feature is a path, false otherwise.
      Parameters:
      `nfeFeature` - feature

      Returns:
      true if the feature is a path, false otherwise

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

- [Prev Class](NFEUtil.md)
- [Next Class](SpatialUtils.md)

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
