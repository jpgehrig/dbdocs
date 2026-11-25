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

- **[Prev Class](PipelineConstants.md)**
- **[Next Class](PipelineErrorHandler.md)**

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

**oracle.xml.pipeline.controller**

## **Class PipelineDoc**

- **java.lang.Object**

- - **oracle.xml.pipeline.controller.PipelineDoc**

<!-- -->

- **All Implemented Interfaces:**
  **[PipelineConstants](PipelineConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class PipelineDoc
      extends java.lang.Object
      implements PipelineConstants

  **Encapsulates the pipeline doc, which forms the input to the pipeline execution.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.pipeline.controller.[PipelineConstants](PipelineConstants.md)**

      **[`COMPSTREAMRESULT`](PipelineConstants.md)`, `[`COMPSTREAMSOURCE`](PipelineConstants.md)`, `[`DOCFRAG`](PipelineConstants.md)`, `[`DOCUMENT`](PipelineConstants.md)`, `[`DOMRESULT`](PipelineConstants.md)`, `[`DOMSOURCE`](PipelineConstants.md)`, `[`ELEMENT`](PipelineConstants.md)`, `[`PROCESS_WAITING`](PipelineConstants.md)`, `[`SAXRESULT`](PipelineConstants.md)`, `[`SAXSOURCE`](PipelineConstants.md)`, `[`STREAMRESULT`](PipelineConstants.md)`, `[`STREAMSOURCE`](PipelineConstants.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                               |
    |---------------------------------------------------------------------------------------------------------------------------|
    | `PipelineDoc``(`[`InputSource`](../../../../org/xml/sax/InputSource.md)` in, boolean validate)`<br>Create a pipeline doc. |
    | `PipelineDoc``(java.io.InputStream in, boolean validate)`<br>Create a pipeline doc.                                       |
    | `PipelineDoc``(java.io.Reader r, boolean validate)`<br>Create a pipeline doc.                                             |
    | `PipelineDoc``(java.lang.String in, boolean validate)`<br>Create a pipeline doc.                                          |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                    |
    |-------------------------------------------------|-----------------------------------------------------------|
    | [`XMLDocument`](../../parser/v2/XMLDocument.md) | `getDocument``()`<br>Get the encapsulated document object |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PipelineDoc

          public PipelineDoc(InputSource in,
                             boolean validate)
                      throws XMLParseException,
                             SAXException,
                             java.io.IOException,
                             XSDException,
                             java.lang.Exception

      Create a pipeline doc.
      Parameters:
      `in` - - xml pipeline doc as InputSource

      `validate` - - validate against schema

      Throws:
      [`XMLParseException`](../../parser/v2/XMLParseException.md) - thrown for any parsing error

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown if any SAX error

      `java.io.IOException` - thrown if error reading input stream

      [`XSDException`](../../parser/schema/XSDException.md) - thrown if error during schema validation

      `java.lang.Exception` - thrown if error building XMLSchema object

    <!-- -->

    - #### PipelineDoc

          public PipelineDoc(java.io.InputStream in,
                             boolean validate)
                      throws XMLParseException,
                             SAXException,
                             java.io.IOException,
                             XSDException,
                             java.lang.Exception

      Create a pipeline doc.
      Parameters:
      `in` - - xml pipeline doc as InputStream

      `validate` - - validate against schema or not

      Throws:
      [`XMLParseException`](../../parser/v2/XMLParseException.md) - thrown for any parsing error

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown if any SAX error

      `java.io.IOException` - thrown if error reading input stream

      [`XSDException`](../../parser/schema/XSDException.md) - thrown if error during schema validation

      `java.lang.Exception` - thrown if error building XMLSchema object

    <!-- -->

    - #### PipelineDoc

          public PipelineDoc(java.io.Reader r,
                             boolean validate)
                      throws XMLParseException,
                             SAXException,
                             java.io.IOException,
                             XSDException,
                             java.lang.Exception

      Create a pipeline doc.
      Parameters:
      `r` - - xml pipeline doc as Reader

      `validate` - - validate against schema or not

      Throws:
      [`XMLParseException`](../../parser/v2/XMLParseException.md) - thrown for any parsing error

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown if any SAX error

      `java.io.IOException` - thrown if error reading input stream

      [`XSDException`](../../parser/schema/XSDException.md) - thrown if error during schema validation

      `java.lang.Exception` - thrown if error building XMLSchema object

    <!-- -->

    - #### PipelineDoc

          public PipelineDoc(java.lang.String in,
                             boolean validate)
                      throws XMLParseException,
                             SAXException,
                             java.io.IOException,
                             XSDException,
                             java.lang.Exception

      Create a pipeline doc.
      Parameters:
      `in` - - xml pipeline doc as a String

      `validate` - - validate against schema or not

      Throws:
      [`XMLParseException`](../../parser/v2/XMLParseException.md) - thrown for any parsing error

      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown if any SAX error

      `java.io.IOException` - thrown if error reading input string

      [`XSDException`](../../parser/schema/XSDException.md) - thrown if error during schema validation

      `java.lang.Exception` - thrown if error building XMLSchema object

  <!-- -->

  - ### Method Detail

    - #### getDocument

          public XMLDocument getDocument()

      Get the encapsulated document object
      Returns:
      XMLDocument object

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

- **[Prev Class](PipelineConstants.md)**
- **[Next Class](PipelineErrorHandler.md)**

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
