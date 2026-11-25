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

- **[Prev Class](XMLDOMException.md)**
- **[Next Class](XMLElement.md)**

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

## **Class XMLDOMImplementation**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLDOMImplementation**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable, [DOMImplementation](../../../../org/w3c/dom/DOMImplementation.md), [DOMImplementationLS](../../../../org/w3c/dom/ls/DOMImplementationLS.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLDOMImplementation
      extends java.lang.Object
      implements DOMImplementation, java.io.Serializable, DOMImplementationLS

  **This class implements the DOMImplementation**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.ls.[DOMImplementationLS](../../../../org/w3c/dom/ls/DOMImplementationLS.md)**

      **[`MODE_ASYNCHRONOUS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)`, `[`MODE_SYNCHRONOUS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XMLDOMImplementation``()`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                            | Method and Description                                                                                                                                                                                                                                                       |
    |--------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Document`](../../../../org/w3c/dom/Document.md)            | `createDocument``(ContentManager contentMgr)`<br>Creates an LAZY/Scalable DOM currently only support with XTI Format.                                                                                                                                                        |
    | [`Document`](../../../../org/w3c/dom/Document.md)            | `createDocument``(`[`InfosetReader`](../../scalable/InfosetReader.md)` reader)`<br>Creates an LAZY/Scalable DOM with optional plug-in XML data.                                                                                                                              |
    | [`Document`](../../../../org/w3c/dom/Document.md)            | `createDocument``(java.lang.String namespaceURI, java.lang.String qualifiedName, `[`DocumentType`](../../../../org/w3c/dom/DocumentType.md)` doctype)`<br>Creates an empty DocumentType node.                                                                                |
    | [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)    | `createDocumentType``(java.lang.String qualifiedName, java.lang.String publicId, java.lang.String systemId)`<br>Creates an XML Document object of the specified type with its document element                                                                               |
    | [`LSInput`](../../../../org/w3c/dom/ls/LSInput.md)           | `createLSInput``()`<br>Create a new empty input source object where `LSInput.characterStream`, `LSInput.byteStream` , `LSInput.stringData` `LSInput.systemId`, `LSInput.publicId`, `LSInput.baseURI`, and `LSInput.encoding` are null, and `LSInput.certifiedText` is false. |
    | [`LSOutput`](../../../../org/w3c/dom/ls/LSOutput.md)         | `createLSOutput``()`<br>Create a new empty output destination object where `LSOutput.characterStream`, `LSOutput.byteStream`, `LSOutput.systemId`, `LSOutput.encoding` are null.                                                                                             |
    | [`LSParser`](../../../../org/w3c/dom/ls/LSParser.md)         | `createLSParser``(short mode, java.lang.String schemaType)`<br>Create a new `LSParser`.                                                                                                                                                                                      |
    | [`LSSerializer`](../../../../org/w3c/dom/ls/LSSerializer.md) | `createLSSerializer``()`<br>Create a new `LSSerializer` object.                                                                                                                                                                                                              |
    | `boolean`                                                    | `hasFeature``(java.lang.String feature, java.lang.String version)`<br>Test if the DOM implementation implements a specific feature.                                                                                                                                          |
    | `void`                                                       | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                              |
    | `void`                                                       | `setFeature``(java.lang.String feature)`<br>Sets a specified feature                                                                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLDOMImplementation

          public XMLDOMImplementation()

  <!-- -->

  - ### Method Detail

    - #### hasFeature

          public boolean hasFeature(java.lang.String feature,
                                    java.lang.String version)

      Test if the DOM implementation implements a specific feature.
      Specified by:
      [`hasFeature`](../../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `feature` - ,implementation checked

      `version` - This is the version number of the feature to test. In Level 2, the string can be either "2.0" or "1.0". If the version is not specified, supporting any version of the feature causes the method to return `true`.

      Returns:
      true if the feature is implemented ,false otherwise

    <!-- -->

    - #### createDocumentType

          public DocumentType createDocumentType(java.lang.String qualifiedName,
                                                 java.lang.String publicId,
                                                 java.lang.String systemId)
                                          throws DOMException

      Creates an XML Document object of the specified type with its document element
      Specified by:
      [`createDocumentType`](../../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `qualifiedName` - Qualified name of document type to be created

      `publicId` - Public identifier of the document type object to be created

      `systemId` - System identifier of the document type object to be created

      Returns:
      the DocumentType object created.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character NAMESPACE_ERR: Raised if the qualifiedName is malformed.

    <!-- -->

    - #### createDocument

          public Document createDocument(java.lang.String namespaceURI,
                                         java.lang.String qualifiedName,
                                         DocumentType doctype)
                                  throws DOMException

      Creates an empty DocumentType node. Entity declarations and notations are not made available. Entity reference expansions and default attribute additions do not occur.
      Specified by:
      [`createDocument`](../../../../org/w3c/dom/DOMImplementation.md) in interface [`DOMImplementation`](../../../../org/w3c/dom/DOMImplementation.md)

      Parameters:
      `qualifiedName` - QName of the root element or null

      `namespaceURI` - Namespace of the root element or null

      `doctype` - DocumentType of the Document object created

      Returns:
      the Document object created. INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character NAMESPACE_ERR: Raised if the qualifiedName is malformed, if the qname has a prefix and the namespaceURI is null or an empty String, or if the qualifiedName has a prefix that is "xml" and namespaceURI is different from "http://www.w3.org/XML/1998/namespace" WRONG_DOCUMENT_ERR: Raised if doctype has already been used with a different document or was created from a different implementation

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, or if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace" .
      WRONG_DOCUMENT_ERR: Raised if `doctype` has already been used with a different document or was created from a different implementation.

    <!-- -->

    - #### createDocument

          public Document createDocument(InfosetReader reader)
                                  throws DOMException

      Creates an LAZY/Scalable DOM with optional plug-in XML data.
      Parameters:
      `reader` - - An InfosetReader that is the interface to plug-in XML. If null, an empty DOM will be created

      Returns:
      the Document object created. IllegalArgumentException: If the property of InfosetReader doesn't support access mode.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### createDocument

          public Document createDocument(ContentManager contentMgr)
                                  throws DOMException

      Creates an LAZY/Scalable DOM currently only support with XTI Format.
      Parameters:
      `contentMgr` - - The content manager

      Returns:
      the Document object created.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String feature)
                          throws DOMException

      Sets a specified feature
      Parameters:
      `feature` - the DOM feature

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - if the feature could not be set

    <!-- -->

    - #### createLSParser

          public LSParser createLSParser(short mode,
                                         java.lang.String schemaType)
                                  throws DOMException

      Create a new `LSParser`. The newly constructed parser may then be configured by means of its `DOMConfiguration` object, and used to parse documents by means of its `parse` method.
      Specified by:
      [`createLSParser`](../../../../org/w3c/dom/ls/DOMImplementationLS.md) in interface [`DOMImplementationLS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)

      Parameters:
      `mode` - The `mode` argument is either `MODE_SYNCHRONOUS` or `MODE_ASYNCHRONOUS`, if `mode` is `MODE_SYNCHRONOUS` then the `LSParser` that is created will operate in synchronous mode, if it's `MODE_ASYNCHRONOUS` then the `LSParser` that is created will operate in asynchronous mode.

      `schemaType` - An absolute URI representing the type of the schema language used during the load of a `Document` using the newly created `LSParser`. Note that no lexical checking is done on the absolute URI. In order to create a `LSParser` for any kind of schema types (i.e. the LSParser will be free to use any schema found), use the value `null`.

      Returns:
      The newly created `LSParser` object. This `LSParser` is either synchronous or asynchronous depending on the value of the `mode` argument.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if the requested mode or schema type is NOTE: DOM LS interfaces are pre W3C Recommendation and are subject to change from release to relase until W3C Recommendation. Therefore this method is subject to change.

    <!-- -->

    - #### createLSSerializer

          public LSSerializer createLSSerializer()

      Create a new `LSSerializer` object.
      Specified by:
      [`createLSSerializer`](../../../../org/w3c/dom/ls/DOMImplementationLS.md) in interface [`DOMImplementationLS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)

      Returns:
      The newly created `LSSerializer` object.

      **Note:** By default, the newly created `LSSerializer` has no `DOMErrorHandler`, i.e. the value of the `"error-handler"` configuration parameter is `null`. However, implementations may provide a default error handler at creation time. In that case, the initial value of the `"error-handler"` configuration parameter on the new created `LSSerializer` contains a reference to the default error handler. NOTE: DOM LS interfaces are pre W3C Recommendation and are subject to change from release to relase until W3C Recommendation. Therefore this method is subject to change.

    <!-- -->

    - #### createLSInput

          public LSInput createLSInput()

      Create a new empty input source object where `LSInput.characterStream`, `LSInput.byteStream` , `LSInput.stringData` `LSInput.systemId`, `LSInput.publicId`, `LSInput.baseURI`, and `LSInput.encoding` are null, and `LSInput.certifiedText` is false.
      Specified by:
      [`createLSInput`](../../../../org/w3c/dom/ls/DOMImplementationLS.md) in interface [`DOMImplementationLS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)

      Returns:
      The newly created input object. NOTE: DOM LS interfaces are pre W3C Recommendation and are subject to change from release to relase until W3C Recommendation. Therefore this method is subject to change.

    <!-- -->

    - #### createLSOutput

          public LSOutput createLSOutput()

      Create a new empty output destination object where `LSOutput.characterStream`, `LSOutput.byteStream`, `LSOutput.systemId`, `LSOutput.encoding` are null.
      Specified by:
      [`createLSOutput`](../../../../org/w3c/dom/ls/DOMImplementationLS.md) in interface [`DOMImplementationLS`](../../../../org/w3c/dom/ls/DOMImplementationLS.md)

      Returns:
      The newly created output object. NOTE: DOM LS interfaces are pre W3C Recommendation and are subject to change from release to relase until W3C Recommendation. Therefore this method is subject to change.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

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

- **[Prev Class](XMLDOMException.md)**
- **[Next Class](XMLElement.md)**

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
