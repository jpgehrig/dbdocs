Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](AttrDecl.md)**
- **[Next Class](DefaultXMLDocumentHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Class BinaryParser**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLParser](XMLParser.md)**

  - - **oracle.xml.parser.v2.BinaryParser**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class BinaryParser
      extends XMLParser

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                                              |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `BINARY_RESULT_ID`<br>Attribute IDs for Binary configuration BINARY_RESULT_ID -- binary storage, value can be OutputStream, File or Blob PAGE_MANAGER_ID -- value must be a PageManager ELEMENT_INDEXING_ID - Indexing or not, value is a Boolean. |
    | `static int`      | `ELEMENT_INDEXING_ID`                                                                                                                                                                                                                              |
    | `static int`      | `PAGE_MANAGER_ID`                                                                                                                                                                                                                                  |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)**

      **[`BASE_URL`](XMLParser.md)`, `[`BASE_URL_ID`](XMLParser.md)`, `[`CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`DEFAULT_ENTITY_EXPANSION_DEPTH_SECURE`](XMLParser.md)`, `[`DTD_OBJECT`](XMLParser.md)`, `[`DTD_OBJECT_ID`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH`](XMLParser.md)`, `[`ENTITY_EXPANSION_DEPTH_ID`](XMLParser.md)`, `[`EXPAND_ENTITYREF`](XMLParser.md)`, `[`EXPAND_ENTITYREF_ID`](XMLParser.md)`, `[`IGNORE_DUPLICATE_ID`](XMLParser.md)`, `[`PARSER`](XMLParser.md)`, `[`PARSER_CDATA`](XMLParser.md)`, `[`PARSER_DTD`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT`](XMLParser.md)`, `[`RESOLVE_ENTITY_DEFAULT_ID`](XMLParser.md)`, `[`SCHEMA_LANGUAGE`](XMLParser.md)`, `[`SCHEMA_LANGUAGE_ID`](XMLParser.md)`, `[`SCHEMA_OBJECT`](XMLParser.md)`, `[`SCHEMA_OBJECT_ID`](XMLParser.md)`, `[`SCHEMA_SOURCE`](XMLParser.md)`, `[`SCHEMA_SOURCE_ID`](XMLParser.md)`, `[`STANDALONE`](XMLParser.md)`, `[`STANDALONE_ID`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION`](XMLParser.md)`, `[`USE_DTD_ONLY_FOR_VALIDATION_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_DEFAULT`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_ID`](XMLParser.md)`, `[`XDK_ATTRIBUTE_ENTITY_EXPANSION_COUNT_LIMIT_SECURE`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING`](XMLParser.md)`, `[`XDK_FEATURE_ALLOW_ILLEGAL_UTF8_ENCODING_ID`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC`](XMLParser.md)`, `[`XDK_FEATURE_CONTENT_MODEL_DETERMINISTIC_ID`](XMLParser.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `BinaryParser``()`          |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                           |
    |--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | [`BinaryStream`](../../scalable/BinaryStream.md) | `getBinaryStream``()`                                                                                                            |
    | `void`                                           | `setAttribute``(int id, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation. |
    | `void`                                           | `setBinaryStream``(`[`BinaryStream`](../../scalable/BinaryStream.md)` stream)`                                                   |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLParser](XMLParser.md)

      [`getAttribute`](XMLParser.md)`, `[`getBaseURL`](XMLParser.md)`, `[`getEntityResolver`](XMLParser.md)`, `[`getErrorHandler`](XMLParser.md)`, `[`getReleaseVersion`](XMLParser.md)`, `[`getValidationMode`](XMLParser.md)`, `[`getValidationModeValue`](XMLParser.md)`, `[`getXMLProperty`](XMLParser.md)`, `[`isXMLPropertyReadOnly`](XMLParser.md)`, `[`isXMLPropertySupported`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`parse`](XMLParser.md)`, `[`reset`](XMLParser.md)`, `[`setAttribute`](XMLParser.md)`, `[`setBaseURL`](XMLParser.md)`, `[`setDoctype`](XMLParser.md)`, `[`setEntityResolver`](XMLParser.md)`, `[`setErrorHandler`](XMLParser.md)`, `[`setLocale`](XMLParser.md)`, `[`setPreserveWhitespace`](XMLParser.md)`, `[`setSchemaValidationMode`](XMLParser.md)`, `[`setSchemaValidatorProperty`](XMLParser.md)`, `[`setSecureProcessing`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setValidationMode`](XMLParser.md)`, `[`setXMLProperty`](XMLParser.md)`, `[`setXMLSchema`](XMLParser.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### BINARY_RESULT_ID

          public static final int BINARY_RESULT_ID

      Attribute IDs for Binary configuration BINARY_RESULT_ID -- binary storage, value can be OutputStream, File or Blob PAGE_MANAGER_ID -- value must be a PageManager ELEMENT_INDEXING_ID - Indexing or not, value is a Boolean.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### PAGE_MANAGER_ID

          public static final int PAGE_MANAGER_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ELEMENT_INDEXING_ID

          public static final int ELEMENT_INDEXING_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### BinaryParser

          public BinaryParser()

  <!-- -->

  - ### Method Detail

    - #### setBinaryStream

          public void setBinaryStream(BinaryStream stream)
                               throws java.lang.IllegalArgumentException

      Throws:
      `java.lang.IllegalArgumentException`

    <!-- -->

    - #### getBinaryStream

          public BinaryStream getBinaryStream()

    <!-- -->

    - #### setAttribute

          public void setAttribute(int id,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Overrides:
      [`setAttribute`](XMLParser.md) in class [`XMLParser`](XMLParser.md)

      Parameters:
      `id` - The id of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](AttrDecl.md)**
- **[Next Class](DefaultXMLDocumentHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
