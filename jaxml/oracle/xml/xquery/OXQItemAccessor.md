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

- **[Prev Class](OXQItem.md)**
- **[Next Class](OXQJavaResolverFactory.md)**

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

## **Interface OXQItemAccessor**

- **All Known Subinterfaces:**
  **[OXQItem](OXQItem.md), [OXQSequence](OXQSequence.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface OXQItemAccessor

  **Extensions to [`javax.xml.xquery.XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md).**
  **Use method [`OXQView.getItemAccessor(XQItemAccessor)`](OXQView.md) to access the extensions. For example:**

       OXQDataSource ds = new OXQDataSource();
       XQConnection con = ds.getConnection();
       XQItem item = con.createItemFromDocument(...); // XQItem extends XQItemAccessor
       OXQItemAccessor oitem = OXQView.getItemAccessor(item);
       ...


  **Since:**
  **12.1**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                |
    |-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                              | `getAttributeValue``()`<br>Returns the value of the item, if the item is an attribute node.                                                                                           |
    | `java.io.InputStream`                                           | `getItemAsInputStream``(java.util.Properties props)`<br>Reads the current item as an `InputStream` object, as described in *Section 12 Serialization, XQuery API for Java (XQJ) 1.0*. |
    | `int`                                                           | `getItemKind``()`<br>This is a convenience method that is equivalent to `getItemType().getItemKind()`.                                                                                |
    | `javax.xml.namespace.QName`                                     | `getNodeName``()`<br>Returns the node name for this item, if the item is an element or an attribute node.                                                                             |
    | `java.lang.String`                                              | `getTextValue``()`<br>Returns the value of the item, if the item is an text node.                                                                                                     |
    | [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) | `getXQView``()`<br>Returns the [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) instance corresponding to this instance.                                               |

<!-- -->

- - ### Method Detail

    - #### getXQView

          XQItemAccessor getXQView()

      Returns the [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) instance corresponding to this instance.
      Returns:
      the [`XQItemAccessor`](../../../javax/xml/xquery/XQItemAccessor.md) instance

    <!-- -->

    - #### getItemAsInputStream

          java.io.InputStream getItemAsInputStream(java.util.Properties props)
                                            throws XQException

      Reads the current item as an `InputStream` object, as described in *Section 12 Serialization, XQuery API for Java (XQJ) 1.0*. The serialization process might fail, in which case an exception is thrown.
      While the stream is being read, the application must not do any other concurrent operations on the underlying [`XQItem`](../../../javax/xml/xquery/XQItem.md) or [`XQSequence`](../../../javax/xml/xquery/XQSequence.md) instance. If the underlying sequence is repositioned or the state of the underlying item or sequence is changed, the behavior of the stream is undefined.

      Parameters:
      `props` - specifies the serialization parameters, `null` is considered equivalent to an empty `Properties` object

      Returns:
      the input stream

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing the current item or the underlying sequence, (2) the underlying sequence or item is in a closed state, (3) in the case of a forward only sequence, a get or write method has already been invoked on the current item, or (4) in case of an error during serialization

    <!-- -->

    - #### getNodeName

          javax.xml.namespace.QName getNodeName()
                                         throws XQException

      Returns the node name for this item, if the item is an element or an attribute node.
      Returns:
      the node name for this element or attribute node or `null` for all other kinds of items.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing the current item, (2) if the underlying sequence or item is in a closed state

    <!-- -->

    - #### getAttributeValue

          java.lang.String getAttributeValue()
                                      throws XQException

      Returns the value of the item, if the item is an attribute node.
      Returns:
      the value of an attribute node or `null` for all other kinds of items.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing the current item, (2) if the underlying sequence or item is in a closed state

    <!-- -->

    - #### getTextValue

          java.lang.String getTextValue()
                                 throws XQException

      Returns the value of the item, if the item is an text node.
      Returns:
      the value of a text node or `null` for all other kinds of items.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing the current item, (2) if the underlying sequence or item is in a closed state

    <!-- -->

    - #### getItemKind

          int getItemKind()
                   throws XQException

      This is a convenience method that is equivalent to `getItemType().getItemKind()`.
      Returns:
      kind of this item.

      Throws:
      [`XQException`](../../../javax/xml/xquery/XQException.md) - if (1) there are errors accessing the current item, (2) if the underlying sequence or item is in a closed state

      See Also:
      [`XQItemAccessor.getItemType()`](../../../javax/xml/xquery/XQItemAccessor.md), [`XQItemType.getItemKind()`](../../../javax/xml/xquery/XQItemType.md)

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

- **[Prev Class](OXQItem.md)**
- **[Next Class](OXQJavaResolverFactory.md)**

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
