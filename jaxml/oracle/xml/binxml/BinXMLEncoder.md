Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](BinXMLDecoder.md)**
- **[Next Class](BinXMLException.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.binxml**

## **Interface BinXMLEncoder**

-

  ------------------------------------------------------------------------

  **
  **

      public interface BinXMLEncoder

  **An interface which contains APIs to convert XML to binary stream.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                      |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `ENC_IMPLICIT_SCHEMA_REG`<br>If true, - then the schema in the top level xsi:schemaLocation tag is to be used for validation.                                                              |
    | `static int`      | `ENC_INLINE_TOKEN_DEFS`<br>If true, and if schemaAware = false, then the token definitions will be inlined in the binary stream.                                                           |
    | `static int`      | `ENC_MID_TIER_OPT`<br>If true, and if schemaAware = false, then the binary stream will be optimized for mid-tier usage and will not depend on metadata repository.                         |
    | `static int`      | `ENC_SAVE_VALIDATION_INFO`<br>If true, then while encoding store information available after a schema validation, which can be accessed using XDK extension APIs for PSVI on Scalable DOM. |
    | `static int`      | `ENC_SCHEMA_AWARE`<br>If true, encode the binary stream using a schema.                                                                                                                    |
    | `static int`      | `ENC_SCHEMA_LOCATION_AWARE`                                                                                                                                                                |
    | `static int`      | `ENC_XDB_COMPATIBLE`<br>If true, Encoder will work on XDB compatible mode All whitespaces between elements are considered ignorable                                                        |
    | `static int`      | `ENC_XDB_INLINE_TOKENS`                                                                                                                                                                    |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                              | Method and Description                                                                                                                                    |
    |----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ContentHandler`](../../../org/xml/sax/ContentHandler.md)     | `getContentHandler``()`<br>This is the main SAX handler which receives events such as start and end document, start and end element, character data, etc. |
    | [`DeclHandler`](../../../org/xml/sax/ext/DeclHandler.md)       | `getDeclHandler``()`<br>Returns the DeclHandler to be set in the user application.                                                                        |
    | [`DTDHandler`](../../../org/xml/sax/DTDHandler.md)             | `getDTDHandler``()`<br>Returns the DTDHandler to be set in the user application                                                                           |
    | [`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)         | `getErrorHandler``()`<br>Returns the default error handler to be used in the user application                                                             |
    | [`LexicalHandler`](../../../org/xml/sax/ext/LexicalHandler.md) | `getLexicalHandler``()`<br>Returns the LexcialHandler to be set in the user application.                                                                  |
    | `void`                                                         | `setProperty``(int propType, boolean value)`<br>Set properties for encoding.                                                                              |
    | `void`                                                         | `setSchema``(java.lang.String schemaURL)`<br>If ENC_SCHEMA_AWARE is set to true, then this schema will be used for validation and encoding.               |

<!-- -->

- - ### Field Detail

    - #### ENC_SCHEMA_AWARE

          static final int ENC_SCHEMA_AWARE

      If true, encode the binary stream using a schema. The same annotated schema will be required for decoding. If false, then the encoded binary stream will not be dependant on a schema. Default is false.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_SAVE_VALIDATION_INFO

          static final int ENC_SAVE_VALIDATION_INFO

      If true, then while encoding store information available after a schema validation, which can be accessed using XDK extension APIs for PSVI on Scalable DOM. It also indicates that the input XML will be fully validated with respect to the schema. This can be true even if schemaAware = false, the only requirement is that a schema should be available for validation. If false, then schema information is not included in the output binary stream. The default is false.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_IMPLICIT_SCHEMA_REG

          static final int ENC_IMPLICIT_SCHEMA_REG

      If true, - then the schema in the top level xsi:schemaLocation tag is to be used for validation. If false, ignore the schemaLocation tag and use the registered schema for validation. This value is considered when schemaAware = true and/or saveSchemaValidationInfo = true. Default is false.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_INLINE_TOKEN_DEFS

          static final int ENC_INLINE_TOKEN_DEFS

      If true, and if schemaAware = false, then the token definitions will be inlined in the binary stream. If false, and if schemaAware = false, then token definitions will not be inline in the binary stream, instead the token sets will be stored in the local Vocabulary cache and persisted to the metadata repository. If schema aware = true this value will be ignored.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_MID_TIER_OPT

          static final int ENC_MID_TIER_OPT

      If true, and if schemaAware = false, then the binary stream will be optimized for mid-tier usage and will not depend on metadata repository. If schemaAware = true this value will be ignored.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_XDB_COMPATIBLE

          static final int ENC_XDB_COMPATIBLE

      If true, Encoder will work on XDB compatible mode All whitespaces between elements are considered ignorable
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_SCHEMA_LOCATION_AWARE

          static final int ENC_SCHEMA_LOCATION_AWARE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENC_XDB_INLINE_TOKENS

          static final int ENC_XDB_INLINE_TOKENS

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setProperty

          void setProperty(int propType,
                           boolean value)
                    throws BinXMLException

      Set properties for encoding.
      Parameters:
      `propType` - a property constant ENC\_\* defined in the Encoder.

      `value` - true or false

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### setSchema

          void setSchema(java.lang.String schemaURL)
                  throws BinXMLException

      If ENC_SCHEMA_AWARE is set to true, then this schema will be used for validation and encoding. If schema is not available in the local cache or metadata repository then it will be registered before encoding. If ENC_SCHEMA_AWARE is set to false and ENC_SAVE_VALIDATION_INFO is set to true, then this schema will be used for validation only.
      Parameters:
      `schemaURL` - schema to be used for encoding

      Throws:
      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getContentHandler

          ContentHandler getContentHandler()
                                    throws BinXMLException

      This is the main SAX handler which receives events such as start and end document, start and end element, character data, etc. This handler will convert XML SAX events to CSX to be stored in the BinaryXMLStream.
      Returns:
      the ContentHandler to be set in the user application

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getErrorHandler

          ErrorHandler getErrorHandler()
                                throws BinXMLException

      Returns the default error handler to be used in the user application
      Returns:
      error handler object

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getDTDHandler

          DTDHandler getDTDHandler()
                            throws BinXMLException

      Returns the DTDHandler to be set in the user application
      Returns:
      handler for DTD related events

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getDeclHandler

          DeclHandler getDeclHandler()
                              throws BinXMLException

      Returns the DeclHandler to be set in the user application. This is an optional extension handler for SAX2 to provide information about DTD declarations in an XML document.
      Returns:
      handler for DTD declarations

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

    <!-- -->

    - #### getLexicalHandler

          LexicalHandler getLexicalHandler()
                                    throws BinXMLException

      Returns the LexcialHandler to be set in the user application. This is an optional extension handler for SAX2 to provide information about comments and CDATA section boundaries.
      Returns:
      handler for lexical information such as comments and CDATA section boundaries

      Throws:
      [`BinXMLException`](BinXMLException.md) - Raised for any errors encountered

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](BinXMLDecoder.md)**
- **[Next Class](BinXMLException.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
