Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../../../oracle/xml/xsql/package-summary.md)**
- **[Next Package](events/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

# **Package org.w3c.dom**

**A W3C standard package for XML Document Object Model (DOM), that provides a framework of interfaces for implementing  'DOM level 2 CORE..**

**See: Description**

- **Interface Summary**

  | Interface                                             | Description                                                                                                                                                                                                                  |
  |-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Attr](Attr.md)                                       | The `Attr` interface represents an attribute in an `Element` object.                                                                                                                                                         |
  | [CDATASection](CDATASection.md)                       | CDATA sections are used to escape blocks of text containing characters that would otherwise be regarded as markup.                                                                                                           |
  | [CharacterData](CharacterData.md)                     | The `CharacterData` interface extends Node with a set of attributes and methods for accessing character data in the DOM.                                                                                                     |
  | [Comment](Comment.md)                                 | This interface inherits from `CharacterData` and represents the content of a comment, i.e., all the characters between the starting ' `<!`                                                                                   |
  | [Document](Document.md)                               | The `Document` interface represents the entire HTML or XML document.                                                                                                                                                         |
  | [DocumentFragment](DocumentFragment.md)               | `DocumentFragment` is a "lightweight" or "minimal" `Document` object.                                                                                                                                                        |
  | [DocumentType](DocumentType.md)                       | Each `Document` has a `doctype` attribute whose value is either `null` or a `DocumentType` object.                                                                                                                           |
  | [DOMConfiguration](DOMConfiguration.md)               | The `DOMConfiguration` interface represents the configuration of a document and maintains a table of recognized parameters.                                                                                                  |
  | [DOMError](DOMError.md)                               | `DOMError` is an interface that describes an error.                                                                                                                                                                          |
  | [DOMErrorHandler](DOMErrorHandler.md)                 | `DOMErrorHandler` is a callback interface that the DOM implementation can call when reporting errors that happens while processing XML data, or when doing some other processing (e.g. validating a document).               |
  | [DOMImplementation](DOMImplementation.md)             | The `DOMImplementation` interface provides a number of methods for performing operations that are independent of any particular instance of the document object model.                                                       |
  | [DOMImplementationList](DOMImplementationList.md)     | The `DOMImplementationList` interface provides the abstraction of an ordered collection of DOM implementations, without defining or constraining how this collection is implemented.                                         |
  | [DOMImplementationSource](DOMImplementationSource.md) | This interface permits a DOM implementer to supply one or more implementations, based upon requested features and versions, as specified in .                                                                                |
  | [DOMLocator](DOMLocator.md)                           | `DOMLocator` is an interface that describes a location (e.g.                                                                                                                                                                 |
  | [DOMStringList](DOMStringList.md)                     | The `DOMStringList` interface provides the abstraction of an ordered collection of `DOMString` values, without defining or constraining how this collection is implemented.                                                  |
  | [Element](Element.md)                                 | The `Element` interface represents an element in an HTML or XML document.                                                                                                                                                    |
  | [Entity](Entity.md)                                   | This interface represents an entity, either parsed or unparsed, in an XML document.                                                                                                                                          |
  | [EntityReference](EntityReference.md)                 | `EntityReference` objects may be inserted into the structure model when an entity reference is in the source document, or when the user wishes to insert an entity reference.                                                |
  | [NamedNodeMap](NamedNodeMap.md)                       | Objects implementing the `NamedNodeMap` interface are used to represent collections of nodes that can be accessed by name.                                                                                                   |
  | [NameList](NameList.md)                               | The `NameList` interface provides the abstraction of an ordered collection of parallel pairs of name and namespace values (which could be null values), without defining or constraining how this collection is implemented. |
  | [Node](Node.md)                                       | The `Node` interface is the primary datatype for the entire Document Object Model.                                                                                                                                           |
  | [NodeList](NodeList.md)                               | The `NodeList` interface provides the abstraction of an ordered collection of nodes, without defining or constraining how this collection is implemented.                                                                    |
  | [Notation](Notation.md)                               | This interface represents a notation declared in the DTD.                                                                                                                                                                    |
  | [ProcessingInstruction](ProcessingInstruction.md)     | The `ProcessingInstruction` interface represents a "processing instruction", used in XML as a way to keep processor-specific information in the text of the document.                                                        |
  | [Text](Text.md)                                       | The `Text` interface inherits from `CharacterData` and represents the textual content (termed character data in XML) of an `Element` or `Attr`.                                                                              |
  | [TypeInfo](TypeInfo.md)                               | The `TypeInfo` interface represent a type referenced from `Element` or `Attr` nodes, specified in the schemas associated with the document.                                                                                  |
  | [UserDataHandler](UserDataHandler.md)                 | When associating an object to a key on a node using `Node.setUserData()` the application can provide a handler that gets called when the node the object is associated to is being cloned, imported, or renamed.             |

- **Exception Summary**

  | Exception                       | Description                                                                                                                                                                                                                  |
  |---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [DOMException](DOMException.md) | DOM operations only raise exceptions in "exceptional" circumstances, i.e., when an operation is impossible to perform (either for logical reasons, because data is lost, or because the implementation has become unstable). |

## **Package org.w3c.dom Description**

**A W3C standard package for XML Document Object Model (DOM), that provides a framework of interfaces for implementing  'DOM level 2 CORE..
**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../../../oracle/xml/xsql/package-summary.md)**
- **[Next Package](events/package-summary.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
