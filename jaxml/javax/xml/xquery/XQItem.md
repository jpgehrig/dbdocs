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

- **[Prev Class](XQExpression.md)**
- **[Next Class](XQItemAccessor.md)**

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

## **Interface XQItem**

- **All Superinterfaces:**
  **[XQItemAccessor](XQItemAccessor.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[XQResultItem](XQResultItem.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQItem
      extends XQItemAccessor

  **This interface represents an item in the XDM.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Close the item and release all the resources associated with this item. |
    | `boolean`         | `isClosed``()`<br>Checks if the item is closed.                                        |

    - ### Methods inherited from interface javax.xml.xquery.[XQItemAccessor](XQItemAccessor.md)

      [`getAtomicValue`](XQItemAccessor.md)`, `[`getBoolean`](XQItemAccessor.md)`, `[`getByte`](XQItemAccessor.md)`, `[`getDouble`](XQItemAccessor.md)`, `[`getFloat`](XQItemAccessor.md)`, `[`getInt`](XQItemAccessor.md)`, `[`getItemAsStream`](XQItemAccessor.md)`, `[`getItemAsString`](XQItemAccessor.md)`, `[`getItemType`](XQItemAccessor.md)`, `[`getLong`](XQItemAccessor.md)`, `[`getNode`](XQItemAccessor.md)`, `[`getNodeUri`](XQItemAccessor.md)`, `[`getObject`](XQItemAccessor.md)`, `[`getShort`](XQItemAccessor.md)`, `[`instanceOf`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItem`](XQItemAccessor.md)`, `[`writeItemToResult`](XQItemAccessor.md)`, `[`writeItemToSAX`](XQItemAccessor.md)

<!-- -->

- - ### Method Detail

    - #### close

          void close()
              throws XQException

      Close the item and release all the resources associated with this item. No method other than the `isClosed` or `close` method may be called once the item is closed. Calling close on an `XQItem` object that is already closed has no effect.
      Throws:
      [`XQException`](XQException.md) - if there is an error during closing the item

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the item is closed.
      Returns:
      `boolean` `true` if the item is in a closed state, `false` otherwise

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

- **[Prev Class](XQExpression.md)**
- **[Next Class](XQItemAccessor.md)**

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
