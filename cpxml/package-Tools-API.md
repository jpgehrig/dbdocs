The `Tools` package contains types and methods for creating and instantiating Oracle XML tools. It describes `Tools` datatypes, `Factory` methods, and `FactoryException` methods.

### Tools Datatypes

Table 7-1 summarizes the datatypes of the `Tools` package.

Table 7-1 Summary of Datatypes; Tools Package

| Datatype             | Description              |
|:---------------------|:-------------------------|
| FactoryExceptionCode | Tool Factory exceptions. |

#### FactoryExceptionCode

Tool Factory exceptions.

##### Definition

    typedef enum FactoryExceptionCode {
       FACTORY_UNDEFINED_ERR = 0,
       FACTORY_OTHER_ERR = 1
    } FactoryExceptionCode;

### Factory Interface

Table 7-2 summarizes the methods available through the `Factory` interface.

Table 7-2 Summary of Factory Methods; Tools Package

| Function                       | Summary                          |
|:-------------------------------|:---------------------------------|
| Factory()                      | Constructor.                     |
| createDOMParser()              | Create DOM Parser.               |
| createSAXParser()              | Create SAX Parser.               |
| createSchemaValidator()        | Create schema validator.         |
| createXPathCompProcessor()     | Create extended XPath processor. |
| createXPathCompiler()          | Create XPath compiler.           |
| createXPathProcessor()         | Create XPath processor.          |
| createXPointerProcessor()      | Create XPointer processor.       |
| createXslCompiler()            | Create Xsl compiler.             |
| createXslExtendedTransformer() | Create XSL extended transformer. |
| createXslTransformer()         | Create XSL transformer.          |
| getContext()                   | Get factory's context.           |
| ~Factory()                     | Default destructor.              |

#### Factory()

Class constructor.

| Syntax                                                               | Description                                    |
|:---------------------------------------------------------------------|:-----------------------------------------------|
| `Factory() `<br>`throw (FactoryException);`                          | Default constructor                            |
| `Factory(`<br>`   Context* ctx_ptr) `<br>`throw (FactoryException);` | Creates factory object given a Context object. |

| Parameter | Description                 |
|:----------|:----------------------------|
| `ctx_ptr` | pointer to a context object |

##### Returns

`(Factory)` object

#### createDOMParser()

Creates DOM parser.

##### Syntax

    DOMParser< Context, Node>* createDOMParser (
       DOMParserIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | parser id type              |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(DOMParser*)` pointer to the parser object

#### createSAXParser()

Creates SAX parser.

##### Syntax

    SAXParser< Context>* createSAXParser (
       SAXParserIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | parser id type              |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(SAXParser*)` pointer to the parser object

#### createSchemaValidator()

Creates schema validator.

##### Syntax

    SchemaValidator< Node>* createSchemaValidator (
       SchValidatorIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | validator id type           |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(SchemaValidator*)` pointer to the validator object

#### createXPathCompProcessor()

Creates extended XPath processor; takes `XvmPrCXml` value only.

##### Syntax

    CompProcessor< Context, Node>* createXPathCompProcessor (
       XPathPrIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | processor id type           |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(CompProcessor*)` pointer to the processor object

#### createXPathCompiler()

Creates XPath compiler.

##### Syntax

    XPath::Compiler< Context, Node>* createXPathCompiler (
       XPathCompIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | compiler id type            |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(XPathCompiler*)` pointer to the compiler object

#### createXPathProcessor()

Creates XPath processor.

##### Syntax

    XPath::Processor< Context, Node>* createXPathProcessor (
       XPathPrIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | processor id type           |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(Processor*)` pointer to the processor object

#### createXPointerProcessor()

Creates XPointer processor.

##### Syntax

    XPointer::Processor< Context, Node>* createXPointerProcessor (
       XppPrIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | processor id type           |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(Processor*)` pointer to the processor object

#### createXslCompiler()

Creates Xsl compiler.

##### Syntax

    Xsl::Compiler< Context, Node>* createXslCompiler (
       XslCompIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | compiler id type            |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(Compiler*)` pointer to the compiler object

#### createXslExtendedTransformer()

Creates XSL extended `trnasformer`; takes `XvmTrCXml` value only.

##### Syntax

    CompTransformer< Context, Node>* createXslExtendedTransformer (
       XslTrIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | transformer id type         |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(CompTrasformer*)` pointer to the transformer object

#### createXslTransformer()

Creates XSL trnasformer.

##### Syntax

    Transformer< Context, Node>* createXslTransformer (
       XslTrIdType id_type,
       Context* ctx_ptr = NULL)
    throw (FactoryException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `id_type` | transformer id type         |
| `ctx_ptr` | pointer to a Context object |

##### Returns

`(Trasformer*)` pointer to the transformer object

#### getContext()

Returns factory's context.

##### Syntax

    Context* getContext() const;

##### Returns

`(Context*)` pointer to the context object

#### ~Factory()

Default destructor.

##### Syntax

    ~Factory();

### FactoryException Interface

Table 7-3 summarizes the methods available through the `FactoryException` interface.

Table 7-3 Summary of FactoryException Methods; Tools Package

| Function         | Summary                                              |
|:-----------------|:-----------------------------------------------------|
| getCode()        | Get Oracle XML error code embedded in the exception. |
| getFactoryCode() | Get FactoryException code embedded in the exception. |
| getMesLang()     | Get current language (encoding) of error messages.   |
| getMessage()     | Get Oracle XML error message.                        |

#### getCode()

Gets Oracle XML error code embedded in the exception. Virtual member function inherited from `XmlException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (0 on success)

#### getFactoryCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning exception codes specific to the Tools namespace, defined in FactoryExceptionCode, of the exceptional situations during execution

##### Syntax

    virtual FactoryExceptionCode getFactoryCode() const = 0;

##### Returns

`(FactoryExceptionCode)` exception code

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
