SAX is a standard interface for event-based XML parsing, developed collaboratively by the members of the XML-DEV mailing list. To use SAX, an `xmlsaxcb` structure is initialized with function pointers and passed to one of the `XmlLoadSax` calls. A pointer to a user-defined context structure is also provided, and will be passed to each SAX function.

For event-based schema validation APIs, refer to [Package Event APIs for C](package-Event-API.md).

The following table summarizes the methods available through the `SAX` interface for XML C APIs.

Table 7-1 Summary of SAX Methods for XML C Implementation

| Function                   | Summary                                                                     |
|:---------------------------|:----------------------------------------------------------------------------|
| XmlSaxAttributeDecl()      | Receives SAX notification of an attribute's declaration.                    |
| XmlSaxCDATA()              | Receives SAX notification of `CDATA`. Oracle extension.                     |
| XmlSaxCharacters()         | Receives SAX notification of character data                                 |
| XmlSaxComment()            | Receives SAX notification of a comment.                                     |
| XmlSaxElementDecl()        | Receives SAX notification of an element's declaration. Oracle extension.    |
| XmlSaxEndDocument()        | Receives SAX end-of-document notification.                                  |
| XmlSaxEndElement()         | Receives SAX end-of-element notification.                                   |
| XmlSaxNotationDecl()       | Receives SAX notification of a notation declaration.                        |
| XmlSaxPI()                 | Receives SAX notification of a processing instruction.                      |
| XmlSaxParsedEntityDecl()   | Receives SAX notification of a parsed entity declaration. Oracle extension. |
| XmlSaxStartDocument()      | Receives SAX start-of-document notification.                                |
| XmlSaxStartElement()       | Receives SAX start-of-element notification.                                 |
| XmlSaxStartElementNS()     | Receives SAX namespace-aware start-of-element notification.                 |
| XmlSaxUnparsedEntityDecl() | Receives SAX notification of an unparsed entity declaration.                |
| XmlSaxWhitespace()         | Receives SAX notification of ignorable (whitespace) data.                   |
| XmlSaxXmlDecl()            | Receives SAX notification of an XML declaration. Oracle extension.          |

### XmlSaxAttributeDecl()

This event marks an element declaration in the DTD. The element's name and content will be in the data encoding. Note that an attribute may be declared before the element it belongs to!

#### Syntax

    xmlerr XmlSaxAttributeDecl(
       void *ctx,
       oratext *elem,
       oratext *attr,
       oratext *body);

| Parameter | In/Out | Description                                                |
|:----------|:-------|:-----------------------------------------------------------|
| `ctx`     | `IN`   | user's SAX context                                         |
| `elem`    | `IN`   | element for which the attribute is declared; data encoding |
| `attr`    | `IN`   | attribute's name; data encoding                            |
| `body`    | `IN`   | body of an attribute declaration                           |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxAttributeDecl()

### XmlSaxBeginGen()

This call creates an XML generation context from the specified XML meta context. This context is uded by the SAX calls to generate an incremental XML document.

#### Syntax

    void *XmlSaxBeginGen(
       XmlCtx *xctx);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `xctx`    | `IN`   | the XML meta contextt |

### XmlSaxCDATA()

This event handles `CDATA`, as distinct from `Text`. If no `XmlSaxCDATA` callback is provided, the Text callback will be invoked. The data will be in the data encoding, and the returned length is in characters, not bytes. See also `XmlSaxWhitespace`, which receiving notification about ignorable (whitespace formatting) character data.

#### Syntax

    xmlerr XmlSaxCDATA(
       void *ctx,
       oratext *ch,
       size_t len);

| Parameter | In/Out | Description                       |
|:----------|:-------|:----------------------------------|
| `ctx`     | `IN`   | user's SAX context                |
| `ch`      | `IN`   | pointer to `CDATA`; data encoding |
| `len`     | `IN`   | length of `CDATA`, in characters  |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxWhitespace()

### XmlSaxCharacters()

This event marks character data, either `Text` or `CDATA`. If an `XmlSaxCDATA` callback is provided, then `CDATA` will be send to that instead; with no `XmlSaxCDATA` callback, both `Text` and `CDATA` go to the `XmlSaxCharacters` callback. The data will be in the data encoding, and the returned length is in characters, not bytes. See also `XmlSaxWhitespace`, which receiving notification about ignorable (whitespace formatting) character data.

#### Syntax

    xmlerr XmlSaxCharacters(
       void *ctx,
       oratext *ch,
       size_t len);

| Parameter | In/Out | Description                    |
|:----------|:-------|:-------------------------------|
| `ctx`     | `IN`   | user's SAX context             |
| `ch`      | `IN`   | pointer to data; data encoding |
| `len`     | `IN`   | length of data, in characters  |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxWhitespace()

### XmlSaxComment()

This event marks a comment in the XML document. The comment's data will be in the data encoding. Oracle extension, not in SAX standard.

#### Syntax

    xmlerr XmlSaxComment(
       void *ctx,
       oratext *data);

| Parameter | In/Out | Description                   |
|:----------|:-------|:------------------------------|
| `ctx`     | `IN`   | user's SAX context            |
| `data`    | `IN`   | comment's data; data encoding |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

### XmlSaxElementDecl()

This event marks an element declaration in the DTD. The element's name and content will be in the data encoding.

#### Syntax

    xmlerr XmlSaxElementDecl(
       void *ctx,
       oratext *name,
       oratext *content);

| Parameter | In/Out | Description             |
|:----------|:-------|:------------------------|
| `ctx`     | `IN`   | user's SAX context      |
| `name`    | `IN`   | element's name          |
| `content` | `IN`   | element's context model |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxAttributeDecl()

### XmlSaxEndDocument()

The last SAX event, called once for each document, indicating the end of the document. Matching event is `XmlSaxStartDocument`.

#### Syntax

    xmlerr XmlSaxEndDocument(
       void *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | user's SAX context |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxStartDocument()

### XmlSaxEndElement()

This event marks the close of an element; it matches the `XmlSaxStartElement` or `XmlSaxStartElementNS` events. The name is the `tagName` of the element (which may be a qualified name for namespace-aware elements) and is in the data encoding.

### XmlSaxEndGen()

Completes the generation of an incrementally constructed XML document, and returns it to the application.

#### Syntax

    orastream *XmlSaxEndGen(
       void *genCtx);

| Parameter | In/Out | Description                                                                                   |
|:----------|:-------|:----------------------------------------------------------------------------------------------|
| `genCtx`  | `IN`   | the generation context used to create the XML document; see XmlSaxBeginGen()XmlSaxBeginGen()t |

#### Return

`(orastream*)` the stream containing the generated XML document

### XmlSaxNotationDecl()

The even marks the declaration of a notation in the DTD. The notation's name, public ID, and system ID will all be in the data encoding. Both IDs are optional and may be `NULL`.

### XmlSaxPI()

This event marks a `ProcessingInstruction`. The `ProcessingInstruction`s target and data will be in the data encoding. There is always a target, but the data may be `NULL`.

#### Syntax

    xmlerr XmlSaxPI(
       void *ctx,
       oratext *target,
       oratext *data);

| Parameter | In/Out | Description                           |
|:----------|:-------|:--------------------------------------|
| `ctx`     | `IN`   | user's SAX context                    |
| `target`  | `IN`   | PI's target; data encoding            |
| `data`    | `IN`   | PI's data as data encoding, or `NULL` |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

### XmlSaxParsedEntityDecl()

Marks an parsed entity declaration in the DTD. The parsed entity's name, public ID, system ID, and notation name will all be in the data encoding.

#### Syntax

    xmlerr XmlSaxParsedEntityDecl(
       void *ctx,
       oratext *name,
       oratext *value,
       oratext *pubId,
       oratext *sysId,
       boolean general);

| Parameter | In/Out | Description                                           |
|:----------|:-------|:------------------------------------------------------|
| `ctx`     | `IN`   | user's SAX context                                    |
| `name`    | `IN`   | entity's name; data encoding                          |
| `value`   | `IN`   | entity's value; data encoding                         |
| `pubId`   | `IN`   | entity's public ID as data encoding, or `NULL`        |
| `sysId`   | `IN`   | entity's system ID; data encoding                     |
| `general` | `IN`   | `TRUE` if general entity, `FALSE` if parameter entity |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxUnparsedEntityDecl()

### XmlSaxStartDocument()

The first SAX event, called once for each document, indicating the start of the document. Matching event is `XmlSaxEndDocument`.

#### Syntax

    xmlerr XmlSaxStartDocument(
       void *ctx);

| Parameter | In/Out | Description        |
|:----------|:-------|:-------------------|
| `ctx`     | `IN`   | user's SAX context |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxEndDocument()

### XmlSaxStartElement()

This event marks the start of an element. Note this is the original SAX 1 non-namespace-aware version; `XmlSaxStartElementNS` is the SAX 2 namespace-aware version. If both are registered, only the NS version will be called. The element's name will be in the data encoding, as are all the attribute parts. See the functions in the `NamedNodeMap` interface for operating on the attributes map. The matching function is `XmlSaxEndElement` (there is no namespace aware version of this function).

#### Syntax

    xmlerr XmlSaxStartElement(
       void *ctx,
       oratext *name,
       xmlnodelist *attrs);

| Parameter | In/Out | Description                            |
|:----------|:-------|:---------------------------------------|
| `ctx`     | `IN`   | user's SAX context                     |
| `name`    | `IN`   | element's name; data encoding          |
| `attrs`   | `IN`   | `NamedNodeMap` of element's attributes |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxEndElement(), [XmlDomGetNodeMapLength()](package-DOM-API.md) and [XmlDomRemoveNamedItem()](package-DOM-API.md) in [Package DOM APIs for C](package-DOM-API.md)

### XmlSaxStartElementNS()

This event marks the start of an element. Note this is the new SAX 2 namespace-aware version; XmlSaxStartElement is the SAX 1 non-namespace-aware version. If both are registered, only the NS version will be called. The element's qualified name, local name, and namespace URI will be in the data encoding, as are all the attribute parts. See the functions in the `NamedNodeMap` interface for operating on the attributes map. The matching function is `XmlSaxEndElement` (there is no namespace aware version of this function).

#### Syntax

    xmlerr XmlSaxStartElementNS(
       void *ctx,
       oratext *qname,
       oratext *local,
       oratext *nsp,
       xmlnodelist *attrs);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `ctx`     | `IN`   | user's SAX context                            |
| `qname`   | `IN`   | element's qualified name; data encoding       |
| `local`   | `IN`   | element's namespace local name; data encoding |
| `nsp`     | `IN`   | element's namespace URI; data encoding        |
| `attrs`   | `IN`   | `NodeList` of element's attributes, or `NULL` |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxStartElement(), XmlSaxEndElement(), [XmlDomGetNodeMapLength()](package-DOM-API.md) and [XmlDomRemoveNamedItem()](package-DOM-API.md) in [Package DOM APIs for C](package-DOM-API.md)

### XmlSaxUnparsedEntityDecl()

Marks an unparsed entity declaration in the DTD, see `XmlSaxParsedEntityDecl` for the parsed entity version. The unparsed entity's name, public ID, system ID, and notation name will all be in the data encoding.

#### Syntax

    xmlerr XmlSaxUnparsedEntityDecl(
       void *ctx,
       oratext *name,
       oratext *pubId,
       oratext *sysId,
       oratext *note);

| Parameter | In/Out | Description                                    |
|:----------|:-------|:-----------------------------------------------|
| `ctx`     | `IN`   | user's SAX context                             |
| `name`    | `IN`   | entity's name; data encoding                   |
| `pubId`   | `IN`   | entity's public ID as data encoding, or `NULL` |
| `sysId`   | `IN`   | entity's system ID; data encoding              |
| `note`    | `IN`   | entity's notation name; data encoding          |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxParsedEntityDecl()

### XmlSaxWhitespace()

This event marks ignorable whitespace data such as newlines, and indentation between lines. The matching function is `XmlSaxCharacters`, which receives notification of normal character data. The data is in the data encoding, and the returned length is in characters, not bytes.

#### Syntax

    xmlerr XmlSaxWhitespace(
       void *ctx,
       oratext *ch,
       size_t len);

| Parameter | In/Out | Description                    |
|:----------|:-------|:-------------------------------|
| `ctx`     | `IN`   | user's SAX context             |
| `ch`      | `IN`   | pointer to data; data encoding |
| `len`     | `IN`   | length of data, in characters  |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success

**See Also:**

XmlSaxCharacters()

### XmlSaxXmlDecl()

This event marks an XML declaration. The `XmlSaxStartDocument` event is always first; if this callback is registered and an `XMLDecl` exists, it will be the second event. The encoding flag says whether an encoding was specified. Since the document's own encoding specification may be overridden (or wrong), and the input will be converted to the data encoding anyway, the actual encoding specified in the document is not provided. For the standalone flag, `-1` will be returned if it was not specified, otherwise `0` for `FALSE`, 1 for `TRUE`.

#### Syntax

    xmlerr XmlSaxXmlDecl(
       void *ctx,
       oratext *version,
       boolean encoding,
       sword standalone);

| Parameter    | In/Out | Description                                              |
|:-------------|:-------|:---------------------------------------------------------|
| `ctx`        | `IN`   | user's SAX context                                       |
| `version`    | `IN`   | version string from XMLDecl; data encoding               |
| `encoding`   | `IN`   | whether encoding was specified                           |
| `standalone` | `IN`   | value of the standalone document; `< 0` if not specified |

#### Returns

`(xmlerr)` error code, `XMLERR_OK [0]` for success
