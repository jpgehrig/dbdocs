Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Tree.md)
- [Next Class](TreeNode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Interface TreeLink

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface TreeLink
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines a tree link for trace-out. Note the tree links can either regular links or partial links (defined by a start and an end percentages)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                  |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------|
    | `double`                                | `getCost``()`<br>Returns the link cost                                                                  |
    | `double`                                | `getDuration``()`<br>Returns the sum of duration from root node to this node                            |
    | `double`                                | `getEndPercentage``()`<br>Returns the end percentage of the link if the tree link is a partial link     |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`<br>Returns the geometry of the tree link                                              |
    | [`Link`](Link.md)                       | `getLink``()`<br>Returns the link.                                                                      |
    | `double`                                | `getStartPercentage``()`<br>Returns the start percentage of the link if the tree link is a partial link |
    | `boolean`                               | `isPartialLink``()`<br>If the tree link is a partial link?                                              |
    | `boolean`                               | `isRegularLink``()`<br>if the tree link is a regular link                                               |

<!-- -->

- - ### Method Detail

    - #### isPartialLink

          boolean isPartialLink()

      If the tree link is a partial link?

    <!-- -->

    - #### isRegularLink

          boolean isRegularLink()

      if the tree link is a regular link

    <!-- -->

    - #### getLink

          Link getLink()

      Returns the link.

    <!-- -->

    - #### getStartPercentage

          double getStartPercentage()

      Returns the start percentage of the link if the tree link is a partial link

    <!-- -->

    - #### getEndPercentage

          double getEndPercentage()

      Returns the end percentage of the link if the tree link is a partial link

    <!-- -->

    - #### getCost

          double getCost()

      Returns the link cost

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry of the tree link

    <!-- -->

    - #### getDuration

          double getDuration()

      Returns the sum of duration from root node to this node
      Returns:
      sum of duration

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Tree.md)
- [Next Class](TreeNode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
