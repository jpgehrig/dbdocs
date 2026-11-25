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

- [Prev Class](XSSessionException.md)
- [Next Class](XSSessionManagerException.md)

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

## Class XSSessionManager

- java.lang.Object

- - oracle.security.xs.XSSessionManager

<!-- -->

-

  ------------------------------------------------------------------------



      public abstract class XSSessionManager
      extends java.lang.Object

  This class provides functions to manage the `Session`, inlcude session life cycle (createSession, attachSession, detachSessiona and destroySession), session attribute (cookie, inactivity timeout) and session namespace. It also provides functions to initialize the middle-tier cache and manage it. The following code snippet provides a typical use of this class:

        XSSessionManager manager = XSSessionManager.getSessionManager(cacheConn,
                                                            30, 2048000);

        Session lws = manager.createSession(lwsConn, user, cookie);

        manager.attachSession(lws_conn, lws, ...);

        boolean ret = XSAccessController.checkPrivilege(lws, "UPDATE");

        manager.detachSession(lws);
        manager.destroySession(lws);




  Most of the methods in this class are not static, and very security sensitive. The caller has to get hold of an object to call the methods. The object is highly protected. The only way to get the object is to call getSessionManager with followings:
           - XSSecurityPermission ("initSecurityManager") to be granted to the caller's code
           - Dispatcher's DB connection or Datasource


  In the integration case, we expect only trusted layer (OPSS) can initialize and get hold of the the XSSessionManager object. Application code should not be able to get hold of the object and further invoke most of the methods.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XSSessionManager``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    |------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract void`                                                        | `abortSession``(`[`Session`](Session.md)` session)`<br>Detaches this session.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `abstract void`                                                        | `assignUser``(`[`Session`](Session.md)` session, `[`ExternalUser`](ExternalUser.md)` targetUser, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`ExternalRole`](ExternalRole.md)`> externalRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Assigns an external user to the session that was previously created for anonymous user. |
    | `abstract void`                                                        | `assignUser``(`[`Session`](Session.md)` session, java.lang.String targetUser, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Assigns an XS user to the session that was previously created for anonymous user.                                                                                                   |
    | `abstract void`                                                        | `attachSession``(java.sql.Connection conn, `[`Session`](Session.md)` session, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`ExternalRole`](ExternalRole.md)`> externalRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Attaches the JDBC connection to the specified XS user's session.                                           |
    | `abstract void`                                                        | `attachSession``(java.sql.Connection conn, `[`Session`](Session.md)` session, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Attaches the JDBC connection to the specified XS user's session.                                                                                                                    |
    | `abstract `[`Session`](Session.md)                                     | `attachSessionByCookie``(java.sql.Connection conn, java.lang.String cookie, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`ExternalRole`](ExternalRole.md)`> externalRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Attaches the corresponding session for a specified cookie and returns the Session object.                    |
    | `abstract `[`Session`](Session.md)                                     | `attachSessionByID``(java.sql.Connection conn, java.lang.String id, java.util.Collection<java.lang.String> enabledDynamicRoles, java.util.Collection<java.lang.String> disabledDynamicRoles, java.util.Collection<`[`ExternalRole`](ExternalRole.md)`> externalRoles, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues, java.sql.Timestamp authenticationTime)`<br>Attaches the corresponding session for a specified ID and returns the Session object.                                |
    | `abstract void`                                                        | `clearCache``()`<br>Explicitly clears the shared cache from the middle tier.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `abstract `[`Session`](Session.md)                                     | `createAnonymousSession``(java.sql.Connection conn, java.lang.String cookie, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Creates an anonymous `Session` for XS user (to be assigned to) on the server as well as its corresponding middle-tier representation.                                                                                                                                                                                                                |
    | `abstract `[`Session`](Session.md)                                     | `createAnonymousSessionTrusted``(java.sql.Connection conn, java.lang.String cookie, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Creates an anonymous `Session` in trusted mode on the server for external user (to be assigned to) as well as its corresponding middle-tier representation.                                                                                                                                                                                   |
    | `abstract `[`SessionNamespaceAttribute`](SessionNamespaceAttribute.md) | `createAttribute``(`[`SessionNamespace`](SessionNamespace.md)` sessionNS, java.lang.String name, java.lang.String value, java.util.List<`[`SessionNamespace.ATTR_EVENT_TYPE`](SessionNamespace.ATTR_EVENT_TYPE.md)`> event)`<br>Creates a new attribute in the namespace with the specified name, value, and event.                                                                                                                                                                                                  |
    | `abstract `[`SessionNamespace`](SessionNamespace.md)                   | `createNamespace``(`[`Session`](Session.md)` session, java.lang.String name)`<br>Creates a new namespace for the given session.                                                                                                                                                                                                                                                                                                                                                                                      |
    | `abstract `[`Session`](Session.md)                                     | `createSession``(java.sql.Connection conn, `[`ExternalUser`](ExternalUser.md)` externalUser, java.lang.String cookie, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Creates a `Session` object for specified external user on the server as well as its corresponding middle-tier representation.                                                                                                                                                                               |
    | `abstract `[`Session`](Session.md)                                     | `createSession``(java.sql.Connection conn, java.lang.String user, java.lang.String cookie, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Creates a `Session` object on the server as well as its corresponding midtier representation.                                                                                                                                                                                                                                          |
    | `abstract `[`Session`](Session.md)                                     | `createSessionTrusted``(java.sql.Connection conn, `[`ExternalUser`](ExternalUser.md)` externalUser, java.lang.String cookie, java.util.Collection<`[`NamespaceValue`](NamespaceValue.md)`> namespaceValues)`<br>Creates a `Session` object for specified external user in trusted mode on the server as well as its corresponding middle-tier representation.                                                                                                                                                        |
    | `abstract void`                                                        | `deleteAttribute``(`[`SessionNamespace`](SessionNamespace.md)` sessionNS, java.lang.String name)`<br>Deletes the specified attribute The dispatcher needs to have the privilege to delete the given attribute                                                                                                                                                                                                                                                                                                        |
    | `abstract void`                                                        | `deleteNamespace``(`[`Session`](Session.md)` session, java.lang.String namespace)`<br>Removes a namespace from the session.                                                                                                                                                                                                                                                                                                                                                                                          |
    | `abstract void`                                                        | `destroySession``(java.sql.Connection conn, `[`Session`](Session.md)` session)`<br>Destroys the XS session.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `abstract void`                                                        | `detachSession``(`[`Session`](Session.md)` session)`<br>Detaches this session.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `abstract int`                                                         | `getCacheMaxIdleTime``()`<br>Returns the maximum number of minutes for which the cache can remain without any activity                                                                                                                                                                                                                                                                                                                                                                                               |
    | `abstract long`                                                        | `getCacheMaxSize``()`<br>Returns the maximum cache size, in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `abstract float`                                                       | `getHighWaterMark``()`<br>Gets the high watermark for the cache.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `abstract float`                                                       | `getLowWaterMark``()`<br>Gets the low watermark for the cache.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `abstract int`                                                         | `getPrivateCacheMaxEntries``()`<br>Returns the maximum number of entries that the ACL evaluation result can be cached in the session.                                                                                                                                                                                                                                                                                                                                                                                |
    | `static XSSessionManager`                                              | `getSessionManager``(java.sql.Connection conn, int cacheMaxIdleTime, int cacheMaxsize)`<br>Initializes an `XSSessionManager` using a dedicated connections.                                                                                                                                                                                                                                                                                                                                                          |
    | `static XSSessionManager`                                              | `getSessionManager``(javax.sql.DataSource datasource, int cacheMaxIdleTime, int cacheMaxsize)`<br>Initializes an `XSSessionManager` using connections from the connection pool.                                                                                                                                                                                                                                                                                                                                      |
    | `abstract `[`SessionNamespaceAttribute`](SessionNamespaceAttribute.md) | `resetAttribute``(`[`SessionNamespace`](SessionNamespace.md)` sessionNS, java.lang.String name)`<br>Resets the specified attribute in the namespace to its default value.                                                                                                                                                                                                                                                                                                                                            |
    | `abstract void`                                                        | `saveSession``(`[`Session`](Session.md)` session)`<br>Saves the specified session leaving it attached.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `abstract `[`SessionNamespaceAttribute`](SessionNamespaceAttribute.md) | `setAttribute``(`[`SessionNamespace`](SessionNamespace.md)` sessionNS, java.lang.String name, java.lang.String value)`<br>Sets the attribute for a session namespace with the specified name and value The dispatcher needs to have the privilege to set the attribute on the given namespace                                                                                                                                                                                                                        |
    | `abstract void`                                                        | `setCacheMaxIdleTime``(int minutes)`<br>Sets the maximum number of minutes for which the cache can remain without any activity.                                                                                                                                                                                                                                                                                                                                                                                      |
    | `abstract void`                                                        | `setCacheMaxSize``(long megaBytes)`<br>Sets the size of the cache on the middle tier, in bytes.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `abstract void`                                                        | `setCookie``(`[`Session`](Session.md)` session, java.lang.String cookie)`<br>Sets the cookie for the session                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `abstract void`                                                        | `setInactivityTimeout``(`[`Session`](Session.md)` session, int minutes)`<br>Sets the inactivity timeout for the session in minutes.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `abstract void`                                                        | `setPrivateCacheMaxEntries``(int maxEntries)`<br>Sets the maximum number of entries that the ACL evaluation result can be cached in the session.                                                                                                                                                                                                                                                                                                                                                                     |
    | `abstract void`                                                        | `setWaterMark``(float low, float high)`<br>Sets the high and low watermarks for the cache.                                                                                                                                                                                                                                                                                                                                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSSessionManager

          public XSSessionManager()

  <!-- -->

  - ### Method Detail

    - #### createSession

          public abstract Session createSession(java.sql.Connection conn,
                                                java.lang.String user,
                                                java.lang.String cookie,
                                                java.util.Collection<NamespaceValue> namespaceValues)
                                         throws InvalidXSUserException,
                                                AccessDeniedException,
                                                java.sql.SQLException,
                                                XSException,
                                                InvalidXSNamespaceException

      Creates a `Session` object on the server as well as its corresponding midtier representation. It also creates or changes the `Namespace` specified in the `Session`. The cookie can be used to identify the newly created XS user session in future calls, until the cookie value is changed or the session is destroyed. By default, the session is created in secure mode.
      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `user` - the XS user associated with the `Session`

      `cookie` - used to identify the session

      `namespaceValues` - the namespace with attributes The `user` must have the `bindNamespace` privilege.

      Returns:
      session the `Session` object

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), [`SessionNamespace`](SessionNamespace.md)

    <!-- -->

    - #### createAnonymousSession

          public abstract Session createAnonymousSession(java.sql.Connection conn,
                                                         java.lang.String cookie,
                                                         java.util.Collection<NamespaceValue> namespaceValues)
                                                  throws InvalidXSUserException,
                                                         AccessDeniedException,
                                                         java.sql.SQLException,
                                                         XSException,
                                                         InvalidXSNamespaceException

      Creates an anonymous `Session` for XS user (to be assigned to) on the server as well as its corresponding middle-tier representation. It also creates or changes the `Namespace` specified in the `Session`. The user for this session is a seeded anonymous user. The cookie can be used to identify the newly created XS user session in future calls, until the cookie value is changed or the session is destroyed. It is possible to assign a specific user to take over this session that will keep some of the state of the session.
      By default, the session is created in secure mode.

      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `cookie` - used to identify the session

      `namespaceValues` - a list of namespaces with attributes

      Returns:
      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), [`SessionNamespace`](SessionNamespace.md)

    <!-- -->

    - #### createAnonymousSessionTrusted

          public abstract Session createAnonymousSessionTrusted(java.sql.Connection conn,
                                                                java.lang.String cookie,
                                                                java.util.Collection<NamespaceValue> namespaceValues)
                                                         throws InvalidXSUserException,
                                                                AccessDeniedException,
                                                                java.sql.SQLException,
                                                                XSException,
                                                                InvalidXSNamespaceException

      Creates an anonymous `Session` in trusted mode on the server for external user (to be assigned to) as well as its corresponding middle-tier representation. It also creates or changes the `Namespace` specified in the `Session` . The session is going to be assigned to an extenal user, which has no footprint at Database, so no database role is enabled in the session. The user for this session is a seeded anonymous user. The cookie can be used to identify the newly created session in future calls, until the cookie value is changed or the session is destroyed. It is possible to assign a specific external user to take over this session that will keep some of the state of the session.
      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `cookie` - used to identify the session

      `namespaceValues` - a list of namespaces with attributes

      Returns:
      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), [`SessionNamespace`](SessionNamespace.md)

    <!-- -->

    - #### saveSession

          public abstract void saveSession(Session session)
                                    throws java.sql.SQLException,
                                           NotAttachedException,
                                           XSException

      Saves the specified session leaving it attached. It commits all the changes on the session. The changes can be related to namespace, user, role, and other session attributes. For committing changes, this method is same as the detachSession. The only difference is that it does not detach from the connection, but stay attached. This is a server roundtrip.
      Parameters:
      `session,` - a `Session` object

      Throws:
      `java.sql.SQLException`

      [`NotAttachedException`](NotAttachedException.md)

      [`XSException`](XSException.md)

    <!-- -->

    - #### createSessionTrusted

          public abstract Session createSessionTrusted(java.sql.Connection conn,
                                                       ExternalUser externalUser,
                                                       java.lang.String cookie,
                                                       java.util.Collection<NamespaceValue> namespaceValues)
                                                throws InvalidXSUserException,
                                                       AccessDeniedException,
                                                       java.sql.SQLException,
                                                       XSException,
                                                       InvalidXSNamespaceException

      Creates a `Session` object for specified external user in trusted mode on the server as well as its corresponding middle-tier representation. It also creates or changes the `Namespace` specified in the `Session`. The cookie can be used to identify the newly session in future calls, until the cookie value is changed or the session is destroyed.
      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `externalUser` - the external user associated with the `Session`

      `cookie` - used to identify the session

      `namespaceValues` - the namespace with attributes

      Returns:
      session the `Session` object

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), [`SessionNamespace`](SessionNamespace.md)

    <!-- -->

    - #### createSession

          public abstract Session createSession(java.sql.Connection conn,
                                                ExternalUser externalUser,
                                                java.lang.String cookie,
                                                java.util.Collection<NamespaceValue> namespaceValues)
                                         throws InvalidXSUserException,
                                                AccessDeniedException,
                                                java.sql.SQLException,
                                                XSException,
                                                InvalidXSNamespaceException

      Creates a `Session` object for specified external user on the server as well as its corresponding middle-tier representation. It also creates or changes the `Namespace` specified for the `Session`.
      The cookie can be used to identify the newly created XS user session in future calls, until the cookie value is changed or the session is destroyed. By default, the session is in secure mode

      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `externalUser` - the external user associated with the `Session`

      `cookie` - used to identify the session

      `namespaceValues` - the namespace with attributes

      Returns:
      session the `Session` object

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), [`SessionNamespace`](SessionNamespace.md)

    <!-- -->

    - #### attachSessionByCookie

          public abstract Session attachSessionByCookie(java.sql.Connection conn,
                                                        java.lang.String cookie,
                                                        java.util.Collection<java.lang.String> enabledDynamicRoles,
                                                        java.util.Collection<java.lang.String> disabledDynamicRoles,
                                                        java.util.Collection<ExternalRole> externalRoles,
                                                        java.util.Collection<NamespaceValue> namespaceValues,
                                                        java.sql.Timestamp authenticationTime)
                                                 throws java.sql.SQLException,
                                                        AccessDeniedException,
                                                        InvalidSessionException,
                                                        XSException,
                                                        InvalidXSNamespaceException

      Attaches the corresponding session for a specified cookie and returns the Session object. At same time, changes the dynamic roles, external roles, namespaces, and authentication time on the session. Dynamic roles, external roles, and namespace with attributes are supported in this operation.
      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `cookie` - the cookie string

      `enabledDynamicRoles` - the enabled dynamic roles list

      `disabledDynamicRoles` - the disabled dyamic roles list

      `externalRoles` - the external roles list

      `namespaceValues` - the namespaces with attributes.

      `authenticationTime` - the authentication time

      Returns:
      a `Session` object

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      [`InvalidSessionException`](InvalidSessionException.md)

    <!-- -->

    - #### attachSessionByID

          public abstract Session attachSessionByID(java.sql.Connection conn,
                                                    java.lang.String id,
                                                    java.util.Collection<java.lang.String> enabledDynamicRoles,
                                                    java.util.Collection<java.lang.String> disabledDynamicRoles,
                                                    java.util.Collection<ExternalRole> externalRoles,
                                                    java.util.Collection<NamespaceValue> namespaceValues,
                                                    java.sql.Timestamp authenticationTime)
                                             throws java.sql.SQLException,
                                                    AccessDeniedException,
                                                    InvalidSessionException,
                                                    XSException,
                                                    InvalidXSNamespaceException

      Attaches the corresponding session for a specified ID and returns the Session object. At same time, changes the dynamic roles, external roles, namespaces, and authentication time on the session.
      Parameters:
      `conn` - the JDBC connection for server roundtrip

      `id` - the session ID of the session

      `enabledDynamicRoles` - the enabled dynamic roles list

      `disabledDynamicRoles` - the disabled dyamic roles list

      `externalRoles` - the external roles list

      `namespaceValues` - the namespaces with attributes.

      `authenticationTime` - the authentication time

      Returns:
      a `Session` object

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - if the current user does not have the privilege to create this session

      `java.sql.SQLException` - if a JDBC exception happens

      [`InvalidXSUserException`](InvalidXSUserException.md) - if an invalid XS user is specified

      [`XSException`](XSException.md) - if a generic error is detected

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      [`InvalidSessionException`](InvalidSessionException.md)

    <!-- -->

    - #### attachSession

          public abstract void attachSession(java.sql.Connection conn,
                                             Session session,
                                             java.util.Collection<java.lang.String> enabledDynamicRoles,
                                             java.util.Collection<java.lang.String> disabledDynamicRoles,
                                             java.util.Collection<ExternalRole> externalRoles,
                                             java.util.Collection<NamespaceValue> namespaceValues,
                                             java.sql.Timestamp authenticationTime)
                                      throws java.sql.SQLException,
                                             AccessDeniedException,
                                             InvalidSessionException,
                                             XSException,
                                             InvalidXSNamespaceException

      Attaches the JDBC connection to the specified XS user's session. At same time,changes the dynamic roles, namespaces, and authentication time on the session.
      Parameters:
      `conn` - database connection to be used to attach to the session

      `session` - the session object that needs to be attached

      `enabledDynamicRoles` - a collection of dynamic role names to be enabled

      `disabledDynamicRoles` - a collection of dynamic role names to be disabled

      `externalRoles` - a collection of `ExternalRoles` to be enabled

      `namespaceValues` - a list of `NamespaceAttributeValue` objects to be created

      `authenticationTime` - the authenticateion time

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to attach to this session

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), `oracle.security.xs.NamespaceAttributeValue`

    <!-- -->

    - #### attachSession

          public abstract void attachSession(java.sql.Connection conn,
                                             Session session,
                                             java.util.Collection<java.lang.String> enabledDynamicRoles,
                                             java.util.Collection<java.lang.String> disabledDynamicRoles,
                                             java.util.Collection<NamespaceValue> namespaceValues,
                                             java.sql.Timestamp authenticationTime)
                                      throws java.sql.SQLException,
                                             AccessDeniedException,
                                             InvalidSessionException,
                                             XSException,
                                             InvalidXSNamespaceException

      Attaches the JDBC connection to the specified XS user's session. At same time, changes the dynamic roles and namespaces on the session.
      Parameters:
      `conn` - database connection to be used to attach to the session

      `session` - the session object that needs to be attached

      `enabledDynamicRoles` - a collection of dynamic role names to be enabled

      `disabledDynamicRoles` - a collection of dynamic role names to be disabled

      `namespaceValues` - a list of `NamespaceAttributeValue` objects to be created

      `authenticationTime` - the authenticateion time

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to attach to this session

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

      See Also:
      [`Session`](Session.md), `oracle.security.xs.NamespaceAttributeValue`

    <!-- -->

    - #### detachSession

          public abstract void detachSession(Session session)
                                      throws java.sql.SQLException,
                                             NotAttachedException,
                                             XSException

      Detaches this session. Commits all the changes. A database round trip is required to perform this operation.
      Throws:
      `java.sql.SQLException` - a JDBC exception is thrown

      [`XSException`](XSException.md) - a generic error is detected

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### abortSession

          public abstract void abortSession(Session session)
                                     throws java.sql.SQLException,
                                            NotAttachedException,
                                            XSException

      Detaches this session. Rollback all the changes. A database round trip is required to perform this operation.
      Throws:
      `java.sql.SQLException` - a JDBC exception is thrown

      [`XSException`](XSException.md) - a generic error is detected

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### destroySession

          public abstract void destroySession(java.sql.Connection conn,
                                              Session session)
                                       throws java.sql.SQLException,
                                              XSException,
                                              AccessDeniedException,
                                              InvalidSessionException

      Destroys the XS session. The destroyed session may no longer be accessed from any JVM. A database round trip is required to perform this operation.
      Parameters:
      `conn` - the JDBC Connection used to make a roundtrip operation to the server and destroy the session

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to destroy

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

    <!-- -->

    - #### assignUser

          public abstract void assignUser(Session session,
                                          java.lang.String targetUser,
                                          java.util.Collection<java.lang.String> enabledDynamicRoles,
                                          java.util.Collection<java.lang.String> disabledDynamicRoles,
                                          java.util.Collection<NamespaceValue> namespaceValues,
                                          java.sql.Timestamp authenticationTime)
                                   throws java.sql.SQLException,
                                          AccessDeniedException,
                                          InvalidSessionException,
                                          XSException,
                                          InvalidXSNamespaceException

      Assigns an XS user to the session that was previously created for anonymous user. At same time, changes the dynamic roles, namespaces, and authentication time on the session.
      Parameters:
      `session` - Session obejct to assign user on

      `targetUser` - a user initialized based on authentication

      `enabledDynamicRoles` - a list of dynamic role names to be enabled

      `disabledDynamicRoles` - a list of dynamic role names to be disabled

      `namespaceValues` - a list of `NamespaceValue` objects to be created.

      `authenticationTime` - a timestamp indicated if the user authenticated

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to switchuser

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSUserException`](InvalidXSUserException.md) - an invalid XS user is specified

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

    <!-- -->

    - #### assignUser

          public abstract void assignUser(Session session,
                                          ExternalUser targetUser,
                                          java.util.Collection<java.lang.String> enabledDynamicRoles,
                                          java.util.Collection<java.lang.String> disabledDynamicRoles,
                                          java.util.Collection<ExternalRole> externalRoles,
                                          java.util.Collection<NamespaceValue> namespaceValues,
                                          java.sql.Timestamp authenticationTime)
                                   throws java.sql.SQLException,
                                          AccessDeniedException,
                                          InvalidSessionException,
                                          XSException,
                                          InvalidXSNamespaceException

      Assigns an external user to the session that was previously created for anonymous user. At same time, changes the dynamic roles, external roles, namespace, and authentication time on the session.
      Parameters:
      `session` - Session obejct to assign user on

      `targetUser` - a `User` object initialized based on authentication

      `enabledDynamicRoles` - a list of dynamic role names to be enabled

      `disabledDynamicRoles` - a list of dynamic role names to be disabled

      `externalRoles` - a list of external roles to be granted

      `namespaceValues` - a list of `NamespaceAttributeValue` objects to be created.

      `authenticationTime` - a timestamp indicated if the user authenticated

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the current user does not have the privilege to switchuser

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`InvalidXSUserException`](InvalidXSUserException.md) - an invalid XS user is specified

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - if an invalid namespace is specified

    <!-- -->

    - #### clearCache

          public abstract void clearCache()
                                   throws java.security.AccessControlException,
                                          XSSessionManagerException

      Explicitly clears the shared cache from the middle tier.
      Throws:
      `java.security.AccessControlException` - if security manager is enabled and clearCache `XSSecurityPermission` is not granted

      `XSSecurityManagerException` - `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### getSessionManager

          public static XSSessionManager getSessionManager(javax.sql.DataSource datasource,
                                                           int cacheMaxIdleTime,
                                                           int cacheMaxsize)
                                                    throws XSException,
                                                           java.security.NoSuchAlgorithmException,
                                                           java.security.InvalidAlgorithmParameterException,
                                                           java.security.spec.InvalidKeySpecException,
                                                           java.security.InvalidKeyException,
                                                           java.sql.SQLException

      Initializes an `XSSessionManager` using connections from the connection pool. By default, the initialized XSSessionManager will sign the request. So the given connection pool user will be used to authorize the session operations. The caller of this method needs to have initSecurityManager `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `datasource` - the connection pool `DateSource` for the database connection

      `cacheMaxIdleTime` - maximum amount of time that the cache persists, in minutes, before synchronizing with the server

      `cacheMaxsize` - maximum allowable size, in bytes, of the `ACL` or `SecurityClass` cache

      Throws:
      [`XSException`](XSException.md) - a generic error is detected

      `java.security.NoSuchAlgorithmException` - a particular cryptographic algorithm is requested but is not available in the environment

      `java.security.InvalidAlgorithmParameterException` - invalid or inappropriate algorithm parameters

      `java.security.spec.InvalidKeySpecException` - invalid key specifications

      `java.security.InvalidKeyException` - invalid Keys

      `java.sql.SQLException` - a problem in the SQL

    <!-- -->

    - #### getSessionManager

          public static XSSessionManager getSessionManager(java.sql.Connection conn,
                                                           int cacheMaxIdleTime,
                                                           int cacheMaxsize)
                                                    throws XSException,
                                                           java.security.NoSuchAlgorithmException,
                                                           java.security.InvalidAlgorithmParameterException,
                                                           java.security.spec.InvalidKeySpecException,
                                                           java.security.InvalidKeyException,
                                                           java.sql.SQLException

      Initializes an `XSSessionManager` using a dedicated connections. By default, the initialized XSSessionManager will sign the request. So the given connection will be used to authorize the session operations. The caller of this method needs to have initSecurityManager `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `conn` - decicated JDBC connection

      `cacheMaxIdleTime` - maximum amount of time that the cache persists, in minutes, before synchronizing with the server

      `cacheMaxsize` - maximum allowable size, in bytes, of the `ACL` or `SecurityClass` cache

      Throws:
      [`XSException`](XSException.md) - a generic error is detected

      `java.security.NoSuchAlgorithmException` - a particular cryptographic algorithm is requested but is not available in the environment

      `java.security.InvalidAlgorithmParameterException` - invalid or inappropriate algorithm parameters

      `java.security.spec.InvalidKeySpecException` - invalid key specifications

      `java.security.InvalidKeyException` - invalid Keys

      `java.sql.SQLException` - a problem in the SQL

    <!-- -->

    - #### getCacheMaxIdleTime

          public abstract int getCacheMaxIdleTime()
                                           throws XSSessionManagerException

      Returns the maximum number of minutes for which the cache can remain without any activity
      Returns:
      maximum number of minutes for which the cache can remain without any activity

      Throws:
      `XSSecurityManagerException` - `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### setCacheMaxIdleTime

          public abstract void setCacheMaxIdleTime(int minutes)
                                            throws java.security.AccessControlException,
                                                   XSSessionManagerException

      Sets the maximum number of minutes for which the cache can remain without any activity. The caller of this method needs to have setCacheMaxIdleTime `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `minutes` - the maximum number of minutes for which the cache can remain without any activity

      Throws:
      `java.security.AccessControlException` - if missing required permission

      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### getCacheMaxSize

          public abstract long getCacheMaxSize()
                                        throws XSSessionManagerException

      Returns the maximum cache size, in bytes.
      Returns:
      maximum cache size, in bytes

      Throws:
      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### setCacheMaxSize

          public abstract void setCacheMaxSize(long megaBytes)
                                        throws java.security.AccessControlException,
                                               XSSessionManagerException

      Sets the size of the cache on the middle tier, in bytes. The default value is 10MB and the minimum value is 1MB. The caller of this method needs to have setCacheSize `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `megaBytes` - integer value representing cache in bytes

      Throws:
      `java.security.AccessControlException` - if missing required permission

      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized.

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### getHighWaterMark

          public abstract float getHighWaterMark()
                                          throws XSSessionManagerException

      Gets the high watermark for the cache. if the cache size reaches high watermark the cache eviction algorithm removes entries until the cache size reaches low watermark.
      Throws:
      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### getLowWaterMark

          public abstract float getLowWaterMark()
                                         throws XSSessionManagerException

      Gets the low watermark for the cache. if the cache size reaches high watermark the cache eviction algorithm removes entries until the cache size reaches low watermark.
      Throws:
      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### setWaterMark

          public abstract void setWaterMark(float low,
                                            float high)
                                     throws java.security.AccessControlException,
                                            XSSessionManagerException

      Sets the high and low watermarks for the cache. The high watermark value must be in the range of 0.0 to 1.0, and the low watermark value must be lower then the high watermark value. The caller of this method needs to have setWaterMark `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `low` - low watermark value

      `high` - high watermark value

      Throws:
      `java.security.AccessControlException` - if missing required permission

      `XSSecurityManagerException` - if `XSSecurityManager` is not initialized

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### getPrivateCacheMaxEntries

          public abstract int getPrivateCacheMaxEntries()

      Returns the maximum number of entries that the ACL evaluation result can be cached in the session.

    <!-- -->

    - #### setPrivateCacheMaxEntries

          public abstract void setPrivateCacheMaxEntries(int maxEntries)
                                                  throws java.security.AccessControlException,
                                                         XSSessionManagerException

      Sets the maximum number of entries that the ACL evaluation result can be cached in the session. The caller of this method needs to have setPrivateCacheMaxEntries `XSSecurityPermission` if security manager is enabled.
      Parameters:
      `maxEntries` - number of cache entries

      Throws:
      `java.security.AccessControlException`

      [`XSSessionManagerException`](XSSessionManagerException.md)

    <!-- -->

    - #### setCookie

          public abstract void setCookie(Session session,
                                         java.lang.String cookie)
                                  throws XSException

      Sets the cookie for the session
      Parameters:
      `session` - the session to be set

      `cookie` - value of the cookie

      Throws:
      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### setInactivityTimeout

          public abstract void setInactivityTimeout(Session session,
                                                    int minutes)
                                             throws XSException

      Sets the inactivity timeout for the session in minutes.
      Parameters:
      `session` - the session to be set

      `minutes` - number in minutes

      Throws:
      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### createNamespace

          public abstract SessionNamespace createNamespace(Session session,
                                                           java.lang.String name)
                                                    throws java.sql.SQLException,
                                                           AccessDeniedException,
                                                           XSException,
                                                           InvalidXSNamespaceException,
                                                           InvalidSessionException,
                                                           NotAttachedException

      Creates a new namespace for the given session. The createNamespace method creates a new session namespace using the namespace template document, whose name matches with the specified name. If an event handler is defined in the template document, then the defined event handler applies to all the namespaces created using that template. The dispatcher needs to have the privilege for the given namesapce.
      Parameters:
      `session` - the given session

      `name` - the name of the session namespace.

      Returns:
      `SessionNamespace` that is created

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the dispatcher does not have the privilege to create the namespace

      [`XSException`](XSException.md) - a generic error is detected

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - namespace already exists

      [`InvalidSessionException`](InvalidSessionException.md) - an attempt is made to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

    <!-- -->

    - #### deleteNamespace

          public abstract void deleteNamespace(Session session,
                                               java.lang.String namespace)
                                        throws java.sql.SQLException,
                                               AccessDeniedException,
                                               XSException,
                                               InvalidXSNamespaceException,
                                               InvalidSessionException,
                                               NotAttachedException

      Removes a namespace from the session. The dispatcher needs to have the privilege for the given namesapce.
      Parameters:
      `session` - the given session

      `namespace` - the namespace to be removed

      Throws:
      [`AccessDeniedException`](AccessDeniedException.md) - the dispatcher does not have the privilege to delete this namespace

      `java.sql.SQLException` - a JDBC exception is thrown

      [`InvalidXSNamespaceException`](InvalidXSNamespaceException.md) - namespace is invalid

      [`InvalidSessionException`](InvalidSessionException.md) - attempted to reference an invalid session

      [`NotAttachedException`](NotAttachedException.md) - session not attached

      [`XSException`](XSException.md) - a generic error is detected

    <!-- -->

    - #### createAttribute

          public abstract SessionNamespaceAttribute createAttribute(SessionNamespace sessionNS,
                                                                    java.lang.String name,
                                                                    java.lang.String value,
                                                                    java.util.List<SessionNamespace.ATTR_EVENT_TYPE> event)
                                                             throws java.sql.SQLException,
                                                                    SessionNamespaceException,
                                                                    AccessDeniedException,
                                                                    XSException,
                                                                    InvalidXSAttributeException,
                                                                    NotAttachedException

      Creates a new attribute in the namespace with the specified name, value, and event. The dispatcher needs to have the privilege for the given namesapce and attribute
      Parameters:
      `sessionNS` - the given `SessionNamespace`

      `name` - name of the attribute

      `value` - value of the attribute

      `event` - event registration of the attribute

      Returns:
      the newly created attribute

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the dispatcher does not have the privilege

      [`XSException`](XSException.md) - when a generic error is detected

      [`SessionNamespaceException`](SessionNamespaceException.md) - when the attibute name is invalid

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute value is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### deleteAttribute

          public abstract void deleteAttribute(SessionNamespace sessionNS,
                                               java.lang.String name)
                                        throws java.sql.SQLException,
                                               AccessDeniedException,
                                               XSException,
                                               InvalidXSAttributeException,
                                               NotAttachedException

      Deletes the specified attribute The dispatcher needs to have the privilege to delete the given attribute
      Parameters:
      `sessionNS` - the given `SessionNamespace`

      `name` - name of the attribute

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the dispatcher user does not have the privilege to delete the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### resetAttribute

          public abstract SessionNamespaceAttribute resetAttribute(SessionNamespace sessionNS,
                                                                   java.lang.String name)
                                                            throws java.sql.SQLException,
                                                                   AccessDeniedException,
                                                                   XSException,
                                                                   InvalidXSAttributeException,
                                                                   NotAttachedException

      Resets the specified attribute in the namespace to its default value. The dispatcher needs to have the privilege to restet the namespace
      Parameters:
      `sessionNS` - the given `SessionNamespace`

      `name` - name of the attribute

      Returns:
      the attribute that has been reset

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the current user does not have the privilege to reset the attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

    <!-- -->

    - #### setAttribute

          public abstract SessionNamespaceAttribute setAttribute(SessionNamespace sessionNS,
                                                                 java.lang.String name,
                                                                 java.lang.String value)
                                                          throws java.sql.SQLException,
                                                                 SessionNamespaceException,
                                                                 AccessDeniedException,
                                                                 XSException,
                                                                 InvalidXSAttributeException,
                                                                 NotAttachedException

      Sets the attribute for a session namespace with the specified name and value The dispatcher needs to have the privilege to set the attribute on the given namespace
      Parameters:
      `sessionNS` - the given `SessionNamespace`

      `name` - name of the attribute

      `value` - value of the attribute

      Returns:
      SessionNamespaceAttribute attribute object whose value is set

      Throws:
      `java.sql.SQLException` - when a JDBC exception is thrown

      [`AccessDeniedException`](AccessDeniedException.md) - when the dispatcher does not have the privilege to set the attribute on the namespace/attribute

      [`XSException`](XSException.md) - when a generic error is detected

      [`SessionNamespaceException`](SessionNamespaceException.md) - when the namespace is invalid

      [`InvalidXSAttributeException`](InvalidXSAttributeException.md) - when the attribute is invalid

      [`NotAttachedException`](NotAttachedException.md) - when the session is not attached

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

- [Prev Class](XSSessionException.md)
- [Next Class](XSSessionManagerException.md)

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
