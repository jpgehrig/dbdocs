Skip navigation links

- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Hierarchy For Package oracle.security.xs

## Class Hierarchy

- java.lang.Object
  - oracle.security.xs.[AclId](AclId.md)
  - oracle.security.xs.[AttributeValue](AttributeValue.md)
  - oracle.security.xs.[NamespaceValue](NamespaceValue.md)
  - java.security.Permission (implements java.security.Guard, java.io.Serializable)
    - java.security.BasicPermission (implements java.io.Serializable)
      - oracle.security.xs.[XSSecurityPermission](XSSecurityPermission.md)
  - oracle.security.xs.[Principal](Principal.md) (implements java.security.Principal)
    - oracle.security.xs.[ExternalRole](ExternalRole.md)
    - oracle.security.xs.[Role](Role.md)
    - oracle.security.xs.[User](User.md)
      - oracle.security.xs.[ExternalUser](ExternalUser.md)
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.security.xs.[XSException](XSException.md)
        - oracle.security.xs.[AccessDeniedException](AccessDeniedException.md)
        - oracle.security.xs.[InvalidSessionException](InvalidSessionException.md)
        - oracle.security.xs.[InvalidXSAttributeException](InvalidXSAttributeException.md)
        - oracle.security.xs.[InvalidXSNamespaceException](InvalidXSNamespaceException.md)
        - oracle.security.xs.[InvalidXSUserException](InvalidXSUserException.md)
        - oracle.security.xs.[NotAttachedException](NotAttachedException.md)
        - oracle.security.xs.[SessionNamespaceException](SessionNamespaceException.md)
        - oracle.security.xs.[XSPrincipalException](XSPrincipalException.md)
        - oracle.security.xs.[XSSessionException](XSSessionException.md)
        - oracle.security.xs.[XSSessionManagerException](XSSessionManagerException.md)
  - oracle.security.xs.[XSAccessController](XSAccessController.md)
  - oracle.security.xs.[XSAuthenticationModule](XSAuthenticationModule.md)
  - oracle.security.xs.[XSSessionManager](XSSessionManager.md)

## Interface Hierarchy

- oracle.security.xs.[Session](Session.md)
- oracle.security.xs.[SessionNamespace](SessionNamespace.md)
- oracle.security.xs.[SessionNamespaceAttribute](SessionNamespaceAttribute.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.security.xs.[SessionNamespace.ATTR_EVENT_TYPE](SessionNamespace.ATTR_EVENT_TYPE.md)

Skip navigation links

- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
