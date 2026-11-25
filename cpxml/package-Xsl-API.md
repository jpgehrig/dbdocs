The `Xsl` package for C++ contains types and methods related to XSL transformation. They include `Xsl` datatypes, `Compiler` methods, `CompTransformer` methods, `Transformer` methods, and `XSLException` methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-XSLT-processor-for-C-plus-plus.md)

### Xsl Datatypes

Table 10-1 summarizes the datatypes of the `Xsl `package.

Table 10-1 Summary of Datatypes; Xsl Package

| Datatype         | Description                          |
|:-----------------|:-------------------------------------|
| XslCompIdType    | Defines XSL compiler identifiers.    |
| XslExceptionCode | Defines XSLT related exceptions.     |
| XslTrIdType      | Defines XSL transformer identifiers. |

#### XslCompIdType

Defines XSL compiler identifiers.

##### Definition

    typedef enum XslCompIdType {
       XvmCompCXml = 1
    } XslCompIdType;

#### XslExceptionCode

Defines XSLT related exceptions.

##### Definition

    typedef typedef enum XslExceptionCode {
       XSL_UNDEFINED_ERR = 0,
       XSL_OTHER_ERR = 1
    } XslExceptionCode;


#### XslTrIdType

Defines XSL transformer identifiers.

##### Definition

    typedef enum XslTrIdType {
       XslTrCXml         = 1,
       XvmTrCXml         = 2
    } XslTrIdType;

### Compiler Interface

Table 10-2 summarizes the methods available through the `Compiler` interface.

Table 10-2 Summary of Compiler Methods; Xsl Package

| Function        | Summary                                                    |
|:----------------|:-----------------------------------------------------------|
| compile()       | Compile Xsl and return its compiled binary representation. |
| getCompilerId() | Get compiler's Id.                                         |
| getLength()     | Get length of compiled XSL document.                       |

#### compile()

Compiles Xsl and returns its compiled binary representation.

##### Syntax

    virtual ub2* compile(
       InputSource* isrc_ptr)
    throw (XslException) = 0;

| Parameter  | Description  |
|:-----------|:-------------|
| `isrc_ptr` | Xsl document |

##### Returns

`(InputSource)` Xsl document in compiled binary representation

#### getCompilerId()

Get the compiler Id.

##### Syntax

    virtual XslCompIdType getCompilerId() const = 0;

##### Returns

`(XslCompIdType)` Compiler's Id

#### getLength()

Returns length of compiled XSL document

##### Syntax

    virtual ub4 getLength(
       ub2* binxsl_ptr)
    throw (XslException) = 0;

| Parameter    | Description           |
|:-------------|:----------------------|
| `binxsl_ptr` | compiled Xsl document |

##### Returns

`(ub4)` length of the document

### CompTransformer Interface

Table 10-3 summarizes the methods available through the `CompTransformer` interface.

Table 10-3 Summary of CompTransformer Methods; Xsl Package

| Function           | Summary                                 |
|:-------------------|:----------------------------------------|
| getTransformerId() | Get transformer's Id.                   |
| setBinXsl()        | Set compiled Xsl.                       |
| setSAXHandler()    | Set SAX handler.                        |
| setXSL()           | Set XSLT document for this transformer. |
| transform()        | Transform the document.                 |

#### getTransformerId()

Get transformer's id.

##### Syntax

    virtual XslTrIdType getTransformerId() const = 0;

##### Returns

`(XslTrIdType)` Transformer's Id

#### setBinXsl()

Sets compiled Xsl.

##### Syntax

    virtual void setBinXsl (
       ub2* binxsl_ptr)
    throw (XslException) = 0;

| Parameter    | Description           |
|:-------------|:----------------------|
| `binxsl_ptr` | compiled Xsl document |

#### setSAXHandler()

Inherited from Transformer.

##### Syntax

    virtual void setSAXHandler(
       SAXHandlerRoot* hdlr_ptr) = 0;

| Parameter  | Description         |
|:-----------|:--------------------|
| `hdlr_ptr` | SAX handler pointer |

#### setXSL()

Set XSLT document for this transformer. Should be called before the transform member function is called. It is inherited from Transform.

##### Syntax

    virtual void setXSL (
       InputSource* isrc_ptr)
    throw (XslException) = 0;

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `isrc_ptr` | instance document to process |

#### transform()

Transforms the document. Throws an exception if an XSLT document is not set by a previous call to setXSL. Inherited from Transform.

| Syntax                                                                                                                    | Description                                   |
|:--------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------|
| `virtual NodeRef< Node>* transform(`<br>`   nputSource* isrc_ptr)`<br>`throw (XslException) = 0;`                         | Transform the document and return DOM.        |
| `virtual void transform(`<br>`   InputSource* isrc_ptr,`<br>`   SAXHandlerRoot* hdlr_ptr)`<br>`throw (XslException) = 0;` | Transform the document and return SAX events. |

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `isrc_ptr` | instance document to process |
| `hdlr_ptr` | SAX handler pointer          |

##### Returns

`(DocumentRef)` document tree of new document

### Transformer Interface

Table 10-4 summarizes the methods available through the `Transformer` interface.

Table 10-4 Summary of Transformer Methods; Xsl Package

| Function           | Summary                                       |
|:-------------------|:----------------------------------------------|
| getTransformerId() | Get transformer's Id.                         |
| setSAXHandler()    | Set SAX handler.                              |
| setXSL()           | Set XSLT document for this transformer.       |
| transform()        | Transform the document and return SAX events. |

#### getTransformerId()

Gets transformer's id.

##### Syntax

    virtual XslTrIdType getTransformerId() const = 0;

##### Returns

`(XslTrIdType)` Transformer's Id

#### setSAXHandler()

Set SAX handler.

##### Syntax

    virtual void setSAXHandler(
       SAXHandlerRoot* hdlr_ptr) = 0;

| Parameter  | Description         |
|:-----------|:--------------------|
| `hdlr_ptr` | SAX handler pointer |

#### setXSL()

Set XSLT document for this transformer. Should be called before the transform member function is called.

##### Syntax

    virtual void setXSL (
       InputSource* isrc_ptr)
    throw (XslException) = 0;

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `isrc_ptr` | instance document to process |

#### transform()

Transforms the document. Throws an exception if an XSLT document is not set by a previous call to setXSL.

| Syntax                                                                                                                    | Description                                   |
|:--------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------|
| `virtual NodeRef< Node>* transform(`<br>`   nputSource* isrc_ptr)`<br>`throw (XslException) = 0;`                         | Transform the document and return DOM.        |
| `virtual void transform(`<br>`   InputSource* isrc_ptr,`<br>`   SAXHandlerRoot* hdlr_ptr)`<br>`throw (XslException) = 0;` | Transform the document and return SAX events. |

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `isrc_ptr` | instance document to process |
| `hdlr_ptr` | SAX handler pointer          |

##### Returns

`(DocumentRef)` document tree of new document

### XSLException Interface

Table 10-5 summarizes the methods available through the `XSLException` interface.

Table 10-5 Summary of XSLException Methods; Xsl Package

| Function     | Summary                                              |
|:-------------|:-----------------------------------------------------|
| getCode()    | Get Oracle XML error code embedded in the exception. |
| getMesLang() | Get current language (encoding) of error messages.   |
| getMessage() | Get Oracle XML error message.                        |
| getXslCode() | Defines a prototype for implementation.              |

#### getCode()

Gets Oracle XML error code embedded in the exception. Virtual member function inherited from `XmlException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (`0` on success)

#### getMesLang()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext*)` Current language (encoding) of error messages

#### getMessage()

Virtual member function inherited from `XmlException`

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message

#### getXslCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning XSL transformer and compiler exception codes, defined in` XslExceptionCode`, of the exceptional situations during execution.

##### Syntax

    virtual XslExceptionCode getXslCode() const = 0;

##### Returns

`(XslExceptionCode)` exception code
