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

- [Prev Class](ExternalRole.md)
- [Next Class](InvalidSessionException.md)

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

## Class ExternalUser

- java.lang.Object

- - [oracle.security.xs.Principal](Principal.md)

  - - [oracle.security.xs.User](User.md)

    - - oracle.security.xs.ExternalUser

<!-- -->

- All Implemented Interfaces:
  java.security.Principal

  ------------------------------------------------------------------------



      public class ExternalUser
      extends User

  This class represents externally managed users used in a session.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ExternalUser``(java.lang.String uuid)`<br>Constructs an `ExternalUser` object from a name                                                           |
    | `ExternalUser``(java.lang.String name, java.lang.String uuid)`<br>Constructs an `ExternalUser` object from a name and a `UUID`                       |
    | `ExternalUser``(java.lang.String name, java.lang.String uuid, long dbid)`<br>Constructs an `ExternalUser` object from a name, a `UUID` and a `DBID`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                           |
    |-------------------|------------------------------------------------------------------|
    | `boolean`         | `isAnonymous``()`<br>Indicates if the current user is anonymous. |

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

    - #### ExternalUser

          public ExternalUser(java.lang.String name,
                              java.lang.String uuid,
                              long dbid)
                       throws XSPrincipalException

      Constructs an `ExternalUser` object from a name, a `UUID` and a `DBID`.
      Parameters:
      `name` - name of the `ExternalUser` object

      `uuid` - `UUID` of the `ExternalUser` object

      `dbid` - `DBID` of the `ExternalUser` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### ExternalUser

          public ExternalUser(java.lang.String name,
                              java.lang.String uuid)
                       throws XSPrincipalException

      Constructs an `ExternalUser` object from a name and a `UUID`
      Parameters:
      `name` - name of the `ExternalUser` object

      `uuid` - `UUID` of the `ExternalUser` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### ExternalUser

          public ExternalUser(java.lang.String uuid)
                       throws XSPrincipalException

      Constructs an `ExternalUser` object from a name
      Parameters:
      `name` - name of the `ExternalUser` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

  <!-- -->

  - ### Method Detail

    - #### isAnonymous

          public boolean isAnonymous()

      Indicates if the current user is anonymous.

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

- [Prev Class](ExternalRole.md)
- [Next Class](InvalidSessionException.md)

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
