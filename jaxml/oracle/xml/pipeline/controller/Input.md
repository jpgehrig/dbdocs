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

- **Prev Class**
- **[Next Class](orapipe.md)**

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

## **Class Input**

- **java.lang.Object**

- - **[oracle.xml.pipeline.controller.PipeDocElement](PipeDocElement.md)**

  - - **oracle.xml.pipeline.controller.Input**

<!-- -->

- **All Implemented Interfaces:**
  **[PipelineConstants](PipelineConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class Input
      extends PipeDocElement

  **This class represents an input object of a pipeline process.**

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

    | Modifier and Type | Method and Description                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------|
    | `boolean`         | `isXMLType``(int type)`<br>Checks whether this Input object supports the following types of XML as input. |
    | `void`            | `supportType``(int type)`<br>Set the types of input to support for this Input.                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### supportType

          public void supportType(int type)

      Set the types of input to support for this Input.
      Parameters:
      `type` - constants allowed are DOMSOURCE, SAXSOURCE, STREAMSOURCE, COMPSTREAMSOURCE, DOCUMENT, DOCFRAG, ELEMENT

    <!-- -->

    - #### isXMLType

          public boolean isXMLType(int type)

      Checks whether this Input object supports the following types of XML as input.
      Parameters:
      `type` - constants allowed are DOMSOURCE, SAXSOURCE, STREAMSOURCE, COMPSTREAMSOURCE, DOCUMENT, DOCFRAG, ELEMENT

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

- **Prev Class**
- **[Next Class](orapipe.md)**

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
