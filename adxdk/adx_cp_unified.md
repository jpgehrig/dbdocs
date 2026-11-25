The unified C++ interfaces are described.

### 27.1 What Is the Unified C++ API?

Unified C++ application programming interfaces (APIs) for Extensible Markup Language (XML) tools represent a set of C++ interfaces for Oracle XML tools. All three kinds of C++ interfaces: abstract classes, templates, and implicit interfaces represented by generic template parameters, are used by the unified framework.

This unified approach provides a generic, interface-based framework that allows XML tools to be improved, updated, replaced, or added without affecting any interface-based user code, and minimally affecting application drivers and, possibly, application configuration.

**Note:**

Use the unified C++ API in `xml.hpp` for Oracle XML Developer's Kit (XDK) applications. The older, nonunified C++ API in `oraxml.hpp` is deprecated and supported only for backward compatibility. It will be removed in a future release.

The unified C++ API supports the World Wide Web Consortium (W3C) specification as closely as possible. However, Oracle cannot guarantee that the specification is fully supported by our implementation because the W3C specification does not cover C++ implementations.

### 27.2 Accessing the C++ Interface

The C++ interface is provided with Oracle Database. Sample files are located in `$ORACLE_HOME/xdk/demo/cpp`. `readme.html` in the root directory of the software archive contains release specific information including bug fixes and API additions.

### 27.3 OracleXML Namespace

`OracleXml` is the C++ namespace for all XML C++ interfaces. It contains common interfaces and namespaces for different XDK packages.

The following namespaces are included in namespace `OracleXML`:

- `Ctx`—namespace for TCtx related declarations

- `Dom`—namespace for Document Object Model (DOM) related declarations

- `Parser`—namespace for parser and schema validator declarations

- `IO`—namespace for input and output source declarations

- `Xsl`—namespace for Extensible Stylesheet Language Transformation (XSLT) related declarations

- `XPath `- namespace for XPath related declarations

- `Tools`—namespace for Tools::Factory related declarations

`OracleXml` is fully defined in the file `xml.hpp`. Another namespace, `XmlCtxNS`, visible to users, is defined in `xmlctx.hpp`. That namespace contains C++ definitions of data structures corresponding to C level definitions of the `xmlctx` context and related data structures. While there is no need for users to know details of that namespace, `xmlctx.hpp` must be included in most application main modules.

Multiple encodings are currently supported on the base of the `oratext` type that is currently supposed to be used by all implementations. All strings are represented as `oratext*`.

#### 27.3.1 OracleXML Interfaces

`XMLException` interface—This is the root interface for all XML exceptions.

### 27.4 Ctx Namespace

The Ctx namespace contains data types and interfaces related to the TCtx interface.

#### 27.4.1 OracleXML Data Types

OracleXML data types are described.

`encoding`—a particular supported encoding. The following kinds of encodings (or encoding names) are supported:

- data_encoding

- default_input_encoding

- input_encoding—overwrites the previous one

- error_language—gets overwritten by the language of the error handler, if specified

`encodings`—array of encodings.

#### 27.4.2 Ctx Interfaces

Ctx interfaces `ErrorHandler`, `MemAllocator`, and `Tctx` are described.

`ErrorHandler` Interface — This is the root error handler class. It deals with local processing of errors, mainly from the underlying C implementation. In some implementations, it might throw `XmlException`. To accommodate the needs of all implementations, this behavior is not specified in its signature. However, it can create exception objects. The error handler is passed to the `TCtx` constructor when `TCtx` is initialized. Implementations of this interface are provided by the user.

`MemAllocator` Interface—This is a simple root interface to make the `TCtx` interface reasonably generic so that different allocator approaches can be used in the future. It is passed to the `TCt`x constructor when `TCtx` is initialized. It is a low level allocator that does not know the type of an object being allocated. The allocators with this interface can also be used directly. In this case the user is responsible for the explicit deallocation of objects (with `dealloc`).

If the `MemAllocator` interface is passed as a parameter to the `TCtx` constructor, it often makes sense to overwrite the operator new. In this case, all memory allocations in both C and C++ can be done by the same allocator.

`Tctx` Interface—This is an implicit interface to XML context implementations. It is primarily used for memory allocation, error (not exception) handling, and different encodings handling. The context interface is an implicit interface that is supposed to be used as type parameter. The name `TCtx` is used as a corresponding type parameter name. Its actual substitutions are instantiations of implementations parameterized (templatized) by real context implementations. In the case of errors `XmlException` might be thrown.All constructors create and initialize context implementations. In a multithreaded environment a separate context implementation must be initialized for each thread.

### 27.5 IO Namespace

The `IO` namespace specifies interfaces for the different input and output options for all XML tools.

#### 27.5.1 IO Data Types

Data type `InputSourceType` specifies the kinds of input sources that are supported.

- `ISRC_URI`—Input is to be read from the specified Universal Resource Identifier (URI).

- `ISRC_FILE`—Input is to be read from a file.

- `ISRC_BUFFER`—Input is to be read from a buffer.

- `ISRC_DOM`—Input is a DOM tree.

- `ISRC_CSTREAM`—Input is a C level stream.

#### 27.5.2 IO Interfaces

The interfaces to inputs are described.

`URISource`—This is an interface to inputs from specified URIs.

`FileSource`—This is an interface to inputs from a file.

`BufferSource`—This is an interface to inputs from a buffer.

`DOMSource`—This is an interface to inputs from a DOM tree.

`CStreamSource`—This is an interface to inputs from a C level stream.

### 27.6 Tools Package

`Tools` is the package (subspace of `OracleXml`) for types and interfaces that are related to the creation and instantiation of Oracle XML tools.

#### 27.6.1 Tools Interfaces

Interfaces for XML tools are described.

`FactoryException`—Specifies tools factory exceptions. It is derived from `XMLExceptions`.

`Factory`—XML tools factory. Hides implementations of all XML tools and provides methods to create objects representing these tools based on their identifier (ID) values.

### 27.7 Error Message Files

Error message files are provided in directory `$ORACLE_HOME/xdk/mesg`. You can set environment variable `ORA_XML_MESG` to point to this directory, but this not required.

**See Also:**

[Oracle Database XML C++ API Reference](../cpxml/package-Ctx-API.md) package Ctx APIs for C++
