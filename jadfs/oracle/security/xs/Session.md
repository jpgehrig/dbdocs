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

- [Prev Class](Role.md)
- [Next Class](SessionNamespace.md)

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

## Interface Session

-

  ------------------------------------------------------------------------



      public interface Session

  This interface represents an application security context that encapsulates user, role, and namespace.
  The session is created at database, and attached to a JDBC connection to enforce data security. The session state (user, role, and namespace) can be changed after attach. The changes take effect immediately on the current JDBC connection (database session), and are committed to database upon detach from the connection.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                 |
    |---------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`SessionNamespace`](SessionNamespace.md)   | `createNamespace``(java.lang.String name)`<br>Creates a new namespace for this session.                                                                                                                |
    | `void`                                      | `deleteNamespace``(java.lang.String namespace)`<br>Removes a namespace from a session.                                                                                                                 |
    | `void`                                      | `disableRole``(`[`Role`](Role.md)` role)`<br>Disables a role granted to the current user for this session.                                                                                             |
    | `void`                                      | `enableRole``(`[`Role`](Role.md)` role)`<br>Enables a role granted to the current user for this session.                                                                                               |
    | `java.sql.Connection`                       | `getConnection``()`<br>Returns the Oracle JDBC `Connection` attached with this session.                                                                                                                |
    | `java.lang.String`                          | `getCookie``()`<br>Returns the secure session cookie used for this session.                                                                                                                            |
    | `java.util.Collection<`[`Role`](Role.md)`>` | `getEnabledRoles``()`<br>Returns a collection of all currently enabled roles.                                                                                                                          |
    | `java.lang.String`                          | `getId``()`<br>Returns the internal session ID generated at server for this session.                                                                                                                   |
    | [`SessionNamespace`](SessionNamespace.md)   | `getNamespace``(java.lang.String name)`<br>Returns the specified namespace in the session.                                                                                                             |
    | `java.lang.String`                          | `getUser``()`<br>Returns current session's user                                                                                                                                                        |
    | `boolean`                                   | `isAnonymous``()`<br>Determines if this session user is anonymous.                                                                                                                                     |
    | `boolean`                                   | `isAttached``()`<br>Determines if this session is attached to a `Connection`.                                                                                                                          |
    | `boolean`                                   | `isRoleEnabled``(java.lang.String roleName)`<br>Tests if the specified role is enabled in this user's session.                                                                                         |
    | `boolean`                                   | `isTrusted``()`<br>Determins if the current session is in trusted mode.                                                                                                                                |
    | `void`                                      | `switchUser``(java.lang.String targetUser, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Changes the session user.                                                |
    | `void`                                      | `switchUserKeepState``(java.lang.String targetUser, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Changes the session user and retains session state (Namespace). |
    | `java.lang.String`                          | `toString``()`                                                                                                                                                                                         |

<!-- -->

- - ### Method Detail

    - #### switchUser

          void switchUser(java.lang.String targetUser,
                          java.util.Collection<NamespaceValue> namespaceValues)
                   throws java.sql.SQLException,
                          AccessDeniedException,
                          InvalidSessionException,
                          InvalidXSUserException,
                          XSException,
                          NotAttachedException,
                          InvalidXSNamespaceException

      Changes the session user. By default, it does not retain the session state, which means that all the existing namespaces in the session are dropped and newly specified namespaces are created. The attribute values inside NamespaceValue are set or created.
      Parameters:
      `targetUser` - a `User` object initialized based on authentication

      `namespaceValues` - a list of `NamespaceValue` objects to be created and changed.

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to switch to the target user.

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSUserException`](InvalidXSUserException.md) - XS user specified is invalid

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - when an invalid namespace specified

    <!-- -->

    - #### switchUserKeepState

          void switchUserKeepState(java.lang.String targetUser,
                                   java.util.Collection<NamespaceValue> namespaceValues)
                            throws java.sql.SQLException,
                                   AccessDeniedException,
                                   InvalidSessionException,
                                   InvalidXSUserException,
                                   XSException,
                                   NotAttachedException,
                                   InvalidXSNamespaceException

      Changes the session user and retains session state (Namespace). If the given namespaces do not exist in the current session, then they are created. The attributes value inside `NamespaceValue` will be set/created.
      Parameters:
      `targetUser` - a `User` object initialized based on authentication

      `namespaceValues` - a list of `NamespaceValue` objects to be created and changed.

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to switch to the target user.

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSUserException`](InvalidXSUserException.md) - XS user specified is invalid

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - when an invalid namespace specified

    <!-- -->

    - #### getEnabledRoles

          java.util.Collection<Role> getEnabledRoles()

      Returns a collection of all currently enabled roles. No database roundtrip is required.

    <!-- -->

    - #### isRoleEnabled

          boolean isRoleEnabled(java.lang.String roleName)
                         throws XSException,
                                NotAttachedException

      Tests if the specified role is enabled in this user's session. No database roundtrip is required.
      Parameters:
      `roleName` - name of role to enable

      Returns:
      boolean true if role is enabled or else false

      Throws:
      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - generic error is detected

    <!-- -->

    - #### getCookie

          java.lang.String getCookie()

      Returns the secure session cookie used for this session.
      Returns:
      The cookie

    <!-- -->

    - #### getId

          java.lang.String getId()

      Returns the internal session ID generated at server for this session.
      Returns:
      The Session ID

    <!-- -->

    - #### isAttached

          boolean isAttached()

      Determines if this session is attached to a `Connection`.
      Returns:
      Boolean indicating whether the session is attached

    <!-- -->

    - #### isAnonymous

          boolean isAnonymous()

      Determines if this session user is anonymous.
      Returns:
      Boolean indicating whether the session user is anonymous

    <!-- -->

    - #### getConnection

          java.sql.Connection getConnection()

      Returns the Oracle JDBC `Connection` attached with this session.
      Returns:
      The JDBC `Connection`

    <!-- -->

    - #### enableRole

          void enableRole(Role role)
                   throws AccessDeniedException,
                          java.sql.SQLException,
                          XSException,
                          InvalidSessionException,
                          NotAttachedException

      Enables a role granted to the current user for this session. This method has no effect if the role is currently enabled. This operation requires a database roundtrip.
      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to enable this role

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### disableRole

          void disableRole(Role role)
                    throws AccessDeniedException,
                           java.sql.SQLException,
                           XSException,
                           InvalidSessionException,
                           NotAttachedException

      Disables a role granted to the current user for this session. This operation requires a database roundtrip.
      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to disable this role

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### createNamespace

          SessionNamespace createNamespace(java.lang.String name)
                                    throws java.sql.SQLException,
                                           AccessDeniedException,
                                           XSException,
                                           InvalidXSNamespaceException,
                                           InvalidSessionException,
                                           NotAttachedException

      Creates a new namespace for this session. The createNamespace method creates a new session namespace using the namespace template document, whose name matches with the specified name. If an event handler is defined in the template document, then the defined event handler applies to all the namespaces created using that template.
      Parameters:
      `name` - the name of the session namespace. The user should have "bindNamespace" privilege on the namespace template documents corersponding to the name.

      Returns:
      `SessionNamespace` that is created

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - user does not have the privilege to create the namespace

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - namespace already exists

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### getNamespace

          SessionNamespace getNamespace(java.lang.String name)
                                 throws java.sql.SQLException,
                                        AccessDeniedException,
                                        XSException,
                                        InvalidSessionException,
                                        InvalidXSNamespaceException,
                                        NotAttachedException

      Returns the specified namespace in the session.
      Parameters:
      `name` - the namespace to get

      Returns:
      object corresponding to the namespace name

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to get namespace

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - namespace already exists

      [`InvalidSessionException`](InvalidSessionException.md) - attempt to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### deleteNamespace

          void deleteNamespace(java.lang.String namespace)
                        throws java.sql.SQLException,
                               AccessDeniedException,
                               XSException,
                               InvalidXSNamespaceException,
                               InvalidSessionException,
                               NotAttachedException

      Removes a namespace from a session.
      Parameters:
      `namespace` - the namespace object to be removed

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to delete this namespace

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - namespace is invalid

      [`InvalidSessionException`](InvalidSessionException.md) - attempted to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### isTrusted

          boolean isTrusted()

      Determins if the current session is in trusted mode.
      Returns:
      true if it is trusted; otherwise false.

    <!-- -->

    - #### getUser

          java.lang.String getUser()

      Returns current session's user

    <!-- -->

    - #### toString

          java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](Role.md)
- [Next Class](SessionNamespace.md)

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
