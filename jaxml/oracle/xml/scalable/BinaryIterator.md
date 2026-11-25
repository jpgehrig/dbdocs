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

- **[Prev Class](BinaryIndex.md)**
- **[Next Class](BinaryNav.md)**

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

**oracle.xml.scalable**

## **Interface BinaryIterator**

-

  ------------------------------------------------------------------------

  **
  **

      public interface BinaryIterator

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description |
    |-----------------------------|------------------------|
    | `long`                      | `getBinaryOffset``()`  |
    | `long`                      | `getNodeIndex``()`     |
    | `javax.xml.namespace.QName` | `getNodeName``()`      |
    | `int`                       | `getNodeType``()`      |
    | `java.lang.String`          | `getNodeValue``()`     |
    | `boolean`                   | `hasNext``()`          |
    | `void`                      | `()`                   |

<!-- -->

- - ### Method Detail

    - #### hasNext

          boolean hasNext()

    <!-- -->

    - #### next

          void next()

    <!-- -->

    - #### getNodeType

          int getNodeType()

    <!-- -->

    - #### getNodeName

          javax.xml.namespace.QName getNodeName()

    <!-- -->

    - #### getBinaryOffset

          long getBinaryOffset()

    <!-- -->

    - #### getNodeIndex

          long getNodeIndex()

    <!-- -->

    - #### getNodeValue

          java.lang.String getNodeValue()

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

- **[Prev Class](BinaryIndex.md)**
- **[Next Class](BinaryNav.md)**

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
