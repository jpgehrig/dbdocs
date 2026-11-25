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

- [Prev Class](CategorizedUserData.md)
- [Next Class](Cluster.md)

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

## Class CategorizedUserDataImpl

- java.lang.Object

- - oracle.spatial.network.lod.CategorizedUserDataImpl

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [CategorizedUserData](CategorizedUserData.md)

  ------------------------------------------------------------------------



      public class CategorizedUserDataImpl
      extends java.lang.Object
      implements CategorizedUserData, java.io.Serializable

  Default implementation for CategorizedUserData.
  Since:
  Oracle Database 11g Release 2 (11.2)

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                          |
    |----------------------------------------------------------------------|
    | `CategorizedUserDataImpl``(int numUserDataCategories)`               |
    | `CategorizedUserDataImpl``(`[`UserData`](UserData.md)`[] userData)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`        | `clone``()`<br>Supports cloneable                                                                                     |
    | `int`                     | `getNumberOfCategories``()`<br>Returns the number of user data categories.                                            |
    | [`UserData`](UserData.md) | `getUserData``(int category)`<br>Returns the user data for the specified category.                                    |
    | `void`                    | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets the user data for the specified category. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CategorizedUserDataImpl

          public CategorizedUserDataImpl(int numUserDataCategories)

    <!-- -->

    - #### CategorizedUserDataImpl

          public CategorizedUserDataImpl(UserData[] userData)

  <!-- -->

  - ### Method Detail

    - #### getNumberOfCategories

          public int getNumberOfCategories()

      Description copied from interface: [`CategorizedUserData`](CategorizedUserData.md)
      Returns the number of user data categories.
      Specified by:

      [`getNumberOfCategories`](CategorizedUserData.md) in interface [`CategorizedUserData`](CategorizedUserData.md)

      Returns:

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Description copied from interface: [`CategorizedUserData`](CategorizedUserData.md)
      Supports cloneable
      Specified by:
      [`clone`](CategorizedUserData.md) in interface [`CategorizedUserData`](CategorizedUserData.md)

      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### getUserData

          public UserData getUserData(int category)

      Description copied from interface: [`CategorizedUserData`](CategorizedUserData.md)
      Returns the user data for the specified category.
      Specified by:

      [`getUserData`](CategorizedUserData.md) in interface [`CategorizedUserData`](CategorizedUserData.md)

      Parameters:

      `category` - category ID

      Returns:

    <!-- -->

    - #### setUserData

          public void setUserData(int category,
                                  UserData userData)

      Description copied from interface: [`CategorizedUserData`](CategorizedUserData.md)
      Sets the user data for the specified category.
      Specified by:
      [`setUserData`](CategorizedUserData.md) in interface [`CategorizedUserData`](CategorizedUserData.md)

      Parameters:
      `category` - category ID

      `userData` - user data

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

- [Prev Class](CategorizedUserData.md)
- [Next Class](Cluster.md)

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
