Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- [Prev Class](ApplicationSessionException.md)
- [Next Class](NamespaceNotFoundException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.security.xs.ee.session

## Class ApplicationSessionService

- java.lang.Object

- - oracle.security.xs.ee.session.ApplicationSessionService

<!-- -->

-

  ------------------------------------------------------------------------



      public final class ApplicationSessionService
      extends java.lang.Object

  Exposed RAS Session Service APIs.
  Session service internally sets up session transparently. This API is exposed for application to use the session. It must work together with session setup layer. (servlet filter)

  The methods can be grouped as:

            - Attach/detach/destroy session
            - Namespace operation
            - Privilege check


  The following code snippet provides a typical use of this class:

            try {
                ApplicationSessionService.attachSession(conn);
                stmt = conn.createStatement();
                rs = stmt.executeQuery(query);
            } finally {
                ApplicationSessionService.detachSession(conn);
            }



<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description      |
    |----------------------------------|
    | `ApplicationSessionService``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                              |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`             | `attachSession``(java.sql.Connection conn)`<br>Attaches the current user's application session to the given connection.                                                                                             |
    | `static void`             | `attachSessionPrivileged``(java.sql.Connection conn, java.lang.String role)`<br>Attaches the current user's application session to the given connection, and enable the given dynamic role in the attached session. |
    | `static boolean`          | `checkPrivilege``(java.sql.Connection conn, byte[] acls, java.lang.String privilege)`<br>Checks the privielge on the attached session.                                                                              |
    | `static void`             | `createNamespace``(java.sql.Connection conn, java.lang.String name)`<br>Creates the namespace on the current user's application session.                                                                            |
    | `static void`             | `deleteNamespace``(java.sql.Connection conn, java.lang.String name)`<br>Deletes the namespace on the current user's application session.                                                                            |
    | `static void`             | `deleteNamespaceAttribute``(java.sql.Connection conn, java.lang.String name, java.lang.String attribute)`<br>Deletes the namespace attribute on the current user's application session.                             |
    | `static void`             | `destroySession``(java.sql.Connection conn)`<br>Destroys the current user's application session.                                                                                                                    |
    | `static void`             | `detachSession``(java.sql.Connection conn)`<br>Detaches the current user's application session from the given connection.                                                                                           |
    | `static java.lang.String` | `getNamespaceAttribute``(java.lang.String name, java.lang.String attribute)`<br>Gets the namespace attribute from the current user's application session.                                                           |
    | `static void`             | `setNamespaceAttribute``(java.sql.Connection conn, java.lang.String name, java.lang.String attribute, java.lang.String value)`<br>Sets the namespace attribute on the current user's application session.           |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ApplicationSessionService

          public ApplicationSessionService()

  <!-- -->

  - ### Method Detail

    - #### attachSession

          public static void attachSession(java.sql.Connection conn)
                                    throws ApplicationSessionException

      Attaches the current user's application session to the given connection.
      Parameters:
      `conn` - the given JDBC connection

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens during attach

    <!-- -->

    - #### detachSession

          public static void detachSession(java.sql.Connection conn)
                                    throws ApplicationSessionException

      Detaches the current user's application session from the given connection.
      Parameters:
      `conn` - the given JDBC connection

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens during detach

    <!-- -->

    - #### attachSessionPrivileged

          public static void attachSessionPrivileged(java.sql.Connection conn,
                                                     java.lang.String role)
                                              throws ApplicationSessionException

      Attaches the current user's application session to the given connection, and enable the given dynamic role in the attached session. The role must be defined as "request scope". The caller code should have `SessionCodePermission` granted.
      Parameters:
      `conn` - the given JDBC connection

      `role` - the given dynamic role, must be request-scope

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### destroySession

          public static void destroySession(java.sql.Connection conn)
                                     throws ApplicationSessionException

      Destroys the current user's application session.
      Parameters:
      `conn` - the given JDBC connection

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### createNamespace

          public static void createNamespace(java.sql.Connection conn,
                                             java.lang.String name)
                                      throws ApplicationSessionException

      Creates the namespace on the current user's application session. The connection must be attached, and the namespace's template must be already created at database. The "modify_namespace" privilege must be enabled in the attached session for the given namespace, unless "ADMIN_ANY_NAMESPACE" privilege is enabled in the session.
      Parameters:
      `conn` - the given JDBC connection

      `name` - the given namespace name

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### deleteNamespace

          public static void deleteNamespace(java.sql.Connection conn,
                                             java.lang.String name)
                                      throws NamespaceNotFoundException,
                                             ApplicationSessionException

      Deletes the namespace on the current user's application session. The connection must be attached, and the namespace must be already created in the session. The "modify_namespace" privilege must be enabled in the attached session for the given namespace, unless "ADMIN_ANY_NAMESPACE" privilege is enabled in the session.
      Parameters:
      `conn` - the given JDBC connection

      `name` - the given namespace name

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

      [`NamespaceNotFoundException`](NamespaceNotFoundException.md)

    <!-- -->

    - #### setNamespaceAttribute

          public static void setNamespaceAttribute(java.sql.Connection conn,
                                                   java.lang.String name,
                                                   java.lang.String attribute,
                                                   java.lang.String value)
                                            throws NamespaceNotFoundException,
                                                   ApplicationSessionException

      Sets the namespace attribute on the current user's application session.The connection must be attached, and the namespace must be already created on the session. If the attribute is not existing, this API automatically creates it.The "modify_namespace" privilege must be enabled in the attached session for the given namespace, unless "ADMIN_ANY_NAMESPACE" privilege is enabled in the session.
      Parameters:
      `conn` - the given JDBC connection

      `name` - the given namespace name

      `attribute` - the given namespace attribute name

      `value` - the given namespace attribute value

      Throws:
      [`NamespaceNotFoundException`](NamespaceNotFoundException.md) - if the namespace is not existing

      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### deleteNamespaceAttribute

          public static void deleteNamespaceAttribute(java.sql.Connection conn,
                                                      java.lang.String name,
                                                      java.lang.String attribute)
                                               throws NamespaceNotFoundException,
                                                      ApplicationSessionException

      Deletes the namespace attribute on the current user's application session. The connection must be attached, the namespace must be already created on the session, and the attribute must be existed in the namespace.The "modify_namespace" privilege must be enabled in the attached session for the given namespace, unless "ADMIN_ANY_NAMESPACE" privilege is enabled in the session.
      Parameters:
      `conn` - the given JDBC connection

      `name` - the given namespace name

      `attribute` - the given namespace attribute name

      Throws:
      [`NamespaceNotFoundException`](NamespaceNotFoundException.md) - if the namespace is not existing

      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### getNamespaceAttribute

          public static java.lang.String getNamespaceAttribute(java.lang.String name,
                                                               java.lang.String attribute)
                                                        throws NamespaceNotFoundException,
                                                               ApplicationSessionException

      Gets the namespace attribute from the current user's application session.
      Parameters:
      `name` - the given namespace name

      `attribute` - the given namespace attribute name

      Throws:
      [`NamespaceNotFoundException`](NamespaceNotFoundException.md) - if the namespace is not existing

      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

    <!-- -->

    - #### checkPrivilege

          public static boolean checkPrivilege(java.sql.Connection conn,
                                               byte[] acls,
                                               java.lang.String privilege)
                                        throws ApplicationSessionException

      Checks the privielge on the attached session. The connection must be attached. The acls are the encoded ACL IDs in row format queried from database using ORA_GET_ACLIDS.
      Parameters:
      `conn` - the given JDBC connection

      `acls` - the given ACL IDs in row format

      `privilege` - the given privilege name

      Throws:
      [`ApplicationSessionException`](ApplicationSessionException.md) - if an error happens

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- [Prev Class](ApplicationSessionException.md)
- [Next Class](NamespaceNotFoundException.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
