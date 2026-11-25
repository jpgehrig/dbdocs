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

- **[Prev Class](DiffOpReceiver.md)**
- **[Next Class](Options.md)**

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

**oracle.xml.diff**

## **Class InsertDiffOp**

- **java.lang.Object**

- - **[oracle.xml.diff.DiffOp](DiffOp.md)**

  - - **oracle.xml.diff.InsertDiffOp**

<!-- -->

- **All Implemented Interfaces:**
  **java.lang.Comparable\<[DiffOp](DiffOp.md)\>**

  ------------------------------------------------------------------------

  **
  **

      public class InsertDiffOp
      extends DiffOp

  **InsertDiffOp. Models an insert-before-node diff operation.**

<!-- -->

-
  -

    ### **Nested Class Summary**

    -

      ### **Nested classes/interfaces inherited from class oracle.xml.diff.[DiffOp](DiffOp.md)**

      **[`DiffOp.Name`](DiffOp.Name.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                      | Method and Description                                                                                              |
    |----------------------------------------|---------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../org/w3c/dom/Node.md) | `getCurrent``()`<br>Returns the node to be deleted, for a delete `DiffOp`.                                          |
    | `java.lang.String`                     | `getCurrentXPath``()`<br>Returns the XPath to the node to be deleted, for a delete `DiffOp`.                        |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getNew``()`<br>Returns the node to be inserted or appended, for an insert or append `DiffOp`.                      |
    | [`DiffOp.Name`](DiffOp.Name.md)        | `getOpName``()`<br>Returns the name of the diff operation, one of: append-node, insert-before-node, or delete-node. |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getParent``()`<br>Returns the parent node, for an append `DiffOp`.                                                 |
    | `java.lang.String`                     | `getParentXPath``()`<br>Returns the parent node XPath, for an append `DiffOp`.                                      |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getSibling``()`<br>Returns the node to be inserted before, for an insert `DiffOp`                                  |
    | `java.lang.String`                     | `getSiblingXPath``()`<br>Returns the XPath to the node to be inserted before, for an insert `DiffOp`.               |

    - ### Methods inherited from class oracle.xml.diff.[DiffOp](DiffOp.md)

      [`compareTo`](DiffOp.md)`, `[`getPrefixToNamespace`](DiffOp.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getOpName

          public DiffOp.Name getOpName()

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the name of the diff operation, one of: append-node, insert-before-node, or delete-node.
      Specified by:
      [`getOpName`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `Name` containing the name of the diff operation, one of: `Name.INSERT_BY_APPENDING, Name.INSERT_BEFORE_NODE, Name.DELETE`

    <!-- -->

    - #### getCurrent

          public Node getCurrent()
                          throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the node to be deleted, for a delete `DiffOp`.
      Specified by:
      [`getCurrent`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `Node` to be deleted

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getNew

          public Node getNew()
                      throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the node to be inserted or appended, for an insert or append `DiffOp`.
      Specified by:
      [`getNew`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `Node` to be appended or inserted

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getSibling

          public Node getSibling()
                          throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the node to be inserted before, for an insert `DiffOp`
      Specified by:
      [`getSibling`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `Node` to be inserted before

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getParent

          public Node getParent()
                         throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the parent node, for an append `DiffOp`.
      Specified by:
      [`getParent`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      parent `Node` that the new child will be appended to

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getParentXPath

          public java.lang.String getParentXPath()
                                          throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the parent node XPath, for an append `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and the computational cost. For maxiumum performance, this option should be turned off.
      Specified by:
      [`getParentXPath`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `String` representing the XPath to the parent node, `null` if it is not available

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getSiblingXPath

          public java.lang.String getSiblingXPath()
                                           throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the XPath to the node to be inserted before, for an insert `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and computational cost. For maxiumum performance, this option should be turned off.
      Specified by:
      [`getSiblingXPath`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `String` representing the XPath to the node to be inserted before, `null` if it is not available

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCurrentXPath

          public java.lang.String getCurrentXPath()
                                           throws java.lang.Exception

      Description copied from class: [`DiffOp`](DiffOp.md)
      Returns the XPath to the node to be deleted, for a delete `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and computational cost. For maxiumum performance, this option should be turned off.
      Specified by:
      [`getCurrentXPath`](DiffOp.md) in class [`DiffOp`](DiffOp.md)

      Returns:
      `String` representing the XPath to the node to be deleted, `null` if it's not available

      Throws:
      `java.lang.Exception`

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

- **[Prev Class](DiffOpReceiver.md)**
- **[Next Class](Options.md)**

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
