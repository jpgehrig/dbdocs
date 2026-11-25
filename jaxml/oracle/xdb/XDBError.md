Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SQLXMLType.md)**
- **[Next Class](XDBOutputStream.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**oracle.xdb**

## **Class XDBError**

- **java.lang.Object**

- - **oracle.xdb.XDBError**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBError
      extends java.lang.Object

  **This class contains the error messages thrown by XDB.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                     |
    |---------------------------|-------------------------------------------|
    | `static java.lang.String` | `CANT_UNBIND_SUBCONTEXT`<br>Error message |
    | `static java.lang.String` | `CLOSED_OBJECT`<br>Error message          |
    | `static java.lang.String` | `EMPTY_PATH`<br>Error message             |
    | `static java.lang.String` | `END_OF_ENUM`<br>Error message            |
    | `static java.lang.String` | `INVALID_CSID`<br>Error message           |
    | `static java.lang.String` | `INVALID_INPUT`                           |
    | `static java.lang.String` | `INVALID_OBJECT`<br>Error message         |
    | `static java.lang.String` | `INVALID_PARAM`<br>Error message          |
    | `static java.lang.String` | `INVALID_PCFG`                            |
    | `static java.lang.String` | `PATH_ELEM_TOO_LONG`<br>Error message     |
    | `static java.lang.String` | `PATH_TOO_LONG`<br>Error message          |
    | `static java.lang.String` | `READ_FORBIDDEN`                          |
    | `static java.lang.String` | `READONLY_OBJECT`                         |
    | `static java.lang.String` | `SQLXML_EMPTY`                            |
    | `static java.lang.String` | `SQLXML_INVRESULT`                        |
    | `static java.lang.String` | `SQLXML_INVSOURCE`                        |
    | `static java.lang.String` | `THIN_NOT_SUPPORTED`<br>Error message     |
    | `static java.lang.String` | `UNSUPPORTED_DOM`                         |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `XDBError``()`              |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                          |
    |---------------------------|-------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `getMsg``(java.lang.String msgname)`<br>Gets the error message for the specified error message. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### INVALID_PARAM

          public static final java.lang.String INVALID_PARAM

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### EMPTY_PATH

          public static final java.lang.String EMPTY_PATH

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PATH_TOO_LONG

          public static final java.lang.String PATH_TOO_LONG

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PATH_ELEM_TOO_LONG

          public static final java.lang.String PATH_ELEM_TOO_LONG

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CANT_UNBIND_SUBCONTEXT

          public static final java.lang.String CANT_UNBIND_SUBCONTEXT

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### END_OF_ENUM

          public static final java.lang.String END_OF_ENUM

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INVALID_OBJECT

          public static final java.lang.String INVALID_OBJECT

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### THIN_NOT_SUPPORTED

          public static final java.lang.String THIN_NOT_SUPPORTED

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CLOSED_OBJECT

          public static final java.lang.String CLOSED_OBJECT

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INVALID_CSID

          public static final java.lang.String INVALID_CSID

      Error message
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INVALID_PCFG

          public static final java.lang.String INVALID_PCFG

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### READONLY_OBJECT

          public static final java.lang.String READONLY_OBJECT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### READ_FORBIDDEN

          public static final java.lang.String READ_FORBIDDEN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SQLXML_INVSOURCE

          public static final java.lang.String SQLXML_INVSOURCE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SQLXML_INVRESULT

          public static final java.lang.String SQLXML_INVRESULT

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SQLXML_EMPTY

          public static final java.lang.String SQLXML_EMPTY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UNSUPPORTED_DOM

          public static final java.lang.String UNSUPPORTED_DOM

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### INVALID_INPUT

          public static final java.lang.String INVALID_INPUT

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XDBError

          public XDBError()

  <!-- -->

  - ### Method Detail

    - #### getMsg

          public static java.lang.String getMsg(java.lang.String msgname)

      Gets the error message for the specified error message. Loads it if it is null.
      Parameters:
      `msgname` - The message name.

      Returns:
      The error message string.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SQLXMLType.md)**
- **[Next Class](XDBOutputStream.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
