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

- [Prev Class](EuclideanCostFunction.md)
- [Next Class](Feature.FeatureType.md)

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

## Interface Feature

- All Known Subinterfaces:
  [PathFeature](PathFeature.md)

  <!-- -->

  All Known Implementing Classes:
  [FeatureImpl](FeatureImpl.md), [PathFeatureImpl](PathFeatureImpl.md)

  ------------------------------------------------------------------------



      public interface Feature

  This interface defines the methods supported by a network feature. A network feature is a collection of feature elements. A feature element can be a point on node, a point along a link, a link or partial link. Each feature element corresponds to a feature element index, starting from 0.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                         |
    |-------------------|-----------------------------------------------------------------------------------|
    | `static class `   | [`Feature.FeatureType`](Feature.FeatureType.md)<br>A list of valid feature types. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                                                      |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addElement``(int i, `[`FeatureElement`](FeatureElement.md)` element)`<br>Adds a feature element at the ith position of the feature.                        |
    | `void`                                          | `addElements``(`[`FeatureElement`](FeatureElement.md)`[] newElements)`<br>Appends a list of elements to the end of the feature.                             |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                            |
    | `void`                                          | `deleteElement``(int i)`<br>Deletes the ith element in the feature.                                                                                         |
    | `int`                                           | `findElement``(`[`FeatureElement`](FeatureElement.md)` element)`<br>Finds the input feature element in this feature, and returns the feature element index. |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                              |
    | [`FeatureElement`](FeatureElement.md)           | `getElement``(int i)`<br>Returns the ith element in the feature.                                                                                            |
    | [`FeatureElement`](FeatureElement.md)`[]`       | `getElements``()`<br>Returns the feature elements in the feature.                                                                                           |
    | `long`                                          | `getId``()`<br>Returns the feature ID.                                                                                                                      |
    | `int`                                           | `getNumberOfElements``()`<br>Returns the number of elements in the feature.                                                                                 |
    | [`Feature.FeatureType`](Feature.FeatureType.md) | `getType``()`<br>Returns the feature type.                                                                                                                  |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                              |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                       |
    | `void`                                          | `setElement``(int i, `[`FeatureElement`](FeatureElement.md)` element)`<br>Sets the ith feature element.                                                     |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                           |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Returns the feature ID.
      Returns:

    <!-- -->

    - #### getType

          Feature.FeatureType getType()

      Returns the feature type.
      Returns:

    <!-- -->

    - #### getElement

          FeatureElement getElement(int i)

      Returns the ith element in the feature.
      Parameters:

      `i` - feature element index

      Returns:

    <!-- -->

    - #### getElements

          FeatureElement[] getElements()

      Returns the feature elements in the feature.
      Returns:

    <!-- -->

    - #### getNumberOfElements

          int getNumberOfElements()

      Returns the number of elements in the feature.
      Returns:

    <!-- -->

    - #### addElement

          void addElement(int i,
                          FeatureElement element)

      Adds a feature element at the ith position of the feature.
      Parameters:
      `i` - feature element index

      `element` -

    <!-- -->

    - #### addElements

          void addElements(FeatureElement[] newElements)

      Appends a list of elements to the end of the feature.
      Parameters:
      `newElements` -

    <!-- -->

    - #### deleteElement

          void deleteElement(int i)

      Deletes the ith element in the feature.
      Parameters:
      `i` - feature element index

    <!-- -->

    - #### findElement

          int findElement(FeatureElement element)

      Finds the input feature element in this feature, and returns the feature element index. If the feature element is not found, returns 0.
      Parameters:

      `element` -

      Returns:

    <!-- -->

    - #### setElement

          void setElement(int i,
                          FeatureElement element)

      Sets the ith feature element.
      Parameters:
      `i` - feature element index

      `element` -

    <!-- -->

    - #### getCategorizedUserData

          CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          void setUserData(int category,
                           UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

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

- [Prev Class](EuclideanCostFunction.md)
- [Next Class](Feature.FeatureType.md)

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
