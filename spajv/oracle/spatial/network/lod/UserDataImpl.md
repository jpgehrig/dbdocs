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

- [Prev Class](UserData.md)
- [Next Class](VisitedNode.md)

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

## Class UserDataImpl

- java.lang.Object

- - oracle.spatial.network.lod.UserDataImpl

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [UserData](UserData.md)

  ------------------------------------------------------------------------



      public class UserDataImpl
      extends java.lang.Object
      implements UserData, java.io.Serializable

  Default implementation of UserData.
  Since:
  Oracle Database 11g Release 2 (11.2)

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                    |
    |------------------------------------------------|
    | `UserDataImpl``(java.lang.Object[] userData)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                |
    |--------------------|-------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `clone``()`<br>Returns the cloned object.                                                             |
    | `java.lang.Object` | `get``(int index)`<br>Returns the user data at the specified index.                                   |
    | `int`              | `getNumberOfUserData``()`<br>Returns the total number of user data contained in this UserData object. |
    | `void`             | `set``(int index, java.lang.Object userData)`<br>Sets the user data at the specified index.           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UserDataImpl

          public UserDataImpl(java.lang.Object[] userData)

  <!-- -->

  - ### Method Detail

    - #### get

          public java.lang.Object get(int index)

      Description copied from interface: [`UserData`](UserData.md)
      Returns the user data at the specified index.
      Specified by:

      [`get`](UserData.md) in interface [`UserData`](UserData.md)

      Returns:

    <!-- -->

    - #### set

          public void set(int index,
                          java.lang.Object userData)

      Description copied from interface: [`UserData`](UserData.md)
      Sets the user data at the specified index.
      Specified by:
      [`set`](UserData.md) in interface [`UserData`](UserData.md)

    <!-- -->

    - #### getNumberOfUserData

          public int getNumberOfUserData()

      Description copied from interface: [`UserData`](UserData.md)
      Returns the total number of user data contained in this UserData object.
      Specified by:

      [`getNumberOfUserData`](UserData.md) in interface [`UserData`](UserData.md)

      Returns:

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Description copied from interface: [`UserData`](UserData.md)
      Returns the cloned object.
      Specified by:

      [`clone`](UserData.md) in interface [`UserData`](UserData.md)

      Overrides:

      `clone` in class `java.lang.Object`

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

- [Prev Class](UserData.md)
- [Next Class](VisitedNode.md)

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
