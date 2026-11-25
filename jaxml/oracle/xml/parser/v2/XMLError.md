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

- **[Prev Class](XMLEntityReference.md)**
- **[Next Class](XMLLocator.md)**

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

## **Class XMLError**

- **java.lang.Object**

- - **[oracle.xml.util.XMLError](../../util/XMLError.md)**

  - - **oracle.xml.parser.v2.XMLError**

<!-- -->

- **All Implemented Interfaces:**
  **[DOMError](../../../../org/w3c/dom/DOMError.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLError
      extends XMLError
      implements DOMError

  **This class hold error message and the line number where it occured**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[DOMError](../../../../org/w3c/dom/DOMError.md)**

      **[`SEVERITY_ERROR`](../../../../org/w3c/dom/DOMError.md)`, `[`SEVERITY_FATAL_ERROR`](../../../../org/w3c/dom/DOMError.md)`, `[`SEVERITY_WARNING`](../../../../org/w3c/dom/DOMError.md)**

  <!-- -->

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

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                   |
    |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                    | `error``(int line, int col, java.lang.String pubId, java.lang.String sysId, java.lang.String mesg, int id, int type, boolean stop)`<br>Adds a new error to the vector                                                    |
    | `boolean`                                                 | `error``(short severity, java.lang.String mesg, int id, java.lang.String type, `[`DOMException`](../../../../org/w3c/dom/DOMException.md)` relatedException, java.lang.Object relatedData)`<br>DOM 3.0 error information |
    | `void`                                                    | `flushErrors``()`<br>Flush all the error to the ouput stream output stream defaults or to error handler                                                                                                                  |
    | `void`                                                    | `flushErrors1``()`                                                                                                                                                                                                       |
    | `void`                                                    | `flushNodes``(java.lang.String errMsg, java.lang.String val)`<br>Set the properties for the nodes where validation error occured.                                                                                        |
    | `boolean`                                                 | `getDOMErrorOption``()`<br>Gets the flag for DOM Errors to be returned.                                                                                                                                                  |
    | [`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md) | `getErrorHandler``()`<br>Return register error handler                                                                                                                                                                   |
    | `java.util.Vector`                                        | `getListTrees``()`<br>This method returns the list of stacks that was built with the nodes where the schema validation failed                                                                                            |
    | `boolean`                                                 | `getStopNormalizing``()`                                                                                                                                                                                                 |
    | `void`                                                    | `setDOMErrorOption``(boolean docerrflag)`<br>Sets the flag for DOM Errors to be returned.                                                                                                                                |
    | `void`                                                    | `setErrorHandler``(`[`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md)` err)`<br>Register error handler                                                                                                           |

    - ### Methods inherited from class oracle.xml.util.[XMLError](../../util/XMLError.md)

      [`error`](../../util/XMLError.md)`, `[`error`](../../util/XMLError.md)`, `[`error0`](../../util/XMLError.md)`, `[`error1`](../../util/XMLError.md)`, `[`error2`](../../util/XMLError.md)`, `[`error3`](../../util/XMLError.md)`, `[`flushErrorStream`](../../util/XMLError.md)`, `[`formatErrorMesg`](../../util/XMLError.md)`, `[`getColumnNumber`](../../util/XMLError.md)`, `[`getException`](../../util/XMLError.md)`, `[`getFirstError`](../../util/XMLError.md)`, `[`getLineNumber`](../../util/XMLError.md)`, `[`getLocator`](../../util/XMLError.md)`, `[`getMessage`](../../util/XMLError.md)`, `[`getMessage`](../../util/XMLError.md)`, `[`getMessage0`](../../util/XMLError.md)`, `[`getMessage1`](../../util/XMLError.md)`, `[`getMessage2`](../../util/XMLError.md)`, `[`getMessage3`](../../util/XMLError.md)`, `[`getMessage4`](../../util/XMLError.md)`, `[`getMessage5`](../../util/XMLError.md)`, `[`getMessageId`](../../util/XMLError.md)`, `[`getMessageType`](../../util/XMLError.md)`, `[`getNumExceptions`](../../util/XMLError.md)`, `[`getNumFatalMessages`](../../util/XMLError.md)`, `[`getNumMessages`](../../util/XMLError.md)`, `[`getPublicId`](../../util/XMLError.md)`, `[`getSystemId`](../../util/XMLError.md)`, `[`printErrorListener`](../../util/XMLError.md)`, `[`reset`](../../util/XMLError.md)`, `[`setErrorStream`](../../util/XMLError.md)`, `[`setErrorStream`](../../util/XMLError.md)`, `[`setErrorStream`](../../util/XMLError.md)`, `[`setException`](../../util/XMLError.md)`, `[`setLocale`](../../util/XMLError.md)`, `[`setLocator`](../../util/XMLError.md)`, `[`showWarnings`](../../util/XMLError.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[DOMError](../../../../org/w3c/dom/DOMError.md)

      [`getLocation`](../../../../org/w3c/dom/DOMError.md)`, `[`getMessage`](../../../../org/w3c/dom/DOMError.md)`, `[`getRelatedData`](../../../../org/w3c/dom/DOMError.md)`, `[`getRelatedException`](../../../../org/w3c/dom/DOMError.md)`, `[`getSeverity`](../../../../org/w3c/dom/DOMError.md)`, `[`getType`](../../../../org/w3c/dom/DOMError.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLError

          public XMLError()

      Default constructor

  <!-- -->

  - ### Method Detail

    - #### setErrorHandler

          public void setErrorHandler(ErrorHandler err)

      Register error handler
      Parameters:
      `err` - - ErrorHandler

    <!-- -->

    - #### getErrorHandler

          public ErrorHandler getErrorHandler()

      Return register error handler
      Returns:
      ErrorHandler

    <!-- -->

    - #### error

          public void error(int line,
                            int col,
                            java.lang.String pubId,
                            java.lang.String sysId,
                            java.lang.String mesg,
                            int id,
                            int type,
                            boolean stop)
                     throws XMLParseException

      Adds a new error to the vector
      Parameters:
      `line` - the line number where error occurs

      `col` - the column number where the error occurs

      `pubId` - the public Identifier

      `sysId` - the system identifier

      `mesg` - the error message

      `id` - the error id

      `type` - the error type

      `stop` - boolean to indicate if the processing needs to be stopped.

      Throws:
      [`XMLParseException`](XMLParseException.md) - in case of a fatal error

    <!-- -->

    - #### flushErrors

          public void flushErrors()
                           throws XMLParseException

      Flush all the error to the ouput stream output stream defaults or to error handler
      Throws:
      [`XMLParseException`](XMLParseException.md) - in case of a fatal error

    <!-- -->

    - #### flushErrors1

          public void flushErrors1()
                            throws XMLParseException,
                                   SAXParseException,
                                   SAXException,
                                   java.io.IOException

      Throws:
      [`XMLParseException`](XMLParseException.md)

      [`SAXParseException`](../../../../org/xml/sax/SAXParseException.md)

      [`SAXException`](../../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### flushNodes

          public void flushNodes(java.lang.String errMsg,
                                 java.lang.String val)

      Set the properties for the nodes where validation error occured. Flush the XMLNode objects from the locator and add them to a a stack.Finally, the stack is added to a Vector which keeps track all the nodes where Validation failed.
      Parameters:
      `errMsg` - - Error message returned from validator

      `val` - - Node/Attribute name.

    <!-- -->

    - #### getListTrees

          public java.util.Vector getListTrees()

      This method returns the list of stacks that was built with the nodes where the schema validation failed

    <!-- -->

    - #### setDOMErrorOption

          public void setDOMErrorOption(boolean docerrflag)

      Sets the flag for DOM Errors to be returned. This flag should be used only when trying to validate an already parsed document
      Parameters:
      `docerrflag` - - boolean

    <!-- -->

    - #### getDOMErrorOption

          public boolean getDOMErrorOption()

      Gets the flag for DOM Errors to be returned. This flag should be used only when trying to validate a parsed XML document
      Returns:
      docerrflag - boolean

    <!-- -->

    - #### error

          public boolean error(short severity,
                               java.lang.String mesg,
                               int id,
                               java.lang.String type,
                               DOMException relatedException,
                               java.lang.Object relatedData)

      DOM 3.0 error information

    <!-- -->

    - #### getStopNormalizing

          public boolean getStopNormalizing()

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

- **[Prev Class](XMLEntityReference.md)**
- **[Next Class](XMLLocator.md)**

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
