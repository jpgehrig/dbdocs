This C implementation of the XML processor (or parser) follows the W3C XML specification (rev REC-xml-19980210) and implements the required behavior of an XML processor in terms of how it must read XML data and the information it must provide to the application.

The following table summarizes the methods available through the `XML` package for XML C APIs.

Table 11-1 Summary of XML Methods for XML C Implementation

| Function            | Summary                                                                 |
|:--------------------|:------------------------------------------------------------------------|
| XmlAccess()         | Set access method callbacks for URL.                                    |
| XmlCreate()         | Create an XML Developer's Toolkit `xmlctx`.                             |
| XmlCreateDTD()      | Create DTD.                                                             |
| XmlCreateDocument() | Create Document (node).                                                 |
| XmlDestroy()        | Destroy an `xmlctx`.                                                    |
| XmlDiff()           | Compares two XML documents.                                             |
| XmlFreeDocument()   | Free a document (releases all resources).                               |
| XmlGetEncoding()    | Returns data encoding in use by XML context.                            |
| XmlHasFeature()     | Determine if DOM feature is implemented.                                |
| XmlIsSimple()       | Returns single-byte (simple) characterset flag.                         |
| XmlIsUnicode()      | Returns `XmlIsUnicode` (simple) characterset flag.                      |
| XmlLoadDom()        | Load (parse) an XML document and produce a DOM.                         |
| XmlLoadSax()        | Load (parse) an XML document from and produce SAX events.               |
| XmlLoadSaxVA()      | Load (parse) an XML document from and produce SAX events \[`varargs`\]. |
| XmlSaveDom()        | Saves (serializes, formats) an XML document.                            |
| XmlVersion()        | Returns version string for XDK.                                         |

### XmlAccess()

Sets the open/read/close callbacks used to load data for a specific URL access method. Overrides the built-in data loading functions for HTTP, FTP, and so on, or provides functions to handle new types, such as `UNKNOWN`.

#### Syntax

    xmlerr XmlAccess(
       xmlctx *xctx,
       xmlurlacc access,
       void *userctx,
       XML_ACCESS_OPEN_F(
          (*openf),
          ctx,
          uri,
          parts,
          length,
          uh),
       XML_ACCESS_READ_F(
          (*readf),
          ctx,
          uh,
          data,
          nraw,
          eoi),
       XML_ACCESS_CLOSE_F(
          (*closef),
          ctx,
          uh));

| Parameter | In/Out | Description                              |
|:----------|:-------|:-----------------------------------------|
| `xctx`    | `IN`   | XML context                              |
| `access`  | `IN`   | URL access method                        |
| `userctx` | `IN`   | user-defined context passed to callbacks |
| `openf`   | `IN`   | open-access callback function            |
| `readf`   | `IN`   | read-access callback function            |
| `closef`  | `IN`   | close-access callback function           |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlLoadDom(), XmlLoadSax()

### XmlCreate()

Create an XML Developer's Toolkit `xmlctx`.

#### Syntax

    xmlctx *XmlCreate(
       xmlerr *err,
       oratext *name,
       list);

| Parameter | In/Out | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `err`     | `OUT`  | returned error code                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `access`  | `IN`   | name of context, for debugging                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments. Properties common to all `xmlctx`'s, both XDK and XMLType, are:<br>• `data_encoding` is the data encoding in which XML data will be presented through DOM and SAX. Default is UTF-8 and UTF-E on EBCDIC platforms. Single-byte encodings are substantially faster than multibyte encodings; Unicode (UTF-16) uses more memory but has better performance than multibyte. If the `data_encoding` parameter is set to UTF-16, the APIs process wide-`CHAR` arrays, not `oratext` byte arrays.<br>• `default_input_encoding` is the default input encoding). If the encoding of an input document cannot be automatically determined through other methods, this encoding will be the default.<br>• `error_language` is the language (and optional encoding) in which error messages are created. Default is American with UTF-8 encoding. To specify only the language, give the name of the language ("American"). To also specify the encoding, add the period and the Oracle name of the encoding ("American.WE8ISO8859P1").<br>• `error_handler` is the function pointer; see `XML_ERRMSG_F`. By default, errors output the formatted message to `stderr`. If an error handler is provided, message will be passed to it, and not printed.<br>• `error_context` is user-defined context for error handler, a context pointer to be passed to the error handler function. It is user-defined; it is just specified here and passed along when an error occurs.<br>• `input_encoding` is the name of a forced input encoding for input documents. Use it to override a document's `XMLDecl`, and always interpret it in the given encoding. It should be not necessary in normal use, as existing BOMs and `XMLDecl`s should be correct.<br>• `memory_allo`c is a low-level memory allocation function, if not using `malloc`. If used, the matching free function must also be given. See `XML_ALLOC_F`.<br>• `memory_free` is a low-level memory freeing function, if not using `free`. Matches the `memory_alloc` function.<br>• `memory_context` is a user-defined memory context passed to the alloc and free functions. Its definition and use is entirely up to the user; it is just set here and passed to the callbacks.<br>The XDK has additional properties:<br>• `input_buffer_size` is the basic I/O buffer size. Default is 256K; the range is 4K to 4MB. Depending on the encoding, 1, 2 or 3 of these buffers may be needed. Note that size is in characters, not bytes. If the buffer holds Unicode data, it will be twice as large.<br>• `memory_block_size` is the size of chunk the high-level memory package will request from the low-level allocator; it is the basic unit of memory allocation. Default is 64K; the range is 16K to 256K.<br>These optional parameters should be used in the following manner:<br>`xmlctx *XmlCreate(`<br>`   xmlerr *err, `<br>`   oratext *name,`<br>`   ("data_encoding", dataEncoding),`<br>`   ("default_data_encoding", defaultDataEncoding),`<br>`   ("error_language", errorLanguage),`<br>`   ("error_handler", errorHandler),`<br>`   ("error_context", errorContext)`<br>`   ("input_encoding", inputEncoding),`<br>`   ("memory_alloc", memAlloc),`<br>`   ("memory_free", memFree),`<br>`   ("memory_context", memContext),`<br>`   ("input_buffer_seize", inputBufSize),`<br>`   ("memory_block_size", memBlockSize) );` |

#### Returns

`(xmlctx *)` created xmlctx \[or `NULL` on error with err set\]

**See Also:**

XmlDestroy(), [XML_ERRMSG_F()](package-callback-API.md) in [Package Callback APIs for C](package-callback-API.md)

### XmlCreateDTD()

Create DTD.

#### Syntax

    xmldocnode* XmlCreateDTD(
       xmlctx *xctx
       oratext *qname,
       oratext *pubid,
       oratext *sysid,
       xmlerr *err);

| Parameter | In/Out | Description                       |
|:----------|:-------|:----------------------------------|
| `xctx`    | `IN`   | XML context                       |
| `qname`   | `IN`   | qualified name                    |
| `pubid`   | `IN`   | external subset public identifier |
| `sysid`   | `IN`   | external subset system identifier |
| `err`     | `OUT`  | returned error code               |

#### Returns

`(xmldtdnode *)` new DTD node

### XmlCreateDocument()

Creates the initial top-level `DOCUMENT` node and its supporting infrastructure. If a qualified name is provided, a an element with that name is created and set as the document's root element.

#### Syntax

    xmldocnode* XmlCreateDocument(
       xmlctx *xctx,
       oratext *uri,
       oratext *qname,
       xmldtdnode *dtd,
       xmlerr *err);

| Parameter | In/Out | Description                                        |
|:----------|:-------|:---------------------------------------------------|
| `xctx`    | `IN`   | XML context                                        |
| `uri`     | `IN`   | namespace URI of root element to create, or `NULL` |
| `qname`   | `IN`   | qualified name of root element, or `NULL` if none  |
| `dtd`     | `IN`   | associated DTD node                                |
| `err`     | `OUT`  | returned error code                                |

#### Returns

`(xmldocnode *)` new `Document` object.

### XmlDestroy()

Destroys an XML context.

#### Syntax

    void XmlDestroy(
       xmlctx *xctx);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |

**See Also:**

XmlCreate()

### XmlDiff()

Compares two XML documents, specified either as DOM Trees, files, URIs, `orastream`s, and so on, and returns its document node. If input documents are not supplied as DOM trees, DOM trees will be created for them.

If the inputs are DOMs, that memory will not be freed when the call completes.

Data(DOM) encoding of both the documents must be the same as the data encoding in the XML context. The DOM for the diff will be created in the data encoding specified by the XML context.

#### Syntax

    xmldocnode *XmlDiff(
       xmlctx *xctx,
       xmlerr *err,
       ub4  flags,
       xmldfsrct firstSourceType,
       void *firstSource,
       void *firstSourceExtra,
       xmldfsrct secondSourceType,
       void *secondSource,
       void *secondSourceExtra,
       uword hashLevel);

| Parameter           | In/Out | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------|:-------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `xctx`              | `IN`   | XML context                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `err`               | `OUT`  | numeric error code, `XMLERR_OK [0]` on success                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `flags`             | `IN`   | Comparison options. By default, global algorithm and snapshot model are used.<br>• `XMLDF_FL_DEFAULTS(=0)` chooses defaults<br>• `XMLDF_FL_ALGORITHM_GLOBAL` is the global algorithm; it will generate the minimal diff using `INSERT`, `APPEND`, `DELETE` and `UPDATE`, and needs more memory and time than XMLDF_FL_ALGORITHM_LOCAL<br>• `XMLDF_FL_ALGORITHM_LOCAL` is the local algorithm; it may not generate the minimal diff, but it is faster and uses less space than `XMLDF_FL_ALGORITHM_GLOBAL`<br>• `XMLDF_FL_DISABLE_UPDATE` disables update operations with global algorithms<br>• `XMLDF_FL_OUTPUT_SNAPSHOT` uses the snapshot model |
| `firstSourceType`   | `IN`   | Source type for the first document. If `0`, assumed to be a DOM document node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `firstSource`       | `IN`   | Pointer to the first document source                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `firstSourceExtra`  | `IN`   | An additional pointer to the first document source; used for the buffer length pointer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `secondSourceType`  | `IN`   | Source type for the second document. If `0`, assumed to be a DOM document node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `secondSource`      | `IN`   | Pointer to the second document source                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `secondSourceExtra` | `IN`   | An additional pointer to the second document source; used for the buffer length pointer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `hashLevel`         | `IN`   | `1`-based depth (counting from the root), where hashing should be used for subtrees. Values less than or equal to 1 indicate no hashing. This value must be specified programmatically.<br>The hash value for every element node is associated with the entire subtree rooted at that node. During the computation of the diff, there is no further drilling down into the tree beyond hash level depth.<br>• If hashing is used with `XMLDF_FL_ALGORITHM_GLOBAL`, it will speed up diff computation significantly, but may reduce the quality of the diff.<br>• With `XMLDF_FL_ALGORITHM_LOCAL`, it improves the quality of the diff              |

### XmlFreeDocument()

Destroys a document created by `XmlCreateDocument` or through one of the Load functions. Releases all resources associated with the document, which is then invalid.

#### Syntax

    void XmlFreeDocument(
       xmlctx *xctx,
       xmldocnode *doc);

| Parameter | In/Out | Description      |
|:----------|:-------|:-----------------|
| `xctx`    | `IN`   | XML context      |
| `doc`     | `IN`   | document to free |

**See Also:**

XmlCreateDocument(), XmlLoadDom()

### XmlGetEncoding()

Returns data encoding in use by XML context. Ordinarily, the data encoding is chosen by the user, so this function is not needed. However, if the data encoding is not specified, and allowed to default, this function can be used to return the name of that default encoding.

#### Syntax

    oratext *XmlGetEncoding(
       xmlctx *xctx);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |

#### Returns

`(oratext *)` name of data encoding

**See Also:**

XmlIsSimple(), XmlIsUnicode()

### XmlHasFeature()

Determine if a DOM feature is implemented. Returns `TRUE` if the feature is implemented in the specified version, `FALSE` otherwise.

In level 1, the legal values for package are 'HTML' and 'XML' (case-insensitive), and the version is the string "1.0". If the version is not specified, supporting any version of the feature will cause the method to return `TRUE`.

- DOM 1.0 features are "XML" and "HTML".

- DOM 2.0 features are "Core", "XML", "HTML", "Views", "StyleSheets", "CSS", "CSS2", "Events", "UIEvents", "MouseEvents", "MutationEvents", "HTMLEvents", "Range", "Traversal"

#### Syntax

    boolean XmlHasFeature(
       xmlctx *xctx,
       oratext *feature,
       oratext *version);

| Parameter | In/Out | Description                                |
|:----------|:-------|:-------------------------------------------|
| `xctx`    | `IN`   | XML context                                |
| `feature` | `IN`   | package name of the feature to test        |
| `version` | `IN`   | version number of the package name to test |

#### Returns

`(boolean)` feature is implemented?

### XmlIsSimple()

Returns a flag saying whether the context's data encoding is "simple", single-byte for each character, like ASCII or EBCDIC.

#### Syntax

    boolean XmlIsSimple(
       xmlctx *xctx);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |

#### Returns

`(boolean)` `TRUE` of data encoding is "simple", `FALSE` otherwise

**See Also:**

XmlGetEncoding(), XmlIsUnicode()

### XmlIsUnicode()

Returns a flag saying whether the context's data encoding is Unicode, UTF-16, with two-byte for each character.

#### Syntax

    boolean XmlIsUnicode(
       xmlctx *xctx);

| Parameter | In/Out | Description |
|:----------|:-------|:------------|
| `xctx`    | `IN`   | XML context |

#### Returns

`(boolean)` `TRUE` of data encoding is Unicode, `FALSE` otherwise

**See Also:**

XmlGetEncoding(), XmlIsSimple()

### XmlLoadDom()

Loads (parses) an XML document from an input source and creates a DOM. The root document node is returned on success, or `NULL` on failure (with err set).

The function takes two fixed arguments, the xmlctx and an error return code, then zero or more (property, value) pairs, then `NULL`.

`SOURCE` Input source is set by one of the following mutually exclusive properties (choose one):

- ("`uri`", document URI) \[compiler encoding\]

- ("`file`", document filesystem path) \[compiler encoding\]

- ("`buffer`", address of buffer, "`buffer_length`", \# bytes in buffer)

- ("`stream`", address of stream object, "`stream_context"`, pointer to stream object's context)

- ("`stdio`", `FILE*` stream)

`PROPERTIES` Additional properties:

- ("`dtd`", DTD node) DTD for document

- ("`base_uri`", document base URI) for documents loaded from other sources than a URI, sets the effective base URI. the document's base URI is needed in order to resolve relative URI include, import, and so on.

- ("`input_encoding`", encoding name) forced input encoding \[name\]

- ("`default_input_encoding`", `encoding_name`) default input encoding to assume if document is not self-describing (no BOM, protocol header, `XMLDecl`, and so on)

- ("`schema_location`", `string`) `schemaLocation` of schema for this document. used to figure optimal layout when loading documents into a database

- ("`validate`", boolean) when `TRUE`, turns on DTD validation; by default, only well-formedness is checked. note that schema validation is a separate beast.

- ("`discard_whitespace`", boolean) when `TRUE`, formatting whitespace between elements (newlines and indentation) in input documents is discarded. by default, ALL input characters are preserved.

- ("`dtd_only`", boolean) when `TRUE`, parses an external DTD, not a complete XML document.

- ("`stop_on_warning`", boolean) when `TRUE`, warnings are treated the same as errors and cause parsing, validation, and so on, to stop immediately. by default, warnings are issued but the game continues.

- ("`warn_duplicate_entity`", boolean) when `TRUE`, entities which are declared more than once will cause warnings to be issued. the default is to accept the first declaration and silently ignore the rest.

- ("`no_expand_char_ref`", boolean) when `TRUE`, causes character references to be left unexpanded in the DOM data. ordinarily, character references are replaced by the character they represent. however, when a document is saved those characters entities do not reappear. to way to ensure they remain through load and save is to not expand them.

- ("`no_check_chars`", boolean) when `TRUE`, omits the test of XML \[2\] Char production: all input characters will be accepted as valid

#### Syntax

    xmldocnode *XmlLoadDom(
       xmlctx *xctx,
       xmlerr *err,
       list);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `err`     | `OUT`  | returned error code                          |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(xmldocnode *)` document node on success \[`NULL` on failure with err set\]

**See Also:**

XmlSaveDom()

### XmlLoadSax()

Loads (parses) an XML document from an input source and generates a set of SAX events (as user callbacks). Input sources and basic set of properties is the same as for `XmlLoadDom`.

#### Syntax

    xmlerr XmlLoadSax(
       xmlctx *xctx,
       xmlsaxcb *saxcb,
       void *saxctx,
       list);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `saxcb`   | `IN`   | SAX callback structure                       |
| `saxctx`  | `IN`   | context passed to SAX callbacks              |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

### XmlLoadSaxVA()

Loads (parses) an XML document from an input source and generates a set of SAX events (as user callbacks). Input sources and basic set of properties is the same as for `XmlLoadDom`.

#### Syntax

    xmlerr XmlLoadSaxVA(
       xmlctx *xctx,
       xmlsaxcb *saxcb,
       void *saxctx,
       va_list va);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `saxcb`   | `IN`   | SAX callback structure                       |
| `saxctx`  | `IN`   | context passed to SAX callbacks              |
| `va`      | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

### XmlSaveDom()

Serializes document or subtree to the given destination and returns the number of bytes written; if no destination is provided, just returns formatted size but does not output.

If an output encoding is specified, the document will be re-encoded on output; otherwise, it will be in its existing encoding.

The top level is indented step\*level spaces, the next level step\*(level+1) spaces, and so on.

When saving to a buffer, if the buffer overflows, `0` is returned and err is set to `XMLERR_SAVE_OVERFLOW`.

`DESTINATION` Output destination is set by one of the following mutually exclusive properties (choose one):

- ("`ur`i", document URI) `POST`, `PUT`? \[compiler encoding\]

- ("file", document filesystem path) \[compiler encoding\]

- ("`buffer`", address of buffer, "b`uffer_length`", \# bytes in buffer)

- ("`stream`", address of stream object, "`stream_context`", pointer to stream object's context)

PROPERTIES Additional properties:

- ("`output_encoding`", encoding name) name of final encoding for document. unless specified, saved document will be in same encoding as xmlctx.

- ("`indent_step`", unsigned) spaces to indent each level of output. default is `4`, `0` means no indentation.

- ("`indent_level`", unsigned) initial indentation level. default is `0`, which means no indentation, flush left.

- ("`xmldecl"`, boolean) include an `XMLDecl` in the output document. ordinarily an X`MLDecl` is output for a compete document (root node is DOC).

- ("`bom`", boolean) input a BOM in the output document. usually the BOM is only needed for certain encodings (UTF-16), and optional for others (UTF-8). causes optional BOMs to be output.

- ("`prune`", boolean) prunes the output like the unix 'find' command; does not not descend to children, just prints the one node given.

#### Syntax

    ubig_ora XmlSaveDom(
       xmlctx *xctx,
       xmlerr *err,
       xmlnode *root,
       list);

| Parameter | In/Out | Description                                  |
|:----------|:-------|:---------------------------------------------|
| `xctx`    | `IN`   | XML context                                  |
| `err`     | `OUT`  | error code on failure                        |
| `root`    | `IN`   | root node or subtree to save                 |
| `list`    | `IN`   | `NULL`-terminated list of variable arguments |

#### Returns

`(ubig_ora)` number of bytes written to destination

**See Also:**

XmlLoadDom()

### XmlVersion()

Returns the version string for the XDK

#### Syntax

    oratext *XmlVersion();

#### Returns

`(oratext *)` version string
