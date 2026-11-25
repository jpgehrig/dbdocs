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

- [Prev Class](FeatureDataImpl.md)
- [Next Class](FeatureElement.FeatureElementType.md)

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

## Interface FeatureElement

- All Superinterfaces:
  java.lang.Cloneable

  <!-- -->

  All Known Implementing Classes:
  [FeatureElementImpl](FeatureElementImpl.md)

  ------------------------------------------------------------------------



      public interface FeatureElement
      extends java.lang.Cloneable

  A feature element is a point or line defined on a network element. A network element is a node or link on a network. A feature element can be a point on a node, a point along a link, a link or partial link.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                             |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`FeatureElement.FeatureElementType`](FeatureElement.FeatureElementType.md)<br>A list of valid feature element types. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                 |
    |-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                          | `clone``()`<br>Support cloneable                                                       |
    | `double`                                                                    | `getEndPercentage``()`<br>Returns the end percentage of the feature element.           |
    | `long`                                                                      | `getLinkId``()`<br>Returns the ID of the link on which the feature element is defined. |
    | `long`                                                                      | `getNodeId``()`<br>Returns the ID of the node on which the feature element is defined. |
    | `double`                                                                    | `getStartPercentage``()`<br>Returns the start percentage of the feature element.       |
    | [`FeatureElement.FeatureElementType`](FeatureElement.FeatureElementType.md) | `getType``()`<br>Returns the type of the feature element.                              |

<!-- -->

- - ### Method Detail

    - #### getType

          FeatureElement.FeatureElementType getType()

      Returns the type of the feature element.
      Returns:

    <!-- -->

    - #### getLinkId

          long getLinkId()

      Returns the ID of the link on which the feature element is defined. This method is meaningless for feature elements of type POINT_ON_NODE.
      Returns:

    <!-- -->

    - #### getNodeId

          long getNodeId()

      Returns the ID of the node on which the feature element is defined. This method is only meaningful for feature elements of type POINT_ON_NODE.
      Returns:

    <!-- -->

    - #### getStartPercentage

          double getStartPercentage()

      Returns the start percentage of the feature element. For feature elements of type POINT_ON_NODE, the returned value is ignored; For feature elements of type POINT_ON_LINK, this method returns the percentage of the point along the link; For feature elements of type LINE, this method returns the start percentage of the line along the link.
      Returns:

    <!-- -->

    - #### getEndPercentage

          double getEndPercentage()

      Returns the end percentage of the feature element. For feature elements of type POINT_ON_NODE, the returned value is ignored; For feature elements of type POINT_ON_LINK, the returned value is ignored; For feature elements of type LINE, this method returns the end percentage of the line along the link.
      Returns:

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](FeatureDataImpl.md)
- [Next Class](FeatureElement.FeatureElementType.md)

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
