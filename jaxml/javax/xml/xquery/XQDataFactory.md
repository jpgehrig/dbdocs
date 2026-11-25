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

- **[Prev Class](XQConstants.md)**
- **[Next Class](XQDataSource.md)**

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

**javax.xml.xquery**

## **Interface XQDataFactory**

- **All Known Subinterfaces:**
  **[XQConnection](XQConnection.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQDataFactory

  **This interface represents a factory to obtain sequences, item objects and types.**
  **The items, sequences and types obtained through this interface are independent of any connection.**

  **The items and sequences created are immutable. The `close` method can be called to close the item or sequence and release all resources associated with this item or sequence.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                                                                                                                                                                                                                                                                                                             |
    |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQItemType`](XQItemType.md)         | `createAtomicType``(int basetype)`<br>Creates a new `XQItemType` object representing an XQuery atomic type.                                                                                                                                                                                                                                                                                        |
    | [`XQItemType`](XQItemType.md)         | `createAtomicType``(int basetype, javax.xml.namespace.QName typename, java.net.URI schemaURI)`<br>Creates a new `XQItemType` object representing an XQuery atomic type.                                                                                                                                                                                                                            |
    | [`XQItemType`](XQItemType.md)         | `createAttributeType``(javax.xml.namespace.QName nodename, int basetype)`<br>Creates a new `XQItemType` object representing the XQuery `attribute(`*`nodename`*`, `*`basetype`*`)` type with the given node name and base type.                                                                                                                                                                    |
    | [`XQItemType`](XQItemType.md)         | `createAttributeType``(javax.xml.namespace.QName nodename, int basetype, javax.xml.namespace.QName typename, java.net.URI schemaURI)`<br>Creates a new `XQItemType` object representing the XQuery `attribute(`*`nodename`*`,`*`basetype`*`,`*`typename`*`,`*`schemaURI`*`)` type, with the given node name, base type, schema type name and schema URI.                                           |
    | [`XQItemType`](XQItemType.md)         | `createCommentType``()`<br>Creates a new `XQItemType` object representing the XQuery `comment()` type.                                                                                                                                                                                                                                                                                             |
    | [`XQItemType`](XQItemType.md)         | `createDocumentElementType``(`[`XQItemType`](XQItemType.md)` elementType)`<br>Creates a new `XQItemType` object representing the XQuery `document-node(`*`elementType`*`)` type containing a single element.                                                                                                                                                                                       |
    | [`XQItemType`](XQItemType.md)         | `createDocumentSchemaElementType``(`[`XQItemType`](XQItemType.md)` elementType)`<br>Creates a new `XQItemType` object representing the XQuery `document-node(`*`elementType`*`)` type containing a single `schema-element(...)`                                                                                                                                                                    |
    | [`XQItemType`](XQItemType.md)         | `createDocumentType``()`<br>Creates a new `XQItemType` object representing the XQuery `document-node()` type.                                                                                                                                                                                                                                                                                      |
    | [`XQItemType`](XQItemType.md)         | `createElementType``(javax.xml.namespace.QName nodename, int basetype)`<br>Creates a new `XQItemType` object representing the XQuery `element(`*`nodename`*`, `*`basetype`*`)` type, with the given node name and base type.                                                                                                                                                                       |
    | [`XQItemType`](XQItemType.md)         | `createElementType``(javax.xml.namespace.QName nodename, int basetype, javax.xml.namespace.QName typename, java.net.URI schemaURI, boolean allowNill)`<br>Creates a new `XQItemType` object representing the XQuery `element(`*`nodename`*`,`*`basetype`*`,`*`typename`*`,`*`schemaURI`*`, `*`allowNill`*`)` type, given the node name, base type, schema type name, schema URI, and nilled check. |
    | [`XQItem`](XQItem.md)                 | `createItem``(`[`XQItem`](XQItem.md)` item)`<br>Creates a copy of the specified `XQItem`.                                                                                                                                                                                                                                                                                                          |
    | [`XQItem`](XQItem.md)                 | `createItemFromAtomicValue``(java.lang.String value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                 |
    | [`XQItem`](XQItem.md)                 | `createItemFromBoolean``(boolean value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                              |
    | [`XQItem`](XQItem.md)                 | `createItemFromByte``(byte value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                    |
    | [`XQItem`](XQItem.md)                 | `createItemFromDocument``(java.io.InputStream value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from the given value.                                                                                                                                                                                                                                     |
    | [`XQItem`](XQItem.md)                 | `createItemFromDocument``(java.io.Reader value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from the given value.                                                                                                                                                                                                                                          |
    | [`XQItem`](XQItem.md)                 | `createItemFromDocument``(`[`Source`](../transform/Source.md)` value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from the given `Source`.                                                                                                                                                                                                                                           |
    | [`XQItem`](XQItem.md)                 | `createItemFromDocument``(java.lang.String value, java.lang.String baseURI, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from the given value.                                                                                                                                                                                                                                        |
    | [`XQItem`](XQItem.md)                 | `createItemFromDocument``(javax.xml.stream.XMLStreamReader value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from the given value.                                                                                                                                                                                                                                                  |
    | [`XQItem`](XQItem.md)                 | `createItemFromDouble``(double value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                |
    | [`XQItem`](XQItem.md)                 | `createItemFromFloat``(float value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                  |
    | [`XQItem`](XQItem.md)                 | `createItemFromInt``(int value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                      |
    | [`XQItem`](XQItem.md)                 | `createItemFromLong``(long value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                    |
    | [`XQItem`](XQItem.md)                 | `createItemFromNode``(`[`Node`](../../../org/w3c/dom/Node.md)` value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                |
    | [`XQItem`](XQItem.md)                 | `createItemFromObject``(java.lang.Object value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                      |
    | [`XQItem`](XQItem.md)                 | `createItemFromShort``(short value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                                  |
    | [`XQItem`](XQItem.md)                 | `createItemFromString``(java.lang.String value, `[`XQItemType`](XQItemType.md)` type)`<br>Creates an item from a given value.                                                                                                                                                                                                                                                                      |
    | [`XQItemType`](XQItemType.md)         | `createItemType``()`<br>Creates a new `XQItemType` object representing the XQuery item type.                                                                                                                                                                                                                                                                                                       |
    | [`XQItemType`](XQItemType.md)         | `createNodeType``()`<br>Creates a new `XQItemType` object representing the XQuery `node()` type.                                                                                                                                                                                                                                                                                                   |
    | [`XQItemType`](XQItemType.md)         | `createProcessingInstructionType``(java.lang.String piTarget)`<br>Creates a new `XQItemType` object representing the XQuery `processing-instruction(`*`piTarget`*`)` type.                                                                                                                                                                                                                         |
    | [`XQItemType`](XQItemType.md)         | `createSchemaAttributeType``(javax.xml.namespace.QName nodename, int basetype, java.net.URI schemaURI)`<br>Creates a new `XQItemType` object representing the XQuery `schema-attribute(`*`nodename`*`,`*`basetype`*`,`*`schemaURI`*`)` type, with the given node name, base type, and schema URI.                                                                                                  |
    | [`XQItemType`](XQItemType.md)         | `createSchemaElementType``(javax.xml.namespace.QName nodename, int basetype, java.net.URI schemaURI)`<br>Creates a new `XQItemType` object representing the XQuery `schema-element(`*`nodename`*`,`*`basetype`*`,`*`schemaURI`*`)` type, given the node name, base type, and the schema URI.                                                                                                       |
    | [`XQSequence`](XQSequence.md)         | `createSequence``(java.util.Iterator i)`<br>Creates an `XQSequence`, containing all the items from the iterator.                                                                                                                                                                                                                                                                                   |
    | [`XQSequence`](XQSequence.md)         | `createSequence``(`[`XQSequence`](XQSequence.md)` s)`<br>Creates a copy of the specified `XQSequence`.                                                                                                                                                                                                                                                                                             |
    | [`XQSequenceType`](XQSequenceType.md) | `createSequenceType``(`[`XQItemType`](XQItemType.md)` item, int occurence)`<br>Creates a new sequence type from an item type and occurence indicator.                                                                                                                                                                                                                                              |
    | [`XQItemType`](XQItemType.md)         | `createTextType``()`<br>Creates a new `XQItemType` object representing the XQuery `text()` type.                                                                                                                                                                                                                                                                                                   |

<!-- -->

- - ### Method Detail

    - #### createItemFromAtomicValue

          XQItem createItemFromAtomicValue(java.lang.String value,
                                           XQItemType type)
                                    throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the casting from `xs:string` rules outlined in [*17.1.1 Casting from xs:string and xs:untypedAtomic, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#casting_from_strings). If the cast fails an `XQException` is thrown.
      Parameters:
      `value` - the lexical string value of the type

      `type` - the item type

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) any of the arguments are `null`, (2) given type is not an atomic type, (3) the conversion of the value to an XDM instance failed, or (4) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromString

          XQItem createItemFromString(java.lang.String value,
                                      XQItemType type)
                               throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type, which must represent an `xs:string` or a type derived by restriction from `xs:string`. If the specified type is `null`, it defaults to `xs:string`.
      Subsequently the value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type, `xs:string`, is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(java.lang.String value,
                                        java.lang.String baseURI,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given value.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(java.io.Reader value,
                                        java.lang.String baseURI,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given value.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(java.io.InputStream value,
                                        java.lang.String baseURI,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given value.

      If the value represents a well-formed XML document, it will be parsed and results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `baseURI` - an optional base URI, can be `null`. It can be used, for example, to resolve relative URIs and to include in error messages.

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(javax.xml.stream.XMLStreamReader value,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given value.

      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT` or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(Source value,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given `Source`. An XQJ implementation must at least support the following implementations:
      - `javax.xml.transform.dom.DOMSource`
      - `javax.xml.transform.sax.SAXSource`
      - `javax.xml.transform.stream.StreamSource`



      If the value represents a well-formed XML document, it will result in a document node. The kind of the input type must be `null`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromObject

          XQItem createItemFromObject(java.lang.Object value,
                                      XQItemType type)
                               throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromBoolean

          XQItem createItemFromBoolean(boolean value,
                                       XQItemType type)
                                throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromByte

          XQItem createItemFromByte(byte value,
                                    XQItemType type)
                             throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDouble

          XQItem createItemFromDouble(double value,
                                      XQItemType type)
                               throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromFloat

          XQItem createItemFromFloat(float value,
                                     XQItemType type)
                              throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromInt

          XQItem createItemFromInt(int value,
                                   XQItemType type)
                            throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromLong

          XQItem createItemFromLong(long value,
                                    XQItemType type)
                             throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromNode

          XQItem createItemFromNode(Node value,
                                    XQItemType type)
                             throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - if (1) the `value` argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromShort

          XQItem createItemFromShort(short value,
                                     XQItemType type)
                              throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the converstion fails, an `XQException` will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      `XQItem` representing the resulting item

      Throws:
      [`XQException`](XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItem

          XQItem createItem(XQItem item)
                     throws XQException

      Creates a copy of the specified `XQItem`. This method can be used, for example, to copy an `XQResultItem` object so that the new item is not dependant on the connection.
      Parameters:
      `item` - the `XQItem` to copy

      Returns:
      `XQItem` independent of any underlying `XQConnection` is created

      Throws:
      [`XQException`](XQException.md) - if (1) the specified item is `null`, (2) the underlying object implementing the interface is closed, (3) the specified item is closed

    <!-- -->

    - #### createSequence

          XQSequence createSequence(XQSequence s)
                             throws XQException

      Creates a copy of the specified `XQSequence`. The newly created `XQSequence` is scrollable and independent of any underlying `XQConnection`. The new `XQSequence` will contain all items from the specified `XQSequence` starting from its current position. The copy process will implicitly perform next operations on the specified sequence to read the items. All items are consumed, the current position of the cursor is set to point after the last item.
      Parameters:
      `s` - input sequence

      Returns:
      `XQSequence` representing a copy of the input sequence

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the items in the specified sequence, (2) the specified sequence is closed, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) the `s` parameter is `null`, or (5) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequence

          XQSequence createSequence(java.util.Iterator i)
                             throws XQException

      Creates an `XQSequence`, containing all the items from the iterator. The newly created `XQSequence` is scrollable and independent of any underlying `XQConnection`. If the iterator returns an `XQItem`, it is added to the sequence. If the iterator returns any other object, an item is added to the sequence following the rules from *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the iterator does not return any items, then an empty sequence is created.
      Parameters:
      `i` - input iterator

      Returns:
      `XQSequence` representing the sequence containing all items from the input iterator

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of any of the objects in the iterator to item fails, (2) the `i` parameter is `null`, or (3) underlying object implementing the interface is closed

    <!-- -->

    - #### createAtomicType

          XQItemType createAtomicType(int basetype)
                               throws XQException

      Creates a new `XQItemType` object representing an XQuery atomic type. The item kind of the item type will be `XQItemType.XQITEMKIND_ATOMIC`.
      Example -
            XQConnection conn = ...;

            // to create xs:integer item type
            conn.createAtomicType(XQItemType.XQBASETYPE_INTEGER);


      Parameters:
      `basetype` - one of the `XQItemType.XQBASETYPE_*` constants. All basetype constants except the following are valid:


            XQItemType.XQBASETYPE_UNTYPED
            XQItemType.XQBASETYPE_ANYTYPE
            XQItemType.XQBASETYPE_IDREFS
            XQItemType.XQBASETYPE_NMTOKENS
            XQItemType.XQBASETYPE_ENTITIES
            XQItemType.XQBASETYPE_ANYSIMPLETYPE


      Returns:
      a new `XQItemType` representing the atomic type

      Throws:
      [`XQException`](XQException.md) - if (1) an invalid `basetype` value is passed in, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createAtomicType

          XQItemType createAtomicType(int basetype,
                                      javax.xml.namespace.QName typename,
                                      java.net.URI schemaURI)
                               throws XQException

      Creates a new `XQItemType` object representing an XQuery atomic type. The item kind of the item type will be `XQItemType.XQITEMKIND_ATOMIC`.
      Example -

            XQConnection conn = ...;

            // to create po:hatsize atomic item type
            conn.createAtomicType(XQItemType.XQBASETYPE_INTEGER,
                            new QName("http://www.hatsizes.com", "hatsize","po"),
                            new URI("http://hatschema.com"));


      Parameters:
      `basetype` - one of the `XQItemType.XQBASETYPE_*` constants. All basetype constants except the following are valid:


            XQItemType.XQBASETYPE_UNTYPED
            XQItemType.XQBASETYPE_ANYTYPE
            XQItemType.XQBASETYPE_IDREFS
            XQItemType.XQBASETYPE_NMTOKENS
            XQItemType.XQBASETYPE_ENTITIES
            XQItemType.XQBASETYPE_ANYSIMPLETYPE


      `typename` - the `QName` of the type. If the `QName` refers to a predefinied type, it must match the `basetype`. Can be `null`

      `schemaURI` - the URI to the schema. Can be `null`. This can only be specified if the typename is also specified

      Returns:
      a new `XQItemType` representing the atomic type

      Throws:
      [`XQException`](XQException.md) - if (1) an invalid `basetype` value is passed in, (2) the underlying object implementing the interface is closed, (3) the implementation does not support user-defined XML schema types, or (4) if the `typename` refers to a predefinied type and does not match `basetype`

    <!-- -->

    - #### createAttributeType

          XQItemType createAttributeType(javax.xml.namespace.QName nodename,
                                         int basetype)
                                  throws XQException

      Creates a new `XQItemType` object representing the XQuery `attribute(`*`nodename`*`, `*`basetype`*`)` type with the given node name and base type. This method can be used to create item type for attributes with a pre-defined schema type.

      Example -

            XQConnection conn = ..; // An XQuery connection

            - attribute() // no node name, pass null for the node name

              conn.createAttributeType(null, XQItemType.XQBASETYPE_ANYSIMPLETYPE);

            - attribute (*)  // equivalent to attribute()

              conn.createAttributeType(null, XQItemType.XQBASETYPE_ANYSIMPLETYPE);

            - attribute (person) // attribute of name person and any simple type.

              conn.createAttributeType(new QName("person"), XQItemType.XQBASETYPE_ANYSIMPLETYPE);

            - attribute(foo:bar) // node name foo:bar, type is any simple type

              conn.createAttributeType(new QName("http://www.foo.com", "bar","foo"),
                                       XQItemType.XQBASETYPE_ANYSIMPLETYPE);

            - attribute(foo:bar, xs:integer) // node name foo:bar, type is xs:integer

              conn.createAttributeType(new QName("http://www.foo.com", "bar","foo"),
                                       XQItemType.XQBASETYPE_INTEGER);


      Parameters:
      `nodename` - specifies the name of the node.`null` indicates a wildcard for the node name

      `basetype` - the base type of the attribute. One of the `XQItemType.XQBASETYPE_*` other than `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`

      Returns:
      a new `XQItemType` representing the XQuery `attribute(`*`nodename`*`, `*`basetype`*`)` type

      Throws:
      [`XQException`](XQException.md) - if (1) the underlying object implementing the interface is closed or (2) if the base type is one of: `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`

    <!-- -->

    - #### createAttributeType

          XQItemType createAttributeType(javax.xml.namespace.QName nodename,
                                         int basetype,
                                         javax.xml.namespace.QName typename,
                                         java.net.URI schemaURI)
                                  throws XQException

      Creates a new `XQItemType` object representing the XQuery `attribute(`*`nodename`*`,`*`basetype`*`,`*`typename`*`,`*`schemaURI`*`)` type, with the given node name, base type, schema type name and schema URI. The type name can reference either pre-defined simple types or user-defined simple types.

      Example -

            XQConnection conn = ..; // An XQuery connection

            - attribute (name, employeename) // attribute name of type employeename

            conn.createAttributeType(new QName("name"), XQItemType.XQBASETYPE_ANYSIMPLETYPE,
                                     new QName("employeename"), null);

            - attribute (foo:bar, po:city)
            where the prefix foo refers to the namespace http://www.foo.com and the
            prefix po refers to the namespace "http://www.address.com"

            conn.createAttributeType(new QName("http://www.foo.com", "bar","foo"),
                                     XQItemType.XQBASETYPE_ANYSIMPLETYPE,
                                     new QName("http://address.com", "address","po"), null);

            - attribute (zip, zipcode) // attribute zip of type zipchode which derives from
                                       // xs:string

            conn.createAttributeType(new QName("zip"), XQItemType.XQBASETYPE_STRING,
                                     new QName("zipcode"), null);

            - attribute(foo:bar, po:hatsize)
            where the prefix foo refers to the namespace http://www.foo.com and the
            prefix po refers to the namespace "http://www.hatsizes.com"
            with schema URI "http://hatschema.com"

            conn.createAttributeType(new QName("http://www.foo.com", "bar","foo"),
                            XQItemType.XQBASETYPE_INTEGER,
                            new QName("http://www.hatsizes.com", "hatsize","po"),
                            new QName("http://hatschema.com"));


      Parameters:
      `nodename` - specifies the name of the node.`null` indicates a wildcard for the node name

      `basetype` - the base type of the attribute. One of the `XQItemTyupe.XQBASETYPE_*` constants other than `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`

      `typename` - the `QName` of the type. If the `QName` refers to a predefinied type, it must match the `basetype`. Can be `null`.

      `schemaURI` - the URI to the schema. Can be `null`. This can only be specified if the typename is also specified

      Returns:
      a new `XQItemType` representing the XQuery `attribute(`*`nodename`*`,`*`basetype`*`, `*`typename`*`,`*`schemaURI`*`)` type.

      Throws:
      [`XQException`](XQException.md) - if (1) the underlying object implementing the interface is closed, (2) if the base type is one of: `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`, (3) the schema URI is specified and the typename is not specified, (4) the implementation does not support user-defined XML schema types, or (5) if the `typename` refers to a predefinied type and does not match `basetype`

    <!-- -->

    - #### createSchemaAttributeType

          XQItemType createSchemaAttributeType(javax.xml.namespace.QName nodename,
                                               int basetype,
                                               java.net.URI schemaURI)
                                        throws XQException

      Creates a new `XQItemType` object representing the XQuery `schema-attribute(`*`nodename`*`,`*`basetype`*`,`*`schemaURI`*`)` type, with the given node name, base type, and schema URI.

      Example -

               XQConnection conn = ..; // An XQuery connection

               - schema-attribute (name) // schema-attribute name, found in the schema
                                         // available at http://customerschema.com

               conn.createSchemaAttributeType(new QName("name"),
                            XQItemType.XQBASETYPE_STRING,
                            new URI(http://customerschema.com));


      Parameters:
      `nodename` - specifies the name of the node

      `basetype` - the base type of the attribute. One of the `XQItemTyupe.XQBASETYPE_*` constants other than `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`

      `schemaURI` - the URI to the schema. Can be `null`

      Returns:
      a new `XQItemType` representing the XQuery `schema-attribute(`*`nodename`*`,`*`basetype`*`, `*`schemaURI`*`)` type

      Throws:
      [`XQException`](XQException.md) - if (1) the node name is `null`, (2) if the base type is one of: `XQItemType.XQBASETYPE_UNTYPED` or `XQItemType.XQBASETYPE_ANYTYPE`, (3) the underlying object implementing the interface is closed, or (4) the implementation does not support user-defined XML schema types

    <!-- -->

    - #### createCommentType

          XQItemType createCommentType()
                                throws XQException

      Creates a new `XQItemType` object representing the XQuery `comment()` type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_COMMENT`.

      Example -
            XQConnection conn = ..; // An XQuery connection
            XQItemType cmttype = conn.createCommentType();

            int itemkind = cmttype.getItemKind(); // will be XQItemType.XQITEMKIND_COMMENT

            XQExpression expr = conn.createExpression();
            XQSequence result = expr.executeQuery("<!-- comments -->");

            result.next();
            boolean pi = result.instanceOf(cmttype);  // will be true


      Returns:
      a new `XQItemType` representing the XQuery `comment()` type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

    <!-- -->

    - #### createDocumentElementType

          XQItemType createDocumentElementType(XQItemType elementType)
                                        throws XQException

      Creates a new `XQItemType` object representing the XQuery `document-node(`*`elementType`*`)` type containing a single element. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_DOCUMENT_ELEMENT` and the base type set to the item type of the input `elementType`.
      Parameters:
      `elementType` - an `XQItemType` object representing an XQuery `element()` type, cannot be `null`

      Returns:
      a new `XQItemType` representing the XQuery `document-node(`*`elementType`*`)` type containing a single element

      Throws:
      [`XQException`](XQException.md) - if (1) the underlying object implementing the interface is closed or (2) the `elementType` has an item kind different from `XQItemType.XQITEMKIND_ELEMENT`, (3) the `elementType` argument is `null`, or (4) the implementation does not support user-defined XML schema types

    <!-- -->

    - #### createDocumentSchemaElementType

          XQItemType createDocumentSchemaElementType(XQItemType elementType)
                                              throws XQException

      Creates a new `XQItemType` object representing the XQuery `document-node(`*`elementType`*`)` type containing a single `schema-element(...)`. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT` and the base type set to the item type of the input `elementType`.
      Parameters:
      `elementType` - an `XQItemType` object representing an XQuery `schema-element(...)` type, cannot be `null`

      Returns:
      a new `XQItemType` representing the XQuery `document-node(`*`elementType`*`)` type containing a single `schema-element(...)` element

      Throws:
      [`XQException`](XQException.md) - if (1) the underlying object implementing the interface is closed or (2) the `elementType` has an item kind different from `XQItemType.XQITEMKIND_SCHEMA_ELEMENT`, (3) the `elementType` argument is `null`, (4) the implementation does not support user-defined XML schema types

    <!-- -->

    - #### createDocumentType

          XQItemType createDocumentType()
                                 throws XQException

      Creates a new `XQItemType` object representing the XQuery `document-node()` type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_DOCUMENT`.
      Returns:
      a new `XQItemType` representing the XQuery `document-node()` type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

    <!-- -->

    - #### createElementType

          XQItemType createElementType(javax.xml.namespace.QName nodename,
                                       int basetype)
                                throws XQException

      Creates a new `XQItemType` object representing the XQuery `element(`*`nodename`*`, `*`basetype`*`)` type, with the given node name and base type. This method can be used to create item type for elements with a pre-defined schema type.

      Example -
            XQConnection conn = ..; // An XQuery connection
            - element() // no node name, pass null for the node name

            conn.createElementType(null, XQItemType.XQBASETYPE_ANYTYPE);

            - element (*)  // equivalent to element()

            conn.createElementType(null, XQItemType.XQBASETYPE_ANYTYPE);

            - element(person) // element of name person and any type.

            conn.createElementType(new QName("person"), XQItemType.XQBASETYPE_ANYTYPE);

            - element(foo:bar) // node name foo:bar, type is anytype

            conn.createElementType(new QName("http://www.foo.com", "bar","foo"),
                                   XQItemType.XQBASETYPE_ANYTYPE);

            - element(foo:bar, xs:integer) // node name foo:bar, type is xs:integer

            conn.createElementType(new QName("http://www.foo.com", "bar","foo"),
                                   XQItemType.XQBASETYPE_INTEGER);


      Parameters:
      `nodename` - specifies the name of the node. `null` indicates a wildcard for the node name

      `basetype` - the base type of the item. One of the `XQItemType.XQBASETYPE_*` constants

      Returns:
      a new `XQItemType` representing the XQuery `element(`*`nodename`*`, `*`basetype`*`)` type

      Throws:
      [`XQException`](XQException.md) - if (1) the underlying object implementing the interface is closed

    <!-- -->

    - #### createElementType

          XQItemType createElementType(javax.xml.namespace.QName nodename,
                                       int basetype,
                                       javax.xml.namespace.QName typename,
                                       java.net.URI schemaURI,
                                       boolean allowNill)
                                throws XQException

      Creates a new `XQItemType` object representing the XQuery `element(`*`nodename`*`,`*`basetype`*`,`*`typename`*`,`*`schemaURI`*`, `*`allowNill`*`)` type, given the node name, base type, schema type name, schema URI, and nilled check. The type name can reference either pre-defined schema types or user-defined types.

      Example -
            XQConnection conn = ..; // An XQuery connection

            - element (person, employee) // element person of type employee

            conn.createElementType(new QName("person"), XQItemType.XQBASETYPE_ANYTYPE,
                                   new QName("employee"), null ,false);

            - element(person, employee ? ) // element person of type employee, whose nilled
                                           // property may be true or false.

            conn.createElementType(new QName("person"), XQItemType.XQBASETYPE_ANYTYPE,
                                   new QName("employee"), null ,true);

            - element(foo:bar, po:address)
            where the prefix foo refers to the namespace http://www.foo.com and the
            prefix po refers to the namespace "http://www.address.com"

            conn.createElementType(new QName("http://www.foo.com", "bar","foo"),
                         XQItemType.XQBASETYPE_ANYTYPE,
                         new QName("http://address.com", "address","po"), null, false);

            - element (zip, zipcode) // element zip of type zipchode which derives from
                                     // xs:string

            conn.createElementType(new QName("zip"), XQItemType.XQBASETYPE_STRING,
                                   new QName("zipcode"), null, false);

            - element (*, xs:anyType ?)

            conn.createElementType(null, XQItemType.XQBASETYPE_ANYTYPE, null, null, true);

            - element(foo:bar, po:hatsize)
            where the prefix foo refers to the namespace http://www.foo.com and the
            prefix po refers to the namespace "http://www.hatsizes.com"
            with schema URI "http://hatschema.com"

            conn.createElementType(new QName("http://www.foo.com", "bar","foo"),
                                XQItemType.XQBASETYPE_INTEGER,
                                new QName("http://www.hatsizes.com", "hatsize","po"),
                                new QName("http://hatschema.com"), false);



      Parameters:
      `nodename` - specifies the name of the element. `null` indicates a wildcard for the node name

      `basetype` - the base type of the item. One of the `XQItemType.XQBASETYPE_*` constants

      `typename` - the `QName` of the type. If the `QName` refers to a predefinied type, it must match the `basetype`. Can be `null`

      `schemaURI` - the URI to the schema. Can be `null`. This can only be specified if the typename is also specified

      `allowNill` - the nilled property of the element

      Returns:
      a new `XQItemType` representing the XQuery `element(`*`nodename`*`,`*`basetype`*`, `*`typename`*`,`*`schemaURI`*`, `*`allowNill`*`)` type

      Throws:
      [`XQException`](XQException.md) - if (1) schemaURI is specified but the typename is not specified, (2) the underlying object implementing the interface is closed, (3) the implementation does not support user-defined XML schema types, or (4) if the `typename` refers to a predefinied type and does not match `basetype`

    <!-- -->

    - #### createSchemaElementType

          XQItemType createSchemaElementType(javax.xml.namespace.QName nodename,
                                             int basetype,
                                             java.net.URI schemaURI)
                                      throws XQException

      Creates a new `XQItemType` object representing the XQuery `schema-element(`*`nodename`*`,`*`basetype`*`,`*`schemaURI`*`)` type, given the node name, base type, and the schema URI.

      Example -
               XQConnection conn = ..; // An XQuery connection

               - schema-element (customer) // schema-element person, found in
                                           // the schema available at http://customerschema.com

               conn.createElementType(new QName("customer"), XQItemType.XQBASETYPE_ANYTYPE,
                                   new URI("http://customerschema.com"));



      Parameters:
      `nodename` - specifies the name of the element

      `basetype` - the base type of the item. One of the `XQItemType.XQBASETYPE_*` constants

      `schemaURI` - the URI to the schema. Can be `null`

      Returns:
      a new `XQItemType` representing the XQuery `schema-element(`*`nodename`*`,`*`basetype`*`, `*`schemaURI`*`)` type

      Throws:
      [`XQException`](XQException.md) - if (1) the node name is `null`, (2) the underlying object implementing the interface is closed, or (3) the implementation does not support user-defined XML schema types

    <!-- -->

    - #### createItemType

          XQItemType createItemType()
                             throws XQException

      Creates a new `XQItemType` object representing the XQuery item type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_ITEM`.

      Example -
            XQConnection conn = ..; // An XQuery connection
            XQItemType typ = conn.createItemType(); // represents the XQuery item type "item()"


      Returns:
      a new `XQItemType` representing the XQuery item type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

    <!-- -->

    - #### createNodeType

          XQItemType createNodeType()
                             throws XQException

      Creates a new `XQItemType` object representing the XQuery `node()` type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_NODE`.
      Returns:
      a new `XQItemType` representing the XQuery `node()` type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

    <!-- -->

    - #### createProcessingInstructionType

          XQItemType createProcessingInstructionType(java.lang.String piTarget)
                                              throws XQException

      Creates a new `XQItemType` object representing the XQuery `processing-instruction(`*`piTarget`*`)` type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_PI`. A string literal can be passed to match the PITarget of the processing instruction as described in [*2.5.4.2 Matching an Item Type and an Item, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_matching_item).

      Example -
             XQConnection conn = ..; // An XQuery connection
             XQItemType anypi = conn.createProcessingInstructionType();
             XQItemType foopi = conn.createProcessingInstructionType("foo-format");

             XQExpression expr = conn.createExpression();
             XQSequence result = expr.executeQuery("<?format role="output" ?>");

             result.next();
             boolean pi = result.instanceOf(anypi);  // will be true
             pi = result.instanceOf(foopi);  // will be false

             XQExpression expr = conn.createExpression();
             XQSequence result = expr.executeQuery("<?foo-format role="output" ?>");

             result.next();
             boolean pi = result.instanceOf(anypi);  // will be true
             pi = result.instanceOf(foopi);  // will be true


      Parameters:
      `piTarget` - the string literal to match the processing instruction's PITarget. A `null` string value will match all processing instruction nodes

      Returns:
      a new `XQItemType` representing the XQuery `processing-instruction(`*`piTarget`*`)` type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequenceType

          XQSequenceType createSequenceType(XQItemType item,
                                            int occurence)
                                     throws XQException

      Creates a new sequence type from an item type and occurence indicator.
      Parameters:
      `item` - the item type. This parameter must be `null` if the occurance is `XQSequenceType.OCC_EMPTY`, and cannot be `null` for any other occurance indicator

      `occurence` - The occurence of the item type, must be one of `XQSequenceType.OCC_ZERO_OR_ONE`, `XQSequenceType.OCC_EXACTLY_ONE`, `XQSequenceType.OCC_ZERO_OR_MORE`, `XQSequenceType.OCC_ONE_OR_MORE`, `XQSequenceType.OCC_EMPTY`

      Returns:
      a new `XQSequenceType` representing the type of a sequence

      Throws:
      [`XQException`](XQException.md) - if (1) the `item` is `null` and the occurance is not `XQSequenceType.OCC_EMPTY`, (2) the `item` is not `null` and the occurance is `XQSequenceType.OCC_EMPTY`, (3) the occurence is not one of: `XQSequenceType.OCC_ZERO_OR_ONE`, `XQSequenceType.OCC_EXACTLY_ONE`, `XQSequenceType.OCC_ZERO_OR_MORE`, `XQSequenceType.OCC_ONE_OR_MORE`, `XQSequenceType.OCC_EMPTY` or (4) the underlying object implementing the interface is closed

    <!-- -->

    - #### createTextType

          XQItemType createTextType()
                             throws XQException

      Creates a new `XQItemType` object representing the XQuery `text()` type. The `XQItemType` object will have the item kind set to `XQItemType.XQITEMKIND_TEXT`.
      Returns:
      a new `XQItemType` representing the XQuery `text()` type

      Throws:
      [`XQException`](XQException.md) - if the underlying object implementing the interface is closed

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

- **[Prev Class](XQConstants.md)**
- **[Next Class](XQDataSource.md)**

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
