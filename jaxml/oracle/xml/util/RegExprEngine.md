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

- **[Prev Class](Queue.md)**
- **[Next Class](UnicodeUtil.md)**

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

**oracle.xml.util**

## **Class RegExprEngine**

- **java.lang.Object**

- - **oracle.xml.common.regex.xerces.GenericEngine\<oracle.xml.common.regex.xerces.ParseException\>**

  - - **oracle.xml.util.RegExprEngine**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class RegExprEngine
      extends oracle.xml.common.regex.xerces.GenericEngine<oracle.xml.common.regex.xerces.ParseException>

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `RegExprEngine``(java.lang.String regexp, java.lang.String flags)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                       |
    |-------------------------------------------------|----------------------------------------------------------------------------------------------|
    | `oracle.xml.common.regex.xerces.ParseException` | `createBadFlagsException``(java.lang.String flags)`<br>Overriden by XQuery and XSLT!         |
    | `oracle.xml.common.regex.xerces.ParseException` | `createBadReplacementException``(java.lang.String repval)`<br>Overridden by XQuery ant XSLT! |

    - ### Methods inherited from class oracle.xml.common.regex.xerces.GenericEngine

      `createMatchObject, getGroupParentIndex, match, match, normalizeFlags, replace, tokenize`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RegExprEngine

          public RegExprEngine(java.lang.String regexp,
                               java.lang.String flags)
                        throws oracle.xml.common.regex.xerces.ParseException

      Throws:
      `oracle.xml.common.regex.xerces.ParseException`

  <!-- -->

  - ### Method Detail

    - #### createBadFlagsException

          public oracle.xml.common.regex.xerces.ParseException createBadFlagsException(java.lang.String flags)

      Description copied from class: `oracle.xml.common.regex.xerces.GenericEngine`
      Overriden by XQuery and XSLT!
      Specified by:
      `createBadFlagsException` in class `oracle.xml.common.regex.xerces.GenericEngine<oracle.xml.common.regex.xerces.ParseException>`

    <!-- -->

    - #### createBadReplacementException

          public oracle.xml.common.regex.xerces.ParseException createBadReplacementException(java.lang.String repval)

      Description copied from class: `oracle.xml.common.regex.xerces.GenericEngine`
      Overridden by XQuery ant XSLT!
      Specified by:
      `createBadReplacementException` in class `oracle.xml.common.regex.xerces.GenericEngine<oracle.xml.common.regex.xerces.ParseException>`

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

- **[Prev Class](Queue.md)**
- **[Next Class](UnicodeUtil.md)**

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
