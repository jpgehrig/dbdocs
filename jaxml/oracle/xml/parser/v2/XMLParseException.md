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

- **[Prev Class](XMLOutputStream.md)**
- **[Next Class](XMLParser.md)**

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

**oracle.xml.parser.v2**

## **Class XMLParseException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **[org.xml.sax.SAXException](../../../../org/xml/sax/SAXException.md)**

      - - **[org.xml.sax.SAXParseException](../../../../org/xml/sax/SAXParseException.md)**

        - - **oracle.xml.parser.v2.XMLParseException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XMLParseException
      extends SAXParseException

  **Indicates that a parsing exception occurred while processing an XML document**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

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

    | Constructor and Description                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `XMLParseException``(java.lang.String mesg, java.lang.String pubId, java.lang.String sysId, int line, int col, int type)`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                            |
    |-----------------------|---------------------------------------------------------------------------------------------------|
    | `java.lang.String`    | `formatErrorMessage``(int i)`<br>Get the error message at specified index                         |
    | `int`                 | `getColumnNumber``(int i)`<br>Get the column number of error at specified index                   |
    | `java.lang.Exception` | `getException``(int i)`<br>Get the exception (if exists) that occured in error at specified index |
    | `int`                 | `getLineNumber``(int i)`<br>Get the line number of error at specified index                       |
    | `java.lang.String`    | `getMessage``(int i)`<br>Get the error message at specified index                                 |
    | `int`                 | `getMessageType``(int i)`<br>Get the type of the error message at specified index                 |
    | `int`                 | `getNumMessages``()`<br>Return the total number of errors/warnings found during parsing           |
    | `java.lang.String`    | `getPublicId``(int i)`<br>Get the public ID of input when error at specified index occured        |
    | `java.lang.String`    | `getSystemId``(int i)`<br>Get the system ID of input when error at specified index occured        |

    - ### Methods inherited from class org.xml.sax.[SAXParseException](../../../../org/xml/sax/SAXParseException.md)

      [`getColumnNumber`](../../../../org/xml/sax/SAXParseException.md)`, `[`getLineNumber`](../../../../org/xml/sax/SAXParseException.md)`, `[`getPublicId`](../../../../org/xml/sax/SAXParseException.md)`, `[`getSystemId`](../../../../org/xml/sax/SAXParseException.md)

    <!-- -->

    - ### Methods inherited from class org.xml.sax.[SAXException](../../../../org/xml/sax/SAXException.md)

      [`getException`](../../../../org/xml/sax/SAXException.md)`, `[`getMessage`](../../../../org/xml/sax/SAXException.md)`, `[`toString`](../../../../org/xml/sax/SAXException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR

          public static final int ERROR

      Code for non-fatal error
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FATAL_ERROR

          public static final int FATAL_ERROR

      Code for fatal error
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### WARNING

          public static final int WARNING

      Code for warning
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLParseException

          public XMLParseException(java.lang.String mesg,
                                   java.lang.String pubId,
                                   java.lang.String sysId,
                                   int line,
                                   int col,
                                   int type)

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

    - #### getMessageType

          public int getMessageType(int i)

      Get the type of the error message at specified index
      Returns:
      The error message type

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

- **[Prev Class](XMLOutputStream.md)**
- **[Next Class](XMLParser.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
