The `XPointer` package for C++ contains types and methods related to `XPointer` processing, such as `XPointer` datatypes, `Processor` methods, `XppException` methods, `XPPLocation` methods, and `XppLocSet` methods.

### XPointer Datatypes

Table 9-1 summarizes the datatypes of the `XPointer` package.

Table 9-1 Summary of Datatypes; XPointer Package

| Datatype         | Description                             |
|:-----------------|:----------------------------------------|
| XppExceptionCode | Defines XPath compiler identifiers.     |
| XppPrIdType      | Defines XPointer processor identifiers. |
| XppLocType       | Defines location types for XPointer.    |

#### XppExceptionCode

XPointer related exception codes.

##### Definition

    typedef enum XPathCompIdType {
       XvmXPathCompCXml = 1
    } XPathCompIdType;

#### XppPrIdType

Defines XPointer processor identifiers.

##### Definition

    typedef enum XppPrIdType {   XPtrPrCXml         = 1} XppPrIdType;


#### XppLocType

Defines location types for XPointer.

##### Definition

    typedef enum XppLocType {
          XPPLOC_TYPE_UNKNOWN = 0,
          XPPLOC_TYPE_NODE    = 1,
          XPPLOC_TYPE_POINT   = 2,
          XPPLOC_TYPE_RANGE   = 3,
          XPPLOC_TYPE_BOOL    = 4,
          XPPLOC_TYPE_NUM     = 5,
          XPPLOC_TYPE_STR     = 6
        } XppLocType;

### Processor Interface

Table 9-2 summarizes the methods available through the `Processor` interface.

Table 9-2 Summary of Processor Methods; XPointer Package

| Function         | Summary                                              |
|:-----------------|:-----------------------------------------------------|
| getProcessorId() | Get processor's Id.                                  |
| process()        | Evaluate XPointer expression against given document. |

#### getProcessorId()

Get Processor Id.

##### Syntax

    virtual XppPrIdType getProcessorId() const = 0;

##### Returns

`(XppPrIdType)` Processor's Id

#### process()

Evaluates XPointer expression against given document and returns result XPointer location set object.

##### Syntax

    virtual XppLocSet< Node>* process (
       InputSource* isrc_ptr,
       oratext* xpp_exp)
    throw (XppException) = 0;

Table 9-3 Description of Process Method Parameters

| Parameter  | Description                  |
|:-----------|:-----------------------------|
| `isrc_ptr` | instance document to process |
| `xpp_exp`  | XPointer expression          |

##### Returns

`(XppLocSet*)` XPath object

### XppException Interface

Table 9-4 summarizes the methods available through the `XPPException` interface.

Table 9-4 Summary of XppException Methods; Package XPointer

| Function     | Summary                                                |
|:-------------|:-------------------------------------------------------|
| getCode()    | Get Oracle XML error code embedded in the exception.   |
| getMesLang() | Get current language (encoding) of error messages.     |
| getMesLang() | Get Oracle XML error message.                          |
| getXppCode() | Get XPointer exception code embedded in the exception. |

#### getCode()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual unsigned getCode() const = 0;

##### Returns

`(unsigned)` numeric error code (0 on success)

#### getMesLang()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMesLang() const = 0;

##### Returns

`(oratext*)` Current language (encoding) of error messages

#### getMessage()

Virtual member function inherited from `XmlException`.

##### Syntax

    virtual oratext* getMessage() const = 0;

##### Returns

`(oratext *)` Error message

#### getXppCode()

This is a virtual member function that defines a prototype for implementation defined member functions returning XPointer processor and compiler exception codes, defined in XppExceptionCode, of the exceptional situations during execution.

##### Syntax

    virtual XppExceptionCode getXppCode() const = 0;

##### Returns

`(XppExceptionCode)` exception code

### XppLocation Interface

Table 9-5 summarizes the methods available through the `XppLocation` interface.

Table 9-5 Summary of XppLocation Methods; XPointer Package

| Function     | Summary                |
|:-------------|:-----------------------|
| getLocType() | Get the location type. |
| getNode()    | Get the node.          |
| getRange()   | Get range.             |

#### getLocType()

Get the location type.

##### Syntax

     XppLocType getLocType() const;

#### getNode()

Get the node.

##### Syntax

     Node* getNode() const;

#### getRange()

Get range.

##### Syntax

     Range< Node>* getRange() const;

### XppLocSet Interface

Table 9-6 summarizes the methods available through the `XppLocSet` interface.

Table 9-6 Summary of XppLocSet Methods; XPointer Package

| Function  | Summary                   |
|:----------|:--------------------------|
| getItem() | Get item given its index. |
| getSize() | Get location set size.    |

#### getItem()

Returns a reference to the item.

##### Syntax

    XppLocation< Node>* getItem(
       ub4 index) const;

Table 9-7 Summary of getItem Method; XPointer Package

| Parameter | Description      |
|:----------|:-----------------|
| `index`   | index of an item |

##### Returns

`(XppLocation*)` reference to the item

#### getSize()

The size of the node set.

##### Syntax

    ub4 getSize() const;

##### Returns

`(ub4)` node set size
