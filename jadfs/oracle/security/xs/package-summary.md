Skip navigation links

- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev Package
- Next Package

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.security.xs

Provides classes to access Fusion Security functions from java Middle Tier.

See: Description

- **Interface Summary**

  | Interface                                                 | Description                                                                                                                                                                               |
  |-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Session](Session.md)                                     | This interface represents an application security context that encapsulates user, role, and namespace.                                                                                    |
  | [SessionNamespace](SessionNamespace.md)                   | This interface represents a set of name/value (`SessionNamespaceAttibute`) pairs associated with `Session`, which are commonly used to record application state, user profile, and so on. |
  | [SessionNamespaceAttribute](SessionNamespaceAttribute.md) | This interface represents a name/value pair that is stored as an attribute in the session namespace ( `SessionNamespace` ).                                                               |

- **Class Summary**

  | Class                                               | Description                                                                                                                                                                                                                |
  |-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AclId](AclId.md)                                   | This class represents multiple ACL IDs in either long or raw form.                                                                                                                                                         |
  | [AttributeValue](AttributeValue.md)                 | This class provides a name/value pair that is stored in session namespace.                                                                                                                                                 |
  | [ExternalRole](ExternalRole.md)                     | This class represents externally managed roles used in a session.                                                                                                                                                          |
  | [ExternalUser](ExternalUser.md)                     | This class represents externally managed users used in a session.                                                                                                                                                          |
  | [NamespaceValue](NamespaceValue.md)                 | This class represents a namespace and its attributes, which are used in session namespace operations.                                                                                                                      |
  | [Principal](Principal.md)                           | This class represents a `Principal` entity, such as a `Role` or a `User`.                                                                                                                                                  |
  | [Role](Role.md)                                     | This class represents a type of principal that can be associated with a group of users.                                                                                                                                    |
  | [User](User.md)                                     | This class represents a user, which is a type of principal.                                                                                                                                                                |
  | [XSAccessController](XSAccessController.md)         | This class provides authorization functions to check the privilege on the ACL based on the session.                                                                                                                        |
  | [XSAuthenticationModule](XSAuthenticationModule.md) | This class provides authentication functions to verify the user credentials against the Database.                                                                                                                          |
  | [XSSecurityPermission](XSSecurityPermission.md)     | This class represents a Java permission that extends the `BasicPermission` class to authorize the execution of critical XS methods in the oracle.security.xs package.                                                      |
  | [XSSessionManager](XSSessionManager.md)             | This class provides functions to manage the `Session`, inlcude session life cycle (createSession, attachSession, detachSessiona and destroySession), session attribute (cookie, inactivity timeout) and session namespace. |

- **Enum Summary**

  | Enum                                                                    | Description                                        |
  |-------------------------------------------------------------------------|----------------------------------------------------|
  | [SessionNamespace.ATTR_EVENT_TYPE](SessionNamespace.ATTR_EVENT_TYPE.md) | The list of possible events an attribute can have. |

- **Exception Summary**

  | Exception                                                     | Description                                                                    |
  |---------------------------------------------------------------|--------------------------------------------------------------------------------|
  | [AccessDeniedException](AccessDeniedException.md)             | Exception thrown when an operation fails due to insufficient privilege.        |
  | [InvalidSessionException](InvalidSessionException.md)         | Exception thrown on any session operations when the session is not valid.      |
  | [InvalidXSAttributeException](InvalidXSAttributeException.md) | Exception thrown after an attempt to reference an invalid namespace attribute. |
  | [InvalidXSNamespaceException](InvalidXSNamespaceException.md) | Exception thrown after an attempt is made to reference an invalid namespace.   |
  | [InvalidXSUserException](InvalidXSUserException.md)           | Exception thrown in any session operations when the specified user is invalid. |
  | [NotAttachedException](NotAttachedException.md)               | Exception thrown if a session operation is called without being attached.      |
  | [SessionNamespaceException](SessionNamespaceException.md)     | Exception thrown when a generic error happens on namespace operation.          |
  | [XSException](XSException.md)                                 | Base exception class and a wrapper for server-side error.                      |
  | [XSPrincipalException](XSPrincipalException.md)               | Exception thrown when creating a principal object with invalid values.         |
  | [XSSessionException](XSSessionException.md)                   |                                                                                |
  | [XSSessionManagerException](XSSessionManagerException.md)     | Exception thrown when the session manager is not working.                      |

## Package oracle.security.xs Description

Provides classes to access Fusion Security functions from java Middle Tier.

Skip navigation links

- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev Package
- Next Package

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
