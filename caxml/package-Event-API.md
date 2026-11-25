The following table summarizes the methods available through the `Event` interface for XML C APIs.

Table 4-1 Summary of Event Methods for XML C Implementation

| Function                     | Summary                                                                                                                                                                                                                                                                                         |
|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| XmlEvCleanPPCtx()            | Cleans up intenal structures related to a parse operation. This will not destroy the event context. The event context can be reused after this call.                                                                                                                                            |
| XmlEvCreatePPCtx()           | Creates an Event context in pull-parse mode.                                                                                                                                                                                                                                                    |
| XmlEvCreateSVCtx()           | Creates an event context for the streaming validadtor.                                                                                                                                                                                                                                          |
| XmlEvDestroyPPCtx()          | Destroys the event context. Terminates parsing. May be called at any time during a parsing operation.                                                                                                                                                                                           |
| XmlEvDestroySVCtx()          | Terminates an event context created by a streaming validator.                                                                                                                                                                                                                                   |
| XmlEvGetAttrCount()          | Retrieves the number of attributes for the `XML_EVENT_START_ELEMENT` event.                                                                                                                                                                                                                     |
| XmlEvGetAttrDeclBody()       | Retrieves the attribute body in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                     |
| XmlEvGetAttrDeclBody0()      | Retrieves the `NULL`-terminated attribute body in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                        |
| XmlEvGetAttrDeclCount()      | Retreives the number of attributes in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                                    |
| XmlEvGetAttrDeclElName()     | Retrieves the element name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                       |
| XmlEvGetAttrDeclElName0()    | Retrieves the `NULL`-terminated element name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                          |
| XmlEvGetAttrDeclLocalName()  | Retrieves the local name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                         |
| XmlEvGetAttrDeclLocalName0() | Retrieves the `NULL`-terminated local name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                            |
| XmlEvGetAttrDeclName()       | Retrieves the attribute name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                     |
| XmlEvGetAttrDeclName0()      | Retrieves the `NULL`-terminated attribute name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                        |
| XmlEvGetAttrDeclPrefix()     | Retrieves the attribute prefix in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                   |
| XmlEvGetAttrDeclPrefix0()    | Retrieves the `NULL`-terminated attribute prefix in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.                                                                                                                                                                                      |
| XmlEvGetAttrID()             | Retrieves the ID for the attribute's `QNAME`, for `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                             |
| XmlEvGetAttrLocalName()      | Retrieves the attribute local name for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.                                                                                                                                                               |
| XmlEvGetAttrLocalName0()     | Retrieves the `NULL`-terminated attribute name for the `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                        |
| XmlEvGetAttrName()           | Retrieves the attribute name for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.                                                                                                                                                                     |
| XmlEvGetAttrName0()          | Retrieves the `NULL`-terminated attribute name for the `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                        |
| XmlEvGetAttrPrefix()         | Retrieves the prefix tag for `XML_EVENT_START_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter.                                                                                                                                                              |
| XmlEvGetAttrPrefix0()        | Retrieves the `NULL`-terminated attribute prefix for the `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                      |
| XmlEvGetAttrURI()            | Retrieves the attribute URI for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.                                                                                                                                                                      |
| XmlEvGetAttrURI0()           | Retrieves the `NULL`-terminated attribute URI for the `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                         |
| XmlEvGetAttrUriID()          | Retrieves the ID for the attribute's URI, for `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                                 |
| XmlEvGetAttrValue()          | Retrieves the attribute value for one of the `XML_EVENT_START_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter.                                                                                                                                              |
| XmlEvGetAttrValue0()         | Retrieves the `NULL`-terminated attribute value for the `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                       |
| XmlEvGetElDeclContent()      | Retrieves the element declaration content for `XML_EVENT_ELEMENT_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                             |
| XmlEvGetElDeclContent0()     | Retrieves the element declaration content for `XML_EVENT_ELEMENT_DECLARATION`.                                                                                                                                                                                                                  |
| XmlEvGetEncoding()           | Returns the value of the encoding specified.                                                                                                                                                                                                                                                    |
| XmlEvGetError()              | Retrieves the error number when the `XML_EVENT_FATAL_ERROR` or `XML_EVENT_ERROR` event is returned by an XmlEvNext()                                                                                                                                                                            |
| XmlEvGetName()               | Retrurns the name of for either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events, and the length of the event in the `OUT` `len` parameter.                                                                                                                                          |
| XmlEvGetName0()              | Retrieves a `NULL`-terminated name for either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events                                                                                                                                                                                       |
| XmlEvGetLocalName()          | Retrieves the local name tag for either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter:                                                                                                                        |
| XmlEvGetLocalName0()         | Retrieves a `NULL`-terminated local name tag for either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter:                                                                                                        |
| XmlEvGetLocation()           | Retrieves the location during parsing, as `OUT` parameters for the line number of the input stream and its path.                                                                                                                                                                                |
| XmlEvGetPIData()             | Retrieves the text for `XML_EVENT_PI` or `XML_EVENT_PI_CONT` events, and also returns the length of the event as an `OUT len` parameter.                                                                                                                                                        |
| XmlEvGetPIData0()            | Retrieves `NULL`-terminated text for `XML_EVENT_PI` or `XML_EVENT_PI_CONT` events.                                                                                                                                                                                                              |
| XmlEvGetPITarget()           | Retrieves the target for `XML_EVENT_PI` and `XML_EVENT_PI_CONT` events, and also returns the length of the event as an `OUT len` parameter.                                                                                                                                                     |
| XmlEvGetPITarget0()          | Retrieves the `NULL`-terminated target for `XML_EVENT_PI` and `XML_EVENT_PI_CONT` events.                                                                                                                                                                                                       |
| XmlEvGetPEIsGen()            | Determines if the general entity was declared, `XML_EVENT_PE_DECLARATION`.                                                                                                                                                                                                                      |
| XmlEvGetPERepl()             | Retrieves the replacement text of PE declaration, `XML_EVENT_PE_DECLARATION`. Also, provides the length as an `OUT len` parameter.                                                                                                                                                              |
| XmlEvGetPERepl0()            | Retrieves the `NULL`-terminated replacement text of PE declaration, `XML_EVENT_PE_DECLARATION`.                                                                                                                                                                                                 |
| XmlEvGetPrefix()             | Retrieves the prefix tag for one of either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter.                                                                                                                     |
| XmlEvGetPrefix0()            | Retrieves the prefix tag for one of either `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events..                                                                                                                                                                                        |
| XmlEvGetPubId()              | Retrieves the public id for `XML_EVENT_PE_DECLARATION`, `XML_EVENT_UE_DECLARATION`, or `XML_EVENT_NOTATION_DECLARATION` events; also, provides the length as an `OUT len` parameter.                                                                                                            |
| XmlEvGetPubId0()             | Retrieves the `NULL`-terminated public id for `XML_EVENT_PE_DECLARATION`, `XML_EVENT_UE_DECLARATION`, or `XML_EVENT_NOTATION_DECLARATION` events.                                                                                                                                               |
| XmlEvGetSysId()              | Retrieves the system id for `XML_EVENT_PE_DECLARATION`, `XML_EVENT_UE_DECLARATION`, or `XML_EVENT_NOTATION_DECLARATION` events; also, provides the length as an `OUT len` parameter.                                                                                                            |
| XmlEvGetSysId0()             | Retrieves the `NULL`-terminated system id for `XML_EVENT_PE_DECLARATION`, `XML_EVENT_UE_DECLARATION`, or `XML_EVENT_NOTATION_DECLARATION` events.                                                                                                                                               |
| XmlEvGetTagID()              | Retrieves the ID for the tag's `QNAME`, for `XML_EVENT_START_ELEMENT` events.                                                                                                                                                                                                                   |
| XmlEvGetTagUriID()           | Retrieves the ID for the tag's URI, for `XML_EVENT_START_ELEMENT` and `XML_EVENT_END_ELEMENT` events.                                                                                                                                                                                           |
| XmlEvGetText()               | Retrieves the text for `XML_EVENT_CHARACTERS`, `XML_EVENT_CHARACTERS_CONT`, `XML_EVENT_SPACE,` `XML_EVENT_SPACE_CONT`, `XML_EVENT_COMMENT`, `XML_EVENT_COMMENT_CONT`, `XML_EVENT_CDATA`, and `XML_EVENT_CDATA_CONT` events, and also returns the length of the event as an `OUT len` parameter. |
| XmlEvGetText0()              | Retrieves the `NULL`-terminated text for `XML_EVENT_CHARACTERS`, `XML_EVENT_CHARACTERS_CONT`, `XML_EVENT_SPACE,` `XML_EVENT_SPACE_CONT`, `XML_EVENT_COMMENT`, `XML_EVENT_COMMENT_CONT`, `XML_EVENT_CDATA`, and `XML_EVENT_CDATA_CONT` events.                                                   |
| XmlEvGetUENdata()            | Retrieves the ndata for `XML_EVENT_UE_DECLARATION` event, and also returns the length of the event as an `OUT len` parameter.                                                                                                                                                                   |
| XmlEvGetUENdata0()           | Retrieves the `NULL`-terminated ndata for `XML_EVENT_UE_DECLARATION` event.                                                                                                                                                                                                                     |
| XmlEvGetURI()                | Retrieves the URI tag for `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter:                                                                                                                                      |
| XmlEvGetURI0()               | Retrieves the `NULL`-terminated URI tag for `XML_EVENT_START_ELEMENT` or `XML_EVENT_END_ELEMENT` events.                                                                                                                                                                                        |
| XmlEvGetVersion()            | Provides information about version specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event.                                                                                                                                                                                   |
| XmlEvIsEncodingSpecified()   | Provides information about encoding specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event.                                                                                                                                                                                  |
| XmlEvIsNamespaceAttr()       | Determines if an attribute is a namespace atrribute for `XML_EVENT_START_ELEMENT` event.                                                                                                                                                                                                        |
| XmlEvIsStandalone()          | Provides information about standalone specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event                                                                                                                                                                                 |
| XmlEvNext()                  | Gets the next event and advances the parser.                                                                                                                                                                                                                                                    |
| XmlEvNextTag()               | Advances the parser to the next tag event.                                                                                                                                                                                                                                                      |
| XmlEvLoadPPDoc()             | Loads a new document and configures it for pull parsing.                                                                                                                                                                                                                                        |
| XmlEvSchemaValidate()        | Validates XML documents represented by events.                                                                                                                                                                                                                                                  |

### XmlEvCleanPPCtx()

Cleans up intenal structures related to a parse operation. This will not destroy the event context. The event context can be reused after this call.

#### Syntax

    xmlerr XmlEvCleanPPCtx(
       xmlctx *xctx,
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `xctx`    | `IN`   | XML context       |
| `evtx`    | `IN`   | XmlEvents context |

#### Returns

`(xmlerr)` the error number

### XmlEvCreatePPCtx()

Creates an Event context in pull-parse mode.

The document is loaded using XmlEvLoadPPDoc. The actual parsing is driven by multiple calls to XmlEvNext(). After each call, relevant information may be retrieved by calls to the various `XmlEvGet``XXX`() functions. Basic set of properties are the same as for `XmlLoadDom`. Input source should be specified with XmlEvLoadPPDoc() call.

#### Syntax

    xmlevctx *XmlEvCreatePPCtx(
       xmlctx *xctx,
       xmlerr  *xerr,
       list);

| Parameter | In/Out | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------|:-------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `xctx`    | `IN`   | XML context                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `xerr`    | `IN`   | numeric error code, `XMLERR_OK[0]` on success                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `list`    | `IN`   | These additional properties should be supplied with a terminal `NULL`:<br>• `("expand_entities", boolean)` that, when `FALSE`, causes parsed non-parameter entity references not be expanded. By default such references are expanded.<br>• `("use_buffer", buffer)` is the address of a buffer that when specified, will use the buffer to collect data that should be returned back to the user. The `get``XXX``()` functions will return this buffer as a data pointer.<br>• `("use_buffer_len", lengthOfBuffer)` is the number of bytes in a buffer, the actual lenght of the buffer, and no more than the specified length is collected. In the case, only part of the data is collected, generating the `CONT` flavor of the event is generated. Subsequent calls to `XmlEventsNext` provide additional data. Sequence of `CONT`-flavored events is always terminated by a non -`CONT` event. The buffer may be only partially filled.<br>• `("get_id_callback", function)` is the addres for the callback function, to convert text base names to 8-byte IDs. Once such function is supplied, the user is allowed to use `XmlEvGetTagID`, `XmlEvGetAttrID`, `XmlEvGetTagUriID`, and `XmlEvGetAttrUriID`.<br>• `("raw_buffer_len", length)` is the number of bytes in a buffer. By default, this parameter is 256K. Raw buffer is used to read the input data and perform character conversion, and also to convert CRLFs and CRs to LFs.<br>• `("error_callback", callback)` provides the address of a callback function tha is invoked to signal illegal use of an API for that event.<br>These optional parameters should be used in the following manner:<br>`xmlevctx *XmlEvCreatePPCtx(`<br>`   xmlctx *xctx, `<br>`   xmlerr  *xerr,`<br>`   ("expand_entities", mode),`<br>`   ("use_buffer", buffer),`<br>`   ("use_buffer_len", length),`<br>`   ("get_id_callback", function),`<br>`   ("raw_buffer_len",  length),`<br>`   ("error_callback", callback) );` |

#### Returns

`(xmlevctx)` Event contex to be passed on subsequent calls to XmlEvNext()

### XmlEvCreateSVCtx()

Creates an event context for the streaming validadtor. Initializes the streaming validator and returns an event context that can be used in subsequent calls.

Use in conjunction with XmlEvDestroySVCtx()XmlEvDestroySVCtx(). This is a transparent method. An alternate approach would be to use the opague XmlEvSchemaValidate()XmlEvSchemaValidate().

#### Syntax

    xmlevctx *XmlEvCreateSVCtx(
       xmlctx *xctx,
       xsdctx *sctx,
       xmlevctx *docEvCtx,
       xmlerr *err);

| Parameter  | In/Out | Description                                      |
|:-----------|:-------|:-------------------------------------------------|
| `xctx`     | `IN`   | XML context; must be valid                       |
| `sctx`     | `IN`   | Schema context; must be valid                    |
| `docEvCtx` | `IN`   | Event context for the document that is validated |
| `err`      | `OUT`  | numeric error code, `XMLERR_OK[0]` on success    |

#### Returns

`(xmlevctx)` Event contex to be passed on subsequent calls to XmlEvNext()XmlEvNext()

### XmlEvDestroyPPCtx()

Destroys the event context. Terminates parsing. May be called at any time during a parsing operation.

#### Syntax

    void XmlEvDestroyPPCtx(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

### XmlEvDestroySVCtx()

Terminates an event context created by a streaming validator. Returns `XMLERR_OK[0]` on success, or a numeric error code on failure.

Use in conjunction with XmlEvCreateSVCtx()XmlEvCreateSVCtx(). This is a transparent method. An alternate approach would be to use the opague XmlEvSchemaValidate()XmlEvSchemaValidate().

#### Syntax

    xmlerr XmlEvDestroySVCtx(
       xmlctx *xctx,
       xmlevctx *evCtx);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `evCtx`   | `IN`   | Event context that should be terminatedt |

#### Returns

`(xmlerr)` the error number

### XmlEvGetAttrCount()

Retrieves the number of attributes for the `XML_EVENT_START_ELEMENT` event.

#### Syntax

    ub4  XmlEvGetAttrCount(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(ub4)` the number of attributes

### XmlEvGetAttrDeclBody()

Retrieves the attribute body in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrDeclBody(
       xmlevctx *evctx,
       ub4 index,
       ub4 *len);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |
| `len`     | `OUT`  | the length             |

#### Returns

`(oratext*)` the declaration body

### XmlEvGetAttrDeclBody0()

Retrieves the `NULL`-terminated attribute body in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    oratext *XmlEvGetAttrDeclBody0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the declaration body

### XmlEvGetAttrDeclCount()

Retreives the number of attributes in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    ub4 XmlEvGetAttrDeclCount(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(ub4)` number of attributes

### XmlEvGetAttrDeclElName()

Retrieves the element name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrDeclElName(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `len`     | `OUT`  | the length        |

#### Returns

`(oratext*)` the element name

### XmlEvGetAttrDeclElName0()

Retrieves the `NULL`-terminated element name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    oratext *XmlEvGetAttrDeclElName0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` the element name

### XmlEvGetAttrDeclLocalName()

Retrieves the local name of the attribute declaration event, `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrDeclLocalName(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |
| `len`     | `OUT`  | the length             |

#### Returns

`(oratext*)` the local name

### XmlEvGetAttrDeclLocalName0()

Retrieves the `NULL`-terminated local name in attribute declaration event, `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    oratext *XmlEvGetAttrDeclLocalName0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the local name

### XmlEvGetAttrDeclName()

Retrieves the attribute name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrDeclName(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |
| `len`     | `OUT`  | the length             |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrDeclName0()

Retrieves the `NULL`-terminated attribute name in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    oratext *XmlEvGetAttrDeclName0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrDeclPrefix()

Retrieves the attribute prefix in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrDeclPrefix(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |
| `len`     | `OUT`  | the length             |

#### Returns

`(oratext*)` the attribute prefix

### XmlEvGetAttrDeclPrefix0()

Retrieves the `NULL`-terminated attribute prefix in attribute declaration `XML_EVENT_ATTLIST_DECLARATION`.

#### Syntax

    oratext *XmlEvGetAttrDeclPrefix0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the attribute prefix

### XmlEvGetAttrID()

Retrieves the ID for the attribute's `QNAME`, for `XML_EVENT_START_ELEMENT` events. Invokes the user-supplied ID callback specified in XmlEvCreatePPCtx(); if the callback is not specified, returns `0`.

#### Syntax

    sb8 XmlEvGetAttrID(
       xmlevctx *evctx
       ub4 index);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `evctx`   | `IN`   | XML Event context  |
| `index`   | `IN`   | index of attribute |

#### Returns

`(sb8)` the ID

### XmlEvGetAttrLocalName()

Retrieves the attribute local name for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrLocalName(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description                                                |
|:----------|:-------|:-----------------------------------------------------------|
| `evctx`   | `IN`   | XML Event context                                          |
| `index`   | `IN`   | index of the attribute; ignored for `XML_EVENT_START_ATTR` |
| `len`     | `OUT`  | the length                                                 |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrLocalName0()

Retrieves the `NULL`-terminated attribute local name for the `XML_EVENT_START_ELEMENT` events.

#### Syntax

    oratext *XmlEvGetAttrLocalName0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description                                                |
|:----------|:-------|:-----------------------------------------------------------|
| `evctx`   | `IN`   | XML Event context                                          |
| `index`   | `IN`   | index of the attribute; ignored for `XML_EVENT_START_ATTR` |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrName()

Retrieves the attribute name for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrName(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description                                                |
|:----------|:-------|:-----------------------------------------------------------|
| `evctx`   | `IN`   | XML Event context                                          |
| `index`   | `IN`   | index of the attribute; ignored for `XML_EVENT_START_ATTR` |
| `len`     | `OUT`  | the length                                                 |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrName0()

Retrieves the `NULL`-terminated attribute name for the `XML_EVENT_START_ELEMENT` events.

#### Syntax

    oratext *XmlEvGetAttrName0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description                                                |
|:----------|:-------|:-----------------------------------------------------------|
| `evctx`   | `IN`   | XML Event context                                          |
| `index`   | `IN`   | index of the attribute; ignored for `XML_EVENT_START_ATTR` |

#### Returns

`(oratext*)` the attribute name

### XmlEvGetAttrPrefix()

Retrieves the prefix tag for `XML_EVENT_START_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrPrefix(
       xmlevctx *evctx,
       ub4 index,
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `index`   | `IN`   | index of the attribute   |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` the attribute prefix

### XmlEvGetAttrPrefix0()

Retrieves the `NULL`-terminated attribute prefix for the `XML_EVENT_START_ELEMENT` events.

#### Syntax

    oratext *XmlEvGetAttrPrefix0(
       xmlevctx *evctx);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the attribute prefix

### XmlEvGetAttrURI()

Retrieves the attribute URI for the `XML_EVENT_START_ELEMENT` events. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrURI(
       xmlevctx *evctx,
       ub4 index
       ub4 *len);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |
| `len`     | `OUT`  | the length             |

#### Returns

`(oratext*)` the attribute URI

### XmlEvGetAttrURI0()

Retrieves the `NULL`-terminated attribute URI for the `XML_EVENT_START_ELEMENT` events.

#### Syntax

    oratext *XmlEvGetAttrURI0(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the attribute URI

### XmlEvGetAttrUriID()

Retrieves the ID for the attribute's URI, for `XML_EVENT_START_ELEMENT` events. Invokes the user-supplied ID callback specified in XmlEvCreatePPCtx(); if the callback is not specified, returns `0`.

#### Syntax

    sb8 XmlEvGetAttrUriID(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `evctx`   | `IN`   | XML Event context  |
| `index`   | `IN`   | index of attribute |

#### Returns

`(sb8)` the ID

### XmlEvGetAttrValue()

Retrieves the attribute value for one of the `XML_EVENT_START_ELEMENT` events, and also returns the length of the event as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetAttrValue(
       xmlevctx *evctx,
       ub4 index,
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `index`   | `IN`   | index of the attribute   |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` the attribute value

### XmlEvGetAttrValue0()

Retrieves the `NULL`-terminated attribute value for the `XML_EVENT_START_ELEMENT` events.

#### Syntax

    oratext *XmlEvGetAttrValue0(
       xmlevctx *evctx);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`(oratext*)` the attribute value

### XmlEvGetElDeclContent()

Retrieves the element declaration content for `XML_EVENT_ELEMENT_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetElDeclContent(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `len`     | `OUT`  | the length        |

#### Returns

`(oratext*)` the declaration content

### XmlEvGetElDeclContent0()

Retrieves the element declaration content for `XML_EVENT_ELEMENT_DECLARATION`.

#### Syntax

    oratext *XmlEvGetElDeclContent0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` the declaration content

### XmlEvGetEncoding()

Returns the value of the encoding specified in either XmlEvCreatePPCtx() call or XmlEvCreateSVCtx() call.

#### Syntax

    oratext *XmlEvGetEncoding(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` the encoding value in out-encoding; `NULL` if no encoding is specified

### XmlEvGetError()

Retrieves the error number when the `XML_EVENT_FATAL_ERROR` or `XML_EVENT_ERROR` event is returned by a XmlEvNext() call.

#### Syntax

    xmlerr XmlEvGetError(
       xmlevctx *evctx
       oratext **message);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `message` | `IN`   | the error message |

#### Returns

`(xmlerr)` the error number

### XmlEvGetName()

Retrurns the name of the events, and the length of the event in the `OUT` `len` parameter. The event name could be on of the following:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

- `XML_EVENT_START_ENTITY`

- `XML_EVENT_ENTITY_REFERENCE`

- `XML_EVENT_ELEMENT_DECLARATION`

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATTION_DECLARATION`

#### Syntax

    oratext *XmlEvGetName(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `evctx`   | `IN`   | XML Event context  |
| `len`     | `OUT`  | length of the name |

#### Returns

`(oratext*)` The name

### XmlEvGetName0()

Retrieves a `NULL`-terminated name for one of the following events:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

- `XML_EVENT_START_ENTITY`

- `XML_EVENT_ENTITY_REFERENCE`

- `XML_EVENT_ELEMENT_DECLARATION`

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATTION_DECLARATION`

#### Syntax

    oratext *XmlEventGetName0(
       xmleventctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` The name

### XmlEvGetLocalName()

Retrieves the local name tag for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetLocalName(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` local name tag

### XmlEvGetLocalName0()

Retrieves the `NULL`-terminated local name tag for one of the following events:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetLocalName0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` local name tag

### XmlEvGetLocation()

Retrieves the location during parsing, as `OUT` parameters for the line number of the input stream and its path. Can be used at any time during the parsing processes.

#### Syntax

    void *XmlEvGetLocation(
       xmlevctx *evctx,
       ub4 *line,
       oratext **path);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `line`    | `OUT`  | line number       |
| `path`    | `OUT`  | URL or file name  |

### XmlEvGetPIData()

Retrieves the text for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_PI`

- `XML_EVENT_PI_CONT`

#### Syntax

    oratext *XmlEvGetPIData(
       xmlevctx *evctx
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` data

### XmlEvGetPIData0()

Retrieves the `NULL`-terminated data for one of the following events:

- `XML_EVENT_PI`

- `XML_EVENT_PI_CONT`

#### Syntax

    oratext *XmlEvGetPIData0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` data

### XmlEvGetPITarget()

Retrieves the target for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_PI`

- `XML_EVENT_PI_CONT`

#### Syntax

    oratext *XmlEvGetPITarget(
       xmlevctx *evctx
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` target

### XmlEvGetPITarget0()

Retrieves the `NULL`-terminated target for one of the following events:

- `XML_EVENT_PI`

- `XML_EVENT_PI_CONT`

#### Syntax

    oratext *XmlEvGetPITarget0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` target

### XmlEvGetPEIsGen()

Determines if the general entity was declared, `XML_EVENT_PE_DECLARATION`.

#### Syntax

    boolean XmlEvGetPEIsGen(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`TRUE` for a general entity, `FALSE` if a parameter

### XmlEvGetPERepl()

Retrieves the replacement text of PE declaration, `XML_EVENT_PE_DECLARATION`. Also, provides the length as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetPERepl(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `len`     | `OUT`  | the length        |

#### Returns

`(oratext*)` PE replacement text

### XmlEvGetPERepl0()

Retrieves the `NULL`-terminated replacement text of PE declaration, `XML_EVENT_PE_DECLARATION`.

#### Syntax

    oratext *XmlEvGetPERepl0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` PE replacement text

### XmlEvGetPrefix()

Retrieves the prefix tag for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetPrefix(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description          |
|:----------|:-------|:---------------------|
| `evctx`   | `IN`   | XML Event context    |
| `len`     | `OUT`  | length of the prefix |

#### Returns

`(oratext*)` the prefix tag

### XmlEvGetPrefix0()

Retrieves the `NULL`-terminated prefix tag for one of the following events:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetPrefix0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` the prefix tag

### XmlEvGetPubId()

Retrieves the public id for one of the following events; also, provides the length as an `OUT len` parameter:

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATION_DECLARATION`

#### Syntax

    oratext *XmlEvGetPubId(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `len`     | `OUT`  | the length        |

#### Returns

`(oratext*)` public id

### XmlEvGetPubId0()

Retrieves the `NULL`-terminated public id for one of the following events:

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATION_DECLARATION`

#### Syntax

    oratext *XmlEvGetPubId0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returnsb

`(oratext*)` public id

### XmlEvGetSysId()

Retrieves the system id for one of the following events; also, provides the length as an `OUT len` parameter:

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATION_DECLARATION`

#### Syntax

    oratext *XmlEvGetSysId(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |
| `len`     | `OUT`  | the length        |

#### Returns

`(oratext*)` system id

### XmlEvGetSysId0()

Retrieves the `NULL`-terminated system id for one of the following events:

- `XML_EVENT_PE_DECLARATION`

- `XML_EVENT_UE_DECLARATION`

- `XML_EVENT_NOTATION_DECLARATION`

#### Syntax

    oratext *XmlEvGetSysId0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` system id

### XmlEvGetTagID()

Retrieves the ID for the tag's `QNAME`, for `XML_EVENT_START_ELEMENT` events. Invokes the user-supplied ID callback specified in XmlEvCreatePPCtx(); if the callback is not specified, returns `0`.

#### Syntax

    sb8 XmlEvGetTagID(
       xmlevctx *evctx)

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(sb8)` the ID

### XmlEvGetTagUriID()

Retrieves the ID for the tag's URI, for `XML_EVENT_START_ELEMENT` and `XML_EVENT_END_ELEMENT` events. Invokes the user-supplied ID callback specified in XmlEvCreatePPCtx(); if the callback is not specified, returns `0`.

#### Syntax

    sb8 XmlEvGetTagUriID(
       xmlevctx *evctx)

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(sb8)` the ID

### XmlEvGetText()

Retrieves the text for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_CHARACTERS`

- `XML_EVENT_CHARACTERS_CONT`

- `XML_EVENT_SPACE`

- `XML_EVENT_SPACE_CONT`

- `XML_EVENT_COMMENT`

- `XML_EVENT_COMMENT_CONT`

- `XML_EVENT_CDATA`

- `XML_EVENT_CDATA_CONT`

#### Syntax

    oratext *XmlEvGetText(
       xmlevctx *evctx
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` event text

### XmlEvGetText0()

Retrieves the `NULL`-terminated text for one of the following events:

- `XML_EVENT_CHARACTERS`

- `XML_EVENT_CHARACTERS_CONT`

- `XML_EVENT_SPACE`

- `XML_EVENT_SPACE_CONT`

- `XML_EVENT_COMMENT`

- `XML_EVENT_COMMENT_CONT`

- `XML_EVENT_CDATA`

- `XML_EVENT_CDATA_CONT`

#### Syntax

    oratext *XmlEvGetText0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` event text

### XmlEvGetUENdata()

Retrieves the ndata for `XML_EVENT_UE_DECLARATION` event, and also returns the length of the event as an `OUT len` parameter.

#### Syntax

    oratext *XmlEvGetUENdata(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` ndata

### XmlEvGetUENdata0()

Retrieves the `NULL`-terminated ndata for `XML_EVENT_UE_DECLARATION` event.

#### Syntax

    oratext *XmlEvGetUENdata0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` ndata

### XmlEvGetURI()

Retrieves the URI tag for one of the following events, and also returns the length of the event as an `OUT len` parameter:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetURI(
       xmlevctx *evctx,
       ub4 *len);

| Parameter | In/Out | Description              |
|:----------|:-------|:-------------------------|
| `evctx`   | `IN`   | XML Event context        |
| `len`     | `OUT`  | length of the event name |

#### Returns

`(oratext*)` URI tag

### XmlEvGetURI0()

Retrieves the `NULL`-terminated URI tag for one of the following events:

- `XML_EVENT_START_ELEMENT`

- `XML_EVENT_END_ELEMENT`

#### Syntax

    oratext *XmlEvGetURI0(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` URI tag

### XmlEvGetVersion()

Provides information about version specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event.

#### Syntax

    oratext *XmlEvGetVersion(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(oratext*)` version string from the XML declaration.

### XmlEvIsEncodingSpecified()

Provides information about encoding specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event.

#### Syntax

    boolean XmlEvIsEncodingSpecified(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`TRUE` if encoding was specified in XML declaration, `FALSE` otherwise

### XmlEvIsNamespaceAttr()

Determines if an attribute is a namespace atrribute for `XML_EVENT_START_ELEMENT` event.

#### Syntax

    boolean XmlEvIsNamespaceAttr(
       xmlevctx *evctx,
       ub4 index);

| Parameter | In/Out | Description            |
|:----------|:-------|:-----------------------|
| `evctx`   | `IN`   | XML Event context      |
| `index`   | `IN`   | index of the attribute |

#### Returns

`TRUE` if an attribute is a namespace attribute, `FALSE` otherwise

### XmlEvIsStandalone()

Provides information about standalone specification in XML declaration for the `XML_EVENT_START_DOCUMENT` event.

#### Syntax

    sword  XmlEvIsStandalone(
       xmlevctx *evctx);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `evctx`   | `IN`   | XML Events contextt |

#### Returns

`(sword) ` `-1 ` if standalone was not specified in the XML declaration, `0` if `FALSE` was specified for standalone, and `1` if `TRUE` was specified for standalone

### XmlEvNext()

Gets the next event; advances the parser.

#### Syntax

    xmlevtype XmlEvNext(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(xmlevtype)` the event

### XmlEvNextTag()

Advances the parser to the next tag event, such as `XML_EVENT_START_ELEMENT`, `XML_EVENT_END_ELEMENT`, and `XML_EVENT_END_DOCUMENT`.

#### Syntax

    xmlevtype XmlEvNextTag(
       xmlevctx *evctx);

| Parameter | In/Out | Description       |
|:----------|:-------|:------------------|
| `evctx`   | `IN`   | XML Event context |

#### Returns

`(xmlevtype)` the event

### XmlEvLoadPPDoc()

Loads a new document and sets it up for pull parsing. Prepares to start parsing the XML document from an input source in pull-parse mode. Input sources are the same as for [XmlLoadDom()](package-XML-API.md)[XmlLoadDom()](package-XML-API.md) and [XmlLoadSax()](package-XML-API.md)[XmlLoadSax()](package-XML-API.md) of [Package XML APIs for C](package-XML-API.md). The actual parsing is driven by multiple calls to XmlEvNext().

#### Syntax

    xmlerr XmlEvLoadPPDoc(
       xmlctx *xctx,
       xmlevctx *evctx,
       oratext *inputType,
       void *input,
       ub4 inputLen,
       oratext *inputEncoding);

| Parameter       | In/Out | Description                                                |
|:----------------|:-------|:-----------------------------------------------------------|
| `xctx`          | `IN`   | XML context                                                |
| `evctx`         | `IN`   | XML Events contextt                                        |
| `inputType`     | `IN`   | type of input, such as file, buffer, uri, stream, or stdio |
| `input`         | `IN`   | the input                                                  |
| `inputLen`      | `IN`   | input length for buffer input type                         |
| `inputEncoding` | `IN`   | input encoding                                             |

#### Returns

`(xmlerr)` the error code

### XmlEvSchemaValidate()

Validates XML documents represented by events. Initializes the stream validator.

This is an opaque method. An alternate approach would be to use the transparent XmlEvCreateSVCtx()XmlEvCreateSVCtx() and XmlEvDestroySVCtx()XmlEvDestroySVCtx().

#### Syntax

    xmlerr XmlEvSchemaValidate(
       xmlctx *xctx,
       xsdctx *sctx,
       xmlevctx *docEvCtx,
       oratext **errmsg);

| Parameter  | In/Out | Description                                          |
|:-----------|:-------|:-----------------------------------------------------|
| `xctx`     | `IN`   | XML context                                          |
| `sctx`     | `IN`   | Schema context                                       |
| `docEvCtx` | `IN`   | Event context for the document that is validated     |
| `errmsg`   | `OUT`  | The error message that corresponds to the error code |

#### Returns

`(xmlerr)` the error code
