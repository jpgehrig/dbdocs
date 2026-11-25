Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DOMException.md)**
- **[Next Class](DOMImplementationList.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**org.w3c.dom**

## **Interface DOMImplementation**

- **All Known Implementing Classes:**
  **[XDBDomImplementation](../../../oracle/xdb/dom/XDBDomImplementation.md), [XMLDOMImplementation](../../../oracle/xml/parser/v2/XMLDOMImplementation.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMImplementation

  **The `DOMImplementation` interface provides a number of methods for performing operations that are independent of any particular instance of the document object model.**
  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                              |
    |-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Document`](Document.md)         | `createDocument``(java.lang.String namespaceURI, java.lang.String qualifiedName, `[`DocumentType`](DocumentType.md)` doctype)`<br>Creates an XML `Document` object of the specified type with its document element. |
    | [`DocumentType`](DocumentType.md) | `createDocumentType``(java.lang.String qualifiedName, java.lang.String publicId, java.lang.String systemId)`<br>Creates an empty `DocumentType` node.                                                               |
    | `boolean`                         | `hasFeature``(java.lang.String feature, java.lang.String version)`<br>Test if the DOM implementation implements a specific feature.                                                                                 |

<!-- -->

- - ### Method Detail

    - #### hasFeature

          boolean hasFeature(java.lang.String feature,
                             java.lang.String version)

      Test if the DOM implementation implements a specific feature.
      Parameters:
      `feature` - The name of the feature to test (case-insensitive). The values used by DOM features are defined throughout the DOM Level 2 specifications and listed in the section. The name must be an XML name. To avoid possible conflicts, as a convention, names referring to features defined outside the DOM specification should be made unique by reversing the name of the Internet domain name of the person (or the organization that the person belongs to) who defines the feature, component by component, and using this as a prefix. For instance, the W3C SVG Working Group defines the feature "org.w3c.dom.svg".

      `version` - This is the version number of the feature to test. In Level 2, the string can be either "2.0" or "1.0". If the version is not specified, supporting any version of the feature causes the method to return `true`.

      Returns:
      `true` if the feature is implemented in the specified version, `false` otherwise.

    <!-- -->

    - #### createDocumentType

          DocumentType createDocumentType(java.lang.String qualifiedName,
                                          java.lang.String publicId,
                                          java.lang.String systemId)
                                   throws DOMException

      Creates an empty `DocumentType` node. Entity declarations and notations are not made available. Entity reference expansions and default attribute additions do not occur. It is expected that a future version of the DOM will provide a way for populating a `DocumentType`.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `qualifiedName` - The qualified name of the document type to be created.

      `publicId` - The external subset public identifier.

      `systemId` - The external subset system identifier.

      Returns:
      A new `DocumentType` node with `Node.ownerDocument` set to `null`.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed.

      Since:
      DOM Level 2

    <!-- -->

    - #### createDocument

          Document createDocument(java.lang.String namespaceURI,
                                  java.lang.String qualifiedName,
                                  DocumentType doctype)
                           throws DOMException

      Creates an XML `Document` object of the specified type with its document element. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the document element to create.

      `qualifiedName` - The qualified name of the document element to be created.

      `doctype` - The type of document to be created or `null`. When `doctype` is not `null`, its `Node.ownerDocument` attribute is set to the document being created.

      Returns:
      A new `Document` object.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, or if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace" .
      WRONG_DOCUMENT_ERR: Raised if `doctype` has already been used with a different document or was created from a different implementation.

      Since:
      DOM Level 2

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](DOMException.md)**
- **[Next Class](DOMImplementationList.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
