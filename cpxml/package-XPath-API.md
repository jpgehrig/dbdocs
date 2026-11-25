The `XPath` package for C++ contains types and interfaces related to `XPath` processing, such as `XPath` datatypes, `CompProcessor` methods,`Compiler` methods, `NodeSet` methods, `Processor` methods, `XPathException` methods, and `XPathObject` methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-XPath-processor-for-C-plus-plus.md)

### XPath Datatypes

Table 8-1 summarizes the datatypes of the `XPath` package.

Table 8-1 Summary of Datatypes; XPath Package

| Datatype           | Description                                               |
|:-------------------|:----------------------------------------------------------|
| XPathCompIdType    | Defines XPath compiler identifiers.                       |
| XPathObjType       | Defines object types for XPath 1.0 based implementations. |
| XPathExceptionCode | XPath related exception codes.                            |
| XPathPrIdType      | Defines XPath processor identifiers.                      |

#### XPathCompIdType

Defines XPath compiler identifiers.

##### Definition

    typedef enum XPathCompIdType {
       XvmXPathCompCXml = 1
    } XPathCompIdType;

#### XPathObjType

Defines object types for XPath 1.0 based implementations.

##### Definition

    typedef enum XPathObjType {
       XPOBJ_TYPE_UNKNOWN = 0,
       XPOBJ_TYPE_NDSET   = 1,
       XPOBJ_TYPE_BOOL    = 2,
       XPOBJ_TYPE_NUM     = 3,
       XPOBJ_TYPE_STR     = 4
    } XPathObjType;


#### XPathExceptionCode

XPath related exception codes.

##### Definition

    typedef enum XPathExceptionCode {
       XPATH_UNDEFINED_ERR = 0,
       XPATH_OTHER_ERR = 1
    } XPathExceptionCode;

#### XPathPrIdType

Defines XPath processor identifiers.

##### Definition

    typedef enum XPathPrIdType {      XPathPrCXml       = 1,      XvmPrCXml         = 2    } XPathPrIdType;

### CompProcessor Interface

Table 8-2 summarizes the methods available through the `CompProcessor` interface.

Table 8-2 Summary of CompProcessor Methods; XPath Package

| Function              | Summary                                                    |
|:----------------------|:-----------------------------------------------------------|
| getProcessorId()      | Get processor's Id.                                        |
| process()             | Evaluate XPath expression against given document.          |
| processWithBinXPath() | Evaluate compiled XPath expression against given document. |

#### getProcessorId()

Get processor Id.

##### Syntax

    virtual XPathPrIdType getProcessorId() const = 0;

##### Returns

`(XPathPrIdType)` Processor's Id

#### process()

Inherited from Processor.

##### Syntax

    virtual XPathObject< Node>* process (
       InputSource* isrc_ptr,
       oratext* xpath_exp)
    throw (XPathException) = 0;

| Parameter   | Description                  |
|:------------|:-----------------------------|
| `isrc_ptr`  | instance document to process |
| `xpath_exp` | XPATH expression             |

##### Returns

`(XPathGenObject*)` XPath object

#### processWithBinXPath()

Evaluates compiled XPath expression against given document.

##### Syntax

    virtual XPathObject< Node>* processWithBinXPath (
       InputSource* isrc_ptr,
       ub2* bin_xpath)
    throw (XPathException) = 0;

| Parameter   | Description                  |
|:------------|:-----------------------------|
| `isrc_ptr`  | instance document to process |
| `bin_xpath` | compiled XPATH expression    |

##### Returns

`(XPathGenObject*)` XPath object

### Compiler Interface

Table 8-3 summarizes the methods available through the `Compiler` interface.

Table 8-3 Summary of Compiler Methods; XPath Package

| Function        | Summary                                                      |
|:----------------|:-------------------------------------------------------------|
| compile()       | Compile XPath and return its compiled binary representation. |
| getCompilerId() | Get the compiler's Id                                        |

#### compile()

Compiles XPath and returns its compiled binary representation.

##### Syntax

    virtual ub2* compile (
       oratext* xpath_exp)
    throw (XPathException) = 0;

| Parameter   | Description      |
|:------------|:-----------------|
| `xpath_exp` | XPATH expression |

##### Returns

`(ub2)` XPath expression in compiled binary representation

#### getCompilerId()

Get compiler's id.

##### Syntax

    virtual XPathCompIdType getCompilerId() const = 0;

##### Returns

`(XPathCompIdType)` Compiler's Id

### NodeSet Interface

Table 8-4 summarizes the methods available through the `NodeSet` interface.

Table 8-4 Summary of NodeSet Methods; XPath Package

| Function  | Summary                   |
|:----------|:--------------------------|
| getNode() | Get node given its index. |
| getSize() | Get `NodeSet` size.       |

#### getNode()

Returns a reference to the node.

##### Syntax

    NodeRef< Node>* getNode(
       ub4 idx) const;

| Parameter | Description                  |
|:----------|:-----------------------------|
| `idx`     | index of the node in the set |

##### Returns

`(NodeRef)` reference to the node

#### getSize()

The size of the node set.

##### Syntax

    ub4 getSize() const;

##### Returns

`(ub4)` node set size

### Processor Interface

Table 8-5 summarizes the methods available through the `Processor` interface.

Table 8-5 Summary of Processor Methods; XPath Package

| Function         | Summary                                           |
|:-----------------|:--------------------------------------------------|
| getProcessorId() | Get processor's Id.                               |
| process()        | Evaluate XPath expression against given document. |

#### getProcessorId()

Get processor Id.

##### Syntax

    virtual XPathPrIdType getProcessorId() const = 0;

##### Returns

`(XPathPrIdType)` Processor's Id

#### process()

Evaluates XPath expression against given document and returns result XPath object.

##### Syntax

    virtual XPathObject< Node>* process (
       InputSource* isrc_ptr,
       oratext* xpath_exp)
    throw (XPathException) = 0;

| Parameter   | Description                  |
|:------------|:-----------------------------|
| `isrc_ptr`  | instance document to process |
| `xpath_exp` | XPath expression             |

##### Returns

`(XPathGenObject*)` XPath object

### XPathException Interface

Table 8-6 summarizes the methods available through the `XPathException` interface.

Table 8-6 Summary of XPathException Methods; XPath Package

| Function       | Summary                                              |
|:---------------|:-----------------------------------------------------|
| getCode()      | Get Oracle XML error code embedded in the exception. |
| getMesLang()   | Get current language (encoding) of error messages.   |
| getMessage()   | Get Oracle XML error message.                        |
| getXPathCode() | Get XPath exception code embedded in the exception.  |

#### getCode()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (0 on success)

#### getMesLang()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext*)` Current language (encoding) of error messages

#### getMessage()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message

#### getXPathCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning XPath processor and compiler exception codes, defined in XPathExceptionCode, of the exceptional situations during execution.

##### Syntax

    virtual XPathExceptionCode getXPathCode() const = 0;

##### Returns

`(XPathExceptionCode)` exception code

### XPathObject Interface

Table 8-7 summarizes the methods available through the `XPathObject` interface.

Table 8-7 Summary of XPathObject Methods; XPath Package

| Function        | Summary                  |
|:----------------|:-------------------------|
| XPathObject()   | Copy constructor.        |
| getNodeSet()    | Get the node set.        |
| getObjBoolean() | Get boolean from object. |
| getObjNumber()  | Get number from object.  |
| getObjString()  | Get string from object.  |
| getObjType()    | Get type from object.    |

#### XPathObject()

Copy constructor.

##### Syntax

    XPathObject(
       XPathObject< Node>& src);

| Parameter | Description                          |
|:----------|:-------------------------------------|
| `src`     | reference to the object to be copied |

##### Returns

`(XPathObject)` new object

#### getNodeSet()

Get the node set.

##### Syntax

    NodeSet< Node>* getNodeSet() const;

#### getObjBoolean()

Get the boolean from the object.

##### Syntax

    boolean getObjBoolean() const;

#### getObjNumber()

Get the number from the object.

##### Syntax

    double getObjNumber() const;

#### getObjString()

Get the string from the object.

##### Syntax

    oratext* getObjString() const;

#### getObjType()

Get the type from the object.

##### Syntax

    XPathObjType getObjType() const;
