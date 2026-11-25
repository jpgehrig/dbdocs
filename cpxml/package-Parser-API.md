The Parser interfaces include `Parser`datatypes, `DOMParser`methods, `GParser` methods, `ParserException` methods,`SAXHandler` methods, `SAXParser`methods, and `SchemaValidator`methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-XML-parser-for-C-plus-plus.md)

### Parser Datatypes

Table 5-1 summarizes the datatypes of the `Parser `package.

Table 5-1 Summary of Datatypes; Parser Package

| Datatype            | Description                          |
|:--------------------|:-------------------------------------|
| ParserExceptionCode | Parser implementation of exceptions. |
| DOMParserIdType     | Defines parser identifiers.          |
| SAXParserIdType     | Defines type of node.                |
| SchValidatorIdType  | Defines validator identifiers.       |

#### ParserExceptionCode

Parser implementation of exceptions.

##### Definition

    typedef enum ParserExceptionCode {
       PARSER_UNDEFINED_ERR = 0,
       PARSER_VALIDATION_ERR = 1,
       PARSER_VALIDATOR_ERR = 2,
       PARSER_BAD_ISOURCE_ERR = 3,
       PARSER_CONTEXT_ERR = 4,
       PARSER_PARAMETER_ERR = 5,
       PARSER_PARSE_ERR = 6,
       PARSER_SAXHANDLER_SET_ERR = 7,
       PARSER_VALIDATOR_SET_ERR = 8 }
    ParserExceptionCode;

#### DOMParserIdType

Defines parser identifiers.

##### Definition

    typedef enum DOMParserIdType {      DOMParCXml         = 1    } DOMParserIdType;
    ypedef enum CompareHowCode {
       START_TO_START = 0,
       START_TO_END = 1,
       END_TO_END = 2,
       END_TO_START = 3 }
    CompareHowCode;

#### SAXParserIdType

Defines parser identifiers.

##### Definition

    typedef enum SAXParserIdType {
       SAXParCXml = 1 }
    SAXParserIdType;

#### SchValidatorIdType

Defines validator identifiers.These identifiers are used as parameters to the XML tools factory when a particular validator object has to be created.

##### Definition

    typedef enum SchValidatorIdType {
       SchValCXml        = 1
    } SchValidatorIdType;

### DOMParser Interface

Table 5-2 summarizes the methods available through the `DOMParser` interface.

Table 5-2 Summary of DOMParser Methods; Parser Package

| Function       | Summary                                                  |
|:---------------|:---------------------------------------------------------|
| getContext()   | Returns parser's XML context (allocation and encodings). |
| getParserId()  | Get parser id.                                           |
| parse()        | Parse the document.                                      |
| parseDTD()     | Parse DTD document.                                      |
| parseSchVal()  | Parse and validate the document.                         |
| setValidator() | Set the validator for this parser.                       |

#### getContext()

Each parser object is allocated and executed in a particular Oracle XML context. This member function returns a pointer to this context.

##### Syntax

    virtual Context* getContext() const = 0;

##### Returns

`(Context*)` pointer to parser's context

#### getParserId()

##### Syntax

    virtual DOMParserIdType getParserId() const = 0;

##### Returns

`(DOMParserIdType)` Parser Id

#### parse()

Parses the document and returns the tree root node

##### Syntax

    virtual DocumentRef< Node>* parse(
       InputSource* isrc_ptr,
       boolean DTDvalidate = FALSE,
       DocumentTypeRef< Node>* dtd_ptr = NULL,
       boolean no_mod = FALSE,
       DOMImplementation< Node>* impl_ptr = NULL)
    throw (ParserException) = 0;

| Parameter     | Description                          |
|:--------------|:-------------------------------------|
| `isrc_ptr`    | input source                         |
| `DTDvalidate` | `TRUE` if validated by DTD           |
| `dtd_ptr`     | DTD reference                        |
| `no_mod`      | `TRUE` if no modifications allowed   |
| `impl_ptr`    | optional `DomImplementation` pointer |

##### Returns

`(DocumentRef)` document tree

#### parseDTD()

Parse DTD document.

##### Syntax

    virtual DocumentRef< Node>* parseDTD(
       InputSource* isrc_ptr,
       boolean no_mod = FALSE,
       DOMImplementation< Node>* impl_ptr = NULL)
    throw (ParserException) = 0;

| Parameter  | Description                        |
|:-----------|:-----------------------------------|
| `isrc_ptr` | input source                       |
| `no_mod`   | `TRUE` if no modifications allowed |
| `impl_ptr` | optional DomImplementation pointer |

##### Returns

`(DocumentRef)` DTD document tree

#### parseSchVal()

Parses and validates the document. Sets the validator if the corresponding parameter is not `NULL`.

##### Syntax

    virtual DocumentRef< Node>* parseSchVal(
       InputSource* src_par,
       boolean no_mod = FALSE,
       DOMImplementation< Node>* impl_ptr = NULL,
       SchemaValidator< Node>* tor_ptr = NULL)
    throw (ParserException) = 0;

| Parameter  | Description                        |
|:-----------|:-----------------------------------|
| `isrc_ptr` | input source                       |
| `no_mod`   | `TRUE` if no modifications allowed |
| `impl_ptr` | optional DomImplementation pointer |
| `tor_ptr`  | schema validator                   |

##### Returns

`(DocumentRef)` document tree

#### setValidator()

Sets the validator for all validations except when another one is given in parseSchVal

##### Syntax

    virtual void setValidator(
    SchemaValidator< Node>* tor_ptr) = 0;

| Parameter | Description      |
|:----------|:-----------------|
| `tor_ptr` | schema validator |

### GParser Interface

Table 5-3 summarizes the methods available through the `GParser` interface.

Table 5-3 Summary of GParser Methods; Parser Package

| Function                 | Summary                                                        |
|:-------------------------|:---------------------------------------------------------------|
| SetWarnDuplicateEntity() | Specifies if multiple entity declarations result in a warning. |
| getBaseURI()             | Returns the base URI for the document.                         |
| getDiscardWhitespaces()  | Checks if whitespaces between elements are discarded.          |
| getExpandCharRefs()      | Checks if character references are expanded.                   |
| getSchemaLocation()      | Get schema location for this document.                         |
| getStopOnWarning()       | Get if document processing stops on warnings.                  |
| getWarnDuplicateEntity() | Get if multiple entity declarations cause a warning.           |
| setBaseURI()             | Sets the base URI for the document.                            |
| setDiscardWhitespaces()  | Sets if formatting whitespaces should be discarded.            |
| setExpandCharRefs()      | Get if character references are expanded.                      |
| setSchemaLocation()      | Set schema location for this document.                         |
| setStopOnWarning()       | Sets if document processing stops on warnings.                 |

#### SetWarnDuplicateEntity()

Specifies if entities that are declared more than once will cause warnings to be issued.

##### Syntax

    void setWarnDuplicateEntity(
       boolean par_bool);

| Parameter  | Description                                            |
|:-----------|:-------------------------------------------------------|
| `par_bool` | `TRUE` if multiple entity declarations cause a warning |

#### getBaseURI()

Returns the base URI for the document. Usually only documents loaded from a URI will automatically have a base URI. Documents loaded from other sources (`stdin`, buffer, and so on) will not naturally have a base URI, but a base URI may have been set for them using `setBaseURI`, for the purposes of resolving relative URIs in inclusion.

##### Syntax

    oratext* getBaseURI() const;

##### Returns

`(oratext *)` current document's base URI \[or `NULL`\]

#### getDiscardWhitespaces()

Checks if formatting whitespaces between elements, such as newlines and indentation in input documents are discarded. By default, all input characters are preserved.

##### Syntax

    boolean getDiscardWhitespaces() const;

##### Returns

`(boolean)` `TRUE` if whitespace between elements are discarded

#### getExpandCharRefs()

Checks if character references are expanded in the DOM data. By default, character references are replaced by the character they represent. However, when a document is saved those characters entities do not reappear. To ensure they remain through load and save, they should not be expanded.

##### Syntax

    boolean getExpandCharRefs() const;

##### Returns

`(boolean)` `TRUE` if character references are expanded

#### getSchemaLocation()

Gets schema location for this document. It is used to figure out the optimal layout when loading documents into a database.

##### Syntax

    oratext* getSchemaLocation() const;

##### Returns

`(oratext*)` schema location

#### getStopOnWarning()

When `TRUE` is returned, warnings are treated the same as errors and cause parsing, validation, and so on, to stop immediately. By default, warnings are issued but the processing continues.

##### Syntax

    boolean getStopOnWarning() const;

##### Returns

`(boolean)` `TRUE` if document processing stops on warnings

#### getWarnDuplicateEntity()

Get if entities which are declared more than once will cause warnings to be issued.

##### Syntax

    boolean getWarnDuplicateEntity() const;

##### Returns

`(boolean)` `TRUE` if multiple entity declarations cause a warning

#### setBaseURI()

Sets the base URI for the document. Usually only documents that were loaded from a URI will automatically have a base URI. Documents loaded from other sources (stdin, buffer, and so on) will not naturally have a base URI, but a base URI may have been set for them using setBaseURI, for the purposes of resolving relative URIs in inclusion.

##### Syntax

    void setBaseURI( oratext* par);

| Parameter | Description |
|:----------|:------------|
| `par`     | base URI    |

#### setDiscardWhitespaces()

Sets if formatting whitespaces between elements (newlines and indentation) in input documents are discarded. By default, ALL input characters are preserved.

##### Syntax

    void setDiscardWhitespaces(
       boolean par_bool);

| Parameter  | Description                               |
|:-----------|:------------------------------------------|
| `par_bool` | `TRUE `if whitespaces should be discarded |

#### setExpandCharRefs()

Sets if character references should be expanded in the DOM data. Ordinarily, character references are replaced by the character they represent. However, when a document is saved those characters entities do not reappear. To ensure they remain through load and save is to not expand them.

##### Syntax

    void setExpandCharRefs(
       boolean par_bool);

| Parameter  | Description                                        |
|:-----------|:---------------------------------------------------|
| `par_bool` | `TRUE `if character references should be discarded |

#### setSchemaLocation()

Sets schema location for this document. It is used to figure out the optimal layout when loading documents into a database.

##### Syntax

     void setSchemaLocation(
       oratext* par);

| Parameter | Description     |
|:----------|:----------------|
| `par`     | schema location |

#### setStopOnWarning()

When `TRUE` is set, warnings are treated the same as errors and cause parsing, validation, and so on, to stop immediately. By default, warnings are issued but the processing continues.

##### Syntax

    void setStopOnWarning(
       boolean par_bool);

| Parameter  | Description                                           |
|:-----------|:------------------------------------------------------|
| `par_bool` | `TRUE `if document processing should stop on warnings |

### ParserException Interface

Table 5-4 summarizes the methods available through the P`arserException` interface.

Table 5-4 Summary of ParserException Methods; Parser Package

| Function        | Summary                                              |
|:----------------|:-----------------------------------------------------|
| getCode()       | Get Oracle XML error code embedded in the exception. |
| getMesLang()    | Get current language (encoding) of error messages.   |
| getMessage()    | Get Oracle XML error message.                        |
| getParserCode() | Get parser exception code embedded in the exception. |

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

#### getParserCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning parser and validator exception codes, defined in ParserExceptionCode, of the exceptional situations during execution.

##### Syntax

    virtual ParserExceptionCode getParserCode() const = 0;

##### Returns

`(ParserExceptionCode)` exception code

### SAXHandler Interface

Table 5-5 summarizes the methods available through the `SAXHandler` interface.

Table 5-5 Summary of SAXHandler Methods; Parser Package

| Function                | Summary                                                  |
|:------------------------|:---------------------------------------------------------|
| CDATA()                 | Receive notification of CDATA.                           |
| XMLDecl()               | Receive notification of an XML declaration.              |
| attributeDecl()         | Receive notification of attribute's declaration.         |
| characters()            | Receive notification of character data.                  |
| comment()               | Receive notification of a comment.                       |
| elementDecl()           | Receive notification of element's declaration.           |
| endDocument()           | Receive notification of the end of the document.         |
| endElement()            | Receive notification of element's end.                   |
| notationDecl()          | Receive notification of a notation declaration.          |
| parsedEntityDecl()      | Receive notification of a parsed entity declaration.     |
| processingInstruction() | Receive notification of a processing instruction.        |
| startDocument()         | Receive notification of the start of the document.       |
| startElement()          | Receive notification of element's start.                 |
| startElementNS()        | Receive namespace aware notification of element's start. |
| unparsedEntityDecl()    | Receive notification of an unparsed entity declaration.  |
| whitespace()            | Receive notification of whitespace characters.           |

#### CDATA()

This event handles CDATA, as distinct from Text. The data will be in the data encoding, and the returned length is in characters, not bytes. This is an Oracle extension.

##### Syntax

    virtual void CDATA(
       oratext* data,
       ub4 size) = 0;

| Parameter | Description      |
|:----------|:-----------------|
| `data`    | pointer to CDATA |
| `size`    | size of CDATA    |

#### XMLDecl()

This event marks an XML declaration (`XMLDecl`). The `startDocument` event is always first; this event will be the second event. The encoding flag says whether an encoding was specified. For the standalone flag, -1 will be returned if it was not specified, otherwise `0` for `FALSE`, 1 for `TRUE`. This member function is an Oracle extension.

##### Syntax

    virtual void XMLDecl(
       oratext* version,
       boolean is_encoding,
       sword standalone) = 0;

| Parameter     | Description                    |
|:--------------|:-------------------------------|
| `version`     | version string from XMLDecl    |
| `is_encoding` | whether encoding was specified |
| `standalone`  | value of standalone value flag |

#### attributeDecl()

This event marks an attribute declaration in the DTD. It is an Oracle extension; not in SAX standard

##### Syntax

    virtual void attributeDecl(
       oratext* attr_name,
       oratext *name,
       oratext *content) = 0;

| Parameter   | Description                   |
|:------------|:------------------------------|
| `attr_name` | name of the attribute         |
| `name`      | name of the declaration       |
| `content`   | body of attribute declaration |

#### characters()

This event marks character data.

##### Syntax

    virtual void characters(
       oratext* ch,
       ub4 size) = 0;

| Parameter | Description     |
|:----------|:----------------|
| `ch`      | pointer to data |
| `size`    | length of data  |

#### comment()

This event marks a comment in the XML document. The comment's data will be in the data encoding. It is an Oracle extension, not in SAX standard.

##### Syntax

    virtual void comment(
       oratext* data) = 0;

| Parameter | Description    |
|:----------|:---------------|
| `data`    | comment's data |

#### elementDecl()

This event marks an element declaration in the DTD. It is an Oracle extension; not in SAX standard.

##### Syntax

    virtual void elementDecl(
       oratext *name,
       oratext *content) = 0;

| Parameter | Description       |
|:----------|:------------------|
| `name`    | element's name    |
| `content` | element's content |

#### endDocument()

Receive notification of the end of the document.

##### Syntax

    virtual void endDocument() = 0;

#### endElement()

This event marks the end of an element. The name is the `tagName` of the element (which may be a qualified name for namespace-aware elements) and is in the data encoding.

##### Syntax

    virtual void endElement( oratext* name) = 0;

#### notationDecl()

The even marks the declaration of a notation in the DTD. The notation's name, public ID, and system ID will all be in the data encoding. Both IDs are optional and may be `NULL`.

##### Syntax

    virtual void notationDecl(
       oratext* name,
       oratext* public_id,
       oratext* system_id) = 0;

| Parameter   | Description          |
|:------------|:---------------------|
| `name`      | notations's name     |
| `public_id` | notation's public Id |
| `sysem_id`  | notation's system Id |

#### parsedEntityDecl()

Marks a parsed entity declaration in the DTD. The parsed entity's name, public ID, system ID, and notation name will all be in the data encoding. This is an Oracle extension.

##### Syntax

    virtual void parsedEntityDecl(
       oratext* name,
       oratext* value,
       oratext* public_id,
       oratext* system_id,
       boolean general) = 0;

| Parameter   | Description                                            |
|:------------|:-------------------------------------------------------|
| `name`      | entity's name                                          |
| `value`     | entity's value if internal                             |
| `public_id` | entity's public Id                                     |
| `sysem_id`  | entity's system Id                                     |
| `general`   | whether a general entity (`FALSE` if parameter entity) |

#### processingInstruction()

This event marks a processing instruction. The PI's target and data will be in the data encoding. There is always a target, but the data may be `NULL`.

##### Syntax

    virtual void processingInstruction(
       oratext* target,
       oratext* data) = 0;

| Parameter | Description |
|:----------|:------------|
| `target`  | PI's target |
| `data`    | PI's data   |

#### startDocument()

Receive notification of the start of document.

##### Syntax

    virtual void startDocument() = 0;

#### startElement()

This event marks the start of an element.

##### Syntax

    virtual void startElement(
       oratext* name,
       NodeListRef< Node>* attrs_ptr) = 0;

| Parameter   | Description                  |
|:------------|:-----------------------------|
| `name`      | element's name               |
| `attrs_ptr` | list of element's attributes |

#### startElementNS()

This event marks the start of an element. Note this is the new SAX 2 namespace-aware version. The element's qualified name, local name, and namespace URI will be in the data encoding, as are all the attribute parts.

##### Syntax

    virtual void startElementNS(
       oratext* qname,
       oratext* local,
       oratext* ns_URI,
       NodeListRef< Node>* attrs_ptr) = 0;

| Parameter   | Description                        |
|:------------|:-----------------------------------|
| `qname`     | element's qualified name           |
| `local`     | element's namespace local name     |
| `ns_URI`    | element's namespace URI            |
| `attrs_ref` | `NodeList` of element's attributes |

#### unparsedEntityDecl()

Marks an unparsed entity declaration in the DTD. The unparsed entity's name, public ID, system ID, and notation name will all be in the data encoding.

##### Syntax

    virtual void unparsedEntityDecl(
       oratext* name,
       oratext* public_id,
       oratext* system_id,
       oratext* notation_name) = 0;
    };

| Parameter       | Description            |
|:----------------|:-----------------------|
| `name`          | entity's name          |
| `public_id`     | entity's public Id     |
| `sysem_id`      | entity's system Id     |
| `notation_name` | entity's notation name |

#### whitespace()

This event marks ignorable whitespace data such as newlines, and indentation between lines.

##### Syntax

    virtual void whitespace(
       oratext* data,
       ub4 size) = 0;

| Parameter | Description     |
|:----------|:----------------|
| `data`    | pointer to data |
| `size`    | length of data  |

### SAXParser Interface

Table 5-6 summarizes the methods available through the `SAXParser` interface.

Table 5-6 Summary of SAXParser Methods; Parser Package

| Function        | Summary                                                  |
|:----------------|:---------------------------------------------------------|
| getContext()    | Returns parser's XML context (allocation and encodings). |
| getParserId()   | Returns parser Id.                                       |
| parse()         | Parse the document.                                      |
| parseDTD()      | Parse the DTD.                                           |
| setSAXHandler() | Set SAX handler.                                         |

#### getContext()

Each parser object is allocated and executed in a particular Oracle XML context. This member function returns a pointer to this context.

##### Syntax

    virtual Context* getContext() const = 0;

##### Returns

`(Context*)` pointer to parser's context

#### getParserId()

Returns the parser id.

##### Syntax

    virtual SAXParserIdType getParserId() const = 0;

##### Returns

`(SAXParserIdType)` Parser Id

#### parse()

Parses a document.

##### Syntax

    virtual void parse(
       InputSource* src_ptr,
       boolean DTDvalidate = FALSE,
       SAXHandlerRoot* hdlr_ptr = NULL)
    throw (ParserException) = 0;

| Parameter     | Description                 |
|:--------------|:----------------------------|
| `src_ptr`     | input source                |
| `DTDValidate` | `TRUE` if validate with DTD |
| `hdlr_ptr`    | SAX handler pointer         |

#### parseDTD()

Parses a DTD.

##### Syntax

    virtual void parseDTD(
       InputSource* src_ptr,
       SAXHandlerRoot* hdlr_ptr = NULL)
    throw (ParserException) = 0;

| Parameter  | Description         |
|:-----------|:--------------------|
| `src_ptr`  | input source        |
| `hdlr_ptr` | SAX handler pointer |

#### setSAXHandler()

Sets SAX handler for all parser invocations except when another SAX handler is specified in the parser call.

##### Syntax

    virtual void setSAXHandler(
       SAXHandlerRoot* hdlr_ptr) = 0;

| Parameter  | Description         |
|:-----------|:--------------------|
| `hdlr_ptr` | SAX handler pointer |

### SchemaValidator Interface

Table 5-7 summarizes the methods available through the `SchemaValidator` interface.

Table 5-7 Summary of SchemaValidator Methods; Parser Package

| Function         | Summary                   |
|:-----------------|:--------------------------|
| getSchemaList()  | Return the Schema list.   |
| getValidatorId() | Get validator identifier. |
| loadSchema()     | Load a schema document.   |
| unloadSchema()   | Unload a schema document. |

#### getSchemaList()

Return only the size of loaded schema list documents if "list" is `NULL`. If "list" is not `NULL`, a list of URL pointers is returned in the user-provided pointer buffer. Note that its user's responsibility to provide a buffer with big enough size.

##### Syntax

    virtual ub4 getSchemaList(
       oratext **list) const = 0;

| Parameter | Description                 |
|:----------|:----------------------------|
| `list`    | address of a pointer buffer |

##### Returns

`(ub4)` list size and list of loaded schemas (I/O parameter)

#### getValidatorId()

Get the validator identifier corresponding to the implementation of this validator object.

##### Syntax

    virtual SchValidatorIdType getValidatorId() const = 0;

##### Returns

`(SchValidatorIdType)` validator identifier

#### loadSchema()

Load up a schema document to be used in the next validation session. Throws an exception in the case of an error.

##### Syntax

    virtual void loadSchema(
       oratext* schema_URI)
    throw (ParserException) = 0;

| Parameter    | Description                                 |
|:-------------|:--------------------------------------------|
| `schema_URI` | URL of a schema document; compiler encoding |

#### unloadSchema()

Unload a schema document and all its descendants (included or imported in a nested manner from the validator. All previously loaded schema documents will remain loaded until they are unloaded. To unload all loaded schema documents, set `schema_URI` to be `NULL`. Throws an exception in the case of an error.

##### Syntax

    virtual void unloadSchema(
       oratext* schema_URI)
    throw (ParserException) = 0;

| Parameter    | Description                                 |
|:-------------|:--------------------------------------------|
| `schema_URI` | URL of a schema document; compiler encoding |
