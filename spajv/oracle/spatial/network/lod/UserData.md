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

- [Prev Class](TspTimeWindowConstraint.md)
- [Next Class](UserDataImpl.md)

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

## Interface UserData

- All Superinterfaces:
  java.io.Serializable

  <!-- -->

  All Known Implementing Classes:
  [UserDataImpl](UserDataImpl.md)

  ------------------------------------------------------------------------



      public interface UserData
      extends java.io.Serializable

  This interface defines methods supported by a user data set. A UserData contains an array of user data objects, each with a unique index. The indexes of these objects start at 0.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                |
    |--------------------|-------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `clone``()`<br>Returns the cloned object.                                                             |
    | `java.lang.Object` | `get``(int index)`<br>Returns the user data at the specified index.                                   |
    | `int`              | `getNumberOfUserData``()`<br>Returns the total number of user data contained in this UserData object. |
    | `void`             | `set``(int index, java.lang.Object userData)`<br>Sets the user data at the specified index.           |

<!-- -->

- - ### Method Detail

    - #### get

          java.lang.Object get(int index)

      Returns the user data at the specified index.
      Parameters:

      `index` -

      Returns:

    <!-- -->

    - #### set

          void set(int index,
                   java.lang.Object userData)

      Sets the user data at the specified index.
      Parameters:
      `index` -

      `userData` -

    <!-- -->

    - #### getNumberOfUserData

          int getNumberOfUserData()

      Returns the total number of user data contained in this UserData object.
      Returns:

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Returns the cloned object.
      Returns:
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

- [Prev Class](TspTimeWindowConstraint.md)
- [Next Class](UserDataImpl.md)

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
