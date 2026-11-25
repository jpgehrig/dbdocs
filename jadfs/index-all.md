Skip navigation links

- [Package](oracle/security/xs/package-summary.md)
- Class
- [Tree](oracle/security/xs/package-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

A C D E G I N O P R S T U V X 

## A

[abortSession(Session)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Detaches this session.

[AccessDeniedException](oracle/security/xs/AccessDeniedException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown when an operation fails due to insufficient privilege.

[AccessDeniedException(Throwable)](oracle/security/xs/AccessDeniedException.md) - Constructor for exception oracle.security.xs.[AccessDeniedException](oracle/security/xs/AccessDeniedException.md)
 

[AccessDeniedException(String)](oracle/security/xs/AccessDeniedException.md) - Constructor for exception oracle.security.xs.[AccessDeniedException](oracle/security/xs/AccessDeniedException.md)
 

[AccessDeniedException()](oracle/security/xs/AccessDeniedException.md) - Constructor for exception oracle.security.xs.[AccessDeniedException](oracle/security/xs/AccessDeniedException.md)
 

[AclId](oracle/security/xs/AclId.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents multiple ACL IDs in either long or raw form.

[AclId(byte\[\])](oracle/security/xs/AclId.md) - Constructor for class oracle.security.xs.[AclId](oracle/security/xs/AclId.md)
Constructs an AclId using the raw binary returned by the ora_get_aclids operator.

[AclId(List\<Long\>)](oracle/security/xs/AclId.md) - Constructor for class oracle.security.xs.[AclId](oracle/security/xs/AclId.md)
Constructs an AclId with internal ACL IDs of type long.

[assignUser(Session, String, Collection\<String\>, Collection\<String\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Assigns an XS user to the session that was previously created for anonymous user.

[assignUser(Session, ExternalUser, Collection\<String\>, Collection\<String\>, Collection\<ExternalRole\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Assigns an external user to the session that was previously created for anonymous user.

[attachSession(Connection, Session, Collection\<String\>, Collection\<String\>, Collection\<ExternalRole\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Attaches the JDBC connection to the specified XS user's session.

[attachSession(Connection, Session, Collection\<String\>, Collection\<String\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Attaches the JDBC connection to the specified XS user's session.

[attachSessionByCookie(Connection, String, Collection\<String\>, Collection\<String\>, Collection\<ExternalRole\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Attaches the corresponding session for a specified cookie and returns the Session object.

[attachSessionByID(Connection, String, Collection\<String\>, Collection\<String\>, Collection\<ExternalRole\>, Collection\<NamespaceValue\>, Timestamp)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Attaches the corresponding session for a specified ID and returns the Session object.

[AttributeValue](oracle/security/xs/AttributeValue.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class provides a name/value pair that is stored in session namespace.

[AttributeValue(String, String)](oracle/security/xs/AttributeValue.md) - Constructor for class oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
Creates an `AttibuteValue` with the specified attribute name and attribute value.

[authenticate(String, String, String)](oracle/security/xs/XSAuthenticationModule.md) - Static method in class oracle.security.xs.[XSAuthenticationModule](oracle/security/xs/XSAuthenticationModule.md)
Authenticates the user against the Database.

## C

[checkAcl(Session, AclId, List\<String\>)](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Checks for mutiple privileges.

[checkAcl(Session, AclId, String)](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Checks for a privilege.

[checkAcl(Session, byte\[\], List\<String\>)](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Checks for multiple privileges.

[checkAcl(Session, byte\[\], String)](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Checks for a privilege.

[clearCache()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Explicitly clears the shared cache from the middle tier.

[createAnonymousSession(Connection, String, Collection\<NamespaceValue\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates an anonymous `Session` for XS user (to be assigned to) on the server as well as its corresponding middle-tier representation.

[createAnonymousSessionTrusted(Connection, String, Collection\<NamespaceValue\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates an anonymous `Session` in trusted mode on the server for external user (to be assigned to) as well as its corresponding middle-tier representation.

[createAttribute(String, String)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Creates a new attribute in the namespace with the specified name and value.

[createAttribute(String, String, List\<SessionNamespace.ATTR_EVENT_TYPE\>)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Creates a new attribute in the namespace with the specified name, value, and event.

[createAttribute(SessionNamespace, String, String, List\<SessionNamespace.ATTR_EVENT_TYPE\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates a new attribute in the namespace with the specified name, value, and event.

[createNamespace(String)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Creates a new namespace for this session.

[createNamespace(Session, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates a new namespace for the given session.

[createSession(Connection, String, String, Collection\<NamespaceValue\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates a `Session` object on the server as well as its corresponding midtier representation.

[createSession(Connection, ExternalUser, String, Collection\<NamespaceValue\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates a `Session` object for specified external user on the server as well as its corresponding middle-tier representation.

[createSessionTrusted(Connection, ExternalUser, String, Collection\<NamespaceValue\>)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Creates a `Session` object for specified external user in trusted mode on the server as well as its corresponding middle-tier representation.

## D

[deleteAttribute(String)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Deletes the specified attribute

[deleteAttribute(SessionNamespace, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Deletes the specified attribute The dispatcher needs to have the privilege to delete the given attribute

[deleteNamespace(String)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Removes a namespace from a session.

[deleteNamespace(Session, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Removes a namespace from the session.

[destroySession(Connection, Session)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Destroys the XS session.

[detachSession(Session)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Detaches this session.

[disableRole(Role)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Disables a role granted to the current user for this session.

## E

[enableRole(Role)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Enables a role granted to the current user for this session.

[ExternalRole](oracle/security/xs/ExternalRole.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents externally managed roles used in a session.

[ExternalRole(String, String, long)](oracle/security/xs/ExternalRole.md) - Constructor for class oracle.security.xs.[ExternalRole](oracle/security/xs/ExternalRole.md)
Constructs an `ExternalRole` object from a name, a `UUID`, and a `DBID`.

[ExternalRole(String, String)](oracle/security/xs/ExternalRole.md) - Constructor for class oracle.security.xs.[ExternalRole](oracle/security/xs/ExternalRole.md)
Constructs an `ExternalRole` object from a name and a `UUID`

[ExternalRole(String)](oracle/security/xs/ExternalRole.md) - Constructor for class oracle.security.xs.[ExternalRole](oracle/security/xs/ExternalRole.md)
Constructs an `ExternalRole` object from a `UUID`

[ExternalUser](oracle/security/xs/ExternalUser.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents externally managed users used in a session.

[ExternalUser(String, String, long)](oracle/security/xs/ExternalUser.md) - Constructor for class oracle.security.xs.[ExternalUser](oracle/security/xs/ExternalUser.md)
Constructs an `ExternalUser` object from a name, a `UUID` and a `DBID`.

[ExternalUser(String, String)](oracle/security/xs/ExternalUser.md) - Constructor for class oracle.security.xs.[ExternalUser](oracle/security/xs/ExternalUser.md)
Constructs an `ExternalUser` object from a name and a `UUID`

[ExternalUser(String)](oracle/security/xs/ExternalUser.md) - Constructor for class oracle.security.xs.[ExternalUser](oracle/security/xs/ExternalUser.md)
Constructs an `ExternalUser` object from a name

## G

[getAttribute(String)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
" Returns the specified attribute."

[getAttributes()](oracle/security/xs/NamespaceValue.md) - Method in class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
Retrieves the list of attributes.

[getAttributes()](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Returns a collection of the attribute names in the namespace.

[getCacheMaxIdleTime()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Returns the maximum number of minutes for which the cache can remain without any activity

[getCacheMaxSize()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Returns the maximum cache size, in bytes.

[getConnection()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns the Oracle JDBC `Connection` attached with this session.

[getCookie()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns the secure session cookie used for this session.

[getDBID()](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Retrieves the `DBID` of the `Principal`.

[getDefaultValue()](oracle/security/xs/SessionNamespaceAttribute.md) - Method in interface oracle.security.xs.[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md)
Returns the default value of the attribute

[getEnabledRoles()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns a collection of all currently enabled roles.

[getHighWaterMark()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Gets the high watermark for the cache.

[getId()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns the internal session ID generated at server for this session.

[getIds()](oracle/security/xs/AclId.md) - Method in class oracle.security.xs.[AclId](oracle/security/xs/AclId.md)
Returns internal ACL IDs of type long.

[getLowWaterMark()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Gets the low watermark for the cache.

[getMessage()](oracle/security/xs/XSException.md) - Method in exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Returns the detailed message of the exception.

[getMessage(Locale)](oracle/security/xs/XSException.md) - Method in exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Returns the detailed message of the exception in the specified `Locale`.

[getName()](oracle/security/xs/AttributeValue.md) - Method in class oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
Returns the attribute name.

[getName()](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Retrieves the name of the Principal.

[getName()](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Returns the name of the namespace

[getName()](oracle/security/xs/SessionNamespaceAttribute.md) - Method in interface oracle.security.xs.[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md)
Returns the attribute name.

[getNamespace()](oracle/security/xs/NamespaceValue.md) - Method in class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
Retrieves the namespace name.

[getNamespace(String)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns the specified namespace in the session.

[getPrivateCacheMaxEntries()](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Returns the maximum number of entries that the ACL evaluation result can be cached in the session.

[getPrivileges(Session, AclId)](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Returns a collection of privileges, which is granted in the specified ACL (AclId), based on the specified session.

[getPrivileges(Session, byte\[\])](oracle/security/xs/XSAccessController.md) - Static method in class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
Returns a collection of privileges, which is granted in the specified ACL (byte\[\]), based on the specified session.

[getSessionManager(DataSource, int, int)](oracle/security/xs/XSSessionManager.md) - Static method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Initializes an `XSSessionManager` using connections from the connection pool.

[getSessionManager(Connection, int, int)](oracle/security/xs/XSSessionManager.md) - Static method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Initializes an `XSSessionManager` using a dedicated connections.

[getUser()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Returns current session's user

[getUUID()](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Retrieves the `UUID` of the `Principal`.

[getValue()](oracle/security/xs/AttributeValue.md) - Method in class oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
Returns the attribute value.

[getValue()](oracle/security/xs/SessionNamespaceAttribute.md) - Method in interface oracle.security.xs.[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md)
Returns the attribute value.

## I

[InvalidSessionException](oracle/security/xs/InvalidSessionException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown on any session operations when the session is not valid.

[InvalidSessionException()](oracle/security/xs/InvalidSessionException.md) - Constructor for exception oracle.security.xs.[InvalidSessionException](oracle/security/xs/InvalidSessionException.md)
 

[InvalidSessionException(String)](oracle/security/xs/InvalidSessionException.md) - Constructor for exception oracle.security.xs.[InvalidSessionException](oracle/security/xs/InvalidSessionException.md)
 

[InvalidSessionException(Throwable)](oracle/security/xs/InvalidSessionException.md) - Constructor for exception oracle.security.xs.[InvalidSessionException](oracle/security/xs/InvalidSessionException.md)
 

[InvalidSessionException(String, Throwable)](oracle/security/xs/InvalidSessionException.md) - Constructor for exception oracle.security.xs.[InvalidSessionException](oracle/security/xs/InvalidSessionException.md)
 

[InvalidXSAttributeException](oracle/security/xs/InvalidXSAttributeException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown after an attempt to reference an invalid namespace attribute.

[InvalidXSAttributeException()](oracle/security/xs/InvalidXSAttributeException.md) - Constructor for exception oracle.security.xs.[InvalidXSAttributeException](oracle/security/xs/InvalidXSAttributeException.md)
 

[InvalidXSAttributeException(String)](oracle/security/xs/InvalidXSAttributeException.md) - Constructor for exception oracle.security.xs.[InvalidXSAttributeException](oracle/security/xs/InvalidXSAttributeException.md)
 

[InvalidXSNamespaceException](oracle/security/xs/InvalidXSNamespaceException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown after an attempt is made to reference an invalid namespace.

[InvalidXSNamespaceException()](oracle/security/xs/InvalidXSNamespaceException.md) - Constructor for exception oracle.security.xs.[InvalidXSNamespaceException](oracle/security/xs/InvalidXSNamespaceException.md)
 

[InvalidXSNamespaceException(String)](oracle/security/xs/InvalidXSNamespaceException.md) - Constructor for exception oracle.security.xs.[InvalidXSNamespaceException](oracle/security/xs/InvalidXSNamespaceException.md)
 

[InvalidXSUserException](oracle/security/xs/InvalidXSUserException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown in any session operations when the specified user is invalid.

[InvalidXSUserException()](oracle/security/xs/InvalidXSUserException.md) - Constructor for exception oracle.security.xs.[InvalidXSUserException](oracle/security/xs/InvalidXSUserException.md)
 

[InvalidXSUserException(String)](oracle/security/xs/InvalidXSUserException.md) - Constructor for exception oracle.security.xs.[InvalidXSUserException](oracle/security/xs/InvalidXSUserException.md)
 

[InvalidXSUserException(Throwable)](oracle/security/xs/InvalidXSUserException.md) - Constructor for exception oracle.security.xs.[InvalidXSUserException](oracle/security/xs/InvalidXSUserException.md)
 

[isAnonymous()](oracle/security/xs/ExternalUser.md) - Method in class oracle.security.xs.[ExternalUser](oracle/security/xs/ExternalUser.md)
Indicates if the current user is anonymous.

[isAnonymous()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Determines if this session user is anonymous.

[isAttached()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Determines if this session is attached to a `Connection`.

[isRoleEnabled(String)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Tests if the specified role is enabled in this user's session.

[isTrusted()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Determins if the current session is in trusted mode.

## N

[NamespaceValue](oracle/security/xs/NamespaceValue.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents a namespace and its attributes, which are used in session namespace operations.

[NamespaceValue(String, Collection\<AttributeValue\>)](oracle/security/xs/NamespaceValue.md) - Constructor for class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
Creates a namespace with the specified name and attributes.

[NotAttachedException](oracle/security/xs/NotAttachedException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown if a session operation is called without being attached.

[NotAttachedException()](oracle/security/xs/NotAttachedException.md) - Constructor for exception oracle.security.xs.[NotAttachedException](oracle/security/xs/NotAttachedException.md)
Constructs a new `NotAttachException`.

[NotAttachedException(String)](oracle/security/xs/NotAttachedException.md) - Constructor for exception oracle.security.xs.[NotAttachedException](oracle/security/xs/NotAttachedException.md)
Constructs a new `NotAttachException`.

## O

[oracle.security.xs](oracle/security/xs/package-summary.md) - package oracle.security.xs
Provides classes to access Fusion Security functions from java Middle Tier.

## P

[Principal](oracle/security/xs/Principal.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents a `Principal` entity, such as a `Role` or a `User`.

[Principal()](oracle/security/xs/Principal.md) - Constructor for class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Constructs a new `Principal`.

[Principal(String)](oracle/security/xs/Principal.md) - Constructor for class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Constructs a new `Principal` with the specified name.

## R

[resetAttribute(String)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Resets the specified attribute in the namespace to its default value.

[resetAttribute(SessionNamespace, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Resets the specified attribute in the namespace to its default value.

[Role](oracle/security/xs/Role.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents a type of principal that can be associated with a group of users.

[Role()](oracle/security/xs/Role.md) - Constructor for class oracle.security.xs.[Role](oracle/security/xs/Role.md)
Constructs a `Role` object.

[Role(String, String, long)](oracle/security/xs/Role.md) - Constructor for class oracle.security.xs.[Role](oracle/security/xs/Role.md)
Constructs an `Role` object from a name, a `UUID` and a `DBID`.

[Role(String, String)](oracle/security/xs/Role.md) - Constructor for class oracle.security.xs.[Role](oracle/security/xs/Role.md)
Constructs an `Role` object from a name and a `UUID`.

[Role(String, long)](oracle/security/xs/Role.md) - Constructor for class oracle.security.xs.[Role](oracle/security/xs/Role.md)
Constructs an `Role` object from a name and a `DBID`.

## S

[saveSession(Session)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Saves the specified session leaving it attached.

[Session](oracle/security/xs/Session.md) - Interface in [oracle.security.xs](oracle/security/xs/package-summary.md)
This interface represents an application security context that encapsulates user, role, and namespace.

[SessionNamespace](oracle/security/xs/SessionNamespace.md) - Interface in [oracle.security.xs](oracle/security/xs/package-summary.md)
This interface represents a set of name/value (`SessionNamespaceAttibute`) pairs associated with `Session`, which are commonly used to record application state, user profile, and so on.

[SessionNamespace.ATTR_EVENT_TYPE](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md) - Enum in [oracle.security.xs](oracle/security/xs/package-summary.md)
The list of possible events an attribute can have.

[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md) - Interface in [oracle.security.xs](oracle/security/xs/package-summary.md)
This interface represents a name/value pair that is stored as an attribute in the session namespace ( `SessionNamespace` ).

[SessionNamespaceException](oracle/security/xs/SessionNamespaceException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown when a generic error happens on namespace operation.

[SessionNamespaceException(String)](oracle/security/xs/SessionNamespaceException.md) - Constructor for exception oracle.security.xs.[SessionNamespaceException](oracle/security/xs/SessionNamespaceException.md)
 

[setAttribute(String, String)](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Sets the attribute for a session namespace with the specified name and value

[setAttribute(SessionNamespace, String, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the attribute for a session namespace with the specified name and value The dispatcher needs to have the privilege to set the attribute on the given namespace

[setAttributes(List\<AttributeValue\>)](oracle/security/xs/NamespaceValue.md) - Method in class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
Sets the list of attributes

[setCacheMaxIdleTime(int)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the maximum number of minutes for which the cache can remain without any activity.

[setCacheMaxSize(long)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the size of the cache on the middle tier, in bytes.

[setCookie(Session, String)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the cookie for the session

[setInactivityTimeout(Session, int)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the inactivity timeout for the session in minutes.

[setNamespace(String)](oracle/security/xs/NamespaceValue.md) - Method in class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
set namespace name

[setPrivateCacheMaxEntries(int)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the maximum number of entries that the ACL evaluation result can be cached in the session.

[setValue(String)](oracle/security/xs/AttributeValue.md) - Method in class oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
Sets the attribute value

[setWaterMark(float, float)](oracle/security/xs/XSSessionManager.md) - Method in class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
Sets the high and low watermarks for the cache.

[switchUser(String, Collection\<NamespaceValue\>)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Changes the session user.

[switchUserKeepState(String, Collection\<NamespaceValue\>)](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
Changes the session user and retains session state (Namespace).

## T

[toString()](oracle/security/xs/AttributeValue.md) - Method in class oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
 

[toString()](oracle/security/xs/NamespaceValue.md) - Method in class oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
 

[toString()](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Returns a string representation of the `Principal`.

[toString()](oracle/security/xs/Session.md) - Method in interface oracle.security.xs.[Session](oracle/security/xs/Session.md)
 

[toString()](oracle/security/xs/SessionNamespace.md) - Method in interface oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
Returns a string representation of the namespace

[toString()](oracle/security/xs/SessionNamespaceAttribute.md) - Method in interface oracle.security.xs.[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md)
Returns a string representation of the `SessionNamespaceAttribute`.

[toString()](oracle/security/xs/XSSessionManagerException.md) - Method in exception oracle.security.xs.[XSSessionManagerException](oracle/security/xs/XSSessionManagerException.md)
Returns a string representation of the `XSSessionManagerException`.

## U

[User](oracle/security/xs/User.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents a user, which is a type of principal.

[User()](oracle/security/xs/User.md) - Constructor for class oracle.security.xs.[User](oracle/security/xs/User.md)
Constructs a `User` object.

[User(String)](oracle/security/xs/User.md) - Constructor for class oracle.security.xs.[User](oracle/security/xs/User.md)
Constructs a `User` object with the specified name.

[User(String, String, long)](oracle/security/xs/User.md) - Constructor for class oracle.security.xs.[User](oracle/security/xs/User.md)
Constructs a `User` object with the specified name, UUID and DBID.

[User(String, String)](oracle/security/xs/User.md) - Constructor for class oracle.security.xs.[User](oracle/security/xs/User.md)
Constructs a `User` object with the specified name and UUID.

## V

[validate()](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Tests whether the object is valid or not.

[valueOf(String)](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md) - Static method in enum oracle.security.xs.[SessionNamespace.ATTR_EVENT_TYPE](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md)
Returns the enum constant of this type with the specified name.

[values()](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md) - Static method in enum oracle.security.xs.[SessionNamespace.ATTR_EVENT_TYPE](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md)
Returns an array containing the constants of this enum type, in the order they are declared.

[verify(String, String, long)](oracle/security/xs/Principal.md) - Method in class oracle.security.xs.[Principal](oracle/security/xs/Principal.md)
Tests whether the object is the same as specified

## X

[XSAccessController](oracle/security/xs/XSAccessController.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class provides authorization functions to check the privilege on the ACL based on the session.

[XSAccessController()](oracle/security/xs/XSAccessController.md) - Constructor for class oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
 

[XSAuthenticationModule](oracle/security/xs/XSAuthenticationModule.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class provides authentication functions to verify the user credentials against the Database.

[XSAuthenticationModule()](oracle/security/xs/XSAuthenticationModule.md) - Constructor for class oracle.security.xs.[XSAuthenticationModule](oracle/security/xs/XSAuthenticationModule.md)
 

[XSException](oracle/security/xs/XSException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Base exception class and a wrapper for server-side error.

[XSException()](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new `XSException`.

[XSException(String)](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new XSException with the specified exception message.

[XSException(Throwable)](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new XSException with the specified cause of the exception.

[XSException(String, Throwable)](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new XSException with the specified exception message and cause of exception.

[XSException(String, Object\[\], Throwable)](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new XSException with the specified error key, parameters, and cause of error.

[XSException(String, Object\[\])](oracle/security/xs/XSException.md) - Constructor for exception oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
Creates a new XSException with the specified error key and parameters.

[XSPrincipalException](oracle/security/xs/XSPrincipalException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown when creating a principal object with invalid values.

[XSPrincipalException(String)](oracle/security/xs/XSPrincipalException.md) - Constructor for exception oracle.security.xs.[XSPrincipalException](oracle/security/xs/XSPrincipalException.md)
 

[XSPrincipalException(Throwable)](oracle/security/xs/XSPrincipalException.md) - Constructor for exception oracle.security.xs.[XSPrincipalException](oracle/security/xs/XSPrincipalException.md)
 

[XSSecurityPermission](oracle/security/xs/XSSecurityPermission.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class represents a Java permission that extends the `BasicPermission` class to authorize the execution of critical XS methods in the oracle.security.xs package.

[XSSecurityPermission(String)](oracle/security/xs/XSSecurityPermission.md) - Constructor for class oracle.security.xs.[XSSecurityPermission](oracle/security/xs/XSSecurityPermission.md)
Constructs a new XSSecurityPermission from the specified name.

[XSSessionException](oracle/security/xs/XSSessionException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
 

[XSSessionException()](oracle/security/xs/XSSessionException.md) - Constructor for exception oracle.security.xs.[XSSessionException](oracle/security/xs/XSSessionException.md)
 

[XSSessionManager](oracle/security/xs/XSSessionManager.md) - Class in [oracle.security.xs](oracle/security/xs/package-summary.md)
This class provides functions to manage the `Session`, inlcude session life cycle (createSession, attachSession, detachSessiona and destroySession), session attribute (cookie, inactivity timeout) and session namespace.

[XSSessionManager()](oracle/security/xs/XSSessionManager.md) - Constructor for class oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)
 

[XSSessionManagerException](oracle/security/xs/XSSessionManagerException.md) - Exception in [oracle.security.xs](oracle/security/xs/package-summary.md)
Exception thrown when the session manager is not working.

[XSSessionManagerException(String)](oracle/security/xs/XSSessionManagerException.md) - Constructor for exception oracle.security.xs.[XSSessionManagerException](oracle/security/xs/XSSessionManagerException.md)
Creates a new XSSessionManagerException with the specified exception message.

A C D E G I N O P R S T U V X 

Skip navigation links

- [Package](oracle/security/xs/package-summary.md)
- Class
- [Tree](oracle/security/xs/package-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
