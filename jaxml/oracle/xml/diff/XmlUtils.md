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

- **[Prev Class](Options.md)**
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

**oracle.xml.diff**

## **Class XmlUtils**

- **java.lang.Object**

- - **oracle.xml.diff.XmlUtils**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XmlUtils
      extends java.lang.Object

  **XmlUtils. Contains various methods for comparing two XML inputs.**
  **`diffToDoc(...)` methods perform a diff of two inputs and return the result as `Document`, containing a series of diff operations.**

  **`diff(...)` methods perform a diff of two inputs and return the result as a list of [`DiffOp`](DiffOp.md) objects, each representing a diff operation. This list is returned via a user provided object that implements the [`DiffOpReceiver`](DiffOpReceiver.md) interface.**

  **`hash(...)` methods calculate a hash value for the input. These methods return a hash value that, with a high probability, uniquely represents the input. However, hash function collisions are possible, so it is possible for different inputs to have the same hash value.**

  **We also provide `equal(...)` methods to verify that two inputs are truly identical by walking the two inputs in lockstep.**

  **[`Options`](Options.md) has various options that control how the input is processed by `XmlUtils`.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                          |
    |------------------------------------------------------|
    | `XmlUtils``()`<br>Constructs a new `XmlUtils`object. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                                             |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                         | `diff``(java.io.File file1, java.io.File file2, `[`DiffOpReceiver`](DiffOpReceiver.md)` diffOpReceiver, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, stored in the input files.                                                                                                        |
    | `void`                                         | `diff``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc1, `[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc2, `[`DiffOpReceiver`](DiffOpReceiver.md)` diffOpReceiver, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, stored in the `InputSource` parameters.     |
    | `void`                                         | `diff``(`[`Node`](../../../org/w3c/dom/Node.md)` dom1, `[`Node`](../../../org/w3c/dom/Node.md)` dom2, `[`DiffOpReceiver`](DiffOpReceiver.md)` diffOpReceiver, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, represented by DOM nodes.                                                   |
    | [`Document`](../../../org/w3c/dom/Document.md) | `diffToDoc``(java.io.File file1, java.io.File file2, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, stored in the input files.                                                                                                                                                           |
    | [`Document`](../../../org/w3c/dom/Document.md) | `diffToDoc``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc1, `[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc2, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, stored in the `InputSource` parameters.                                                        |
    | [`Document`](../../../org/w3c/dom/Document.md) | `diffToDoc``(`[`Node`](../../../org/w3c/dom/Node.md)` dom1, `[`Node`](../../../org/w3c/dom/Node.md)` dom2, `[`Options`](Options.md)` opt)`<br>Diffs two input XMLs, represented by DOM nodes.                                                                                                      |
    | `boolean`                                      | `equal``(java.io.File file1, java.io.File file2, `[`Options`](Options.md)` opt)`<br>Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not.                                                                                       |
    | `boolean`                                      | `equal``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc1, `[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc2, `[`Options`](Options.md)` opt)`<br>Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not. |
    | `boolean`                                      | `equal``(`[`Node`](../../../org/w3c/dom/Node.md)` dom1, `[`Node`](../../../org/w3c/dom/Node.md)` dom2, `[`Options`](Options.md)` opt)`<br>Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not.                                 |
    | `byte[]`                                       | `hash``(java.io.File file, `[`Options`](Options.md)` opt)`<br>Compute a hash value that, with a high probability, uniquely identifies the input XML, stored in the input `File`.                                                                                                                   |
    | `byte[]`                                       | `hash``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` inSrc, `[`Options`](Options.md)` opt)`<br>Compute a hash value that, with a high probability, uniquely identifies the input XML, given as an `InputSource`.                                                                         |
    | `byte[]`                                       | `hash``(`[`Node`](../../../org/w3c/dom/Node.md)` node, `[`Options`](Options.md)` opt)`<br>Compute a hash value that, with a high probability, uniquely identifies the input XML, represented as a `Node`.                                                                                          |
    | `static java.lang.String`                      | `nodeToString``(`[`Node`](../../../org/w3c/dom/Node.md)` node, boolean withDecl)`<br>Helper method for printing out the DOM `Node`.                                                                                                                                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XmlUtils

          public XmlUtils()

      Constructs a new `XmlUtils`object.

  <!-- -->

  - ### Method Detail

    - #### diffToDoc

          public Document diffToDoc(Node dom1,
                                    Node dom2,
                                    Options opt)
                             throws java.lang.Exception

      Diffs two input XMLs, represented by DOM nodes.
      Parameters:
      `dom1` - first input node

      `dom2` - second input node

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs

    <!-- -->

    - #### diffToDoc

          public Document diffToDoc(java.io.File file1,
                                    java.io.File file2,
                                    Options opt)
                             throws java.lang.Exception

      Diffs two input XMLs, stored in the input files.
      Parameters:
      `file1` - first input XML file

      `file2` - second input XML file

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input files

    <!-- -->

    - #### diffToDoc

          public Document diffToDoc(InputSource inSrc1,
                                    InputSource inSrc2,
                                    Options opt)
                             throws java.lang.Exception

      Diffs two input XMLs, stored in the `InputSource` parameters.
      Parameters:
      `inSrc1` - first input XML as `InputSource`

      `inSrc2` - second input XML as `InputSource`

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input sources

    <!-- -->

    - #### diff

          public void diff(Node dom1,
                           Node dom2,
                           DiffOpReceiver diffOpReceiver,
                           Options opt)
                    throws java.lang.Exception

      Diffs two input XMLs, represented by DOM nodes. The result is returned programmatically as a list of [`DiffOp`](DiffOp.md) objects, to the [`DiffOpReceiver`](DiffOpReceiver.md) object that is passed as a parameter to this method.
      Parameters:
      `dom1` - first input node

      `dom2` - second input node

      `diffOpReceiver` - an object implementing the [`DiffOpReceiver`](DiffOpReceiver.md) interface

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null` this parameter is null.

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs

    <!-- -->

    - #### diff

          public void diff(java.io.File file1,
                           java.io.File file2,
                           DiffOpReceiver diffOpReceiver,
                           Options opt)
                    throws java.lang.Exception

      Diffs two input XMLs, stored in the input files. The result is returned programmatically as a list of [`DiffOp`](DiffOp.md) objects, to the [`DiffOpReceiver`](DiffOpReceiver.md) object that is passed as a parameter to this method.
      Parameters:
      `file1` - first input XML file

      `file2` - second input XML file

      `diffOpReceiver` - an object implementing the [`DiffOpReceiver`](DiffOpReceiver.md) interface

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input files

    <!-- -->

    - #### diff

          public void diff(InputSource inSrc1,
                           InputSource inSrc2,
                           DiffOpReceiver diffOpReceiver,
                           Options opt)
                    throws java.lang.Exception

      Diffs two input XMLs, stored in the `InputSource` parameters. The result is returned programmatically as a list of [`DiffOp`](DiffOp.md) objects, to the [`DiffOpReceiver`](DiffOpReceiver.md) object that is passed as a parameter to this method.
      Parameters:
      `inSrc1` - first input XML as `InputSource`

      `inSrc2` - second input XML as `InputSource`

      `diffOpReceiver` - an object implementing the [`DiffOpReceiver`](DiffOpReceiver.md) interface

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input sources

    <!-- -->

    - #### equal

          public boolean equal(Node dom1,
                               Node dom2,
                               Options opt)
                        throws java.lang.Exception

      Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not.
      Parameters:
      `dom1` - first input node

      `dom2` - second input node

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs

    <!-- -->

    - #### equal

          public boolean equal(java.io.File file1,
                               java.io.File file2,
                               Options opt)
                        throws java.lang.Exception

      Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not.
      Parameters:
      `file1` - first input XML file

      `file2` - second input XML file

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input files

    <!-- -->

    - #### equal

          public boolean equal(InputSource inSrc1,
                               InputSource inSrc2,
                               Options opt)
                        throws java.lang.Exception

      Perform a lockstep comparison of two XML inputs and return a boolean indicating whether the two inputs are equal or not.
      Parameters:
      `inSrc1` - first input XML as `InputSource`

      `inSrc2` - second input XML as `InputSource`

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      `Document` containing the diff

      Throws:
      `java.lang.Exception` - if there is an error during the comparison of the two inputs, or during the parsing of the input sources

    <!-- -->

    - #### hash

          public byte[] hash(java.io.File file,
                             Options opt)
                      throws java.lang.Exception

      Compute a hash value that, with a high probability, uniquely identifies the input XML, stored in the input `File`.
      Parameters:
      `file` - `File` containing the input XML

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      hash value as a `byte[]`

      Throws:
      `java.lang.Exception` - if there is an error during the hash calculation, or parsing of the input

    <!-- -->

    - #### hash

          public byte[] hash(InputSource inSrc,
                             Options opt)
                      throws java.lang.Exception

      Compute a hash value that, with a high probability, uniquely identifies the input XML, given as an `InputSource`.
      Parameters:
      `inSrc` - `InputSource` representing the input XML

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      hash value as a `byte[]`

      Throws:
      `java.lang.Exception` - if there is an error during the hash calculation, or parsing of the input

    <!-- -->

    - #### hash

          public byte[] hash(Node node,
                             Options opt)
                      throws java.lang.Exception

      Compute a hash value that, with a high probability, uniquely identifies the input XML, represented as a `Node`.
      Parameters:
      `node` - input node

      `opt` - options used during the comparison. Default option settings will be used if this parameter is `null`

      Returns:
      hash value as a `byte[]`

      Throws:
      `java.lang.Exception` - if there is an error during the hash calculation

    <!-- -->

    - #### nodeToString

          public static java.lang.String nodeToString(Node node,
                                                      boolean withDecl)
                                               throws java.lang.Exception

      Helper method for printing out the DOM `Node`.
      Parameters:
      `node` - node to print out

      Returns:
      a `String` containg the node representation

      Throws:
      `java.lang.Exception` - if there's an error outputting the `Node` to `String`

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

- **[Prev Class](Options.md)**
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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
