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

- **[Prev Class](BinaryIterator.md)**
- **[Next Class](BinaryStream.md)**

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

## **Class BinaryNav**

- **java.lang.Object**

- - **oracle.xml.scalable.BinaryNav**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class BinaryNav
      extends java.lang.Object

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static long`     | `DOC_IDX`             |
    | `static long`     | `NULL_IDX`            |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `BinaryNav``(`[`BinaryIndex`](BinaryIndex.md)` idx)`<br>Constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                         |
    |----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                           | `clone``()`<br>Clone the BinaryNav.                                                                                                                                            |
    | `int`                                        | `currentLevel``()`                                                                                                                                                             |
    | `boolean`                                    | `document``()`<br>Go to the document node                                                                                                                                      |
    | `boolean`                                    | `firstChild``()`<br>Move the cursor to the first child element if any                                                                                                          |
    | `java.lang.String`                           | `getAttribute``(java.lang.String tag)`<br>Access the attribute with given name for the current element                                                                         |
    | `java.lang.String`                           | `getAttributeNS``(java.lang.String namespace, java.lang.String localpart)`<br>Access the attribute with given name and namespace for the current element                       |
    | [`SAXAttrList`](../parser/v2/SAXAttrList.md) | `getAttributes``()`<br>Access the attributes for the current element                                                                                                           |
    | [`BinaryIndex`](BinaryIndex.md)              | `getBinaryIndex``()`<br>Get the binary index this base on                                                                                                                      |
    | `long`                                       | `getCurrentIndex``()`<br>Get the current element's index                                                                                                                       |
    | `long`                                       | `getLocator``()`                                                                                                                                                               |
    | `java.lang.String`                           | `getNamespace``()`                                                                                                                                                             |
    | `java.lang.String`                           | `getNodeValue``()`<br>Get the string value for the current element                                                                                                             |
    | `javax.xml.namespace.QName`                  | `getQName``()`                                                                                                                                                                 |
    | [`InfosetReader`](InfosetReader.md)          | `getReader``()`<br>Get the inforset reader used in accesing binary data                                                                                                        |
    | `java.lang.String`                           | `getTagName``()`                                                                                                                                                               |
    | `boolean`                                    | `lastChild``()`<br>Move the cursor to the last child element if any                                                                                                            |
    | `boolean`                                    | `nextElementByQName``(javax.xml.namespace.QName qname)`<br>Move cursor to next element with given QName This will find the next element in document order with the given QName |
    | `boolean`                                    | `nextSibling``()`<br>Move the cursor to the following sibling element if any                                                                                                   |
    | `boolean`                                    | `nextSiblingByQName``(javax.xml.namespace.QName qname)`<br>Move cursor to next sibling element with given QName                                                                |
    | `boolean`                                    | `parent``()`<br>Move to the parent element if there is one                                                                                                                     |
    | `boolean`                                    | `prevSibling``()`<br>Move the cursor to the previous sibling element if any                                                                                                    |
    | `boolean`                                    | `root``()`<br>Go back to the root element                                                                                                                                      |
    | `boolean`                                    | `seekToIndex``(long idx)`<br>Move the cursor to the given element index                                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DOC_IDX

          public static final long DOC_IDX

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NULL_IDX

          public static final long NULL_IDX

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### BinaryNav

          public BinaryNav(BinaryIndex idx)

      Constructor
      Parameters:
      `idx` - - the binary index to create from

  <!-- -->

  - ### Method Detail

    - #### clone

          public java.lang.Object clone()

      Clone the BinaryNav.
      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      a copy of this BinaryNav instance.

    <!-- -->

    - #### getReader

          public InfosetReader getReader()

      Get the inforset reader used in accesing binary data
      Returns:
      the InfosetReader in use

    <!-- -->

    - #### getLocator

          public long getLocator()

    <!-- -->

    - #### currentLevel

          public int currentLevel()

    <!-- -->

    - #### getQName

          public javax.xml.namespace.QName getQName()

    <!-- -->

    - #### getNamespace

          public java.lang.String getNamespace()

    <!-- -->

    - #### getTagName

          public java.lang.String getTagName()

    <!-- -->

    - #### document

          public boolean document()

      Go to the document node
      Returns:
      true;

    <!-- -->

    - #### root

          public boolean root()

      Go back to the root element
      Returns:
      true;

    <!-- -->

    - #### parent

          public boolean parent()

      Move to the parent element if there is one
      Returns:
      true if operation is successful, flase otherwise

    <!-- -->

    - #### nextSibling

          public boolean nextSibling()

      Move the cursor to the following sibling element if any
      Returns:
      true if operation is successful, flase otherwise

    <!-- -->

    - #### prevSibling

          public boolean prevSibling()

      Move the cursor to the previous sibling element if any
      Returns:
      true if operation is successful, flase otherwise

    <!-- -->

    - #### firstChild

          public boolean firstChild()

      Move the cursor to the first child element if any
      Returns:
      true if operation is successful, flase otherwise

    <!-- -->

    - #### lastChild

          public boolean lastChild()

      Move the cursor to the last child element if any
      Returns:
      true if operation is successful, flase otherwise

    <!-- -->

    - #### getAttributes

          public SAXAttrList getAttributes()

      Access the attributes for the current element
      Returns:
      SAXAttrList or null

    <!-- -->

    - #### getAttribute

          public java.lang.String getAttribute(java.lang.String tag)

      Access the attribute with given name for the current element
      Returns:
      String value or null

    <!-- -->

    - #### getAttributeNS

          public java.lang.String getAttributeNS(java.lang.String namespace,
                                                 java.lang.String localpart)

      Access the attribute with given name and namespace for the current element
      Returns:
      String value or null

    <!-- -->

    - #### getNodeValue

          public java.lang.String getNodeValue()

      Get the string value for the current element
      Returns:
      String value or null

    <!-- -->

    - #### nextSiblingByQName

          public boolean nextSiblingByQName(javax.xml.namespace.QName qname)

      Move cursor to next sibling element with given QName
      Parameters:
      `qname` - - the QName of element to search

      Returns:
      true if there is one, false if none

    <!-- -->

    - #### nextElementByQName

          public boolean nextElementByQName(javax.xml.namespace.QName qname)

      Move cursor to next element with given QName This will find the next element in document order with the given QName
      Parameters:
      `qname` - - the QName of element to search

      Returns:
      true if there is one, false if none

    <!-- -->

    - #### seekToIndex

          public boolean seekToIndex(long idx)

      Move the cursor to the given element index
      Parameters:
      `idx` - the element index to go to

      Returns:
      true if the operation is successful, false otherwise

    <!-- -->

    - #### getCurrentIndex

          public long getCurrentIndex()

      Get the current element's index
      Returns:
      index in long

    <!-- -->

    - #### getBinaryIndex

          public BinaryIndex getBinaryIndex()

      Get the binary index this base on
      Returns:
      BinaryIndex instance

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

- **[Prev Class](BinaryIterator.md)**
- **[Next Class](BinaryStream.md)**

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
