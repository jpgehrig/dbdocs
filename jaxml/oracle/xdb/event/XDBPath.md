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

- **[Prev Class](XDBLink.md)**
- **[Next Class](XDBRenderStream.md)**

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

## **Class XDBPath**

- **java.lang.Object**

- - **oracle.xdb.event.XDBPath**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBPath
      extends java.lang.Object

  **This class stores information about the path of a resource**
  **Since:**
  **release specific (what release of product did this appear in)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                          |
    |--------------------|-----------------------------------------------------------------|
    | `java.lang.String` | `getName``()`<br>Returns the string representation of the path. |
    | `XDBPath`          | `getParentPath``(int level)`<br>Returns the path of the parent. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getParentPath

          public XDBPath getParentPath(int level)

      Returns the path of the parent. The level indicates the number of levels up the hierarchy. This value must be greater than zero. Level 1 means the immediate parent. If level exceeds the height of the tree then a null is returned.
      Parameters:
      `level` - - The number of levels up the hierarchy

      Returns:
      The path of the parent

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Returns the string representation of the path.
      Returns:
      The path of the resource

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

- **[Prev Class](XDBLink.md)**
- **[Next Class](XDBRenderStream.md)**

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
