The following table lists the OCI SODA functions that are described in this chapter.

Table 36-1 OCI SODA Functions

| Function                             | Purpose                                                                                                                                                                      |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OCISodaBulkInsert()`                | Inserts a document array into a collection.                                                                                                                                  |
| `OCISodaBulkInsertAndGet()`          | Inserts a document array into a collection and gets the result document array back.                                                                                          |
| `OCISodaBulkInsertAndGetWithOpts ()` | Inserts several SODA documents with options.                                                                                                                                 |
| `OCISodaBulkInsertAndGetWithCtnt()`  | Inserts a document array into a collection and gets the result document array back. The input documents are represented as an array of content strings and an array of keys. |
| `OCISodaBulkInsertWithCtnt()`        | Inserts an array of documents into a collection. The documents are represented as an array of content strings and an array of keys.                                          |
| `OCISodaCollCreate()`                | Creates a new document collection with default metadata settings.                                                                                                            |
| `OCISodaCollCreateWithMetadata()`    | Creates a new document collection with metadata.                                                                                                                             |
| ` OCISodaCollDrop()`                 | Drops a collection from the database.                                                                                                                                        |
| ` OCISodaCollGetNext()`              | Gets the next collection from the collection cursor.                                                                                                                         |
| `OCISodaCollList()`                  | Lists the collections in the schema associated with the supplied service context handle parameter.                                                                           |
| `OCISodaCollOpen()`                  | Opens the collection.                                                                                                                                                        |
| `OCISodaDataGuideGet()`              | Gets JSON data guide information.                                                                                                                                            |
| `OCISodaDataGuideGetWithOpts () `    | Get data guide with options.                                                                                                                                                 |
| `OCISodaDocCount()`                  | Counts the number of documents from a collection.                                                                                                                            |
| `OCISodaDocCountWithFilter()`        | Counts the number of documents in a collection based on the query-by-example filter document.                                                                                |
| `OCISodaDocCreate()`                 | Creates a document.                                                                                                                                                          |
| `OCISodaDocCreateWithKey()`          | Creates a document with document key and content.                                                                                                                            |
| `OCISodaDocCreateWithKeyAndMType()`  | Creates a document with document key, content, and media type.                                                                                                               |
| `OCISodaDocGetNext()`                | Gets the next document in the collection.                                                                                                                                    |
| `OCISodaFind()`                      | Find documents in a collection.                                                                                                                                              |
| `OCISodaFindOne()`                   | Finds a single document in a collection.                                                                                                                                     |
| `OCISodaFindOneWithKey()`            | Finds a single document in a collection given a key.                                                                                                                         |
| `OCISodaIndexCreate()`               | Creates an index with an index specification.                                                                                                                                |
| `OCISodaIndexDrop()`                 | Drops an index.                                                                                                                                                              |
| `OCISodaInsert()`                    | Inserts a document into a collection.                                                                                                                                        |
| `OCISodaInsertAndGet()`              | Inserts a document into a collection and returns a result document.                                                                                                          |
| `OCISodaInsertAndGetWithOpts ()`     | Inserts a SODA document with options.                                                                                                                                        |
| `OCISodaInsertAndGetWithCtnt()`      | Inserts a document into a collection and returns a result document. The input document is represented as a content string and a key                                          |
| `OCISodaInsertWithCtnt()`            | Inserts a document into a collection. The document is represented as a content string and a key                                                                              |
| `OCISodaRemove()`                    | Removes matching documents from a collection.                                                                                                                                |
| `OCISodaRemoveOneWithKey()`          | Removes a document from a collection given a key.                                                                                                                            |
| `OCISodaReplOne()`                   | Replaces a document in a collection.                                                                                                                                         |
| `OCISodaReplOneAndGet()`             | Replaces a document in a collection. The input document is represented only by the content string.                                                                           |
| `OCISodaReplOneAndGetWithCtnt()`     | Replaces a document in a collection and returns the result document. The input document is represented only by the content string.                                           |
| `OCISodaReplOneAndGetWithKey()`      | Replace a document in a collection given a key and returns the result document.                                                                                              |
| `OCISodaReplOneWithCtnt()`           | Replaces a document in a collection. The document is represented only by the content string                                                                                  |
| `OCISodaReplOneWithKey()`            | Replaces a document in a collection given a key.                                                                                                                             |
| `OCISodaSave()`                      | Saves a document into a collection.                                                                                                                                          |
| `OCISodaSaveAndGet()`                | Saves a document into a collection, returning a document containing metadata information.                                                                                    |
| `OCISodaSaveAndGetWithOpts ()`       | Saves a SODA document with options.                                                                                                                                          |
| `OCISodaOperKeysSet()`               | Sets the array of keys on Operation Options Handle.                                                                                                                          |

### 36.2.1 OCISodaBulkInsert()

Inserts an array of documents into a collection.

#### Purpose

To insert an array of documents into a collection.

#### Syntax

    sword OCISodaBulkInsert(OCISvcCtx            *svchp,
                            OCISodaColl          *collection,
                            OCISodaDoc          **documentarray,
                            ub4                   arraylen,
                            OCISodaOutputOptions *opoptns,
                            OCIError             *errhp,
                            ub4                   mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)         | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection (IN)    | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| documentarray (IN) | Array of handles of documents to be inserted into the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| arrarylen (IN)     | The length of the document handle array supplied in the `documentarray` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| opoptns (OUT)      | Output options handle. Valid attributes are:<br>• `OCI_ATTR_SODA_DOC_COUNT.` — The number of documents inserted.<br>Note: If an error occurs,` OCI_ATTR_SODA_DOC_COUNT` contains the number of documents inserted before the error occurred.                                                                                                                                                                                                                                                                                                                                                     |
| errhp (OUT)        | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document array insertion into the specified collection is successful.

`OCI_ERROR`, if the document array insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6)

### 36.2.2 OCISodaBulkInsertAndGet()

Inserts an array of documents into a collection, and returns an array of result documents each containing all document components except for the content.

#### Purpose

To insert an array of documents into a collection, and return an array of result documents, each containing all document components except for the content. The components generated by SODA during the insert, such as key (if the collection has auto-assigned keys), last-modified timestamp, created-on timestamp, and version, are returned with each result document.

#### Syntax

    sword OCISodaBulkInsertAndGet(OCISvcCtx            *svchp,
                                  OCISodaColl          *collection,
                                  OCISodaDoc          **documentarray,
                                  ub4                   arraylen,
                                  OCISodaOutputOptions *opoptns,
                                  OCIError             *errhp,
                                  ub4                   mode);

#### Parameters

| Parameter              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)             | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection (IN)        | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| documentarray (IN/OUT) | Array of handles of documents to be inserted into the collection.<br>Note: Since the result documents are returned using the same parameter, you need to save a reference to each input document handle so that you can free it later along with each result document handle, using `OCIHandleFree()` method. If you do not save a reference to each input document handle, it is overwritten with a reference to the result document, and the input document handle will never be properly freed (leads to memory leak).                                                                        |
| arrarylen (IN)         | The length of the document handle array supplied in `documentarray` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| opoptns (OUT)          | Output options handle. Valid attributes are:<br>• `OCI_ATTR_SODA_DOC_COUNT`:<br>• The number of documents inserted. If an error occurs, `OCI_ATTR_SODA_DOC_COUNT` contains the number of documents inserted before the occurrence of the error.                                                                                                                                                                                                                                                                                                                                                  |
| errhp (OUT)            | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)              | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document array insertion into the specified collection is successful.

`OCI_ERROR`, if the document array insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6).

### 36.2.3 OCISodaBulkInsertAndGetWithOpts()

Inserts several SODA documents with options.

#### Purpose

To insert several SODA documents with options.

#### Syntax

    sword OCISodaBulkInsertAndGetWithOpts(OCISvcCtx                 *svchp,
                                          OCISodaColl               *collection,
                                          OCISodaDoc               **documentarray,
                                          ub4                        arraylen,
                                          OCISodaOperationOptions   *oproptns,
                                          OCISodaOutputOptions      *opoptns,
                                          OCIError                  *errhp,
                                          ub4                        mode);

#### Parameters

| Parameter              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)             | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection (IN)        | The collection handle in which you want to insert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| documentarray (IN/OUT) | The document array to be inserted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| arrarylen (IN)         | The length of the document array to be inserted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| oproptns (IN)          | Operation options handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| opoptns (OUT)          | Output options handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| errhp (IN)             | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)              | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the documents were inserted.

### 36.2.4 OCISodaBulkInsertAndGetWithCtnt()

Inserts an array of documents into a collection using only their contents, and returns an array of result documents containing all the document components except for the content.

#### Purpose

To insert an array of documents into a collection using only their contents and returns an array of result documents, each document containing all document components except for the content.

**Note:**

This is a convenience method for inserting JSON documents only without constructing document handles for them. The more general method is `OCISodaBulkInsertAndGet`.

#### Syntax

    sword OCISodaBulkInsertAndGetWithCont(OCISvcCtx             *svchp,
                                          OCISodaColl           *collection,
                                          void                 **contentStrings,
                                          ub4                   *contentStringLengths,
                                          OraText              **keys,
                                          ub4                   *keyLengths,
                                          ub4                    arrayLength,
                                          ub4                    docFlags,
                                          OCISodaDoc           **documents,
                                          OCISodaOutputOptions  *opoptns,
                                          OCIError              *errhp
                                          ub4                    mode);

#### Parameters

| Parameter                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)                 | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| collection (IN)            | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| contentStrings (IN)        | An array of strings that contains the JSON content for the documents.<br>Note: This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| contentStringLengths (IN)  | An array of content string lengths.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| keys (IN)                  | An array of keys for the inserted documents. Provide the keys, if the collection has client-assigned keys. Otherwise, set to null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| keyLengths (IN)            | An array of key lengths. Needs to be set only if the collection has client-assigned keys. Otherwise, must be set to null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| arrayLength (IN)           | The length of the `contentStrings` and `keys` arrays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| docFlags (IN)              | The encoding flags used to indicate the encoding of the supplied document's content. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| documents (OUT)            | Returns an array of result documents containing all document components except for the content. Each result document contains the components such as key (if the collection has auto-assigned keys), last-modified timestamp, created-on timestamp, and version generated by SODA insert command.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| opoptns (OUT)              | Specifies the output options handle. Valid attributes are:<br>• `OCI_ATTR_SODA_DOC_COUNT.` — The number of documents inserted.<br>Note: If an error occurs,` OCI_ATTR_SODA_DOC_COUNT` contains the number of documents inserted before the error occurred.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| errhp (OUT)                | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)                  | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                        |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6).

### 36.2.5 OCISodaBulkInsertWithCtnt()

Inserts an array of documents into a collection using only their contents.

#### Purpose

To insert an array of documents into a collection using only their contents.

**Note:**

This is a convenience method for inserting JSON documents only without constructing document handles for them. The more general method is `OCISodaBulkInsert`.

#### Syntax

    sword OCISodaBulkInsertWithCtnt(OCISvcCtx            *svchp,
                                    OCISodaColl          *collection,
                                    void                **contentStrings,
                                    ub4                  *contentStringLengths,
                                    OraText             **keys,
                                    ub4                  *keyLengths,
                                    ub4                   arrayLength,
                                    ub4                   docFlags,
                                    OCISodaOutputOptions *opoptns,
                                    OCIError             *errhp,
                                    ub4                   mode);

#### Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)                | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| collection (IN)           | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| contentStrings (IN)       | An array of strings that contain the JSON content for the documents. This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| contentStringLengths (IN) | An array of content string lengths.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| keys (IN)                 | An array of keys for the inserted documents. Provide the keys, if the collection has client-assigned keys. Otherwise, set to null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| keyLengths (IN)           | An array of key lengths. Needs to be set only if the collection has client-assigned keys. Otherwise, must be set to null.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| arrayLength (IN)          | The length of the `contentStrings` and `keys` arrays.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| docFlags (IN)             | The encoding flags used to create the documents. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| opoptns (OUT)             | Specifies the output options handle. Valid attributes are:<br>• `OCI_ATTR_SODA_DOC_COUNT.` — The number of documents inserted.<br>Note: If an error occurs,` OCI_ATTR_SODA_DOC_COUNT` contains the number of documents inserted before the error occurred.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| errhp (OUT)               | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| mode (IN)                 | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                    |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For example, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6)

### 36.2.6 OCISodaCollCreate()

Creates a new document collection with default metadata settings.

#### Purpose

Create a new document collection with default metadata settings.

#### Syntax

    sword OCISodaCollCreate(OCISvcCtx       *svchp,
                            const OraText   *collname,
                            ub4              collnamelen,
                            OCISodaColl    **collection,
                            OCIError        *errhp,
                            ub4              mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| collname (IN)    | The name of the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| collnamelen (IN) | The length of the collection name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| collection (OUT) | Allocates the collection handle representing the document collection that was created. Call `OCIHandleFree()` to free the collection handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| errhp (IN/OUT)   | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• `OCI_SODA_COLL_CREATE_MAP` - Creates a new collection mapping to an existing table. Minimal checking is performed to ensure that the table has correct shape matching the default collection metadata. This function returns an error, if this check fails. |

#### Returns

`OCI_SUCCESS`, if the collection is successfully created.

`OCI_ERROR`, if the collection is not created. The `OCIError` parameter has the necessary error information.

#### Usage Notes

- If the collection with the specified name already exists, then this function acts as `OCISodaCollOpen()` and opens the existing collection.

- This function, unlike a SQL DDL operation, does not perform a commit operation before or after it runs. (Unless you specify `OCI_SODA_ATOMIC_COMMIT` mode, only then is the current transaction committed after the operation runs).

#### Examples

Example 36-1 Creating a Collection

for examples, see [Creating a Document Collection for SODA with C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-8B40F7AB-1397-4520-9854-B68B6B6D2D5D).

### 36.2.7 OCISodaCollCreateWithMetadata()

Creates a new document collection with metadata.

#### Purpose

Create a new document collection with metadata.

#### Syntax

    sword OCISodaCollCreateWithMetadata(OCISvcCtx      *svchp,
                                        const OraText  *collname,
                                        ub4             collnamelen,
                                        OraText        *metadata,
                                        ub4             metadatalen,
                                        OCISodaColl   **collection,
                                        OCIError       *errhp,
                                        ub4             mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| collname (IN)    | The name of the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| collnamelen (IN) | The length of the collection name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| metadata (IN)    | The JSON string that contains the collection metadata information. If `metadata` is `NULL`, it uses the default metadata settings to create the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| metadatalen (IN) | The length of the metadata JSON string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| collection (OUT) | Allocates the collection handle representing the document collection that was created. Call `OCIHandleFree()` to free the collection handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| errhp (IN/OUT)   | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` - Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• `OCI_SODA_COLL_CREATE_MAP` - Creates a new collection mapping to an existing table. Minimal checking is performed to ensure that the table has correct shape, matching the specified collection metadata or default metadata, if metadata parameter is `NULL`. This function returns an error, if this check fails. |

#### Returns

`OCI_SUCCESS`, if the collection is successfully created.

`OCI_ERROR`, if the collection is not created. The `OCIError` parameter has the necessary error information.

#### Usage Notes

- If the collection with the specified name already exists and that collection has metadata equivalent to the supplied metadata, then this function acts as `OCISodaCollOpen()` and opens the existing collection. If the collection contains metadata that does not match with the specified collection name, then an error is returned.

- This function, unlike a SQL DDL operation, does not perform a commit operation before or after it runs. (Unless you specify `OCI_SODA_ATOMIC_COMMIT` mode, only then is the current transaction committed after the operation runs).

#### Examples

For example, see [Creating a Document Collection for SODA with C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-8B40F7AB-1397-4520-9854-B68B6B6D2D5D).

### 36.2.8 OCISodaCollDrop()

Drops a collection from the database.

#### Purpose

Drop a collection from the database.

#### Syntax

    sword OCISodaCollDrop(OCISvcCtx   *svchp,
                          OCISodaColl *coll,
                          boolean     *isDropped,
                          OCIError    *errhp,
                          ub4          mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| coll (IN)       | The collection to be dropped. If `coll` no longer references an existing collection, then no error is returned, but `isDropped` is `FALSE` indicating the drop operation was not successful after the invocation of `OCISodaCollDrop()`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| isDropped (OUT) | Returns the status of the drop operation: `TRUE` if the drop operation is successful, `FALSE` if the drop operation is not successful.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| errhp (IN/OUT)  | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• `OCI_SODA_COLL_DROP_PURGE `— When this mode is set, the data table is purged.<br>• `OCI_SODA_COLL_DROP_MAPPED_TABLE`— When this mode is set, the data table is dropped while dropping a mapped collection. |

#### Returns

`OCI_SUCCESS`, if dropping the collection is successful.

`OCI_ERROR`, if dropping the collection failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

- This function only drops the collection; it does not free the collection handle. Call `OCIHandleFree()` to free the collection handle to avoid memory leaks.

- This function, unlike a SQL DDL operation, does not perform a commit operation before or after it runs. (Unless you specify `OCI_SODA_ATOMIC_COMMIT` mode, only then is the current transaction committed after the operation runs).

#### Examples

For examples, see [Dropping a Document Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-F92DF544-ED19-466F-BC05-192246ECEE3E).

### 36.2.9 OCISodaCollGetNext()

Gets the next collection from the collection cursor.

#### Purpose

Get the next collection from the collection cursor.

#### Syntax

    sword OCISodaCollGetNext(OCISvcCtx                *svchp,
                             const OCISodaCollCursor  *cur,
                             OCISodaColl             **coll,
                             OCIError                 *errhp,
                             ub4                       mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                  |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context handle.                                                                                                                                                  |
| cur (IN)       | The collection cursor handle remains valid when allocated by `OCISodaCollList()`. Call `OCIHandleFree()` to free the collection cursor handle when it is no longer required. |
| coll (OUT)     | Allocates the collection handle and returns it to the next collection to be found. Call `OCIHandleFree()` to free the collection handle when it is no longer required.       |
| errhp (IN/OUT) | The error handle.                                                                                                                                                            |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.                      |

#### Returns

`OCI_SUCCESS`, if the next collection is returned from the specified cursor.

`OCI_ERROR`, if there was an error fetching the next collection. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Discovering Existing Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-7F1DFCEF-3A2C-41A3-810B-420299A4E66B)

### 36.2.10 OCISodaCollList()

Lists the collections in the schema associated with the supplied service context handle parameter.

#### Purpose

List the collections in the schema.

#### Syntax

    sword OCISodaCollList(OCISvcCtx          *svchp,
                          const OraText      *startname,
                          ub4                 stnamelen,
                          OCISodaCollCursor **cur,
                          OCIError           *errhp,
                          ub4                 mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| startname (IN) | The collection start name. Can be set to `NULL` and `stnamelen` set to the value 0 to return all existing collections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| stnamelen (IN) | The length of the collection start name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| cur (OUT)      | Allocates the collection cursor handle and returns it. The collection cursor represents the collection list. Call `OCIHandleFree()` to free the collection cursor handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| errhp (IN/OUT) | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaCollList()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if getting a cursor over all collections in the schema is successful.

`OCI_ERROR`, if getting a cursor over all collections in the schema is not successful. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Discovering Existing Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-7F1DFCEF-3A2C-41A3-810B-420299A4E66B).

### 36.2.11 OCISodaCollOpen()

Opens the collection.

#### Purpose

Open the collection.

#### Syntax

    sword OCISodaCollOpen(OCISvcCtx      *svchp,
                          const OraText  *collname,
                          ub4             collnamelen,
                          OCISodaColl   **coll,
                          OCIError       *errhp,
                          ub4             mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| collname (IN)    | The name assigned to the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| collnamelen (IN) | The length of the collection name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| coll (OUT)       | Allocates the collection handle and returns it with the specified collection name. The function returns `OCI_SUCCESS` if there are no errors while trying to open the collection. If the collection with the supplied name is not present, that is not considered an error and returns `OCI_SUCCESS`, but the collection-handle pointer returns as `NULL`. So a way to check if the collection exists and was successfully opened, is to check that the `coll (OUT)` pointer is not `NULL` after this function returns with `OCI_SUCCESS`. Call `OCIHandleFree()` to free the collection handle when it is no longer required.                                                                                                                                                              |
| errhp (IN/OUT)   | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaCollOpen()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if there were no errors while trying to open the collection.

`OCI_ERROR`, if errors were encountered while trying to open the collection. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Opening an Existing Document Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-BEE217C1-8B25-4697-8216-F8B86F425386).

### 36.2.12 OCISodaDataGuideGet()

Gets JSON data guide information.

#### Purpose

To get the JSON data guide information.

#### Syntax

    sword OCISodaDataGuideGet(OCISvcCtx           *svchp,
                               const OCISodaColl  *collection,
                               ub4                 docFlags,
                               OCISodaDoc        **doc,
                               OCIError           *errhp,
                               ub4                 mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| collection(IN) | The collection handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| docFlags (IN)  | The following flags control the encoding of the returned document's content. Valid flag options are:<br>• `OCI_DEFAULT` — Document content is returned in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle).<br>• `OCI_SODA_AS_AL32UTF8` — Document content is returned in the character set AL32UTF8.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| doc (OUT)      | The document handle with content representing the JSON data guide.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| errhp (OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaDataGuideGet()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if getting the data guide information of a specified collection is successful.

`OCI_ERROR`, if getting data guide information results in an error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Getting a Data Guide for a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-80CC6F4E-FB19-4336-B407-1CF46B1CD3CD).

### 36.2.13 OCISodaDataGuideGetWithOpts ()

For only the documents selected from your query, a data guide is created guide dynamically from scratch. Dataguide enabled JSON search index is not required.

#### Purpose

To get data guide.

#### Syntax

    sword OCISodaDataGuideGetWithOpts(OCISvcCtx                *svchp,
                                      const OCISodaColl        *collection,
                                      OCISodaOperationOptions  *optns,
                                      ub4                       format,
                                      ub4                       flags,
                                      ub4                       docFlags,
                                      OCISodaDoc              **doc,
                                      OCIError                 *errhp,
                                      ub4                       mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection(IN) | The collection handle in which you want to intert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| optns (IN)     | Operation options handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| format (IN)    | OCI SODA DataGuide formats:<br>• `OCI_SODA_DG_FMT_HIERARCHICAL `: Hierarchical data guide is represented in JSON as an object with nested JSON data in the same format as defined by the JSON Schema (version 4, json-schema-core).<br>• `OCI_SODA_DG_FMT_FLAT`: A flat data guide is represented in JSON as an array of objects, each of which represents the JSON data of a specific path in the document set.                                                                                                                                                                                 |
| flags (IN)     | OCI SODA DataGuide flags:<br>• `OCI_SODA_DATAGUIDE_PRETTY `: Use this flag bit to improve readability of the returned data guide with appropriate indentation.<br>• `OCI_SODA_DATAGUIDE_GEOJSON `: Use this flag bit for the data guide to auto detect the GeoJSON type.<br>• `OCI_SODA_DATAGUIDE_GATHER_STATS`: Use this flag bit for the data guide to collect statistical information.                                                                                                                                                                                                        |
| docflags (IN)  | Document flags.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| doc (OUT)      | Document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| errhp (OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if data guide is retrieved.

### 36.2.14 OCISodaAsOfTimestampGet ()

Fetches the database timestamp value as a string.

#### Purpose

To fetch the database timestamp value as a string.

#### Syntax

    sword OCISodaAsOfTimestampGet(OCISvcCtx      *svchp,
                                  void           *tstamp,
                                  ub4            *tstampLen,
                                  OCIError       *errhp,
                                  ub4             mode);

#### Parameters

| Parameter       | Description                      |
|:----------------|:---------------------------------|
| svchp (IN)      | The service context.             |
| tstamp (IN/OUT) | The Database timestamp value.    |
| tstampLen (OUT) | Length of timestamp string.      |
| errhp (OUT)     | The error handle.                |
| mode (IN)       | Specifies the mode of execution. |

#### Returns

`OCI_SUCCESS`, if the operation is successful.

`OCI_ERROR`, if getting data guide information results in an error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

The input timestamp buffer (`tstamp`) is expected to be atleast `OCI_SODA_TIMESTAMP_MAXSIZE` in size. If `OCI_UTF16ID` is specified for SQL CHAR data in the `OCIEnvNlsCreate()` function, then `tstamp` is expected to be `utext` array of `OCI_SODA_TIMESTAMP_MAXSIZE` size, that is `Utext tstamp[OCI_SODA_TIMESTAMP_MAXSIZE]`.

### 36.2.15 OCISodaAsOfScnGet ()

Fetches the database SCN value.

#### Purpose

To fetch the database SCN value.

#### Syntax

    sword OCISodaAsOfScnGet(OCISvcCtx        *svchp,
                              ub8            *scn,
                              OCIError       *errhp,
                              ub4             mode);

#### Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN) | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| scn (OUT)  | Database SCN value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| errhp (IN) | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)  | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS` if the operation is successful.

### 36.2.16 OCISodaDocCount()

Counts the number of documents matching the attributes set in the operation options handle. If the operation options handle has no attributes set, then the function counts all the documents in the collection.

#### Purpose

To count the number of documents matching the attributes set in the operation options handle. If the operation options handle has no attributes set, then the function counts all the documents in the collection.

#### Syntax

    sword OCISodaDocCount(OCISvcCtx                     *svchp,
                          const OCISodaColl             *coll,
                          const OCISodaOperationOptions *optns,
                          ub8                           *numdocs,
                          OCIError                      *errhp,
                          ub4                            mode);

#### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)    | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| coll (IN)     | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| optns (IN)    | The operation options handle. If skip and limit attributes are set on the operation options handle, then an error is returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| numdocs (OUT) | The number of documents in the collection matching attributes (if any) set on the operation options handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| errhp (OUT)   | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| mode (IN)     | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaDocCount()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if the document count from the specified collection is successful.

`OCI_ERROR`, if the document count failed due to hard errors. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Counting the Number of Documents Found](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E__GUID-9ED8FED2-085C-4212-962D-26A33B91ECA7).

### 36.2.17 OCISodaDocCountWithFilter()

Counts the number of documents matching a filter specification.

#### Purpose

To count the number of documents matching a filter specification.

**Note:**

This is a convenience method for counting documents matching a filter specification. A more general method for counting documents is `OCISodaDocCount()` which can count documents matching a filter specification or other criteria.

#### Syntax

    sword OCISodaDocCountWithFilter(OCISvcCtx         *svchp,
                                    const OCISodaColl *coll,
                                    const OraText     *filterSpec,
                                    ub4                filterSpecLen,
                                    ub8               *numdocs,
                                    OCIError          *errhp,
                                    ub4                mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)         | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| coll (IN)          | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| filterSpec (IN)    | The JSON filter string used to search the documents in a collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| filterSpecLen (IN) | The length of the filter string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| numdocs (OUT)      | The number of documents in the collection matching the filter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| errhp (OUT)        | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaDocCountWithFilter()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if the document count from the specified collection is successful.

`OCI_ERROR`, if the document count failed due to hard errors. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

### 36.2.18 OCISodaDocCreate()

Creates a document.

#### Purpose

Create a document.

#### Syntax

    sword OCISodaDocCreate (OCIEnv            *envhp,
                            const void        *content,
                            ub4                contentLength,
                            ub4                docFlags,
                            OCISodaDoc       **document,
                            OCIError          *errhp,
                            ub4                mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| envhp (IN)         | The environment handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| content(IN)        | A string containing the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| contentLength (IN) | The string length of the content parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| docFlags (IN)      | Used to detect JSON encoding while creating a document. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| document (OUT)     | Allocates and returns the document handle. Call `OCIHandleFree()` to free the document handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| errhp (IN/OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

#### Returns

`OCI_SUCCESS`, if the document is successfully created.

`OCI_ERROR`, if the document creation failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

Example 36-2 Creating a Document

For examples, see [Creating Documents with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-793B416B-2E8C-4425-9B35-381855E673AA).

### 36.2.19 OCISodaDocCreateWithKey()

Creates a document with a document key and content.

#### Purpose

Create a document with a document key and content.

#### Syntax

    sword OCISodaDocCreateWithKey(OCIEnv        *envhp,
                                  const void    *content,
                                  ub4            contentLength,
                                  const OraText *key,
                                  ub4            keylen,
                                  ub4            docFlags,
                                  OCISodaDoc   **document,
                                  OCIError      *errhp,
                                  ub4            mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| envhp (IN)         | The environment handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| content (IN)       | A string containing the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| contentLength (IN) | The string length of the content parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| key (IN)           | A string that contains the document key. The key can be `NULL`.<br>For example, in the default case, collection has auto-generated keys, so you do not want to set the key on the document (if you do, you get an error when you pass such a doc to a write operation, such as insert). You only want to set a non-`NULL` key if your collection is configured with client-assigned keys, which is not the default.                                                                                                                                                                                                                                                                                                                                                                                                     |
| keylen (IN)        | The length of the key string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| docFlags (IN)      | The flags used to create a document. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| document (OUT)     | Allocates and returns the document handle. Call `OCIHandleFree()` to free the document handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| errhp (IN/OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

#### Returns

`OCI_SUCCESS`, if the document is successfully created.

`OCI_ERROR`, if the document creation failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Creating Documents with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-793B416B-2E8C-4425-9B35-381855E673AA).

### 36.2.20 OCISodaDocCreateWithKeyAndMType()

Creates a document with a document key, content, and media type.

#### Purpose

Create a document with a document key, content, and media type.

#### Syntax

    sword OCISodaDocCreateWithKeyAndMType(OCIEnv               *envhp,
                                          const void           *content,
                                          ub4                   contentLength,
                                          const OraText        *key,
                                          ub4                   keylen,
                                          const OraText        *mediaType,
                                          ub4                   mediaTypeLength,
                                          ub4                   docFlags,
                                          OCISodaDoc          **document,
                                          OCIError             *errhp,
                                          ub4                   mode);

#### Parameters

| Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| envhp (IN)            | The environment handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| content (IN)          | A string containing the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| contentLength (IN)    | The string length of the content parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| key (IN)              | A string that contains the document key. The key can be `NULL`.<br>For example, in the default case, collection has auto-generated keys, so you do not want to set the key on the document (if you do, you get an error when you pass such a doc to a write operation, such as insert). You only want to set a non-`NULL` key if your collection is configured with client-assigned keys, which is not the default.                                                                                                                                                                                                                                                                                                                                                                                                       |
| keylen (IN)           | The length of the key string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| mediaType (IN)        | A string that contains the document media type. If no media type value is specified, it defaults to "`application/json`". By specifying a value, you can create non-JSON documents (using a media type other than "`application/json`").                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| mediaTypeLength (IN)  | The length of the media type string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| docFlags (IN)         | The flags used to create the document. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| document (OUT)        | Allocates and returns the document handle. Call `OCIHandleFree()` to free the document handle when it is no longer required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| errhp (IN/OUT)        | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| mode (IN)             | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

#### Returns

`OCI_SUCCESS`, if the document is successfully created.

`OCI_ERROR`, if the document creation failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Creating Documents with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-793B416B-2E8C-4425-9B35-381855E673AA).

### 36.2.21 OCISodaDocGetNext()

Gets the next document from the cursor.

#### Purpose

To get the next document from the cursor.

#### Syntax

    sword OCISodaDocGetNext(OCISvcCtx                *svchp,
                            const OCISodaDocCursor   *cursor,
                            OCISodaDoc              **doc,
                            OCIError                 *errhp,
                            ub4                       mode);

#### Parameters

| Parameter   | Description                                                                                                                                   |
|:------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)  | The service context.                                                                                                                          |
| cursor (IN) | The cursor for the document results.                                                                                                          |
| doc (OUT)   | The document handle returned by the cursor.                                                                                                   |
| errhp (OUT) | The error handle.                                                                                                                             |
| mode (IN)   | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — the default mode meaning calling this function executes its statement. |

#### Returns

`OCI_SUCCESS`, if the document is found in the specified collection.

`OCI_ERROR`, if the document search failed. The `OCIError` parameter has the necessary error information.

`OCI_NO_DATA`, if data not found. (exit criteria).

#### Usage Notes

None.

#### Examples

for examples, see [Finding Documents in Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E).

### 36.2.22 OCISodaFind()

Finds the documents in a collection matching the attributes set in operation options input handle. If no conditions are set, all the documents in the collection are returned.

#### Purpose

To find the documents in a collection matching the attributes set in operation options input handle. If no conditions are set, then all the documents in the collection are returned.

#### Syntax

    sword OCISodaFind(OCISvcCtx                      *svchp,
                      const OCISodaColl              *coll,
                      const OCISodaOperationOptions  *findOptions,
                      ub4                             docFlags,
                      OCISodaDocCursor              **cursor,
                      OCIError                       *errhp,
                      ub4                             mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| coll (IN)        | The collection to search for the documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| findOptions (IN) | The operation options handle with attributes to drive the find operation. If no attributes are set, then all the documents in the collection are returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| docFlags (IN)    | The following flags control the encoding of the returned document's content. Valid flag options are<br>• `OCI_DEFAULT` — Document content is returned in the character set defined by the environment handle (or environment variable NLS_LANG, if not set for the handle).<br>• `OCI_SODA_AS_STORED` — Document content is returned in the character set in which the content was stored in the database. Use this parameter value only for BLOB content. If the content is not stored in a BLOB instance then an error is raised.<br>• `OCI_SODA_AS_AL32UTF8` — Document content is returned in the character set `AL32UTF8`.                                                                                                                                                                   |
| cursor (OUT)     | The cursor for the document results.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| errhp (OUT)      | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaFindOneWithKey()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if the document is found in the specified collection.

`OCI_ERROR`, in case of hard errors. The `OCIError` parameter has the necessary error information.

`OCI_NO_DATA`, if data not found. (exit criteria).

#### Usage Notes

None.

#### Examples

For examples, see [Finding Documents in Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E).

### 36.2.23 OCISodaFindOne()

Finds the document in a collection matching the attributes set in operation options input handle. If more than one document in the collection matches the attributes set, then the first document is returned.

#### Purpose

To find the document in a collection matching the attributes set in operation options input handle. If more than one document in the collection matches the attributes set, then the first document is returned.

#### Syntax

    sword OCISodaFindOne(OCISvcCtx                      *svchp,
                         const OCISodaColl              *coll,
                         const OCISodaOperationOptions  *findOptions,
                         ub4                             docFlags,
                         OCISodaDoc                    **doc,
                         OCIError                       *errhp,
                         ub4                             mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| coll (IN)        | The collection to search for the documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| findOptions (IN) | The operation options handle with attributes to drive the find operation. If more than one document in the collection matches, then the first matching document is returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| docFlags (IN)    | The following flags control the encoding of the returned document's content. Valid flag options are:<br>• `OCI_DEFAULT` — Document content is returned in the character set defined by the environment handle (or environment variable NLS_LANG, if not set for the handle).<br>• `OCI_SODA_AS_STORED` — Document content is returned in the character set in which the content was stored in the database. Use this parameter value only for BLOB content. If the content is not stored in a `BLOB` instance then an error is raised.<br>• `OCI_SODA_AS_AL32UTF8` —Document content is returned in the character set `AL32UTF8`.                                                                                                                                                                 |
| doc (OUT)        | The document found (returns `NULL` if no document is found).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| errhp (OUT)      | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaFindOneWithKey()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if the document is found in the specified collection.

`OCI_ERROR`, if the document search failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Finding Documents in Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E).

### 36.2.24 OCISodaFindOneWithKey()

Finds a single document in a collection, given a key.

#### Purpose

To find a single document in a collection, given a key.

**Note:**

This is a convenience method for finding a document by a key. A more general method is `OCISodaFindOne.`

#### Syntax

    sword OCISodaFindOneWithKey(OCISvcCtx          *svchp,
                                const OCISodaColl  *coll,
                                const OraText      *key,
                                ub4                 keylen,
                                ub4                 docFlags,
                                OCISodaDoc        **doc,
                                OCIError           *errhp,
                                ub4                 mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| coll (IN)      | The collection to search for the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| key (IN)       | The key used to identify the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| keylen (IN)    | The length of the key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| docFlags (IN)  | The following flags control the encoding of the returned document's content. Valid flag options are:<br>• `OCI_DEFAULT` — Document content is returned in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle).<br>• `OCI_SODA_AS_STORED` — Document content is returned in the character set in which the content was stored in the database. Use this parameter value only for `BLOB` content. If the content is not stored in a BLOB instance then an error is raised.<br>• `OCI_SODA_AS_AL32UTF8` — Document content is returned in the character set AL32UTF8.                                                                                                                                                                |
| doc (OUT)      | Allocates and returns the document handle if the document is found in the collection. If the document is not found in the collection, a `NULL` document is returned and the function returns `OCI_NO_DATA`. Call `OCIHandleFree()` to free the collection handle when the find operation completes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| errhp (IN/OUT) | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• **Note:**<br>• `OCISodaFindOneWithKey()` does not make any changes to the database; however, you can use this mode to commit an existing transaction without performing another round trip. |

#### Returns

`OCI_SUCCESS`, if the document is found in the specified collection.

`OCI_NO_DATA`, if the document was not found.

`OCI_ERROR`, if there was an error in trying to find the document. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Finding Documents in Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E)

### 36.2.25 OCISodaIndexCreate()

Creates an index with an index specification.

#### Purpose

To create an index with an index specification. The following three types of index specifications can be supplied, B-tree, JSON search index, and spatial.

#### Syntax

    sword OCISodaIndexCreate(OCISvcCtx         *svchp,
                             const OCISodaColl *coll,
                             const OraText     *indexspec,
                             ub4                speclen,
                             OCIError          *errhp,
                             ub4                mode);

#### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)     | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| coll (IN)      | The handle for the collection to be indexed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| indexspec (IN) | The index specification.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| speclen(IN)    | The index specification length.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| errhp (OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)      | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` - Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if index creation on the specified collection is successful.

`OCI_ERROR`, if index creation results in an error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

This function, unlike a SQL DDL operation, does not perform a commit operation before or after it runs. (Unless you specify OCI_SODA_ATOMIC_COMMIT mode, only then is the current transaction committed after the operation runs).

#### Examples

For examples, see [Indexing the Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-5F6ED443-F775-4529-BEE9-93D84062D90F).

**Related Topics**

- [Overview of SODA Indexing](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-4848E6A0-58A7-44FD-8D6D-A033D0CCF9CB)
- [SODA Index Specifications (Reference)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-00C06941-6FFD-4CEB-81B6-9A7FBD577A2C)

### 36.2.26 OCISodaIndexDrop()

Drops an index.

#### Purpose

To drop an index.

#### Syntax

    sword OCISodaIndexDrop(OCISvcCtx   *svchp,
                           OraText     *indexname,
                           ub4          indexnamelen,
                           boolean     *isDropped,
                           OCIError    *errhp,
                           ub4          mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| indexname (IN)   | The index name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| indexnamelen(IN) | The index name length.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| isDropped (OUT)  | Returns the status of the drop operation: `TRUE` if the drop operation is successful, `FALSE` if the index with the specified name does not exist.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| errhp (OUT)      | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_INDEX_DROP_FORCE` - Forces the index to be dropped. Should only be used for JSON Search Index or Spatial Index. Not supported for dropping B-tree indexes.<br>• Note: See [DROP INDEX](../sqlrf/DROP-INDEX.md) for more information about FORCE flag.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if dropping an index on specified collection is successful.

`OCI_ERROR`, if dropping an index results in an error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

This function, unlike a SQL DDL operation, does not perform a commit operation before or after it runs. (Unless you specify `OCI_SODA_ATOMIC_COMMIT` mode, only then is the current transaction committed after the operation runs).

#### Examples

For example, see [Dropping an Index with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-5F6ED443-F775-4529-BEE9-93D84062D90F__DROPPINGANINDEXWITHSODAFORC-D1C1B14E).

### 36.2.27 OCISodaInsert()

Inserts a document into a collection.

#### Purpose

Insert a document into a collection.

#### Syntax

    sword OCISodaInsert(OCISvcCtx   *svchp,
                        OCISodaColl *collection,
                        OCISodaDoc  *document,
                        OCIError    *errhp,
                        ub4          mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| collection (IN) | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| document (IN)   | The handle of the document that is to be inserted into the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| errhp (IN/OUT)  | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6).

### 36.2.28 OCISodaInsertAndGet()

Inserts a document into a collection, returning a result document containing all document components except for content.

#### Purpose

Insert a document into a collection, returning a result document containing all document components except for content. The components generated by SODA during the insert, such as key (if the collection has auto-assigned keys), last-modified timestamp, created-on timestamp, and version, are returned as part of the result document.

#### Syntax

    sword OCISodaInsertAndGet(OCISvcCtx      *svchp,
                              OCISodaColl    *collection,
                              OCISodaDoc    **document,
                              OCIError       *errhp,
                              ub4             mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| collection (IN)   | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| document (IN/OUT) | The handle of the document that is to be inserted into the collection. Returns the result document through this same parameter as it is an `IN/OUT`.<br>**Caution:**<br>Because the result document is returned using the same parameter, you need to save a reference to the input document handle so that you can free it later, along with the result document handle, using `OCIHandleFree()`. If you do not save a reference to the input document handle, it is overwritten with a reference to the result document, and the input document handle will never be properly freed (it's a memory leak). |
| errhp (IN/OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.            |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6).

### 36.2.29 OCISodaInsertAndGetWithOpts ()

Inserts a SODA document with options.

#### Purpose

To insert a SODA document with options.

#### Syntax

    sword OCISodaInsertAndGetWithOpts(OCISvcCtx                 *svchp,
                                      OCISodaColl               *collection,
                                      OCISodaDoc               **document,
                                      OCISodaOperationOptions   *oproptns,
                                      OCIError                  *errhp,
                                      ub4                        mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| collection (IN)   | The collection handle in which you want to insert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| document (IN/OUT) | Document handle to be inserted and returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| oproptns (IN)     | Operation options handle                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| errhp (IN/OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document is inserted.

### 36.2.30 OCISodaInsertAndGetWithCtnt()

Inserts a document into a collection using just the content, returning a result document containing all document components except for content.

#### Purpose

Insert a document into a collection using just the content, returning a result document containing all document components except for content. The components generated by SODA during the insert, such as key (if the collection has auto-assigned keys), last-modified timestamp, created-on timestamp, and version, are returned as part of the result document.

**Note:**

This is a convenience method for inserting a JSON document without constructing a document handle for them. A more general method is `OCISodaInsertAndGet`.

#### Syntax

    sword OCISodaInsertAndGetWithCtnt(OCISvcCtx        *svchp,
                                      OCISodaColl      *collection,
                                      const OraText    *key,
                                      ub4               keyLength,
                                      const void       *content,
                                      ub4               contentLength,
                                      ub4               docFlags,
                                      OCISodaDoc      **document,
                                      OCIError         *errhp,
                                      ub4               mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)         | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection (IN)    | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| key (IN)           | A string that contains the document key. Must be `NULL` if inserting a document into a collection configured for auto-generated keys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| keyLength (IN)     | The length of the key string. Must be 0 if inserting a document into a collection configured for auto-generated keys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| content (IN)       | A string containing the JSON content for the document.<br> Note: This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| contentLength (IN) | The string length of the `content` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| docFlags (IN)      | The encoding flags used to indicate the encoding of the supplied document's content. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| document (OUT)     | Allocates and returns a result document containing all document components except for content. The components generated by SODA during the insert, such as key (if the collection has auto-assigned keys), last-modified timestamp, created-on timestamp, and version, are returned as part of the result document.<br>If `NULL` is passed for this parameter, then the result document is not returned. (In other words, the function then behaves identically to the `OCISodaInsertWithCtnt()` function, which does not return a result document).                                                                                                                                                                                                                                                                                                                    |
| errhp (IN/OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                        |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6)

### 36.2.31 OCISodaInsertWithCtnt()

Inserts a document into a collection using only the content.

#### Purpose

Insert a document into a collection using only the content.

**Note:**

This is a convenience method for inserting a JSON document without constructing a document handle for them. A more general method is `OCISodaInsert`.

#### Syntax

    sword OCISodaInsertWithCtnt(OCISvcCtx           *svchp,
                                OCISodaColl         *collection,
                                const OraText       *key,
                                ub4                  keyLength,
                                const void          *content,
                                ub4                  contentLength,
                                ub4                  docFlags,
                                OCIError            *errhp,
                                ub4                  mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)         | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| collection (IN)    | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| key (IN)           | A string that contains the document key. Must be `NULL` if inserting a document into a collection configured for auto-generated keys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| keyLength (IN)     | The length of the key string. Must be 0 if inserting a document into a collection configured for auto-generated keys.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| content (IN)       | A string containing the JSON content for the document.<br>Note: This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| contentLength (IN) | The length of the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| docFlags (IN)      | The encoding flags used to indicate the encoding of the supplied document's content. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| errhp (IN/OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                        |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Inserting Documents into Collections with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-3111C13E-2809-44EC-B618-80D4CF1E0CA6).

### 36.2.32 OCISodaRemove()

Removes the documents matching the attributes set in operation options input handle from the collection. If no attributes are set, then all the documents in the collection are removed.

#### Purpose

To remove the documents matching the attributes set in operation options input handle from the collection. If no attributes are set, then all the documents in the collection are removed.

#### Syntax

    sword OCISodaRemove(OCISvcCtx                       *svchp,
                        const OCISodaColl               *coll,
                        const OCISodaOperationOptions   *optns,
                        ub8                             *removeCount,
                        OCIError                        *errhp,
                        ub4                              mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| coll (IN)         | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| optns (IN)        | The operation options handle with attributes to drive the remove operation. If no attributes are set, all the documents in the collection are removed. If `OCI_ATTR_SODA_SKIP `and ` OCI_ATTR_SODA_LIMIT` attributes are set on the operation options handle, then they are ignored. That is, they do not apply to write operations such as removes.                                                                                                                                                                                                                                             |
| removeCount (OUT) | The number of documents removed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| errhp (OUT)       | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if one or more documents are removed from the specified collection.

`OCI_ERROR`, if the document removal failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Removing Documents from a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-F3C144A6-7F15-4ABC-AE0E-5C962C5A7AFE)

### 36.2.33 OCISodaRemoveOneWithKey()

Removes a document from a collection given a key.

#### Purpose

Remove a document from a collection given a key.

**Note:**

This is a convenience method for removing a document with a single key. A more general method is `OCISodaRemove`.

#### Syntax

    sword OCISodaRemoveOneWithKey(OCISvcCtx          *svchp,
                                  const OCISodaColl  *coll,
                                  const OraText      *key,
                                  ub4                 keylength,
                                  boolean            *isRemoved,
                                  OCIError           *errhp,
                                  ub4                 mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| coll (IN)       | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| key (IN)        | The key of the document to be removed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| keylength (IN)  | The length of key of the document to be removed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| isRemoved (OUT) | Returns `TRUE` if a document was found with the specified key and removed; `FALSE` if no document could be found with the specified key.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| errhp (IN/OUT)  | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document with the specified key was not found. `OCI_SUCCESS` is still returned (and `isRemoved` will be set to `FALSE`). Check that the `isRemoved` parameter is set to `TRUE` to know whether the document has been removed.

`OCI_ERROR`, if the document removal operation failed during execution due to a SQL error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Removing Documents from a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-F3C144A6-7F15-4ABC-AE0E-5C962C5A7AFE).

### 36.2.34 OCISodaReplOne()

Replaces a document matching the attributes set in operation options input handle.

#### Purpose

To replace a document matching the attributes set in operation options input handle. In order to uniquely identify the document to be replaced, at least `OCI_ATTR_SODA_KEY` key must be set in operation options. Other attributes can also be set.

#### Syntax

    sword OCISodaReplOne(OCISvcCtx                       *svchp,
                         const OCISodaColl               *coll,
                         const OCISodaOperationOptions   *optns,
                         OCISodaDoc                      *document,
                         boolean                         *isReplaced,
                         OCIError                        *errhp,
                         ub4                              mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| coll (IN)        | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| optns (IN)       | The operation options handle with attributes to drive the replace operation. At least the key, `OCI_ATTR_SODA_KEY` attribute must be set to uniquely identify the document to be replaced. Otherwise the operation returns an error. Other attributes such as `OCI_ATTR_SODA_VERSION`, and `OCI_ATTR_SODA_FILTER` can also be set. If `OCI_ATTR_SODA_SKIP` and `OCI_ATTR_SODA_LIMIT` attributes are set on the operation options handle, then they are ignored. That is, they are not applied to the write operations such as replace.                                                           |
| document (IN)    | The document handle to use as the replacement of the document currently in the collection. Only the content and media type component from this handle is used during the replace operation (that is, this operation replaces the content and media type of the document in the collection). Other components, if set on the input document, are ignored.                                                                                                                                                                                                                                         |
| isReplaced (OUT) | Whether the document is replaced or not. Returns `TRUE` if replaced, otherwise it returns `FALSE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| errhp (OUT)      | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` - Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, document is replaced in the specified collection.

`OCI_ERROR`, if the document replacment failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6).

### 36.2.35 OCISodaReplOneAndGet()

Replaces a document matching the attributes set in operation options input handle, and returns the handle to the result document.

#### Purpose

To replace a document matching the attributes set in operation options input handle, and returns the handle to the result document. In order to uniquely identify the document to be replaced, at least `OCI_ATTR_SODA_KEY` key must be set in operation options. Other attributes can also be set.

#### Syntax

    sword OCISodaReplOneAndGet(OCISvcCtx                       *svchp,
                               const OCISodaColl               *coll,
                               const OCISodaOperationOptions   *optns,
                               OCISodaDoc                     **document,
                               boolean                         *isReplaced,
                               OCIError                        *errhp,
                               ub4                              mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| coll (IN)         | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| optns (IN)        | The operation options handle with attributes to drive the replace operation. At least the key, `OCI_ATTR_SODA_KEY` attribute must be set to uniquely identify the document to be replaced. Otherwise the operation returns an error. Other attributes such as `OCI_ATTR_SODA_VERSION`, and `OCI_ATTR_SODA_FILTER` can also be set. If `OCI_ATTR_SODA_SKIP` and `OCI_ATTR_SODA_LIMIT` attributes are set on the operation options handle, then they are ignored. That is, they are not applied to the write operations such as replace.                                                                                                                                                                                                                                                                                                                                                        |
| document (IN/OUT) | The document handle to use as the replacement of the document currently in the collection. Only the content and media type component from this handle is used during the replace operation (that is, this operation replaces the content and media type of the document in the collection). Other components, if set on the input document, are ignored. Returns the result document through this same parameter as it is an `IN/OUT`.<br>**Caution:**<br>Because the result document is returned using the same parameter, you need to save a reference to the input document handle so that you can free it later, along with the result document handle, using `OCIHandleFree()`. If you do not save a reference to the input document handle, it is overwritten with a reference to the result document, and the input document handle will never be properly freed (it's a memory leak). |
| isReplaced (OUT)  | Whether the document is replaced or not. Returns `TRUE` if replaced, otherwise it returns `FALSE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| errhp (OUT)       | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                                              |

#### Returns

`OCI_SUCCESS`, if the document is replaced in the specified collection.

`OCI_ERROR`, if the document replacement failed due to hard errors. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6).

### 36.2.36 OCISodaReplOneAndGetWithCtnt()

Replaces the content of the document matching the attributes set in operation options input handle with new content, and returns the handle to the result document.

#### Purpose

To replace the content of the document matching the attributes set in operation options input handle with new content, and returns the handle to the result document containing all components except for the content, including the updated ones, such as the last-modified timestamp and version. In order to uniquely identify the document to be replaced, at least `OCI_ATTR_SODA_KEY` key must be set in operation options. Other attributes can also be set.

**Note:**

This is a convenience method for replacing a document with a JSON document without constructing a document handle for the replacement document. A more general method is `OCISodaReplOneAndGet`. This method is only for JSON documents. That is, the supplied replacement document must be a JSON document and the target document that is being replaced in the collection may or may not be a JSON document.

#### Syntax

    sword OCISodaReplOneAndGetWithCtnt(OCISvcCtx                     *svchp,
                                       const OCISodaColl             *coll,
                                       const OCISodaOperationOptions *optns,
                                       const void                    *content,
                                       ub4                            contentLen,
                                       ub4                            docFlags,
                                       OCISodaDoc                   **document,
                                       boolean                       *isReplaced,
                                       OCIError                      *errhp,
                                       ub4                            mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| coll (IN)        | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| optns (IN)       | The operation options handle with attributes to drive the replace operation. At least the key, `OCI_ATTR_SODA_KEY` attribute must be set to uniquely identify the document to be replaced. Otherwise the operation returns an error. Other attributes such as `OCI_ATTR_SODA_VERSION`, and `OCI_ATTR_SODA_FILTER` can also be set. If `OCI_ATTR_SODA_SKIP` and `OCI_ATTR_SODA_LIMIT` attributes are set on the operation options handle, then they are ignored. That is, they are not applied to the write operations such as replace.                                                                                                                                                                                                                                                                                                                                  |
| content (IN)     | A string containing the JSON content of the document.<br>Note: This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| contentLen (IN)  | The length of the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| docFlags (IN)    | The encoding flags used to indicate the encoding of the supplied document's content. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| document (OUT)   | Result document contains all components except for the content, including the updated ones, such as the last-modified timestamp and version.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| isReplaced (OUT) | Whether the document is replaced or not. Returns `TRUE` if replaced, otherwise it returns `FALSE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| errhp (OUT)      | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                        |

#### Returns

`OCI_SUCCESS`, if the document is replaced in the specified collection.

`OCI_ERROR`, if the document replacement failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6).

### 36.2.37 OCISodaReplOneAndGetWithKey()

Replaces a document in a collection given a key and returns the handle to the result document.

#### Purpose

To replace a document in a collection given a key and return the handle to the result document containing all components except content, including the updated ones, such as the last-modified timestamp and version.

**Note:**

This is a convenience method for replacing a document by a key. A more general method is `OCISodaReplOneAndGet`.

#### Syntax

    sword OCISodaReplOneAndGetWithKey(OCISvcCtx         *svchp,
                                      const OCISodaColl *coll,
                                      const OraText     *key,
                                      ub4                keylength,
                                      OCISodaDoc       **document,
                                      boolean           *isReplaced,
                                      OCIError          *errhp,
                                      ub4                mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| coll (IN)         | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| key (IN)          | The key used to identify the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| keylength (IN)    | The length of the key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| document (IN/OUT) | The document handle to use as the replacement of the document currently in the collection. Only the content and media type component from this handle is used during the replace operation (that is, this operation replaces the content and media type of the document in the collection). Other components, if set on the input document, are ignored. Returns the result document through this same parameter as it is an `IN/OUT`.<br>**Caution:**<br>Because the result document is returned using the same parameter, you need to save a reference to the input document handle so that you can free it later, along with the result document handle, using `OCIHandleFree()`. If you do not save a reference to the input document handle, it is overwritten with a reference to the result document, and the input document handle will never be properly freed (it's a memory leak). |
| isReplaced (OUT)  | Returns `TRUE` if a document was found with the specified key and replaced; `FALSE` if no document could be found with the specified key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| errhp (IN/OUT)    | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                                              |

#### Returns

`OCI_SUCCESS`, if the document with the specified key was not found. `OCI_SUCCESS` is still returned (and `isReplaced` will be set to `FALSE`). Check that the `isReplaced` parameter is set to `TRUE` to know whether the document has been replaced.

`OCI_ERROR`, if the document replacement operation failed during execution due to a SQL error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6)

### 36.2.38 OCISodaReplOneWithCtnt()

Replaces the content of the document matching the attributes set in operation options input handle with new content.

#### Purpose

To replace the content of the document matching the attributes set in operation options input handle with new content. In order to uniquely identify the document to be replaced, at least `OCI_ATTR_SODA_KEY` key must be set in operation options. Other attributes can also be set.

**Note:**

This is a convenience method for replacing a document with a JSON document without constructing a document handle for the replacement document. A more general method is `OCISodaReplOne`. This method is only for JSON documents. That is, the supplied replacement document must be a JSON document and the target document that is being replaced in the collection may or may not be a JSON document.

#### Syntax

    sword OCISodaReplOneWithCtnt(OCISvcCtx                       *svchp,
                                 const OCISodaColl               *coll,
                                 const OCISodaOperationOptions   *optns,
                                 const void                      *content,
                                 ub4                              contentLength,
                                 ub4                              docFlags,
                                 boolean                         *isReplaced,
                                 OCIError                        *errhp,
                                 ub4                              mode);

#### Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)         | The service context.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| coll (IN)          | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| optns (IN)         | The operation options handle with attributes to drive the replace operation. At least the key, `OCI_ATTR_SODA_KEY` attribute must be set to uniquely identify the document to be replaced. Otherwise the operation returns an error. Other attributes such as `OCI_ATTR_SODA_VERSION`, and `OCI_ATTR_SODA_FILTER` can also be set. If `OCI_ATTR_SODA_SKIP` and `OCI_ATTR_SODA_LIMIT` attributes are set on the operation options handle, then they are ignored. That is, they are not applied to the write operations such as replace.                                                                                                                                                                                                                                                                                                                                  |
| content (IN)       | A string containing the JSON content of the document.<br>Note: This method works only for JSON documents.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| contentLength (IN) | The length of the document content.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| docFlags (IN)      | The encoding flags used to indicate the encoding of the supplied document's content. Valid flag options are:<br>• `OCI_DEFAULT` — If you use this parameter value then you are, in effect, declaring that the document content is in the character set defined by the environment handle (or environment variable `NLS_LANG`, if not set for the handle). If that is not the case for a given document, then the result of trying to write the document is unpredictable.<br>• `OCI_SODA_DETECT_JSON_ENC` — Automatically detects the encoding of the document content as either UTF-8, UTF-16 LE, or UTF-16 BE. If you use this parameter value then you are, in effect, declaring that the document content is either UTF-8, UTF-16 LE, or UTF-16 BE. If that is not the case for a given document, then the result of trying to write the document is unpredictable. |
| isReplaced (OUT)   | Whether the document is replaced or not. Returns `TRUE` if replaced, otherwise it returns `FALSE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| errhp (OUT)        | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| mode (IN)          | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.                                                                                                                                                                                                                                                                        |

#### Returns

`OCI_SUCCESS`, if the document is replaced in the specified collection.

`OCI_ERROR`, if the document replacement failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6).

### 36.2.39 OCISodaReplOneWithKey()

Replaces a document in a collection given a key.

#### Purpose

To replace a document in a collection given a key.

**Note:**

This is a convenience method for replacing a document by a key. A more general method is `OCISodaReplOne.`

#### Syntax

    sword OCISodaReplOneWithKey (OCISvcCtx           *svchp,
                                 const OCISodaColl   *coll,
                                 const OraText       *key,
                                 ub4                  keylength,
                                 OCISodaDoc          *document,
                                 boolean             *isReplaced,
                                 OCIError            *errhp,
                                 ub4                  mode);

#### Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)       | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| coll (IN)        | The collection handle for an existing collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| key (IN)         | The key used to identify the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| keylength (IN)   | The length of the key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| document (IN)    | The document handle to use as the replacement of the document currently in the collection. Only the content and media type component from this handle is used during the replace operation (that is, this operation replaces the content and media type of the document in the collection). Other components, if set on the input document, are ignored.                                                                                                                                                                                                                                         |
| isReplaced (OUT) | Returns `TRUE` if a document was found with the specified key and replaced; `FALSE` if no document could be found with the specified key.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| errhp (IN/OUT)   | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)        | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document with the specified key was not found. `OCI_SUCCESS` is still returned (and `isReplaced` will be set to `FALSE`). Check that the `isReplaced` parameter is set to `TRUE` to know whether the document has been replaced.

`OCI_ERROR`, if the document replacement operation failed during execution due to a SQL error. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

For examples, see [Replacing Documents in a Collection with SODA for C](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-25680AEE-1D25-4FF5-803D-7A500A9F2DF6)

### 36.2.40 OCISodaSave()

Saves a document into a collection.

#### Purpose

Save a document into a collection.

This function is equivalent to insert function except that if the client-assigned keys are used, or the document with the specified key already exists in the collection, then it is replaced with the input document. The key is automatically created, unless this collection is configured with client-assigned keys and the key is provided in the input document.

#### Syntax

    sword OCISodaSave(OCISvcCtx   *svchp,
                      OCISodaColl *collection,
                      OCISodaDoc  *document,
                      OCIError    *errhp,
                      ub4          mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| collection (IN) | An opened collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| document (IN)   | The document handle that is used to insert the content into the collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| errhp (OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — the default mode meaning calling this function executes its statement.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document save into the specified collection is successful.

`OCI_ERROR`, if the document save failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

See the example in OCISodaDocCreateWithKeyAndMType().

### 36.2.41 OCISodaSaveAndGet()

Saves a document into a collection, returning a document containing metadata information.

#### Purpose

Save a document into a collection, returning a document containing metadata information, such as key, version, and timestamp information.

This function is equivalent to insert function except that if the client-assigned keys are used, or the document with the specified key already exists in the collection, then it is replaced with the input document. The key is automatically created, unless this collection is configured with client-assigned keys and the key is provided in the input document.

#### Syntax

    sword OCISodaSaveAndGet(OCISvcCtx      *svchp,
                            OCISodaColl    *collection,
                            OCISodaDoc    **document,
                            OCIError       *errhp,
                            ub4             mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| collection (IN)   | An opened collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| document (IN/OUT) | The document structure that is saved into the collection. If the key parameter in the call to `OCISodaDocCreate()` is `NULL`, then the document parameter contains the auto-generated key as well as other information, such as version and creation timestamp.                                                                                                                                                                                                                                                                                                                        |
| errhp (OUT)       | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — the default mode meaning calling this function executes its statement.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document save into the specified collection is successful.

`OCI_ERROR`, if the document save failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

See the example in OCISodaDocCreateWithKeyAndMType().

### 36.2.42 OCISodaSaveAndGetWithOpts()

Saves a SODA document with options.

#### Purpose

To save a SODA document with options.

#### Syntax

    sword OCISodaSaveAndGetWithOpts(OCISvcCtx                *svchp,
                                    OCISodaColl              *collection,
                                    OCISodaDoc              **document,
                                    OCISodaOperationOptions  *oproptns,
                                    OCIError                 *errhp,
                                    ub4                       mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| collection (IN)   | The collection handle in which you want to insert.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| document (IN/OUT) | The document handle to be inserted and returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| oproptns (IN)     | Operation options handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| errhp (IN)        | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes.<br>• `OCI_SODA_ATOMIC_COMMIT` — When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document is saved.

### 36.2.43 OCISodaSaveWithCtnt()

Saves a document into a collection with its content.

#### Purpose

To save the document which has specified keys.

This function is equivalent to insert function except that if the client-assigned keys are used, or the document with the specified key already exists in the collection, then it is replaced with the input document. The key is automatically created, unless this collection is configured with client-assigned keys and the key is provided in the input document.

#### Syntax

    sword OCISodaSaveWithCtnt(OCISvcCtx         *svchp,
                              OCISodaColl       *collection,
                              const OraText     *key,
                              ub4                keylength,
                              const void        *content,
                              ub4                contentlen,
                              ub4                docFlags,
                              OCIError          *errhp,
                              ub4                mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| collection (IN) | An opened collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| key (IN)        | The specified key of the document to be saved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| keylength(IN)   | The length of the key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| content (IN)    | A string that contains `content` of the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| contentlen(IN)  | The length of the `content` string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| docFlags (IN)   | The encoding flags used to save the document. Valid flag options are:<br>• `OCI_DEFAULT` — The default value.<br>• `OCI_SODA_DETECT_JSON_ENC` — Detect the JSON encoding.<br>• `OCI_SODA_AS_STORED` — Retrieve as stored in `BLOB` column.<br>• `OCI_SODA_AS_AL32UTF8` — Retrieve as `UTF-8`.                                                                                                                                                                                                                                                                                          |
| errhp (OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — the default mode meaning calling this function executes its statement.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the collection is successfully created.

`OCI_ERROR`, if the collection is not created. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

See the example in OCISodaDocCreateWithKeyAndMType().

### 36.2.44 OCISodaSaveAndGetWithCtnt()

Saves a document into a collection and gets the new document handle.

#### Purpose

Saves the document which has specified keys and new document handle to obtain the saved documents.

This function is equivalent to insert function except that if the client-assigned keys are used, or the document with the specified key already exists in the collection, then it is replaced with the input document. The key is automatically created, unless this collection is configured with client-assigned keys and the key is provided in the input document.

#### Syntax

    sword OCISodaSaveAndGetWithCont(OCISvcCtx         *svchp,
                                    OCISodaColl       *collection,
                                    const OraText     *key,
                                    ub4                keylength,
                                    const void        *content,
                                    ub4                contentlen,
                                    ub4                docFlags,
                                    OCISodaDoc       **document,
                                    OCIError          *errhp,
                                    ub4                mode);

#### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)        | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| collection (IN)   | An opened collection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| key (IN)          | The specified key for the document to be saved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| keylength(IN)     | The length of the key.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| content (IN)      | A string that contains content of the document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| contentlen(IN)    | The length of the `content` string.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| docFlags (IN)     | The encoding flags used to save the document. Valid flag options are:<br>• `OCI_DEFAULT` — The default value.<br>• `OCI_SODA_DETECT_JSON_ENC` — Detect the JSON encoding.<br>• `OCI_SODA_AS_STORED` — Retrieve as stored in `BLOB` column.<br>• `OCI_SODA_AS_AL32UTF8` — Retrieve as `UTF-8`.                                                                                                                                                                                                                                                                                          |
| document (IN/OUT) | The document handle containing metadata of the saved document.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| errhp (OUT)       | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — the default mode meaning calling this function executes its statement.<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back. |

#### Returns

`OCI_SUCCESS`, if the document insertion into the specified collection is successful.

`OCI_ERROR`, if the document insertion failed. The `OCIError` parameter has the necessary error information.

#### Usage Notes

None.

#### Examples

See the example in OCISodaDocCreateWithKeyAndMType().

### 36.2.45 OCISodaCollTruncate()

Truncates a SODA document collection.

#### Purpose

Truncates the document collection.

    sword OCISodaCollTruncate (OCISvcCtx *svchp,
                              const OCISodaColl   *collection,
                              OCIError            *errhp,
                              ub4                  mode);

#### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| svchp (IN)      | The service context handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| collection (IN) | The collection handle for the collection you want to truncate.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| errhp (OUT)     | The error handle.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| mode (IN)       | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT`<br>• `OCI_SODA_ATOMIC_COMMIT` - When an operation executes in this mode and it completes successfully, then the current transaction is committed after completion. This commits all outstanding changes, not just changes made by the SODA operation. If the operation fails, then only changes made for the SODA operation are rolled back; any uncommitted changes made prior to invocation of the SODA operation are not rolled back.<br>• `OCI_SODA_TRUNCATE_REUSE_STORAGE` |

#### Returns

An Oracle return error code.

#### Usage Notes

None.

### 36.2.46 OCISodaOperKeysSet()

Sets an array of keys on Operation Options Handle.

#### Purpose

Sets an array of keys on Operation Options Handle. Attributes of the operation options handle are set with standard `OCIAttrSet` function. The `OCIAttrSet` function is not used to set the array of keys, because both the array of keys and the array of key lengths need to be set.

**Note:**

If you use function `OCIAttrSet()` to set attribute `OCI_ATTR_SODA_KEY` on an operation-options handle, and you also use function `OCISodaOperKeysSet()` to set multiple keys on the same handle, then only the latest of the two settings takes effect. The effect of the first function invoked is overridden by the effect of the second.

#### Syntax

    sword OCISodaOperKeysSet (const OCISodaOperationOptions  *operhp,
                              OraText                        **keysArray,
                              ub4                            *lengthsArray,
                              ub4                             count,
                              OCIError                       *errhp,
                              ub4                             mode);

#### Parameters

| Parameter         | Description                                                                                                                                             |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| operhp (IN)       | Operation options handle                                                                                                                                |
| keysArray (IN)    | Array of `oratext*` keys                                                                                                                                |
| lengthsArray (IN) | Array of `ub4` lengths corresponding to each key                                                                                                        |
| count  (IN)       | Number of elements in the keys array                                                                                                                    |
| errhp (OUT)       | Error handle                                                                                                                                            |
| mode (IN)         | Specifies the mode of execution. Valid modes are:<br>• `OCI_DEFAULT` — Is the default mode. It means execute the operation as is with no special modes. |

#### Returns

`OCI_SUCCESS`, if the keys were set successfully.

#### Usage Notes

None.

#### Examples

For examples, see [Finding Multiple Documents with Specified Document Keys](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-0CD8625C-61DF-4B82-A93E-A3BB6B379A5E__GUID-04C97005-F38E-43FE-A207-7A977724158F) and [Removing Documents from a Collection Using Document Keys](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-F3C144A6-7F15-4ABC-AE0E-5C962C5A7AFE__GUID-DA7147DD-BFF0-45BF-8F9C-22EB7AE1E609).
