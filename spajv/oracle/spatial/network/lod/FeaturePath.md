Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureMetadata.md)
- [Next Class](FilePairwisePathResultIO.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class FeaturePath

- java.lang.Object

- - oracle.spatial.network.lod.FeaturePath

<!-- -->

- All Implemented Interfaces:
  java.lang.Comparable\<FeaturePath\>

  ------------------------------------------------------------------------



      public class FeaturePath
      extends java.lang.Object
      implements java.lang.Comparable<FeaturePath>

  A FeaturePath object consists of a Feature and the PathFeature that ends at the feature. It is used in analysis results.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------------------------|
    | `FeaturePath``(`[`Feature`](Feature.md)` feature, `[`PathFeature`](PathFeature.md)` path)`<br>Constructs a FeaturePath object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                             |
    |---------------------------------|------------------------------------------------------------------------------------|
    | `int`                           | `compareTo``(FeaturePath o)`<br>Compares the cost of the path.                     |
    | [`Feature`](Feature.md)         | `getFeature``()`<br>Returns the feature of interest.                               |
    | [`PathFeature`](PathFeature.md) | `getPath``()`<br>Returns the path feature.                                         |
    | `void`                          | `setFeature``(`[`Feature`](Feature.md)` feature)`<br>Sets the feature of interest. |
    | `void`                          | `setPath``(`[`PathFeature`](PathFeature.md)` path)`<br>Sets the path feature.      |
    | `java.lang.String`              | `toString``()`                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeaturePath

          public FeaturePath(Feature feature,
                             PathFeature path)

      Constructs a FeaturePath object.
      Parameters:
      `feature` - feature of interest

      `path` - path that ends at the feature of interest

  <!-- -->

  - ### Method Detail

    - #### compareTo

          public int compareTo(FeaturePath o)

      Compares the cost of the path.
      Specified by:

      `compareTo` in interface `java.lang.Comparable<FeaturePath>`

      Parameters:

      `o` -

      Returns:

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### setFeature

          public void setFeature(Feature feature)

      Sets the feature of interest.
      Parameters:
      `feature` -

    <!-- -->

    - #### getFeature

          public Feature getFeature()

      Returns the feature of interest.
      Returns:

    <!-- -->

    - #### setPath

          public void setPath(PathFeature path)

      Sets the path feature.
      Parameters:
      `path` -

    <!-- -->

    - #### getPath

          public PathFeature getPath()

      Returns the path feature.
      Returns:

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureMetadata.md)
- [Next Class](FilePairwisePathResultIO.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
