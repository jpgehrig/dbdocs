An explanation is given of how to use the Extensible Markup Language (XML) parser for C++.

**Note:**

Use the unified C++ application programming interface (API) in `xml.hpp` for Oracle XML Developer's Kit (XDK) applications. The older, nonunified C++ API in `oraxml.hpp` is deprecated and supported only for backward compatibility. It will be removed in a future release.

### 28.1 Introduction to Oracle XML Parser for C++

Oracle XML parser for C++ determines whether an XML document is well-formed and optionally validates it against a document type definition (DTD) or Extensible Markup Language (XML) schema. The parser constructs an object tree that can be accessed through one of these two XML APIs:

- Document Object Model (DOM): Tree-based APIs. A tree-based API compiles an XML document into an internal tree structure, then allows an application to navigate that tree using the DOM, a standard tree-based API for XML and HTML documents.

- Simple API for XML (SAX): Event-based APIs. An event-based API reports parsing events (such as the start and end of elements) directly to the application through a user defined SAX even handler, and does not usually build an internal tree. The application implements handlers to deal with the different events, much like handling events in a graphical user interface.

Tree-based APIs are useful for a wide range of applications, but they often put a great strain on system resources, especially if the document is large (under very controlled circumstances, it is possible to construct the tree in a lazy fashion to avoid some of this problem). Furthermore, some applications must build their own, different data trees, and it is very inefficient to build a tree of parse nodes only to map it onto a new tree.

### 28.2 DOM Namespace

The DOM namespace is the namespace for DOM-related types and interfaces.

DOM interfaces are represented as generic references to different implementations of the DOM specification. They are parameterized by `Node` that supports various specializations and instantiations. Of them, the most important is `xmlnode` which corresponds to the current C implementation

These generic references do not have a `NULL`-like value. Any implementation must never create a reference with no state (like `NULL`). If it is necessary to signal that something has no state, the implementation must throw an exception.

Many methods might throw the `SYNTAX_ERR` exception, if the DOM tree is incorrectly formed, or they might throw `UNDEFINED_ERR`, when encountering incorrect parameters or unexpected `NULL` pointers. If these are the only errors that a particular method might throw, it is not reflected in the method signature.

Actual DOM trees do not depend on the context, `TCtx`. However, manipulations on DOM trees in the current, `xmlctx`-based implementation require access to the current context, `TCtx`. This is accomplished by passing the context pointer to the constructor of `DOMImplRef`. In multithreaded environment `DOMImplRef` is always created in the thread context and, so, has the pointer to the right context.

`DOMImplRef` provides a way to create DOM trees. `DomImplRef` is a reference to the actual `DOMImplementation` object that is created when a regular, noncopy constructor of `DomImplRef` is invoked. This works well in a multithreaded environment where DOM trees must be shared, and each thread has a separate `TCtx` associated with it. This works equally well in a single threaded environment.

`DOMString` is one encoding supported by Oracle implementations. The support of other encodings is an Oracle extension. The `oratext*` data type is used for all encodings. Interfaces represent DOM level 2 Core interfaces according to [Document Object Model Core](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adxdk&id=w3_org_dom_level2_core). These C++ interfaces support the DOM specification as closely as possible. However, Oracle cannot guarantee that the specification is fully supported by our implementation because the World Wide Web Consortium (W3C) specification does not cover C++ binding.

#### 28.2.1 DOM Data Types

`DomNodeType` defines types of DOM nodes. `DomExceptionCode` defines exception codes returned by the DOM API.

#### 28.2.2 DOM Interfaces

The DOM interfaces are described.

`DOMException` Interface—See exception `DOMException` in the W3C DOM documentation. DOM operations raise exceptions only in "exceptional" circumstances: when an operation is impossible to perform (either for logical reasons, because data is lost, or because the implementation has become unstable). The functionality of XMLException can be used for a wider range of exceptions.

`NodeRef` Interface—See interface `Node` in the W3C documentation.

`DocumentRef` Interface—See interface `Document` in the W3C documentation.

`DocumentFragmentRef` Interface—See interface `DocumentFragment` in the W3C documentation.

`ElementRef` Interface—See interface `Element` in the W3C documentation.

`AttrRef` Interface—See interface `Attr` in the W3C documentation.

`CharacterDataRef` Interface—See interface `CharacterData` in the W3C documentation.

`TextRef` Interface—See `Text` nodes in the W3C documentation.

`CDATASectionRef` Interface—See `CDATASection` nodes in the W3C documentation.

`CommentRef` Interface—See `Comment` nodes in the W3C documentation.

`ProcessingInstructionRef` Interface—See `PI` nodes in the W3C documentation.

`EntityRef` Interface—See `Entity` nodes in the W3C documentation.

`EntityReferenceRef` Interface—See `EntityReference` nodes in the W3C documentation.

`NotationRef` Interface—See `Notation` nodes in the W3C documentation.

`DocumentTypeRef` Interface—See `DTD` nodes in the W3C documentation.

`DOMImplRef` Interface—See interface `DOMImplementation` in the W3C DOM documentation. `DOMImplementation` is fundamental for manipulating DOM trees. Every DOM tree is attached to a particular DOM implementation object. Several DOM trees can be attached to the same DOM implementation object. Each DOM tree can be deleted and deallocated by deleting the document object. All DOM trees attached to a particular DOM implementation object are deleted when this object is deleted. The `DOMImplementation` object is not visible to the user directly. It is visible through the class `DOMImplRef`. This functionality is needed because of requirements for multithreaded environments.

`NodeListRef` Interface—Abstract implementation of node list. See interface NodeList in the W3C documentation.

`NamedNodeMapRef` Interface—Abstract implementation of a node map. See interface NamedNodeMap in the W3C documentation.

#### 28.2.3 DOM Traversal and Range Data Types

`AcceptNodeCode` is the data type for values returned by node filters for iterators and tree walkers. `WhatToShowCode` is the data type for codes to filter nodes. `RangeExceptionCode` is the data type for exceptions that can be thrown by interface `Range`. `CompareHowCode` is the data type for range comparisons.

#### 28.2.4 DOM Traversal and Range Interfaces

The DOM 2 traversal and range interfaces are `NodeFilter`, `NodeIterator`, `TreeWalker`, `DocumentTraversal`, `RangeException`, `Range`, and `DocumentRange`.

### 28.3 Parser Namespace

Interfaces associated with the parser namespace are described.

`DOMParser` Interface—DOM parser root class.

`GParser` Interface—Root class for XML parsers.

`ParserException` Interface—Exception class for parser and validator.

`SAXHandler` Interface—Root class for current SAX handler implementations.

`SAXHandlerRoot` Interface—Root class for all SAX handlers.

`SAXParser` Interface—Root class for all SAX parsers.

`SchemaValidator` Interface—XML schema-aware validator.

#### 28.3.1 GParser Interface

Interface `GParser` is the root class for all XML parser interfaces and implementations. It is not an abstract class; that is, it is not an interface. It is a real class that you can use to set and check parser parameters.

#### 28.3.2 DOMParser Interface

Interface `DOMParser` is the DOM parser root abstract class or interface. In addition to parsing and checking that a document is well formed, it provides ways to validate a document against a document type definition (DTD) or an XML schema.

#### 28.3.3 SAXParser Interface

Interface `SAXParser` is the root abstract class for all SAX parsers.

##### 28.3.3.1 SAX Event Handlers

To use SAX, a SAX event handler class must be provided by the user and passed to the SAXParser in a `parse()` invocation or set before such invocation.

`SAXHandlerRoot` Interface—root class for all SAX handlers.

`SAXHandler` Interface—root class for current SAX handler implementations.

### 28.4 Thread Safety for the XML Parser for C++

If threads are forked in the midst of the init–parse–term sequence of invocations, unpredictable behavior or results can occur.

### 28.5 XML Parser for C++ Usage

Invoke `Tools::Factory` to create a parser and initialize the parsing process. The XML input can be kind of `InputSource` (see `IO` namespace). `DOMParser` invocation produces the DOM tree. `SAXParser` invocation produces SAX events. Invoking the `parser` destructor terminates the process.

### 28.6 XML Parser for C++ Default Behavior

The default behavior for the XML parser for C++ is described.

- Character set encoding is 8-bit encoding of Unicode (UTF-8). If all your documents are ASCII, you are encouraged to set the encoding to US-ASCII for better performance.

- Messages are printed to `stderr` unless `msghdlr` is specified.

- XML parser for C++ determines whether an XML document is well-formed and optionally validates it against a DTD. The parser constructs an object tree that can be accessed through a DOM interface or operates serially through a SAX interface.

- A parse tree which can be accessed by DOM APIs is built unless `saxcb` is set to use the SAX callback APIs. You can set any of the SAX callback functions to `NULL` if not needed.

- The default behavior for the parser is to check that the input is well-formed but not to check whether it is valid. The flag `XML_FLAG_VALIDATE` can be set to validate the input. The default behavior for white space processing is to be fully conformant with the XML 1.0 spec, that is, all white space is reported back to the application but it is indicated which white space is ignorable. However, some applications may prefer to set the `XML_FLAG_DISCARD_WHITESPACE` which discards all white space between an end-element tag and this start-element tag.

  **Note:**

  Oracle recommends that you set the default encoding explicitly if using only single-byte character sets (such as US-ASCII or any of the ISO-8859 character sets) for performance up to 25% faster than with multibyte character sets, such as UTF-8.

- In both of these cases, an event-based API provides a simpler, lower-level access to an XML document: you can parse documents much larger than your available system memory, and you can construct your own data structures using your callback event handlers.

### 28.7 C++ Sample Files

Directory `xdk/demo/cpp/parser/` contains several XML applications that show how to use the XML parser for C++ with the DOM and SAX interfaces.

Change directories to the sample directory (`$ORACLE_HOME/xdk/demo/cpp` on Solaris, for example) and read the `README` file. This document explains how to build the sample programs.

Table 28-1 lists the sample files in the directory. Each file `*Main.cpp` has a corresponding `*Gen.cpp` and `*Gen.hpp`.

Table 28-1 XML Parser for C++ Sample Files

| Sample File Name        | Description                                           |
|:------------------------|:------------------------------------------------------|
| `DOMSampleMain.cpp`     | Sample usage of C++ interfaces of XML parser and DOM. |
| `FullDOMSampleMain.cpp` | Manually build DOM and then exercise.                 |
| `SAXSampleMain.cpp`     | Source for SAXSample program.                         |

**See Also:**

[Oracle Database XML C++ API Reference](../cpxml/package-Parser-API.md) for parser package APIs for C++
