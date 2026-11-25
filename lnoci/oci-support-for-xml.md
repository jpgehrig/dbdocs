Oracle XML DB provides support for storing and manipulating XML instances by using the `XMLType` data type. You can access these XML instances with OCI, in conjunction with the C DOM API for XML.

An application program must initialize the usual OCI handles, such as the server handle or the statement handle, and it must then initialize the XML context. The program can either operate on XML instances in the back end or create new instances on the client side. The initialized XML context can be used with all the C DOM functions.

XML data stored in Oracle XML DB can be accessed on the client side with the C DOM structure `xmldocnode`. You can use this structure for binding, defining, and operating on XML values in OCI statements.

This section includes the following topics:

- XML Context

- XML Data on the Server

- Using OCI XML DB Functions

- OCI Client Access to Binary XML

**See Also:**

- [OCI XML DB Functions](oci-xml-databse-functions.md) for information about the XML support in C

- [Oracle XML DB Developer’s Guide](../adxdb/C-API-for-XMLType.md) for more information about using the C API for XML, including a binary XML example

- [Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-XML-parser-for-C.md)for more information about the XML parser for C

- [Oracle Database XML C API Reference](../caxml/package-DOM-API.md) for information about the DOM C APIs for XML

### 23.1 XML Context

An XML context is a required parameter in all the C DOM API functions.

This opaque context encapsulates information pertaining to data encoding, error message language, and so on. The contents of this context are different for XDK and for Oracle XML DB applications.

For Oracle XML DB, there are two OCI functions provided to initialize and free an XML context:

    xmlctx *OCIXmlDbInitXmlCtx (OCIEnv *envhp, OCISvcCtx *svchp, OCIError *errhp,
           ocixmldbparam *params, ub4 num_params);

    void OCIXmlDbFreeXmlCtx (xmlctx *xctx);

### 23.2 XML Data on the Server

XML data on the server can be operated on with OCI statement calls. You can bind and define `XMLType` values using `xmldocnode`, as with other object instances.

OCI statements are used to select XML data from the server. This data can be used in the C DOM functions directly. Similarly, the values can be bound back to SQL statements directly.

### 23.3 Using OCI XML DB Functions

To initialize and terminate the XML context, use the functions `OCIXmlDbInitXmlCtx()` and `OCIXmlDbFreeXmlCtx()` respectively.

The header file `ocixmldb.h` is used with the unified C API.

Example 23-1 is a code fragment of a tested example that shows how to perform operations with the C API.

Example 23-1 Initializing and Terminating XML Context with a C API

    #ifndef S_ORACLE
    #include <s.h>
    #endif
    #ifndef ORATYPES_ORACLE
    #include <oratypes.h>
    #endif
    #ifndef XML_ORACLE
    #include <xml.h>
    #endif
    #ifndef OCIXML_ORACLE
    #include <ocixmldb.h>
    #endif
    #ifndef OCI_ORACLE
    #include <oci.h>
    #endif
    #include <string.h>

    typedef struct test_ctx {
            OCIEnv *envhp;
            OCIError *errhp;
            OCISvcCtx *svchp;
            OCIStmt *stmthp;
            OCIServer *srvhp;
            OCIDuration dur;
            OCISession *sesshp;
            oratext *username;
            oratext *password;
    } test_ctx;

    ...
    void main()
    {
      test_ctx temp_ctx;
      test_ctx *ctx = &temp_ctx;
      OCIType *xmltdo = (OCIType *) 0;
      xmldocnode *doc = (xmldocnode *)0;
      ocixmldbparam params[1];
      xmlnode *quux, *foo, *foo_data, *top;
      xmlerr err;
      sword status = 0;
      xmlctx *xctx;
     ...
      /* Initialize envhp, svchp, errhp, dur, stmthp */
      ...

      /* Get an xml context */
      params[0].name_ocixmldbparam = XCTXINIT_OCIDUR;
      params[0].value_ocixmldbparam = &ctx->dur;
      xctx = OCIXmlDbInitXmlCtx(ctx->envhp, ctx->svchp, ctx->errhp, params, 1);

    /* Do unified C API operations next */
    ...

    /* Free the statement handle using OCIHandleFree() */
    ...
    /* Free the allocations associated with the context */
    OCIXmlDbFreeXmlCtx(xctx);
    /* Free envhp, svchp, errhp, stmthp */
    ...
    }

**See Also:**

- [OCIXmlDbInitXmlCtx()](oci-xml-db-functions.md)

- [OCIXmlDbFreeXmlCtx()](oci-xml-db-functions.md)

### 23.4 OCI Client Access to Binary XML

The middle tier and client tiers can produce, consume, and process XML in binary XML format.

The C application fetches data from the XML DB repository, performs updates on the XML using DOM, and stores it back in the database. Or an XML document is created or input on the client and XSLT, XQuery, and other utilities can be used on it. Then the output XML is saved in XML DB.

A client application requires a connection (called a metadata connection) to the metadata repository (typically a back-end database) to fetch token definitions, XML schemas, and DTDs while encoding or decoding a binary XML document.

A repository context is initialized using either a dedicated connection or a connection pool. The connection obtained from the repository context is used to fetch metadata such as token definitions and XML schemas. In contrast, the application also has data connections that are used for the regular transfer of data (including XML data) to and from the database. A repository context is explicitly associated with (one or more) data connections. When XML data is read or written from or to the database using the data connection, the appropriate repository context is accessed during the underlying encode or decode operations. As required, the metadata connection is used to fetch the metadata from the repository.

This section includes the following topics:

- Accessing XML Data from an OCI Application

- Repository Context

- Create Repository Context from a Dedicated OCI Connection

- Create Repository Context from a Connection Pool

- About Associating Repository Context with a Data Connection

- About Setting XMLType Encoding Format Preference

- Example of Using a Connection Pool

#### 23.4.1 Accessing XML Data from an OCI Application

Your C application can use OCI to access persistent XML in the database and the Unified XML C API to operate on the fetched XML data.

The following steps are taken by a client application:

1.  Create the usual OCI handles such as `OCIEnv`, `OCISvcCtx`, and `OCIError`.
2.  Create one or more repository contexts to fetch the binary XML metadata.
3.  Associate the repository context with the data connection.
4.  Bind or define (`xmldocnode`) variables into the select, insert, and update statements.
5.  Execute the select, insert, or update statement to fetch or store the XML document. At this point, the client OCI libraries interact with the database back end to fetch the needed XML Schemas, DTDs, token definitions, and so on.
6.  Use the Unified C API to operate on the XML data (DOM).

#### 23.4.2 Repository Context

`OCIBinXmlReposCtx` is the repository context data structure.

The client application creates this context by providing the connection information to the metadata repository. An application can create multiple repository contexts to connect to multiple token repositories. A repository context is explicitly associated with a data connection (`OCISvcCtx`). When the system must fetch metadata to encode or decode data to or from a data connection, it accesses the appropriate metadata.

It is recommended that applications create one repository context per `OCIEnv`. This allows better concurrency for multithreaded applications.

The repository context can be created out of a dedicated OCI connection or an OCI connection pool.

#### 23.4.3 Create Repository Context from a Dedicated OCI Connection

`OCIBinXmlCreateReposCtxFromConn()` creates a repository context using the specified dedicated OCI connection.

The OCI connection is only to be used for metadata access and should not be used in any other scenarios by the application. Also note that the access to this connection is serialized; that is, if multiple threads try to use the same connection, access is limited to one thread at a time. For scalability reasons, it is recommended that applications create a repository context using a connection pool, as described in the next section.

Note: You can also potentially pass in the same connection as the one being used for data. However, this might result in an error in certain cases where the client system attempts to contact the metadata repository while part of another operation (such as select or insert).

**See Also:**

[OCIBinXmlCreateReposCtxFromConn()](oci-xml-db-functions.md)

#### 23.4.4 Create Repository Context from a Connection Pool

`OCIBinXmlCreateReposCtxFromCPool()` creates a repository context from a connection pool.

When the application accesses the back-end repository, any available connection from the pool is used. Further, this connection is released back to the pool as soon as the metadata operation is complete. Connection pools are highly recommended for multithreaded application scenarios. Different threads can use different connections in the pool and release them as soon as they are done. This approach allows for higher scalability and concurrency with a smaller number of physical connections.

**See Also:**

[OCIBinXmlCreateReposCtxFromCPool()](oci-xml-db-functions.md)

#### 23.4.5 About Associating Repository Context with a Data Connection

`OCIBinXmlSetReposCtxForConn()` associates a repository context with a data connection described by `OCISvcCtx` `*`.

Multiple data connections can share the same repository context, but access to the repository can be serialized (if it is based on a dedicated connection). When the system must fetch the metadata for encode or decode operations, it looks up the appropriate repository connection from the `OCIEnv`, `OCISvcCtx` pair and uses it to fetch the metadata required.

**See Also:**

[OCIBinXmlSetReposCtxForConn()](oci-xml-db-functions.md)

#### 23.4.6 About Setting XMLType Encoding Format Preference

By default, XML data sent to the database is encoded in one of these possible formats (text, object-relational, or binary XML) based on certain internal criteria such as the source format (if it was read from the DB). `OCIBinXmlSetFormatPref()` provides an explicit mechanism to set the preference for encoding format. In the future, the default format can be binary XML, but this function could be used to override it if needed.

**See Also:**

[OCIBinXmlSetFormatPref()](oci-xml-db-functions.md)

#### 23.4.7 Example of Using a Connection Pool

Creating a repository context from a connection pool and associating the repository context with a data connection is shown in this example in the XML DB documentation.

The database is local and the test is in single-threaded mode.

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/C-API-for-XMLType.md) for more information about using OCI and the C API for XML with Oracle XML DB
