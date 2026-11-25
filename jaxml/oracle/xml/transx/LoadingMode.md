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

- **[Prev Class](loader.md)**
- **[Next Class](TransX.md)**

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

**oracle.xml.transx**

## **Class LoadingMode**

- **java.lang.Object**

- - **oracle.xml.transx.LoadingMode**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class LoadingMode
      extends java.lang.Object

  **LoadingMode class. LoadingMode is used to specify the behaviour when there are one or more existing rows in the database whose values in the key columns are the same as those in the dataset to be loaded. The loader by default skips duplicates i.e. The flag is SKIP.**
  **See Also:**
  **[`TransX.setLoadingMode(int)`](TransX.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                           |
    |-------------------|-------------------------------------------------|
    | `static int`      | `EXCEPTION_ON_DUPLICATES`<br>throw an exception |
    | `static int`      | `SKIP_DUPLICATES`<br>skip duplicate rows        |
    | `static int`      | `UPDATE_DUPLICATES`<br>update the rows          |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `LoadingMode``()`           |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`**

<!-- -->

-
  -

    ### **Field Detail**

    - #### **SKIP_DUPLICATES**

          public static final int SKIP_DUPLICATES

      **skip duplicate rows**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **UPDATE_DUPLICATES**

          public static final int UPDATE_DUPLICATES

      **update the rows**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

    - #### **EXCEPTION_ON_DUPLICATES**

          public static final int EXCEPTION_ON_DUPLICATES

      **throw an exception**
      **See Also:**
      **[Constant Field Values](../../../constant-values.md)**

  <!-- -->

  -

    ### **Constructor Detail**

    - #### **LoadingMode**

          public LoadingMode()

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](loader.md)**
- **[Next Class](TransX.md)**

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
