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

- **[Prev Class](OXQConstants.md)**
- **[Next Class](OXQDataSource.md)**

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

**oracle.xml.xquery**

## **Interface OXQDataFactory**

- **All Known Subinterfaces:**
  **[OXQConnection](OXQConnection.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQDataFactory

  **Extensions to [`javax.xml.xquery.XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md).**
  **Use method [`OXQView.getDataFactory(XQDataFactory)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQDataFactory factory = ds.getConnection(); // XQConnection extends XQDataFactory
       OXQDataFactory ofactory = OXQView.getDataFactory(factory);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                     |
    |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromBigDecimal``(java.math.BigDecimal value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                                            |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromBigInteger``(java.math.BigInteger value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                                            |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromBinary``(byte[] value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                                                              |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromCalendar``(javax.xml.datatype.XMLGregorianCalendar value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                           |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromDocument``(`[`OXQEntity`](OXQEntity.md)` value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from the given [`document entity`](OXQEntity.md).                       |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromDuration``(javax.xml.datatype.Duration value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                                       |
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)                 | `createItemFromQName``(javax.xml.namespace.QName value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates an item from a given value.                                                            |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)         | `createSequence``(`[`XQItem`](../../../javax/xml/xquery/XQItem.md)` item)`<br>Creates a sequence containing the specified `item`.                                                                                          |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)         | `createSequenceFromDocument``(java.io.InputStream value, java.lang.String baseURI, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates a sequence of one item from the given value.                |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)         | `createSequenceFromDocument``(`[`OXQEntity`](OXQEntity.md)` value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates a sequence of one item from the given [`document entity`](OXQEntity.md).    |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)         | `createSequenceFromDocument``(java.io.Reader value, java.lang.String baseURI, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates a sequence of one item from the given value.                     |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md)         | `createSequenceFromDocument``(javax.xml.stream.XMLStreamReader value, `[`XQItemType`](../../../javax/xml/xquery/XQItemType.md)` type)`<br>Creates a sequence of one item from the given value.                             |
    | [`XQSequenceType`](../../../javax/xml/xquery/XQSequenceType.md) | `createSequenceTypeFromJavaType``(java.lang.Class<?> javaType)`<br>Creates a new sequence type from the Java type according to type conversion rules defined in *14 Data Type Conversions, XQuery API for Java (XQJ) 1.0*. |
    | [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md)   | `getXQView``()`<br>Returns the [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) instance corresponding to this instance.                                                                                      |

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQDataFactory getXQView()

      Returns the [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) instance corresponding to this instance.
      Returns:
      the data factory

    <!-- -->

    - #### createItemFromDocument

          XQItem createItemFromDocument(OXQEntity value,
                                        XQItemType type)
                                 throws XQException

      Creates an item from the given [`document entity`](OXQEntity.md). The semantics of this method is equivalent to XQJ's `XQDataFactory.createItemFromDocument(...)` methods.
      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. Can be `null` as per XQJ's `XQDataFactory.createItemFromDocument(...)`

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if construction fails as per XQJ's `XQDataFactory.createItemFromDocument(...)`

    <!-- -->

    - #### createItemFromBigDecimal

          XQItem createItemFromBigDecimal(java.math.BigDecimal value,
                                          XQItemType type)
                                   throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromBigInteger

          XQItem createItemFromBigInteger(java.math.BigInteger value,
                                          XQItemType type)
                                   throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromBinary

          XQItem createItemFromBinary(byte[] value,
                                      XQItemType type)
                               throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromCalendar

          XQItem createItemFromCalendar(javax.xml.datatype.XMLGregorianCalendar value,
                                        XQItemType type)
                                 throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromDuration

          XQItem createItemFromDuration(javax.xml.datatype.Duration value,
                                        XQItemType type)
                                 throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createItemFromQName

          XQItem createItemFromQName(javax.xml.namespace.QName value,
                                     XQItemType type)
                              throws XQException

      Creates an item from a given value. The value is converted into an instance of the specified type according to the rule defined in *14.2 Mapping a Java Data Type to an XQuery Data Type, XQuery API for Java (XQJ) 1.0*. If the conversion fails, an exception will be thrown.
      Parameters:
      `value` - the value to be converted

      `type` - the type of the value to be bound to the external variable. The default type of the value is used in case `null` is specified

      Returns:
      the item

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the conversion of the value to an XDM instance failed, or (2) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequence

          XQSequence createSequence(XQItem item)
                             throws XQException

      Creates a sequence containing the specified `item`. The newly created `XQSequence` is scrollable and independent of any underlying `XQConnection`.
      Parameters:
      `item` - The `XQItem` to be converted

      Returns:
      `XQSequence` representing the sequence containing the specified `item`.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - (1) the `item` is null (2) the conversion from XQItem to XQSequence fails

    <!-- -->

    - #### createSequenceFromDocument

          XQSequence createSequenceFromDocument(OXQEntity value,
                                                XQItemType type)
                                         throws XQException

      Creates a sequence of one item from the given [`document entity`](OXQEntity.md). Note that, unlike the the sequence produced by the standard XQJ sequence creation methods, the sequence created by this method is forward-only and not necessarily materialized during creation. This method is needed because the XQJ standard [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) does not provide a way to create a sequence in a lazy way. The sequence created with this method can be bound lazily using `bindSequence(...)` of `XQPreparedExpression` or `XQExpression`
      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, [`XQItemType.XQITEMKIND_DOCUMENT_ELEMENT`](../../../javax/xml/xquery/XQItemType.md) or [`XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`](../../../javax/xml/xquery/XQItemType.md). An exception will be thrown if any other input type is specified.

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*. An exception will be thrown if the conversion fails.

      If the document [`OXQEntity`](OXQEntity.md) instance has a [`PageManager`](../scalable/PageManager.md) instance set using the [`OXQEntity.PROPERTY_DOCUMENT_PAGE_MANAGER`](OXQEntity.md) property, the value will be copied into the `PageManager`. The pages will be released (deleted) when the [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) returned by this method is closed.

      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      the item sequence

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequenceFromDocument

          XQSequence createSequenceFromDocument(java.io.Reader value,
                                                java.lang.String baseURI,
                                                XQItemType type)
                                         throws XQException

      Creates a sequence of one item from the given value. Note that, unlike the the sequence produced by the standard XQJ sequence creation methods, the sequence created by this method is forward-only and not materialized during creation. This method is needed because the XQJ standard [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) does not provide a way to create a sequence in a lazy way. The sequence created with this method can be bound lazily using `bindSequence(...)` of `XQPreparedExpression` or `XQExpression`
      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, [`XQItemType.XQITEMKIND_DOCUMENT_ELEMENT`](../../../javax/xml/xquery/XQItemType.md) or [`XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`](../../../javax/xml/xquery/XQItemType.md).

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.

      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      the sequence

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequenceFromDocument

          XQSequence createSequenceFromDocument(java.io.InputStream value,
                                                java.lang.String baseURI,
                                                XQItemType type)
                                         throws XQException

      Creates a sequence of one item from the given value. Note that, unlike the the sequence produced by the standard XQJ sequence creation methods, the sequence created by this method is forward-only and not materialized during creation. This method is needed because the XQJ standard [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) does not provide a way to create a sequence in a lazy way. The sequence created with this method can be bound lazily using `bindSequence(...)` of `XQPreparedExpression` or `XQExpression`
      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, [`XQItemType.XQITEMKIND_DOCUMENT_ELEMENT`](../../../javax/xml/xquery/XQItemType.md) or [`XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`](../../../javax/xml/xquery/XQItemType.md).

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.

      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      the sequence

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequenceFromDocument

          XQSequence createSequenceFromDocument(javax.xml.stream.XMLStreamReader value,
                                                XQItemType type)
                                         throws XQException

      Creates a sequence of one item from the given value. Note that, unlike the the sequence produced by the standard XQJ sequence creation methods, the sequence created by this method is forward-only and not materialized during creation. This method is needed because the XQJ standard [`XQDataFactory`](../../../javax/xml/xquery/XQDataFactory.md) does not provide a way to create a sequence in a lazy way. The sequence created with this method can be bound lazily using `bindSequence(...)` of `XQPreparedExpression` or `XQExpression`
      If the value represents a well-formed XML document, it results in a document node. The kind of the input type must be `null`, [`XQItemType.XQITEMKIND_DOCUMENT_ELEMENT`](../../../javax/xml/xquery/XQItemType.md) or [`XQItemType.XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`](../../../javax/xml/xquery/XQItemType.md).

      The value is converted into an instance of the specified type according to the rules defined in *14.3 Mapping a Java XML document to an XQuery document node, XQuery API for Java (XQJ) 1.0*.

      If the value is not well formed, or if a kind of the input type other than the values list above is specified, behavior is implementation defined and may raise an exception.

      Parameters:
      `value` - the value to be converted, cannot be `null`

      `type` - the type of the value for the created document node. If `null` is specified, it behaves as if `XQDataFactory.createDocumentElementType( XQDataFactory.createElementType(null, XQItemType.XQBASETYPE_XS_UNTYPED))` were passed in as the type parameter. That is, the type represents the XQuery sequence type `document-node(element(*, xs:untyped))`

      Returns:
      the sequence

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) the value argument is `null`, (2) the conversion of the value to an XDM instance failed, or (3) the underlying object implementing the interface is closed

    <!-- -->

    - #### createSequenceTypeFromJavaType

          XQSequenceType createSequenceTypeFromJavaType(java.lang.Class<?> javaType)
                                                 throws XQException

      Creates a new sequence type from the Java type according to type conversion rules defined in *14 Data Type Conversions, XQuery API for Java (XQJ) 1.0*.
      Parameters:
      `javaType` - Java type

      Returns:
      a new XQuery type corresponding to given Java type, or `null` if the mapping doesn't exist

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if the `javaType` argument is `null`

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

- **[Prev Class](OXQConstants.md)**
- **[Next Class](OXQDataSource.md)**

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
