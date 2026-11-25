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

- **[Prev Class](XMLError.md)**
- **[Next Class](XMLUtil.md)**

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

## **Class XMLException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **oracle.xml.util.XMLException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XSLException](../parser/v2/XSLException.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLException
      extends java.lang.Exception

  **Indicates that a parsing exception occurred while processing an XML document**
  **See Also:**
  **[Serialized Form](../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                 |
    |-------------------|---------------------------------------|
    | `static int`      | `ERROR`<br>Code for non-fatal error   |
    | `static int`      | `FATAL_ERROR`<br>Code for fatal error |
    | `static int`      | `WARNING`<br>Code for warning         |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `XMLException``(java.lang.String mesg, java.lang.String pubId, java.lang.String sysId, int line, int col, int type)`  |
    | `XMLException``(java.lang.String mesg, java.lang.Throwable ex)`                                                       |
    | `XMLException``(`[`XMLError`](XMLError.md)` err, java.lang.Exception e)`                                              |
    | `XMLException``(`[`XMLError`](XMLError.md)` err, int firsterr)`                                                       |
    | `XMLException``(`[`XMLError`](XMLError.md)` err, int firsterr, java.lang.Exception e)`                                |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                              |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`        | `formatErrorMessage``(int i)`<br>Get the error message at specified index                                                           |
    | `java.lang.Throwable`     | `getCause``()`<br>Get the cause exception                                                                                           |
    | `int`                     | `getColumnNumber``(int i)`<br>Get the column number of error at specified index                                                     |
    | `java.lang.Exception`     | `getException``(int i)`<br>Get the exception (if exists) that occured in error at specified index                                   |
    | `int`                     | `getLineNumber``(int i)`<br>Get the line number of error at specified index                                                         |
    | `java.lang.String`        | `getMessage``(int i)`<br>Get the error message at specified index                                                                   |
    | `int`                     | `getMessageType``(int i)`<br>Get the type of the error message at specified index                                                   |
    | `int`                     | `getNumMessages``()`<br>Return the total number of errors/warnings found during parsing                                             |
    | `java.lang.String`        | `getPublicId``(int i)`<br>Get the public ID of input when error at specified index occured                                          |
    | `java.lang.String`        | `getSystemId``(int i)`<br>Get the system ID of input when error at specified index occured                                          |
    | [`XMLError`](XMLError.md) | `getXMLError``()`<br>Get XMLError object inside XMLException.                                                                       |
    | `java.lang.Throwable`     | `initCause``(java.lang.Throwable ex)`<br>Set the underlying exception (if exists) This overrides the super.initCause (since JDK1.4) |
    | `void`                    | `printStackTrace``()`<br>Prints this `Throwable` and its backtrace to the standard error stream.                                    |
    | `void`                    | `printStackTrace``(java.io.PrintStream s)`<br>Prints this `Throwable` and its backtrace to the specified print stream.              |
    | `void`                    | `printStackTrace``(java.io.PrintWriter s)`<br>Prints this `Throwable` and its backtrace to the specified print writer.              |
    | `void`                    | `setException``(java.lang.Exception ex)`<br>Set the underlying exception (if exists)                                                |
    | `java.lang.String`        | `toString``()`<br>Override toString to pick up any embedded exception.                                                              |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR

          public static final int ERROR

      Code for non-fatal error
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FATAL_ERROR

          public static final int FATAL_ERROR

      Code for fatal error
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WARNING

          public static final int WARNING

      Code for warning
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLException

          public XMLException(java.lang.String mesg,
                              java.lang.Throwable ex)

    <!-- -->

    - #### XMLException

          public XMLException(java.lang.String mesg,
                              java.lang.String pubId,
                              java.lang.String sysId,
                              int line,
                              int col,
                              int type)

    <!-- -->

    - #### XMLException

          public XMLException(XMLError err,
                              int firsterr)

    <!-- -->

    - #### XMLException

          public XMLException(XMLError err,
                              int firsterr,
                              java.lang.Exception e)

    <!-- -->

    - #### XMLException

          public XMLException(XMLError err,
                              java.lang.Exception e)

  <!-- -->

  - ### Method Detail

    - #### getNumMessages

          public int getNumMessages()

      Return the total number of errors/warnings found during parsing
      Returns:
      The number of errors/warnings

    <!-- -->

    - #### getMessage

          public java.lang.String getMessage(int i)

      Get the error message at specified index
      Returns:
      The error message

    <!-- -->

    - #### formatErrorMessage

          public java.lang.String formatErrorMessage(int i)

      Get the error message at specified index
      Returns:
      The error message

    <!-- -->

    - #### getLineNumber

          public int getLineNumber(int i)

      Get the line number of error at specified index
      Returns:
      The line number

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber(int i)

      Get the column number of error at specified index
      Returns:
      The column number

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId(int i)

      Get the system ID of input when error at specified index occured
      Returns:
      The system ID

    <!-- -->

    - #### getPublicId

          public java.lang.String getPublicId(int i)

      Get the public ID of input when error at specified index occured
      Returns:
      The public ID

    <!-- -->

    - #### getException

          public java.lang.Exception getException(int i)

      Get the exception (if exists) that occured in error at specified index
      Returns:
      The exception

    <!-- -->

    - #### getCause

          public java.lang.Throwable getCause()

      Get the cause exception
      Overrides:
      `getCause` in class `java.lang.Throwable`

      Returns:
      The exception

    <!-- -->

    - #### getMessageType

          public int getMessageType(int i)

      Get the type of the error message at specified index
      Returns:
      The error message type

    <!-- -->

    - #### printStackTrace

          public void printStackTrace()

      Prints this `Throwable` and its backtrace to the standard error stream.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintStream s)

      Prints this `Throwable` and its backtrace to the specified print stream.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### printStackTrace

          public void printStackTrace(java.io.PrintWriter s)

      Prints this `Throwable` and its backtrace to the specified print writer.
      Overrides:
      `printStackTrace` in class `java.lang.Throwable`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Override toString to pick up any embedded exception.
      Overrides:
      `toString` in class `java.lang.Throwable`

      Returns:
      A string representation of this exception.

    <!-- -->

    - #### setException

          public void setException(java.lang.Exception ex)

      Set the underlying exception (if exists)
      Parameters:
      `ex` - - The exception

    <!-- -->

    - #### initCause

          public java.lang.Throwable initCause(java.lang.Throwable ex)

      Set the underlying exception (if exists) This overrides the super.initCause (since JDK1.4)
      Overrides:
      `initCause` in class `java.lang.Throwable`

      Parameters:
      `ex` - - The `Throwable` cause

      Returns:
      this

    <!-- -->

    - #### getXMLError

          public XMLError getXMLError()

      Get XMLError object inside XMLException.
      Returns:
      the XMLError object.

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

- **[Prev Class](XMLError.md)**
- **[Next Class](XMLUtil.md)**

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
