This C implementation of the XML schema validator follows the W3C XML Schema specification, rev REC-xmlschema-1-20010502. It implements the required behavior of a schema validator for multiple schema documents to be assembled into a schema. This resulting schema can be used to validate a specific instance document.

For event-based schema validation, see the methods documented in [Package Event APIs for C](package-Event-API.md).

The following table summarizes the methods available through the `Schema` interface for XML C APIs.

Table 8-1 Summary of Schema Methods for XML C Implementation

| Function                      | Summary                                                                      |
|:------------------------------|:-----------------------------------------------------------------------------|
| XmlSchemaClean()              | Cleans up loaded schemas in a schema context and recycle the schema context. |
| XmlSchemaCreate()             | Creates and returns a schema context.                                        |
| XmlSchemaDestroy()            | Destroys a schema context.                                                   |
| XmlSchemaErrorWhere()         | Returns the location where an error occurred.                                |
| XmlSchemaLoad()               | Loads a schema document.                                                     |
| XmlSchemaLoadedList()         | Returns the size and/or list of loaded schema documents.                     |
| XmlSchemaSetErrorHandler()    | Sets an error message handler and its associated context in a schema context |
| XmlSchemaSetValidateOptions() | Sets option(s) to be used in the next validation session.                    |
| XmlSchemaTargetNamespace()    | Returns target namespace of a given schema document.                         |
| XmlSchemaUnload()             | Unloads a schema document.                                                   |
| XmlSchemaValidate()           | Validates an element node against a schema.                                  |
| XmlSchemaVersion()            | Returns the version of this schema implementation.                           |

### XmlSchemaCreate()

Return a schema context to be used in other validator APIs. This needs to be paired with an `XmlSchemaDestroy`.

#### Syntax

    xsdctx *XmlSchemaCreate(
       xmlctx *xctx,
       xmlerr *err,
       list);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `err`     | `OUT`  | returned error code                          |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(xsdctx *)` schema context

**See Also:**

XmlSchemaDestroy(), [XmlCreate()](package-XML-API.md) in [Package XML APIs for C](package-XML-API.md)

### XmlSchemaDestroy()

Destroy a schema context and free up all its resources.

#### Syntax

    void XmlSchemaDestroy(
       xsdctx *sctx);

| Parameter | In/Out | Description                |
|:----------|:-------|:---------------------------|
| `sctx`    | `IN`   | schema context to be freed |

**See Also:**

XmlSchemaCreate()

### XmlSchemaErrorWhere()

Returns the location (line#, path) where an error occurred.

#### Syntax

    xmlerr XmlSchemaErrorWhere(
       xsdctx *sctx,
       ub4 *line,
       oratext **path);

| Parameter | In/Out   | Description                           |
|:----------|:---------|:--------------------------------------|
| `sctx`    | `IN`     | schema context                        |
| `line`    | `IN/OUT` | line number where error occurred      |
| `path`    | `IN/OUT` | URL or filespace where error occurred |

#### Returns

`(xmlerr)` error code

**See Also:**

XmlSchemaSetErrorHandler()

### XmlSchemaLoad()

Load up a schema document to be used in the next validation session. Schema documents can be incrementally loaded into a schema context as long as every loaded schema document is valid. When the last loaded schema turns out to be invalid, you need to clean up the schema context by calling XmlSchemaClean()XmlSchemaClean() and reload everything all over again including the last schema with appropriate correction.

Given a schema document, this function converts the DOM representation into an internal schema representation. The schema document can be provided as a URI or directly a DOM representation. In the URI case, this function reads the input stream and builds a DOM representation of the schema before converting it into internal representation. In the DOM case, the application can provide a DOM representation of the schema, which will be used to create the internal schema representation.

#### Syntax

    xmlerr XmlSchemaLoad(
       xsdctx *sctx,
       oratext *uri,
       list);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `sxctx`   | `IN`   | schema context                               |
| `uri`     | `IN`   | URL of schema document; compiler encoding    |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSchemaUnload(), XmlSchemaLoadedList()

### XmlSchemaLoadedList()

Return only the size of loaded schema documents if `list` is `NULL`. If `list` is not `NULL`, a list of URL pointers are returned in the user-provided pointer buffer. Note that its user's responsibility to provide a buffer with big enough size.

#### Syntax

    ub4 XmlSchemaLoadedList(
       xsdctx *sctx,
       oratext **list);

| Parameter | In/Out | Description               |
|:----------|:-------|:--------------------------|
| `sctx`    | `IN`   | schema context            |
| `list`    | `IN`   | address of pointer buffer |

#### Returns

`(ub4)` list size

**See Also:**

XmlSchemaLoad(), XmlSchemaUnload()

### XmlSchemaSetErrorHandler()

Sets an error message handler and its associated context in a schema context. To retrieve useful location information on errors, the address of the schema context must be provided in the error handler context.

#### Syntax

    xmlerr XmlSchemaSetErrorHandler(
       xsdctx *sctx,
       XML_ERRMSG_F(
          (*errhdl),
          ectx,
          msg,
          err),
       void *errctx);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `sctx`    | `IN`   | schema context        |
| `errhdl`  | `IN`   | error message handler |
| `errctx`  | `IN`   | error handler context |

#### Returns

`(xmlerr)` error code

**See Also:**

XmlSchemaCreate(), XmlSchemaErrorWhere(), and [XML_ERRMSG_F()](package-callback-API.md) in [Package Callback APIs for C](package-callback-API.md)

### XmlSchemaSetValidateOptions()

Set options to be used in the next validation session. Previously set options will remain effective until they are overwritten or reset.

#### Syntax

    xmlerr XmlSchemaSetValidateOptions(
       xsdctx *sctx,
       list);

| Parameter | In/Out | Description                                 |
|:----------|:-------|:--------------------------------------------|
| `sctx`    | `IN`   | schema context                              |
| `list`    | `IN`   | `NULL`-terminated list of variable argument |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSchemaValidate()

### XmlSchemaTargetNamespace()

Return target namespace of a given schema document identified by its URI. All currently loaded schema documents can be queried. Currently loaded schema documents include the ones loaded through `XmlSchemaLoad`s and the ones loaded through `schemaLocation` or `noNamespaceSchemaLocation` hints.

#### Syntax

    oratext *XmlSchemaTargetNamespace(
       xsdctx *sctx,
       oratext *uri);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `sctx`    | `IN`   | XML context                              |
| `uri`     | `IN`   | URL of the schema document to be queried |

#### Returns

`(oratext *)` target namespace string; `NULL` if given document not

**See Also:**

XmlSchemaLoadedList()

### XmlSchemaUnload()

Unload a schema document from the validator. All previously loaded schema documents will remain loaded until they are unloaded. To unload all loaded schema documents, set URI to be `NULL` (this is equivalent to `XmlSchemaClean`). Note that all children schemas associated with the given schema are also unloaded. In this implementation, it only support the following scenarios:

- load, load, ...

- load, load, load, unload, unload, unload, clean, and then repeat.

It doesn't not support: load, load, unload, load, ....

#### Syntax

    xmlerr XmlSchemaUnload(
       xsdctx *sctx,
       oratext *uri,
       list);

| Parameter | In/Out | Description                                   |
|:----------|:-------|:----------------------------------------------|
| `sctx`    | `IN`   | schema context                                |
| `uri`     | `IN`   | URL of the schema document; compiler encoding |
| `list`    | `IN`   | `NULL`-terminated list of variable argument   |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSchemaLoad(), XmlSchemaLoadedList()

### XmlSchemaValidate()

Validates an element node against a schema. Schemas used in current session consists of all schema documents specified through `XmlSchemaLoad` and provided as hint(s) through schemaLocation or `noNamespaceSchemaLocation` in the instance document. After the invocation of this routine, all loaded schema documents remain loaded and can be queried by `XmlSchemaLoadedList`. However, they will remain inactive. In the next validation session, inactive schema documents can be activated by specifying them through `XmlSchemaLoad` or providing them as hint(s) through schemaLocation or `noNamespaceSchemaLocation` in the new instance document. To unload a schema document and all its descendants (documents included or imported in a nested manner), use `XmlSchemaUnload`.

#### Syntax

    xmlerr XmlSchemaValidate(
       xsdctx *sctx,
       xmlctx *xctx,
       xmlelemnode *elem);

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `sctx`    | `IN`   | schema context                           |
| `xctx`    | `IN`   | XML top-level context                    |
| `elem`    | `IN`   | element node in the doc, to be validated |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSchemaSetValidateOptions()

### XmlSchemaVersion()

Return the version of this schema implementation.

#### Syntax

    oratext *XmlSchemaVersion();

#### Returns

`(oratext *)` version string \[compiler encoding\]

### XmlSchemaClean()

Clean up loaded schemas in a schema context and recycle the schema context.

#### Syntax

    void XmlSchemaClean(
       xsdctx *sctx);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `sctx`    | `IN`   | schema context to be cleaned |

**See Also:**

XmlSchemaCreate(), XmlSchemaDestroy()
