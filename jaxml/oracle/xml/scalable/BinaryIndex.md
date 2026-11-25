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

- **Prev Class**
- **[Next Class](BinaryIterator.md)**

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

## **Class BinaryIndex**

- **java.lang.Object**

- - **oracle.xml.scalable.BinaryIndex**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public abstract class BinaryIndex
      extends java.lang.Object

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `BinaryIndex``()`           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                            |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static BinaryIndex`        | `buildIndex``(`[`InfosetReader`](InfosetReader.md)` reader, long size)`<br>Factory method to create concreet index class based on binary size The actual index will be the smallest one that can handle the size. |
    | `static BinaryIndex`        | `createIndex``(int size)`                                                                                                                                                                                         |
    | `void`                      | `endElement``()`                                                                                                                                                                                                  |
    | `BinaryIndex`               | `enlargeIndex``()`                                                                                                                                                                                                |
    | [`BinaryNav`](BinaryNav.md) | `getNavigator``()`<br>Create navigator from the index                                                                                                                                                             |
    | `void`                      | `setStream``(`[`BinaryStream`](BinaryStream.md)` stream)`                                                                                                                                                         |
    | `boolean`                   | `startElement``(long idx)`                                                                                                                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BinaryIndex

          public BinaryIndex()

  <!-- -->

  - ### Method Detail

    - #### getNavigator

          public BinaryNav getNavigator()

      Create navigator from the index
      Returns:
      a BinaryNave object

    <!-- -->

    - #### buildIndex

          public static BinaryIndex buildIndex(InfosetReader reader,
                                               long size)
                                        throws java.lang.Exception

      Factory method to create concreet index class based on binary size The actual index will be the smallest one that can handle the size.
      Parameters:
      `reader` - -- InfosetReader to read binary data

      `size` - -- the size of binary data

      Returns:
      index -- the actual index built

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createIndex

          public static BinaryIndex createIndex(int size)

    <!-- -->

    - #### setStream

          public void setStream(BinaryStream stream)

    <!-- -->

    - #### enlargeIndex

          public BinaryIndex enlargeIndex()

    <!-- -->

    - #### startElement

          public boolean startElement(long idx)

    <!-- -->

    - #### endElement

          public void endElement()

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

- **Prev Class**
- **[Next Class](BinaryIterator.md)**

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
