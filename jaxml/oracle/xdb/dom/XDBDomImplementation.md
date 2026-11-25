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

- **[Prev Class](XDBDOMException.md)**
- **[Next Class](XDBDOMNotFoundErrException.md)**

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

**oracle.xdb.dom**

## **Class XDBDomImplementation**

- **java.lang.Object**

- - **oracle.xdb.dom.XDBDomImplementation**

<!-- -->

- **All Implemented Interfaces:**
  **[DOMImplementation](../../../org/w3c/dom/DOMImplementation.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLDOMImplementation**
  **
  **

      public class XDBDomImplementation
      extends java.lang.Object
      implements DOMImplementation

  **This class implements the DOMImplementation class of DOM.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                             |
    |-------------------------------------------------------------------------|
    | `XDBDomImplementation``()`<br>Deprecated. <br>                          |
    | `XDBDomImplementation``(java.sql.Connection conn)`<br>Deprecated. <br>  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                           |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Document`](../../../org/w3c/dom/Document.md)         | `createDocument``(java.lang.String namespaceURI, java.lang.String qualifiedName, `[`DocumentType`](../../../org/w3c/dom/DocumentType.md)` doctype)`<br>Deprecated. <br>create and return an empty document object and return it. |
    | [`DocumentType`](../../../org/w3c/dom/DocumentType.md) | `createDocumentType``(java.lang.String qualifiedName, java.lang.String publicId, java.lang.String systemId)`<br>Deprecated. <br>create and return a document type defn. object and return it.                                    |
    | `java.lang.Object`                                     | `getFeature``(java.lang.String feature, java.lang.String version)`<br>Deprecated. <br>                                                                                                                                           |
    | `boolean`                                              | `hasFeature``(java.lang.String feature, java.lang.String version)`<br>Deprecated. <br>test if a particular feature is supported by the given version.                                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XDBDomImplementation

          public XDBDomImplementation()

      Deprecated. 

    <!-- -->

    - #### XDBDomImplementation

          public XDBDomImplementation(java.sql.Connection conn)

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### hasFeature

          public boolean hasFeature(java.lang.String feature,
                                    java.lang.String version)

      Deprecated. 
      test if a particular feature is supported by the given version. We do nothing currently.
      Specified by:
      [`hasFeature`](../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `feature` - the name of the feature to test.

      `version` - the version of the DOM implementation

      Returns:
      always true

    <!-- -->

    - #### createDocumentType

          public DocumentType createDocumentType(java.lang.String qualifiedName,
                                                 java.lang.String publicId,
                                                 java.lang.String systemId)
                                          throws DOMException

      Deprecated. 
      create and return a document type defn. object and return it. We return null
      Specified by:
      [`createDocumentType`](../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `qualifiedName` - The qualified name of the document type to be created.

      `publicId` - The external subset public identifier.

      `systemId` - The external subset system identifier.

      Returns:
      always null

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed.

    <!-- -->

    - #### createDocument

          public Document createDocument(java.lang.String namespaceURI,
                                         java.lang.String qualifiedName,
                                         DocumentType doctype)
                                  throws DOMException

      Deprecated. 
      create and return an empty document object and return it. This document does not conform to any schema.
      Specified by:
      [`createDocument`](../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `namespaceURI` - the top level namespace of the document.

      `qualifiedname` - the QNAME of the top level element of the document

      `doctype` - the DTD if any to be used for this document.

      Returns:
      the created document object

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getFeature

          public java.lang.Object getFeature(java.lang.String feature,
                                             java.lang.String version)

      Deprecated. 

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

- **[Prev Class](XDBDOMException.md)**
- **[Next Class](XDBDOMNotFoundErrException.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
