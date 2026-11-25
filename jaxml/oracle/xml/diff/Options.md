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

- **[Prev Class](InsertDiffOp.md)**
- **[Next Class](XmlUtils.md)**

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

## **Class Options**

- **java.lang.Object**

- - **oracle.xml.diff.Options**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class Options
      extends java.lang.Object

  **Options. Options to control the behaviour of methods provided by [`XmlUtils`](XmlUtils.md).**
  **We support the following options:**

  ***normalizeTextNodes* when set to `true` text nodes will be normalized in the inputs that are passed to the [`XmlUtils`](XmlUtils.md) methods. Normalization involves two steps: coalescing adjacent text nodes, followed by stripping leading and trailing whitespace from the coalesced node. Note that single text nodes will have the leading and trailing whitespace stripped, and whitespace only text nodes will be essentially disregarded by the [`XmlUtils`](XmlUtils.md) methods after normalization. The normalization is set to `true` by default. If the user wishes to implement a different normalization prior to invoking [`XmlUtils`](XmlUtils.md), the default normalization must be explicitly turned off by invoking `normalizeTextNodes(false)`.**

  ***includeXPaths* when set to `true` XPath locations will be provided in the returned [`DiffOp`](DiffOp.md) objects. Please note that for maximum performance this option should be set to `false`, which is the default value.**

  ***ignorePrefixDifferences* when set to `true` namespace prefixes will be considered equal in the provided [`XmlUtils`](XmlUtils.md) methods, even if they are different but map to the same `namespaceURI`. The default value of this option is `true`.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                      |
    |--------------------------------------------------------------------------------------------------|
    | `Options``()`                                                                                    |
    | `Options``(boolean normalizeTextNodes, boolean includeXPaths, boolean ignorePrefixDifferences)`  |
    | `Options``(Options opt)`                                                                         |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                |
    |-------------------|-----------------------------------------------------------------------|
    | `boolean`         | `ignoreNamespaceDeclarations``()`                                     |
    | `void`            | `ignoreNamespaceDeclarations``(boolean ignoreNamespaceDeclarations)`  |
    | `boolean`         | `ignorePrefixDifferences``()`                                         |
    | `void`            | `ignorePrefixDifferences``(boolean ignorePrefixDifferences)`          |
    | `boolean`         | `includeXPaths``()`                                                   |
    | `void`            | `includeXPaths``(boolean includeXPaths)`                              |
    | `boolean`         | `normalizeTextNodes``()`                                              |
    | `void`            | `normalizeTextNodes``(boolean normalizeTextNodes)`                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Options

          public Options()

    <!-- -->

    - #### Options

          public Options(boolean normalizeTextNodes,
                         boolean includeXPaths,
                         boolean ignorePrefixDifferences)

    <!-- -->

    - #### Options

          public Options(Options opt)

  <!-- -->

  - ### Method Detail

    - #### normalizeTextNodes

          public void normalizeTextNodes(boolean normalizeTextNodes)

    <!-- -->

    - #### normalizeTextNodes

          public boolean normalizeTextNodes()

    <!-- -->

    - #### includeXPaths

          public void includeXPaths(boolean includeXPaths)

    <!-- -->

    - #### includeXPaths

          public boolean includeXPaths()

    <!-- -->

    - #### ignorePrefixDifferences

          public void ignorePrefixDifferences(boolean ignorePrefixDifferences)

    <!-- -->

    - #### ignorePrefixDifferences

          public boolean ignorePrefixDifferences()

    <!-- -->

    - #### ignoreNamespaceDeclarations

          public void ignoreNamespaceDeclarations(boolean ignoreNamespaceDeclarations)

    <!-- -->

    - #### ignoreNamespaceDeclarations

          public boolean ignoreNamespaceDeclarations()

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

- **[Prev Class](InsertDiffOp.md)**
- **[Next Class](XmlUtils.md)**

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
