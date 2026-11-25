Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NamespaceException.md)**
- **[Next Class](Node.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr**

## **Interface NamespaceRegistry**

- **All Known Subinterfaces:**
  **[OracleNamespaceRegistry](../../oracle/jcr/OracleNamespaceRegistry.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NamespaceRegistry

  **`NamespaceRegistry` represents the global persistent namespace registry of the JCR Repository.**
  **See Also:**
  **[`Workspace.getNamespaceRegistry()`](Workspace.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type    | Method and Description                                                                                                                                                        |
    |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`   | `getPrefix``(java.lang.String uri)`<br>Returns the prefix to which the given URI is mapped                                                                                    |
    | `java.lang.String[]` | `getPrefixes``()`<br>Returns an array holding all currently registered prefixes.                                                                                              |
    | `java.lang.String`   | `getURI``(java.lang.String prefix)`<br>Returns the URI to which the given prefix is mapped.                                                                                   |
    | `java.lang.String[]` | `getURIs``()`<br>Returns an array holding all currently registered URIs.                                                                                                      |
    | `void`               | `registerNamespace``(java.lang.String prefix, java.lang.String uri)`<br>Sets a one-to-one mapping between prefix and URI in the global namespace registry of this repository. |
    | `void`               | `unregisterNamespace``(java.lang.String prefix)`<br>Removes a namespace mapping from the registry.                                                                            |

<!-- -->

- - ### Method Detail

    - #### registerNamespace

          void registerNamespace(java.lang.String prefix,
                                 java.lang.String uri)
                          throws NamespaceException,
                                 UnsupportedRepositoryOperationException,
                                 AccessDeniedException,
                                 RepositoryException

      Sets a one-to-one mapping between prefix and URI in the global namespace registry of this repository. Assigning a new prefix to a URI that already exists in the namespace registry erases the old prefix. In general this can almost always be done, though an implementation is free to prevent particular remappings by throwing a `NamespaceException`.
      On the other hand, taking a prefix that is already assigned to a URI and re-assigning it to a new URI in effect unregisters that URI. Therefore, the same restrictions apply to this operation as to `NamespaceRegistry.unregisterNamespace`:

      - Attempting to re-assign a built-in prefix (`jcr`, `nt`, `mix`, `sv`, `xml`, or the empty prefix) to a new URI will throw a `NamespaceException`.
      - Attempting to re-assign a prefix that is currently assigned to a URI that is present in content (either within an item name or within the value of a `NAME` or `PATH` property) will throw a `NamespaceException`. This includes prefixes in use within in-content node type definitions.
      - Attempting to register a namespace with a prefix that begins with the characters "`xml`" (in any combination of case) will throw a `NamespaceException`.
      - An implementation may prevent the re-assignment of any other namespace prefixes for implementation-specific reasons by throwing a `NamespaceException`.

      In a level 1 implementation, this method always throws an `UnsupportedRepositoryOperationException`.
      If the session associated with the `Workspace` object through which this registry was acquired does not have sufficient permissions to register the namespace an `AccessDeniedException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `prefix` - The prefix to be mapped.

      `uri` - The URI to be mapped.

      Throws:
      [`NamespaceException`](NamespaceException.md) - if an illegal attempt is made to register a mapping.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - in a level 1 implementation

      [`AccessDeniedException`](AccessDeniedException.md) - if the session associated with the `Workspace` object through which this registry was acquired does not have sufficient permissions to register the namespace.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### unregisterNamespace

          void unregisterNamespace(java.lang.String prefix)
                            throws NamespaceException,
                                   UnsupportedRepositoryOperationException,
                                   AccessDeniedException,
                                   RepositoryException

      Removes a namespace mapping from the registry. The following restriction apply:
      - Attempting to unregister a built-in namespace (`jcr`, `nt`, `mix`, `sv`, `xml` or the empty namespace) will throw a `NamespaceException`.
      - Attempting to unregister a namespace that is currently present in content (either within an item name or within the value of a `NAME` or `PATH` property) will throw a `NamespaceException`. This includes prefixes in use within in-content node type definitions.
      - An attempt to unregister a namespace that is not currently registered will throw a `NamespaceException`.
      - An implementation may prevent the unregistering of any other namespace for implementation-specific reasons by throwing a `NamespaceException`.

      In a level 1 implementation, this method always throws an `UnsupportedRepositoryOperationException`.
      If the session associated with the `Workspace` object through which this registry was acquired does not have sufficient permissions to unregister the namespace an `AccessDeniedException` is thrown.

      A `RepositoryException` is thrown if another error occurs.

      Parameters:
      `prefix` - The prefix of the mapping to be removed.

      Throws:
      [`NamespaceException`](NamespaceException.md) - if an illegal attempt is made to remove a mapping.

      [`UnsupportedRepositoryOperationException`](UnsupportedRepositoryOperationException.md) - in a level 1 implementation

      [`AccessDeniedException`](AccessDeniedException.md) - if the session associated with the `Workspace` object through which this registry was acquired does not have sufficient permissions to unregister the namespace.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getPrefixes

          java.lang.String[] getPrefixes()
                                  throws RepositoryException

      Returns an array holding all currently registered prefixes.
      Returns:
      a string array

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getURIs

          java.lang.String[] getURIs()
                              throws RepositoryException

      Returns an array holding all currently registered URIs.
      Returns:
      a string array

      Throws:
      [`RepositoryException`](RepositoryException.md) - if an error occurs.

    <!-- -->

    - #### getURI

          java.lang.String getURI(java.lang.String prefix)
                           throws NamespaceException,
                                  RepositoryException

      Returns the URI to which the given prefix is mapped.
      Parameters:
      `prefix` - a string

      Returns:
      a string

      Throws:
      [`NamespaceException`](NamespaceException.md) - if the prefix is unknown.

      [`RepositoryException`](RepositoryException.md) - is another error occurs

    <!-- -->

    - #### getPrefix

          java.lang.String getPrefix(java.lang.String uri)
                              throws NamespaceException,
                                     RepositoryException

      Returns the prefix to which the given URI is mapped
      Parameters:
      `uri` - a string

      Returns:
      a string

      Throws:
      [`NamespaceException`](NamespaceException.md) - if the URI is unknown.

      [`RepositoryException`](RepositoryException.md) - is another error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NamespaceException.md)**
- **[Next Class](Node.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
