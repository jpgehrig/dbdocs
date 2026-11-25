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

- [Prev Class](NFEFeatureShape.md)
- Next Class

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

## Interface NFEPredefinedConnectedPoint

- All Known Implementing Classes:
  [NFEBasicPredefinedConnectedPoint](NFEBasicPredefinedConnectedPoint.md)

  ------------------------------------------------------------------------



      public interface NFEPredefinedConnectedPoint

  Describes the type of point and how it should be connected to a line when a line is created.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                   |
    |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEPredefinedConnectedPoint`           | `createCopy``()`<br>Returns object copy.                                                                                                                 |
    | `long`                                  | `getId``()`<br>Gets the descriptor ID                                                                                                                    |
    | [`NFEFeatureClass`](NFEFeatureClass.md) | `getLineFeatureClass``()`<br>Gets the descriptor's owner line feature class                                                                              |
    | [`NFEFeatureClass`](NFEFeatureClass.md) | `getPointFeatureClass``()`<br>Gets the feature class of the default connected point described                                                            |
    | `double`                                | `getPosition``()`<br>Gets the position where the default connected point must be placed over a line.                                                     |
    | `void`                                  | `setId``(long id)`<br>Sets the descriptor ID                                                                                                             |
    | `void`                                  | `setLineFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` lineFeatureClass)`<br>Sets the descriptor's owner line feature class                    |
    | `void`                                  | `setPointFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` pointFeatureClass)`<br>Sets the feature class of the default connected point described |
    | `void`                                  | `setPosition``(double position)`<br>Sets the position where the default connected point must be placed over a line.                                      |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Gets the descriptor ID
      Returns:
      the descriptor ID

    <!-- -->

    - #### setId

          void setId(long id)

      Sets the descriptor ID
      Parameters:
      `id` - the descriptor ID

    <!-- -->

    - #### getLineFeatureClass

          NFEFeatureClass getLineFeatureClass()

      Gets the descriptor's owner line feature class
      Returns:
      a line feature class instance

    <!-- -->

    - #### setLineFeatureClass

          void setLineFeatureClass(NFEFeatureClass lineFeatureClass)

      Sets the descriptor's owner line feature class
      Parameters:
      `lineFeatureClass` - a line feature class instance

    <!-- -->

    - #### getPointFeatureClass

          NFEFeatureClass getPointFeatureClass()

      Gets the feature class of the default connected point described
      Returns:
      a point feature class instance

    <!-- -->

    - #### setPointFeatureClass

          void setPointFeatureClass(NFEFeatureClass pointFeatureClass)

      Sets the feature class of the default connected point described
      Parameters:
      `pointFeatureClass` - a point feature class instance

    <!-- -->

    - #### getPosition

          double getPosition()

      Gets the position where the default connected point must be placed over a line.
      Returns:
      a value between 0 an 1, relative to a line's length

    <!-- -->

    - #### setPosition

          void setPosition(double position)

      Sets the position where the default connected point must be placed over a line.
      Parameters:
      `position` - a value between 0 an 1, relative to a line's length

    <!-- -->

    - #### createCopy

          NFEPredefinedConnectedPoint createCopy()

      Returns object copy.
      Returns:
      object copy

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

- [Prev Class](NFEFeatureShape.md)
- Next Class

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
