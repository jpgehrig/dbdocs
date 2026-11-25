The following table lists all C datatypes and their descriptions.

Table 1-1 Summary of Datatypes for XML C Implementation

| Datatype      | Purpose                                                                                                                        |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------|
| oracheck      | Checkword for validating data structures.                                                                                      |
| oraerr        | Error code: `0` is success, non-`0` is failure.                                                                                |
| oraprop_id    | The id of property; if `>= 0` it is valid, if `< 0`, it is invalid.                                                            |
| oramemctx     | Opaque memory context.                                                                                                         |
| oraprop       | Property name.                                                                                                                 |
| oraprop_t     | Property value type.                                                                                                           |
| oraprop_v     | Value: union of storage for all data types.                                                                                    |
| orastream     | Opaque stream object.                                                                                                          |
| orastreamhdl  | Storage for file handles.                                                                                                      |
| xmlcmphow     | Constant used for DOM Range comparisons.                                                                                       |
| xmlctx        | Context shared for all documents in an XML session.                                                                            |
| xmldfsrct     | Specifies input types for `XmlDiff` operations                                                                                 |
| xmlerr        | Numeric error code returned by many functions.                                                                                 |
| xmlevctx      | XML Event context.                                                                                                             |
| xmlhasht      | The hash value of an XML tree or sub-tree; also known as a digest.                                                             |
| xmlistream    | Generic user-defined input stream.                                                                                             |
| xmliter       | Control structure for DOM2 `NodeIterator` and `TreeWalker`.                                                                    |
| xmlnodetype   | The numeric type code of a node.                                                                                               |
| xmlostream    | Generic user-defined output stream.                                                                                            |
| xmlpoint      | XPointer point location.                                                                                                       |
| xmlrange      | Controls structure for DOM2 Range.                                                                                             |
| xmlsoapbind   | Binding for SOAP connections.                                                                                                  |
| xmlsoapcon    | SOAP connection object.                                                                                                        |
| xmlsoapctx    | Context for SOAP operations.                                                                                                   |
| xmlsoaprole   | Role for a SOAP node.                                                                                                          |
| xmlshowbits   | Bit flags used to select which node types to show.                                                                             |
| xmlurlacc     | This is an enumeration of the known access methods for retrieving data from a URL.                                             |
| xmlurlhdl     | This union contains the handle(s) needed to access URL data, be it a stream or `stdio` pointer, file descriptor(s), and so on. |
| xmlurlpart    | This structure contains the sub-parts of a URL.                                                                                |
| xmlxptrloc    | XPointer location datatype.                                                                                                    |
| xmlxptrlocset | XPointer location set datatype.                                                                                                |
| xmlxslobjtype | Type of XSLT object that may be returned.                                                                                      |
| xmlxslomethod | Type of output produced by the XSLT processor.                                                                                 |
| xmlxvm        | An object of type `xmlxvm` is used for XML document transformation.                                                            |
| xmlxvmcomp    | An object of type `xmlxvmcomp` is used for compiling XSL stylesheets.                                                          |
| xmlxvmflags   | Control flags for the XSLT compiler.                                                                                           |
| xmlxvmobjtype | Type of XSLTVM object.                                                                                                         |
| xpctx         | XPath top-level context.                                                                                                       |
| xpexpr        | XPath expression.                                                                                                              |
| xpobj         | XPath object.                                                                                                                  |
| xsdctx        | XMLSchema validator context.                                                                                                   |
| xslctx        | XSL top-level context.                                                                                                         |
| xvmobj        | XSLVM processor run-time object; contents are private and must not be accessed by users.                                       |

### oracheck

Checkword for validating data structures.

#### Definition

    typedef ub4 oracheck;

### oraerr

Error code: `0` is success, non-`0` is failure.

#### Definition

    typedef ub4 oraerr;

### oraprop_id

The id of property; if `>= 0` it is valid, if `< 0`, it is invalid.

#### Definition

    typedef sb2 oraprop_id;

### oramemctx

Opaque memory context.

#### Definition

    typedef struct oramemctx oramemctx;

### oraprop

Property name.

#### Definition

    typedef struct oraprop {
        oratext    *name_oraprop;
        oraprop_id  id_oraprop;
        oraprop_t   type_oraprop;
        oraprop_v   value_oraprop;
    } oraprop;

### oraprop_t

Property value type.

#### Definition

    typedef enum {
        ORAPROP_TYPE_BOOLEAN,
        ORAPROP_TYPE_SIGNED,
        ORAPROP_TYPE_UNSIGNED,
        ORAPROP_TYPE_POINTER
    } oraprop_t;

### oraprop_v

Value: union of storage for all data types.

#### Definition

    typedef union oraprop_v {
        boolean b_oraprop_v;
        sb4     s_oraprop_v;
        ub4     u_oraprop_v;
        void   *p_oraprop_v;
    } oraprop_v;

### orastream

Opaque stream object.

#### Definition

    typedef struct orastream orastream;

### orastreamhdl

Storage for file handles.

#### Definition

    typedef union orastreamhdl {
        void  *ptr_orastreamhdl;    /* generic pointer stream/file/etc */
        struct {
            sb4 fd_orastreamhdl;    /* file descriptor(s) [FTP needs all 3!] */
            sb4 fd2_orastreamhdl;
            sb4 fd3_orastreamhdl;
        } fds_lpihdl;
    } orastreamhdl;

### xmlcmphow

Constant used for DOM Range comparisons.

#### Definition

    typedef enum {
        XMLDOM_START_TO_START ,
        XMLDOM_START_TO_END   ,
        XMLDOM_END_TO_END     ,
        XMLDOM_END_TO_START
    } xmlcmphow;

### xmlctx

Context shared for all documents in an XML session. Contains encoding information, low-level memory allocation function pointers, error message language or encoding and optional handler function, and so on. Required to load (parse) documents and create DOM, generate SAX, and so on.

#### Definition

    struct xmlctx;
    typedef struct xmlctx xmlctx;

### xmldfoptype

Operation type, represents one or more operations. Used for passing the `diff` to a custom Operation Buildder (OB) in [XmlDiff()](package-XmlDiff-API.md)[XmlDiff()](package-XmlDiff-API.md).

#### Definition

    typedef enum {
      XMLDF_OP_NONE, /* Should not be set to non-zero for XMLDF_NUM_OP macro below */
      XMLDF_OP_UPDATE,
      XMLDF_OP_RENAME,
      XMLDF_OP_DELETE,
      XMLDF_OP_INSERT_BEFORE,
      XMLDF_OP_APPEND
    } xmldfoptype;

### xmldfsrct

Specifies input types for `XmlDiff` operations.

#### Definition

    typedef enum {
       XMLDF_SRCT_NONE ,    /* default is DOM */
       XMLDF_SRCT_DOM,      /* DOM: doc node must be specified */
       XMLDF_SRCT_FILE,     /* file name must be specified */
       XMLDF_SRCT_URL,      /* URL in compiler encoding */
       XMLDF_SRCT_BUFFER,   /* buffer: buffer pointer and length must be specified */
       XMLDF_SRCT_FILEP,    /* FILE */
       XMLDF_SRCT_OSTREAM,  /* orastream: stream pointer must be specified */
       XMLDF_SRCT_DOMNODE   /* DOM node, used with XmlHash() */
    } xmldfsrct;

### xmlerr

Numeric error code returned by many functions. A zero value indicates success; a nonzero value indicates error.

#### Definition

    typedef enum {
       XMLERR_OK              , /* success return */
       XMLERR_NULL_PTR        , /* NULL pointer */
       XMLERR_NO_MEMORY       , /* out of memory */
       XMLERR_HASH_DUP        , /* duplicate entry in hash table */
       XMLERR_INTERNAL        ,  /* internal error */
       XMLERR_BUFFER_OVERFLOW ,  /* name/quoted string too long */
       XMLERR_BAD_CHILD       ,  /* invalid child for parent */
       XMLERR_EOI             ,  /* unexpected EndOfInformation */
       XMLERR_BAD_MEMCB       ,  /* invalid memory callbacks */
       XMLERR_UNICODE_ALIGN   , /* Unicode data misalignment */
       XMLERR_NODE_TYPE       , /* wrong node type */
       XMLERR_UNCLEAN         , /* context is not clean */
       XMLERR_NESTED_STRINGS  , /* internal: nested open str */
       XMLERR_PROP_NOT_FOUND  , /* property not found */
       XMLERR_SAVE_OVERFLOW   , /* save output overflowed */
       XMLERR_NOT_IMP         , /* feature not implemented */
       XMLERR_NLS_MISMATCH    , /* specify lxglo/lxd or neither*/
       XMLERR_NLS_INIT        , /* error at NLS initialization */
       XMLERR_LEH_INIT        , /* error at LEH initialization */
       XMLERR_LML_INIT        , /* error at LML initialization */
       XMLERR_LPU_INIT          /* error at LPU initialization */
    } xmlerr;

### xmlevctx

XML Event context.

#### Definition

    typedef  struct {
       void *ctx_xmlevctx;       /* implementation specific context */
       xmlevdisp disp_xmlevctx;  /* dispatch table */
       ub4 checkword_xmlevctx;   /* checkword for integrity check */
       ub4 flags_xmlevctx;       /* mode; default: expand_entity */
       struct xmlevctx;          /* input xmlevctx; chains the XML Event context */
    } xmlevctx;

### xmlevtype

The event type for parser pull events.

#### Definition

    typedef enum  xmlevtype {
       XML_EVENT_FATAL_ERROR,            /* Fatal Error */
       XML_EVENT_BEFORE_START,           /* Before Start Document */
       XML_EVENT_START_DOCUMENT,         /* Indicates Start Document */
       XML_EVENT_START_DTD,              /* Start DTD */
       XML_EVENT_END_DTD,                /* End DTD */
       XML_EVENT_NOTATION_DECLARATION,   /* Notation Decl */
       XML_EVENT_PE_DECLARATION,         /* PE Decl */
       XML_EVENT_UE_DECLARATION,         /* US Decl */
       XML_EVENT_ELEMENT_DECLARATION,    /* Element Decl */
       XML_EVENT_ATTLIST_DECLARATION,    /* Attribute Decl */
       XML_EVENT_START_ELEMENT,          /* Start Element */
       XML_EVENT_END_ELEMENT,            /* End Element */
       XML_EVENT_CHARACTERS,             /* Characters (text) */
       XML_EVENT_CHARACTERS_CONT,        /* Characters Continued */
       XML_EVENT_PI,                     /* Processing Instruction */
       XML_EVENT_PI_CONT,                /* Processing Instruction Continued */
       XML_EVENT_COMMENT,                /* Comment */
       XML_EVENT_COMMENT_CONT,           /* Comment Continued */
       XML_EVENT_SPACE,                  /* White Space */
       XML_EVENT_SPACE_CONT,             /* White Space Continued */
       XML_EVENT_ENTITY_REFERENCE,       /* Entity Reference */
       XML_EVENT_CDATA,                  /* CDATA */
       XML_EVENT_CDATA_CONT,             /* CDATA continued */
       XML_EVENT_START_ENTITY,           /* Start Entity */
       XML_EVENT_END_ENTITY,             /* End Entity */
       XML_EVENT_END_DOCUMENT,           /* End Document */
       XML_EVENT_ERROR                   /* Error */
    }xmlevtype;

### xmlhasht

The hash value of an XML tree or sub-tree; also known as a digest.

If the hash values for two XML trees are equal, the trees are considered equal, to a very high probability; uses the MD5 algorithm.

#### Definition

    struct xmlhasht {
       ub4  l_xmlhasht;   /* lenght of digest in bytes */
       ub1  d_xmlhasht[XMLDF_DIGEST_MAX];   /* the digest */
    };
    typedef struct xmlhasht xmlhasht;

### xmlistream

Generic user-defined input stream. The three function pointers are required (but may be stubs). The context pointer is entirely user-defined; point it to whatever state information is required to manage the stream; it will be passed as first argument to the user functions.

#### Definition

    typedef struct xmlistream {
       XML_STREAM_OPEN_F(
          (*open_xmlistream),
          xctx,
          sctx,
          path,
          parts,
          length);
       XML_STREAM_READ_F(
          (*read_xmlistream),
          xctx,
          sctx,
          path,
          dest,
          size,
          nraw, eoi);
       XML_STREAM_CLOSE_F(
          (*close_xmlistream),
          xctx,
          sctx);
       void *ctx_xmlistream;                         /* user's stream context */
    } xmlistream;

### xmliter

Control structure for DOM 2 `NodeIterator` and `TreeWalker`.

#### Definition

    struct xmliter {
       xmlnode *root_xmliter;   /* root node of the iteration space */
       xmlnode *cur_xmliter;    /* current position iterator ref node */
       ub4      show_xmliter;   /* node filter mask */
       void    *filt_xmliter;   /* node filter function */
       boolean  attach_xmliter; /* is iterator valid? */
       boolean  expan_xmliter;  /* are external entities expanded? */
       boolean  before_xmliter; /* iter position before ref node? */
    };
    typedef struct xmliter xmliter;
    typedef struct xmliter xmlwalk;

### xmlnodetype

The numeric type code of a node. `0` means invalid, 1-13 are the standard numberings from DOM 1.0, and higher numbers are for internal use only.

#### Definition

    typedef enum {
        XMLDOM_NONE     , /* bogus node */
        XMLDOM_ELEM     , /* element */
        XMLDOM_ATTR     , /* attribute */
        XMLDOM_TEXT     , /* char data not escaped by CDATA */
        XMLDOM_CDATA    , /* char data escaped by CDATA */
        XMLDOM_ENTREF   , /* entity reference */
        XMLDOM_ENTITY   , /* entity */
        XMLDOM_PI       , /* <?processing instructions?> */
        XMLDOM_COMMENT  , /* <!-- Comments --> */
        XMLDOM_DOC      , /* Document */
        XMLDOM_DTD      , /* DTD */
        XMLDOM_FRAG     , /* Document fragment */
        XMLDOM_NOTATION , /* notation */

        /* Oracle extensions from here on */
        XMLDOM_ELEMDECL , /* DTD element declaration */
        XMLDOM_ATTRDECL , /* DTD attribute declaration */

        /* Content Particles (nodes in element's Content Model) */
        XMLDOM_CPELEM   , /* element */
        XMLDOM_CPCHOICE , /* choice (a|b) */
        XMLDOM_CPSEQ    , /* sequence (a,b) */
        XMLDOM_CPPCDATA , /* #PCDATA */
        XMLDOM_CPSTAR   , /* '*' (zero or more) */
        XMLDOM_CPPLUS   , /* '+' (one or more) */
        XMLDOM_CPOPT    , /* '?' (optional) */
        XMLDOM_CPEND      /* end marker */
    } xmlnodetype;

### xmlostream

Generic user-defined output stream. The three function pointers are required (but may be stubs). The context pointer is entirely user-defined; point it to whatever state information is required to manage the stream; it will be passed as first argument to the user functions.

#### Definition

    typedef struct xmlostream {
       XML_STREAM_OPEN_F(
          (*open_xmlostream),
          xctx,
          sctx,
          path,
          parts,
          length);
       XML_STREAM_WRITE_F(
          (*write_xmlostream),
          xctx,
          sctx,
          path,
          src,
          size);
       XML_STREAM_CLOSE_F(
          (*close_xmlostream),
          xctx,
          sctx);
       void *ctx_xmlostream;        /* user's stream context */
    } xmlostream;

### xmlpoint

XPointer point location.

#### Definition

    typedef struct xmlpoint xmlpoint;

### xmlrange

Control structure for DOM 2 Range.

#### Definition

    typedef struct xmlrange {
     xmlnode *startnode_xmlrange;  /* start point container */
     ub4      startofst_xmlrange;  /* start point index */
     xmlnode *endnode_xmlrange;    /* end point container */
     ub4      endofst_xmlrange;    /* end point index */
     xmlnode *doc_xmlrange;        /* document node */
     xmlnode *root_xmlrange;       /* root node of the range */
     boolean  collapsed_xmlrange;  /* is range collapsed? */
     boolean  detached_xmlrange;   /* range invalid, invalidated?*/
    } xmlrange;

### xmlsoapbind

Binding for SOAP connections. SOAP does not dictate the binding (transport) used for conveying messages; however the HTTP protocol is well-defined and currently the only choice.

#### Definition

    typedef enum xmlsoapbind {
       XMLSOAP_BIND_NONE ,  /* none */
       XMLSOAP_BIND_HTTP    /* HTTP */ } xmlsoapbind;

### xmlsoapcon

SOAP connection object. Each distinct connection requires an instance of this type, which contains binding and endpoint information.

#### Definition

    typedef struct xmlsoapcon xmlsoapcon;

### xmlsoapctx

Context for SOAP operations. Only a single context is needed and it can be shared by several SOAP messages.

#### Definition

    typedef struct xmlsoapctx xmlsoapctx;

### xmlsoaprole

Role for a SOAP node.

#### Definition

    typedef enum xmlsoaprole {
        XMLSOAP_ROLE_UNSET,   /* not specified */
        XMLSOAP_ROLE_NONE,    /* "none" */
        XMLSOAP_ROLE_NEXT,    /* "next" */
        XMLSOAP_ROLE_ULT,     /* "ultimateReceiver" */
        XMLSOAP_ROLE_OTHER    /* other - user defined */
    } xmlsoaprole;

### xmlshowbits

Bit flags used to select which nodes types to show.

#### Definition

    typedef ub4 xmlshowbits;
    #define XMLDOM_SHOW_ALL        ~(ub4)0
    #define XMLDOM_SHOW_BIT(ntype) ((ub4)1 << (ntype))
    #define XMLDOM_SHOW_ELEM       XMLDOM_SHOW_BIT(XMLDOM_ELEM)
    #define XMLDOM_SHOW_ATTR       XMLDOM_SHOW_BIT(XMLDOM_ATTR)
    #define XMLDOM_SHOW_TEXT       XMLDOM_SHOW_BIT(XMLDOM_TEXT)
    #define XMLDOM_SHOW_CDATA      XMLDOM_SHOW_BIT(XMLDOM_CDATA)
    #define XMLDOM_SHOW_ENTREF     XMLDOM_SHOW_BIT(XMLDOM_ENTREF)
    #define XMLDOM_SHOW_ENTITY     XMLDOM_SHOW_BIT(XMLDOM_ENTITY)
    #define XMLDOM_SHOW_PI         XMLDOM_SHOW_BIT(XMLDOM_PI)
    #define XMLDOM_SHOW_COMMENT    XMLDOM_SHOW_BIT(XMLDOM_COMMENT)
    #define XMLDOM_SHOW_DOC        XMLDOM_SHOW_BIT(XMLDOM_DOC)
    #define XMLDOM_SHOW_DTD        XMLDOM_SHOW_BIT(XMLDOM_DTD)
    #define XMLDOM_SHOW_FRAG       XMLDOM_SHOW_BIT(XMLDOM_FRAG)
    #define XMLDOM_SHOW_NOTATION   XMLDOM_SHOW_BIT(XMLDOM_NOTATION)
    #define XMLDOM_SHOW_DOC_TYPE   XMLDOM_SHOW_BIT(XMLDOM_DOC_TYPE)

### xmlurlacc

This is an enumeration of the known access methods for retrieving data from a URL. Open/read/close functions may be plugged in to override the default behavior.

#### Definition

    typedef enum {
        XML_ACCESS_NONE    , /* not specified */
        XML_ACCESS_UNKNOWN , /* specified but unknown */
        XML_ACCESS_FILE    , /* filesystem access */
        XML_ACCESS_HTTP    , /* HTTP */
        XML_ACCESS_FTP     , /* FTP */
        XML_ACCESS_GOPHER  , /* Gopher */
        XML_ACCESS_ORADB   , /* Oracle DB */
        XML_ACCESS_STREAM    /* user-defined stream */
    } xmlurlacc;

### xmlurlhdl

This union contains the handle(s) needed to access URL data, be it a stream or stdio pointer, file descriptor(s), and so on.

#### Definition

    typedef union xmlurlhdl {
        void  *ptr_xmlurlhdl;  /* generic stream/file/... handle */
        struct {
            sb4 fd1_xmlurlhdl; /* file descriptor(s) [FTP needs all 3!] */
            sb4 fd2_xmlurlhdl;
            sb4 fd3_xmlurlhdl;
        } fds_lpihdl;
    } xmlurlhdl;

### xmlurlpart

This structure contains the sub-parts of a URL. The original URL is parsed and the pieces copies (`NULL`-terminated) to a working buffer, then this structure is filled in to point to the parts. Given URL `http://user:pwd@baz.com:8080/pub/baz.html;quux=1?huh#fraggy`, the example component part from this URL will be shown.

#### Definition

    typedef struct xmlurlpart {
     xmlurlacc access_xmlurlpart;   /* access method code, XMLACCESS_HTTP */
     oratext   *accbuf_xmlurlpart;  /* access method name: "http" */
     oratext   *host_xmlurlpart;    /* hostname:         "baz.com" */
     oratext   *dir_xmlurlpart;     /* directory:        "pub" */
     oratext   *file_xmlurlpart;    /* filename:         "baz.html" */
     oratext   *uid_xmlurlpart;     /* userid/username:  "user" */
     oratext   *passwd_xmlurlpart;  /* password:         "pwd" */
     oratext   *port_xmlurlpart;    /* port (as string): "8080" */
     oratext   *frag_xmlurlpart;    /* fragment:         "fraggy" */
     oratext   *query_xmlurlpart;   /* query:            "huh" */
     oratext   *param_xmlurlpart;   /* parameter:        "quux=1" */
     ub2        portnum_xmlurlpart; /* port (as number): 8080 */
     ub1        abs_xmlurlpart;     /* absolute path?     TRUE */
    } xmlurlpart;

### xmlxptrloc

XPointer location data type.

#### Definition

    typedef struct xmlxptrloc xmlxptrloc;

### xmlxptrlocset

XPointer location set data type.

#### Definition

    typedef struct xmlxptrlocset xmlxptrlocset;

### xmlxslobjtype

Type of XSLT object that may be returned.

#### Definition

    typedef enum xmlxslobjtype {
        XMLXSL_TYPE_UNKNOWN , /* Not a defined type */
        XMLXSL_TYPE_NDSET   , /* Node-set */
        XMLXSL_TYPE_BOOL    , /* Boolean value */
        XMLXSL_TYPE_NUM     , /* Numeric value (double) */
        XMLXSL_TYPE_STR     , /* String */
        XMLXSL_TYPE_FRAG      /* Document Fragment */
    } xmlxslobjtype;

### xmlxslomethod

Type of output to be produced by the XSLT processor.

#### Definition

    typedef enum xmlxslomethod {
     XMLXSL_OUTPUT_UNKNOWN , /* Not defined */
     XMLXSL_OUTPUT_XML     , /* Produce a Document Fragment */
     XMLXSL_OUTPUT_STREAM  , /* Stream out formatted result */
     XMLXSL_OUTPUT_HTML      /* Stream out HTML formatted result */
    } xmlxslomethod;

### xmlxvm

An object of type `xmlxvm` is used for XML documents transformation. The contents of `xmlxvm` are private and must not be accessed by users.

#### Definition

    struct xmlxvm;
    typedef struct xmlxvm xmlxvm;

### xmlxvmcomp

An object of type `xmlxvmcomp` is used for compiling XSL stylesheets. The contents of `xmlxvmcomp` are private and must not be accessed by users.

#### Definition

    struct xmlxvmcomp;
    typedef struct xmlxvmcomp xmlxvmcomp;

### xmlxvmflags

Control flags for the XSLT compiler.

- `XMLXVM_DEBUG` forces compiler to insert debug information into the bytecode.

- `XMLXVM_STRIPSPACE` forces the same behavior as `xsl:strip-space elements="*"`

#### Definition

    typedef ub4 xmlxvmflag;
    #define XMLXVM_NOFLAG
    #define XMLXVM_DEBUG      /* insert debug info into bytecode */
    #define XMLXVM_STRIPSPACE /* same as xsl:strip-space elements="*" */

### xmlxvmobjtype

Type of XSLTVM object.

#### Definition

    typedef enum xmlxvmobjtype {
        XMLXVM_TYPE_UNKNOWN ,
        XMLXVM_TYPE_NDSET   ,
        XMLXVM_TYPE_BOOL    ,
        XMLXVM_TYPE_NUM     ,
        XMLXVM_TYPE_STR     ,
        XMLXVM_TYPE_FRAG
    } xmlxvmobjtype;

### xpctx

XPath top-level context.

#### Definition

    struct xpctx;
    typedef struct xpctx xpctx;

### xpexpr

XPath expression.

#### Definition

    struct xpexpr;
    typedef struct xpexpr xpexpr;

### xpobj

Xpath object.

#### Definition

    struct xpobj;typedef struct xpobj xpobj;

### xsdctx

XML Schema validator context, created by `XmlSchemaCreate` and passed to most Schema functions.

#### Definition

    # define XSDCTX_DEFINED
    struct xsdctx; typedef struct xsdctx xsdctx;

### xslctx

XSL top-level context.

#### Definition

    struct xslctx;
    typedef struct xslctx xslctx;

### xvmobj

XSLVM processor run-time object; content is private and must not be accessed by users.

#### Definition

    struct xvmobj;
    typedef struct xvmobj xvmobj;
