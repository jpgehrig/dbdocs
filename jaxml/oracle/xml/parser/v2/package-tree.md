Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev](../schema/package-tree.md)**
-

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

# **Hierarchy For Package oracle.xml.parser.v2**

**Package Hierarchies:**

- **[All Packages](../../../../overview-tree.md)**

## **Class Hierarchy**

- **java.lang.Object**
  - **org.xml.sax.helpers.[DefaultHandler](../../../../org/xml/sax/helpers/DefaultHandler.md) (implements org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md), org.xml.sax.[DTDHandler](../../../../org/xml/sax/DTDHandler.md), org.xml.sax.[EntityResolver](../../../../org/xml/sax/EntityResolver.md), org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md))**
    - **oracle.xml.parser.v2.[XMLSAXSerializer](XMLSAXSerializer.md) (implements org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md), org.xml.sax.ext.[DeclHandler](../../../../org/xml/sax/ext/DeclHandler.md), org.xml.sax.[DTDHandler](../../../../org/xml/sax/DTDHandler.md), org.xml.sax.[EntityResolver](../../../../org/xml/sax/EntityResolver.md), org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md), org.xml.sax.ext.[LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md))**
  - **org.xml.sax.[HandlerBase](../../../../org/xml/sax/HandlerBase.md) (implements org.xml.sax.[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md), org.xml.sax.[DTDHandler](../../../../org/xml/sax/DTDHandler.md), org.xml.sax.[EntityResolver](../../../../org/xml/sax/EntityResolver.md), org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md))**
    - **oracle.xml.parser.v2.[DefaultXMLDocumentHandler](DefaultXMLDocumentHandler.md) (implements oracle.xml.parser.v2.[XMLDocumentHandler](XMLDocumentHandler.md))**
      - **oracle.xml.parser.v2.[DocumentBuilder](DocumentBuilder.md) (implements org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md), org.xml.sax.ext.[DeclHandler](../../../../org/xml/sax/ext/DeclHandler.md), org.xml.sax.ext.[LexicalHandler](../../../../org/xml/sax/ext/LexicalHandler.md))**
      - **oracle.xml.parser.v2.[XMLTokenizer](XMLTokenizer.md)**
  - **java.io.InputStream (implements java.io.Closeable)**
    - **java.io.ObjectInputStream (implements java.io.ObjectInput, java.io.ObjectStreamConstants)**
      - **oracle.xml.parser.v2.[XMLObjectInputStream](XMLObjectInputStream.md)**
  - **oracle.xml.parser.v2.[NodeFactory](NodeFactory.md) (implements java.io.Serializable)**
  - **oracle.xml.parser.v2.[oraxml](oraxml.md)**
  - **oracle.xml.parser.v2.[oraxsl](oraxsl.md)**
  - **oracle.xml.parser.v2.[SAXAttrList](SAXAttrList.md) (implements org.xml.sax.[AttributeList](../../../../org/xml/sax/AttributeList.md))**
  - **java.lang.Throwable (implements java.io.Serializable)**
    - **java.lang.Exception**
      - **java.lang.RuntimeException**
        - **org.w3c.dom.[DOMException](../../../../org/w3c/dom/DOMException.md)**
          - **oracle.xml.parser.v2.[XMLDOMException](XMLDOMException.md)**
      - **org.xml.sax.[SAXException](../../../../org/xml/sax/SAXException.md)**
        - **org.xml.sax.[SAXParseException](../../../../org/xml/sax/SAXParseException.md)**
          - **oracle.xml.parser.v2.[XMLParseException](XMLParseException.md)**
      - **oracle.xml.util.[XMLException](../../util/XMLException.md)**
        - **oracle.xml.parser.v2.[XSLException](XSLException.md)**
  - **oracle.xml.parser.v2.[XMLDOMImplementation](XMLDOMImplementation.md) (implements org.w3c.dom.[DOMImplementation](../../../../org/w3c/dom/DOMImplementation.md), org.w3c.dom.ls.[DOMImplementationLS](../../../../org/w3c/dom/ls/DOMImplementationLS.md), java.io.Serializable)**
  - **oracle.xml.util.[XMLError](../../util/XMLError.md)**
    - **oracle.xml.parser.v2.[XMLError](XMLError.md) (implements org.w3c.dom.[DOMError](../../../../org/w3c/dom/DOMError.md))**
  - **oracle.xml.parser.v2.[XMLMultiHandler](XMLMultiHandler.md) (implements org.xml.sax.[ContentHandler](../../../../org/xml/sax/ContentHandler.md))**
  - **oracle.xml.parser.v2.[XMLNode](XMLNode.md) (implements java.lang.Cloneable, org.w3c.dom.events.[EventTarget](../../../../org/w3c/dom/events/EventTarget.md), java.io.Externalizable, org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md), org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md))**
    - **oracle.xml.parser.v2.[AttrDecl](AttrDecl.md) (implements java.io.Externalizable)**
    - **oracle.xml.parser.v2.[DTD](DTD.md) (implements org.w3c.dom.[DocumentType](../../../../org/w3c/dom/DocumentType.md), java.io.Externalizable)**
    - **oracle.xml.parser.v2.[ElementDecl](ElementDecl.md) (implements java.io.Externalizable, java.io.Serializable)**
    - **oracle.xml.parser.v2.[XMLComment](XMLComment.md) (implements org.w3c.dom.[Comment](../../../../org/w3c/dom/Comment.md), java.io.Externalizable)**
    - **oracle.xml.parser.v2.[XMLNotation](XMLNotation.md) (implements java.io.Externalizable, org.w3c.dom.[Notation](../../../../org/w3c/dom/Notation.md))**
    - **oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md) (implements java.io.Externalizable)**
      - **oracle.xml.parser.v2.[XMLAttr](XMLAttr.md) (implements org.w3c.dom.[Attr](../../../../org/w3c/dom/Attr.md), java.io.Externalizable, oracle.xml.parser.v2.[NSName](NSName.md))**
      - **oracle.xml.parser.v2.[XMLElement](XMLElement.md) (implements org.w3c.dom.[Element](../../../../org/w3c/dom/Element.md), org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md), java.io.Externalizable, oracle.xml.parser.v2.[NSName](NSName.md), oracle.xml.parser.v2.[NSResolver](NSResolver.md))**
        - **oracle.xml.parser.v2.[XMLDocument](XMLDocument.md) (implements org.w3c.dom.[Document](../../../../org/w3c/dom/Document.md), org.w3c.dom.validation.[DocumentEditVAL](../../../../org/w3c/dom/validation/DocumentEditVAL.md), org.w3c.dom.events.[DocumentEvent](../../../../org/w3c/dom/events/DocumentEvent.md), org.w3c.dom.traversal.[DocumentTraversal](../../../../org/w3c/dom/traversal/DocumentTraversal.md), org.w3c.dom.events.[EventTarget](../../../../org/w3c/dom/events/EventTarget.md), java.io.Externalizable)**
        - **oracle.xml.parser.v2.[XMLDocumentFragment](XMLDocumentFragment.md) (implements org.w3c.dom.[DocumentFragment](../../../../org/w3c/dom/DocumentFragment.md), java.io.Externalizable)**
      - **oracle.xml.parser.v2.[XMLEntity](XMLEntity.md) (implements org.w3c.dom.[Entity](../../../../org/w3c/dom/Entity.md), java.io.Externalizable)**
      - **oracle.xml.parser.v2.[XMLEntityReference](XMLEntityReference.md) (implements org.w3c.dom.[EntityReference](../../../../org/w3c/dom/EntityReference.md), java.io.Externalizable)**
    - **oracle.xml.parser.v2.[XMLPI](XMLPI.md) (implements java.io.Externalizable, org.w3c.dom.[ProcessingInstruction](../../../../org/w3c/dom/ProcessingInstruction.md))**
      - **oracle.xml.parser.v2.[XMLDeclPI](XMLDeclPI.md) (implements java.io.Externalizable)**
    - **oracle.xml.parser.v2.[XMLText](XMLText.md) (implements java.io.Externalizable, org.w3c.dom.[Text](../../../../org/w3c/dom/Text.md))**
      - **oracle.xml.parser.v2.[XMLCDATA](XMLCDATA.md) (implements org.w3c.dom.[CDATASection](../../../../org/w3c/dom/CDATASection.md), java.io.Externalizable)**
  - **oracle.xml.parser.v2.[XMLOutputStream](XMLOutputStream.md)**
  - **oracle.xml.parser.v2.[XMLParser](XMLParser.md)**
    - **oracle.xml.parser.v2.[BinaryParser](BinaryParser.md)**
    - **oracle.xml.parser.v2.[DOMParser](DOMParser.md)**
    - **oracle.xml.parser.v2.[SAXParser](SAXParser.md) (implements org.xml.sax.[Parser](../../../../org/xml/sax/Parser.md), org.xml.sax.[XMLReader](../../../../org/xml/sax/XMLReader.md))**
  - **oracle.xml.parser.v2.[XMLPrintDriver](XMLPrintDriver.md) (implements oracle.xml.parser.v2.[PrintDriver](PrintDriver.md))**
  - **oracle.xml.parser.v2.[XSLExtensionElement](XSLExtensionElement.md)**
  - **oracle.xml.parser.v2.[XSLProcessor](XSLProcessor.md)**
  - **oracle.xml.parser.v2.[XSLProcessor.XSLTVersion](XSLProcessor.XSLTVersion.md)**
  - **oracle.xml.parser.v2.[XSLStylesheet](XSLStylesheet.md) (implements javax.xml.transform.[Templates](../../../../javax/xml/transform/Templates.md))**
  - **oracle.xml.parser.v2.[XSLTContext](XSLTContext.md)**

## **Interface Hierarchy**

- **org.xml.sax.[DocumentHandler](../../../../org/xml/sax/DocumentHandler.md)**
  - **oracle.xml.parser.v2.[XMLDocumentHandler](XMLDocumentHandler.md)**
- **org.xml.sax.[Locator](../../../../org/xml/sax/Locator.md)**
  - **org.xml.sax.ext.[Locator2](../../../../org/xml/sax/ext/Locator2.md)**
    - **oracle.xml.parser.v2.[XMLLocator](XMLLocator.md)**
- **oracle.xml.parser.v2.[NodeReadHandler](NodeReadHandler.md)**
- **oracle.xml.util.[NSName](../../util/NSName.md)**
  - **oracle.xml.parser.v2.[NSName](NSName.md)**
- **oracle.xml.parser.v2.[NSResolver](NSResolver.md)**
- **oracle.xml.parser.v2.[PrintDriver](PrintDriver.md)**
- **oracle.xml.parser.v2.[XMLToken](XMLToken.md)**

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **Tree**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev](../schema/package-tree.md)**
-

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
