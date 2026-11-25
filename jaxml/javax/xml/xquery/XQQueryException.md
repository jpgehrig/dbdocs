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

- **[Prev Class](XQPreparedExpression.md)**
- **[Next Class](XQResultItem.md)**

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

## **Class XQQueryException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.xquery.XQException](XQException.md)**

      - - **javax.xml.xquery.XQQueryException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XQCancelledException](XQCancelledException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XQQueryException
      extends XQException

  **An exception that provides information on errors occurring during the evaluation of an xquery.

  Each `XQQueryException` provides several kinds of optional information, in addition to the properties inherited from `XQException`:**
  - **an error code. This `QName` identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and and its associated specifications; implementation-defined errors may be raised.**
  - **a position. This identifies the character position of the failing expression in the query text. This is a `0` based position. `-1` if unknown.**
  - **the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown**
  - **the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown**
  - **the module uri. This identifies the module in which the error occurred, `null` when the error is located in the main module.**
  - **the XQuery error object of this exception. This is the `$error-object` argument specified through the `fn:error()` function. May be `null` if not specified.**
  - **the XQuery stack trace. This provides additional dynamic information where the exception occurred in the XQuery expression.**

  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XQQueryException``(java.lang.String message)`<br>Constructs an `XQQueryException` object with a given message.                                                                                                                                                                                                                                                                                                                                                          |
    | `XQQueryException``(java.lang.String message, javax.xml.namespace.QName errorCode)`<br>Constructs an `XQQueryException` object with a given message, and error code.                                                                                                                                                                                                                                                                                                     |
    | `XQQueryException``(java.lang.String message, javax.xml.namespace.QName errorCode, int line, int column, int position)`<br>Constructs an `XQQueryException` object with a given message, error code, line number, column number, and position.                                                                                                                                                                                                                           |
    | `XQQueryException``(java.lang.String message, java.lang.String vendorCode, javax.xml.namespace.QName errorCode, int line, int column, int position)`<br>Constructs an `XQQueryException` object with a given message, vendor code, error code, line number, column number, and position.                                                                                                                                                                                 |
    | `XQQueryException``(java.lang.String message, java.lang.String vendorCode, javax.xml.namespace.QName errorCode, int line, int column, int position, java.lang.String moduleURI, `[`XQSequence`](XQSequence.md)` errorObject, `[`XQStackTraceElement`](XQStackTraceElement.md)`[] stackTrace)`<br>Constructs an `XQQueryException` object with a given message, vendor code, error code, line number, column number, position, module URI, error object, and stack trace. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                               | `getColumnNumber``()`<br>Gets the column number in the query string where the error occurred.                                                                                                                                                                                                                                                                                                                                                                                           |
    | `javax.xml.namespace.QName`                         | `getErrorCode``()`<br>Gets the code identifying the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; imlementation-defined errors may also be raised; finally the error code may also be specified in the query using `fn:error()`. |
    | [`XQSequence`](XQSequence.md)                       | `getErrorObject``()`<br>Gets an `XQSequence` representing the error object passed to `fn:error()`.                                                                                                                                                                                                                                                                                                                                                                                      |
    | `int`                                               | `getLineNumber``()`<br>Gets the line number in the query string where the error occurred.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                  | `getModuleURI``()`<br>Gets the module URI of the module in which the error occurred.                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                               | `getPosition``()`<br>Gets the character position in the query string where this exception occurred.                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`XQStackTraceElement`](XQStackTraceElement.md)`[]` | `getQueryStackTrace``()`<br>Returns the query stack stackTrace when the exception occurred, or null if none.                                                                                                                                                                                                                                                                                                                                                                            |

    - ### Methods inherited from class javax.xml.xquery.[XQException](XQException.md)

      [`getNextException`](XQException.md)`, `[`getVendorCode`](XQException.md)`, `[`setNextException`](XQException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XQQueryException

          public XQQueryException(java.lang.String message)

      Constructs an `XQQueryException` object with a given message.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

    <!-- -->

    - #### XQQueryException

          public XQQueryException(java.lang.String message,
                                  javax.xml.namespace.QName errorCode)

      Constructs an `XQQueryException` object with a given message, and error code.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

      `errorCode` - `QName` which identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; implementation-defined errors may be raised.

    <!-- -->

    - #### XQQueryException

          public XQQueryException(java.lang.String message,
                                  javax.xml.namespace.QName errorCode,
                                  int line,
                                  int column,
                                  int position)

      Constructs an `XQQueryException` object with a given message, error code, line number, column number, and position.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

      `errorCode` - `QName` which identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; implementation-defined errors may be raised

      `line` - the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown

      `column` - the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown

      `position` - the position in the query string where the error occured. This is a `0` based position. `-1` if unknown

    <!-- -->

    - #### XQQueryException

          public XQQueryException(java.lang.String message,
                                  java.lang.String vendorCode,
                                  javax.xml.namespace.QName errorCode,
                                  int line,
                                  int column,
                                  int position)

      Constructs an `XQQueryException` object with a given message, vendor code, error code, line number, column number, and position.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

      `vendorCode` - a vendor-specific string identifying the error. `null` indicates there is no vendor code or it is unknown

      `errorCode` - `QName` which identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; implementation-defined errors may be raised

      `line` - the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown

      `column` - the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown

      `position` - the position in the query string where the error occured. This is a `0` based position. `-1` if unknown

    <!-- -->

    - #### XQQueryException

          public XQQueryException(java.lang.String message,
                                  java.lang.String vendorCode,
                                  javax.xml.namespace.QName errorCode,
                                  int line,
                                  int column,
                                  int position,
                                  java.lang.String moduleURI,
                                  XQSequence errorObject,
                                  XQStackTraceElement[] stackTrace)

      Constructs an `XQQueryException` object with a given message, vendor code, error code, line number, column number, position, module URI, error object, and stack trace.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

      `vendorCode` - a vendor-specific string identifying the error. `null` indicates there is no vendor code or it is unknown

      `errorCode` - `QName` which identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; implementation-defined errors may be raised

      `line` - the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown

      `column` - the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown

      `position` - the position in the query string where the error occured. This is a `0` based position. `-1` if unknown

      `moduleURI` - the module URI of the module in which the error occurred. `null` when it is the main module or when the module is unknown

      `errorObject` - an `XQSequence` representing the error object passed to `fn:error()`. `null` if this error was not triggered by `fn:error()` or when the error object is not available.

      `stackTrace` - the XQuery stack trace where the error occurred. `null` if not available

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public javax.xml.namespace.QName getErrorCode()

      Gets the code identifying the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; imlementation-defined errors may also be raised; finally the error code may also be specified in the query using `fn:error()`.
      Returns:
      the code identifying the error, or `null` if not available

    <!-- -->

    - #### getErrorObject

          public XQSequence getErrorObject()

      Gets an `XQSequence` representing the error object passed to `fn:error()`. Returns `null` if this error was not triggered by `fn:error()` or when the error object is not available.
      Returns:
      the sequence passed to `fn:error()`, `null` if not available

    <!-- -->

    - #### getPosition

          public int getPosition()

      Gets the character position in the query string where this exception occurred.
      This is a `0` based position. `-1` if unknown.

      Returns:
      the character position in the query string where the exception occurred

    <!-- -->

    - #### getQueryStackTrace

          public XQStackTraceElement[] getQueryStackTrace()

      Returns the query stack stackTrace when the exception occurred, or null if none. On some implementations only the top frame may be visible.
      Returns:
      the stackTrace where the exception occurred

    <!-- -->

    - #### getModuleURI

          public java.lang.String getModuleURI()

      Gets the module URI of the module in which the error occurred. `null` when it is the main module or when the module is unknown.
      Returns:
      the module URI or `null`

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      Gets the line number in the query string where the error occurred.
      Line numbering starts at `1`. `-1` is returned if the line number is unknown. If the implementation does not support this method, it must return `-1`

      Returns:
      the line number in the query string where the error occurred

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      Gets the column number in the query string where the error occurred.
      Column numbering starts at `1`. `-1` is returned if the column number is unknown. If the implementation does not support this method, it must return `-1`

      Returns:
      the column number in the query string where the error occurred

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

- **[Prev Class](XQPreparedExpression.md)**
- **[Next Class](XQResultItem.md)**

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
