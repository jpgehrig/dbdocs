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

- [Prev Class](Principal.md)
- [Next Class](Session.md)

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

## Class Role

- java.lang.Object

- - [oracle.security.xs.Principal](Principal.md)

  - - oracle.security.xs.Role

<!-- -->

- All Implemented Interfaces:
  java.security.Principal

  ------------------------------------------------------------------------



      public class Role
      extends Principal

  This class represents a type of principal that can be associated with a group of users.
  See Also:
  [`Principal`](Principal.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------|
    | `Role``()`<br>Constructs a `Role` object.                                                                                            |
    | `Role``(java.lang.String name, long dbid)`<br>Constructs an `Role` object from a name and a `DBID`.                                  |
    | `Role``(java.lang.String name, java.lang.String uuid)`<br>Constructs an `Role` object from a name and a `UUID`.                      |
    | `Role``(java.lang.String name, java.lang.String uuid, long dbid)`<br>Constructs an `Role` object from a name, a `UUID` and a `DBID`. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.security.xs.[Principal](Principal.md)

      [`getDBID`](Principal.md)`, `[`getName`](Principal.md)`, `[`getUUID`](Principal.md)`, `[`toString`](Principal.md)`, `[`validate`](Principal.md)`, `[`verify`](Principal.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.security.Principal

      `equals, hashCode, implies`

<!-- -->

- - ### Constructor Detail

    - #### Role

          public Role()

      Constructs a `Role` object.

    <!-- -->

    - #### Role

          public Role(java.lang.String name,
                      java.lang.String uuid,
                      long dbid)
               throws XSPrincipalException

      Constructs an `Role` object from a name, a `UUID` and a `DBID`.
      Parameters:
      `name` - name of the `Role` object

      `uuid` - `UUID` of the `Role` object

      `dbid` - `DBID` of the `Role` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### Role

          public Role(java.lang.String name,
                      java.lang.String uuid)
               throws XSPrincipalException

      Constructs an `Role` object from a name and a `UUID`.
      Parameters:
      `name` - name of the `Role`

      `uuid` - `UUID` of the `Role`

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### Role

          public Role(java.lang.String name,
                      long dbid)
               throws XSPrincipalException

      Constructs an `Role` object from a name and a `DBID`.
      Parameters:
      `name` - name of the `Role`

      `uuid` - `UUID` of the `Role`

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

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

- [Prev Class](Principal.md)
- [Next Class](Session.md)

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
