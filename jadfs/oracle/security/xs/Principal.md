Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](NotAttachedException.md)
- [Next Class](Role.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.security.xs

## Class Principal

- java.lang.Object

- - oracle.security.xs.Principal

<!-- -->

- All Implemented Interfaces:
  java.security.Principal

  <!-- -->

  Direct Known Subclasses:
  [ExternalRole](ExternalRole.md), [Role](Role.md), [User](User.md)

  ------------------------------------------------------------------------



      public class Principal
      extends java.lang.Object
      implements java.security.Principal

  This class represents a `Principal` entity, such as a `Role` or a `User`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                   |
    |-----------------------------------------------------------------------------------------------|
    | `Principal``()`<br>Constructs a new `Principal`.                                              |
    | `Principal``(java.lang.String name)`<br>Constructs a new `Principal` with the specified name. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                   |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `long`             | `getDBID``()`<br>Retrieves the `DBID` of the `Principal`.                                                                |
    | `java.lang.String` | `getName``()`<br>Retrieves the name of the Principal.                                                                    |
    | `java.lang.String` | `getUUID``()`<br>Retrieves the `UUID` of the `Principal`.                                                                |
    | `java.lang.String` | `toString``()`<br>Returns a string representation of the `Principal`.                                                    |
    | `boolean`          | `validate``()`<br>Tests whether the object is valid or not.                                                              |
    | `boolean`          | `verify``(java.lang.String name, java.lang.String uuid, long dbid)`<br>Tests whether the object is the same as specified |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.security.Principal

      `equals, hashCode, implies`

<!-- -->

- - ### Constructor Detail

    - #### Principal

          public Principal()

      Constructs a new `Principal`.

    <!-- -->

    - #### Principal

          public Principal(java.lang.String name)

      Constructs a new `Principal` with the specified name.
      Parameters:
      `name` - name of the `Principal` object

  <!-- -->

  - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Retrieves the name of the Principal.
      Specified by:
      `getName` in interface `java.security.Principal`

      Returns:
      `Principal` name

    <!-- -->

    - #### getUUID

          public java.lang.String getUUID()

      Retrieves the `UUID` of the `Principal`.
      Returns:
      the `UUID` of the `Principal`

    <!-- -->

    - #### getDBID

          public long getDBID()

      Retrieves the `DBID` of the `Principal`.
      Returns:
      the `DBID` of the `Principal`

    <!-- -->

    - #### validate

          public boolean validate()

      Tests whether the object is valid or not.
      Returns:
      true if valid

    <!-- -->

    - #### verify

          public boolean verify(java.lang.String name,
                                java.lang.String uuid,
                                long dbid)

      Tests whether the object is the same as specified
      Parameters:
      `name` - name of the `Principal` object

      `uuid` - UUID of the `Principal` object

      `dbid` - DBID of the `Principal` object

      Returns:
      true if same

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Returns a string representation of the `Principal`.
      Specified by:
      `toString` in interface `java.security.Principal`

      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      a string representation of the `Principal`

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](NotAttachedException.md)
- [Next Class](Role.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
