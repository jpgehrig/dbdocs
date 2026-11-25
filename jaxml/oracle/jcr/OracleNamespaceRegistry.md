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

- **[Prev Class](CredentialsProvider.md)**
- **[Next Class](OracleRepository.md)**

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

**oracle.jcr**

## **Interface OracleNamespaceRegistry**

- **All Superinterfaces:**
  **[NamespaceRegistry](../../javax/jcr/NamespaceRegistry.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **OracleNamespaceRegistry is the JCR namespace registry.**
  **The namespace registry is cached by the OracleNamespaceRegistry object. The cache is automatically refreshed each time `registerNamespace` or `unregisterNamespace` is called on the OracleNamespaceRegistry object. Call `refresh` to explicitly refresh the cache.**

  **Refer to XDBRepositoryConfiguration for further information on how the JCR namespace registry is stored by the XML DB Content Connector.**

  **
  **

      public interface OracleNamespaceRegistry
      extends NamespaceRegistry

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type | Method and Description                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `void`            | `refresh``()`<br>Deprecated. <br>Refresh the in-memory copy of the JCR namespace registry. |

    - ### Methods inherited from interface javax.jcr.[NamespaceRegistry](../../javax/jcr/NamespaceRegistry.md)

      [`getPrefix`](../../javax/jcr/NamespaceRegistry.md)`, `[`getPrefixes`](../../javax/jcr/NamespaceRegistry.md)`, `[`getURI`](../../javax/jcr/NamespaceRegistry.md)`, `[`getURIs`](../../javax/jcr/NamespaceRegistry.md)`, `[`registerNamespace`](../../javax/jcr/NamespaceRegistry.md)`, `[`unregisterNamespace`](../../javax/jcr/NamespaceRegistry.md)

<!-- -->

- - ### Method Detail

    - #### refresh

          void refresh()
                throws RepositoryException

      Deprecated. 
      Refresh the in-memory copy of the JCR namespace registry.
      Throws:
      [`RepositoryException`](../../javax/jcr/RepositoryException.md) - if the operation fails

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

- **[Prev Class](CredentialsProvider.md)**
- **[Next Class](OracleRepository.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
