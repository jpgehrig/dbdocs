Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ElementEditVAL.md)**
- **[Next Class](NodeEditVAL.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.w3c.dom.validation**

## **Class ExceptionVAL**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **java.lang.RuntimeException**

      - - **org.w3c.dom.validation.ExceptionVAL**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class ExceptionVAL
      extends java.lang.RuntimeException

  **Some Validation operations may throw an `ExceptionVAL` as described in their descriptions.**
  **See also the [Document Object Model (DOM) Level 3 Validation Specification](https://www.w3.org/TR/DOM-Level-3-Val/validation.html).**

  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                           |
    |-------------------|-----------------------------------------------------------------------------------------------------------------|
    | `short`           | `code`                                                                                                          |
    | `static short`    | `NO_SCHEMA_AVAILABLE_ERR`<br>This error occurs when the operation cannot complete due to an unavailable schema. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                             |
    |---------------------------------------------------------|
    | `ExceptionVAL``(short code, java.lang.String message)`  |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class java.lang.Throwable**

      **`addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`**

<!-- -->

-
  -

    ### **Field Detail**

    - #### **code**

          public short code

    - #### **NO_SCHEMA_AVAILABLE_ERR**

          public static final short NO_SCHEMA_AVAILABLE_ERR

      **This error occurs when the operation cannot complete due to an unavailable schema. DOM Core needs to provide a definition, and we need to link it here.**
      **See Also:**
      **[Constant Field Values](../../../../constant-values.md)**

  <!-- -->

  -

    ### **Constructor Detail**

    - #### **ExceptionVAL**

          public ExceptionVAL(short code,
                              java.lang.String message)

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](ElementEditVAL.md)**
- **[Next Class](NodeEditVAL.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at [http://www.w3.org/TR/DOM-Level-3-Val](http://www.w3.org/TR/DOM-Level-3-Val/).**
