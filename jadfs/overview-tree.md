Skip navigation links

- [Package](oracle/security/xs/package-summary.md)
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
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

# Hierarchy For All Packages

Package Hierarchies:

- [oracle.security.xs](oracle/security/xs/package-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.security.xs.[AclId](oracle/security/xs/AclId.md)
  - oracle.security.xs.[AttributeValue](oracle/security/xs/AttributeValue.md)
  - oracle.security.xs.[NamespaceValue](oracle/security/xs/NamespaceValue.md)
  - java.security.Permission (implements java.security.Guard, java.io.Serializable)
    - java.security.BasicPermission (implements java.io.Serializable)
      - oracle.security.xs.[XSSecurityPermission](oracle/security/xs/XSSecurityPermission.md)
  - oracle.security.xs.[Principal](oracle/security/xs/Principal.md) (implements java.security.Principal)
    - oracle.security.xs.[ExternalRole](oracle/security/xs/ExternalRole.md)
    - oracle.security.xs.[Role](oracle/security/xs/Role.md)
    - oracle.security.xs.[User](oracle/security/xs/User.md)
      - oracle.security.xs.[ExternalUser](oracle/security/xs/ExternalUser.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.security.xs.[XSException](oracle/security/xs/XSException.md)
        - oracle.security.xs.[AccessDeniedException](oracle/security/xs/AccessDeniedException.md)
        - oracle.security.xs.[InvalidSessionException](oracle/security/xs/InvalidSessionException.md)
        - oracle.security.xs.[InvalidXSAttributeException](oracle/security/xs/InvalidXSAttributeException.md)
        - oracle.security.xs.[InvalidXSNamespaceException](oracle/security/xs/InvalidXSNamespaceException.md)
        - oracle.security.xs.[InvalidXSUserException](oracle/security/xs/InvalidXSUserException.md)
        - oracle.security.xs.[NotAttachedException](oracle/security/xs/NotAttachedException.md)
        - oracle.security.xs.[SessionNamespaceException](oracle/security/xs/SessionNamespaceException.md)
        - oracle.security.xs.[XSPrincipalException](oracle/security/xs/XSPrincipalException.md)
        - oracle.security.xs.[XSSessionException](oracle/security/xs/XSSessionException.md)
        - oracle.security.xs.[XSSessionManagerException](oracle/security/xs/XSSessionManagerException.md)
  - oracle.security.xs.[XSAccessController](oracle/security/xs/XSAccessController.md)
  - oracle.security.xs.[XSAuthenticationModule](oracle/security/xs/XSAuthenticationModule.md)
  - oracle.security.xs.[XSSessionManager](oracle/security/xs/XSSessionManager.md)

## Interface Hierarchy

- oracle.security.xs.[Session](oracle/security/xs/Session.md)
- oracle.security.xs.[SessionNamespace](oracle/security/xs/SessionNamespace.md)
- oracle.security.xs.[SessionNamespaceAttribute](oracle/security/xs/SessionNamespaceAttribute.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.security.xs.[SessionNamespace.ATTR_EVENT_TYPE](oracle/security/xs/SessionNamespace.ATTR_EVENT_TYPE.md)

Skip navigation links

- [Package](oracle/security/xs/package-summary.md)
- Class
- Tree
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
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
