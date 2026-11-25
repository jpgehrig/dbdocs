An explanation is given of how to use the XPath processor for C++.

**Note:**

Use the unified C++ application programming interface (API) in `xml.hpp` for Oracle XML Developer's Kit (XDK) applications. The older, nonunified C++ API in `oraxml.hpp` is deprecated and supported only for backward compatibility. It will be removed in a future release.

### 31.1 XPath Interfaces

The XPath interfaces are described.

`Processor` Interface—basic XPath processor interface to which any XPath processor must conform.

`CompProcessor` Interface—extended XPath processor that adds an ability to use XPath expressions precompiled into an internal binary representation. In this release this interface represents Oracle virtual machine interface.

`Compiler` Interface—XPath compiler into binary representation.

`NodeSetRef` Interface—defines references to node sets when they are returned by the XPath expression evaluation.

`XPathException` Interface—exceptions for XPath compilers and processors.

`XPathObject` Interface—interface for XPath 1.0 objects.

### 31.2 Sample Programs

Sample programs are located in `xdk/demo/cpp/new`.

The programs `XslXPathSample` and `XvmXPathSample` have sources:

`XslXPathSampleGen.hpp`, XslXPathSampleGen.cpp, `XslXPathSampleMain.cpp`, `XslXPathSampleForce.cpp`;

and `XvmXPathSampleGen.hpp`, `XvmXPathSampleGen.cpp`, `XvmXPathSampleMain.cpp`, `XvmXPathSampleForce.cpp`.

**See Also:**

[Oracle Database XML C++ API Reference](../cpxml/package-XPath-API.md) package XPATH APIs for C++
