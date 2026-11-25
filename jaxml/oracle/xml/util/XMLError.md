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

- **[Prev Class](UnicodeUtil.md)**
- **[Next Class](XMLException.md)**

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

## **Class XMLError**

- **java.lang.Object**

- - **oracle.xml.util.XMLError**

<!-- -->

- **Direct Known Subclasses:**
  **[XMLError](../parser/v2/XMLError.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLError
      extends java.lang.Object

  **This class hold error message and the line number where it occured**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description           |
    |---------------------------------------|
    | `XMLError``()`<br>Default constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                    |
    |----------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                       | `error``(int id, int type, java.lang.String msg)`<br>Adds a new error to the vector                                                                                       |
    | `void`                                       | `error``(int id, int type, java.lang.String[] p)`<br>Adds a new error to the vector                                                                                       |
    | `void`                                       | `error0``(int id, int type)`<br>Adds a new error to the vector                                                                                                            |
    | `void`                                       | `error1``(int id, int type, java.lang.String p1)`<br>Adds a new error to the vector                                                                                       |
    | `void`                                       | `error2``(int id, int type, java.lang.String p1, java.lang.String p2)`<br>Adds a new error to the vector                                                                  |
    | `void`                                       | `error3``(int id, int type, java.lang.String p1, java.lang.String p2, java.lang.String p3)`<br>Adds a new error to the vector                                             |
    | `void`                                       | `flushErrorStream``()`<br>Flush all the error to the ouput stream output stream defaults or to error handler                                                              |
    | `java.lang.String`                           | `formatErrorMesg``(int index)`                                                                                                                                            |
    | `int`                                        | `getColumnNumber``(int i)`<br>Get the column number of error at specified index                                                                                           |
    | `java.lang.Exception`                        | `getException``(int i)`<br>Get the exception (if exists) that occured in error at specified index                                                                         |
    | `int`                                        | `getFirstError``()`                                                                                                                                                       |
    | `int`                                        | `getLineNumber``(int i)`<br>Get the line number of error at specified index                                                                                               |
    | [`Locator`](../../../org/xml/sax/Locator.md) | `getLocator``()`<br>Return the registered locator                                                                                                                         |
    | `java.lang.String`                           | `getMessage``(int i)`<br>Get the error message at specified index                                                                                                         |
    | `java.lang.String`                           | `getMessage``(int errId, java.lang.String[] params)`<br>Get error message with more than 5 arguments                                                                      |
    | `java.lang.String`                           | `getMessage0``(int errId)`<br>Get error message with no arguments                                                                                                         |
    | `java.lang.String`                           | `getMessage1``(int errId, java.lang.String a1)`<br>Get error message with 1 arguments                                                                                     |
    | `java.lang.String`                           | `getMessage2``(int errId, java.lang.String a1, java.lang.String a2)`<br>Get error message with 2 arguments                                                                |
    | `java.lang.String`                           | `getMessage3``(int errId, java.lang.String a1, java.lang.String a2, java.lang.String a3)`<br>Get error message with 3 arguments                                           |
    | `java.lang.String`                           | `getMessage4``(int errId, java.lang.String a1, java.lang.String a2, java.lang.String a3, java.lang.String a4)`<br>Get error message with 4 arguments                      |
    | `java.lang.String`                           | `getMessage5``(int errId, java.lang.String a1, java.lang.String a2, java.lang.String a3, java.lang.String a4, java.lang.String a5)`<br>Get error message with 5 arguments |
    | `int`                                        | `getMessageId``(int i)`<br>Get the ID of the error message at specified index                                                                                             |
    | `int`                                        | `getMessageType``(int i)`<br>Get the type of the error message at specified index                                                                                         |
    | `int`                                        | `getNumExceptions``()`<br>Return the total number of fatal errors found during parsing                                                                                    |
    | `int`                                        | `getNumFatalMessages``()`<br>Return the total number of fatal errors found during parsing                                                                                 |
    | `int`                                        | `getNumMessages``()`<br>Return the total number of errors/warnings found during parsing                                                                                   |
    | `java.lang.String`                           | `getPublicId``(int i)`<br>Get the public ID of input when error at specified index occured                                                                                |
    | `java.lang.String`                           | `getSystemId``(int i)`<br>Get the system ID of input when error at specified index occured                                                                                |
    | `void`                                       | `printErrorListener``()`<br>Flush all the JAXP 1.1 errors to the ErrorListener If no ErrorListener was set, default to System.err                                         |
    | `void`                                       | `reset``()`<br>Reset the error class                                                                                                                                      |
    | `void`                                       | `setErrorStream``(java.io.OutputStream out)`<br>Register a output stream                                                                                                  |
    | `void`                                       | `setErrorStream``(java.io.OutputStream out, java.lang.String enc)`<br>Register a output stream                                                                            |
    | `void`                                       | `setErrorStream``(java.io.PrintWriter out)`<br>Register a output stream                                                                                                   |
    | `void`                                       | `setException``(java.lang.Exception exp)`<br>Register a exception                                                                                                         |
    | `void`                                       | `setLocale``(java.util.Locale locale)`<br>Register a locale                                                                                                               |
    | `void`                                       | `setLocator``(`[`Locator`](../../../org/xml/sax/Locator.md)` locator)`<br>Register a locator                                                                              |
    | `void`                                       | `showWarnings``(boolean flag)`<br>Turn reporting warning on/off                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLError

          public XMLError()

      Default constructor

  <!-- -->

  - ### Method Detail

    - #### reset

          public void reset()

      Reset the error class

    <!-- -->

    - #### setErrorStream

          public void setErrorStream(java.io.OutputStream out)

      Register a output stream
      Parameters:
      `out` - - OutputStream to ouput the error/warnings

    <!-- -->

    - #### setErrorStream

          public void setErrorStream(java.io.OutputStream out,
                                     java.lang.String enc)
                              throws java.io.IOException

      Register a output stream
      Parameters:
      `out` - - OutputStream to ouput the error/warnings

      `enc` - - Encoding of the outputstream

      Throws:
      `java.io.IOException` - - if an error occurs initializing the outputstream

    <!-- -->

    - #### setErrorStream

          public void setErrorStream(java.io.PrintWriter out)

      Register a output stream
      Parameters:
      `out` - - PrintWriter to ouput the error/warnings

    <!-- -->

    - #### showWarnings

          public void showWarnings(boolean flag)

      Turn reporting warning on/off
      Parameters:
      `flag` - - controls reporting of warnings

    <!-- -->

    - #### setLocale

          public void setLocale(java.util.Locale locale)

      Register a locale
      Parameters:
      `locale` - - locale for error reporting

    <!-- -->

    - #### setLocator

          public void setLocator(Locator locator)

      Register a locator
      Parameters:
      `locator` - - locater to get lin/col/sysid/pubid info

    <!-- -->

    - #### setException

          public void setException(java.lang.Exception exp)

      Register a exception
      Parameters:
      `exp` - - last exception occured

    <!-- -->

    - #### getLocator

          public Locator getLocator()

      Return the registered locator
      Returns:
      locator

    <!-- -->

    - #### getFirstError

          public int getFirstError()

    <!-- -->

    - #### getNumMessages

          public int getNumMessages()

      Return the total number of errors/warnings found during parsing
      Returns:
      The number of errors/warnings

    <!-- -->

    - #### getNumFatalMessages

          public final int getNumFatalMessages()

      Return the total number of fatal errors found during parsing
      Returns:
      The number of fatal errors

    <!-- -->

    - #### getNumExceptions

          public final int getNumExceptions()

      Return the total number of fatal errors found during parsing
      Returns:
      The number of fatal errors

    <!-- -->

    - #### getMessage

          public java.lang.String getMessage(int i)

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

    - #### getMessageId

          public int getMessageId(int i)

      Get the ID of the error message at specified index
      Returns:
      The error message ID

    <!-- -->

    - #### getMessageType

          public int getMessageType(int i)

      Get the type of the error message at specified index
      Returns:
      The error message type

    <!-- -->

    - #### error

          public void error(int id,
                            int type,
                            java.lang.String msg)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `msg` - - error message (without paramters)

      `type` - - type of the error

    <!-- -->

    - #### error0

          public void error0(int id,
                             int type)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `type` - - type of the error

    <!-- -->

    - #### error1

          public void error1(int id,
                             int type,
                             java.lang.String p1)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `type` - - type of the error

      `p1` - - paramter 1

    <!-- -->

    - #### error2

          public void error2(int id,
                             int type,
                             java.lang.String p1,
                             java.lang.String p2)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `type` - - type of the error

      `p1` - - paramter 1

      `p2` - - paramter 2

    <!-- -->

    - #### error3

          public void error3(int id,
                             int type,
                             java.lang.String p1,
                             java.lang.String p2,
                             java.lang.String p3)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `type` - - type of the error

      `p1` - - paramter 1

      `p2` - - paramter 2

      `p3` - - paramter 3

    <!-- -->

    - #### error

          public void error(int id,
                            int type,
                            java.lang.String[] p)

      Adds a new error to the vector
      Parameters:
      `id` - - id of the error message

      `type` - - type of the error

      `p` - - paramter array

    <!-- -->

    - #### flushErrorStream

          public void flushErrorStream()
                                throws java.io.IOException

      Flush all the error to the ouput stream output stream defaults or to error handler
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### printErrorListener

          public void printErrorListener()
                                  throws java.io.IOException

      Flush all the JAXP 1.1 errors to the ErrorListener If no ErrorListener was set, default to System.err
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### getMessage0

          public java.lang.String getMessage0(int errId)

      Get error message with no arguments

    <!-- -->

    - #### getMessage1

          public java.lang.String getMessage1(int errId,
                                              java.lang.String a1)

      Get error message with 1 arguments

    <!-- -->

    - #### getMessage2

          public java.lang.String getMessage2(int errId,
                                              java.lang.String a1,
                                              java.lang.String a2)

      Get error message with 2 arguments

    <!-- -->

    - #### getMessage3

          public java.lang.String getMessage3(int errId,
                                              java.lang.String a1,
                                              java.lang.String a2,
                                              java.lang.String a3)

      Get error message with 3 arguments

    <!-- -->

    - #### getMessage4

          public java.lang.String getMessage4(int errId,
                                              java.lang.String a1,
                                              java.lang.String a2,
                                              java.lang.String a3,
                                              java.lang.String a4)

      Get error message with 4 arguments

    <!-- -->

    - #### getMessage5

          public java.lang.String getMessage5(int errId,
                                              java.lang.String a1,
                                              java.lang.String a2,
                                              java.lang.String a3,
                                              java.lang.String a4,
                                              java.lang.String a5)

      Get error message with 5 arguments

    <!-- -->

    - #### getMessage

          public java.lang.String getMessage(int errId,
                                             java.lang.String[] params)

      Get error message with more than 5 arguments

    <!-- -->

    - #### formatErrorMesg

          public java.lang.String formatErrorMesg(int index)

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

- **[Prev Class](UnicodeUtil.md)**
- **[Next Class](XMLException.md)**

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
