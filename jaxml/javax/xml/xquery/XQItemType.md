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

- **[Prev Class](XQItemAccessor.md)**
- **[Next Class](XQMetaData.md)**

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

## **Interface XQItemType**

- **All Superinterfaces:**
  **[XQSequenceType](XQSequenceType.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQItemType
      extends XQSequenceType

  **The `XQItemType` interface represents an item type as defined in [*XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery).
  The `XQItemType` extends the `XQSequenceType` but restricts the occurrance indicator to be exactly one. This derivation allows passing an item type wherever a sequence type is expected, but not the other way. The `XQItemType` interface contains methods to represent information about the following aspects of an item type:**
  - **The kind of the item - one of `XQITEMKIND_*` constants**
  - **The base type of the item - one of the `XQBASETYPE_*` constants. For atomic types this is the closest matching built-in XML Schema type, for element and attributes the closest matching built-in XML Schema type this node is based on.**
  - **Name of the node, if any**
  - **Type name, if any. If present, then also whether the typename is an anonymous type**
  - **XML Schema URI associated with the type, if any**
  - **The nillability characteristics, if any**

  **An instance of the `XQItemType` is a standalone object that is independant of the `XQConnection` and any XQuery static or dynamic context.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                     |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `XQBASETYPE_ANYATOMICTYPE`<br>Represents the schema type `xs:anyAtomicType`                                                                                               |
    | `static int`      | `XQBASETYPE_ANYSIMPLETYPE`<br>Represents the schema type `xs:anySimpleType`                                                                                               |
    | `static int`      | `XQBASETYPE_ANYTYPE`<br>Represents the schema type xs:anyType                                                                                                             |
    | `static int`      | `XQBASETYPE_ANYURI`<br>Represents the schema type `xs:anyURI`                                                                                                             |
    | `static int`      | `XQBASETYPE_BASE64BINARY`<br>Represents the schema type `xs:base64Binary`                                                                                                 |
    | `static int`      | `XQBASETYPE_BOOLEAN`<br>Represents the schema type `xs:boolean`                                                                                                           |
    | `static int`      | `XQBASETYPE_BYTE`<br>Represents the schema type `xs:byte`                                                                                                                 |
    | `static int`      | `XQBASETYPE_DATE`<br>Represents the schema type `xs:date`                                                                                                                 |
    | `static int`      | `XQBASETYPE_DATETIME`<br>Represents the schema type `xs:dateTime`                                                                                                         |
    | `static int`      | `XQBASETYPE_DAYTIMEDURATION`<br>Represents the schema type `xs:dayTimeDuration`                                                                                           |
    | `static int`      | `XQBASETYPE_DECIMAL`<br>Represents the schema type `xs:decimal`                                                                                                           |
    | `static int`      | `XQBASETYPE_DOUBLE`<br>Represents the schema type `xs:double`                                                                                                             |
    | `static int`      | `XQBASETYPE_DURATION`<br>Represents the schema type `xs:duration`                                                                                                         |
    | `static int`      | `XQBASETYPE_ENTITIES`<br>Represents the schema type `xs:ENTITIES`                                                                                                         |
    | `static int`      | `XQBASETYPE_ENTITY`<br>Represents the schema type `xs:ENTITY`                                                                                                             |
    | `static int`      | `XQBASETYPE_FLOAT`<br>Represents the schema type `xs:float`                                                                                                               |
    | `static int`      | `XQBASETYPE_GDAY`<br>Represents the schema type `xs:gDay`                                                                                                                 |
    | `static int`      | `XQBASETYPE_GMONTH`<br>Represents the schema type `xs:gMonth`                                                                                                             |
    | `static int`      | `XQBASETYPE_GMONTHDAY`<br>Represents the schema type `xs:gMonthDay`                                                                                                       |
    | `static int`      | `XQBASETYPE_GYEAR`<br>Represents the schema type `xs:gYear`                                                                                                               |
    | `static int`      | `XQBASETYPE_GYEARMONTH`<br>Represents the schema type `xs:gYearMonth`                                                                                                     |
    | `static int`      | `XQBASETYPE_HEXBINARY`<br>Represents the schema type `xs:hexBinary`                                                                                                       |
    | `static int`      | `XQBASETYPE_ID`<br>Represents the schema type `xs:ID`                                                                                                                     |
    | `static int`      | `XQBASETYPE_IDREF`<br>Represents the schema type `xs:IDREF`                                                                                                               |
    | `static int`      | `XQBASETYPE_IDREFS`<br>Represents the schema type `xs:IDREFS`.                                                                                                            |
    | `static int`      | `XQBASETYPE_INT`<br>Represents the schema type `xs:int`                                                                                                                   |
    | `static int`      | `XQBASETYPE_INTEGER`<br>Represents the schema type `xs:integer`                                                                                                           |
    | `static int`      | `XQBASETYPE_LANGUAGE`<br>Represents the schema type `xs:language`                                                                                                         |
    | `static int`      | `XQBASETYPE_LONG`<br>Represents the schema type `xs:long`                                                                                                                 |
    | `static int`      | `XQBASETYPE_NAME`<br>Represents the schema type `xs:Name`                                                                                                                 |
    | `static int`      | `XQBASETYPE_NCNAME`<br>Represents the schema type `xs:NCName`                                                                                                             |
    | `static int`      | `XQBASETYPE_NEGATIVE_INTEGER`<br>Represents the schema type `xs:negativeInteger`                                                                                          |
    | `static int`      | `XQBASETYPE_NMTOKEN`<br>Represents the schema type `xs:NMToken`                                                                                                           |
    | `static int`      | `XQBASETYPE_NMTOKENS`<br>Represents the schema type `xs:NMTOKENS`                                                                                                         |
    | `static int`      | `XQBASETYPE_NONNEGATIVE_INTEGER`<br>Represents the schema type `xs:nonNegativeInteger`                                                                                    |
    | `static int`      | `XQBASETYPE_NONPOSITIVE_INTEGER`<br>Represents the schema type `xs:nonPositiveInteger`                                                                                    |
    | `static int`      | `XQBASETYPE_NORMALIZED_STRING`<br>Represents the schema type `xs:normalizedString`                                                                                        |
    | `static int`      | `XQBASETYPE_NOTATION`<br>Represents the schema type `xs:NOTATION`                                                                                                         |
    | `static int`      | `XQBASETYPE_POSITIVE_INTEGER`<br>Represents the schema type `xs:positiveInteger`                                                                                          |
    | `static int`      | `XQBASETYPE_QNAME`<br>Represents the schema type `xs:QName`                                                                                                               |
    | `static int`      | `XQBASETYPE_SHORT`<br>Represents the schema type `xs:short`                                                                                                               |
    | `static int`      | `XQBASETYPE_STRING`<br>Represents the schema type `xs:string`                                                                                                             |
    | `static int`      | `XQBASETYPE_TIME`<br>Represents the schema type `xs:time`                                                                                                                 |
    | `static int`      | `XQBASETYPE_TOKEN`<br>Represents the schema type `xs:token`                                                                                                               |
    | `static int`      | `XQBASETYPE_UNSIGNED_BYTE`<br>Represents the schema type `xs:unsignedByte`                                                                                                |
    | `static int`      | `XQBASETYPE_UNSIGNED_INT`<br>Represents the schema type `xs:unsignedInt`                                                                                                  |
    | `static int`      | `XQBASETYPE_UNSIGNED_LONG`<br>Represents the schema type `xs:unsignedLong`                                                                                                |
    | `static int`      | `XQBASETYPE_UNSIGNED_SHORT`<br>Represents the schema type `xs:unsignedShort`                                                                                              |
    | `static int`      | `XQBASETYPE_UNTYPED`<br>Represents the schema type xs:untyped                                                                                                             |
    | `static int`      | `XQBASETYPE_UNTYPEDATOMIC`<br>Represents the schema type `xs:untypedAtomic`                                                                                               |
    | `static int`      | `XQBASETYPE_YEARMONTHDURATION`<br>Represents the schema type `xs:yearMonthDuration`                                                                                       |
    | `static int`      | `XQITEMKIND_ATOMIC`<br>Some atomic type.                                                                                                                                  |
    | `static int`      | `XQITEMKIND_ATTRIBUTE`<br>Attribute node                                                                                                                                  |
    | `static int`      | `XQITEMKIND_COMMENT`<br>Comment node                                                                                                                                      |
    | `static int`      | `XQITEMKIND_DOCUMENT`<br>Document type (the type information represents the type of the document element)                                                                 |
    | `static int`      | `XQITEMKIND_DOCUMENT_ELEMENT`<br>Document node containing a single element node as its child (type information represents type of the element child)                      |
    | `static int`      | `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`<br>Document node containing a single schema element node as its child (type information represents type of the schema element child) |
    | `static int`      | `XQITEMKIND_ELEMENT`<br>Element node                                                                                                                                      |
    | `static int`      | `XQITEMKIND_ITEM`<br>Any kind of item                                                                                                                                     |
    | `static int`      | `XQITEMKIND_NODE`<br>Some node type                                                                                                                                       |
    | `static int`      | `XQITEMKIND_PI`<br>Processing instruction node                                                                                                                            |
    | `static int`      | `XQITEMKIND_SCHEMA_ATTRIBUTE`<br>Schema attribute node                                                                                                                    |
    | `static int`      | `XQITEMKIND_SCHEMA_ELEMENT`<br>Schema element node                                                                                                                        |
    | `static int`      | `XQITEMKIND_TEXT`<br>Text node                                                                                                                                            |

    -

      ### **Fields inherited from interface javax.xml.xquery.[XQSequenceType](XQSequenceType.md)**

      **[`OCC_EMPTY`](XQSequenceType.md)`, `[`OCC_EXACTLY_ONE`](XQSequenceType.md)`, `[`OCC_ONE_OR_MORE`](XQSequenceType.md)`, `[`OCC_ZERO_OR_MORE`](XQSequenceType.md)`, `[`OCC_ZERO_OR_ONE`](XQSequenceType.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                          |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                   | `equals``(java.lang.Object o)`<br>Compares the specified object with this item type for equality.                                                                                                                                                               |
    | `int`                       | `getBaseType``()`<br>Returns the base type of the item.                                                                                                                                                                                                         |
    | `int`                       | `getItemKind``()`<br>Returns the kind of the item.                                                                                                                                                                                                              |
    | `int`                       | `getItemOccurrence``()`<br>Returns the occurrence indicator for the item type.                                                                                                                                                                                  |
    | `javax.xml.namespace.QName` | `getNodeName``()`<br>Returns the name of the node in case the item kind is an `XQITEMKIND_DOCUMENT_ELEMENT`, `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`, `XQITEMKIND_ELEMENT`, `XQITEMKIND_SCHEMA_ELEMENT`, `XQITEMKIND_ATTRIBUTE`, or `XQITEMKIND_SCHEMA_ATTRIBUTE`. |
    | `java.lang.String`          | `getPIName``()`<br>Returns the name of the processing instruction type.                                                                                                                                                                                         |
    | `java.net.URI`              | `getSchemaURI``()`<br>Returns the schema location URI of the schema that contains the item's element or type definition.                                                                                                                                        |
    | `javax.xml.namespace.QName` | `getTypeName``()`<br>Represents a type name (global or local).                                                                                                                                                                                                  |
    | `int`                       | `hashCode``()`<br>Returns a hash code consistent with the definition of the equals method.                                                                                                                                                                      |
    | `boolean`                   | `isAnonymousType``()`<br>Represents whether the item type is an anonymous type in the schema.                                                                                                                                                                   |
    | `boolean`                   | `isElementNillable``()`<br>Returns whether the element type is nillable or not.                                                                                                                                                                                 |
    | `java.lang.String`          | `toString``()`<br>Returns a human-readable implementation-defined string representation of the item type.                                                                                                                                                       |

    - ### Methods inherited from interface javax.xml.xquery.[XQSequenceType](XQSequenceType.md)

      [`getItemType`](XQSequenceType.md)

<!-- -->

- - ### Field Detail

    - #### XQITEMKIND_ATOMIC

          static final int XQITEMKIND_ATOMIC

      Some atomic type.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_ATTRIBUTE

          static final int XQITEMKIND_ATTRIBUTE

      Attribute node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_COMMENT

          static final int XQITEMKIND_COMMENT

      Comment node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_DOCUMENT

          static final int XQITEMKIND_DOCUMENT

      Document type (the type information represents the type of the document element)
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_DOCUMENT_ELEMENT

          static final int XQITEMKIND_DOCUMENT_ELEMENT

      Document node containing a single element node as its child (type information represents type of the element child)
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT

          static final int XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT

      Document node containing a single schema element node as its child (type information represents type of the schema element child)
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_ELEMENT

          static final int XQITEMKIND_ELEMENT

      Element node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_ITEM

          static final int XQITEMKIND_ITEM

      Any kind of item
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_NODE

          static final int XQITEMKIND_NODE

      Some node type
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_PI

          static final int XQITEMKIND_PI

      Processing instruction node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_TEXT

          static final int XQITEMKIND_TEXT

      Text node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_SCHEMA_ELEMENT

          static final int XQITEMKIND_SCHEMA_ELEMENT

      Schema element node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQITEMKIND_SCHEMA_ATTRIBUTE

          static final int XQITEMKIND_SCHEMA_ATTRIBUTE

      Schema attribute node
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNTYPED

          static final int XQBASETYPE_UNTYPED

      Represents the schema type xs:untyped
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ANYTYPE

          static final int XQBASETYPE_ANYTYPE

      Represents the schema type xs:anyType
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ANYSIMPLETYPE

          static final int XQBASETYPE_ANYSIMPLETYPE

      Represents the schema type `xs:anySimpleType`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ANYATOMICTYPE

          static final int XQBASETYPE_ANYATOMICTYPE

      Represents the schema type `xs:anyAtomicType`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNTYPEDATOMIC

          static final int XQBASETYPE_UNTYPEDATOMIC

      Represents the schema type `xs:untypedAtomic`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DAYTIMEDURATION

          static final int XQBASETYPE_DAYTIMEDURATION

      Represents the schema type `xs:dayTimeDuration`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_YEARMONTHDURATION

          static final int XQBASETYPE_YEARMONTHDURATION

      Represents the schema type `xs:yearMonthDuration`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ANYURI

          static final int XQBASETYPE_ANYURI

      Represents the schema type `xs:anyURI`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_BASE64BINARY

          static final int XQBASETYPE_BASE64BINARY

      Represents the schema type `xs:base64Binary`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_BOOLEAN

          static final int XQBASETYPE_BOOLEAN

      Represents the schema type `xs:boolean`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DATE

          static final int XQBASETYPE_DATE

      Represents the schema type `xs:date`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_INT

          static final int XQBASETYPE_INT

      Represents the schema type `xs:int`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_INTEGER

          static final int XQBASETYPE_INTEGER

      Represents the schema type `xs:integer`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_SHORT

          static final int XQBASETYPE_SHORT

      Represents the schema type `xs:short`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_LONG

          static final int XQBASETYPE_LONG

      Represents the schema type `xs:long`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DATETIME

          static final int XQBASETYPE_DATETIME

      Represents the schema type `xs:dateTime`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DECIMAL

          static final int XQBASETYPE_DECIMAL

      Represents the schema type `xs:decimal`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DOUBLE

          static final int XQBASETYPE_DOUBLE

      Represents the schema type `xs:double`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_DURATION

          static final int XQBASETYPE_DURATION

      Represents the schema type `xs:duration`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_FLOAT

          static final int XQBASETYPE_FLOAT

      Represents the schema type `xs:float`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_GDAY

          static final int XQBASETYPE_GDAY

      Represents the schema type `xs:gDay`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_GMONTH

          static final int XQBASETYPE_GMONTH

      Represents the schema type `xs:gMonth`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_GMONTHDAY

          static final int XQBASETYPE_GMONTHDAY

      Represents the schema type `xs:gMonthDay`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_GYEAR

          static final int XQBASETYPE_GYEAR

      Represents the schema type `xs:gYear`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_GYEARMONTH

          static final int XQBASETYPE_GYEARMONTH

      Represents the schema type `xs:gYearMonth`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_HEXBINARY

          static final int XQBASETYPE_HEXBINARY

      Represents the schema type `xs:hexBinary`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NOTATION

          static final int XQBASETYPE_NOTATION

      Represents the schema type `xs:NOTATION`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_QNAME

          static final int XQBASETYPE_QNAME

      Represents the schema type `xs:QName`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_STRING

          static final int XQBASETYPE_STRING

      Represents the schema type `xs:string`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_TIME

          static final int XQBASETYPE_TIME

      Represents the schema type `xs:time`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_BYTE

          static final int XQBASETYPE_BYTE

      Represents the schema type `xs:byte`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NONPOSITIVE_INTEGER

          static final int XQBASETYPE_NONPOSITIVE_INTEGER

      Represents the schema type `xs:nonPositiveInteger`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NONNEGATIVE_INTEGER

          static final int XQBASETYPE_NONNEGATIVE_INTEGER

      Represents the schema type `xs:nonNegativeInteger`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NEGATIVE_INTEGER

          static final int XQBASETYPE_NEGATIVE_INTEGER

      Represents the schema type `xs:negativeInteger`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_POSITIVE_INTEGER

          static final int XQBASETYPE_POSITIVE_INTEGER

      Represents the schema type `xs:positiveInteger`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNSIGNED_LONG

          static final int XQBASETYPE_UNSIGNED_LONG

      Represents the schema type `xs:unsignedLong`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNSIGNED_INT

          static final int XQBASETYPE_UNSIGNED_INT

      Represents the schema type `xs:unsignedInt`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNSIGNED_SHORT

          static final int XQBASETYPE_UNSIGNED_SHORT

      Represents the schema type `xs:unsignedShort`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_UNSIGNED_BYTE

          static final int XQBASETYPE_UNSIGNED_BYTE

      Represents the schema type `xs:unsignedByte`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NORMALIZED_STRING

          static final int XQBASETYPE_NORMALIZED_STRING

      Represents the schema type `xs:normalizedString`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_TOKEN

          static final int XQBASETYPE_TOKEN

      Represents the schema type `xs:token`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_LANGUAGE

          static final int XQBASETYPE_LANGUAGE

      Represents the schema type `xs:language`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NAME

          static final int XQBASETYPE_NAME

      Represents the schema type `xs:Name`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NCNAME

          static final int XQBASETYPE_NCNAME

      Represents the schema type `xs:NCName`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NMTOKEN

          static final int XQBASETYPE_NMTOKEN

      Represents the schema type `xs:NMToken`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ID

          static final int XQBASETYPE_ID

      Represents the schema type `xs:ID`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_IDREF

          static final int XQBASETYPE_IDREF

      Represents the schema type `xs:IDREF`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ENTITY

          static final int XQBASETYPE_ENTITY

      Represents the schema type `xs:ENTITY`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_IDREFS

          static final int XQBASETYPE_IDREFS

      Represents the schema type `xs:IDREFS`. Valid only if the item kind is `XQITEMKIND_ELEMENT`, `XQITEMKIND_DOCUMENT_ELEMENT`, or `XQITEMKIND_ATTRIBUTE`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_ENTITIES

          static final int XQBASETYPE_ENTITIES

      Represents the schema type `xs:ENTITIES`
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XQBASETYPE_NMTOKENS

          static final int XQBASETYPE_NMTOKENS

      Represents the schema type `xs:NMTOKENS`
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getBaseType

          int getBaseType()
                   throws XQException

      Returns the base type of the item. One of the `XQBASETYPE_*` constants.

      XQJ defines a constant for each of the built-in schema types defined in XML Schema. For atomic types this is the closest matching built-in XML Schema type, for element and attributes the closest matching built-in XML Schema type this node is based on.
      Returns:
      int one of the `XQBASETYPE_*` constants indicating the basic type of the item

      Throws:
      [`XQException`](XQException.md) - if the item kind is not one of: `XQITEMKIND_DOCUMENT_ELEMENT`, `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`, `XQITEMKIND_ELEMENT`, `XQITEMKIND_SCHEMA_ELEMENT`, `XQITEMKIND_ATTRIBUTE`, `XQITEMKIND_SCHEMA_ATTRIBUTE`, or `XQITEMKIND_ATOMIC`

    <!-- -->

    - #### getItemKind

          int getItemKind()

      Returns the kind of the item. One of the `XQITEMKIND_*` constants.
      Returns:
      int one of the `XQITEMKIND_*` constants indicating the basic kind of the item

    <!-- -->

    - #### getItemOccurrence

          int getItemOccurrence()

      Returns the occurrence indicator for the item type. This method will always return the value `XQSequenceType.OCC_EXACTLY_ONE`.
      Specified by:
      [`getItemOccurrence`](XQSequenceType.md) in interface [`XQSequenceType`](XQSequenceType.md)

      Returns:
      int indicating the occurrence indicator

    <!-- -->

    - #### toString

          java.lang.String toString()

      Returns a human-readable implementation-defined string representation of the item type.
      Specified by:
      [`toString`](XQSequenceType.md) in interface [`XQSequenceType`](XQSequenceType.md)

      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      String a string representation of the item type

    <!-- -->

    - #### getNodeName

          javax.xml.namespace.QName getNodeName()
                                         throws XQException

      Returns the name of the node in case the item kind is an `XQITEMKIND_DOCUMENT_ELEMENT`, `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`, `XQITEMKIND_ELEMENT`, `XQITEMKIND_SCHEMA_ELEMENT`, `XQITEMKIND_ATTRIBUTE`, or `XQITEMKIND_SCHEMA_ATTRIBUTE`. For example, in the case of a type for `element "foo"` this will return the `QName foo`. For wildcard entries a `null` value will be returned.
      Returns:
      `QName` for the name of the element, attribute, or document element node. `null` if it is a wildcard

      Throws:
      [`XQException`](XQException.md) - if the item kind is not one of: `XQITEMKIND_DOCUMENT_ELEMENT`, `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`, `XQITEMKIND_ELEMENT`, `XQITEMKIND_SCHEMA_ELEMENT`, `XQITEMKIND_ATTRIBUTE`, or `XQITEMKIND_SCHEMA_ATTRIBUTE`

    <!-- -->

    - #### getSchemaURI

          java.net.URI getSchemaURI()

      Returns the schema location URI of the schema that contains the item's element or type definition. This method is implementation-definied and an implementation will return a `null` value if it does not support retrieving the schema location URI. If the item corresponds to a validated global element in a schema, the result will be the schema location URI to the XMLSchema containing the element definition. Otherwise if the item is a schema validated node, the result will be the schema location URI of the XMLSchema containing the type definition of that node. If the item is not schema validated, the result is `null`
      Returns:
      `URI` representing the schema location URI of the XMLSchema containing the global element definition or the type definition of the current item. `null` in case the item is not schema validated or if the implementation does not support retrieving the schema URI.

    <!-- -->

    - #### getTypeName

          javax.xml.namespace.QName getTypeName()
                                         throws XQException

      Represents a type name (global or local). This can be used to represent specific type name such as, element foo of type hatsize. The schema type name is represented as a single `QName`. If the return type is an anonymous type, the actual `QName` value returned is implementation defined.
      Returns:
      the `QName` of the schema type in case of a user defined or anonoymous types. For a built-in type, returns a predefined type name as QName (e.g.`xs:anyType`, `xs:decimal`, etc). Cannot be `null`

      Throws:
      [`XQException`](XQException.md) - if the item kind is not one of: `XQITEMKIND_DOCUMENT_ELEMENT`, `XQITEMKIND_DOCUMENT_SCHEMA_ELEMENT`, `XQITEMKIND_ATOMIC`, `XQITEMKIND_ELEMENT`, `XQITEMKIND_SCHEMA_ELEMENT`, `XQITEMKIND_ATTRIBUTE`, or `XQITEMKIND_SCHEMA_ATTRIBUTE`

    <!-- -->

    - #### isAnonymousType

          boolean isAnonymousType()

      Represents whether the item type is an anonymous type in the schema.
      Returns:
      `true` if the item type is an anonymous type in the schema, `false` otherwise

    <!-- -->

    - #### isElementNillable

          boolean isElementNillable()

      Returns whether the element type is nillable or not.
      Returns:
      `true` if the element type is nillable, `false` otherwise

    <!-- -->

    - #### getPIName

          java.lang.String getPIName()
                              throws XQException

      Returns the name of the processing instruction type. As such the item kind of this `XQItemType` must be `XQITEMKIND_PI`.
      Returns:
      the name of the processing instruction type. `null` if it is a wildcard

      Throws:
      [`XQException`](XQException.md) - if the item kind is not `XQITEMKIND_PI`

    <!-- -->

    - #### equals

          boolean equals(java.lang.Object o)

      Compares the specified object with this item type for equality. The result is `true` only if the argument is an item type object which represents the same XQuery item type.

      In order to comply with the general contract of `equals` and `hashCode` across different implementations the following algorithm must be used. Return `true` if and only if both objects are `XQItemType` and:
      - `getItemKind()` is equal
      - if `getBaseType()` is supported for the item kind, it must be equal
      - if `getNodeName()` is supported for the item kind, it must be equal
      - `getSchemaURI()` is equal
      - if `getTypeName()` is supported for the item kind, it must be equal
      - `isAnonymousType()` is equal
      - `isElementNillable()` is equal
      - if `getPIName()` is supported for the item kind, it must be equal

      Specified by:
      [`equals`](XQSequenceType.md) in interface [`XQSequenceType`](XQSequenceType.md)

      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `o` - an `XQItemType` object representing an XQuery item type

      Returns:
      `true` if the input item type object represents the same XQuery item type, `false` otherwise

    <!-- -->

    - #### hashCode

          int hashCode()

      Returns a hash code consistent with the definition of the equals method.

      In order to comply with the general contract of `equals` and `hashCode` across different implementations the following algorithm must be used:
            hashCode = this.getItemKind();
            if this.getSchemaURI != null
              hashCode = 31*hashCode + this.getSchemaURI().hashCode();
            if this.getBaseType() is supported for the item kind
              hashCode = 31*hashCode + this.getbaseType();
            if this.getNodeName () is supported for the item kind and
              this.getNodeName() != null
              hashCode = 31*hashCode + this.getNodeName().hashCode()
            if this.getTypeName () is supported for the item kind
              hashCode = 31*hashCode + this.getTypeName().hashCode();
            if this.getPIName () is supported for the item kind and
              this.getPIName () != null
              hashCode = 31*hashCode + this.getPIName().hashCode();


      Specified by:
      [`hashCode`](XQSequenceType.md) in interface [`XQSequenceType`](XQSequenceType.md)

      Overrides:
      `hashCode` in class `java.lang.Object`

      Returns:
      hash code for this item type

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

- **[Prev Class](XQItemAccessor.md)**
- **[Next Class](XQMetaData.md)**

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
