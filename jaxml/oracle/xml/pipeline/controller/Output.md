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

- **[Prev Class](orapipe.md)**
- **[Next Class](PipeDocElement.md)**

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

## **Class Output**

- **java.lang.Object**

- - **[oracle.xml.pipeline.controller.PipeDocElement](PipeDocElement.md)**

  - - **oracle.xml.pipeline.controller.Output**

<!-- -->

- **All Implemented Interfaces:**
  **[PipelineConstants](PipelineConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class Output
      extends PipeDocElement

  **This class represents an output object of a pipeline process.**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.pipeline.controller.[PipelineConstants](PipelineConstants.md)**

      **[`COMPSTREAMRESULT`](PipelineConstants.md)`, `[`COMPSTREAMSOURCE`](PipelineConstants.md)`, `[`DOCFRAG`](PipelineConstants.md)`, `[`DOCUMENT`](PipelineConstants.md)`, `[`DOMRESULT`](PipelineConstants.md)`, `[`DOMSOURCE`](PipelineConstants.md)`, `[`ELEMENT`](PipelineConstants.md)`, `[`PROCESS_WAITING`](PipelineConstants.md)`, `[`SAXRESULT`](PipelineConstants.md)`, `[`SAXSOURCE`](PipelineConstants.md)`, `[`STREAMRESULT`](PipelineConstants.md)`, `[`STREAMSOURCE`](PipelineConstants.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `isXMLType``(int type)`<br>Checks whether this Output object supports the following types of XML as output. |
    | `void`            | `supportType``(int type)`<br>Set the types of output to support for this Output object.                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### supportType

          public void supportType(int type)

      Set the types of output to support for this Output object.
      Parameters:
      `type` - constants allowed are DOMRESULT, SAXRESULT, STREAMRESULT, COMPSTREAMRESULT, DOCUMENT, DOCFRAG, ELEMENT

    <!-- -->

    - #### isXMLType

          public boolean isXMLType(int type)

      Checks whether this Output object supports the following types of XML as output.
      Parameters:
      `type` - constants allowed are DOMRESULT, SAXRESULT, STREAMRESULT, COMPSTREAMRESULT, DOCUMENT, DOCFRAG, ELEMENT

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

- **[Prev Class](orapipe.md)**
- **[Next Class](PipeDocElement.md)**

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
