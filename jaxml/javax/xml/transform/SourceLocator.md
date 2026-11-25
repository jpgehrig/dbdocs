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

- **[Prev Class](Source.md)**
- **[Next Class](Templates.md)**

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

**javax.xml.transform**

## **Interface SourceLocator**

- **All Known Subinterfaces:**
  **[DOMLocator](dom/DOMLocator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface SourceLocator

  **This interface is primarily for the purposes of reporting where an error occurred in the XML source or transformation instructions.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                        |
    |--------------------|-----------------------------------------------------------------------------------------------|
    | `int`              | `getColumnNumber``()`<br>Return the character position where the current document event ends. |
    | `int`              | `getLineNumber``()`<br>Return the line number where the current document event ends.          |
    | `java.lang.String` | `getPublicId``()`<br>Return the public identifier for the current document event.             |
    | `java.lang.String` | `getSystemId``()`<br>Return the system identifier for the current document event.             |

<!-- -->

- - ### Method Detail

    - #### getPublicId

          java.lang.String getPublicId()

      Return the public identifier for the current document event.
      The return value is the public identifier of the document entity or of the external parsed entity in which the markup that triggered the event appears.

      Returns:
      A string containing the public identifier, or null if none is available.

      See Also:
      `getSystemId()`

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      Return the system identifier for the current document event.
      The return value is the system identifier of the document entity or of the external parsed entity in which the markup that triggered the event appears.

      If the system identifier is a URL, the parser must resolve it fully before passing it to the application.

      Returns:
      A string containing the system identifier, or null if none is available.

      See Also:
      `getPublicId()`

    <!-- -->

    - #### getLineNumber

          int getLineNumber()

      Return the line number where the current document event ends.
      **Warning:** The return value from the method is intended only as an approximation for the sake of error reporting; it is not intended to provide sufficient information to edit the character content of the original XML document.

      The return value is an approximation of the line number in the document entity or external parsed entity where the markup that triggered the event appears.

      Returns:
      The line number, or -1 if none is available.

      See Also:
      `getColumnNumber()`

    <!-- -->

    - #### getColumnNumber

          int getColumnNumber()

      Return the character position where the current document event ends.
      **Warning:** The return value from the method is intended only as an approximation for the sake of error reporting; it is not intended to provide sufficient information to edit the character content of the original XML document.

      The return value is an approximation of the column number in the document entity or external parsed entity where the markup that triggered the event appears.

      Returns:
      The column number, or -1 if none is available.

      See Also:
      `getLineNumber()`

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

- **[Prev Class](Source.md)**
- **[Next Class](Templates.md)**

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
