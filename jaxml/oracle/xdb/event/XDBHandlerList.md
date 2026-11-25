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

- **[Prev Class](XDBHandler.md)**
- **[Next Class](XDBInvalidOperationException.md)**

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

**oracle.xdb.event**

## **Class XDBHandlerList**

- **java.lang.Object**

- - **oracle.xdb.event.XDBHandlerList**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBHandlerList
      extends java.lang.Object

  **This class is used to store and manage the list of `XDBHandler` objects.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                          |
    |-------------------------------|-------------------------------------------------------------------------------------------------|
    | `void`                        | `clear``()`<br>Clears the handler list                                                          |
    | [`XDBHandler`](XDBHandler.md) | `getFirst``()`<br>Returns the first handler in the list.                                        |
    | [`XDBHandler`](XDBHandler.md) | `getNext``()`<br>Returns the next handler in the list.                                          |
    | `void`                        | `remove``(`[`XDBHandler`](XDBHandler.md)` handler)`<br>Removes the given handler from the list. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getFirst

          public XDBHandler getFirst()

      Returns the first handler in the list.
      Returns:
      The first handler

    <!-- -->

    - #### getNext

          public XDBHandler getNext()

      Returns the next handler in the list.
      Returns:
      The next handler

    <!-- -->

    - #### remove

          public void remove(XDBHandler handler)

      Removes the given handler from the list.
      Parameters:
      `handler` - The handler to be removed from the list.

    <!-- -->

    - #### clear

          public void clear()

      Clears the handler list

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

- **[Prev Class](XDBHandler.md)**
- **[Next Class](XDBInvalidOperationException.md)**

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
