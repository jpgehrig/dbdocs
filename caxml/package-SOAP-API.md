SOAP is a lightweight protocol for exchange of information in a decentralized, distributed environment. It is an XML based protocol that consists of three parts: an envelope that defines a framework for describing what is in a message and how to process it, a set of encoding rules for expressing instances of application-defined datatypes, and a convention for representing remote procedure calls and responses.

Attachments are not allowed in Soap 1.1. In Soap 1.2, body may not have other elements if Fault is present.

The structure of a SOAP message is illustrated in the following section of code.

    [SOAP message (XML document)
       [SOAP envelope
          [SOAP header?
                element*
          ]
          [SOAP body
               (element* | Fault)?
          ]
       ]
    ]

The following table summarizes the methods available through the SOAP package for XML C APIs.

Table 9-1 Summary of SOAP Methods for XML C Implementation

| Function                   | Summary                                                 |
|:---------------------------|:--------------------------------------------------------|
| XmlSoapAddBodyElement()    | Adds an element to a SOAP message body.                 |
| XmlSoapAddFaultReason()    | Adds additional Reason to Fault.                        |
| XmlSoapAddFaultSubDetail() | Adds additional child to Fault Detail.                  |
| XmlSoapAddHeaderElement()  | Adds an element to a SOAP header.                       |
| XmlSoapCall()              | Sends a SOAP message then waits for a reply.            |
| XmlSoapCreateConnection()  | Creates a SOAP connection object.                       |
| XmlSoapCreateCtx()         | Creates and returns a SOAP context.                     |
| XmlSoapCreateMsg()         | Creates and returns an empty SOAP message.              |
| XmlSoapDestroyConnection() | Destroys a SOAP connection object.                      |
| XmlSoapDestroyCtx()        | Destroys a SOAP context.                                |
| XmlSoapDestroyMsg()        | Destroys a SOAP message created with XmlSoapCreateMsg.  |
| XmlSoapError()             | Gets a human readable error code.                       |
| XmlSoapGetBody()           | Return a SOAP message's envelope body.                  |
| XmlSoapGetBodyElement()    | Gets an element from a SOAP body.                       |
| XmlSoapGetEnvelope()       | Returns a SOAP part's envelope.                         |
| XmlSoapGetFault()          | Returns Fault code, reason, and details.                |
| XmlSoapGetHeader()         | Returns a SOAP message's envelope header.               |
| XmlSoapGetHeaderElement()  | Gets an element from a SOAP header.                     |
| XmlSoapGetMustUnderstand() | Gets mustUnderstand attribute from SOAP header element. |
| XmlSoapGetReasonLang()     | Gets the language of a reason with the specified index. |
| XmlSoapGetReasonNum()      | Determines the number of reasons in Fault element.      |
| XmlSoapGetRelay()          | Gets Relay attribute from SOAP header element.          |
| XmlSoapGetRole()           | Gets role from SOAP header element.                     |
| XmlSoapHasFault()          | Determines if SOAP message contains Fault object.       |
| XmlSoapSetFault()          | Sets Fault in SOAP message.                             |
| XmlSoapSetMustUnderstand() | Sets mustUnderstand attribute for SOAP header element.  |
| XmlSoapSetRelay()          | Sets Relay attribute for a SOAP header element.         |
| XmlSoapSetRole()           | Sets role for SOAP header element.                      |

### XmlSoapAddBodyElement()

Adds an element to a SOAP message body. Sets the numeric error code.

#### Syntax

    xmlelemnode *XmlSoapAddBodyElement(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext *qname,
       oratext *uri,
       xmlerr *xerr);

| Parameter | In/Out   | Description                     |
|:----------|:---------|:--------------------------------|
| `ctx`     | `IN`     | SOAP context                    |
| `msg`     | `IN/OUT` | SOAP message                    |
| `qname`   | `IN`     | QName of element to add         |
| `uri`     | `IN`     | Namespace URI of element to add |
| `xerr`    | `IN/OUT` | Error code                      |

#### Returns

`(xmlelemnode *)` created element

**See Also:**

XmlSoapAddHeaderElement()

### XmlSoapAddFaultReason()

Add additional Reason to Fault. The same reason text may be provided in different languages. When the fault is created, the primary language/reason is added at that time; use this function to add additional translations of the reason.

#### Syntax

    xmlerr XmlSoapAddFaultReason(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       ratext *reason,
        oratext *lang);

| Parameter | In/Out   | Description                 |
|:----------|:---------|:----------------------------|
| `ctx`     | `IN`     | SOAP context                |
| `msg`     | `IN/OUT` | SOAP message                |
| `reason`  | `IN`     | Human-readable fault Reason |
| `lang`    | `IN`     | Language of reason          |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapSetFault()

### XmlSoapAddFaultSubDetail()

Adds an additional child to Fault Detail. `XmlSoapSetFault` allows for creation of a Deatail element with only one child. Extra children could be added with this function.

#### Syntax

    xmlerr XmlSoapAddFaultSubDetail(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       xmlelemnode *sub);

| Parameter | In/Out   | Description    |
|:----------|:---------|:---------------|
| `ctx`     | `IN`     | SOAP context   |
| `msg`     | `IN/OUT` | SOAP message   |
| `sub`     | `IN`     | subdetail tree |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapGetReasonLang()

### XmlSoapAddHeaderElement()

Adds an element to a SOAP header.

#### Syntax

    xmlelemnode *XmlSoapAddHeaderElement(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext *qname,
       oratext *uri,
       xmlerr *xerr);

| Parameter | In/Out   | Description                     |
|:----------|:---------|:--------------------------------|
| `ctx`     | `IN`     | SOAP context                    |
| `msg`     | `IN/OUT` | SOAP message                    |
| `qname`   | `IN`     | QName of element to add         |
| `uri`     | `IN`     | Namespace URI of element to add |
| `xerr`    | `IN/OUT` | error code                      |

#### Returns

(xmlelemnode \*) created element

**See Also:**

XmlSoapAddBodyElement(), XmlSoapGetHeaderElement()

### XmlSoapCall()

Send a SOAP message over a connection and wait for the response; the message reply (an XML document) is parsed and returned as a SOAP message (equivalent to a DOM).

The message buffer is first used to serialize the outgoing message; if it's too small (overflow occurs), xerr gets XMLERR_SAVE_OVERFLOW and `NULL` is returned. The same buffer is then re-used to receive the replied SOAP message.

Opening the connection object is expected to cause an active SOAP handler to appear on the end-point; how this happens is up to the user. For HTTP, the URL should invoke a cgi-bin, or detect the application/soap+xml content-type.

#### Syntax

    xmldocnode *XmlSoapCall(
       xmlsoapctx *ctx,
       xmlsoapcon *con,
       xmldocnode *msg,
       xmlerr *xerr);

| Parameter | In/Out | Description             |
|:----------|:-------|:------------------------|
| `ctx`     | `IN`   | SOAP context            |
| `con`     | `IN`   | SOAP connection object  |
| `msg`     | `IN`   | SOAP message to send    |
| `xerr`    | `IN`   | numeric code of failure |

#### Returns

`(xmldocnode *)` returned message, or `NULL` on failure with xerr set

**See Also:**

XmlSoapCreateMsg(), XmlSoapCreateConnection(), XmlSoapDestroyConnection()

### XmlSoapCreateConnection()

Create a SOAP connection object, specifying the binding (transport) and endpoint. The binding is an enum of type xmlsoapbind, and the endpoint depends on the binding.

Currently only HTTP binding is supported, and the endpoint is a URL. That URL should be active, i.e. a cgi-bin script or some mechanism to trigger SOAP message processing based on the Content-type of the incoming message ("application/soap+xml").

To control the HTTP access method (GET or POST), use the web-method property named `XMLSOAP_PROP_WEB_METHOD` which can have possible values `XMLSOAP_WEB_METHOD_GET` and `XMLSOAP_WEB_METHOD_POST`.

(conbuf, consiz) is the connection buffer used with LPU; for sending, it contains only the HTTP header, but on reception it holds the entire reply, including HTTP header and the full SOAP body. If no buffer is provided, one will be allocated for you. If size if zero, the default size (64K) will be used.

(msgbuf, msgsiz) is the message buffer used to form SOAP messages for sending. It needs to be large enough to contain the largest message which will be sent. If no buffer is specified, one will be allocated for you. If the size is zero, the default size (64K) will be used.

Two buffers are needed for sending since the SOAP message needs to be formed first in order to determine it's size; then, the HTTP header can be formed, since the Content-Length is now known.

#### Syntax

    xmlsoapcon *XmlSoapCreateConnection(
       xmlsoapctx *ctx,
       xmlerr *xerr,
       xmlsoapbind bind,
       void *endp,
       oratext *conbuf,
       ubig_ora consiz,
       oratext *msgbuf,
       ubig_ora msgsiz,
       ...);

| Parameter | In/Out   | Description                                         |
|:----------|:---------|:----------------------------------------------------|
| `ctx`     | `IN`     | SOAP context                                        |
| `xerr`    | `OUT`    | numeric error code on failure                       |
| `bind`    | `IN`     | connection binding                                  |
| `endp`    | `IN`     | connection endpoint                                 |
| `conbuf`  | `IN/OUT` | connection buffer (or `NULL` to have one allocated) |
| `consiz`  | `IN`     | size of connection buffer (or 0 for default size)   |
| `msgbuf`  | `IN/OUT` | message buffer (or `NULL` to have one allocated)    |
| `msgsiz`  | `IN`     | size of message buffer (or 0 for default size)      |
| `...`     | `IN`     | additional HTTP headers to set, followed by `NULL`  |

#### Returns

`(xmlsoapcon *)` connect object, or `NULL` on error with xerr set

**See Also:**

XmlSoapDestroyConnection(), XmlSoapCall()

### XmlSoapCreateCtx()

Creates and returns a SOAP context. This context must be passed to all XmlSoap APIs. Note the name provided should be unique and is used to identify the context when debugging. Options are specified as (name, value) pairs, ending with a `NULL`, same as for XmlCreate. If no options are desired, the `NULL` is still needed. Options are: `debug_level` (enables SOAP debug output to `stderr`), numeric level (the higher the level, the more detailed extensive the output), `0` for no debug (this is the default setting).

#### Syntax

    xmlsoapctx *XmlSoapCreateCtx(
       xmlctx *xctx,
       xmlerr *xerr,
       oratext *name,
       ...);

| Parameter | In/Out | Description                                         |
|:----------|:-------|:----------------------------------------------------|
| `xctx`    | `IN`   | XML context                                         |
| `xerr`    | `OUT`  | error return code on failure                        |
| `name`    | `IN`   | name of context; used for debugging                 |
| `...`     | `IN`   | options, as (name, value) pairs, followed by `NULL` |

#### Returns

`(xmlsoapctx *)` SOAP context, or `NULL` on failure (w/xerr set)

**See Also:**

XmlSoapDestroyCtx()

### XmlSoapCreateMsg()

Creates and returns an empty SOAP message. The SOAP message will consist of an Envelope. The Envelope contains an empty Header and Body. A SOAP message is an XML document represented by a DOM, and is no different from any other XML document. All DOM operations are valid on the document, but be sure not to harm the overall structure. Changes should be restricted to creating and modifying elements inside the Header and Body.

#### Syntax

    xmldocnode *XmlSoapCreateMsg(
       xmlsoapctx *ctx,
       xmlerr *xerr);

| Parameter | In/Out | Description                  |
|:----------|:-------|:-----------------------------|
| `ctx`     | `IN`   | SOAP context                 |
| `xerr`    | `OUT`  | error retrun code on failure |

#### Returns

`(xmldocnode *)` SOAP message, or `NULL` on failure (w/xerr set)

**See Also:**

XmlSoapDestroyMsg()

### XmlSoapDestroyConnection()

Destroys a SOAP connection object made with XmlSoapCreateConnection and frees all allocated resources.

#### Syntax

    xmlerr XmlSoapDestroyConnection(
       xmlsoapctx *ctx,
       xmlsoapcon *con);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `ctx`     | `IN`   | SOAP context    |
| `con`     | `IN`   | SOAP connection |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapCreateConnection(), XmlSoapCall()

### XmlSoapDestroyCtx()

Destroys a SOAP context created with XmlSoapCreateCtx. All memory allocated will be freed, and all connections closed.

#### Syntax

    xmlerr XmlSoapDestroyCtx(
       xmlsoapctx *ctx);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `ctx`     | `IN`   | SOAP context |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSoapCreateCtx()

### XmlSoapDestroyMsg()

Destroys a SOAP message created with XmlSoapCreateMsg; this is the same as calling XmlFreeDocument.

#### Syntax

    xmlerr XmlSoapDestroyMsg(
       xmlsoapctx *ctx,
       xmldocnode *msg);

| Parameter | In/Out | Description     |
|:----------|:-------|:----------------|
| `ctx`     | `IN`   | SOAP connection |
| `msg`     | `IN`   | SOAP message    |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSoapCreateMsg()

### XmlSoapError()

Retrives human readable representation of the error code. Optionally, retrieves the information about the error code of the underlying layer.

#### Syntax

    oratext *XmlSoapError(
       xmlsoapctx *ctx,
       xmlsoapcon *con,
       xmlerr err,
       uword *suberr,
       oratext **submsg);

| Parameter | In/Out | Description                                                       |
|:----------|:-------|:------------------------------------------------------------------|
| `ctx`     | `IN`   | SOAP context                                                      |
| `con`     | `IN`   | Connection about which additional info is requested               |
| `err`     | `IN`   | Error code for which human readable information will be returned. |
| `suberr`  | `OUT`  | Error code from `con`                                             |
| `submsg`  | `OUT`  | Human readable information about `con` error                      |

#### Returns

`(oratext *)` error code

### XmlSoapGetBody()

Returns a SOAP message's envelope body.

#### Syntax

    xmlelemnode *XmlSoapGetBody(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       xmlerr *xerr);

| Parameter | In/Out   | Description  |
|:----------|:---------|:-------------|
| `ctx`     | `IN`     | SOAP context |
| `msg`     | `IN`     | SOAP message |
| `xmlerr`  | `IN/OUT` | error code   |

#### Returns

`(xmlelemnode *)` SOAP Body

**See Also:**

XmlSoapGetHeader()

### XmlSoapGetBodyElement()

Gets an element from a SOAP body.

#### Syntax

    xmlelemnode *XmlSoapGetBodyElement(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext *uri,
        oratext *local,
        xmlerr *xerr);

| Parameter | In/Out   | Description                     |
|:----------|:---------|:--------------------------------|
| `ctx`     | `IN`     | SOAP context                    |
| `msg`     | `IN`     | SOAP message                    |
| `uri`     | `IN`     | Namespace URI of element to get |
| `local`   | `IN`     | Local name of element to get    |
| `xerr`    | `IN/OUT` | error code                      |

#### Returns

`(xmlelemnode *)` named element, or `NULL` on error

**See Also:**

XmlSoapAddBodyElement()

### XmlSoapGetEnvelope()

Returns a SOAP part's envelope

#### Syntax

    xmlelemnode *XmlSoapGetEnvelope(
       mlsoapctx *ctx,
       xmldocnode *msg,
       xmlerr *xerr);

| Parameter | In/Out   | Description  |
|:----------|:---------|:-------------|
| `ctx`     | `IN`     | SOAP context |
| `msg`     | `IN`     | SOAP message |
| `xerr`    | `IN/OUT` | error code   |

#### Returns

`(xmlelemnode *)` SOAP envelope

### XmlSoapGetFault()

Returns Fault code, reason, and details. Fetches the Fault information and returns through user variables. `NULL` may be supplied for any part which is not needed. For lang, if the pointed-to variable is `NULL`, it will be set to the default language (that of the first reason).

#### Syntax

    xmlerr XmlSoapGetFault(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext **code,
       oratext **reason,
       oratext **lang,
       oratext **node,
       oratext **role,
       xmlelemnode **detail);

| Parameter | In/Out   | Description                                                  |
|:----------|:---------|:-------------------------------------------------------------|
| `ctx`     | `IN`     | SOAP context                                                 |
| `msg`     | `IN/OUT` | SOAP message                                                 |
| `code`    | `OUT`    | Code (1.2), faultcode (1.1)                                  |
| `reason`  | `OUT`    | Human-readable fault Reason (1.2), faultreason (1.1)         |
| `lang`    | `IN`     | Desired language for reason (1.2), not used ( `NULL` in 1.1) |
| `node`    | `OUT`    | Fault node                                                   |
| `role`    | `OUT`    | Role: next, none, or ulitmate receiver. Not used in 1.1      |
| `detail`  | `OUT`    | User-defined details                                         |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSoapSetFault()

### XmlSoapGetHeader()

Returns a SOAP message's envelope header.

#### Syntax

    xmlelemnode *XmlSoapGetHeader(
       xmlsoapctx *ctx,
      xmldocnode *msg,
       xmlerr *xerr);

| Parameter | In/Out   | Description  |
|:----------|:---------|:-------------|
| `ctx`     | `IN`     | SOAP context |
| `msg`     | `IN`     | SOAP message |
| `xerr`    | `IN/OUT` | error code   |

#### Returns

`(xmlelemnode *)` SOAP header

**See Also:**

XmlSoapGetBody()

### XmlSoapGetHeaderElement()

Gets an element from a SOAP header. Sets a numeric error code.

#### Syntax

    xmlelemnode *XmlSoapGetHeaderElement(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext *uri,
       oratext *local,
       xmlerr *xerr);

| Parameter | In/Out   | Description                     |
|:----------|:---------|:--------------------------------|
| `ctx`     | `IN`     | SOAP context                    |
| `msg`     | `IN`     | SOAP message                    |
| `uri`     | `IN`     | Namespace URI of element to get |
| `local`   | `IN`     | Local name of element to get    |
| `xerr`    | `IN/OUT` | Error code                      |

#### Returns

`(xmlelemnode *)` named element, or `NULL` on error

**See Also:**

XmlSoapAddHeaderElement(), XmlSoapGetBodyElement()

### XmlSoapGetMustUnderstand()

Gets `mustUnderstand` attribute from SOAP header element. The absence of this attribute is not an error and treated as value FALSE. To indicate the absence of an attribute, the error code XMLERR_SOAP_NO_MUST_UNDERSTAND is returned in this case, XMLERR_OK (0) is returned if the attribute is present. Other appropriate error codes might be returned. User supplied `mustUnderstand` value is set accordingly.

#### Syntax

    xmlerr XmlSoapGetMustUnderstand(
       xmlsoapctx *ctx,
       xmlelemnode *elem,
       boolean *mustUnderstand);

| Parameter        | In/Out | Description                         |
|:-----------------|:-------|:------------------------------------|
| `ctx`            | `IN`   | SOAP context                        |
| `elem`           | `IN`   | SOAP header element                 |
| `mustUnderstand` | `OUT`  | `mustUnderstand` value, TRUE\|FALSE |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSoapAddBodyElement(), XmlSoapSetMustUnderstand()

### XmlSoapGetReasonLang()

Gets the language of a reason with a particular index.

#### Syntax

    xmlerr XmlSoapGetReasonLang(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       ub4 index,
       oratext **lang);

| Parameter | In/Out | Description           |
|:----------|:-------|:----------------------|
| `ctx`     | `IN`   | SOAP context          |
| `msg`     | `IN`   | SOAP message          |
| `indx`    | `IN`   | Index of fault reason |
| `lang`    | `IN`   | Reason language       |

#### Returns

`(xmlerr)` numeric error code, XMLERR_OK \[0\] on success

**See Also:**

XmlSoapGetFault(), XmlSoapHasFault(), XmlSoapGetReasonNum()

### XmlSoapGetReasonNum()

Determines the number of reasons in Fault element. Returns 0 if Fault is not present.

#### Syntax

    ub4 XmlSoapGetReasonNum(
       xmlsoapctx *ctx,
       xmldocnode *msg);

| Parameter | In/Out | Description  |
|:----------|:-------|:-------------|
| `ctx`     | `IN`   | SOAP context |
| `msg`     | `IN`   | SOAP message |

#### Returns

`(ub4 *)` \#num reasons

**See Also:**

XmlSoapGetFault(), XmlSoapHasFault()

### XmlSoapGetRelay()

Gets Relay attribute from SOAP header element.

#### Syntax

    xmlerr XmlSoapGetRelay(
       xmlsoapctx *ctx,
       xmlelemnode *elem,
       boolean *Relay);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `ctx`     | `IN`   | SOAP context        |
| `elem`    | `IN`   | SOAP header element |
| `Relay`   | `OUT`  | Relay value         |

#### Returns

`xmlerr` numeric error code, `XMLERR_OK` on success

**See Also:**

XmlSoapAddBodyElement(), XmlSoapSetRelay()

### XmlSoapGetRole()

Gets role from SOAP header element. If the element has no role, `XMLERR_SOAP_NO_ROLE` is returned, otherwise `XMLERR_OK (0)` is returned and the user's role is set accordingly. if the element has no role, then according to the standard, the user's role is set to `XMLSOAP_ROLE_ULT`.

#### Syntax

    xmlerr XmlSoapGetRole(
       xmlsoapctx *ctx,
       xmlelemnode *elem,
       xmlsoaprole *role);

| Parameter | In/Out | Description         |
|:----------|:-------|:--------------------|
| `ctx`     | `IN`   | SOAP context        |
| `elem`    | `IN`   | SOAP header element |
| `role`    | `OUT`  | Role value          |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapSetMustUnderstand(), XmlSoapSetRole()

### XmlSoapHasFault()

Determines if SOAP message contains Fault object.

#### Syntax

    boolean XmlSoapHasFault(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       xmlerr *xerr);

| Parameter | In/Out   | Description  |
|:----------|:---------|:-------------|
| `ctx`     | `IN`     | SOAP context |
| `msg`     | `IN`     | SOAP message |
| `xerr`    | `IN/OUT` | Error code   |

#### Returns

`(boolean)` `TRUE` if there's a Fault, `FALSE` if not

**See Also:**

XmlSoapGetFault()

### XmlSoapSetFault()

Sets Fault in SOAP message.

- In version 1.2, only one Fault is allowed for each message, and it must be the only child of the Body. If the Body has children, they are first removed and freed. The Fault is then added with children code - "env:Code" (required), reason - "env:Reason" (required), node - "env:Node" (optional), role - "env:role"(optional), and detail - "env:Detail" (optional). The primary-language reason should be added first; calls to XmlSoapGetFault which pass a `NULL` language will pick this reason. Detail is the user-defined subtree to be spliced into the Fault.

- In version 1.1, only one Fault is allowed per message. If the Body already has Fault, it is first removed and freed. The Fault is then added with children code - "faultcode" (required), reason - "faultstring" (required), node - "faultactor" (optional), and detail - "detail" (optional). Detail is the user-defined subtree to be spliced into the Fault. role and lang are not used in ver 1.1

#### Syntax

    xmlerr XmlSoapSetFault(
       xmlsoapctx *ctx,
       xmldocnode *msg,
       oratext *node,
       oratext *code,
       oratext *reason,
       oratext *lang,
       oratext *role,
       xmlelemnode *detail);

| Parameter | In/Out   | Description                                                 |
|:----------|:---------|:------------------------------------------------------------|
| `ctx`     | `IN`     | SOAP context                                                |
| `msg`     | `IN/OUT` | SOAP message                                                |
| `node`    | `IN`     | URI of SOAP node which faulted, Node (1.2), faultactor(1.1) |
| `code`    | `IN`     | Code (1.2), faultcode (1.1)                                 |
| `reason`  | `IN`     | Human-readable fault Reason (1.2), faultreason (1.1)        |
| `lang`    | `IN`     | Language of reason (1.2), unused (1.1)                      |
| `role`    | `IN`     | URI representing role, Role (1.2), unused (1.1)             |
| `detail`  | `IN`     | detail elements (user-defined)                              |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapAddFaultReason()

### XmlSoapSetMustUnderstand()

Sets `mustUnderstand` attribute for SOAP header element. According to the standard, if the value is `FALSE`, the attribute is not set.

#### Syntax

    xmlerr XmlSoapSetMustUnderstand(
       xmlsoapctx *ctx,
       xmlelemnode *elem,
       boolean mustUnderstand);

| Parameter        | In/Out   | Description                         |
|:-----------------|:---------|:------------------------------------|
| `ctx`            | `IN`     | SOAP context                        |
| `elem`           | `IN/OUT` | SOAP header element                 |
| `mustUnderstand` | `IN`     | `mustUnderstand` value, TRUE\|FALSE |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapSetRole()

### XmlSoapSetRelay()

Sets Relay attribute for a SOAP header element. If the value is FALSE, the attribute is not set.

#### Syntax

    xmlerr XmlSoapSetRelay(
       xmlsoapctx *ctx,
       xmlelemnode *elem,   boolean Relay);

| Parameter | In/Out   | Description         |
|:----------|:---------|:--------------------|
| `ctx`     | `IN`     | SOAP context        |
| `elem`    | `IN/OUT` | SOAP header element |
| `Relay`   | `IN`     | Relay; `TRUE|FALSE` |

#### Returns

`(xmlerr)` numeric error code, `XMLERR_OK [0]` on success

**See Also:**

XmlSoapGetRelay()

### XmlSoapSetRole()

Sets role for SOAP header element. If the role specified is XMLSOAP_ROLE_ULT, then according to the standard the attribute is not set.

#### Syntax

    xmlerr XmlSoapSetRole(
       xmlsoapctx *ctx,
       xmlelemnode *elem,
       xmlsoaprole role);

| Parameter | In/Out   | Description         |
|:----------|:---------|:--------------------|
| `ctx`     | `IN`     | SOAP context        |
| `elem`    | `IN/OUT` | SOAP header element |
| `role`    | `IN`     | Role value          |

#### Returns

`xmlerr` numeric error code, `XMLERR_OK` on success

**See Also:**

XmlSoapSetMustUnderstand()
