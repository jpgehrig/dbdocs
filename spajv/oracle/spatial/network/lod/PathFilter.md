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

- [Prev Class](PathFeatureImpl.md)
- [Next Class](PathToPoint.md)

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

## Interface PathFilter

-

  ------------------------------------------------------------------------



      public interface PathFilter

  This interface defines the methods to check whether a given sub-path is a goal sub-path during network analysis.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                        |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                     |
    | `boolean`         | `isValid``(`[`LogicalSubPath`](LogicalSubPath.md)` subPath)`<br>Returns true if the given sub-path is valid, false otherwise. |

<!-- -->

- - ### Method Detail

    - #### isValid

          boolean isValid(LogicalSubPath subPath)

      Returns true if the given sub-path is valid, false otherwise.
      Parameters:
      `subPath` - the provided sub-path

      Returns:
      true if the provided sub-path is a goal feature, false otherwise.

    <!-- -->

    - #### getUserDataCategories

          int[] getUserDataCategories()

      Returns the required user data categories.
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

- [Prev Class](PathFeatureImpl.md)
- [Next Class](PathToPoint.md)

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
