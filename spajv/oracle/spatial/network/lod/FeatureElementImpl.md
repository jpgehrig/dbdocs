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

- [Prev Class](FeatureElement.FeatureElementType.md)
- [Next Class](FeatureFilter.md)

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

## Class FeatureElementImpl

- java.lang.Object

- - oracle.spatial.network.lod.FeatureElementImpl

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [FeatureElement](FeatureElement.md)

  ------------------------------------------------------------------------



      public class FeatureElementImpl
      extends java.lang.Object
      implements FeatureElement

  Default implementation of FeatureElement.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[FeatureElement](FeatureElement.md)

      [`FeatureElement.FeatureElementType`](FeatureElement.FeatureElementType.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureElementImpl``(long nodeId)`<br>Constructs a POINT_ON_NODE type feature element.                                      |
    | `FeatureElementImpl``(long linkId, double percentage)`<br>Constructs a POINT_ON_LINK type feature element.                   |
    | `FeatureElementImpl``(long linkId, double startPercentage, double endPercentage)`<br>Constructs a LINE type feature element. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                           | Method and Description                                                                 |
    |-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                          | `clone``()`<br>Support cloneable                                                       |
    | `boolean`                                                                   | `equals``(java.lang.Object o)`                                                         |
    | `double`                                                                    | `getEndPercentage``()`<br>Returns the end percentage of the feature element.           |
    | `long`                                                                      | `getLinkId``()`<br>Returns the ID of the link on which the feature element is defined. |
    | `long`                                                                      | `getNodeId``()`<br>Returns the ID of the node on which the feature element is defined. |
    | `double`                                                                    | `getPercentage``()`                                                                    |
    | `double`                                                                    | `getStartPercentage``()`<br>Returns the start percentage of the feature element.       |
    | [`FeatureElement.FeatureElementType`](FeatureElement.FeatureElementType.md) | `getType``()`<br>Returns the type of the feature element.                              |
    | `java.lang.String`                                                          | `toString``()`                                                                         |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureElementImpl

          public FeatureElementImpl(long linkId,
                                    double percentage)

      Constructs a POINT_ON_LINK type feature element.
      Parameters:
      `linkId` - ID of the link

      `percentage` - percentage of the point along the link

    <!-- -->

    - #### FeatureElementImpl

          public FeatureElementImpl(long linkId,
                                    double startPercentage,
                                    double endPercentage)

      Constructs a LINE type feature element.
      Parameters:
      `linkId` - ID of the link

      `startPercentage` - start percentage of the line along the link

      `endPercentage` - end percentage of the line along the link

    <!-- -->

    - #### FeatureElementImpl

          public FeatureElementImpl(long nodeId)

      Constructs a POINT_ON_NODE type feature element.
      Parameters:
      `nodeId` - ID of the node.

  <!-- -->

  - ### Method Detail

    - #### getType

          public FeatureElement.FeatureElementType getType()

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Returns the type of the feature element.
      Specified by:

      [`getType`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Returns:

    <!-- -->

    - #### getLinkId

          public long getLinkId()

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Returns the ID of the link on which the feature element is defined. This method is meaningless for feature elements of type POINT_ON_NODE.
      Specified by:

      [`getLinkId`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Returns:

    <!-- -->

    - #### getNodeId

          public long getNodeId()

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Returns the ID of the node on which the feature element is defined. This method is only meaningful for feature elements of type POINT_ON_NODE.
      Specified by:

      [`getNodeId`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Returns:

    <!-- -->

    - #### getStartPercentage

          public double getStartPercentage()

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Returns the start percentage of the feature element. For feature elements of type POINT_ON_NODE, the returned value is ignored; For feature elements of type POINT_ON_LINK, this method returns the percentage of the point along the link; For feature elements of type LINE, this method returns the start percentage of the line along the link.
      Specified by:

      [`getStartPercentage`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Returns:

    <!-- -->

    - #### getEndPercentage

          public double getEndPercentage()

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Returns the end percentage of the feature element. For feature elements of type POINT_ON_NODE, the returned value is ignored; For feature elements of type POINT_ON_LINK, the returned value is ignored; For feature elements of type LINE, this method returns the end percentage of the line along the link.
      Specified by:

      [`getEndPercentage`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Returns:

    <!-- -->

    - #### getPercentage

          public double getPercentage()

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Description copied from interface: [`FeatureElement`](FeatureElement.md)
      Support cloneable
      Specified by:
      [`clone`](FeatureElement.md) in interface [`FeatureElement`](FeatureElement.md)

      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Overrides:
      `equals` in class `java.lang.Object`

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

- [Prev Class](FeatureElement.FeatureElementType.md)
- [Next Class](FeatureFilter.md)

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
