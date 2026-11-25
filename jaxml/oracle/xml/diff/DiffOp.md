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

- **[Prev Class](DeleteDiffOp.md)**
- **[Next Class](DiffOp.Name.md)**

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

## **Class DiffOp**

- **java.lang.Object**

- - **oracle.xml.diff.DiffOp**

<!-- -->

- **All Implemented Interfaces:**
  **java.lang.Comparable\<DiffOp\>**

  <!-- -->

  **Direct Known Subclasses:**
  **[AppendDiffOp](AppendDiffOp.md), [DeleteDiffOp](DeleteDiffOp.md), [InsertDiffOp](InsertDiffOp.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class DiffOp
      extends java.lang.Object
      implements java.lang.Comparable<DiffOp>

  **DiffOp. Models a diff operation, that represents a single delta between two inputs at a particular location in the input tree. A diff between two inputs is represented as a list of diff operations.**
  **For example, suppose we have two input XMLs: `<b1/>` and ``. If we run them through the `diff(...)` method, the minimal diff will contain a single diff operation: delete-node for the `<b1>` element.**

  **Currently supported diff operations are: *append-node, insert-before-node,* and *delete-node*.See [`DiffOp.Name`](DiffOp.Name.md).**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type | Class and Description            |
    |-------------------|----------------------------------|
    | `static class `   | [`DiffOp.Name`](DiffOp.Name.md)  |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `DiffOp``()`                |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                              |
    |--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
    | `int`                                                  | `compareTo``(DiffOp op)`                                                                                            |
    | `abstract `[`Node`](../../../org/w3c/dom/Node.md)      | `getCurrent``()`<br>Returns the node to be deleted, for a delete `DiffOp`.                                          |
    | `abstract java.lang.String`                            | `getCurrentXPath``()`<br>Returns the XPath to the node to be deleted, for a delete `DiffOp`.                        |
    | `abstract `[`Node`](../../../org/w3c/dom/Node.md)      | `getNew``()`<br>Returns the node to be inserted or appended, for an insert or append `DiffOp`.                      |
    | `abstract `[`DiffOp.Name`](DiffOp.Name.md)             | `getOpName``()`<br>Returns the name of the diff operation, one of: append-node, insert-before-node, or delete-node. |
    | `abstract `[`Node`](../../../org/w3c/dom/Node.md)      | `getParent``()`<br>Returns the parent node, for an append `DiffOp`.                                                 |
    | `abstract java.lang.String`                            | `getParentXPath``()`<br>Returns the parent node XPath, for an append `DiffOp`.                                      |
    | `java.util.HashMap<java.lang.String,java.lang.String>` | `getPrefixToNamespace``()`                                                                                          |
    | `abstract `[`Node`](../../../org/w3c/dom/Node.md)      | `getSibling``()`<br>Returns the node to be inserted before, for an insert `DiffOp`                                  |
    | `abstract java.lang.String`                            | `getSiblingXPath``()`<br>Returns the XPath to the node to be inserted before, for an insert `DiffOp`.               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DiffOp

          public DiffOp()

  <!-- -->

  - ### Method Detail

    - #### getOpName

          public abstract DiffOp.Name getOpName()

      Returns the name of the diff operation, one of: append-node, insert-before-node, or delete-node.
      Returns:
      `Name` containing the name of the diff operation, one of: `Name.INSERT_BY_APPENDING, Name.INSERT_BEFORE_NODE, Name.DELETE`

    <!-- -->

    - #### getCurrent

          public abstract Node getCurrent()
                                   throws java.lang.Exception

      Returns the node to be deleted, for a delete `DiffOp`.
      Returns:
      `Node` to be deleted

      Throws:
      `Exception` - if the `DiffOp` is not a delete

      `java.lang.Exception`

    <!-- -->

    - #### getNew

          public abstract Node getNew()
                               throws java.lang.Exception

      Returns the node to be inserted or appended, for an insert or append `DiffOp`.
      Returns:
      `Node` to be appended or inserted

      Throws:
      `Exception` - if the `DiffOp` not an insert or append

      `java.lang.Exception`

    <!-- -->

    - #### getSibling

          public abstract Node getSibling()
                                   throws java.lang.Exception

      Returns the node to be inserted before, for an insert `DiffOp`
      Returns:
      `Node` to be inserted before

      Throws:
      `Exception` - if the `DiffOp` not an insert

      `java.lang.Exception`

    <!-- -->

    - #### getParent

          public abstract Node getParent()
                                  throws java.lang.Exception

      Returns the parent node, for an append `DiffOp`.
      Returns:
      parent `Node` that the new child will be appended to

      Throws:
      `Exception` - if the `DiffOp` not an append

      `java.lang.Exception`

    <!-- -->

    - #### getParentXPath

          public abstract java.lang.String getParentXPath()
                                                   throws java.lang.Exception

      Returns the parent node XPath, for an append `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and the computational cost. For maxiumum performance, this option should be turned off.
      Returns:
      `String` representing the XPath to the parent node, `null` if it is not available

      Throws:
      `Exception` - if the `DiffOp` not an append

      `java.lang.Exception`

    <!-- -->

    - #### getSiblingXPath

          public abstract java.lang.String getSiblingXPath()
                                                    throws java.lang.Exception

      Returns the XPath to the node to be inserted before, for an insert `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and computational cost. For maxiumum performance, this option should be turned off.
      Returns:
      `String` representing the XPath to the node to be inserted before, `null` if it is not available

      Throws:
      `Exception` - if the `DiffOp` not an insert

      `java.lang.Exception`

    <!-- -->

    - #### getCurrentXPath

          public abstract java.lang.String getCurrentXPath()
                                                    throws java.lang.Exception

      Returns the XPath to the node to be deleted, for a delete `DiffOp`. Whether or not the XPath info is available is controlled by [`Options`](Options.md). The `includeXPaths(...)` methods of [`Options`](Options.md) control the current setting of this option, and allow setting it to a new value. Including XPath info adds to the memory use and computational cost. For maxiumum performance, this option should be turned off.
      Returns:
      `String` representing the XPath to the node to be deleted, `null` if it's not available

      Throws:
      `Exception` - if the `DiffOp` is not a delete

      `java.lang.Exception`

    <!-- -->

    - #### getPrefixToNamespace

          public java.util.HashMap<java.lang.String,java.lang.String> getPrefixToNamespace()

    <!-- -->

    - #### compareTo

          public int compareTo(DiffOp op)

      Specified by:
      `compareTo` in interface `java.lang.Comparable<DiffOp>`

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

- **[Prev Class](DeleteDiffOp.md)**
- **[Next Class](DiffOp.Name.md)**

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
