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

- [Prev Class](AttributeValue.md)
- [Next Class](ExternalUser.md)

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

## Class ExternalRole

- java.lang.Object

- - [oracle.security.xs.Principal](Principal.md)

  - - oracle.security.xs.ExternalRole

<!-- -->

- All Implemented Interfaces:
  java.security.Principal

  ------------------------------------------------------------------------



      public class ExternalRole
      extends Principal

  This class represents externally managed roles used in a session.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ExternalRole``(java.lang.String uuid)`<br>Constructs an `ExternalRole` object from a `UUID`                                                          |
    | `ExternalRole``(java.lang.String name, java.lang.String uuid)`<br>Constructs an `ExternalRole` object from a name and a `UUID`                        |
    | `ExternalRole``(java.lang.String name, java.lang.String uuid, long dbid)`<br>Constructs an `ExternalRole` object from a name, a `UUID`, and a `DBID`. |

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

    - #### ExternalRole

          public ExternalRole(java.lang.String name,
                              java.lang.String uuid,
                              long dbid)
                       throws XSPrincipalException

      Constructs an `ExternalRole` object from a name, a `UUID`, and a `DBID`.
      Parameters:
      `name` - name of the `ExternalRole` object

      `uuid` - `UUID` of the `ExternalRole` object

      `dbid` - `DBID` of the `ExternalRole` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### ExternalRole

          public ExternalRole(java.lang.String name,
                              java.lang.String uuid)
                       throws XSPrincipalException

      Constructs an `ExternalRole` object from a name and a `UUID`
      Parameters:
      `name` - name of the `ExternalRole` object

      `uuid` - `UUID` of the `ExternalRole` object

      Throws:
      `XSPrincipalException,` - if passed parameters not vaild

      [`XSPrincipalException`](XSPrincipalException.md)

    <!-- -->

    - #### ExternalRole

          public ExternalRole(java.lang.String uuid)
                       throws XSPrincipalException

      Constructs an `ExternalRole` object from a `UUID`
      Parameters:
      `uuid` - `UUID` of the `ExternalRole` object

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

- [Prev Class](AttributeValue.md)
- [Next Class](ExternalUser.md)

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
