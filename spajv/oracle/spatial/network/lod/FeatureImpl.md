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

- [Prev Class](FeatureFilterOperator.md)
- [Next Class](FeatureLayer.md)

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

## Class FeatureImpl

- java.lang.Object

- - oracle.spatial.network.lod.FeatureImpl

<!-- -->

- All Implemented Interfaces:
  [Feature](Feature.md)

  <!-- -->

  Direct Known Subclasses:
  [PathFeatureImpl](PathFeatureImpl.md)

  ------------------------------------------------------------------------



      public class FeatureImpl
      extends java.lang.Object
      implements Feature

  Default implementation of Feature.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[Feature](Feature.md)

      [`Feature.FeatureType`](Feature.FeatureType.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                  |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureImpl``(long id, `[`FeatureElement`](FeatureElement.md)`[] elements, `[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Constructs a feature. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                      |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addElement``(int i, `[`FeatureElement`](FeatureElement.md)` element)`<br>Adds a feature element at the ith position of the feature.                        |
    | `void`                                          | `addElements``(`[`FeatureElement`](FeatureElement.md)`[] newElements)`<br>Appends a list of elements to the end of the feature.                             |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                            |
    | `void`                                          | `deleteElement``(int i)`<br>Deletes the ith element in the feature.                                                                                         |
    | `boolean`                                       | `equals``(java.lang.Object o)`<br>Returns true if the input feature consists of the same set of feature elements in the same order as this feature.         |
    | `int`                                           | `findElement``(`[`FeatureElement`](FeatureElement.md)` element)`<br>Finds the input feature element in this feature, and returns the feature element index. |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                              |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                              |
    | [`FeatureElement`](FeatureElement.md)           | `getElement``(int i)`<br>Returns the ith element in the feature.                                                                                            |
    | [`FeatureElement`](FeatureElement.md)`[]`       | `getElements``()`<br>Returns the feature elements in the feature.                                                                                           |
    | `long`                                          | `getId``()`<br>Returns the feature ID.                                                                                                                      |
    | `int`                                           | `getNumberOfElements``()`<br>Returns the number of elements in the feature.                                                                                 |
    | [`Feature.FeatureType`](Feature.FeatureType.md) | `getType``()`<br>Returns the feature type.                                                                                                                  |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                              |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                              |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                       |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.                                            |
    | `void`                                          | `setElement``(int i, `[`FeatureElement`](FeatureElement.md)` element)`<br>Sets the ith feature element.                                                     |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                           |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                           |
    | `java.lang.String`                              | `toString``()`                                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureImpl

          public FeatureImpl(long id,
                             FeatureElement[] elements,
                             CategorizedUserData cud)

      Constructs a feature.
      Parameters:
      `id` - feature ID

      `type` - feature type

      `elements` - feature elements

      `cud` - categorized user data associated with the feature

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Description copied from interface: [`Feature`](Feature.md)
      Returns the feature ID.
      Specified by:

      [`getId`](Feature.md) in interface [`Feature`](Feature.md)

      Returns:

    <!-- -->

    - #### getType

          public Feature.FeatureType getType()

      Description copied from interface: [`Feature`](Feature.md)
      Returns the feature type.
      Specified by:

      [`getType`](Feature.md) in interface [`Feature`](Feature.md)

      Returns:

    <!-- -->

    - #### getElement

          public FeatureElement getElement(int i)

      Description copied from interface: [`Feature`](Feature.md)
      Returns the ith element in the feature.
      Specified by:

      [`getElement`](Feature.md) in interface [`Feature`](Feature.md)

      Parameters:

      `i` - feature element index

      Returns:

    <!-- -->

    - #### getElements

          public FeatureElement[] getElements()

      Description copied from interface: [`Feature`](Feature.md)
      Returns the feature elements in the feature.
      Specified by:

      [`getElements`](Feature.md) in interface [`Feature`](Feature.md)

      Returns:

    <!-- -->

    - #### getNumberOfElements

          public int getNumberOfElements()

      Description copied from interface: [`Feature`](Feature.md)
      Returns the number of elements in the feature.
      Specified by:

      [`getNumberOfElements`](Feature.md) in interface [`Feature`](Feature.md)

      Returns:

    <!-- -->

    - #### addElement

          public void addElement(int i,
                                 FeatureElement element)

      Description copied from interface: [`Feature`](Feature.md)
      Adds a feature element at the ith position of the feature.
      Specified by:
      [`addElement`](Feature.md) in interface [`Feature`](Feature.md)

      Parameters:
      `i` - feature element index

    <!-- -->

    - #### addElements

          public void addElements(FeatureElement[] newElements)

      Description copied from interface: [`Feature`](Feature.md)
      Appends a list of elements to the end of the feature.
      Specified by:
      [`addElements`](Feature.md) in interface [`Feature`](Feature.md)

    <!-- -->

    - #### deleteElement

          public void deleteElement(int i)

      Description copied from interface: [`Feature`](Feature.md)
      Deletes the ith element in the feature.
      Specified by:
      [`deleteElement`](Feature.md) in interface [`Feature`](Feature.md)

      Parameters:
      `i` - feature element index

    <!-- -->

    - #### findElement

          public int findElement(FeatureElement element)

      Description copied from interface: [`Feature`](Feature.md)
      Finds the input feature element in this feature, and returns the feature element index. If the feature element is not found, returns 0.
      Specified by:

      [`findElement`](Feature.md) in interface [`Feature`](Feature.md)

      Returns:

    <!-- -->

    - #### setElement

          public void setElement(int i,
                                 FeatureElement element)

      Description copied from interface: [`Feature`](Feature.md)
      Sets the ith feature element.
      Specified by:
      [`setElement`](Feature.md) in interface [`Feature`](Feature.md)

      Parameters:
      `i` - feature element index

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Returns true if the input feature consists of the same set of feature elements in the same order as this feature. When comparing two features, we assume the order of the feature elements matters. This method returns false if the input feature contains the same set of feature elements but in different order.
      Overrides:

      `equals` in class `java.lang.Object`

      Parameters:

      `o` -

      Returns:

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getCategorizedUserData

          public CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          public void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          public UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          public void setUserData(int category,
                                  UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

    <!-- -->

    - #### getCategorizedUserData

          public CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          public void setCategorizedUserData(CategorizedUserData cud)

      Sets categorized user data.

    <!-- -->

    - #### getUserData

          public UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          public void setUserData(int category,
                                  UserData userData)

      Sets user data for the specified category.

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

- [Prev Class](FeatureFilterOperator.md)
- [Next Class](FeatureLayer.md)

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
