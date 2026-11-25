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

- [Prev Class](User.md)
- [Next Class](XSAuthenticationModule.md)

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

## Class XSAccessController

- java.lang.Object

- - oracle.security.xs.XSAccessController

<!-- -->

-

  ------------------------------------------------------------------------



      public class XSAccessController
      extends java.lang.Object

  This class provides authorization functions to check the privilege on the ACL based on the session.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XSAccessController``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                  |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static boolean`                                | `checkAcl``(`[`Session`](Session.md)` session, `[`AclId`](AclId.md)` acls, java.util.List<java.lang.String> privileges)`<br>Checks for mutiple privileges.                                              |
    | `static boolean`                                | `checkAcl``(`[`Session`](Session.md)` session, `[`AclId`](AclId.md)` acls, java.lang.String privilege)`<br>Checks for a privilege.                                                                      |
    | `static boolean`                                | `checkAcl``(`[`Session`](Session.md)` session, byte[] acls, java.util.List<java.lang.String> privileges)`<br>Checks for multiple privileges.                                                            |
    | `static boolean`                                | `checkAcl``(`[`Session`](Session.md)` session, byte[] acls, java.lang.String privilege)`<br>Checks for a privilege.                                                                                     |
    | `static java.util.Collection<java.lang.String>` | `getPrivileges``(`[`Session`](Session.md)` session, `[`AclId`](AclId.md)` aclId)`<br>Returns a collection of privileges, which is granted in the specified ACL (AclId), based on the specified session. |
    | `static java.util.Collection<java.lang.String>` | `getPrivileges``(`[`Session`](Session.md)` session, byte[] aclId)`<br>Returns a collection of privileges, which is granted in the specified ACL (byte\[\]), based on the specified session.             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSAccessController

          public XSAccessController()

  <!-- -->

  - ### Method Detail

    - #### checkAcl

          public static boolean checkAcl(Session session,
                                         AclId acls,
                                         java.util.List<java.lang.String> privileges)
                                  throws java.sql.SQLException,
                                         XSException,
                                         NotAttachedException

      Checks for mutiple privileges. The privilege is checked against one or multiple ACLs defined in the `AclId` object. This function returns true only when all the privileges are granted in the specified ACLs. It is important to note that all privileges need not be granted in a single ACL.
      Parameters:
      `session` - Session

      `acls` - ACLs

      `privileges` - a list of privilege names

      Returns:
      true if the privilege is grant in all ACLs; otherwise false.

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### checkAcl

          public static boolean checkAcl(Session session,
                                         AclId acls,
                                         java.lang.String privilege)
                                  throws java.sql.SQLException,
                                         XSException,
                                         NotAttachedException

      Checks for a privilege. The privilege is checked against one or multiple ACLs defined in the `AclId` object
      Parameters:
      `session` - Session

      `acls` - ACLs

      `privilege` - the name of the privilege as `String`

      Returns:
      true if the privilege is granted in one of the gieven ACLs; otherwise false.

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### checkAcl

          public static boolean checkAcl(Session session,
                                         byte[] acls,
                                         java.util.List<java.lang.String> privileges)
                                  throws java.sql.SQLException,
                                         XSException,
                                         NotAttachedException

      Checks for multiple privileges. The ACL is given in raw (byte\[\]) format retrived from query, which internally may have one or many ACLs. This function returns true only when all the privileges are granted in the specified ACLs. It is important to note that all privileges need not be granted in a single ACL.
      Parameters:
      `session` - Session

      `acls` - ACLs in raw format

      `privileges` - list of privilege names

      Returns:
      true if all privileges are granted in the ACLs; otherwise false.

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - the session is not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### checkAcl

          public static boolean checkAcl(Session session,
                                         byte[] acls,
                                         java.lang.String privilege)
                                  throws java.sql.SQLException,
                                         XSException,
                                         NotAttachedException

      Checks for a privilege. The privilege is checked against one or multiple ACLs in raw (byte\[\]) format retrived from query.
      Parameters:
      `session` - Session

      `acls` - ACLs in raw format

      `privilege` - the name of the privilege as `String`

      Returns:
      true if the privilege is granted in one of the gieven ACLs; otherwise false.

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - the session is not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### getPrivileges

          public static java.util.Collection<java.lang.String> getPrivileges(Session session,
                                                                             AclId aclId)
                                                                      throws java.sql.SQLException,
                                                                             XSException,
                                                                             NotAttachedException

      Returns a collection of privileges, which is granted in the specified ACL (AclId), based on the specified session.
      Parameters:
      `session` - Session

      `aclId` - AclId

      Returns:
      collection of privilege names in String

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### getPrivileges

          public static java.util.Collection<java.lang.String> getPrivileges(Session session,
                                                                             byte[] aclId)
                                                                      throws java.sql.SQLException,
                                                                             XSException,
                                                                             NotAttachedException

      Returns a collection of privileges, which is granted in the specified ACL (byte\[\]), based on the specified session.
      Parameters:
      `session` - Session

      `aclId` - byte\[\]

      Returns:
      collection of privilege names in String

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`NotAttachedException`](NotAttachedException.md) - session not attached

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

- [Prev Class](User.md)
- [Next Class](XSAuthenticationModule.md)

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
