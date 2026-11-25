The IO Package for C++ APIs describes the input/output `IO` datatypes and `InputSource` methods.

**See Also:**

[Oracle XML Developer's Kit Programmer's Guide](../adxdk/adx_cp_unified.md)

### IO Datatypes

Table 4-1 summarizes the datatypes of the IO package.

Table 4-1 Summary of Datatypes; IO Package

| Datatype        | Description                 |
|:----------------|:----------------------------|
| InputSourceType | Defines input source types. |

#### InputSourceType

Defines input source types.

##### Definition

    typedef enum InputSourceType {
       ISRC_URI = 1,
       ISRC_FILE = 2,
       ISRC_BUFFER = 3,
       ISRC_DOM = 4,
       ISRC_CSTREAM = 5 }
    InputSourceType;

### InputSource Interface

Table 4-2 summarizes the methods available through the IO interface

Table 4-2 Summary of IO Package Interfaces

| Function      | Summary                    |
|:--------------|:---------------------------|
| getBaseURI()  | Get the base URI.          |
| getISrcType() | Get the input source type. |
| setBaseURI()  | Set the base URI.          |

#### getBaseURI()

Gets the base URI. It is used by some input sources such as File and URI.

##### Syntax

    oratext* getBaseURI() { return baseURI; }

##### Returns

`(oratext*)` base URI

#### getISrcType()

Gets the input source type.

##### Syntax

    InputSourceType getISrcType() const { return isrctype; }

##### Returns

`(InputSourceType)` input source type

#### setBaseURI()

Sets the base URI. It is used by some input sources such as File and URI.

##### Syntax

    void setBaseURI( oratext* base_URI)  baseURI = base_URI; }
