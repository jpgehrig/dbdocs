Lists and describes OCI XML DB Functions.

Table 32-2 lists the OCI XML DB functions that are described in this chapter.

Table 32-2 OCI XML DB Functions  

| Function                           | Purpose                                                  |
|:-----------------------------------|:---------------------------------------------------------|
| OCIBinXmlCreateReposCtxFromConn()  | Create metadata connection context                       |
| OCIBinXmlCreateReposCtxFromCPool() | Create metadata connection context connection pool       |
| OCIBinXmlSetFormatPref()           | Specify that images transferred are in binary XML format |
| OCIBinXmlSetReposCtxForConn()      | Associate data connection with the metadata connection   |
| OCIXmlDbFreeXmlCtx()               | Free an XML context                                      |
| OCIXmlDbInitXmlCtx()               | Initialize an XML context for XML data from the database |

### 32.2.1 OCIBinXmlCreateReposCtxFromConn()

Creates a metadata connection context.

#### Purpose

Creates a metadata connection context (`OCIBinXmlReposCtx`) from the specified `OCIEnv`/`OCISvcCtx` dedicated OCI connection. Note that this connection is dedicated to metadata use.

#### Syntax

    sword OCIBinXmlCreateReposCtxFromConn (   OCIEnv              *env,
                                              OCISvcCtx           *svcctx,
                                              OCIError            *err,
                                              OCIBinXmlReposCtx  **ctx);

#### Parameters

env (IN)
The environment handle.

<!-- -->

svcctx (IN)
The handle to the connection to be used to access the metadata.

<!-- -->

err (IN)
The error handle.

<!-- -->

ctx (OUT)
The metadata context that is created and returned.

#### Returns

Returns -1 for error, 0 for success. The `err` parameter contains more information about the error.

**Related Topics**

- OCIBinXmlCreateReposCtxFromCPool()

### 32.2.2 OCIBinXmlCreateReposCtxFromCPool()

Creates a metadata connection context from the specified connection pool.

#### Purpose

Creates a metadata connection context (`OCIBinXmlReposCtx`) from the specified connection pool. A connection from the connection pool is used whenever any information from the token repository is needed.

#### Syntax

    sword OCIBinXmlCreateReposCtxFromCPool (   OCIEnv              *env,
                                               OCICPool            *cpool,
                                               OCIError            *err,
                                               OCIBinXmlReposCtx  **ctx);

#### Parameters

env (IN)
The environment handle.

<!-- -->

cpool (IN)
The handle to the connection to be used to access the metadata.

<!-- -->

err (IN)
The error handle.

<!-- -->

ctx (OUT)
The metadata context that is created and returned.

#### Returns

Returns -1 for error, 0 for success. The `err` parameter contains more information about the error.

**Related Topics**

- OCIBinXmlCreateReposCtxFromConn()

### 32.2.3 OCIBinXmlSetFormatPref()

Specifies that the images being transferred between client and server for the XML document be in binary XML format.

#### Purpose

In the future, all communication will be in the binary XML format. Binary XML-aware applications can set this.

#### Syntax

    sword OCIBinXmlSetFormatPref (   xmldomdoc   *doc,
                                     ub4          formattype);

#### Parameters

doc (IN)
The pointer to the `domdoc` to which the preference is to be applied.

<!-- -->

formattype (IN)
The type of format to be used for pickling. Currently the only values allowed are `OCIXML_FORMATTYPE_TEXT` and `OCIXML_FORMATTYPE_BINXML`.

#### Returns

Returns -1 for error, 0 for success.

**Related Topics**

- OCIBinXmlSetReposCtxForConn()

### 32.2.4 OCIBinXmlSetReposCtxForConn()

Associates the data connection with the metadata connection.

#### Purpose

Note that with a dedicated connection, the environment handle must be the same for the data connection and for the metadata connection.

#### Syntax

    sword OCIBinXmlSetReposCtxForConn (   OCISvcCtx          *dataconn,
                                          OCIBinXmlReposCtx  *reposctx);

#### Parameters

dataconn (IN)
The data connection handle.

<!-- -->

reposctx (IN)
The pointer to the metadata connection.

#### Returns

Returns -1 for error, 0 for success. The `err` parameter contains more information about the error.

**Related Topics**

- OCIBinXmlSetFormatPref()

### 32.2.5 OCIXmlDbFreeXmlCtx()

Frees an XML context.

#### Purpose

Frees any allocations made by the call to `OCIXmlDbInitXmlCtx()`.

#### Syntax

    void OCIXmlDbFreeXmlCtx ( xmlct   *xctx );

#### Parameters

xctx (IN)
The XML context to terminate.

#### Comments

**See Also:**

[Using OCI XML DB Functions](oci-support-for-xml.md) for a usage example

#### Returns

Returns -1 for error, 0 for success.

**Related Topics**

- OCIXmlDbInitXmlCtx()

### 32.2.6 OCIXmlDbInitXmlCtx()

Initializes an XML context.

#### Purpose

Initializes an XML context for XML data from the database.

#### Syntax

    xmlctx *OCIXmlDbInitXmlCtx (   OCIEnv                *envhp,
                                   OCISvcCtx             *svchp,
                                   OCIError              *errhp,
                                   ocixmldbparam         *params,
                                   ub4                    num_params );

#### Parameters

envhp (IN)
The OCI environment handle.

svchp (IN)
The OCI service handle.

errhp (IN)
The OCI error handle.

params (IN)
The optional possible values in this array are pointers to either the OCI duration, in which the default value is `OCI_DURATION_SESSION`, or to an error handler that is a user-registered callback of prototype:

    void (*err_handler) (sword errcode, (const OraText *) errmsg);

The two parameters of `err_handler` are:

errcode (OUT)
A numeric error value.

errmsg (OUT)
The error message text.

num_params (IN)
Number of parameters to be read from `params.` If the value of `num_params` exceeds the size of array `params`, unexpected behavior results.

#### Comments

**See Also:**

[Using OCI XML DB Functions](oci-support-for-xml.md) for a usage example

#### Returns

Returns either:

- A pointer to structure `xmlctx`, with error handler and callbacks populated with appropriate values. This is later used for all OCI calls.

- NULL, if no database connection is available.

**Related Topics**

- OCIXmlDbFreeXmlCtx()
