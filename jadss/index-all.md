Skip navigation links

- [Package](oracle/security/xs/ee/session/package-summary.md)
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

A C D E G H I N O S T W 

## A

[ApplicationSessionException](oracle/security/xs/ee/session/ApplicationSessionException.md) - Exception in [oracle.security.xs.ee.session](oracle/security/xs/ee/session/package-summary.md)
Exception thrown from RAS session service APIs.

[ApplicationSessionException(Throwable)](oracle/security/xs/ee/session/ApplicationSessionException.md) - Constructor for exception oracle.security.xs.ee.session.[ApplicationSessionException](oracle/security/xs/ee/session/ApplicationSessionException.md)
Constructor with the specified cause.

[ApplicationSessionException(String, Throwable)](oracle/security/xs/ee/session/ApplicationSessionException.md) - Constructor for exception oracle.security.xs.ee.session.[ApplicationSessionException](oracle/security/xs/ee/session/ApplicationSessionException.md)
Constructor with the specified detail message and cause.

[ApplicationSessionException(String)](oracle/security/xs/ee/session/ApplicationSessionException.md) - Constructor for exception oracle.security.xs.ee.session.[ApplicationSessionException](oracle/security/xs/ee/session/ApplicationSessionException.md)
Constructor with the specified detail message.

[ApplicationSessionException()](oracle/security/xs/ee/session/ApplicationSessionException.md) - Constructor for exception oracle.security.xs.ee.session.[ApplicationSessionException](oracle/security/xs/ee/session/ApplicationSessionException.md)
Default constructor.

[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md) - Class in [oracle.security.xs.ee.session](oracle/security/xs/ee/session/package-summary.md)
Exposed RAS Session Service APIs.

[ApplicationSessionService()](oracle/security/xs/ee/session/ApplicationSessionService.md) - Constructor for class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
 

[ATTACH_ACTION](oracle/security/xs/ee/session/SessionCodePermission.md) - Static variable in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
 

[attachSession(Connection)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Attaches the current user's application session to the given connection.

[attachSessionPrivileged(Connection, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Attaches the current user's application session to the given connection, and enable the given dynamic role in the attached session.

## C

[checkPrivilege(Connection, byte\[\], String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Checks the privielge on the attached session.

[createNamespace(Connection, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Creates the namespace on the current user's application session.

## D

[deleteNamespace(Connection, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Deletes the namespace on the current user's application session.

[deleteNamespaceAttribute(Connection, String, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Deletes the namespace attribute on the current user's application session.

[destroySession(Connection)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Destroys the current user's application session.

[detachSession(Connection)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Detaches the current user's application session from the given connection.

## E

[equals(Object)](oracle/security/xs/ee/session/SessionCodePermission.md) - Method in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Checks two Permission objects for equality.

## G

[getActions()](oracle/security/xs/ee/session/SessionCodePermission.md) - Method in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Returns the actions of this Permission object.

[getNamespaceAttribute(String, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Gets the namespace attribute from the current user's application session.

## H

[hashCode()](oracle/security/xs/ee/session/SessionCodePermission.md) - Method in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Returns the hash code value of this Permission object.

## I

[implies(Permission)](oracle/security/xs/ee/session/SessionCodePermission.md) - Method in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Checks to see if the current permission implies the given permission.

## N

[NamespaceNotFoundException](oracle/security/xs/ee/session/NamespaceNotFoundException.md) - Exception in [oracle.security.xs.ee.session](oracle/security/xs/ee/session/package-summary.md)
Exception thrown when the given namespace is not found.

[NamespaceNotFoundException(Throwable)](oracle/security/xs/ee/session/NamespaceNotFoundException.md) - Constructor for exception oracle.security.xs.ee.session.[NamespaceNotFoundException](oracle/security/xs/ee/session/NamespaceNotFoundException.md)
Constructor with the specified cause.

## O

[oracle.security.xs.ee.session](oracle/security/xs/ee/session/package-summary.md) - package oracle.security.xs.ee.session
 

## S

[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md) - Class in [oracle.security.xs.ee.session](oracle/security/xs/ee/session/package-summary.md)
Permission to protect session operation to be allowed only for certain trusted code.

[SessionCodePermission(String, String)](oracle/security/xs/ee/session/SessionCodePermission.md) - Constructor for class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Constructor with specified name and action.

[setNamespaceAttribute(Connection, String, String, String)](oracle/security/xs/ee/session/ApplicationSessionService.md) - Static method in class oracle.security.xs.ee.session.[ApplicationSessionService](oracle/security/xs/ee/session/ApplicationSessionService.md)
Sets the namespace attribute on the current user's application session.

## T

[toString()](oracle/security/xs/ee/session/SessionCodePermission.md) - Method in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
Returns a string description of this Permission object.

## W

[WILDCARD](oracle/security/xs/ee/session/SessionCodePermission.md) - Static variable in class oracle.security.xs.ee.session.[SessionCodePermission](oracle/security/xs/ee/session/SessionCodePermission.md)
 

A C D E G H I N O S T W 

Skip navigation links

- [Package](oracle/security/xs/ee/session/package-summary.md)
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- Index
- [Help](help-doc.md)

**Oracle® Database Real Application Security Session Service Java API Reference
Release 19c**
E96304-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
