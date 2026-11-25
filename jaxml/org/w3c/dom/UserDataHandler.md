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

- **[Prev Class](TypeInfo.md)**
- **Next Class**

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

**org.w3c.dom**

## **Interface UserDataHandler**

-

  ------------------------------------------------------------------------

  **
  **

      public interface UserDataHandler

  **When associating an object to a key on a node using `Node.setUserData()` the application can provide a handler that gets called when the node the object is associated to is being cloned, imported, or renamed. This can be used by the application to implement various behaviors regarding the data it associates to the DOM nodes. This interface defines that handler.**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                               |
    |-------------------|---------------------------------------------------------------------|
    | `static short`    | `NODE_ADOPTED`<br>The node is adopted, using `Node.adoptNode()`.    |
    | `static short`    | `NODE_CLONED`<br>The node is cloned, using `Node.cloneNode()`.      |
    | `static short`    | `NODE_DELETED`<br>The node is deleted.                              |
    | `static short`    | `NODE_IMPORTED`<br>The node is imported, using `Node.importNode()`. |
    | `static short`    | `NODE_RENAMED`<br>The node is renamed, using `Node.renameNode()`.   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                            |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handle``(short operation, java.lang.String key, java.lang.Object data, `[`Node`](Node.md)` src, `[`Node`](Node.md)` dst)`<br>This method is called whenever the node for which this handler is registered is imported or cloned. |

<!-- -->

- - ### Field Detail

    - #### NODE_CLONED

          static final short NODE_CLONED

      The node is cloned, using `Node.cloneNode()`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_IMPORTED

          static final short NODE_IMPORTED

      The node is imported, using `Node.importNode()`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_DELETED

          static final short NODE_DELETED

      The node is deleted.
      **Note:** This may not be supported or may not be reliable in certain environments, such as Java, where the implementation has no real control over when objects are actually deleted.

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_RENAMED

          static final short NODE_RENAMED

      The node is renamed, using `Node.renameNode()`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_ADOPTED

          static final short NODE_ADOPTED

      The node is adopted, using `Node.adoptNode()`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### handle

          void handle(short operation,
                      java.lang.String key,
                      java.lang.Object data,
                      Node src,
                      Node dst)

      This method is called whenever the node for which this handler is registered is imported or cloned.
      Any exceptions thrown inside a `UserDataHandler` will be ignored.
      Parameters:
      `operation` - Specifies the type of operation that is being performed on the node.

      `key` - Specifies the key for which this handler is being called.

      `data` - Specifies the data for which this handler is being called.

      `src` - Specifies the node being cloned, adopted, imported, or renamed. This is `null` when the node is being deleted.

      `dst` - Specifies the node newly created if any, or `null`.

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

- **[Prev Class](TypeInfo.md)**
- **Next Class**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
