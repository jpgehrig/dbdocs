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

- **[Prev Class](XQResultItem.md)**
- **[Next Class](XQSequence.md)**

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

## **Interface XQResultSequence**

- **All Superinterfaces:**
  **[XQItemAccessor](XQItemAccessor.md), [XQSequence](XQSequence.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQResultSequence
      extends XQSequence

  **This interface represents a sequence of items obtained as a result of evaluation XQuery expressions. The result sequence is tied to the `XQconnection` object on which the expression was evaluated.**
  **This sequence can be obtained by performing an `executeQuery` on the expression object. It represents a cursor-like interface.**

  **The `XQResultSequence` object is dependent on the connection and the expression from which it was created and is only valid for the duration of those objects. Thus, if any one of those objects is closed, this `XQResultSequence` object will be implicitly closed and it can no longer be used. Similarly re-executing the expression also implicitly closes the associated result sequences.**

  **An XQJ driver is not required to provide finalizer methods for the connection and other objects. Hence it is strongly recommended that users call close method explicitly to free any resources. It is also recommended that they do so under a final block to ensure that the object is closed even when there are exceptions. Not closing this object implicitly or explicitly might result in serious memory leaks.**

  **When the `XQResultSequence` is closed any `XQResultItem` objects obtained from it are also implicitly closed.**

  **Example -**


        XQPreparedExpression expr = conn.prepareExpression("for $i ..");
        XQResultSequence result = expr.executeQuery();

        // create the ItemTypes for string and integer
        XQItemType strType = conn.createAtomicType(XQItemType.XQBASETYPE_STRING);
        XQItemType intType = conn.createAtomicType(XQItemType.XQBASETYPE_INT);

        // posititioned before the first item
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

        result.close(); // explicitly close the result sequence



<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                 |
    |-----------------------------------|----------------------------------------------------------------------------------------|
    | [`XQConnection`](XQConnection.md) | `getConnection``()`<br>Gets the XQuery connection associated with this result sequence |

    - ### Methods inherited from interface javax.xml.xquery.[XQSequence](XQSequence.md)

      [`absolute`](XQSequence.md)`, `[`afterLast`](XQSequence.md)`, `[`beforeFirst`](XQSequence.md)`, `[`close`](XQSequence.md)`, `[`count`](XQSequence.md)`, `[`first`](XQSequence.md)`, `[`getItem`](XQSequence.md)`, `[`getPosition`](XQSequence.md)`, `[`getSequenceAsStream`](XQSequence.md)`, `[`getSequenceAsString`](XQSequence.md)`, `[`isAfterLast`](XQSequence.md)`, `[`isBeforeFirst`](XQSequence.md)`, `[`isClosed`](XQSequence.md)`, `[`isFirst`](XQSequence.md)`, `[`isLast`](XQSequence.md)`, `[`isOnItem`](XQSequence.md)`, `[`isScrollable`](XQSequence.md)`, `[`last`](XQSequence.md)`, , , `[`relative`](XQSequence.md)`, `[`writeSequence`](XQSequence.md)`, `[`writeSequence`](XQSequence.md)`, `[`writeSequenceToResult`](XQSequence.md)`, `[`writeSequenceToSAX`](XQSequence.md)

    <!-- -->

    - ### Methods inherited from interface javax.xml.xquery.[XQItemAccessor](XQItemAccessor.md)

      [`getAtomicValue`](XQItemAccessor.md)`, `[`getBoolean`](XQItemAccessor.md)`, `[`getByte`](XQItemAccessor.md)`, `[`getDouble`](XQItemAccessor.md)`, `[`getFloat`](XQItemAccessor.md)`, `[`getInt`](XQItemAccessor.md)`, `[`getItemAsStream`](XQItemAccessor.md)`, `[`getItemAsString`](XQItemAccessor.md)`, `[`getItemType`](XQItemAccessor.md)`, `[`getLong`](XQItemAccessor.md)`, `[`getNode`](XQItemAccessor.md)`, `[`getNodeUri`](XQItemAccessor.md)`, `[`getObject`](XQItemAccessor.md)`, `[`getShort`](XQItemAccessor.md)`, `[`instanceOf`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItemToResult`](XQItemAccessor.md)`, `[`writeItemToSAX`](XQItemAccessor.md)

<!-- -->

- - ### Method Detail

    - #### getConnection

          XQConnection getConnection()
                              throws XQException

      Gets the XQuery connection associated with this result sequence
      Returns:
      the connection associated with this result sequence

      Throws:
      [`XQException`](XQException.md) - if the result sequence is in a closed state

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

- **[Prev Class](XQResultItem.md)**
- **[Next Class](XQSequence.md)**

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
