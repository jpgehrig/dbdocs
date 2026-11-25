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

- **[Prev Class](XQQueryException.md)**
- **[Next Class](XQResultSequence.md)**

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

## **Interface XQResultItem**

- **All Superinterfaces:**
  **[XQItem](XQItem.md), [XQItemAccessor](XQItemAccessor.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQResultItem
      extends XQItem

  **This interface represents an immutable item object obtained from an `XQResultSequence` using the `getItem` method.**
  **A forward only result sequence does not support calling the getter methods multiple times on the same item. To work around this case, the `getItem` method can be used to obtain a result item and then getter methods may be called multiple times on this item.**

  **The `XQResultItem` object is dependent on the connection, expression and the sequence from which it was created and is only valid for the duration of those objects. Thus, if any one of those objects is closed, this `XQResultItem` object will be implicitly closed, and it can no longer be used. Similarly re-executing the expression also implicitly closes the associated result sequences, which in turn implicitly closes this result item.**

  **An XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call close method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions. Not closing this object implicitly or explicitly might result in serious memory leaks.**

  **Example -**

        XQPreparedExpression expr = conn.prepareExpression("for $i ..");
        XQResultSequence result = expr.executeQuery();

        // posititioned before the first item
        while (result.next())
        {
          XQResultItem item = result.getItem();
          // perform multiple gets on this item
          // get DOM
          org.w3.dom.Node node = item.getNode();
          // get SAX
          item.writeItemToSAX(saxHandler);

          item.close();  // good practice.  Item will get implicitly closed
                         // when the expression,  connection or sequence is closed.
        }

        result.close(); // explicitly close the result sequence



<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                             |
    |-----------------------------------|------------------------------------------------------------------------------------|
    | [`XQConnection`](XQConnection.md) | `getConnection``()`<br>Gets the XQuery connection associated with this result item |

    - ### Methods inherited from interface javax.xml.xquery.[XQItem](XQItem.md)

      [`close`](XQItem.md)`, `[`isClosed`](XQItem.md)

    <!-- -->

    - ### Methods inherited from interface javax.xml.xquery.[XQItemAccessor](XQItemAccessor.md)

      [`getAtomicValue`](XQItemAccessor.md)`, `[`getBoolean`](XQItemAccessor.md)`, `[`getByte`](XQItemAccessor.md)`, `[`getDouble`](XQItemAccessor.md)`, `[`getFloat`](XQItemAccessor.md)`, `[`getInt`](XQItemAccessor.md)`, `[`getItemAsStream`](XQItemAccessor.md)`, `[`getItemAsString`](XQItemAccessor.md)`, `[`getItemType`](XQItemAccessor.md)`, `[`getLong`](XQItemAccessor.md)`, `[`getNode`](XQItemAccessor.md)`, `[`getNodeUri`](XQItemAccessor.md)`, `[`getObject`](XQItemAccessor.md)`, `[`getShort`](XQItemAccessor.md)`, `[`instanceOf`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItemToResult`](XQItemAccessor.md)`, `[`writeItemToSAX`](XQItemAccessor.md)

<!-- -->

- - ### Method Detail

    - #### getConnection

          XQConnection getConnection()
                              throws XQException

      Gets the XQuery connection associated with this result item
      Returns:
      the connection associated with this result item

      Throws:
      [`XQException`](XQException.md) - if the result item is in a closed state

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

- **[Prev Class](XQQueryException.md)**
- **[Next Class](XQResultSequence.md)**

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
