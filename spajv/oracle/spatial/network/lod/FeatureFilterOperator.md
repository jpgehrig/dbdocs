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

- [Prev Class](FeatureFilter.md)
- [Next Class](FeatureImpl.md)

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

## Class FeatureFilterOperator

- java.lang.Object

- - oracle.spatial.network.lod.FeatureFilterOperator

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureFilterOperator
      extends java.lang.Object

  Supports "and", "or", and "not" operations on feature filters.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `FeatureFilterOperator``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                        |
    |----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`FeatureFilter`](FeatureFilter.md) | `and``(`[`FeatureFilter`](FeatureFilter.md)`[] filters)`<br>Performs "and" operation on an array of feature filters, and returns the combined feature filter. |
    | `static `[`FeatureFilter`](FeatureFilter.md) | `not``(`[`FeatureFilter`](FeatureFilter.md)` filter)`<br>Performs "not" operation on the specified feature filter, and returns the opposite feature filter.   |
    | `static `[`FeatureFilter`](FeatureFilter.md) | `or``(`[`FeatureFilter`](FeatureFilter.md)`[] filters)`<br>Performs "or" operation on an array of feature filters, and returns the combined feature filter.   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureFilterOperator

          public FeatureFilterOperator()

  <!-- -->

  - ### Method Detail

    - #### and

          public static FeatureFilter and(FeatureFilter[] filters)

      Performs "and" operation on an array of feature filters, and returns the combined feature filter.

    <!-- -->

    - #### or

          public static FeatureFilter or(FeatureFilter[] filters)

      Performs "or" operation on an array of feature filters, and returns the combined feature filter.

    <!-- -->

    - #### not

          public static FeatureFilter not(FeatureFilter filter)

      Performs "not" operation on the specified feature filter, and returns the opposite feature filter.

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

- [Prev Class](FeatureFilter.md)
- [Next Class](FeatureImpl.md)

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
