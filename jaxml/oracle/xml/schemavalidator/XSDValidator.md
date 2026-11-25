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

- **[Prev Class](DocErrorHandler.md)**
- **[Next Class](XSDValidatorBeanInfo.md)**

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

## **Class XSDValidator**

- **java.lang.Object**

- - **oracle.xml.schemavalidator.XSDValidator**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XSDValidator
      extends java.lang.Object

  **This class encapsulates the oracle.xml.parser.schema.XSDValidator class and adds functionalities for validating a DOM tree. The schema document is a constant and the validation is done for XMLDocuments that can be passed as InputStreams,URLs etc. The validation is done only after the DOM tree is built in all the cases. Nodes with errors are returned in a vector of stack trees where the top element of the stack represents the root node and child nodes are obtained by popping the elemnts of the stack.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                    |
    |----------------------------------------------------------------|
    | `XSDValidator``()`<br>Constructor for oracle.xml.XSDValidator. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                      | Method and Description                                                                                                               |
    |----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLError`](../parser/v2/XMLError.md) | `getError``()`<br>gets the XMLError object for this object.                                                                          |
    | `java.util.Vector`                     | `getStackList``()`<br>Gets the List of Tree Paths in the XMLDocument which leads to the node that encountered a validation error.    |
    | `void`                                 | `setError``(`[`XMLError`](../parser/v2/XMLError.md)` err)`<br>Sets the XMLError object for this object.                              |
    | `void`                                 | `setSchema``(`[`XMLSchema`](../parser/schema/XMLSchema.md)` xmlsch)`<br>Sets the XMLSchema object for this object.                   |
    | `void`                                 | `validate``(java.io.InputStream is)`<br>Validates the InputStream containing the XML instance document against the XMLSchema object. |
    | `void`                                 | `validate``(java.net.URL url)`<br>Validates the URL containing the XML instance document against the XMLSchema object.               |
    | `void`                                 | `validate``(`[`XMLDocument`](../parser/v2/XMLDocument.md)` xmldoc)`<br>Validates an XMLDocument against the XMLSchema object.        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSDValidator

          public XSDValidator()
                       throws XSDException

      Constructor for oracle.xml.XSDValidator. This also constructs the oracle.xml.parser.schema.XSDValidator, XMLSchema & XMLError objects.
      Throws:
      [`XSDException`](../parser/schema/XSDException.md)

  <!-- -->

  - ### Method Detail

    - #### validate

          public void validate(XMLDocument xmldoc)
                        throws XSDException,
                               SAXException,
                               java.io.IOException

      Validates an XMLDocument against the XMLSchema object. The XMLError is set for returning the DOM errors nodes.
      Parameters:
      `xmldoc` - -- Parsed XMLDocument

      Throws:
      [`XSDException`](../parser/schema/XSDException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### validate

          public void validate(java.io.InputStream is)
                        throws XSDException,
                               SAXException,
                               java.io.IOException

      Validates the InputStream containing the XML instance document against the XMLSchema object. The XMLError is set for returning the DOM errors nodes.
      Parameters:
      `is` - -- Parsed XMLDocument

      Throws:
      [`XSDException`](../parser/schema/XSDException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### validate

          public void validate(java.net.URL url)
                        throws XSDException,
                               SAXException,
                               java.io.IOException

      Validates the URL containing the XML instance document against the XMLSchema object. The XMLError is set for returning the DOM errors nodes.
      Parameters:
      `url` - -- Parsed XMLDocument

      Throws:
      [`XSDException`](../parser/schema/XSDException.md)

      [`SAXException`](../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

    <!-- -->

    - #### setSchema

          public void setSchema(XMLSchema xmlsch)

      Sets the XMLSchema object for this object. The validation is done against this schema object.
      Parameters:
      `xmlsch` - -- XMLSchema object

    <!-- -->

    - #### setError

          public void setError(XMLError err)

      Sets the XMLError object for this object.
      Parameters:
      `err` - -- XMLError object

    <!-- -->

    - #### getError

          public XMLError getError()

      gets the XMLError object for this object.
      Returns:
      err -- XMLError object

    <!-- -->

    - #### getStackList

          public java.util.Vector getStackList()

      Gets the List of Tree Paths in the XMLDocument which leads to the node that encountered a validation error.
      Returns:
      \- java.util.Vector

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

- **[Prev Class](DocErrorHandler.md)**
- **[Next Class](XSDValidatorBeanInfo.md)**

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
