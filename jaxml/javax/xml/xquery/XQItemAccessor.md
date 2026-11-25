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

- **[Prev Class](XQItem.md)**
- **[Next Class](XQItemType.md)**

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

## **Interface XQItemAccessor**

- **All Known Subinterfaces:**
  **[XQItem](XQItem.md), [XQResultItem](XQResultItem.md), [XQResultSequence](XQResultSequence.md), [XQSequence](XQSequence.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQItemAccessor

  **This interface represents a common interface for accessing the values of an XQuery item. All the get functions raise an exception if the underlying sequence object is not positioned on an item (e.g. if the sequence is positioned before the first item or after the last item).

  Example -**

        XQPreparedExpression expr = conn.prepareExpression("for $i ..");
        XQSequence result = expr.executeQuery();

        // create the ItemTypes for string and integer
        XQItemType strType = conn.createAtomicType(XQItemType.XQBASETYPE_STRING);
        XQItemType intType = conn.createAtomicType(XQItemType.XQBASETYPE_INTEGER);

        // posititioned before the first item
        while (result.next())
        {
          // If string or any of its subtypes, then get the string value out

          if (result.instanceOf(strType))
            String str = result.getAtomicValue();
          else if (result.instanceOf(intType))
             // if it is exactly an int
            int intval = result.getInt();
            ...

          // Alternatively, you can get the exact type out.
          XQItemType type = result.getItemType();

          // Now perform the comparison..
          if (type.equals(intType))
          { ... };

        }


  **See also:**
  - ***Table 6 - XQuery Atomic Types and Corresponding Java Object Types, XQuery API for Java (XQJ) 1.0*, for mapping of XQuery atomic types to Java object types. For example, if the XQuery value returned is of type `xs:unsignedByte`, then calling the `getObject()` method will return a Java object of type `java.lang.Short`.**
  - ***Table 7 - XQuery Node Types and Corresponding Java Object Types XQuery API for Java (XQJ) 1.0*, for the mapping of XQuery node types to the corresponding Java object types. For example, if the XQuery value returned is an element node, then calling the `getObject()` or `getNode()` method will return a Java object of type `org.w3.dom.Element`.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                      | Method and Description                                                                                                                                                                                                                                      |
    |----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                     | `getAtomicValue``()`<br>Gets the current item as a Java `String`.                                                                                                                                                                                           |
    | `boolean`                              | `getBoolean``()`<br>Gets the current item as a `boolean`.                                                                                                                                                                                                   |
    | `byte`                                 | `getByte``()`<br>Gets the current item as a `byte`.                                                                                                                                                                                                         |
    | `double`                               | `getDouble``()`<br>Gets the current item as a `double`.                                                                                                                                                                                                     |
    | `float`                                | `getFloat``()`<br>Gets the current item as a `float`.                                                                                                                                                                                                       |
    | `int`                                  | `getInt``()`<br>Gets the current item as an `int`.                                                                                                                                                                                                          |
    | `javax.xml.stream.XMLStreamReader`     | `getItemAsStream``()`<br>Read the current item as an `XMLStreamReader` object, as described in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*.                                        |
    | `java.lang.String`                     | `getItemAsString``(java.util.Properties props)`<br>Serializes the current item according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                                                                 |
    | [`XQItemType`](XQItemType.md)          | `getItemType``()`<br>Gets the type of the item.                                                                                                                                                                                                             |
    | `long`                                 | `getLong``()`<br>Gets the current item as a `long`.                                                                                                                                                                                                         |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getNode``()`<br>Gets the item as a DOM node.                                                                                                                                                                                                               |
    | `java.net.URI`                         | `getNodeUri``()`<br>Returns the URI for this item.                                                                                                                                                                                                          |
    | `java.lang.Object`                     | `getObject``()`<br>Gets the current item as an `Object`.                                                                                                                                                                                                    |
    | `short`                                | `getShort``()`<br>Gets the current item as a `short`.                                                                                                                                                                                                       |
    | `boolean`                              | `instanceOf``(`[`XQItemType`](XQItemType.md)` type)`<br>Checks if the item "matches" an item type, as defined in [*2.5.4.2 Matching an Item Type and an Item, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_matching_item).           |
    | `void`                                 | `writeItem``(java.io.OutputStream os, java.util.Properties props)`<br>Serializes the current item to a `Writer` according to [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                                    |
    | `void`                                 | `writeItem``(java.io.Writer ow, java.util.Properties props)`<br>Serializes the current item to a `Writer` according to [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                                          |
    | `void`                                 | `writeItemToResult``(`[`Result`](../transform/Result.md)` result)`<br>Writes the current item to a `Result`.                                                                                                                                                |
    | `void`                                 | `writeItemToSAX``(`[`ContentHandler`](../../../org/xml/sax/ContentHandler.md)` saxhdlr)`<br>Writes the current item to a SAX handler, as described in in *Section 12.2 Serializing an XDM instance into a SAX event stream, XQuery API for Java (XQJ) 1.0*. |

<!-- -->

- - ### Method Detail

    - #### getBoolean

          boolean getBoolean()
                      throws XQException

      Gets the current item as a `boolean`. The current item must be an atomic value of type `xs:boolean` or a subtype.
      Returns:
      a `boolean` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `boolean` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getByte

          byte getByte()
                throws XQException

      Gets the current item as a `byte`. The current item must be an atomic value of type `xs:decimal` or a subtype, and its value must be in the value space of `byte`.
      Returns:
      a `byte` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `byte` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getDouble

          double getDouble()
                    throws XQException

      Gets the current item as a `double`. The current item must be an atomic value of type `xs:double` or a subtype.
      Returns:
      a `double` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `double` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getFloat

          float getFloat()
                  throws XQException

      Gets the current item as a `float`. The current item must be an atomic value of type `xs:float` or a subtype.
      Returns:
      a `float` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `float` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getInt

          int getInt()
              throws XQException

      Gets the current item as an `int`. The current item must be an atomic value of type `xs:decimal` or a subtype, and its value must be in the value space of `int`.
      Returns:
      an `int` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `int` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getItemType

          XQItemType getItemType()
                          throws XQException

      Gets the type of the item.
      On a forward only sequence this method can be called independent of any other get or write method. It will not raise an error if such method has been called already, nor will it affect subsequent invocations of any other get or write method.
      Returns:
      the type of the item

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the type of the item, or (2) the underlying sequence or item is in a closed state

    <!-- -->

    - #### getAtomicValue

          java.lang.String getAtomicValue()
                                   throws XQException

      Gets the current item as a Java `String`. The current item must be an atomic value. This function casts the current item to an `xs:string` value according to the casting rules defined in [*17.1.2 Casting to xs:string and xs:untypedAtomic, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#casting_from_strings), and then returns the value as a Java `String`.
      Returns:
      the string representation of the item

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the item's value, (2) the item is not an atomic value, (3) there is an error when casting the item to a string representation, (4) the underlying sequence or item is in a closed state, or (5) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getLong

          long getLong()
                throws XQException

      Gets the current item as a `long`. The current item must be an atomic value of type `xs:decimal` or a subtype, and its value must be in the value space of `long`.
      Returns:
      a `long` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `long` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getNode

          Node getNode()
                throws XQException

      Gets the item as a DOM node. The current item must be a node. The type of the returned DOM node is governed by *Table 7 - XQuery Node Types and Corresponding Java Object Types XQuery API for Java (XQJ) 1.0* The instance of the returned node is implementation dependent. The node may be a reference or a copy of the internal state of the item. It is advisable to make a copy of the node if the application plans to modify it.
      Returns:
      a DOM node representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) if there are errors accessing the current item, (2) the current item is not a node, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getNodeUri

          java.net.URI getNodeUri()
                           throws XQException

      Returns the URI for this item. If the item is a document node, then this method returns the absolute URI of the resource from which the document node was constructed. If the document URI is not available, then the empty string is returned. If the document URI is available, the returned value is the same as if `fn:document-uri` were evaluated on this document node. If the item is of a node kind other than document node, then the returned URI is implementation-defined.
      On a forward only sequence this method can be called independent of any other get or write method. It will not raise an error if such method has been called already, nor will it affect subsequent invocations of any other get or write method on the current item.
      Returns:
      the document URI for this document node or the empty string if not available. For other node kinds, the result is implementation-defined

      Throws:
      [`XQException`](XQException.md) - if (1) if there are errors accessing the current item, (2) the current item is not a node, (3) if the underlying sequence or item is in a closed state

    <!-- -->

    - #### getObject

          java.lang.Object getObject()
                              throws XQException

      Gets the current item as an `Object`. The data type of the returned object will be the Java `Object` type as specified in *14.4 Mapping an XQuery Atomic Value to a Java Object Type and 14.5 Mapping an XQuery Node to a Java Object Type, XQuery API for Java (XQJ) 1.0*.
      Returns:
      an object representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) if there are errors accessing the current item, (2) if the underlying sequence or item is in a closed state, or (3) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### getItemAsStream

          javax.xml.stream.XMLStreamReader getItemAsStream()
                                                    throws XQException

      Read the current item as an `XMLStreamReader` object, as described in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*. Note that the serialization process might fail, in which case a `XQException` is thrown. While the stream is being read, the application MUST NOT do any other concurrent operations on the underlying item or sequence. The operation on the stream is undefined if the underlying sequence is repositioned or the state of the underlying item or sequence is changed by concurrent operations.
      Returns:
      an XML reader object as `XMLStreamReader`

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (4) in case of an error during serialization of the current item into a StAX event stream as defined in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*

    <!-- -->

    - #### getItemAsString

          java.lang.String getItemAsString(java.util.Properties props)
                                    throws XQException

      Serializes the current item according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information.
      Parameters:
      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Returns:
      the serialized representation of the item

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (4) if there are errors during serialization

    <!-- -->

    - #### getShort

          short getShort()
                  throws XQException

      Gets the current item as a `short`. The current item must be an atomic value of type `xs:decimal` or a subtype, and its value must be in the value space of `short`.
      Returns:
      a `short` representing the current item

      Throws:
      [`XQException`](XQException.md) - if (1) the conversion of the current item to a `short` fails, (2) if there are errors accessing the current item, (3) if the underlying sequence or item is in a closed state, or (4) in the case of forward only sequences, a get or write method was already invoked on the current item

    <!-- -->

    - #### instanceOf

          boolean instanceOf(XQItemType type)
                      throws XQException

      Checks if the item "matches" an item type, as defined in [*2.5.4.2 Matching an Item Type and an Item, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_matching_item). You can use this method to first check the type of the result before calling the specific get methods.

      Example -
            ...
            XQItemType strType = conn.createAtomicType(XQItemType.XQBASETYPE_STRING);
            XQItemType nodeType = conn.createNodeType();

            XQSequence result = preparedExpr.executeQuery();
            while (result.next())
            {
               // Generic check for node..
               if (result.instanceOf(nodeType))
                  org.w3.dom.Node node = result.getNode();
               else if (result.instanceOf(strType))
                  String str = result.getAtomicValue();
             }



      If either the type of the `XQItemAccessor` or the input `XQItemType` is not a built-in type, then this method is allowed to raise exception if it can NOT determine the instanceOf relationship due to the lack of the access of the XML schema that defines the user defined schema types if the `XQMetaData.isUserDefinedXMLSchemaTypeSupported()` method returns `false`.
      Otherwise, this method must determine if the type of the `XQItemAccessor` is an instance of the input `XQItemType`. Note even if `isUserDefinedXMLSchemaTypeSupported()` returns `false`, an XQJ implementation may still be able to determine the instanceOf relationship for certain cases involving user defined schema type. For example, if the type of an `XQItemAccessor` is of `mySchema:hatSize` sequence type and the input parameter `XQItemType` is of `item()` sequence type, the return value for instanceOf relationship should always be `true` even though the XQJ implementation does not know the precise type information of `mySchema:hatSize` type defined in XML schema `'mySchema'`.
      Parameters:
      `type` - item type to match

      Returns:
      `true` if this item matches the input item type as defined in [*2.5.4.2 Matching an Item Type and an Item, XQuery 1.0: An XML Query Language*](http://www.w3.org/TR/xquery/#id_matching_item), and `false` if it does not

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the item's type, (2) if the underlying sequence or item is in a closed state, (3) if the implementation is unable to determine the schema definition of a user defined schema type, or (4) the `type` parameter is `null`

    <!-- -->

    - #### writeItem

          void writeItem(java.io.OutputStream os,
                         java.util.Properties props)
                  throws XQException

      Serializes the current item to a `Writer` according to [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information.
      Parameters:
      `os` - the output stream into which the current item is to be serialized

      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) if there are errors during serialization, or (5) the `os` parameter is `null`

    <!-- -->

    - #### writeItem

          void writeItem(java.io.Writer ow,
                         java.util.Properties props)
                  throws XQException

      Serializes the current item to a `Writer` according to [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information.

      Warning: When outputting to a `Writer`, make sure the writer's encoding matches the encoding parameter if specified as a property or the default encoding.
      Parameters:
      `ow` - the writer object into which the current item is to be serialized

      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) if there are errors during serialization, or (5) the `ow` parameter is `null`

    <!-- -->

    - #### writeItemToSAX

          void writeItemToSAX(ContentHandler saxhdlr)
                       throws XQException

      Writes the current item to a SAX handler, as described in in *Section 12.2 Serializing an XDM instance into a SAX event stream, XQuery API for Java (XQJ) 1.0*. Note that the serialization process might fail, in which case a `XQException` is thrown. The specified `org.xml.sax.ContentHandler` can optionally implement the `org.xml.sax.LexicalHandler` interface. An implementation must check if the specified `ContentHandler` implements `LexicalHandler`. If the handler is a `LexicalHandler` comment nodes are reported, otherwise they will be silently ignored.
      Parameters:
      `saxhdlr` - the SAX content handler, optionally a lexical handler

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) in case of an error while serializing the XDM instance into a SAX event stream, or (5) the `saxhdlr` parameter is `null`

    <!-- -->

    - #### writeItemToResult

          void writeItemToResult(Result result)
                          throws XQException

      Writes the current item to a `Result`. First the item is normalized as described in [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Subsequently it is serialized to the `Result` object.
      Note that the normalization process can fail, in which case an `XQException` is thrown. An XQJ implementation must at least support the following implementations:
      - `javax.xml.transform.dom.DOMResult`
      - `javax.xml.transform.sax.SAXResult`
      - `javax.xml.transform.stream.StreamResult`

      Parameters:
      `result` - the result object into which the item is to be serialized

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) in case of an error while serializing the current item into the `Result` object, or (5) the `result` parameter is `null`

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

- **[Prev Class](XQItem.md)**
- **[Next Class](XQItemType.md)**

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
