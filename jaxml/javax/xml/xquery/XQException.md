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

- **[Prev Class](XQDynamicContext.md)**
- **[Next Class](XQExpression.md)**

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

## **Class XQException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **javax.xml.xquery.XQException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XQQueryException](XQQueryException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XQException
      extends java.lang.Exception

  **An exception that provides information on XQJ, XQuery or other errors reported by an XQJ implementation.

  Each `XQException` provides several kinds of information:**
  - **a string describing the error. This is used as the Java Exception message, available via the method `getMessage`.**
  - **the cause of the error. This is used as the Java Exception cause, available via the method `getCause`.**
  - **the vendor code identifying the error. Available via the method `getVendorCode`. Refer to the vendor documentation which specific codes can be returned.**
  - **a chain of `XQException` objects. If more than one error occurred the exceptions are referenced via this chain.**

  **

  Note that `XQException` has a subclass [`XQQueryException`](XQQueryException.md) providing more detailed information about errors that occurred during the processing of a query. An implementation throws a base `XQException` when an error occurs in the XQJ implementation. Further, implementations are encouraged to use the more detailed `XQQueryException` in case of an error reported by the XQuery engine.

  It is possible that during the processing of a query that one or more errors could occur, each with their own potential causal relationship. This means that when an XQJ application catches an `XQException`, there is a possibility that there may be additional `XQException` objects chained to the original thrown `XQException`. To access the additional chained `XQException` objects, an application would recursively invoke `getNextException` until a `null` value is returned.

  An `XQException` may have a causal relationship, which consists of one or more `Throwable` instances which caused the `XQException` to be thrown. The application may recursively call the method `getCause`, until a `null` value is returned, to navigate the chain of causes.**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                        |
    |----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XQException``(java.lang.String message)`<br>Constructs an `XQException` object with a given message.                                              |
    | `XQException``(java.lang.String message, java.lang.String vendorCode)`<br>Constructs an `XQException` object with a given message and vendor code. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                        |
    |--------------------|-----------------------------------------------------------------------------------------------|
    | `XQException`      | `getNextException``()`<br>Returns the next `XQException` in the chain or `null` if none.      |
    | `java.lang.String` | `getVendorCode``()`<br>Gets the vendor code associated with this exception or `null` if none. |
    | `void`             | `setNextException``(XQException next)`<br>Adds an `XQException` to the chain of exceptions.   |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XQException

          public XQException(java.lang.String message)

      Constructs an `XQException` object with a given message. An optional chain of additional `XQException` objects may be set subsequently using `setNextException`.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

    <!-- -->

    - #### XQException

          public XQException(java.lang.String message,
                             java.lang.String vendorCode)

      Constructs an `XQException` object with a given message and vendor code. An optional chain of additional `XQException` objects may be set subsequently using `setNextException`.
      Parameters:
      `message` - the description of the error. `null` indicates that the message string is non existant

      `vendorCode` - a vendor-specific string identifying the error. `null` indicates there is no vendor code or it is unknown

  <!-- -->

  - ### Method Detail

    - #### getVendorCode

          public java.lang.String getVendorCode()

      Gets the vendor code associated with this exception or `null` if none. A vendor code is a vendor-specific string identifying the failure in a computer-comparable manner. For example, "NOCONNECT" if unable to connect or "DIVBYZERO" if division by zero occurred within the XQuery.
      Returns:
      the vendor code string, or `null` if none available

    <!-- -->

    - #### getNextException

          public XQException getNextException()

      Returns the next `XQException` in the chain or `null` if none.
      Returns:
      the next exception, or `null` if none

    <!-- -->

    - #### setNextException

          public void setNextException(XQException next)

      Adds an `XQException` to the chain of exceptions.
      Parameters:
      `next` - the next exception to be added to the chain of exceptions

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

- **[Prev Class](XQDynamicContext.md)**
- **[Next Class](XQExpression.md)**

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
