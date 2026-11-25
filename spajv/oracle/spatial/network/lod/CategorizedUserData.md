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

- [Prev Class](CachingHandler.md)
- [Next Class](CategorizedUserDataImpl.md)

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

## Interface CategorizedUserData

- All Superinterfaces:
  java.io.Serializable

  <!-- -->

  All Known Implementing Classes:
  [CategorizedUserDataImpl](CategorizedUserDataImpl.md)

  ------------------------------------------------------------------------



      public interface CategorizedUserData
      extends java.io.Serializable

  This interface defines methods supported by a categorized user data object. A categorized user data contains a collection of user data categories. Each category of user data can be accessed by its category ID.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                                                                                  |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`        | `clone``()`<br>Supports cloneable                                                                                       |
    | `int`                     | `getNumberOfCategories``()`<br>Returns the number of user data categories.                                              |
    | [`UserData`](UserData.md) | `getUserData``(int categoryId)`<br>Returns the user data for the specified category.                                    |
    | `void`                    | `setUserData``(int categoryId, `[`UserData`](UserData.md)` userData)`<br>Sets the user data for the specified category. |

<!-- -->

- - ### Method Detail

    - #### getUserData

          UserData getUserData(int categoryId)

      Returns the user data for the specified category.
      Parameters:

      `categoryId` - category ID

      Returns:

    <!-- -->

    - #### setUserData

          void setUserData(int categoryId,
                           UserData userData)

      Sets the user data for the specified category.
      Parameters:
      `categoryId` - category ID

      `userData` - user data

    <!-- -->

    - #### getNumberOfCategories

          int getNumberOfCategories()

      Returns the number of user data categories.
      Returns:

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Supports cloneable
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

- [Prev Class](CachingHandler.md)
- [Next Class](CategorizedUserDataImpl.md)

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
