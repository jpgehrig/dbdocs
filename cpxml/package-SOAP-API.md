According to the W3C definition, “SOAP is a lightweight protocol for exchange of information in a decentralized, distributed environment. It is an XML based protocol that consists of three parts: an envelope that defines a framework for describing what is in a message and how to process it, a set of encoding rules for expressing instances of application-defined datatypes, and a convention for representing remote procedure calls and responses."

The structure of a SOAP message follows:

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

The Oracle C++ implementation of the `SOAP` interface includes `SOAP` datatypes, `SoapException` methods, `ConnectRef` methods, and `MsgFactory` methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/using-SOAP-with-XDK.md)

### SOAP Datatypes

Table 6-1 summarizes the datatypes of the `SOAP `package.

Table 6-1 Summary of Datatypes; SOAP Package

| Datatype          | Description                           |
|:------------------|:--------------------------------------|
| SoapExceptionCode | Defines Soap-related exception codes. |
| SoapBinding       | Defines binding for SOAP connections. |
| SoapRole          | Defines roles for SOAP nodes.         |

#### SoapExceptionCode

Defines Soap-related exception codes.

    typedef enum SoapExceptionCode {
       SOAP_UNDEFINED_ERR       = 0,
       SOAP_OTHER_ERR           = 1} SoapExceptionCode;

#### SoapBinding

Defines binding for SOAP connections. HTTP is currently the only choice.

    typedef enum SoapBinding {
       BIND_NONE  = 0,  /* none */
       BIND_HTTP  = 1   /* HTTP */ } SoapBinding;

#### SoapRole

Defines roles for SOAP nodes.

    typedef enum SoapRole {
       ROLE_UNSET = 0,  /* not specified */
       ROLE_NONE  = 1,  /* "none" */
       ROLE_NEXT  = 2,  /* "next" */
       ROLE_ULT   = 3   /* "ultimateReceiver" */ } SoapRole;

### SoapException Interface

Table 6-2 summarizes the methods available through the SoapException Interface.

Table 6-2 Summary of SoapException Interfaces

| Datatype      | Description                                         |
|:--------------|:----------------------------------------------------|
| getCode()     | Get Oracle XML error code embedded in the exception |
| getMessage()  | Get Oracle XML error message.                       |
| getMesLang()  | Get current language encoding of error messages.    |
| getSoapCode() | Get Soap exception code embedded in the exception.  |

#### getCode()

Get Oracle XML error code embedded in the exception. This is a virtual member function inherited from `XMLException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

(unsigned) numeric error code (0 on success)

#### getMessage()

Get Oracle XML error message. Virtual member function inherited from `XMLException`.

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

(oratext \*) Error message

#### getMesLang()

Get current language encoding of error messages. Virtual member function inherited from `XMLException`.

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

(oratext\*) Current language (encoding) of error messages

#### getSoapCode()

Get SOAP exception code embedded in the exception. This is a virtual member function that defines a prototype for implementing defined member functions that return SOAP API exception codes.

##### Syntax

    virtual SoapExceptionCode getSoapCode() const = 0;

##### Returns

(SoapExceptionCode) exception code

### ConnectRef Interface

Table 6-3 summarizes the methods available ConnectRef Interface.

Table 6-3 Summary of ConnectRef Interfaces

| Datatype      | Description                                    |
|:--------------|:-----------------------------------------------|
| ~ConnectRef() | Destroys a SOAP connection object              |
| call()        | Send a SOAP message then waits for a response. |

#### ~ConnectRef()

Destructor. Destroys a SOAP connection object and frees any resources associated with it.

##### Syntax

    ~ConnectRef() throw (SoapException);

#### call()

Send a SOAP message then waits for a response.

##### Syntax

    DocumentRef< Node>* call(
       DocumentRef< Node>& msg) throw (SoapException);

| Parameter | Description                    |
|:----------|:-------------------------------|
| `msg`     | The SOAP message that is sent. |

##### Returns

(DocumentRef) returned message

### MsgFactory Interface

Table 6-4 summarizes the methods available through the MsgFactory Interface.

Table 6-4 Summary of MsgFactory Interfaces

| Datatype            | Description                                                   |
|:--------------------|:--------------------------------------------------------------|
| ~MsgFactory()       | Destroys the SOAP message factory instance.                   |
| MsgFactory()        | Creates and returns a SOAP Message Factory instance.          |
| addBodyElement()    | Adds an element to a SOAP message body.                       |
| addFaultReason()    | Add s an additional Reason to Fault                           |
| addHeaderElement()  | Adds an element to SOAP header.                               |
| createConnection()  | Creates a SOAP connection.                                    |
| createMessage()     | Creates and returns an empty SOAP message.                    |
| destroyMessage()    | Destroyw a SOAP message.                                      |
| getBody()           | Returns a SOAP message's envelope body..                      |
| getBodyElement()    | Gets an element from a SOAP body.                             |
| getEnvelope()       | Returns a SOAP part's envelope.                               |
| getFault()          | Returns Fault code, reason, and details.                      |
| getHeader()         | Returns a SOAP message's envelope header..                    |
| getHeaderElement()  | Gets an element from a SOAP header.                           |
| getMustUnderstand() | Gets `mustUnderstand` attribute from the SOAP header element. |
| getReasonNum()      | Gets the number of reasons in `Fault` element.                |
| getReasonLang()     | Gets a language of a reason with a particular index.          |
| getRole()           | Gets role from SOAP header element.                           |
| hasFault()          | Determines if a SOAP message contains a Fault object.         |
| setFault()          | Sets Fault in a SOAP message.                                 |
| setMustUnderstand() | Sets `mustUnderstand` attribute for the SOAP header element.  |
| setRole()           | Sets the role for SOAP header element.                        |

#### ~MsgFactory()

Destructor. Destroys the SOAP message factory. All allocated memory is frieed and all connections are closed.

##### Syntax

    ~MsgFactory() throw (SoapException);

#### MsgFactory()

Creates and returns a SOAP Message Factory instance.

##### Syntax

    MsgFactory(
       Context* ctx_ptr) throw (SoapException);

| Parameter | Description       |
|:----------|:------------------|
| `ctx_ptr` | `TContext` object |

##### Returns

(MsgFactory) object

#### addBodyElement()

Adds an element to a SOAP message body.

##### Syntax

    Node* addBodyElement( DocumentRef< Node>& msg,
       oratext *qname,
       oratext *uri) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `msg`     | SOAP message                    |
| `qname`   | QName of element to add         |
| `uri`     | Namespace URI of element to add |

##### Returns

(Node\*) pointer to the created element

#### addFaultReason()

Adds an additional Reason to Fault. The same re son text may be provided in different languages. When the fault is created, the primary language and reasonare added at that time; use this function to add additional translations of the reason.

##### Syntax

    void addFaultReason(
       DocumentRef< Node>& msg,
       oratext *reason,
       oratext *lang) throw (SoapException);

| Parameter | Description                 |
|:----------|:----------------------------|
| `msg`     | SOAP message                |
| `reason`  | Human-readable fault reason |
| `lang`    | Language of reason          |

#### addHeaderElement()

Adds an element to SOAP header.

##### Syntax

    Node* addHeaderElement(
       DocumentRef< Node>& msg,
       oratext *qname, oratext *uri) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `msg`     | SOAP message                    |
| `qname`   | QName of element to add         |
| `uri`     | Namespace URI of element to add |

##### Returns

(Node\*) pointer to the created element

#### createConnection()

Creates a SOAP connection object. The connection reference object should explicitly deleted by the user.

##### Syntax

    ConnectRef< Node>* createConnection(
       SoapBinding bind,
       void *endp,
       oratext *buf,
       ubig_ora bufsiz,
       oratext *msgbuf,
       ubig_ora msgbufsiz) throw (SoapException);

| Parameter   | Description                                      |
|:------------|:-------------------------------------------------|
| `bind`      | connection binding                               |
| `endp`      | connection endpoint                              |
| `buf`       | data buffer (or `NULL` to have one allocated)    |
| `bufsiz`    | size of data buffer (or 0 for default size)      |
| `msgbuf`    | message buffer (or `NULL` to have one allocated) |
| `msgfubsiz` | size of message buffer (or 0 for default size)   |

##### Returns

(ConnectRef) connect object

#### createMessage()

Creates and returns an empty SOAP message. The reference object should be explicitly deleted by the user when no longer needed.

##### Syntax

    DocumentRef< Node>* CreateMessage() throw (SoapException);

##### Returns

(DocumentRef\*) SOAP message, or an exception

#### destroyMessage()

Destroys a SOAP message.

##### Syntax

    void destroyMessage(
       DocumentRef< Node>& msg) throw (SoapException);

| Parameter | Description       |
|:----------|:------------------|
| `msg`     | The SOAP message. |

#### getBody()

Returns a SOAP message's envelope body as a pointer to the body's element node.

##### Syntax

    Node* getBody(
       DocumentRef<Node>& msg) throw (SoapException);

| Parameter | Description  |
|:----------|:-------------|
| `msg`     | SOAP message |

##### Returns

(Node\*) pointer to the SOAP message's envelope body

#### getBodyElement()

Gets an element from a SOAP body as a pointer to its element node.

##### Syntax

    Node* getBodyElement(
       DocumentRef< Node>& msg,
       oratext *uri,
       oratext *local) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `msg`     | SOAP message                    |
| `uri`     | Namespace URI of element to add |
| `local`   | Local name of element to get    |

##### Returns

(Node\*) pointer to the named element

#### getEnvelope()

Returns a SOAP part's envelope as a pointer to envelope element node.

##### Syntax

    Node* getEnvelope(
       DocumentRef<Node>& msg) throw (SoapException);

| Parameter | Description  |
|:----------|:-------------|
| `msg`     | SOAP message |

##### Returns

(Node\*) pointer to the SOAP message's envelope

#### getFault()

Returns Fault code, reason, and details through user variables. `NULL` may be supplied for any part that is not needed. For `lang`, if the pointed-to variable is `NULL`, it will be set to the default language, that of the first reason.

##### Syntax

    Node* getFault(
       DocumentRef< Node>& msg,
       oratext **code,
       oratext **reason,
       oratext **lang,
       oratext **node,
       oratext **role) throw (SoapException);

| Parameter | Description                                                                        |
|:----------|:-----------------------------------------------------------------------------------|
| `msg`     | SOAP message                                                                       |
| `code`    | Fault code                                                                         |
| `reason`  | Human-readable fault reason                                                        |
| `lang`    | Desired reason language or `NULL` (default language, same as for the first reason) |
| `node`    | Fault node                                                                         |
| `role`    | Role: next, none, or ulitmate receiver (not used in 1.1)                           |

##### Returns

(Node) pointer to the detail

#### getHeader()

Returns a SOAP message's envelope header as a pointer to the header element node.

##### Syntax

    Node* getHeader(
       DocumentRef< Node>& msg) throw (SoapException);

| Parameter | Description  |
|:----------|:-------------|
| `msg`     | SOAP message |

##### Returns

(Node\*) pointer to the SOAP message's envelope header

#### getHeaderElement()

Gets an element from a SOAP header as a pointer to its element node.

##### Syntax

    Node* getHeaderElement(
       DocumentRef< Node>& msg,
       oratext *uri,
       oratext *local) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `msg`     | SOAP message                    |
| `uri`     | Namespace URI of element to get |
| `local`   | Local name of element to get    |

##### Returns

(Node\*) pointer to the named element

#### getMustUnderstand()

Gets `mustUnderstand` attribute from SOAP header element.

##### Syntax

    boolean getMustUnderstand(
       ElementRef< Node>& elem) throw (SoapException);

| Parameter | Description         |
|:----------|:--------------------|
| `elem`    | SOAP header element |

##### Returns

(boolean) value of the `mustUnderstand` attribute

#### getReasonNum()

Determines the number of reasons in the `Fault` element. Returns `0` if no `Fault`.

##### Syntax

    ub4 getReasonNum(
       DocumentRef< Node>& msg) throw (SoapException);

| Parameter | Description  |
|:----------|:-------------|
| `msg`     | SOAP message |

##### Returns

(up4) number of reasons in Fault element

#### getReasonLang()

Returns the language of a reason with a particular index.

##### Syntax

    oratext* getReasonLang(
       DocumentRef< Node>& msg,
       ub4 idx) throw (SoapException);

| Parameter | Description             |
|:----------|:------------------------|
| `msg`     | SOAP message            |
| `idx`     | index of a fault reason |

##### Returns

(oratext \*) value of property or `NULL`.

#### getRole()

Gets role from SOAP header element.

##### Syntax

    SoapRole getRole(
       ElementRef< Node>& elem) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `elem`    | Reference to the header element |

##### Returns

(SoapRole) header element's role

#### hasFault()

Determines if a SOAP message contains a Fault object.

##### Syntax

    boolean hasFault(
       DocumentRef< Node>& msg) throw (SoapException);

| Parameter | Description  |
|:----------|:-------------|
| `msg`     | SOAP message |

##### Returns

(boolean) `TRUE` if there's a Fault, `FALSE` if not

#### setFault()

Sets Fault in a SOAP message.

##### Syntax

    void setFault(
       DocumentRef< Node>& msg,
       oratext *node,
       oratext *code,
       oratext *reason,
       oratext *lang,
       oratext *role,
      ElementRef< Node>& detail) throw (SoapException);

| Parameter | Description                                     |
|:----------|:------------------------------------------------|
| `msg`     | SOAP message                                    |
| `node`    | URI of SOAP node which faulted                  |
| `code`    | Fault code                                      |
| `reason`  | Human-readable fault reason                     |
| `lang`    | Language                                        |
| `role`    | URI representing role, Role (1.2), unused (1.1) |
| `detail`  | User-defined elements                           |

#### setMustUnderstand()

Sets `mustUnderstand` attribute for the SOAP header element.

##### Syntax

    void setMustUnderstand(
       ElementRef< Node>& elem,
       boolean mustUnderstand) throw (SoapException);

| Parameter        | Description                                |
|:-----------------|:-------------------------------------------|
| `elem`           | SOAP header element                        |
| `mustUnderstand` | `mustUnderstand` value (`TRUE `or `FALSE`) |

#### setRole()

Sets the role for SOAP header element.

##### Syntax

    void setRole(
       ElementRef< Node>& elem,
       SoapRole role) throw (SoapException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `elem`    | reference to the header element |
| `role`    | role value                      |
