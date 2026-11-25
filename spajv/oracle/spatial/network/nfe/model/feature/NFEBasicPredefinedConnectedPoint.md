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

- [Prev Class](NFEBasicFeatureLayer.md)
- [Next Class](NFECatalog.md)

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

## Class NFEBasicPredefinedConnectedPoint

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEBasicPredefinedConnectedPoint

<!-- -->

- All Implemented Interfaces:
  [NFEPredefinedConnectedPoint](NFEPredefinedConnectedPoint.md)

  ------------------------------------------------------------------------



      public class NFEBasicPredefinedConnectedPoint
      extends java.lang.Object
      implements NFEPredefinedConnectedPoint

  The default implementation of [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description             |
    |-----------------------------------------|
    | `NFEBasicPredefinedConnectedPoint``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                   |
    |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md) | `createCopy``()`<br>Returns object copy.                                                                                                                 |
    | `long`                                                          | `getId``()`<br>Gets the descriptor ID                                                                                                                    |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                         | `getLineFeatureClass``()`<br>Gets the descriptor's owner line feature class                                                                              |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                         | `getPointFeatureClass``()`<br>Gets the feature class of the default connected point described                                                            |
    | `double`                                                        | `getPosition``()`<br>Gets the position where the default connected point must be placed over a line.                                                     |
    | `void`                                                          | `setId``(long id)`<br>Sets the descriptor ID                                                                                                             |
    | `void`                                                          | `setLineFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` lineFeatureClass)`<br>Sets the descriptor's owner line feature class                    |
    | `void`                                                          | `setPointFeatureClass``(`[`NFEFeatureClass`](NFEFeatureClass.md)` pointFeatureClass)`<br>Sets the feature class of the default connected point described |
    | `void`                                                          | `setPosition``(double position)`<br>Sets the position where the default connected point must be placed over a line.                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicPredefinedConnectedPoint

          public NFEBasicPredefinedConnectedPoint()

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Gets the descriptor ID
      Specified by:
      [`getId`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Returns:
      the descriptor ID

    <!-- -->

    - #### setId

          public void setId(long id)

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Sets the descriptor ID
      Specified by:
      [`setId`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Parameters:
      `id` - the descriptor ID

    <!-- -->

    - #### getLineFeatureClass

          public NFEFeatureClass getLineFeatureClass()

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Gets the descriptor's owner line feature class
      Specified by:
      [`getLineFeatureClass`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Returns:
      a line feature class instance

    <!-- -->

    - #### setLineFeatureClass

          public void setLineFeatureClass(NFEFeatureClass lineFeatureClass)

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Sets the descriptor's owner line feature class
      Specified by:
      [`setLineFeatureClass`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Parameters:
      `lineFeatureClass` - a line feature class instance

    <!-- -->

    - #### getPointFeatureClass

          public NFEFeatureClass getPointFeatureClass()

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Gets the feature class of the default connected point described
      Specified by:
      [`getPointFeatureClass`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Returns:
      a point feature class instance

    <!-- -->

    - #### setPointFeatureClass

          public void setPointFeatureClass(NFEFeatureClass pointFeatureClass)

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Sets the feature class of the default connected point described
      Specified by:
      [`setPointFeatureClass`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Parameters:
      `pointFeatureClass` - a point feature class instance

    <!-- -->

    - #### getPosition

          public double getPosition()

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Gets the position where the default connected point must be placed over a line.
      Specified by:
      [`getPosition`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Returns:
      a value between 0 an 1, relative to a line's length

    <!-- -->

    - #### setPosition

          public void setPosition(double position)

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Sets the position where the default connected point must be placed over a line.
      Specified by:
      [`setPosition`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

      Parameters:
      `position` - a value between 0 an 1, relative to a line's length

    <!-- -->

    - #### createCopy

          public NFEPredefinedConnectedPoint createCopy()

      Description copied from interface: [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEPredefinedConnectedPoint.md) in interface [`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)

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

- [Prev Class](NFEBasicFeatureLayer.md)
- [Next Class](NFECatalog.md)

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
