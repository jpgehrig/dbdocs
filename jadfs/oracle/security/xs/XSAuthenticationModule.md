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

- [Prev Class](XSAccessController.md)
- [Next Class](XSException.md)

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

## Class XSAuthenticationModule

- java.lang.Object

- - oracle.security.xs.XSAuthenticationModule

<!-- -->

-

  ------------------------------------------------------------------------



      public class XSAuthenticationModule
      extends java.lang.Object

  This class provides authentication functions to verify the user credentials against the Database.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `XSAuthenticationModule``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                   |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `static boolean`  | `authenticate``(java.lang.String url, java.lang.String user, java.lang.String password)`<br>Authenticates the user against the Database. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSAuthenticationModule

          public XSAuthenticationModule()

  <!-- -->

  - ### Method Detail

    - #### authenticate

          public static boolean authenticate(java.lang.String url,
                                             java.lang.String user,
                                             java.lang.String password)
                                      throws java.sql.SQLException,
                                             XSException

      Authenticates the user against the Database.
      Parameters:
      `url` - database url

      `user` - user ID

      `password` - password

      Returns:
      true if success, false if fail

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`XSException`](XSException.md) - a generic error is detected

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

- [Prev Class](XSAccessController.md)
- [Next Class](XSException.md)

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
