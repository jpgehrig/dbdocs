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

- [Prev Class](XSPrincipalException.md)
- [Next Class](XSSessionException.md)

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

## Class XSSecurityPermission

- java.lang.Object

- - java.security.Permission

  - - java.security.BasicPermission

    - - oracle.security.xs.XSSecurityPermission

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.security.Guard

  ------------------------------------------------------------------------



      public class XSSecurityPermission
      extends java.security.BasicPermission

  This class represents a Java permission that extends the `BasicPermission` class to authorize the execution of critical XS methods in the oracle.security.xs package. Such permissions must be granted in the Java policy file if security manager is turned on. The followings provide a typical use of this in the Java policy file:

          grant codeBase "file:/lib/xs.jar" {
            permission oracle.security.xs.XSSecurityPermission "initSecurityManager" ;
            permission oracle.security.xs.XSSecurityPermission "setCacheMaxIdleTime" ;
            permission oracle.security.xs.XSSecurityPermission "setCacheMaxSize" ;
            permission oracle.security.xs.XSSecurityPermission "setWaterMark" ;
            permission oracle.security.xs.XSSecurityPermission "clearCache" ;
            permission oracle.security.xs.XSSecurityPermission "invalidateACL" ;
            permission oracle.security.xs.XSSecurityPermission "setPrivateCacheMaxEntries" ;
            permission oracle.security.xs.XSSecurityPermission "manageKeyManager" ;
          };


  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------|
    | `XSSecurityPermission``(java.lang.String name)`<br>Constructs a new XSSecurityPermission from the specified name. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.security.BasicPermission

      `equals, getActions, hashCode, implies, newPermissionCollection`

    <!-- -->

    - ### Methods inherited from class java.security.Permission

      `checkGuard, getName, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSSecurityPermission

          public XSSecurityPermission(java.lang.String name)

      Constructs a new XSSecurityPermission from the specified name.
      Parameters:
      `name` - string used to define the permission in the java class, such as `initSecurityManager`

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

- [Prev Class](XSPrincipalException.md)
- [Next Class](XSSessionException.md)

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
