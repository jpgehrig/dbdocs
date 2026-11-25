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

- **[Prev Class](XQSequenceType.md)**
- **[Next Class](XQStackTraceVariable.md)**

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

**javax.xml.xquery**

## **Class XQStackTraceElement**

- **java.lang.Object**

- - **javax.xml.xquery.XQStackTraceElement**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XQStackTraceElement
      extends java.lang.Object
      implements java.io.Serializable

  **This class represents a frame in a stack trace, akin to the `java.lang.StackTraceElement` but for XQuery callstacks instead of Java.**
  **See Also:**
  **[`XQQueryException.getQueryStackTrace`](XQQueryException.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XQStackTraceElement``(java.lang.String moduleURI, int line, int column, int position, javax.xml.namespace.QName function, `[`XQStackTraceVariable`](XQStackTraceVariable.md)`[] variables)`<br>Construct an `XQStackTraceElement` object representing a frame in a stack trace. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                             |
    |-------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                 | `getColumnNumber``()`<br>Gets the column number in the query string containing the execution point represented by this stack trace element.                        |
    | `javax.xml.namespace.QName`                           | `getFunctionQName``()`<br>Gets the `QName` of the function in which the error occurred, or `null` if it occurred outside an enclosing function (in a main module). |
    | `int`                                                 | `getLineNumber``()`<br>Gets the line number in the query string containing the execution point represented by this stack trace element.                            |
    | `java.lang.String`                                    | `getModuleURI``()`<br>Gets the module URI containing the execution point represented by this stack trace element.                                                  |
    | `int`                                                 | `getPosition``()`<br>Gets the character position in the query string containing the execution point represented by this stack trace element.                       |
    | [`XQStackTraceVariable`](XQStackTraceVariable.md)`[]` | `getVariables``()`<br>Gets the variables in scope at this execution point, or `null` if no variable value retrieval is possible.                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XQStackTraceElement

          public XQStackTraceElement(java.lang.String moduleURI,
                                     int line,
                                     int column,
                                     int position,
                                     javax.xml.namespace.QName function,
                                     XQStackTraceVariable[] variables)

      Construct an `XQStackTraceElement` object representing a frame in a stack trace.
      Parameters:
      `moduleURI` - the module URI containing the execution point representing the stack trace element. `null` when it is the main module or when the module is unknown

      `line` - the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown

      `column` - the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown

      `position` - the position in the query string where the error occured. This is a `0` based position. `-1` if unknown

      `function` - the `QName` of the function in which the exception occurred, or `null` if it occurred outside an enclosing function

      `variables` - the variables in scope at this execution point, or `null` if no variable value retrieval is possible

  <!-- -->

  - ### Method Detail

    - #### getModuleURI

          public java.lang.String getModuleURI()

      Gets the module URI containing the execution point represented by this stack trace element. `null` when it is the main module or when the module is unknown.
      Returns:
      the module URI containing the excution point represented by the stack trace element or `null`

    <!-- -->

    - #### getPosition

          public int getPosition()

      Gets the character position in the query string containing the execution point represented by this stack trace element.
      This is a `0` based position. `-1` if unknown.

      Returns:
      the character position in the query string containing the execution point represented by the stack trace element

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      Gets the line number in the query string containing the execution point represented by this stack trace element.
      Line numbering starts at `1`. `-1` is returned if the line number is unknown. If the implementation does not support this method, it must return `-1`

      Returns:
      the line number in the query string containing the execution point represented by the stack trace element

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      Gets the column number in the query string containing the execution point represented by this stack trace element.
      Column numbering starts at `1`. `-1` is returned if the column number is unknown. If the implementation does not support this method, it must return `-1`

      Returns:
      the column number in the query string containing the execution point represented by the stack trace element

    <!-- -->

    - #### getFunctionQName

          public javax.xml.namespace.QName getFunctionQName()

      Gets the `QName` of the function in which the error occurred, or `null` if it occurred outside an enclosing function (in a main module).
      Returns:
      the `QName` of the function in which the error occurred for this stack element or `null` if it occurred outside an enclosing function

    <!-- -->

    - #### getVariables

          public XQStackTraceVariable[] getVariables()

      Gets the variables in scope at this execution point, or `null` if no variable value retrieval is possible.
      Returns:
      the variables in scope at this execution point, or `null` if no variable value retrieval is possible.

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

- **[Prev Class](XQSequenceType.md)**
- **[Next Class](XQStackTraceVariable.md)**

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
