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

- **[Prev Class](PipelineException.md)**
- **[Next Class](Process.md)**

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

## **Class PipelineProcessor**

- **java.lang.Object**

- - **oracle.xml.pipeline.controller.PipelineProcessor**

<!-- -->

- **All Implemented Interfaces:**
  **[PipelineConstants](PipelineConstants.md)**

  ------------------------------------------------------------------------

  **
  **

      public class PipelineProcessor
      extends java.lang.Object
      implements PipelineConstants

  **The top level class which executes the pipeline.**

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

    | Constructor and Description |
    |-----------------------------|
    | `PipelineProcessor``()`     |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `executePipeline``()`<br>Execute the pipeline based on the PipelineDoc set earlier by setPipelineDoc().                                                                      |
    | `int`             | `getExecutionMode``()`<br>Get the type of execution mode                                                                                                                     |
    | `boolean`         | `isForceSpecified``()`<br>Has force been specified for pipeline execution                                                                                                    |
    | `void`            | `setErrorHandler``(`[`PipelineErrorHandler`](PipelineErrorHandler.md)` e)`<br>Set the error handler for the pipeline.                                                        |
    | `void`            | `setExecutionMode``(int m)`<br>Set the type of execution mode, default is parallel.                                                                                          |
    | `void`            | `setForce``(boolean f)`<br>If force is specified, then the pipeline will always execute, regardless of whether the target is up-to-date with respect to the pipeline inputs. |
    | `void`            | `setPipelineDoc``(`[`PipelineDoc`](PipelineDoc.md)` doc)`<br>Set the PipelineDoc object for the pipeline process to process                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PipelineProcessor

          public PipelineProcessor()

  <!-- -->

  - ### Method Detail

    - #### setPipelineDoc

          public void setPipelineDoc(PipelineDoc doc)

      Set the PipelineDoc object for the pipeline process to process
      Parameters:
      `doc` - - PipelineDoc to be processed

    <!-- -->

    - #### setErrorHandler

          public void setErrorHandler(PipelineErrorHandler e)

      Set the error handler for the pipeline. This is mandatory to execute the pipeline.
      Parameters:
      `e` - - error handler conforming to the PipelineErrorHandler interface

    <!-- -->

    - #### setExecutionMode

          public void setExecutionMode(int m)

      Set the type of execution mode, default is parallel.
      Parameters:
      `m` - - execution mode can be PIPELINE_SEQUENTIAL, PIPELINE_PARALLEL

    <!-- -->

    - #### getExecutionMode

          public int getExecutionMode()

      Get the type of execution mode
      Returns:
      \- execution mode can be PIPELINE_SEQUENTIAL, PIPELINE_PARALLEL

    <!-- -->

    - #### setForce

          public void setForce(boolean f)

      If force is specified, then the pipeline will always execute, regardless of whether the target is up-to-date with respect to the pipeline inputs.
      Parameters:
      `f` - - boolean true or false

    <!-- -->

    - #### isForceSpecified

          public boolean isForceSpecified()

      Has force been specified for pipeline execution
      Returns:
      boolean - true if force is specified otherwise false

    <!-- -->

    - #### executePipeline

          public void executePipeline()
                               throws java.net.MalformedURLException,
                                      PipelineException,
                                      java.lang.InterruptedException

      Execute the pipeline based on the PipelineDoc set earlier by setPipelineDoc().
      Throws:
      `java.net.MalformedURLException`

      [`PipelineException`](PipelineException.md)

      `java.lang.InterruptedException` - thrown by threads in parallel execution

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

- **[Prev Class](PipelineException.md)**
- **[Next Class](Process.md)**

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
