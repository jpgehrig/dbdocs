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

- [Prev Class](SessionNamespaceException.md)
- [Next Class](XSAccessController.md)

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

## Class User

- java.lang.Object

- - [oracle.security.xs.Principal](Principal.md)

  - - oracle.security.xs.User

<!-- -->

- All Implemented Interfaces:
  java.security.Principal

  <!-- -->

  Direct Known Subclasses:
  [ExternalUser](ExternalUser.md)

  ------------------------------------------------------------------------



      public class User
      extends Principal

  This class represents a user, which is a type of principal.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------|
    | `User``()`<br>Constructs a `User` object.                                                                                               |
    | `User``(java.lang.String name)`<br>Constructs a `User` object with the specified name.                                                  |
    | `User``(java.lang.String name, java.lang.String uuid)`<br>Constructs a `User` object with the specified name and UUID.                  |
    | `User``(java.lang.String name, java.lang.String uuid, long dbid)`<br>Constructs a `User` object with the specified name, UUID and DBID. |

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

    - #### User

          public User()

      Constructs a `User` object.

    <!-- -->

    - #### User

          public User(java.lang.String name)

      Constructs a `User` object with the specified name.
      Parameters:
      `name` - name of the `User`

    <!-- -->

    - #### User

          public User(java.lang.String name,
                      java.lang.String uuid,
                      long dbid)
               throws XSPrincipalException

      Constructs a `User` object with the specified name, UUID and DBID.
      Parameters:
      `name` - name of the `User`

      `uuid` - UUID of the `User`

      `dbid` - DBID of the `User`

      Throws:
      [`XSPrincipalException`](XSPrincipalException.md) - a problem occured while creating the principal

    <!-- -->

    - #### User

          public User(java.lang.String name,
                      java.lang.String uuid)
               throws XSPrincipalException

      Constructs a `User` object with the specified name and UUID.
      Parameters:
      `name` - name of the `User`

      `uuid` - UUID of the `User`

      Throws:
      [`XSPrincipalException`](XSPrincipalException.md) - a problem occured while creating the principal

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

- [Prev Class](SessionNamespaceException.md)
- [Next Class](XSAccessController.md)

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
