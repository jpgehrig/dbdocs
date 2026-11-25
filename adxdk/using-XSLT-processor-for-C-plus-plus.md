An explanation is given of how to use the Extensible Stylesheet Language Transformation (XSLT) processor for C++.

**Note:**

Use the unified C++ application programming interface (API) in `xml.hpp` for Oracle XML Developer's Kit (XDK) applications. The older, nonunified C++ API in `oraxml.hpp` is deprecated and supported only for backward compatibility. It will be removed in a future release.

### 29.1 Accessing XSLT for C++

Extensible Stylesheet Language Transformation (XSLT) for C++ is provided with Oracle Database.

Sample files are located at `xdk/demo/cpp/new`.

`readme.html` in the root directory of the software archive contains release specific information including bug fixes and API additions.

**Related Topics**

- [XSLT XVM Processor](using-XSLT-and-XVM-processors-for-C.md)

### 29.2 XSL Namespace

This is the namespace for XSLT compilers and transformers.

#### 29.2.1 XSL Interfaces

The XSL interfaces are described.

`XslException` Interface—Root interface for all XSLT-related exceptions.

`Transformer` Interface—Basic XSLT processor. You can use this interface to invoke all XSLT processors.

`CompTransformer` Interface—Extended XSLT processor. You can use this interface only with processors that create intermediate binary bytecode (currently only the XVM-based processor).

`Compiler` Interface—XSLT compiler. It is used for compilers that compile XSLT into binary bytecode.

**See Also:**

[Oracle Database XML C++ API Reference](../cpxml/package-Xsl-API.md) package XSL APIs for C++

### 29.3 XSLT for C++ DOM Interface Usage

Basic usage of XSLT for C++ DOM is described.

There are two inputs to `XMLParser.xmlparse()`:

- The Extensible Markup Language (XML) document

- The XSLT stylesheet to be applied to the XML document

An XSLT processor is initiated by invoking the tools factory to create a particular XSLT transformer or compiler.

An XSLT stylesheet is supplied to a transformer by invoking `setXSL()` member functions.

An XML instance document is supplied as a parameter to the transform member functions.

The resultant document (XML, HTML, Vector Markup Language (VML), and so on) is typically sent to an application for further processing. It is sent as a Document Object Model (DOM) tree or as a sequence of Simple API for XML (SAX) events. SAX events are produced if a SAX event handler is provided by the user.

The application terminates the XSLT processors by invoking their destructors.

### 29.4 Invoking XSLT for C++

You can invoke XSLT for C++ by invoking the executable on the command line or by writing C++ code and using the supplied APIs.

#### 29.4.1 Command-Line Usage

XSLT for C++ can be called as an executable by invoking `bin/xml`.

**See Also:**

[Table 5-4](using-XML-parser-for-C.md)

#### 29.4.2 Writing C++ Code to Use Supplied APIs

XSLT for C++ can be invoked by writing code to use the supplied APIs. The code must be compiled using the headers in directory `public` and linked against the libraries in directory `lib` . See `Makefile` or `make.bat` in `xdk/demo/cpp/new` for full details of how to build your program.

### 29.5 Using the Sample Files Included with the Software

Directory `$ORACLE_HOME/xdk/demo/cpp/parser/` contains several XML applications that show how to use the XSLT for C++.

Table 29-1 XSLT for C++ Sample Files

| Sample File Name                                                | Description                                                                                                                                                                                                                        |
|:----------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `XSLSampleMain.cpp`<br>`XSLSampleGen.cpp`<br>`XSLSampleGen.hpp` | Sources for sample XSLT usage program. `XSLSample` takes two arguments, the XSLT stylesheet and the XML file. If you redirect `stdout` of this program to a file, you may have some output missing, depending on your environment. |
| `XVMSampleMain.cpp`<br>`XVMSampleGen.cpp`<br>`XVMSampleGen.hpp` | Sources for the sample XSLT Virtual Machine (XVM) usage program.                                                                                                                                                                   |
