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

- **[Prev Class](OXQPreparedExpression.md)**
- **[Next Class](OXQSerializationParameters.md)**

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

## **Interface OXQSequence**

- **All Superinterfaces:**
  **[OXQCloseable](OXQCloseable.md), [OXQItemAccessor](OXQItemAccessor.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQSequence
      extends OXQItemAccessor, OXQCloseable

  **Extensions to [`javax.xml.xquery.XQSequence`](../../../javax/xml/xquery/XQSequence.md).**
  **Use method [`OXQView.getSequence(XQSequence)`](OXQView.md) to access these extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQPreparedExpression expr = con.prepareExpression(query);
       XQSequence seq = expr.executeQuery();
       OXQSequence oseq = OXQView.getSequence(seq);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                       | Method and Description                                                                                                                        |
    |---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XQItem`](../../../javax/xml/xquery/XQItem.md)         | `getItem``(boolean independent)`<br>Gets the current item as an `XQItem` object.                                                              |
    | `java.io.InputStream`                                   | `getSequenceAsInputStream``(java.util.Properties props)`<br>Reads the entire sequence starting from the current position as an `InputStream`. |
    | [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) | `getXQView``()`<br>Returns the [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) instance corresponding to this instance.               |

    - ### Methods inherited from interface oracle.xml.xquery.[OXQItemAccessor](OXQItemAccessor.md)

      [`getAttributeValue`](OXQItemAccessor.md)`, `[`getItemAsInputStream`](OXQItemAccessor.md)`, `[`getItemKind`](OXQItemAccessor.md)`, `[`getNodeName`](OXQItemAccessor.md)`, `[`getTextValue`](OXQItemAccessor.md)

    <!-- -->

    - ### Methods inherited from interface oracle.xml.xquery.[OXQCloseable](OXQCloseable.md)

      [`enlistCloseable`](OXQCloseable.md)`, `[`enlistCloseable`](OXQCloseable.md)`, `[`enlistCloseable`](OXQCloseable.md)

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQSequence getXQView()

      Returns the [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) instance corresponding to this instance.
      Specified by:
      [`getXQView`](OXQItemAccessor.md) in interface [`OXQItemAccessor`](OXQItemAccessor.md)

      Returns:
      the sequence

    <!-- -->

    - #### getSequenceAsInputStream

          java.io.InputStream getSequenceAsInputStream(java.util.Properties props)
                                                throws XQException

      Reads the entire sequence starting from the current position as an `InputStream`. The serialization process might fail, in which case an exception is thrown.
      While the stream is being read, the application must not do any other concurrent operations on the sequence. The behavior of the stream is undefined if the underlying sequence position or state is changed by concurrent operations.

      After all bytes are read from the stream, the current position of the sequence is set to point after the last item. In the case of forward only sequences, this method may only be called if the current item has not yet been read through any of the get or write methods.

      Parameters:
      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Returns:
      an InputStream

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing any of the items in the sequence, (2) the sequence is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (4) in case of an error during serialization of the sequence as defined in *Section 12 Serialization, XQuery API for Java (XQJ) 1.0*

    <!-- -->

    - #### getItem

          XQItem getItem(boolean independent)
                  throws XQException

      Gets the current item as an `XQItem` object. In the case of forward only sequences, this method or any other get or write method may only be called once on the current item.

      When the `independent` parameter is `false`, this method is the same as [`XQSequence.getItem()`](../../../javax/xml/xquery/XQSequence.md). When the `independent` parameter is `true`, this method is essentially the same as calling `javax.xml.xquery.XQDataFactory.createItem(java.xml.xquery.XQSequence.getItem())`. In other words, when the `independent` parameter is true, this method returns an `XQItem` that is independent of the sequence. If the sequence is backed by a `PageManager`, creating an independent item may cause the item to be fully materialized in main memory.

      Parameters:
      `independent` - determines if the returned item is independent of the sequence

      Returns:
      an `XQItem` object

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors retrieving the item, or (2) in the case of a forward only sequence, a get or write method has already been invoked on the current item

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

- **[Prev Class](OXQPreparedExpression.md)**
- **[Next Class](OXQSerializationParameters.md)**

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
