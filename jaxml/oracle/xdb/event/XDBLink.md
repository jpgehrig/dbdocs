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

- **[Prev Class](XDBInvalidOperationException.md)**
- **[Next Class](XDBPath.md)**

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

## **Class XDBLink**

- **java.lang.Object**

- - **oracle.xdb.event.XDBLink**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBLink
      extends java.lang.Object

  **This class stores information about the link of a resource.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                              |
    |--------------------|-------------------------------------------------------------------------------------|
    | `byte[]`           | `getChildOID``()`<br>Returns the OID of the resource that this link is pointing to. |
    | `java.lang.String` | `getLinkName``()`<br>Returns the name of this link.                                 |
    | `java.lang.String` | `getParentName``()`<br>Returns the name of the parent of this link.                 |
    | `byte[]`           | `getParentOID``()`<br>Returns the OID of the parent of this link.                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getParentName

          public java.lang.String getParentName()

      Returns the name of the parent of this link.
      Returns:
      The name of the parent folder.

    <!-- -->

    - #### getParentOID

          public byte[] getParentOID()

      Returns the OID of the parent of this link.
      Returns:
      The OID of the parent folder

    <!-- -->

    - #### getChildOID

          public byte[] getChildOID()

      Returns the OID of the resource that this link is pointing to.
      Returns:
      The OID of the resource

    <!-- -->

    - #### getLinkName

          public java.lang.String getLinkName()

      Returns the name of this link.
      Returns:
      The name of the link

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

- **[Prev Class](XDBInvalidOperationException.md)**
- **[Next Class](XDBPath.md)**

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
