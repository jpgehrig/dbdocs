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

- **[Prev Class](XSDValProcess.md)**
- **[Next Class](XSLStylesheetProcess.md)**

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

**oracle.xml.pipeline.processes**

## **Class XSLProcess**

- **java.lang.Object**

- - **[oracle.xml.pipeline.controller.Process](../controller/Process.md)**

  - - **oracle.xml.pipeline.processes.XSLProcess**

<!-- -->

- **All Implemented Interfaces:**
  **java.lang.Runnable, [ErrorListener](../../../../javax/xml/transform/ErrorListener.md), [PipelineConstants](../controller/PipelineConstants.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XSLProcess
      extends Process
      implements ErrorListener

  **Extends the pipeline Process class to create a wrapper around JXTransformer to be used by the pipeline framework. Its parameters are: Inputs - "document" (dom) Params - "stylesheet" (XSLStylesheet), "outputEncoding" (String) Outputs - "result" (stream, dom, sax) Outparams - none**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface oracle.xml.pipeline.controller.[PipelineConstants](../controller/PipelineConstants.md)**

      **[`COMPSTREAMRESULT`](../controller/PipelineConstants.md)`, `[`COMPSTREAMSOURCE`](../controller/PipelineConstants.md)`, `[`DOCFRAG`](../controller/PipelineConstants.md)`, `[`DOCUMENT`](../controller/PipelineConstants.md)`, `[`DOMRESULT`](../controller/PipelineConstants.md)`, `[`DOMSOURCE`](../controller/PipelineConstants.md)`, `[`ELEMENT`](../controller/PipelineConstants.md)`, `[`PROCESS_WAITING`](../controller/PipelineConstants.md)`, `[`SAXRESULT`](../controller/PipelineConstants.md)`, `[`SAXSOURCE`](../controller/PipelineConstants.md)`, `[`STREAMRESULT`](../controller/PipelineConstants.md)`, `[`STREAMSOURCE`](../controller/PipelineConstants.md)**

  <!-- -->

  -

    ### **Method Summary**

    -

      ### **Methods inherited from class oracle.xml.pipeline.controller.[Process](../controller/Process.md)**

      **[`convertFromDOM`](../controller/Process.md)`, `[`convertFromSAX`](../controller/Process.md)`, `[`convertFromStream`](../controller/Process.md)`, `[`error`](../controller/Process.md)`, `[`getErrorDocument`](../controller/Process.md)`, `[`getErrorSource`](../controller/Process.md)`, `[`getErrorStream`](../controller/Process.md)`, `[`getErrorStream`](../controller/Process.md)`, `[`getInParamValue`](../controller/Process.md)`, `[`getInput`](../controller/Process.md)`, `[`getOutParamValue`](../controller/Process.md)`, `[`getOutput`](../controller/Process.md)`, `[`getOutputStream`](../controller/Process.md)`, `[`getOutputWriter`](../controller/Process.md)`, `[`getSAXContentHandler`](../controller/Process.md)`, `[`getSAXErrorHandler`](../controller/Process.md)`, `[`info`](../controller/Process.md)`, `[`setOutputResult`](../controller/Process.md)**

    <!-- -->

    -

      ### **Methods inherited from class java.lang.Object**

      **`equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`**

    <!-- -->

    -

      ### **Methods inherited from interface javax.xml.transform.[ErrorListener](../../../../javax/xml/transform/ErrorListener.md)**

      **[`error`](../../../../javax/xml/transform/ErrorListener.md)`, `[`fatalError`](../../../../javax/xml/transform/ErrorListener.md)`, `[`warning`](../../../../javax/xml/transform/ErrorListener.md)**

    <!-- -->

    -

      ### **Methods inherited from interface java.lang.Runnable**

      **`run`**

    <!-- -->

    -

      ### **Methods inherited from interface org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)**

      **[`error`](../../../../org/xml/sax/ErrorHandler.md)`, `[`fatalError`](../../../../org/xml/sax/ErrorHandler.md)`, `[`warning`](../../../../org/xml/sax/ErrorHandler.md)**

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XSDValProcess.md)**
- **[Next Class](XSLStylesheetProcess.md)**

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
