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

- [Prev Class](FeatureElementImpl.md)
- [Next Class](FeatureFilterOperator.md)

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

## Interface FeatureFilter

-

  ------------------------------------------------------------------------



      public interface FeatureFilter

  This interface defines the methods to check whether a given feature is a goal feature during network analysis.
  Since:
  12.1

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                               |
    | `boolean`         | `isValid``(`[`Feature`](Feature.md)` feature)`<br>Returns true if the given feature is a goal feature, false otherwise. |

<!-- -->

- - ### Method Detail

    - #### isValid

          boolean isValid(Feature feature)

      Returns true if the given feature is a goal feature, false otherwise.
      Parameters:
      `feature` - the given feature

      Returns:
      true if the given feature is a goal feature, false otherwise.

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

- [Prev Class](FeatureElementImpl.md)
- [Next Class](FeatureFilterOperator.md)

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
