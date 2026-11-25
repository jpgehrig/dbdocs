Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Package**
- **[Next Package](lock/package-summary.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

# **Package javax.jcr**

**Content Repository API for Java (JCR 1.0) core**

**See: Description**

- **Interface Summary**

  | Interface                                   | Description                                                                                                                                                                                                                                                                                                                                                                                |
  |---------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Credentials](Credentials.md)               | Interface for all credentials that may be passed to the [`Repository.login(Credentials credentials, String workspaceName)`](Repository.md) method.                                                                                                                                                                                                                                         |
  | [ImportUUIDBehavior](ImportUUIDBehavior.md) | The possible actions specified by the `uuidBehavior` parameter in [`Workspace.importXML(java.lang.String, java.io.InputStream, int)`](Workspace.md), [`Session.importXML(java.lang.String, java.io.InputStream, int)`](Session.md), [`Workspace.getImportContentHandler(java.lang.String, int)`](Workspace.md) and [`Session.getImportContentHandler(java.lang.String, int)`](Session.md). |
  | [Item](Item.md)                             | The `Item` is the base interface of [`Node`](Node.md) and [`Property`](Property.md).                                                                                                                                                                                                                                                                                                       |
  | [ItemVisitor](ItemVisitor.md)               | This interface defines two signatures of the `visit` method; one taking a `Node`, the other a `Property`.                                                                                                                                                                                                                                                                                  |
  | [NamespaceRegistry](NamespaceRegistry.md)   | `NamespaceRegistry` represents the global persistent namespace registry of the JCR Repository.                                                                                                                                                                                                                                                                                             |
  | [Node](Node.md)                             | The `Node` interface represents a node in the hierarchy that makes up the repository.                                                                                                                                                                                                                                                                                                      |
  | [NodeIterator](NodeIterator.md)             | Allows easy iteration through a list of `Node`s with `nextNode` as well as a `skip` method inherited from `RangeIterator`.                                                                                                                                                                                                                                                                 |
  | [Property](Property.md)                     | A `Property` object represents the smallest granularity of content storage.                                                                                                                                                                                                                                                                                                                |
  | [PropertyIterator](PropertyIterator.md)     | Allows easy iteration through a list of `Property`s with `nextProperty` as well as a `skip` method.                                                                                                                                                                                                                                                                                        |
  | [RangeIterator](RangeIterator.md)           | Extends `Iterator` with the `skip`, `getSize` and `getPosition` methods.                                                                                                                                                                                                                                                                                                                   |
  | [Repository](Repository.md)                 | The entry point into the content repository.                                                                                                                                                                                                                                                                                                                                               |
  | [Session](Session.md)                       | The `Session` object provides read and (in level 2) write access to the content of a particular workspace in the repository.                                                                                                                                                                                                                                                               |
  | [Value](Value.md)                           | A generic holder for the value of a property.                                                                                                                                                                                                                                                                                                                                              |
  | [ValueFactory](ValueFactory.md)             | The `ValueFactory` object provides methods for the creation Value objects that can then be used to set properties.                                                                                                                                                                                                                                                                         |
  | [Workspace](Workspace.md)                   | The `Workspace` object represents a "view" of an actual repository workspace entity as seen through the authorization settings of its associated `Session`.                                                                                                                                                                                                                                |

- **Class Summary**

  | Class                                     | Description                                                                                                    |
  |-------------------------------------------|----------------------------------------------------------------------------------------------------------------|
  | [PropertyType](PropertyType.md)           | The property types supported by the JCR standard.                                                              |
  | [SimpleCredentials](SimpleCredentials.md) | `SimpleCredentials` implements the `Credentials` interface and represents simple user ID/password credentials. |

- **Exception Summary**

  | Exception                                                                             | Description                                                                                                                                                                                            |
  |---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AccessDeniedException](AccessDeniedException.md)                                     | Exception thrown by access-related methods.                                                                                                                                                            |
  | [InvalidItemStateException](InvalidItemStateException.md)                             | Exception thrown by the write methods of `Node` and `Property` and by save and refresh if an attempted change would conflict with a change to the persistent workspace made through another `Session`. |
  | [InvalidSerializedDataException](InvalidSerializedDataException.md)                   | Exception thrown by the deserialization methods of `Session` if the serialized data being input has an invalid format.                                                                                 |
  | [ItemExistsException](ItemExistsException.md)                                         | An exception thrown when an attempt is made to place an item in a position where another item already exists.                                                                                          |
  | [ItemNotFoundException](ItemNotFoundException.md)                                     | Exception thrown by methods of [`Item`](Item.md), [`Node`](Node.md) and [`Workspace`](Workspace.md) when an item is not found.                                                                         |
  | [LoginException](LoginException.md)                                                   | Exception thrown by [`Repository.login(Credentials, String)`](Repository.md) and [`Session.impersonate(Credentials)`](Session.md) if the specified credentials are invalid.                            |
  | [MergeException](MergeException.md)                                                   | Exception thrown by [`Node.merge(String srcWorkspace, boolean isDeep)`](Node.md).                                                                                                                      |
  | [NamespaceException](NamespaceException.md)                                           | Exception thrown by [`Session.setNamespacePrefix(String prefix, String uri)`](Session.md) if the specified `uri` is not registered in the [`NamespaceRegistry`](NamespaceRegistry.md)                  |
  | [NoSuchWorkspaceException](NoSuchWorkspaceException.md)                               | Exception thrown by [`Repository.login(Credentials, String)`](Repository.md) when a specific workspace is not found.                                                                                   |
  | [PathNotFoundException](PathNotFoundException.md)                                     | Exception thrown when no `Item` exists at the specified path or when the specified path implies intermediary `Node`s that do not exist.                                                                |
  | [ReferentialIntegrityException](ReferentialIntegrityException.md)                     | Exception thrown on referential integrity violation.                                                                                                                                                   |
  | [RepositoryException](RepositoryException.md)                                         | Main exception thrown by classes in this package.                                                                                                                                                      |
  | [UnsupportedRepositoryOperationException](UnsupportedRepositoryOperationException.md) | Thrown by methods that are not supported by a particluar implementation                                                                                                                                |
  | [ValueFormatException](ValueFormatException.md)                                       | Exception thrown when an attempt is made to assign a value to a property that has an invalid format, given the type of the property.                                                                   |

## Package javax.jcr Description

Content Repository API for Java (JCR 1.0) core

Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Package**
- **[Next Package](lock/package-summary.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
