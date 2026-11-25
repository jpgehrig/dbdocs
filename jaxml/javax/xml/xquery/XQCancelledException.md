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

- **[Prev Class](PooledXQConnection.md)**
- **[Next Class](XQConnection.md)**

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

## **Class XQCancelledException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[javax.xml.xquery.XQException](XQException.md)**

      - - **[javax.xml.xquery.XQQueryException](XQQueryException.md)**

        - - **javax.xml.xquery.XQCancelledException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XQCancelledException
      extends XQQueryException

  **`XQCancelledException` is an exception to indicate that the current XQuery processing is cancelled by the application through a `cancel()` request. This exception allows an application to easily differentiate between a user's cancellation of the query from a general execution failure.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XQCancelledException``(java.lang.String message, java.lang.String vendorCode, javax.xml.namespace.QName errorCode, int line, int column, int position, java.lang.String moduleURI, `[`XQSequence`](XQSequence.md)` errorObject, `[`XQStackTraceElement`](XQStackTraceElement.md)`[] stackTrace)`<br>Constructs an `XQCancelledException` object with a given message, vendor code, error code, line number, column number, position, module URI, error object, and stack trace. |

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class javax.xml.xquery.[XQQueryException](XQQueryException.md)**

      **[`getColumnNumber`](XQQueryException.md)`, `[`getErrorCode`](XQQueryException.md)`, `[`getErrorObject`](XQQueryException.md)`, `[`getLineNumber`](XQQueryException.md)`, `[`getModuleURI`](XQQueryException.md)`, `[`getPosition`](XQQueryException.md)`, `[`getQueryStackTrace`](XQQueryException.md)**

    <!-- -->

    -

      ### **Methods inherited from class javax.xml.xquery.[XQException](XQException.md)**

      **[`getNextException`](XQException.md)`, `[`getVendorCode`](XQException.md)`, `[`setNextException`](XQException.md)**

    <!-- -->

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

    ### **Constructor Detail**

    - #### **XQCancelledException**

          public XQCancelledException(java.lang.String message,
                                      java.lang.String vendorCode,
                                      javax.xml.namespace.QName errorCode,
                                      int line,
                                      int column,
                                      int position,
                                      java.lang.String moduleURI,
                                      XQSequence errorObject,
                                      XQStackTraceElement[] stackTrace)

      **Constructs an `XQCancelledException` object with a given message, vendor code, error code, line number, column number, position, module URI, error object, and stack trace.**
      **Parameters:**
      **`message` - the description of the error. `null` indicates that the message string is non existant**

      **`vendorCode` - a vendor-specific string identifying the error. `null` indicates there is no vendor code or it is unknown**

      **`errorCode` - `QName` which identifies the error according to the standard as described in [*Appendix F, XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery/#id_errors), [*Appendix C, XQuery 1.0 and XPath 2.0 Functions and Operators*](http://www.w3.org/TR/xpath-functions/#error_summary), and its associated specifications; implementation-defined errors may be raised**

      **`line` - the line number in the query string where the error occured. Line numbering starts at `1`. `-1` if unknown**

      **`column` - the column number in the query string where the error occured. Column numbering starts at `1`. `-1` if unknown**

      **`position` - the position in the query string where the error occured. This is a `0` based position. `-1` if unknown**

      **`moduleURI` - the module URI of the module in which the error occurred. `null` when it is the main module or when the module is unknown**

      **`errorObject` - an `XQSequence` representing the error object passed to `fn:error()`. `null` if this error was not triggered by `fn:error()` or when the error object is not available**

      **`stackTrace` - the XQuery stack trace where the error occurred. `null` if not available**

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

- **[Prev Class](PooledXQConnection.md)**
- **[Next Class](XQConnection.md)**

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
