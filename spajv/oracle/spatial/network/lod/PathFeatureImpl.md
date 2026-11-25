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

- [Prev Class](PathFeature.md)
- [Next Class](PathFilter.md)

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

## Class PathFeatureImpl

- java.lang.Object

- - [oracle.spatial.network.lod.FeatureImpl](FeatureImpl.md)

  - - oracle.spatial.network.lod.PathFeatureImpl

<!-- -->

- All Implemented Interfaces:
  [Feature](Feature.md), [PathFeature](PathFeature.md)

  ------------------------------------------------------------------------



      public class PathFeatureImpl
      extends FeatureImpl
      implements PathFeature

  Default implementation of PathFeature.
  Since:
  12.1

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[Feature](Feature.md)

      [`Feature.FeatureType`](Feature.FeatureType.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `PathFeatureImpl``(long id, `[`FeatureElement`](FeatureElement.md)`[] elements, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Constructs a PathFeature instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                      |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | `double[]`                                      | `getCosts``()`<br>Returns the path costs.                                                                             |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | `boolean`                                       | `isReverse``()`<br>Whether the path is a reverse path.                                                                |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data. |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.      |
    | `double[]`                                      | `setCosts``(double[] costs)`<br>Sets the path costs.                                                                  |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |
    | `java.lang.String`                              | `toString``()`                                                                                                        |

    - ### Methods inherited from class oracle.spatial.network.lod.[FeatureImpl](FeatureImpl.md)

      [`addElement`](FeatureImpl.md)`, `[`addElements`](FeatureImpl.md)`, `[`deleteElement`](FeatureImpl.md)`, `[`equals`](FeatureImpl.md)`, `[`findElement`](FeatureImpl.md)`, `[`getElement`](FeatureImpl.md)`, `[`getElements`](FeatureImpl.md)`, `[`getId`](FeatureImpl.md)`, `[`getNumberOfElements`](FeatureImpl.md)`, `[`getType`](FeatureImpl.md)`, `[`setElement`](FeatureImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[Feature](Feature.md)

      [`addElement`](Feature.md)`, `[`addElements`](Feature.md)`, `[`deleteElement`](Feature.md)`, `[`findElement`](Feature.md)`, `[`getElement`](Feature.md)`, `[`getElements`](Feature.md)`, `[`getId`](Feature.md)`, `[`getNumberOfElements`](Feature.md)`, `[`getType`](Feature.md)`, `[`setElement`](Feature.md)

<!-- -->

- - ### Constructor Detail

    - #### PathFeatureImpl

          public PathFeatureImpl(long id,
                                 FeatureElement[] elements,
                                 double[] costs,
                                 CategorizedUserData userData,
                                 boolean isReverse)

      Constructs a PathFeature instance.
      Parameters:
      `id` -

      `elements` -

      `costs` -

      `userData` -

  <!-- -->

  - ### Method Detail

    - #### getCosts

          public double[] getCosts()

      Returns the path costs.
      Specified by:

      [`getCosts`](PathFeature.md) in interface [`PathFeature`](PathFeature.md)

      Returns:

    <!-- -->

    - #### setCosts

          public double[] setCosts(double[] costs)

      Sets the path costs.
      Parameters:

      `costs` -

      Returns:

    <!-- -->

    - #### isReverse

          public boolean isReverse()

      Description copied from interface: [`PathFeature`](PathFeature.md)
      Whether the path is a reverse path. A reverse path is usually generated by a backward search.
      Specified by:

      [`isReverse`](PathFeature.md) in interface [`PathFeature`](PathFeature.md)

      Returns:

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Overrides:
      [`clone`](FeatureImpl.md) in class [`FeatureImpl`](FeatureImpl.md)

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      [`toString`](FeatureImpl.md) in class [`FeatureImpl`](FeatureImpl.md)

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

- [Prev Class](PathFeature.md)
- [Next Class](PathFilter.md)

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
