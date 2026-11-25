Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NSName.md)**
- **[Next Class](oraxml.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Interface NSResolver**

- **All Known Implementing Classes:**
  **[XMLDocument](XMLDocument.md), [XMLDocumentFragment](XMLDocumentFragment.md), [XMLElement](XMLElement.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NSResolver

  **This interface provides support for resolving Namespaces**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                     |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `resolveNamespacePrefix``(java.lang.String prefix)`<br>Find the namespace definition in scope for a given namespace prefix |

<!-- -->

- - ### Method Detail

    - #### resolveNamespacePrefix

          java.lang.String resolveNamespacePrefix(java.lang.String prefix)

      Find the namespace definition in scope for a given namespace prefix
      Parameters:
      `prefix` - Namespace prefix to be resolved

      Returns:
      the resolved Namespace (null, if prefix could not be resolved)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](NSName.md)**
- **[Next Class](oraxml.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
