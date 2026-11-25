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

- **[Prev Class](XQResultSequence.md)**
- **[Next Class](XQSequenceType.md)**

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

## **Interface XQSequence**

- **All Superinterfaces:**
  **[XQItemAccessor](XQItemAccessor.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[XQResultSequence](XQResultSequence.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQSequence
      extends XQItemAccessor

  **This interface represents a sequence of items as defined in the XDM. The sequence may be materialized or non-materialized.**
  **The `next` method is useful to position the `XQSequence` over the next item in the sequence. If the scrollability is `XQConstants.SCROLLTYPE_SCROLLABLE`, then the `previous` method can be called to move backwards. In the case of a forward only sequence, the get methods may be only called once per item. To perform multiple gets on an item, extract the item first from the sequence using the `getItem` method and then operate on the `XQItem` object.**


        XQPreparedExpression expr = conn.prepareExpression("for $i ..");
        XQSequence result = expr.executeQuery();

        // create the ItemTypes for string and integer
        XQItemType strType = conn.createAtomicType(XQItemType.XQBASETYPE_STRING);
        XQItemType intType = conn.createAtomicType(XQItemType.XQBASETYPE_INT);

        // positioned before the first item
        while (result.next())
        {
          XQItemType type = result.getItemType();

          // If string, then get the string value out
          if (type.equals(strType))
            String str = result.getAtomicValue();
          else if (type.equals(intType))  // if it is an integer..
            int intval = result.getInt();

           ...
        }



  **In a sequence, the cursor may be positioned on an item, after the last item or before the first item. The `getPosition` method returns the current position number. A value of 0 indicates that it is positioned before the first item, a value of `count() + 1` indicates that it is positioned after the last item, and any other value indicates that it is positioned on the item at that position.**
  **For example, a position value of 1 indicates that it is positioned on the item at position 1.**

  **The `isOnItem` method may be used to find out if the cursor is positioned on the item. When the cursor is positioned on an item, the `next` method call will move the cursor to be on the next item.**

  **See also: *Section 12 Serialization, XQuery API for Java (XQJ) 1.0*, which describes some general information applicable to various XQJ serialization methods.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                  | Method and Description                                                                                                                                                                                                                                                                             |
    |------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                          | `absolute``(int itempos)`<br>Moves the `XQSequence`'s position to the given item number in this object.                                                                                                                                                                                            |
    | `void`                             | `afterLast``()`<br>Move to the position after the last item.                                                                                                                                                                                                                                       |
    | `void`                             | `beforeFirst``()`<br>Moves to the position before the first item.                                                                                                                                                                                                                                  |
    | `void`                             | `close``()`<br>Closes the sequence and frees all resources associated with this sequence.                                                                                                                                                                                                          |
    | `int`                              | `count``()`<br>Returns a number indicating the number of items in the sequence.                                                                                                                                                                                                                    |
    | `boolean`                          | `first``()`<br>Moves to the first item in the sequence.                                                                                                                                                                                                                                            |
    | [`XQItem`](XQItem.md)              | `getItem``()`<br>Get the current item as an immutable `XQItem` object.                                                                                                                                                                                                                             |
    | `int`                              | `getPosition``()`<br>Gets the current cursor position.                                                                                                                                                                                                                                             |
    | `javax.xml.stream.XMLStreamReader` | `getSequenceAsStream``()`<br>Read the entire sequence starting from the current position as an `XMLStreamReader` object, as described in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*.                                     |
    | `java.lang.String`                 | `getSequenceAsString``(java.util.Properties props)`<br>Serializes the sequence starting from the current position to a String according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                                                         |
    | `boolean`                          | `isAfterLast``()`<br>Checks if the current position is after the last item in the sequence.                                                                                                                                                                                                        |
    | `boolean`                          | `isBeforeFirst``()`<br>Checks if the current position before the first item in the sequence.                                                                                                                                                                                                       |
    | `boolean`                          | `isClosed``()`<br>Checks if the sequence is closed.                                                                                                                                                                                                                                                |
    | `boolean`                          | `isFirst``()`<br>Checks if the current position at the first item in the sequence.                                                                                                                                                                                                                 |
    | `boolean`                          | `isLast``()`<br>Checks if the current position at the last item in the sequence.                                                                                                                                                                                                                   |
    | `boolean`                          | `isOnItem``()`<br>Check if the sequence is positioned on an item or not.                                                                                                                                                                                                                           |
    | `boolean`                          | `isScrollable``()`<br>Checks if the sequence is scrollable.                                                                                                                                                                                                                                        |
    | `boolean`                          | `last``()`<br>Moves to the last item in the sequence.                                                                                                                                                                                                                                              |
    | `boolean`                          | `()`<br>Moves to the next item in the sequence.                                                                                                                                                                                                                                                    |
    | `boolean`                          | `()`<br>Moves to the previous item in the sequence.                                                                                                                                                                                                                                                |
    | `boolean`                          | `relative``(int itempos)`<br>Moves the cursor a relative number of items, either positive or negative.                                                                                                                                                                                             |
    | `void`                             | `writeSequence``(java.io.OutputStream os, java.util.Properties props)`<br>Serializes the sequence starting from the current position to an `OutputStream` according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                             |
    | `void`                             | `writeSequence``(java.io.Writer ow, java.util.Properties props)`<br>Serializes the sequence starting from the current position to a Writer according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/).                                            |
    | `void`                             | `writeSequenceToResult``(`[`Result`](../transform/Result.md)` result)`<br>Writes the entire sequence starting from the current position to a `Result`.                                                                                                                                             |
    | `void`                             | `writeSequenceToSAX``(`[`ContentHandler`](../../../org/xml/sax/ContentHandler.md)` saxhdlr)`<br>Writes the entire sequence starting from the current position to a SAX handler, as described in *Section 12.2 Serializing an XDM instance into a SAX event stream, XQuery API for Java (XQJ) 1.0*. |

    - ### Methods inherited from interface javax.xml.xquery.[XQItemAccessor](XQItemAccessor.md)

      [`getAtomicValue`](XQItemAccessor.md)`, `[`getBoolean`](XQItemAccessor.md)`, `[`getByte`](XQItemAccessor.md)`, `[`getDouble`](XQItemAccessor.md)`, `[`getFloat`](XQItemAccessor.md)`, `[`getInt`](XQItemAccessor.md)`, `[`getItemAsStream`](XQItemAccessor.md)`, `[`getItemAsString`](XQItemAccessor.md)`, `[`getItemType`](XQItemAccessor.md)`, `[`getLong`](XQItemAccessor.md)`, `[`getNode`](XQItemAccessor.md)`, `[`getNodeUri`](XQItemAccessor.md)`, `[`getObject`](XQItemAccessor.md)`, `[`getShort`](XQItemAccessor.md)`, `[`instanceOf`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItemToResult`](XQItemAccessor.md)`, `[`writeItemToSAX`](XQItemAccessor.md)

<!-- -->

- - ### Method Detail

    - #### absolute

          boolean absolute(int itempos)
                    throws XQException

      Moves the `XQSequence`'s position to the given item number in this object. If the item number is positive, the `XQSequence` moves to the given item number with respect to the beginning of the `XQSequence`.
      The first item is item 1, the second is item 2, and so on.

      If the given item number is negative, the `XQSequence` positions itself on an absolute item position with respect to the end of the sequence.

      For example, calling the method `absolute(-1)` positions the `XQSequence` on the last item; calling the method `absolute(-2)` moves the `XQSequence` to the next-to-last item, and so on. `absolute(0)` will position the sequence before the first item.

      An attempt to position the sequence beyond the first/last item set leaves the current position to be before the first item or after the last item.

      Calling this method on an empty sequence will return `false`.

      Parameters:
      `itempos` - the item position to jump to

      Returns:
      `true` if the current position is within the sequence, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### afterLast

          void afterLast()
                  throws XQException

      Move to the position after the last item.
      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### beforeFirst

          void beforeFirst()
                    throws XQException

      Moves to the position before the first item.
      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### close

          void close()
              throws XQException

      Closes the sequence and frees all resources associated with this sequence. Closing an `XQSequence` object also implicitly closes all `XQItem` objects obtained from it. All methods other than the `isClosed` or `close` method will raise exceptions when invoked after closing the sequence. Calling `close` on an `XQSequence` object that is already closed has no effect.
      Throws:
      [`XQException`](XQException.md) - if there are errors during closing of the sequence

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the sequence is closed.
      Returns:
      `true` if the sequence is in a closed state, `false` otherwise

    <!-- -->

    - #### count

          int count()
             throws XQException

      Returns a number indicating the number of items in the sequence.
      Returns:
      the number of items in this sequence

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward-only, or (2) the sequence is closed

    <!-- -->

    - #### getPosition

          int getPosition()
                   throws XQException

      Gets the current cursor position.
      0 indicates that the position is before the first item and `count() + 1` indicates position after the last item. A specific position indicates that the cursor is positioned on the item at that position. Use the `isOnItem` method to verify if the cursor is positioned on the item.

      Calling this method on an empty sequence will return `0`.

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward-only, or (2) the sequence is closed

    <!-- -->

    - #### isOnItem

          boolean isOnItem()
                    throws XQException

      Check if the sequence is positioned on an item or not. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the sequence is currently positioned on an item, `false` if sequence is positioned before the first item, or after the last item

      Throws:
      [`XQException`](XQException.md) - if the sequence is in a closed state

    <!-- -->

    - #### isScrollable

          boolean isScrollable()
                        throws XQException

      Checks if the sequence is scrollable.
      Returns:
      `true` if the sequence can be scrolled backward or forward, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if the sequence is in a closed state

    <!-- -->

    - #### first

          boolean first()
                 throws XQException

      Moves to the first item in the sequence. The method returns `true`, if it was able to move to the first item in the sequence `false`, otherwise. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the sequence was positioned on the first item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### getItem

          XQItem getItem()
                  throws XQException

      Get the current item as an immutable `XQItem` object. In case of an `XQResultSequence`, the item is an `XQResultItem`. In the case of forward only sequences, this method or any other get or write method may only be called once on the curent item.
      The `XQItem` object is dependent on the sequence from which it was created and is only valid for the duration of `XQSequence` lifetime. Thus, the `XQSequence` is closed, this `XQItem` object will be implicitly closed and it can no longer be used.

      Returns:
      an `XQItem` object

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors retrieving the item, or (2) in the case of a forward only sequence, a get or write method has already been invoked on the current item.

    <!-- -->

    - #### getSequenceAsStream

          javax.xml.stream.XMLStreamReader getSequenceAsStream()
                                                        throws XQException

      Read the entire sequence starting from the current position as an `XMLStreamReader` object, as described in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*. Note that the serialization process might fail, in which case a `XQException` is thrown. While the stream is being read, the application MUST NOT do any other concurrent operations on the sequence. The operation on the stream is undefined if the underlying sequence position or state is changed by concurrent operations. After all items are written to the stream, the current position of the cursor is set to point after the last item. Also, in the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods.
      Returns:
      an XML reader object as `XMLStreamReader`

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing any of the items in the sequence, (2) the sequence is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (4) in case of an error during serialization of the sequence into a StAX event stream as defined in *Section 12.1 Serializing an XDM instance into a StAX event stream (XMLStreamReader), XQuery API for Java (XQJ) 1.0*

    <!-- -->

    - #### getSequenceAsString

          java.lang.String getSequenceAsString(java.util.Properties props)
                                        throws XQException

      Serializes the sequence starting from the current position to a String according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information. Reading the sequence during the serialization process performs implicit next operations to read the items. After all items are written to the stream, the current position of the cursor is set to point after the last item. Also, in the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods.
      Parameters:
      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Returns:
      the serialized representation of the sequence

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the items in the sequence, (2) there are errors during serialization, (3) the sequence is in a closed state, or (4) in the case of a forward only sequence, a get or write method has already been invoked on the current item

    <!-- -->

    - #### isAfterLast

          boolean isAfterLast()
                       throws XQException

      Checks if the current position is after the last item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the current position is after the last item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### isBeforeFirst

          boolean isBeforeFirst()
                         throws XQException

      Checks if the current position before the first item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the current position is before the first item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### isFirst

          boolean isFirst()
                   throws XQException

      Checks if the current position at the first item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the current position is at the first item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### isLast

          boolean isLast()
                  throws XQException

      Checks if the current position at the last item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the current position is at the last item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### last

          boolean last()
                throws XQException

      Moves to the last item in the sequence. This method returns `true`, if it was able to move to the last item in the sequence `false`, otherwise. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the sequence was positioned on the last item, `false` otherwise

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state

    <!-- -->

    - #### next

          boolean next()
                throws XQException

      Moves to the next item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the new item is valid, `false` if there are no more items

      Throws:
      [`XQException`](XQException.md) - if the sequence is in a closed state

    <!-- -->

    - #### previous

          boolean previous()
                    throws XQException

      Moves to the previous item in the sequence. Calling this method on an empty sequence will return `false`.
      Returns:
      `true` if the new current position is within the sequence, (i.e., not before first); `false` otherwise.

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state.

    <!-- -->

    - #### relative

          boolean relative(int itempos)
                    throws XQException

      Moves the cursor a relative number of items, either positive or negative. Attempting to move beyond the first/last item in the sequence positions the sequence before/after the the first/last item. Calling `relative(0)` is valid, but does not change the cursor position.
      Note: Calling the method `relative(1)` is identical to calling the method `next` and calling the method `relative(-1)` is identical to calling the method `previous()`. Calling this method on an empty sequence will return `false`.

      Parameters:
      `itempos` - the item position to jump to

      Returns:
      `true` if the new current position is within the sequence (i.e., not before first or after last); `false` otherwise.

      Throws:
      [`XQException`](XQException.md) - if (1) the sequence is forward only, or (2) the sequence is in a closed state.

    <!-- -->

    - #### writeSequence

          void writeSequence(java.io.OutputStream os,
                             java.util.Properties props)
                      throws XQException

      Serializes the sequence starting from the current position to an `OutputStream` according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information. Reading the sequence during the serialization process performs implicit next operations to read the items. After all items are written to the stream, the current position of the cursor is set to point after the last item. Also, in the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods.
      Parameters:
      `os` - the output stream into which the sequence is to be serialized

      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the items in the sequence, (2) there are errors during serialization, (3) the sequence is in a closed state, (4) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (5) the `os` parameter is `null`

    <!-- -->

    - #### writeSequence

          void writeSequence(java.io.Writer ow,
                             java.util.Properties props)
                      throws XQException

      Serializes the sequence starting from the current position to a Writer according to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Serialization parameters, which influence how serialization is performed, can be specified. Refer to the [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/) and *Section 12 Serialization, XQuery API for Java (XQJ) 1.0* for more information.

      Warning: When outputting to a `Writer`, make sure the writer's encoding matches the encoding parameter if specified as a property or the default encoding.

      Reading the sequence during the serialization process performs implicit next operations to read the items. After all items are written to the stream, the current position of the cursor is set to point after the last item. Also, in the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods.
      Parameters:
      `ow` - the writer object into which the sequence is to be serialized

      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing the items in the sequence, (2) there are errors during serialization, (3) the sequence is in a closed state, (4) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (5) the `ow` parameter is `null`

    <!-- -->

    - #### writeSequenceToSAX

          void writeSequenceToSAX(ContentHandler saxhdlr)
                           throws XQException

      Writes the entire sequence starting from the current position to a SAX handler, as described in *Section 12.2 Serializing an XDM instance into a SAX event stream, XQuery API for Java (XQJ) 1.0*. Note that the serialization process might fail, in which case a `XQException` is thrown. After all items are written to the stream, the current position of the cursor is set to point after the last item. Also, in the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods. The specified `org.xml.sax.ContentHandler` can optionally implement the `org.xml.sax.LexicalHandler` interface. An implementation must check if the specified `ContentHandler` implements `LexicalHandler`. If the handler is a `LexicalHandler` comment nodes are reported, otherwise they will be silently ignored.
      Parameters:
      `saxhdlr` - the SAX content handler, optionally a lexical handler

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing any of the items in the sequence, (2) the sequence is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) in case of an error during serializing the XDM instance into a SAX event stream, or (5) the `saxhdlr` parameter is `null`

    <!-- -->

    - #### writeSequenceToResult

          void writeSequenceToResult(Result result)
                              throws XQException

      Writes the entire sequence starting from the current position to a `Result`. First the sequence is normalized as described in [*XSLT 2.0 and XQuery 1.0 serialization*](http://www.w3.org/TR/xslt-xquery-serialization/). Subsequently it is serialized to the `Result` object.
      Note that the normalization process can fail, in which case an `XQException` is thrown. An XQJ implementation must at least support the following implementations:
      - `javax.xml.transform.dom.DOMResult`
      - `javax.xml.transform.sax.SAXResult`
      - `javax.xml.transform.stream.StreamResult`


      Parameters:
      `result` - the result object into which the sequence is to be serialized

      Throws:
      [`XQException`](XQException.md) - if (1) there are errors accessing any of the items in the sequence, (2) the sequence is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, (4) in case of an error while serializing the sequence into the `Result` object, or (5) the `result` parameter is `null`

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

- **[Prev Class](XQResultSequence.md)**
- **[Next Class](XQSequenceType.md)**

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
