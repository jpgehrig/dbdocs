The various interfaces in the `DOM` package represent DOM level 2 Core interfaces specified by W3C: [`http://www.w3.org/TR/DOM-Level-2-Core/`](http://www.w3.org/TR/DOM-Level-2-Core/).

### About DOM Interfaces

DOM interfaces are represented as generic references to different implementations of the DOM specifications. They are parameterized by Node, which supports various specializations and instantiations. Of them, the most important is `xmlnode` that corresponds to the current C implementation.

These generic references do not have a `NULL`-like value. Any implementation should never create a stateless reference. If there is need to signal that something has no state, an exception should be thrown.

Many methods might throw the `SYNTAX_ERR` exception, if the DOM tree is incorrectly formed, or `UNDEFINED_ERR`, in the case of wrong parameters or unexpected `NULL` pointers. If these are the only errors that a particular method might throw, it is not reflected in the method signature.

Actual DOM trees do not dependent on the context (`TCtx`). However, manipulations on DOM trees in the current, `xmlctx` based implementation require access to the current context (`TCtx`). This is accomplished by passing the context pointer to the constructor of DOMImplRef. In multithreaded environment `DOMImplRef` is always created in the thread context and, so, has the pointer to the right context.

`DOMImplRef` providea a way to create DOM trees. DomImplRef is a reference to the actual `DOMImplementation` object that is created when a regular, non-copy constructor of `DomImplRef` is invoked. This works well in multithreaded environment where DOM trees need to be shared, and each thread has a separate TCtx associated with it. This works equally well in a single threaded environment.

`DOMString` is only one of encodings supported by Oracle implementations. The support of other encodings is Oracle's extension. The `oratext*` data type is used for all encodings.

### Dom Datatypes

Table 3-1 summarizes the datatypes of the Dom package.

Table 3-1 Summary of Datatypes; Dom Package

| Datatype           | Description                              |
|:-------------------|:-----------------------------------------|
| AcceptNodeCodes    | Defines values returned by node filters. |
| CompareHowCode     | Defines type of comparison.              |
| DOMNodeType        | Defines type of node.                    |
| DOMExceptionCode   | Defines codes for DOM exception.         |
| WhatToShowCode     | Defines codes for filtering.             |
| RangeExceptionCode | Codes for DOM Range exceptions.          |

#### AcceptNodeCodes

Defines values returned by node filters. Used by node iterators and tree walkers.

##### Definition

    typedef enum AcceptNodeCode {
       FILTER_ACCEPT   = 1,
       FILTER_REJECT   = 2,
       FILTER_SKIP     = 3
        } AcceptNodeCode;

#### CompareHowCode

Defines type of comparison.

##### Definition

    typedef enum CompareHowCode {
       START_TO_START = 0,
       START_TO_END = 1,
       END_TO_END = 2,
       END_TO_START = 3 }
    CompareHowCode;

#### DOMNodeType

Defines type of node.

##### Definition

    typedef enum DOMNodeType {
       UNDEFINED_NODE = 0,
       ELEMENT_NODE = 1,
       ATTRIBUTE_NODE = 2,
       TEXT_NODE = 3,
       CDATA_SECTION_NODE = 4,
       ENTITY_REFERENCE_NODE = 5,
       ENTITY_NODE = 6,
       PROCESSING_INSTRUCTION_NODE = 7,
       COMMENT_NODE = 8,
       DOCUMENT_NODE = 9,
       DOCUMENT_TYPE_NODE = 10,
       DOCUMENT_FRAGMENT_NODE = 11,
       NOTATION_NODE = 12
    } DOMNodeType;

#### DOMExceptionCode

Defines codes for DOM exception.

##### Definition

    typedef enum DOMExceptionCode {
       UNDEFINED_ERR               = 0,
       INDEX_SIZE_ERR              = 1,
       DOMSTRING_SIZE_ERR          = 2,
       HIERARCHY_REQUEST_ERR       = 3,
       WRONG_DOCUMENT_ERR          = 4,
       INVALID_CHARACTER_ERR       = 5,
       NO_DATA_ALLOWED_ERR         = 6,
       NO_MODIFICATION_ALLOWED_ERR = 7,
       NOT_FOUND_ERR               = 8,
       NOT_SUPPORTED_ERR           = 9,
       INUSE_ATTRIBUTE_ERR         = 10,
       INVALID_STATE_ERR           = 11,
       SYNTAX_ERR                  = 12,
       INVALID_MODIFICATION_ERR    = 13,
       NAMESPACE_ERR               = 14,
       INVALID_ACCESS_ERR          = 15
    } DOMExceptionCode;

#### WhatToShowCode

Defines codes for filtering.

##### Definition

    typedef unsigned long WhatToShowCode;
       const unsigned long SHOW_ALL = 0xFFFFFFFF; c
       onst unsigned long SHOW_ELEMENT = 0x00000001;
       const unsigned long SHOW_ATTRIBUTE = 0x00000002;
       const unsigned long SHOW_TEXT = 0x00000004;
       const unsigned long SHOW_CDATA_SECTION = 0x00000008;
       const unsigned long SHOW_ENTITY_REFERENCE = 0x00000010;
       const unsigned long SHOW_ENTITY = 0x00000020;
       const unsigned long SHOW_PROCESSING_INSTRUCTION = 0x00000040;
       const unsigned long SHOW_COMMENT = 0x00000080;
       const unsigned long SHOW_DOCUMENT = 0x00000100;
       const unsigned long SHOW_DOCUMENT_TYPE = 0x00000200;
       const unsigned long SHOW_DOCUMENT_FRAGMENT = 0x00000400;
       const unsigned long SHOW_NOTATION = 0x00000800;

#### RangeExceptionCode

Codes for DOM Range exceptions.

##### Definition

    typedef enum RangeExceptionCode {
       RANGE_UNDEFINED_ERR         = 0,
       BAD_BOUNDARYPOINTS_ERR      = 1,
       INVALID_NODE_TYPE_ERR       = 2
    } RangeExceptionCode;


### AttrRef Interface

Table 3-2 summarizes the methods available through `AttrRef` interface.

Table 3-2 Summary of AttrRef Methods; Dom Package

| Function          | Summary                                                           |
|:------------------|:------------------------------------------------------------------|
| AttrRef()         | Constructor.                                                      |
| getName()         | Return attribute's name.                                          |
| getOwnerElement() | Return attribute's owning element.                                |
| getSpecified()    | Return boolean indicating if an attribute was explicitly created. |
| getValue()        | Return attribute's value.                                         |
| setValue()        | Set attribute's value.                                            |
| ~AttrRef()        | Public default destructor.                                        |

#### AttrRef()

Class constructor.

| Syntax                                                                  | Description                                                                            |
|:------------------------------------------------------------------------|:---------------------------------------------------------------------------------------|
| `AttrRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given attribute node after a call to `createAttribute`. |
| `AttrRef(`<br>`   const AttrRef< Node>& nref);`                         | Copy constructor.                                                                      |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(AttrRef)` `Node` reference object

#### getName()

Returns the fully-qualified name of an attribute (in the data encoding) as a `NULL`-terminated string.

##### Syntax

     oratext* getName() const;

##### Returns

`(oratext *)` name of attribute

#### getOwnerElement()

Returns attribute's owning element

##### Syntax

    Node* getOwnerElement();

##### Returns

`(Node*)` attribute's owning element node.

#### getSpecified()

Returns the 'specified' value for an attribute. If the attribute was explicitly given a value in the original document, it is `TRUE`; otherwise, it is `FALSE`. If the node is not an attribute, returns `FALSE`. If the user sets attribute's value through DOM, its 'specified' value will be `TRUE`.

##### Syntax

    boolean getSpecified() const;

##### Returns

`(boolean)` attribute's "specified" value

#### getValue()

Returns the "value" (character data) of an attribute (in the data encoding) as `NULL`-terminated string. Character and general entities will have been replaced.

##### Syntax

    oratext* getValue() const;

##### Returns

`(oratext*)` attribute's value

#### setValue()

Sets the given attribute's value to data. The new value must be in the data encoding. It is not verified, converted, or checked. The attribute's 'specified' flag will be `TRUE` after setting a new value.

##### Syntax

    void setValue(
       oratext* data)
    throw (DOMException);

| Parameter | Description            |
|:----------|:-----------------------|
| `data`    | new value of attribute |

#### ~AttrRef()

This is the default destructor.

##### Syntax

    ~AttrRef();

### CDATASectionRef Interface

Table 3-3 summarizes the methods available through CDATASectionRef interface.

Table 3-3 Summary of CDATASectionRef Methods; Dom Package

| Function           | Summary                    |
|:-------------------|:---------------------------|
| CDATASectionRef()  | Constructor.               |
| ~CDATASectionRef() | Public default destructor. |

#### CDATASectionRef()

Class constructor.

| Syntax                                                                          | Description                                                                           |
|:--------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------|
| `CDATASectionRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given CDATA node after a call to `createCDATASection`. |
| `CDATASectionRef(`<br>`   const CDATASectionRef< Node>& nref);`                 | Copy constructor.                                                                     |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(CDATASectionRef)` `Node` reference object

#### ~CDATASectionRef()

This is the default destructor.

##### Syntax

    ~CDATASectionRef();

### CharacterDataRef Interface

Table 3-4 summarizes the methods available through `CharacterDataRef` interface.

Table 3-4 Summary of CharacterDataRef Methods; Dom Package

| Function        | Summary                                             |
|:----------------|:----------------------------------------------------|
| appendData()    | Append data to end of node's current data.          |
| deleteData()    | Remove part of node's data.                         |
| freeString()    | Deallocate the string allocated by `substringData`. |
| getData()       | Return node's data.                                 |
| getLength()     | Return length of node's data.                       |
| insertData()    | Insert string into node's current data.             |
| replaceData()   | Replace part of node's data.                        |
| setData()       | Set node's data.                                    |
| substringData() | Get substring of node's data.                       |

#### appendData()

Append a string to the end of a `CharacterData` node's data. The appended data should be in the data encoding. It will not be verified, converted, or checked.

##### Syntax

    void appendData(
       oratext* data)
    throw (DOMException);

| Parameter | Description    |
|:----------|:---------------|
| `data`    | data to append |

#### deleteData()

Remove a range of characters from a `CharacterData` node's data. The offset is zero-based, so offset zero refers to the start of the data. Both offset and count are in characters, not bytes. If the sum of offset and count exceeds the data length then all characters from offset to the end of the data are deleted.

##### Syntax

    void deleteData(
       ub4 offset,
       ub4 count)
    throw (DOMException);

| Parameter | Description                            |
|:----------|:---------------------------------------|
| `offset`  | character offset where deletion starts |
| `count`   | number of characters to delete         |

#### freeString()

Deallocates the string allocated by substringData(). It is Oracle's extension.

##### Syntax

    void freeString(
       oratext* str);

| Parameter | Description |
|:----------|:------------|
| `str`     | string      |

#### getData()

Returns the data for a `CharacterData` node (type text, comment or CDATA) in the data encoding.

##### Syntax

    oratext* getData() const;

##### Returns

`(oratext*)` node's data

#### getLength()

Returns the length of the data for a `CharacterData` node (type `Text`, `Comment` or `CDATA`) in characters (not bytes).

##### Syntax

    ub4 getLength() const;

##### Returns

`(ub4)` length in characters (not bytes!) of node's data

#### insertData()

Insert a string into a `CharacterData` node's data at the specified position. The inserted data must be in the data encoding. It will not be verified, converted, or checked. The offset is specified as characters, not bytes. The offset is zero-based, so inserting at offset zero prepends the data.

##### Syntax

    void insertData(
       ub4 offset,
       oratext* data)
    throw (DOMException);

| Parameter | Description                             |
|:----------|:----------------------------------------|
| `offset`  | character offset where insertion starts |
| `data`    | data to insert                          |

#### replaceData()

Replaces a range of characters in a `CharacterData` node's data with a new string. The offset is zero-based, so offset zero refers to the start of the data. The replacement data must be in the data encoding. It will not be verified, converted, or checked. The offset and count are both in characters, not bytes. If the sum of offset and count exceeds length, then all characters to the end of the data are replaced.

##### Syntax

    void replaceData(
       ub4 offset,
       ub4 count,
       oratext* data)
    throw (DOMException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `offset`  | offset                          |
| `count`   | number of characters to replace |
| `data`    | data                            |

#### setData()

Sets data for a `CharacterData` node (type text, comment or CDATA), replacing the old data. The new data is not verified, converted, or checked -- it should be in the data encoding.

##### Syntax

    void setData(
       oratext* data)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `data`    | data        |

#### substringData()

Returns a range of character data from a `CharacterData` node (type `Text`, `Comment` or `CDATA`). Since the data is in the data encoding, offset and count are in characters, not bytes. The beginning of the string is offset 0. If the sum of offset and count exceeds the length, then all characters to the end of the data are returned. The substring is permanently allocated in the context managed memory and should be explicitly deallocated by `freeString`

##### Syntax

    oratext* substringData(
       ub4 offset,
       ub4 count)
    throw (DOMException);

| Parameter | Description                     |
|:----------|:--------------------------------|
| `offset`  | offset                          |
| `count`   | number of characters to extract |

##### Returns

`(oratext *)` specified substring

### CommentRef Interface

Table 3-5 summarizes the methods available through `CommentRef` interface.

Table 3-5 Summary of CommentRef Methods; Dom Package

| Function      | Summary                    |
|:--------------|:---------------------------|
| CommentRef()  | Constructor.               |
| ~CommentRef() | Public default destructor. |

#### CommentRef()

Class constructor.

| Syntax                                                                     | Description                                                                      |
|:---------------------------------------------------------------------------|:---------------------------------------------------------------------------------|
| `CommentRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given comment node after a call to createComment. |
| `CommentRef(`<br>`   const CommentRef< Node>& nref);`                      | Copy constructor.                                                                |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(CommentRef)` `Node` reference object

#### ~CommentRef()

This is the default destructor.

##### Syntax

    ~CommentRef();

### DOMException Interface

Table 3-6 summarizes the methods available through the `DOMException `interface.

Table 3-6 Summary of DOMException Methods; Dom Package

| Function     | Summary                                           |
|:-------------|:--------------------------------------------------|
| getDOMCode() | Get DOM exception code embedded in the exception. |
| getMesLang() | Get current language encoding of error messages.  |
| getMessage() | Get Oracle XML error message.                     |

#### getDOMCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning DOM exception codes, defined in `DOMExceptionCode`, of the exceptional situations during execution

##### Syntax

    virtual DOMExceptionCode getDOMCode() const = 0;

##### Returns

`(DOMExceptionCode)` exception code

#### getMesLang()

Virtual member function inherited from `XmlException`

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext*)` Current language (encoding) of error messages

#### getMessage()

Virtual member function inherited from `XmlException`

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message

### DOMImplRef Interface

Table 3-7 summarizes the methods available through `DOMImplRef` interface.

Table 3-7 Summary of DOMImplRef Methods; Dom Package

| Function             | Summary                                                      |
|:---------------------|:-------------------------------------------------------------|
| DOMImplRef()         | Constructor.                                                 |
| createDocument()     | Create document reference.                                   |
| createDocumentType() | Create DTD reference.                                        |
| formDocument()       | Forms document reference given a document pointer.           |
| getImplementation()  | Get `DOMImplementation` object associated with the document. |
| getNoMod()           | Get the 'no modification allowed' flag value.                |
| hasFeature()         | Determine if DOM feature is implemented.                     |
| setContext()         | Set another context to a node.                               |
| ~DOMImplRef()        | Public default destructor.                                   |

#### DOMImplRef()

Class constructor.

| Syntax                                                                                   | Description                                                                                                                |
|:-----------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| `DOMImplRef(`<br>`   Context* ctx_ptr,`<br>`   DOMImplementation< Node>* impl_ptr);`     | Creates reference object to `DOMImplementation` object in a given context. Returns reference to the implementation object. |
| `DOMImplRef(`<br>`   const DOMImplRef< Context, Node>& iref);`                           | It is needed to create other references to the implementation object; deletion flags are not copied.                       |
| `DOMImplRef(`<br>`   const DOMImplRef< Context, Node>& iref,`<br>`   Context* ctx_ptr);` | It is needed to create references to the implementation object in a different context; deletion flags are not copied.      |

| Parameter  | Description     |
|:-----------|:----------------|
| `ctx_ptr`  | context pointer |
| `impl_ptr` | implementation  |

##### Returns

`(DOMImplRef)` reference to the implementation object

#### createDocument()

Creates document reference

##### Syntax

    DocumentRef< Node>* createDocument(
       oratext* namespaceURI,
       oratext* qualifiedName,
       DocumentTypeRef< Node>& doctype)
    throw (DOMException);

| Parameter       | Description                    |
|:----------------|:-------------------------------|
| `namespaceURI`  | namespace URI of root element  |
| `qualifiedName` | qualified name of root element |
| `doctype`       | associated DTD node            |

##### Returns

`(DocumentRef< Node>*)` document reference

#### createDocumentType()

Creates DTD reference

##### Syntax

    DocumentTypeRef< Node>* createDocumentType(
       oratext* qualifiedName,
       oratext* publicId,
       oratext* systemId)
    throw (DOMException);

| Parameter       | Description               |
|:----------------|:--------------------------|
| `qualifiedName` | qualified name            |
| `publicId`      | external subset public Id |
| `systemId`      | external subset system Id |

##### Returns

`(DocumentTypeRef< Node>*)` DTD reference

#### formDocument()

Forms a document reference given a document pointer.

##### Syntax

    DocumentRef< Node>* formDocument( Node* node);

| Parameter | Description                  |
|:----------|:-----------------------------|
| `node`    | pointer to the document node |

##### Returns

(DocumentRef\< Node\>\*) pointer to the document reference

#### getImplementation()

Returns `DOMImplementation` object that was used to create this document. When the `DOMImplementation` object is destructed, all document trees associated with it are also destructed.

##### Syntax

    DOMImplementation< Node>* getImplementation() const;

##### Returns

`(DOMImplementation)` `DOMImplementation` reference object

#### getNoMod()

Get the 'no modification allowed' flag value. This is an Oracle extension.

##### Syntax

    boolean getNoMod() const;

##### Returns

`TRUE` if flag's value is `TRUE`, `FALSE` otherwise

#### hasFeature()

Determine if a DOM feature is implemented. Returns `TRUE` if the feature is implemented in the specified version, `FALSE` otherwise.

In level 1, the legal values for package are 'HTML' and 'XML' (case-insensitive), and the version is the string "1.0". If the version is not specified, supporting any version of the feature will cause the method to return `TRUE`.

DOM 1.0 features are "XML" and "HTML".

DOM 2.0 features are "Core", "XML", "HTML", "Views", "StyleSheets", "CSS", "CSS2", "Events", "UIEvents", "MouseEvents", "MutationEvents", "HTMLEvents", "Range", "Traversal"

##### Syntax

    boolean hasFeature(
       oratext* feature,
       oratext* version);

| Parameter | Description             |
|:----------|:------------------------|
| `feature` | package name of feature |
| `version` | version of package      |

##### Returns

`(boolean)` is feature implemented?

#### setContext()

It is needed to create node references in a different context

##### Syntax

    void setContext(
       NodeRef< Node>& nref,
       Context* ctx_ptr);

| Parameter | Description     |
|:----------|:----------------|
| `nref`    | reference node  |
| `ctx_ptr` | context pointer |

#### ~DOMImplRef()

This is the default destructor. It cleans the reference to the implementation object. It is usually called by the environment. But it can be called by the user directly if necessary.

##### Syntax

    ~DOMImplRef();

### DOMImplementation Interface

Table 3-8 summarizes the methods available through `DOMImplementation` interface.

Table 3-8 Summary of DOMImplementation Methods; Dom Package

| Function             | Summary                                     |
|:---------------------|:--------------------------------------------|
| DOMImplementation()  | Constructor.                                |
| getNoMod()           | Get the 'nomodificationallowed' flag value. |
| ~DOMImplementation() | Public default destructor.                  |

#### DOMImplementation()

Creates `DOMImplementation` object. Sets the 'no modifications allowed' flag to the parameter value.

##### Syntax

    DOMImplementation(
       boolean no_mod);

| Parameter | Description                                                         |
|:----------|:--------------------------------------------------------------------|
| `no_mod`  | whether modifications are allowed (`FALSE`) or not allowed (`TRUE`) |

##### Returns

`(DOMImplementation)` implementation object

#### getNoMod()

Get the 'no modification allowed' flag value. This is an Oracle extension.

##### Syntax

    boolean getNoMod() const;

##### Returns

`TRUE` if flag's value is `TRUE`, `FALSE` otherwise

#### ~DOMImplementation()

This is the default destructor. It removes all DOM trees associated with this object.

##### Syntax

    ~DOMImplementation();

### DocumentFragmentRef Interface

Table 3-9 summarizes the methods available through `DocumentFragmentRef `interface.

Table 3-9 Summary of DocumentFragmentRef Methods; Dom Package

| Function               | Summary                    |
|:-----------------------|:---------------------------|
| DocumentFragmentRef()  | Constructor.               |
| ~DocumentFragmentRef() | Public default destructor. |

#### DocumentFragmentRef()

Class constructor.

| Syntax                                                                              | Description                                                                                  |
|:------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------|
| `DocumentFragmentRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given fragment node after a call to `createDocumentFragment`. |
| `DocumentFragmentRef(`<br>`   const DocumentFragmentRef< Node>& nref);`             | Copy constructor.                                                                            |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(DocumentFragmentRef)` `Node` reference object

#### ~DocumentFragmentRef()

This is the default destructor.

##### Syntax

    ~DocumentFragmentRef() {}

### DocumentRange Interface

Table 3-10 summarizes the methods available through `DocumentRange` interface.

Table 3-10 Summary of DocumentRange Methods; Dom Package

| Function         | Summary                  |
|:-----------------|:-------------------------|
| DocumentRange()  | Constructor.             |
| createRange()    | Create new range object. |
| destroyRange()   | Destroys Range object.   |
| ~DocumentRange() | Default destructor.      |

#### DocumentRange()

Constructs the factory.

##### Syntax

    DocumentRange();

##### Returns

`(DocumentRange)` new factory object

#### createRange()

Create new range object.

##### Syntax

    Range< Node>* createRange(
       DocumentRef< Node>& doc);

| Parameter | Description                |
|:----------|:---------------------------|
| `doc`     | reference to document node |

##### Returns

`(Range*)` Pointer to new range

#### destroyRange()

Destroys range object.

##### Syntax

    void destroyRange(
       Range< Node>* range)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `range`   | range       |

#### ~DocumentRange()

Default destructor.

##### Syntax

    ~DocumentRange();

### DocumentRef Interface

Table 3-11 summarizes the methods available through DocumentRef interface.

Table 3-11 Summary of DocumentRef Methods; Dom Package

| Function                      | Summary                                                             |
|:------------------------------|:--------------------------------------------------------------------|
| DocumentRef()                 | Constructor.                                                        |
| createAttribute()             | Create an attribute node.                                           |
| createAttributeNS()           | Create an attribute node with namespace information.                |
| createCDATASection()          | Create a CDATA node.                                                |
| createComment()               | Create a comment node.                                              |
| createDocumentFragment()      | Create a document fragment.                                         |
| createElement()               | Create an element node.                                             |
| createElementNS()             | Create an element node with names pace information.                 |
| createEntityReference()       | Create an entity reference node.                                    |
| createProcessingInstruction() | Create a `ProcessingInstruction` node                               |
| createTextNode()              | Create a text node.                                                 |
| getDoctype()                  | Get DTD associated with the document.                               |
| getDocumentElement()          | Get top-level element of this document.                             |
| getElementById()              | Get an element given its ID.                                        |
| getElementsByTagName()        | Get elements in the document by tag name.                           |
| getElementsByTagNameNS()      | Get elements in the document by tag name (namespace aware version). |
| getImplementation()           | Get `DOMImplementation` object associated with the document.        |
| importNode()                  | Import a node from another DOM.s                                    |
| ~DocumentRef()                | Public default destructor.                                          |

#### DocumentRef()

This is a constructor.

| Syntax                                                                  | Description          |
|:------------------------------------------------------------------------|:---------------------|
| `DocumentRef(`<br>`   const NodeRef< Node>& nref,`<br>`   Node* nptr);` | Default constructor. |
| `DocumentRef(`<br>`   const DocumentRef< Node>& nref);`                 | Copy constructor.    |

| Parameter | Description                      |
|:----------|:---------------------------------|
| `nref`    | reference to provide the context |
| `nptr`    | referenced node                  |

##### Returns

`(DocumentRef)` `Node` reference object

#### createAttribute()

Creates an attribute node with the given name. This is the non-namespace aware function. The new attribute will have `NULL` namespace URI and prefix, and its local name will be the same as its name, even if the name specified is a qualified name. The new node is an orphan with no parent. The name is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createAttribute(
       oratext* name)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `name`    | name        |

##### Returns

`(Node*)` New attribute node

#### createAttributeNS()

Creates an attribute node with the given namespace URI and qualified name. The new node is an orphan with no parent. The URI and qualified name are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createAttributeNS(
       oratext* namespaceURI,
       oratext* qualifiedName)
       throw (DOMException);

| Parameter       | Description    |
|:----------------|:---------------|
| `namespaceURI`  | namespace URI  |
| `qualifiedName` | qualified name |

##### Returns

`(Node*)` New attribute node

#### createCDATASection()

Creates a `CDATA` section node with the given initial data (which should be in the data encoding). A `CDATA` section is considered verbatim and is never parsed; it will not be joined with adjacent text nodes by the normalize operation. The initial data may be `NULL`, if provided; it is not verified, converted, or checked. The name of a `CDATA` node is always "`#cdata-section`". The new node is an orphan with no parent. The `CDATA` is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createCDATASection(
       oratext* data)
    throw (DOMException);

| Parameter | Description       |
|:----------|:------------------|
| `data`    | data for new node |

##### Returns

`(Node*)` New CDATA node

#### createComment()

Creates a comment node with the given initial data (which must be in the data encoding). The data may be `NULL`, if provided; it is not verified, converted, or checked. The name of the comment node is always "`#comment`". The new node is an orphan with no parent. The comment data is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createComment(
       oratext* data)
    throw (DOMException);

| Parameter | Description       |
|:----------|:------------------|
| `data`    | data for new node |

##### Returns

`(Node*)` New comment node

#### createDocumentFragment()

Creates an empty Document Fragment node. A document fragment is treated specially when it is inserted into a DOM tree: the children of the fragment are inserted in order instead of the fragment node itself. After insertion, the fragment node will still exist, but have no children. The name of a fragment node is always "`#document-fragment`".

##### Syntax

    Node* createDocumentFragment()
    throw (DOMException);

##### Returns

`(Node*)` new document fragment node

#### createElement()

Creates an element node with the given tag name (which should be in the data encoding). The new node is an orphan with no parent. The `tagname` is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

Note that the tag name of an element is case sensitive. This is the non-namespace aware function: the new node will have `NULL` namespace URI and prefix, and its local name will be the same as its tag name, even if the tag name specified is a qualified name.

##### Syntax

    Node* createElement(
       oratext* tagname)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `tagname` | tag name    |

##### Returns

`(Node*)` New element node

#### createElementNS()

Creates an element with the given namespace URI and qualified name. The new node is an orphan with no parent. The URI and qualified name are not copied, their pointers are just stored. The user is responsible for persistence and freeing of that data.

Note that element names are case sensitive, and the qualified name is required though the URI may be `NULL`. The qualified name will be split into prefix and local parts. The tagName will be the full qualified name.

##### Syntax

    Node* createElementNS(
       oratext* namespaceURI,
       oratext* qualifiedName)
    throw (DOMException);

| Parameter       | Description    |
|:----------------|:---------------|
| `namespaceURI`  | namespace URI  |
| `qualifiedName` | qualified name |

##### Returns

`(Node*)` New element node

#### createEntityReference()

Creates an entity reference node; the name (which should be in the data encoding) is the name of the entity to be referenced. The named entity does not have to exist. The name is not verified, converted, or checked. The new node is an orphan with no parent. The entity reference name is not copied; its pointer is just stored. The user is responsible for persistence and freeing of that data.

Note that entity reference nodes are never generated by the parser; instead, entity references are expanded as encountered. On output, an entity reference node will turn into a "&name;" style reference.

##### Syntax

    Node* createEntityReference(
       oratext* name)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `name`    | name        |

##### Returns

`(Node*)` New entity reference node

#### createProcessingInstruction()

Creates a processing instruction node with the given target and data (which should be in the data encoding). The data may be `NULL`, but the target is required and cannot be changed. The target and data are not verified, converted, or checked. The name of the node is the same as the target. The new node is an orphan with no parent. The target and data are not copied; their pointers are just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createProcessingInstruction(
       oratext* target,
       oratext* data)
    throw (DOMException);

| Parameter | Description       |
|:----------|:------------------|
| `target`  | target            |
| `data`    | data for new node |

##### Returns

`(Node*)` New PI node

#### createTextNode()

Creates a text node with the given initial data (which must be non-`NULL` and in the data encoding). The data may be `NULL`; if provided, it is not verified, converted, checked, or parsed (entities will not be expanded). The name of the node is always "`#text`". The new node is an orphan with no parent. The text data is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

##### Syntax

    Node* createTextNode(
       oratext* data)
    throw (DOMException);

| Parameter | Description            |
|:----------|:-----------------------|
| `data`    | data for new text node |

##### Returns

`(Node*)` new text node

#### getDoctype()

Returns the DTD node associated with this document. After this call, a `DocumentType`Ref object needs to be created with an appropriate constructor in order to call its member functions. The DTD tree cannot be edited.

##### Syntax

    Node* getDoctype() const;

##### Returns

`(Node*)` DTD node

#### getDocumentElement()

Returns the root element (node) of the DOM tree. Each document has only one uppermost Element node, called the root element. If there is no root element, `NULL` is returned. This can happen when the document tree is being constructed.

##### Syntax

    Node* getDocumentElement() const;

##### Returns

`(Node*)` Root element

#### getElementById()

Returns the element node which has the given ID. Throws `NOT_FOUND_ERR` if no element is found. The given ID should be in the data encoding or it might not match.

Note that attributes named "`ID`" are not automatically of type ID; ID attributes (which can have any name) must be declared as type ID in the DTD or XML schema associated with the document.

##### Syntax

    Node* getElementById(
       oratext* elementId);

| Parameter   | Description |
|:------------|:------------|
| `elementId` | element id  |

##### Returns

`(Node*)``Element` node

#### getElementsByTagName()

Returns a list of all elements in the document with a given tag name, in document order (the order in which they would be encountered in a preorder traversal of the tree). The list should be freed by the user when it is no longer needed. The list is not live, it is a snapshot. That is, if a new node which matched the tag name were added to the DOM after the list was returned, the list would not automatically be updated to include the node.

The special name "\*" matches all tag names; a `NULL` name matches nothing. Note that tag names are case sensitive, and should be in the data encoding or a mismatch might occur.

This function is not namespace aware; the full tag names are compared. If two qualified names with two different prefixes both of which map to the same URI are compared, the comparison will fail.

##### Syntax

    NodeList< Node>* getElementsByTagName(
       oratext* tagname) const;

| Parameter | Description |
|:----------|:------------|
| `tagname` | tag name    |

##### Returns

`(NodeList< Node>*)` List of nodes

#### getElementsByTagNameNS()

Returns a list of all elements in the document with a given namespace URI and local name, in document order (the order in which they would be encountered in a preorder traversal of the tree). The list should be freed by the user when it is no longer needed. The list is not live, it is a snapshot. That is, if a new node which matches the URI and local name were added to the DOM after the list was returned, the list would not automatically be updated to include the node.

The URI and local name should be in the data encoding. The special name "\*" matches all local names; a `NULL` local name matches nothing. Namespace URIs must always match, however, no wildcard is allowed. Note that comparisons are case sensitive.

##### Syntax

    NodeList< Node>* getElementsByTagNameNS(
       oratext* namespaceURI,
       oratext* localName);

| Parameter      | Description            |
|:---------------|:-----------------------|
| `namespaceURI` | namespace URI to match |
| `localName`    | local name to match    |

##### Returns

`(NodeList< Node>*)` List of nodes

#### getImplementation()

Returns DOMImplementation object that was used to create this document. When the DOMImplementation object is destructed, all document trees associated with it are also destructed.

##### Syntax

    DOMImplementation< Node>* getImplementation() const;

##### Returns

`(DOMImplementation)` DOMImplementation reference object

#### importNode()

Imports a node from one Document to another. The new node is an orphan and has no parent. The original node is not modified in any way or removed from its document; instead, a new node is created with copies of all the original node's qualified name, prefix, namespace URI, and local name.

The `deep` parameter controls whether the children of the node are recursively imported. If `FALSE`, only the node itself is imported, and it will have no children. If `TRUE`, all descendents of the node will be imported as well, and an entire new subtree created. Elements will have only their specified attributes imported; non-specified (default) attributes are omitted. New default attributes (for the destination document) are then added. Document and `DocumentType` nodes cannot be imported.

##### Syntax

    Node* importNode(
       NodeRef< Node>& importedNode,
       boolean deep) const
    throw (DOMException);

| Parameter      | Description                                     |
|:---------------|:------------------------------------------------|
| `importedNode` | node to import                                  |
| `deep`         | indicator for recursively importing the subtree |

##### Returns

`(Node*)` New imported node

#### ~DocumentRef()

This is the default destructor. It cleans the reference to the node. If the document node is marked for deletion, the destructor deletes the node and the tree under it. It is always deep deletion in the case of a document node. The destructor can be called by the environment or by the user directly.

##### Syntax

    ~DocumentRef();

### DocumentTraversal Interface

Table 3-12 summarizes the methods available through DocumentTraversal interface.

Table 3-12 Summary of DocumentTraversal Methods; Dom Package

| Function              | Summary                           |
|:----------------------|:----------------------------------|
| DocumentTraversal()   | Constructor.                      |
| createNodeIterator()  | Create new `NodeIterator` object. |
| createTreeWalker()    | Create new `TreeWalker` object.   |
| destroyNodeIterator() | Destroys `NodeIterator` object.   |
| destroyTreeWalker()   | Destroys `TreeWalker` object.     |
| ~DocumentTraversal()  | Default destructor.               |

#### DocumentTraversal()

Constructs the factory.

##### Syntax

    DocumentTraversal();

##### Returns

`(DocumentTraversal)` new factory object

#### createNodeIterator()

Create new iterator object.

##### Syntax

    NodeIterator< Node>* createNodeIterator(
       NodeRef< Node>& root,
       WhatToShowCode whatToShow,
       boolean entityReferenceExpansion)
    throw (DOMException);

| Parameter                  | Description                         |
|:---------------------------|:------------------------------------|
| `root`                     | root of subtree, for iteration      |
| `whatToShow`               | node types filter                   |
| `entityReferenceExpansion` | if `TRUE`, expand entity references |

##### Returns

`(NodeIterator*)` Pointer to new iterator

#### createTreeWalker()

Create new `TreeWalker` object.

##### Syntax

    TreeWalker< Node>* createTreeWalker(
       NodeRef< Node>& root,
       WhatToShowCode whatToShow,
       boolean entityReferenceExpansion)
    throw (DOMException);

| Parameter                  | Description                         |
|:---------------------------|:------------------------------------|
| `root`                     | root of subtree, for traversal      |
| `whatToShow`               | node types filter                   |
| `entityReferenceExpansion` | if `TRUE`, expand entity references |

##### Returns

`(TreeWalker*)` Pointer to new tree walker

#### destroyNodeIterator()

Destroys node iterator object.

##### Syntax

    void destroyNodeIterator(
       NodeIterator< Node>* iter)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `iter`    | iterator    |

#### destroyTreeWalker()

Destroys `TreeWalker` object.

##### Syntax

    void destroyTreeWalker(
       TreeWalker< Node>* walker)
    throw (DOMException);

| Parameter | Description  |
|:----------|:-------------|
| `walker`  | `TreeWalker` |

#### ~DocumentTraversal()

Default destructor.

##### Syntax

    ~DocumentTraversal();

### DocumentTypeRef Interface

Table 3-13 summarizes the methods available through DocumentTypeRef interface.

Table 3-13 Summary of DocumentTypeRef Methods; Dom Package

| Function            | Summary                    |
|:--------------------|:---------------------------|
| DocumentTypeRef()   | Constructor.               |
| getEntities()       | Get DTD's entities.        |
| getInternalSubset() | Get DTD's internal subset. |
| getName()           | Get name of DTD.           |
| getNotations()      | Get DTD's notations.       |
| getPublicId()       | Get DTD's public ID.       |
| getSystemId()       | Get DTD's system ID.       |
| ~DocumentTypeRef()  | Public default destructor. |

#### DocumentTypeRef()

This is a constructor.

| Syntax                                                                          | Description          |
|:--------------------------------------------------------------------------------|:---------------------|
| `DocumentTypeRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Default constructor. |
| `DocumentTypeRef(`<br>`   const DocumentTypeRef< Node>& node_ref);`             | Copy constructor.    |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(DocumentTypeRef)` `Node` reference object

#### getEntities()

Returns a named node map of general entities defined by the DTD.

##### Syntax

    NamedNodeMap< Node>* getEntities() const;

##### Returns

`(NamedNodeMap< Node>*)` map containing entities

#### getInternalSubset()

Returns the content model for an element. If there is no DTD, returns `NULL`.

##### Syntax

    Node* getInternalSubset(
       oratext* name);

| Parameter | Description     |
|:----------|:----------------|
| `name`    | name of element |

##### Returns

`(xmlnode*)` content model subtree

#### getName()

Returns DTD's name (specified immediately after the `DOCTYPE` keyword)

##### Syntax

    oratext* getName() const;

##### Returns

`(oratext*)` name of DTD

#### getNotations()

Returns a named node map of notations declared by the DTD.

##### Syntax

    NamedNodeMap< Node>* getNotations() const;

##### Returns

`(NamedNodeMap< Node>*)` map containing notations

#### getPublicId()

Returns DTD's public identifier

##### Syntax

    oratext* getPublicId() const;

##### Returns

`(oratext*)` DTD's public identifier

#### getSystemId()

Returns DTD's system identifier

##### Syntax

    oratext* getSystemId() const;

##### Returns

`(oratext*)` DTD's system identifier

#### ~DocumentTypeRef()

This is the default destructor.

##### Syntax

    ~DocumentTypeRef();

### ElementRef Interface

Table 3-14 summarizes the methods available through `ElementRef` interface.

Table 3-14 Summary of ElementRef Methods; Dom Package

| Function               | Summary                                                    |
|:-----------------------|:-----------------------------------------------------------|
| ElementRef()           | Constructor.                                               |
| getAttribute()         | Get attribute's value given its name.                      |
| getAttributeNS()       | Get attribute's value given its URI and local name.        |
| getAttributeNode()     | Get the attribute node given its name.                     |
| getElementsByTagName() | Get elements with given tag name.                          |
| getTagName()           | Get element's tag name.                                    |
| hasAttribute()         | Check if named attribute exists.                           |
| hasAttributeNS()       | Check if named attribute exists (namespace aware version). |
| removeAttribute()      | Remove attribute with specified name.                      |
| removeAttributeNS()    | Remove attribute with specified URI and local name.        |
| removeAttributeNode()  | Remove attribute node                                      |
| setAttribute()         | Set new attribute for this element and/or new value.       |
| setAttributeNS()       | Set new attribute for the element and/or new value.        |
| setAttributeNode()     | Set attribute node.                                        |
| ~ElementRef()          | Public default destructor.                                 |

#### ElementRef()

Class constructor.

| Syntax                                                                     | Description                                                                      |
|:---------------------------------------------------------------------------|:---------------------------------------------------------------------------------|
| `ElementRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given element node after a call to createElement. |
| `ElementRef(`<br>`   const ElementRef< Node>& node_ref);`                  | Copy constructor.                                                                |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(ElementRef)` `Node` reference object

#### getAttribute()

Returns the value of an element's attribute (specified by name). Note that an attribute may have the empty string as its value, but cannot be `NULL`.

##### Syntax

    oratext* getAttribute(
       oratext* name) const;

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | name of attribute (data encoding) |

##### Returns

`(oratext*)` named attribute's value (in data encoding)

#### getAttributeNS()

Returns the value of an element's attribute (specified by URI and local name). Note that an attribute may have the empty string as its value, but cannot be `NULL`.

##### Syntax

    oratext* getAttributeNS(
       oratext* namespaceURI,
       oratext* localName);

| Parameter      | Description                                |
|:---------------|:-------------------------------------------|
| `namespaceURI` | namespace URI of attribute (data encoding) |
| `localName`    | local name of attribute (data encoding)    |

##### Returns

`(oratext *)` named attribute's value (in data encoding)

#### getAttributeNode()

Returns the attribute node given its name.

##### Syntax

    Node* getAttributeNode(
       oratext* name) const;

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | name of attribute (data encoding) |

##### Returns

`(Node*)` the attribute node

#### getElementsByTagName()

Returns a list of all elements with a given tag name, in the order in which they would be encountered in a preorder traversal of the subtree. The tag name should be in the data encoding. The special name "`*`" matches all tag names; a `NULL` name matches nothing. Tag names are case sensitive. This function is not namespace aware; the full tag names are compared. The returned list should be freed by the user.

##### Syntax

    NodeList< Node>* getElementsByTagName(
       oratext* name);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | tag name to match (data encoding) |

##### Returns

`(NodeList< Node>*)` the list of elements

#### getTagName()

Returns the tag name of an element node which is supposed to have the same value as the node name from the node interface

##### Syntax

    oratext* getTagName() const;

##### Returns

`(oratext*)` element's name \[in data encoding\]

#### hasAttribute()

Determines if an element has a attribute with the given name

##### Syntax

    boolean hasAttribute(
       oratext* name);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | name of attribute (data encoding) |

##### Returns

`(boolean)` `TRUE` if element has attribute with given name

#### hasAttributeNS()

Determines if an element has a attribute with the given URI and local name

##### Syntax

    boolean hasAttributeNS(
       oratext* namespaceURI,
       oratext* localName);

| Parameter      | Description                                |
|:---------------|:-------------------------------------------|
| `namespaceURI` | namespace URI of attribute (data encoding) |
| `localName`    | local name of attribute (data encoding)    |

##### Returns

`(boolean)` `TRUE` if element has such attribute

#### removeAttribute()

Removes an attribute specified by name. The attribute is removed from the element's list of attributes, but the attribute node itself is not destroyed.

##### Syntax

    void removeAttribute(
       oratext* name) throw (DOMException);

| Parameter | Description                       |
|:----------|:----------------------------------|
| `name`    | name of attribute (data encoding) |

#### removeAttributeNS()

Removes an attribute specified by URI and local name. The attribute is removed from the element's list of attributes, but the attribute node itself is not destroyed.

##### Syntax

    void removeAttributeNS(
       oratext* namespaceURI,
       oratext* localName)
    throw (DOMException);

| Parameter      | Description                                |
|:---------------|:-------------------------------------------|
| `namespaceURI` | namespace URI of attribute (data encoding) |
| `localName`    | local name of attribute (data encoding)    |

#### removeAttributeNode()

Removes an attribute from an element. Returns a pointer to the removed attribute or `NULL`

##### Syntax

    Node* removeAttributeNode(
       AttrRef< Node>& oldAttr)
    throw (DOMException);

| Parameter | Description        |
|:----------|:-------------------|
| `oldAttr` | old attribute node |

##### Returns

`(Node*)` the attribute node (old) or `NULL`

#### setAttribute()

Creates a new attribute for an element with the given name and value (which should be in the data encoding). If the named attribute already exists, its value is simply replaced. The name and value are not verified, converted, or checked. The value is not parsed, so entity references will not be expanded.

##### Syntax

    void setAttribute(
       oratext* name,
       oratext* value)
    throw (DOMException);

| Parameter | Description                        |
|:----------|:-----------------------------------|
| `name`    | names of attribute (data encoding) |
| `value`   | value of attribute (data encoding) |

#### setAttributeNS()

Creates a new attribute for an element with the given URI, local name and value (which should be in the data encoding). If the named attribute already exists, its value is simply replaced. The name and value are not verified, converted, or checked. The value is not parsed, so entity references will not be expanded.

##### Syntax

    void setAttributeNS(
       oratext* namespaceURI,
       oratext* qualifiedName,
       oratext* value)
    throw (DOMException);

| Parameter       | Description                                |
|:----------------|:-------------------------------------------|
| `namespaceURI`  | namespace URI of attribute (data encoding) |
| `qualifiedName` | qualified name of attribute(data encoding) |
| `value`         | value of attribute(data encoding)          |

#### setAttributeNode()

Adds a new attribute to an element. If an attribute with the given name already exists, it is replaced and a pointer to the old attribute returned. If the attribute is new, it is added to the element's list and a pointer to the new attribute is returned.

##### Syntax

    Node* setAttributeNode(
       AttrRef< Node>& newAttr)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `newAttr` | new node    |

##### Returns

`(Node*)` the attribute node (old or new)

#### ~ElementRef()

This is the default destructor.

##### Syntax

    ~ElementRef();

### EntityRef Interface

Table 3-15 summarizes the methods available through `EntityRef` interface.

Table 3-15 Summary of EntityRef Methods; Dom Package

| Function                           | Summary                    |
|:-----------------------------------|:---------------------------|
| EntityRef()EntityRef()             | Constructor.               |
| getNotationName()getNotationName() | Get entity's notation.     |
| getPublicId()getPublicId()         | Get entity's public ID.    |
| getSystemId()getSystemId()         | Get entity's system ID.    |
| getType()getType()                 | Get entity's type.         |
| ~EntityRef()~EntityRef()           | Public default destructor. |

#### EntityRef()

Class constructor.

| Syntax                                                                    | Description                                                                       |
|:--------------------------------------------------------------------------|:----------------------------------------------------------------------------------|
| `EntityRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given entity node after a call to create `Entity`. |
| `EntityRef(`<br>`   const EntityRef< Node>& nref);`                       | Copy constructor.                                                                 |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(EntityRef)` `Node` reference object

#### getNotationName()

For unparsed entities, returns the name of its notation (in the data encoding). For parsed entities and other node types, returns `NULL`.

##### Syntax

    oratext* getNotationName() const;

##### Returns

`(oratext*)` entity's notation

#### getPublicId()

Returns an entity's public identifier (in the data encoding).

##### Syntax

    oratext* getPublicId() const;

##### Returns

`(oratext*)` entity's public identifier

#### getSystemId()

Returns an entity's system identifier (in the data encoding).

##### Syntax

    oratext* getSystemId() const;

##### Returns

`(oratext*)` entity's system identifier

#### getType()

Returns a boolean for an entity describing whether it is general (`TRUE`) or parameter (`FALSE`).

##### Syntax

    boolean getType() const;

##### Returns

`(boolean)` `TRUE` for general entity, `FALSE` for parameter entity

#### ~EntityRef()

This is the default destructor.

##### Syntax

    ~EntityRef();

### EntityReferenceRef Interface

Table 3-16 summarizes the methods available through `EntityReferenceRef` interface.

Table 3-16 Summary of EntityReferenceRef Methods; Dom Package

| Function              | Summary                    |
|:----------------------|:---------------------------|
| EntityReferenceRef()  | Constructor.               |
| ~EntityReferenceRef() | Public default destructor. |

#### EntityReferenceRef()

Class constructor.

| Syntax                                                                             | Description                                                                                          |
|:-----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| `EntityReferenceRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given entity reference node after a call to create `EntityReference`. |
| `EntityReferenceRef(`<br>`   const EntityReferenceRef< Node>& nref);`              | Copy constructor.                                                                                    |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(EntityReferenceRef)` `Node` reference object

#### ~EntityReferenceRef()

This is the default destructor.

##### Syntax

    ~EntityReferenceRef();

### NamedNodeMapRef Interface

Table 3-17 summarizes the methods available through `NamedNodeMapRef` interface.

Table 3-17 Summary of NamedNodeMapRef Methods; Dom Package

| Function            | Summary                                          |
|:--------------------|:-------------------------------------------------|
| NamedNodeMapRef()   | Constructor                                      |
| getLength()         | Get map's length                                 |
| getNamedItem()      | Get item given its name                          |
| getNamedItemNS()    | Get item given its namespace URI and local name. |
| item()              | Get item given its index.                        |
| removeNamedItem()   | Remove an item given its name.                   |
| removeNamedItemNS() | Remove the item from the map.                    |
| setNamedItem()      | Add new item to the map.                         |
| setNamedItemNS()    | Set named item to the map.                       |
| ~NamedNodeMapRef()  | Default destructor.                              |

#### NamedNodeMapRef()

Class constructor.

| Syntax                                                                                         | Description                                               |
|:-----------------------------------------------------------------------------------------------|:----------------------------------------------------------|
| `NamedNodeMapRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   NamedNodeMap< Node>* mptr);` | Used to create references to a given `NamedNodeMap` node. |
| `NamedNodeMapRef(`<br>`   const NamedNodeMapRef< Node>& mref);`                                | Copy constructor.                                         |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(NamedNodeMapRef)` `Node` reference object

#### getLength()

Get the length of the map.

##### Syntax

    ub4 getLength() const;

##### Returns

`(ub4)` map's length

#### getNamedItem()

Get the name of the item, given its name.

##### Syntax

    Node* getNamedItem( oratext* name) const;

| Parameter | Description  |
|:----------|:-------------|
| `name`    | name of item |

##### Returns

`(Node*)` pointer to the item

#### getNamedItemNS()

Get the name of the item, given its namespace URI and local name.

##### Syntax

    Node* getNamedItemNS(
       oratext* namespaceURI,
       oratext* localName) const;

| Parameter      | Description           |
|:---------------|:----------------------|
| `namespaceURI` | namespace URI of item |
| `localName`    | local name of item    |

##### Returns

`(Node*)` pointer to the item

#### item()

Get item, given its index.

##### Syntax

    Node* item(
       ub4 index) const;

| Parameter | Description   |
|:----------|:--------------|
| `index`   | index of item |

##### Returns

`(Node*)` pointer to the item

#### removeNamedItem()

Remove the item from the map, given its name.

##### Syntax

    Node* removeNamedItem(
       oratext* name)
    throw (DOMException);

| Parameter | Description  |
|:----------|:-------------|
| `name`    | name of item |

##### Returns

`(Node*)` pointer to the removed item

#### removeNamedItemNS()

Remove the item from the map, given its namespace URI and local name.

##### Syntax

    Node* removeNamedItemNS(
       oratext* namespaceURI,
       oratext* localName)
    throw (DOMException);

| Parameter      | Description           |
|:---------------|:----------------------|
| `namespaceURI` | namespace URI of item |
| `localName`    | local name of item    |

##### Returns

`(Node*)` pointer to the removed item

#### setNamedItem()

Add new item to the map.

##### Syntax

    Node* setNamedItem(
       NodeRef< Node>& newItem)
    throw (DOMException);

| Parameter | Description         |
|:----------|:--------------------|
| `newItem` | item set to the map |

##### Returns

`(Node*)` pointer to new item

#### setNamedItemNS()

Set named item, which is namespace aware, to the map.

##### Syntax

    Node* setNamedItemNS(
       NodeRef< Node>& newItem)
    throw (DOMException);

| Parameter | Description         |
|:----------|:--------------------|
| `newItem` | item set to the map |

##### Returns

`(Node*)` pointer to the item

#### ~NamedNodeMapRef()

Default destructor.

##### Syntax

    ~NamedNodeMapRef();

### NodeFilter Interface

Table 3-18 summarizes the methods available through NodeFilter interface.

Table 3-18 Summary of NodeFilter Methods; Dom Package

| Function                 | Summary                                               |
|:-------------------------|:------------------------------------------------------|
| acceptNode()acceptNode() | Execute it for a given node and use its return value. |

#### acceptNode()

This function is used as a test by NodeIterator and `TreeWalker`.

##### Syntax

    template< typename Node> AcceptNodeCode AcceptNode(
       NodeRef< Node>& nref);

| Parameter | Description                         |
|:----------|:------------------------------------|
| `nref`    | reference to the node to be tested. |

##### Returns

`(AcceptNodeCode)` result returned by the filter function

### NodeIterator Interface

Table 3-19 summarizes the methods available through `NodeIterator` interface.

Table 3-19 Summary of NodeIterator Methods; Dom Package

| Function       | Summary                                      |
|:---------------|:---------------------------------------------|
| adjustCtx()    | Attach this iterator to the another context. |
| detach()       | Invalidate the iterator.                     |
| nextNode()     | Go to the next node.                         |
| previousNode() | Go to the previous node.                     |

#### adjustCtx()

Attaches this iterator to the context associated with a given node reference

##### Syntax

    void adjustCtx(
       NodeRef< Node>& nref);

| Parameter | Description    |
|:----------|:---------------|
| `nref`    | reference node |

#### detach()

Invalidates the iterator.

##### Syntax

    void detach();

#### nextNode()

Go to the next node.

##### Syntax

    Node* nextNode() throw (DOMException);

##### Returns

`(Node*)` pointer to the next node

#### previousNode()

Go to the previous node.

##### Syntax

    Node* previousNode() throw (DOMException);

##### Returns

`(Node*)` pointer to the previous node

### NodeListRef Interface

Table 3-20 summarizes the methods available through NodeListRef interface.

Table 3-20 Summary of NodeListRef Methods; Dom Package

| Function       | Summary                   |
|:---------------|:--------------------------|
| NodeListRef()  | Constructor.              |
| getLength()    | Get list's length.        |
| item()         | Get item given its index. |
| ~NodeListRef() | Default destructor.       |

#### NodeListRef()

Class constructor.

| Syntax                                                                                 | Description                                           |
|:---------------------------------------------------------------------------------------|:------------------------------------------------------|
| `NodeListRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   NodeList< Node>* lptr);` | Used to create references to a given `NodeList` node. |
| `NodeListRef(`<br>`   const NodeListRef< Node>& lref);`                                | Copy constructor.                                     |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `lptr`     | referenced list                  |

##### Returns

`(NodeListRef)` `Node` reference object

#### getLength()

Get the length of the list.

##### Syntax

    ub4 getLength() const;

##### Returns

`(ub4)` list's length

#### item()

Get the item, given its index.

##### Syntax

    Node* item(
       ub4 index) const;

| Parameter | Description   |
|:----------|:--------------|
| `index`   | index of item |

##### Returns

`(Node*)` pointer to the item

#### ~NodeListRef()

Destructs the object.

##### Syntax

    ~NodeListRef();

### NodeRef Interface

Table 3-21 summarizes the methods available through `NodeRef` interface.

Table 3-21 Summary of NodeRef Methods; Dom Package

| Function             | Summary                                                        |
|:---------------------|:---------------------------------------------------------------|
| NodeRef()            | Constructor.                                                   |
| appendChild()        | Append new child to node's list of children.                   |
| cloneNode()          | Clone this node.                                               |
| getAttributes()      | Get attributes of this node.                                   |
| getChildNodes()      | Get children of this node.                                     |
| getFirstChild()      | Get the first child node of this node.                         |
| getLastChild()       | Get the last child node of this node.                          |
| getLocalName()       | Get local name of this node.                                   |
| getNamespaceURI()    | Get namespace URI of this node as a `NULL`-terminated string.  |
| getNextSibling()     | Get the next sibling node of this node.                        |
| getNoMod()           | Tests if no modifications are allowed for this node.           |
| getNodeName()        | Get node's name as `NULL`-terminated string.                   |
| getNodeType()        | Get DOMNodeType of the node.                                   |
| getNodeValue()       | Get node's value as `NULL`-terminated string.                  |
| getOwnerDocument()   | Get the owner document of this node.                           |
| getParentNode()      | Get parent node of this node.                                  |
| getPrefix()          | Get namespace prefix of this node.                             |
| getPreviousSibling() | Get the previous sibling node of this node.                    |
| hasAttributes()      | Tests if this node has attributes.                             |
| hasChildNodes()      | Test if this node has children.                                |
| insertBefore()       | Insert new child into node's list of children.                 |
| isSupported()        | Tests if specified feature is supported by the implementation. |
| markToDelete()       | Sets the mark to delete the referenced node.                   |
| normalize()          | Merge adjacent text nodes.                                     |
| removeChild()        | Remove an existing child node.                                 |
| replaceChild()       | Replace an existing child of a node.                           |
| resetNode()          | Reset NodeRef to reference another node.                       |
| setNodeValue()       | Set node's value as `NULL`-terminated string.                  |
| setPrefix()          | Set namespace prefix of this node.                             |
| ~NodeRef()           | Public default destructor.                                     |

#### NodeRef()

Class constructor.

| Syntax                                                              | Description                                                                                                                                                                          |
|:--------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NodeRef(`<br>`   const NodeRef< Node>& nref,`<br>`   Node* nptr);` | Used to create references to a given node when at least one reference to this node or another node is already available. The node deletion flag is not copied and is set to `FALSE`. |
| `NodeRef(`<br>`   const NodeRef< Node>& nref);`                     | Copy constructor. Used to create additional references to the node when at least one reference is already available. The node deletion flag is not copied and is set to `FALSE`.     |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(NodeRef)` `Node` reference object

#### appendChild()

Appends the node to the end of this node's list of children and returns the new node. If `newChild` is a `DocumentFragment`, all of its children are appended in original order; the `DocumentFragment` node itself is not. If `newChild` is already in the DOM tree, it is first removed from its current position.

##### Syntax

    Node* appendChild(
       NodeRef& newChild)
    throw (DOMException);

| Parameter  | Description    |
|:-----------|:---------------|
| `newChild` | reference node |

##### Returns

`(Node*)` the node appended

#### cloneNode()

Creates and returns a duplicate of this node. The duplicate node has no parent. Cloning an Element copies all attributes and their values, including those generated by the XML processor to represent defaulted attributes, but it does not copy any text it contains unless it is a deep clone, since the text is contained in a child `Text` node. Cloning any other type of node simply returns a copy of the node. If deep is `TRUE`, all children of the node are recursively cloned, and the cloned node will have cloned children; a non-deep clone will have no children. If the cloned node is not inserted into another tree or fragment, it probably should be marked, through its reference, for deletion (by the user).

##### Syntax

    Node* cloneNode(
       boolean deep);

| Parameter | Description                                                                                             |
|:----------|:--------------------------------------------------------------------------------------------------------|
| `deep`    | whether to clone the entire node hierarchy beneath the node (`TRUE`), or just the node itself (`FALSE`) |

##### Returns

`(Node*)` duplicate (cloned) node

#### getAttributes()

Returns `NamedNodeMap` of attributes of this node, or `NULL` if it has no attributes. Only element nodes can have attribute nodes. For other node kinds, `NULL` is always returned. In the current implementation, the node map of child nodes is live; all changes in the original node are reflected immediately. Because of this, side effects can be present for some DOM tree manipulation styles, in particular, in multithreaded environments.

##### Syntax

    NamedNodeMap< Node>* getAttributes() const;

##### Returns

`(NamedNodeMap*)` `NamedNodeMap` of attributes

#### getChildNodes()

Returns the list of child nodes, or `NULL` if this node has no children. Only Element, Document, DTD, and DocumentFragment nodes may have children; all other types will return `NULL`. In the current implementation, the list of child nodes is live; all changes in the original node are reflected immediately. Because of this, side effects can be present for some DOM tree manipulation styles, in particular, in multithreaded environments.

##### Syntax

    NodeList< Node>* getChildNodes() const;

##### Returns

`(NodeList*)` the list of child nodes

#### getFirstChild()

Returns the first child node, or `NULL`, if this node has no children

##### Syntax

    Node* getFirstChild() const;

##### Returns

`(Node*)` the first child node, or `NULL`

#### getLastChild()

Returns the last child node, or `NULL`, if this node has no children

##### Syntax

    Node* getLastChild() const;

##### Returns

`(Node*)` the last child node, or `NULL`

#### getLocalName()

Returns local name (local part of the qualified name) of this node (in the data encoding) as a `NULL`-terminated string. If this node's name is not fully qualified (has no prefix), then the local name is the same as the name.

##### Syntax

    oratext* getLocalName() const;

##### Returns

`(oratext*)` local name of this node

#### getNamespaceURI()

Returns the namespace URI of this node (in the data encoding) as a `NULL`-terminated string. If the node's name is not qualified (does not contain a namespace prefix), it will have the default namespace in effect when the node was created (which may be `NULL`).

##### Syntax

    oratext* getNamespaceURI() const;

##### Returns

`(oratext*)` namespace URI of this node

#### getNextSibling()

Returns the next sibling node, or `NULL`, if this node has no next sibling

##### Syntax

    Node* getNextSibling() const;

##### Returns

`(Node*)` the next sibling node, or `NULL`

#### getNoMod()

Tests if no modifications are allowed for this node and the DOM tree it belongs to. This member function is Oracle extension.

##### Syntax

    boolean getNoMod() const;

##### Returns

`(boolean)` `TRUE` if no modifications are allowed

#### getNodeName()

Returns the (fully-qualified) name of the node (in the data encoding) as a `NULL`-terminated string, for example "bar\0" or "foo:bar\0". Some node kinds have fixed names: "`#text`", "`#cdata-section`", "`#comment`", "`#document`", "`#document-fragment`". The name of a node cannot changed once it is created.

##### Syntax

    oratext* getNodeName() const;

##### Returns

`(oratext*)` name of node in data encoding

#### getNodeType()

Returns DOMNodeType of the node

##### Syntax

    DOMNodeType getNodeType() const;

##### Returns

`(DOMNodeType)` of the node

#### getNodeValue()

Returns the "value" (associated character data) for a node as a `NULL`-terminated string. Character and general entities will have been replaced. Only `Attr`, `CDATA`, `Comment`, `ProcessingInstruction` and `Text` nodes have values, all other node types have `NULL` value.

##### Syntax

    oratext* getNodeValue() const;

##### Returns

`(oratext *)` value of node

#### getOwnerDocument()

Returns the document node associated with this node. It is assumed that the document node type is derived from the node type. Each node may belong to only one document, or may not be associated with any document at all, such as immediately after it was created on user's request. The "owning" document \[node\] is returned, or the WRONG_DOCUMENT_ERR exception is thrown.

##### Syntax

    Node* getOwnerDocument() const throw (DOMException);

##### Returns

`(Node*)` the owning document node

#### getParentNode()

Returns the parent node, or `NULL`, if this node has no parent

##### Syntax

    Node* getParentNode() const;

##### Returns

`(Node*)` the parent node, or `NULL`

#### getPrefix()

Returns the namespace prefix of this node (in the data encoding) (as a `NULL`-terminated string). If this node's name is not fully qualified (has no prefix), `NULL` is returned.

##### Syntax

    oratext* getPrefix() const;

##### Returns

`(oratext*)` namespace prefix of this node

#### getPreviousSibling()

Returns the previous sibling node, or `NULL`, if this node has no previous siblings

##### Syntax

    Node* getPreviousSibling() const;

##### Returns

`(Node*)` the previous sibling node, or `NULL`

#### hasAttributes()

Returns `TRUE` if this node has attributes, if it is an element. Otherwise, it returns `FALSE`. Note that for nodes that are not elements, it always returns `FALSE`.

##### Syntax

    boolean hasAttributes() const;

##### Returns

`(boolean)` `TRUE` is this node is an element and has attributes

#### hasChildNodes()

Tests if this node has children. Only `Element`, `Document`, `DTD`, and `DocumentFragment` nodes may have children.

##### Syntax

    boolean hasChildNodes() const;

##### Returns

`(boolean)` `TRUE` if this node has any children

#### insertBefore()

Inserts the node `newChild` before the existing child node `refChild` in this node. `refChild` must be a child of this node. If` newChild` is a `DocumentFragment`, all of its children are inserted (in the same order) before `refChild`; the `DocumentFragment` node itself is not. If `newChild` is already in the DOM tree, it is first removed from its current position.

##### Syntax

    Node* insertBefore(
       NodeRef& newChild,
       NodeRef& refChild)
    throw (DOMException);

| Parameter  | Description    |
|:-----------|:---------------|
| `newChild` | new node       |
| `refChild` | reference node |

##### Returns

`(Node*)` the node being inserted

#### isSupported()

Tests if the feature, specified by the arguments, is supported by the DOM implementation of this node.

##### Syntax

    boolean isSupported(
       oratext* feature,
       oratext* version) const;

| Parameter | Description             |
|:----------|:------------------------|
| `feature` | package name of feature |
| `version` | version of package      |

##### Returns

`(boolean)` `TRUE` is specified feature is supported

#### markToDelete()

Sets the mark indicating that the referenced node should be deleted at the time when destructor of this reference is called. All other references to the node become invalid. This behavior is inherited by all other reference classes. This member function is Oracle extension.

##### Syntax

    void markToDelete();

#### normalize()

"Normalizes" the subtree rooted at an element, merges adjacent `Text` nodes children of elements. Note that adjacent `Text` nodes will never be created during a normal parse, only after manipulation of the document with DOM calls.

##### Syntax

    void normalize();

#### removeChild()

Removes the node from this node's list of children and returns it. The node is orphaned; its parent will be `NULL` after removal.

##### Syntax

    Node* removeChild(
       NodeRef& oldChild)
    throw (DOMException);

| Parameter  | Description |
|:-----------|:------------|
| `oldChild` | old node    |

##### Returns

`(Node*)` node removed

#### replaceChild()

Replaces the child node `oldChild` with the new node `newChild` in this node's children list, and returns `oldChild` (which is now orphaned, with a `NULL` parent). If `newChild` is a `DocumentFragment`, all of its children are inserted in place of `oldChild`; the `DocumentFragment` node itself is not. If `newChild` is already in the DOM tree, it is first removed from its current position.

##### Syntax

    Node* replaceChild(
       NodeRef& newChild,
       NodeRef& oldChild)
    throw (DOMException);

| Parameter  | Description |
|:-----------|:------------|
| `newChild` | new node    |
| `oldChild` | old node    |

##### Returns

`(Node*)` the node replaced

#### resetNode()

This function resets `NodeRef` to reference `Node` given as an argument

##### Syntax

    void resetNode(
       Node* nptr);

| Parameter | Description    |
|:----------|:---------------|
| `nptr`    | reference node |

#### setNodeValue()

Sets a node's value (character data) as a `NULL`-terminated string. Does not allow setting the value to `NULL`. Only `Attr`, `CDATA`, `Comment`, `ProcessingInstruction`, and `Text` nodes have values. Trying to set the value of another kind of node is a no-op. The new value must be in the data encoding! It is not verified, converted, or checked. The value is not copied, its pointer is just stored. The user is responsible for persistence and freeing of that data.

It throws the `NO_MODIFICATION_ALLOWED_ERR` exception, if no modifications are allowed, or `UNDEFINED_ERR`, with an appropriate Oracle XML error code (see xml.h), in the case of an implementation defined error.

##### Syntax

    void setNodeValue(
       oratext* data)
    throw (DOMException);

| Parameter | Description        |
|:----------|:-------------------|
| `data`    | new value for node |

#### setPrefix()

Sets the namespace prefix of this node (as `NULL`-terminated string). Does not verify the prefix is defined! And does not verify that the prefix is in the current data encoding. Just causes a new qualified name to be formed from the new prefix and the old local name.

It throws the `NO_MODIFICATION_ALLOWED_ERR` exception, if no modifications are allowed. Or it throws `NAMESPACE_ERR` if the `namespaceURI` of this node is `NULL`, or if the specified prefix is "xml" and the namespaceURI of this node is different from "http://www.w3.org/XML/1998/namespace", or if this node is an attribute and the specified prefix is "xmlns" and the namespaceURI of this node is different from "http://www.w3.org/2000/xmlns/". Note that the `INVALID_CHARACTER_ERR` exception is never thrown since it is not checked how the prefix is formed

##### Syntax

    void setPrefix(
       oratext* prefix)
    throw (DOMException);

| Parameter | Description          |
|:----------|:---------------------|
| `prefix`  | new namespace prefix |

#### ~NodeRef()

This is the default destructor. It cleans the reference to the node and, if the node is marked for deletion, deletes the node. If the node was marked for deep deletion, the tree under the node is also deleted (deallocated). It is usually called by the environment. But it can be called by the user directly if necessary.

##### Syntax

    ~NodeRef();

### NotationRef Interface

Table 3-22 summarizes the methods available through `NotationRef` interface.

Table 3-22 Summary of NotationRef Methods; Dom Package

| Function       | Summary                    |
|:---------------|:---------------------------|
| NotationRef()  | Constructor.               |
| getPublicId()  | Get public ID.             |
| getSystemId()  | Get system ID.             |
| ~NotationRef() | Public default destructor. |

#### NotationRef()

Class constructor.

| Syntax                                                                      | Description                                                                           |
|:----------------------------------------------------------------------------|:--------------------------------------------------------------------------------------|
| `NotationRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given notation node after a call to create `Notation`. |
| `NotationRef(`<br>`   const NotationRef< Node>& nref);`                     | Copy constructor.                                                                     |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(NotationRef)` `Node` reference object

#### getPublicId()

Get public id.

##### Syntax

    oratext* getPublicId() const;

##### Returns

`(oratext*)` public ID

#### getSystemId()

Get system id.

##### Syntax

    oratext* getSystemId() const;

##### Returns

`(oratext*)` system ID

#### ~NotationRef()

This is the default destructor.

##### Syntax

    ~NotationRef();

### ProcessingInstructionRef Interface

Table 3-23 summarizes the methods available through `ProcessingInstructionRef` interface.

Table 3-23 Summary of ProcessingInstructionRef Methods; Dom Package

| Function                    | Summary                              |
|:----------------------------|:-------------------------------------|
| ProcessingInstructionRef()  | Constructor.                         |
| getData()                   | Get processing instruction's data.   |
| getTarget()                 | Get processing instruction's target. |
| setData()                   | Set processing instruction's data.   |
| ~ProcessingInstructionRef() | Public default destructor.           |

#### ProcessingInstructionRef()

Class constructor.

| Syntax                                                                                   | Description                                                                                                       |
|:-----------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| `ProcessingInstructionRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given `ProcessingInstruction` node after a call to create` ProcessingInstruction`. |
| `ProcessingInstructionRef(`<br>`   const ProcessingInstructionRef< Node>& nref);`        | Copy constructor.                                                                                                 |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(ProcessingInstructionRef)` `Node` reference object

#### getData()

Returns the content (data) of a processing instruction (in the data encoding). The content is the part from the first non-whitespace character after the target until the ending "`?>`".

##### Syntax

    oratext* getData() const;

##### Returns

`(oratext*)` processing instruction's data

#### getTarget()

Returns a processing instruction's target string. The target is the first token following the markup that begins the `ProcessingInstruction`. All `ProcessingInstruction`s must have a target, though the data part is optional.

##### Syntax

    oratext* getTarget() const;

##### Returns

`(oratext*)` processing instruction's target

#### setData()

Sets processing instruction's data (content), which must be in the data encoding. It is not permitted to set the data to `NULL`. The new data is not verified, converted, or checked.

##### Syntax

    void setData(
       oratext* data)
    throw (DOMException);

| Parameter | Description |
|:----------|:------------|
| `data`    | new data    |

#### ~ProcessingInstructionRef()

This is the default destructor.

##### Syntax

    ~ProcessingInstructionRef();

### Range Interface

Table 3-24 summarizes the methods available through Range interface.

Table 3-24 Summary of Range Methods; Dom Package

| Function                     | Summary                                          |
|:-----------------------------|:-------------------------------------------------|
| CompareBoundaryPoints()      | Compares boundary points.                        |
| cloneContent()               | Makes a clone of the node.                       |
| cloneRange()                 | Clones a range of nodes.                         |
| deleteContents()             | Deletes contents of the node.                    |
| detach()                     | Invalidate the range.                            |
| extractContent()             | Extract the node.                                |
| getCollapsed()               | Check if the range is collapsed.                 |
| getCommonAncestorContainer() | Get the deepest common ancestor node.            |
| getEndContainer()            | Get end container node.                          |
| getEndOffset()               | Get offset of the end point.                     |
| getStartContainer()          | Get start container node.                        |
| getStartOffset()             | Get offset of the start point.                   |
| insertNode()                 | Inserts a node.                                  |
| selectNodeContent()          | Selects node content by its reference.           |
| selectNode()                 | Selects a node.                                  |
| setEnd()                     | Set end point.                                   |
| setEndAfter()                | Sets the end pointer after a specified node.     |
| setEndBefore()               | Set the end before a specified node.             |
| setStart()                   | Set start point.                                 |
| setStartAfter()              | Sets start pointer after a specified node.       |
| setStartBefore()             | Sets start pointer before a specified node.      |
| surroundContents()           | Makes a node into a child of the specified node. |
| toString()                   | Converts an item into a string.                  |

#### CompareBoundaryPoints()

Compares boundary points.

##### Syntax

    CompareHowCode compareBoundaryPoints(
       unsigned short how,
       Range< Node>* sourceRange)
    throw (DOMException);

| Parameter     | Description         |
|:--------------|:--------------------|
| `how`         | how to compare      |
| `sourceRange` | range of comparison |

##### Returns

`(CompareHowCode)` result of comparison

#### cloneContent()

Makes a clone of the node, including its children.

##### Syntax

    Node* cloneContents() throw (DOMException);

##### Returns

`(Node*)` subtree cloned

#### cloneRange()

Clones a range of nodes.

##### Syntax

    Range< Node>* cloneRange();

##### Returns

`(Range< Node>*)` new cloned range

#### deleteContents()

Deletes contents of the node.

##### Syntax

    void deleteContents() throw (DOMException);

#### detach()

Invalidates the range. It is not recommended to use this method since it leaves the object in invalid state. The preferable way is to call the destructor.

##### Syntax

    void detach();

#### extractContent()

Extract the node.

##### Syntax

    Node* extractContents() throw (DOMException);

##### Returns

`(Node*)` subtree extracted

#### getCollapsed()

Checks if the range is collapsed.

##### Syntax

    boolean getCollapsed() const;

##### Returns

`(boolean)` `TRUE` if the range is collapsed, `FALSE` otherwise

#### getCommonAncestorContainer()

Get the deepest common ancestor of the node.

##### Syntax

    Node* getCommonAncestorContainer() const;

##### Returns

`(Node*)` common ancestor node

#### getEndContainer()

Gets the container node.

##### Syntax

    Node* getEndContainer() const;

##### Returns

`(Node*)` end container node

#### getEndOffset()

Get offset of the end point.

##### Syntax

    long getEndOffset() const;

##### Returns

`(long)` offset

#### getStartContainer()

Get start container node.

##### Syntax

    Node* getStartContainer() const;

##### Returns

`(Node*)` start container node

#### getStartOffset()

Get offset of the start point.

##### Syntax

    long getStartOffset() const;

##### Returns

`(long)` offset

#### insertNode()

Inserts a node.

##### Syntax

    void insertNode(
       NodeRef< Node>& newNode)
    throw (RangeException, DOMException);

| Parameter | Description   |
|:----------|:--------------|
| `newNode` | inserted node |

#### selectNodeContent()

Selects node content by its reference.

##### Syntax

    void selectNodeContent(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### selectNode()

Selects a node.

##### Syntax

    void selectNode(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### setEnd()

Sets an end point.

##### Syntax

    void setEnd(
       NodeRef< Node>& refNode,
       long offset)
    throw (RangeException, DOMException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |
| `offset`  | offset         |

#### setEndAfter()

Sets the end pointer after a specified node.

##### Syntax

    void setEndAfter(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### setEndBefore()

Set the end before a specified node.

##### Syntax

    void setEndBefore(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### setStart()

Sets start point.

##### Syntax

    void setStart(
       NodeRef< Node>& refNode,
       long offset)
    throw (RangeException, DOMException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |
| `offset`  | offset         |

#### setStartAfter()

Sets start pointer after a specified node.

##### Syntax

    void setStartAfter(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### setStartBefore()

Sets start pointer before a specified node.

##### Syntax

    void setStartBefore(
       NodeRef< Node>& refNode)
    throw (RangeException);

| Parameter | Description    |
|:----------|:---------------|
| `refNode` | reference node |

#### surroundContents()

Makes a node into a child of the specified node.

##### Syntax

    void surroundContents(
       NodeRef< Node>& newParent)
    throw (RangeException, DOMException);

| Parameter   | Description |
|:------------|:------------|
| `newParent` | parent node |

#### toString()

Converts an item into a string.

##### Syntax

    oratext* toString();

##### Returns

`(oratext*)` string representation of the range

### RangeException Interface

Table 3-25 summarizes the methods available through `RangeException` interface.

Table 3-25 Summary of RangeException Methods; Dom Package

| Function       | Summary                                              |
|:---------------|:-----------------------------------------------------|
| getCode()      | Get Oracle XML error code embedded in the exception. |
| getMesLang()   | Get current language (encoding) of error messages.   |
| getMessage()   | Get Oracle XML error message.                        |
| getRangeCode() | Get Range exception code embedded in the exception.  |

#### getCode()

Gets Oracle XML error code embedded in the exception. Virtual member function inherited from `XmlException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (0 on success)

#### getMesLang()

Gets the current language encoding of error messages. Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext*)` Current language (encoding) of error messages

#### getMessage()

Get XML error message. Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message

#### getRangeCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning Range exception codes, defined in `RangeExceptionCode`, of the exceptional situations during execution.

##### Syntax

    virtual RangeExceptionCode getRangeCode() const = 0;

##### Returns

`(RangeExceptionCode)` exception code

### TextRef Interface

Table 3-26 summarizes the methods available through `TextRef` interface.

Table 3-26 Summary of TextRef Methods; Dom Package

| Function    | Summary                    |
|:------------|:---------------------------|
| TextRef()   | Constructor.               |
| splitText() | Split text node into two.  |
| ~TextRef()  | Public default destructor. |

#### TextRef()

Class constructor.

| Syntax                                                                  | Description                                                                  |
|:------------------------------------------------------------------------|:-----------------------------------------------------------------------------|
| `TextRef(`<br>`   const NodeRef< Node>& node_ref,`<br>`   Node* nptr);` | Used to create references to a given text node after a call to `createtext`. |
| `TextRef(`<br>`   const TextRef< Node>& nref);`                         | Copy constructor.                                                            |

| Parameter  | Description                      |
|:-----------|:---------------------------------|
| `node_ref` | reference to provide the context |
| `nptr`     | referenced node                  |

##### Returns

`(TextRef)` `Node` reference object

#### splitText()

Splits a single text node into two text nodes; the original data is split between them. The offset is zero-based, and is in characters, not bytes. The original node is retained, its data is just truncated. A new text node is created which contains the remainder of the original data, and is inserted as the next sibling of the original. The new text node is returned.

##### Syntax

    Node* splitText(
       ub4 offset)
    throw (DOMException);

| Parameter | Description                          |
|:----------|:-------------------------------------|
| `offset`  | character offset where to split text |

##### Returns

`(Node*)` new node

#### ~TextRef()

This is the default destructor.

##### Syntax

    ~TextRef();

### TreeWalker Interface

Table 3-27 summarizes the methods available through `TreeWalker` interface.

Table 3-27 Summary of TreeWalker Methods; Dom Package

| Function          | Summary                                     |
|:------------------|:--------------------------------------------|
| adjustCtx()       | Attach this tree walker to another context. |
| firstChild()      | Get the first child of the current node.    |
| lastChild()       | Get the last child of the current node.     |
| nextNode()        | Get the next node.                          |
| nextSibling()     | Get the next sibling node.                  |
| parentNode()      | Get the parent of the current node.         |
| previousNode()    | Get the previous node.                      |
| previousSibling() | Get the previous sibling node.              |

#### adjustCtx()

Attaches this tree walker to the context associated with a given node reference

##### Syntax

    void adjustCtx(
       NodeRef< Node>& nref);

| Parameter | Description                      |
|:----------|:---------------------------------|
| `nref`    | reference to provide the context |

#### firstChild()

Get the first child of the current node.

##### Syntax

    Node* firstChild();

##### Returns

`(Node*)` pointer to first child node

#### lastChild()

Get the last child of the current node.

##### Syntax

    Node* lastChild();

##### Returns

`(Node*)` pointer to last child node

#### nextNode()

Get the next node.

##### Syntax

    Node* nextNode();

##### Returns

`(Node*)` pointer to the next node

#### nextSibling()

Get the next sibling node.

##### Syntax

    Node* nextSibling();

##### Returns

`(Node*)` pointer to the next sibling node

#### parentNode()

Get the parent of the current node.

##### Syntax

    Node* parentNode();

##### Returns

`(Node*)` pointer to the parent node

#### previousNode()

Get the previous node.

##### Syntax

    Node* previousNode();

##### Returns

`(Node*)` pointer to previous node

#### previousSibling()

Get the previous sibling node.

##### Syntax

    Node* previousSibling();

##### Returns

`(Node*)` pointer to the previous sibling node
