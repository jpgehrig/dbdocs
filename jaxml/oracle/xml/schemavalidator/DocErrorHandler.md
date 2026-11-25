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

- **Prev Class**
- **[Next Class](XSDValidator.md)**

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

**oracle.xml.schemavalidator**

## **Class DocErrorHandler**

- **java.lang.Object**

- - **oracle.xml.schemavalidator.DocErrorHandler**

<!-- -->

- **All Implemented Interfaces:**
  **[ErrorHandler](../../../org/xml/sax/ErrorHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DocErrorHandler
      extends java.lang.Object
      implements ErrorHandler

  **This class implements the three methods,i.e., error(),warning(), fatalError() defined in the ErrorHandler interface. All three methods adds the line, column, node information along with the error message to a vector maintained internally. This handler is useful in getting a dump of the error that occured during the schema validation.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `DocErrorHandler``()`<br>Default Constructor for the ErrorHandler |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                           |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `error``(`[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` ex)`<br>Adds a Error message to the vector           |
    | `void`             | `fatalError``(`[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` ex)`<br>Adds a fatalError message to the vector |
    | `java.util.Vector` | `getErrorList``()`<br>Gets the List of Error messages returned by the Validator.                                                 |
    | `int`              | `getNumErrors``()`<br>Gets the List of Error messages returned by the Validator.                                                 |
    | `void`             | `warning``(`[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` ex)`<br>Adds a warning message to the vector       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DocErrorHandler

          public DocErrorHandler()
                          throws java.io.IOException,
                                 java.io.FileNotFoundException

      Default Constructor for the ErrorHandler
      Throws:
      `java.io.IOException`

      `java.io.FileNotFoundException`

  <!-- -->

  - ### Method Detail

    - #### warning

          public void warning(SAXParseException ex)
                       throws SAXException

      Adds a warning message to the vector
      Specified by:
      [`warning`](../../../org/xml/sax/ErrorHandler.md) in interface [`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)

      Parameters:
      `ex` - - SAXParseException ex

      Throws:
      `-` - SAXException

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

    <!-- -->

    - #### error

          public void error(SAXParseException ex)
                     throws SAXException

      Adds a Error message to the vector
      Specified by:
      [`error`](../../../org/xml/sax/ErrorHandler.md) in interface [`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)

      Parameters:
      `ex` - - SAXParseException ex

      Throws:
      `-` - SAXException

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

    <!-- -->

    - #### fatalError

          public void fatalError(SAXParseException ex)
                          throws SAXException

      Adds a fatalError message to the vector
      Specified by:
      [`fatalError`](../../../org/xml/sax/ErrorHandler.md) in interface [`ErrorHandler`](../../../org/xml/sax/ErrorHandler.md)

      Parameters:
      `ex` - - SAXParseException ex

      Throws:
      `-` - SAXException

      [`SAXException`](../../../org/xml/sax/SAXException.md) - Any SAX exception, possibly wrapping another exception.

      See Also:
      [`SAXParseException`](../../../org/xml/sax/SAXParseException.md)

    <!-- -->

    - #### getErrorList

          public java.util.Vector getErrorList()

      Gets the List of Error messages returned by the Validator.
      Returns:
      \- array of strings

    <!-- -->

    - #### getNumErrors

          public int getNumErrors()

      Gets the List of Error messages returned by the Validator.
      Returns:
      \- array of strings

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

- **Prev Class**
- **[Next Class](XSDValidator.md)**

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
