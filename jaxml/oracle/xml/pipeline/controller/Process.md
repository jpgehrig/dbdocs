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

- **[Prev Class](PipelineProcessor.md)**
- **Next Class**

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

## **Class Process**

- **java.lang.Object**

- - **oracle.xml.pipeline.controller.Process**

<!-- -->

- **All Implemented Interfaces:**
  **java.lang.Runnable, [PipelineConstants](PipelineConstants.md), [ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[CompressReaderProcess](../processes/CompressReaderProcess.md), [CompressWriterProcess](../processes/CompressWriterProcess.md), [DOMParserProcess](../processes/DOMParserProcess.md), [SAXParserProcess](../processes/SAXParserProcess.md), [XPathProcess](../processes/XPathProcess.md), [XSDSchemaBuilder](../processes/XSDSchemaBuilder.md), [XSDValProcess](../processes/XSDValProcess.md), [XSLProcess](../processes/XSLProcess.md), [XSLStylesheetProcess](../processes/XSLStylesheetProcess.md)**

  ------------------------------------------------------------------------

  **
  **

      public class Process
      extends java.lang.Object
      implements java.lang.Runnable, PipelineConstants, ErrorHandler

  **Base class for all pipeline process definitions. To create a custom pipeline process, you need to create a class which extends from the Process class. At the minimum, every custom process should overwrite the initialize() and execute() method of this class. If the custom process takes SAX events as input, it should overwrite the SAXContentHandler() method to return the appropriate ContentHandler which will handle incoming SAX events.**

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

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                          |
    |---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                        | `convertFromDOM``(`[`DOMResult`](../../../../javax/xml/transform/dom/DOMResult.md)` res, `[`Output`](Output.md)` output)`<br>Should be called by the Process which outputs DOM.                                                                 |
    | `void`                                                        | `convertFromSAX``(`[`SAXResult`](../../../../javax/xml/transform/sax/SAXResult.md)` result, `[`Output`](Output.md)` output)`<br>Should be called by the Process which outputs SAX events.                                                       |
    | `void`                                                        | `convertFromStream``(`[`StreamResult`](../../../../javax/xml/transform/stream/StreamResult.md)` res, `[`Output`](Output.md)` output)`<br>Should be called by the Process which outputs xml as Stream.                                           |
    | `void`                                                        | `error``(int type, java.lang.Exception e)`<br>Called by a custom Process whenever an error occurs.                                                                                                                                              |
    | [`XMLDocument`](../../parser/v2/XMLDocument.md)               | `getErrorDocument``(java.lang.String errorName, boolean convert)`<br>Get the error element as an XML Document tree                                                                                                                              |
    | [`Source`](../../../../javax/xml/transform/Source.md)         | `getErrorSource``(java.lang.String errorName)`<br>Retrieve the error element as Source                                                                                                                                                          |
    | `java.io.InputStream`                                         | `getErrorStream``(java.lang.String errorName, boolean convert)`<br>Get the error element as an Input stream for reading error.                                                                                                                  |
    | `void`                                                        | `getErrorStream``(java.lang.String errorName, java.io.OutputStream out, boolean convert)`<br>Write the error element to the outputstream provided.                                                                                              |
    | `java.lang.Object`                                            | `getInParamValue``(java.lang.String name)`<br>Get an input param value based on its name                                                                                                                                                        |
    | [`Input`](Input.md)                                           | `getInput``(java.lang.String inputName)`<br>Retrieve the Input object by name                                                                                                                                                                   |
    | `java.lang.Object`                                            | `getOutParamValue``(java.lang.String name)`<br>Get the output param value based on its name                                                                                                                                                     |
    | [`Output`](Output.md)                                         | `getOutput``(java.lang.String outputName)`<br>Retrieve a particular output by name                                                                                                                                                              |
    | `java.io.OutputStream`                                        | `getOutputStream``(java.lang.String outputName)`<br>Get the output stream for printing to a specific output                                                                                                                                     |
    | `java.io.Writer`                                              | `getOutputWriter``(java.lang.String outputName)`<br>Get the output writer for writing to a specific output                                                                                                                                      |
    | [`ContentHandler`](../../../../org/xml/sax/ContentHandler.md) | `getSAXContentHandler``(`[`Output`](Output.md)` out)`<br>Get the ContentHandler which will handle the sax events generated.                                                                                                                     |
    | [`ErrorHandler`](../../../../org/xml/sax/ErrorHandler.md)     | `getSAXErrorHandler``(`[`Output`](Output.md)` out)`<br>Get the SAX ErrorHandler which will handle the sax error events generated.                                                                                                               |
    | `void`                                                        | `info``(java.lang.String msg)`<br>Called by a Process to report an informational message and continue with execution.                                                                                                                           |
    | `void`                                                        | `setOutputResult``(java.lang.String outputName, `[`Result`](../../../../javax/xml/transform/Result.md)` res)`<br>All user defined processes (extending from Process) need to create a Result object and set it in the output using this method. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.lang.Runnable

      `run`

    <!-- -->

    - ### Methods inherited from interface org.xml.sax.[ErrorHandler](../../../../org/xml/sax/ErrorHandler.md)

      [`error`](../../../../org/xml/sax/ErrorHandler.md)`, `[`fatalError`](../../../../org/xml/sax/ErrorHandler.md)`, `[`warning`](../../../../org/xml/sax/ErrorHandler.md)

<!-- -->

- - ### Method Detail

    - #### getInput

          public final Input getInput(java.lang.String inputName)

      Retrieve the Input object by name
      Parameters:
      `inputName` - input name as String

      Returns:
      Input object if there one by inputName, otherwise null

    <!-- -->

    - #### getOutput

          public Output getOutput(java.lang.String outputName)

      Retrieve a particular output by name
      Parameters:
      `outputName` - as a String

      Returns:
      Output object, null if no output by this name exists

    <!-- -->

    - #### getInParamValue

          public final java.lang.Object getInParamValue(java.lang.String name)

      Get an input param value based on its name
      Parameters:
      `name` - name of InParam as String

      Returns:
      InParam value as type Object, null if none exists

    <!-- -->

    - #### getOutParamValue

          public final java.lang.Object getOutParamValue(java.lang.String name)

      Get the output param value based on its name
      Parameters:
      `name` - OutParam name as String

      Returns:
      OutParam value of type Object

    <!-- -->

    - #### setOutputResult

          public final void setOutputResult(java.lang.String outputName,
                                            Result res)

      All user defined processes (extending from Process) need to create a Result object and set it in the output using this method.
      Parameters:
      `outputName` - as String

      `res` - Result object

    <!-- -->

    - #### getOutputStream

          public final java.io.OutputStream getOutputStream(java.lang.String outputName)
                                                     throws java.io.FileNotFoundException,
                                                            java.io.IOException

      Get the output stream for printing to a specific output
      Parameters:
      `outputName` - name of output

      Returns:
      OutputStream for printing

      Throws:
      `java.io.FileNotFoundException`

      `java.io.IOException`

    <!-- -->

    - #### getOutputWriter

          public final java.io.Writer getOutputWriter(java.lang.String outputName)
                                               throws java.io.FileNotFoundException,
                                                      java.io.IOException

      Get the output writer for writing to a specific output
      Parameters:
      `outputName` - name of output

      Returns:
      Writer for printing

      Throws:
      `java.io.FileNotFoundException`

      `java.io.IOException`

    <!-- -->

    - #### getErrorSource

          public Source getErrorSource(java.lang.String errorName)

      Retrieve the error element as Source
      Parameters:
      `errorName` - name of error from pipeline document

      Returns:
      Source error element as a Source object

    <!-- -->

    - #### getErrorStream

          public void getErrorStream(java.lang.String errorName,
                                     java.io.OutputStream out,
                                     boolean convert)
                              throws java.io.IOException

      Write the error element to the outputstream provided. If convert is true then convert from error node to stream.
      Parameters:
      `errorName` - name of error element

      `out` - outputstream to write to

      `convert` - convert from DOM to stream or not

      Throws:
      `java.io.IOException` - while writing to outputstream

    <!-- -->

    - #### getErrorStream

          public final java.io.InputStream getErrorStream(java.lang.String errorName,
                                                          boolean convert)
                                                   throws java.io.IOException

      Get the error element as an Input stream for reading error.
      Parameters:
      `errorName` - error element name as String

      `convert` - convert from Node to InputStream or not

      Returns:
      InputStream of of error element

      Throws:
      `java.io.IOException` - reading from error element

    <!-- -->

    - #### getErrorDocument

          public XMLDocument getErrorDocument(java.lang.String errorName,
                                              boolean convert)
                                       throws SAXException,
                                              XMLParseException,
                                              java.io.IOException

      Get the error element as an XML Document tree
      Parameters:
      `errorName` - error element name as String

      `convert` - convert from stream to DOM if necessary

      Returns:
      XMLDocument error element as XMLDocument

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - while parsing

      [`XMLParseException`](../../parser/v2/XMLParseException.md) - while parsing

      `java.io.IOException`

    <!-- -->

    - #### error

          public final void error(int type,
                                  java.lang.Exception e)
                           throws PipelineException

      Called by a custom Process whenever an error occurs.
      Parameters:
      `type` - error type as defined in PipelineConstants

      `e` - exception

      Throws:
      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### info

          public void info(java.lang.String msg)

      Called by a Process to report an informational message and continue with execution.
      Parameters:
      `msg` - - message to report

    <!-- -->

    - #### getSAXContentHandler

          public final ContentHandler getSAXContentHandler(Output out)
                                                    throws PipelineException

      Get the ContentHandler which will handle the sax events generated. This function will handle the conversion from SAX to DOM or Stream if its necessary. If this method returns null, then call setProcessStatus(PROCESS_WAITING), and return from execute().
      Parameters:
      `out` - the Output object which is the SAX source

      Returns:
      ContentHandler for taking SAX events as input to this process

      Throws:
      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### getSAXErrorHandler

          public final ErrorHandler getSAXErrorHandler(Output out)

      Get the SAX ErrorHandler which will handle the sax error events generated.
      Parameters:
      `out` - Output object which is the SAX source

      Returns:
      ErrorHandler will be called on input SAX error

      Throws:
      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### convertFromSAX

          public final void convertFromSAX(SAXResult result,
                                           Output output)
                                    throws java.io.FileNotFoundException,
                                           java.io.IOException

      Should be called by the Process which outputs SAX events. It is assumed that the ContentHandler used by the Process has been fetched using getSAXContentHandler. This function will check the input type of the dependent process or processes and perform the conversion from SAX to DOM/Stream. The function will call setOutputResult as there could be multiple results to be set for multiple inputs
      Parameters:
      `result` - the process result as a SAXResult object

      `output` - output object to be associated with the SAX, to be piped into the input of the next process in pipeline

      Throws:
      `FileNoFoundException`

      `java.io.IOException`

      `java.io.FileNotFoundException`

    <!-- -->

    - #### convertFromDOM

          public final void convertFromDOM(DOMResult res,
                                           Output output)
                                    throws SAXException,
                                           java.io.IOException,
                                           PipelineException

      Should be called by the Process which outputs DOM. This function will check the input type of the dependent process or processes and perform the conversion from DOM to SAX/Stream. The function will call setOutputResult as there could be multiple results to be set for multiple inputs
      Parameters:
      `res` - the process result as a DOMResult object

      `output` - output object associated with result, to be piped to the next process in pipeline

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### convertFromStream

          public final void convertFromStream(StreamResult res,
                                              Output output)
                                       throws SAXException,
                                              java.io.IOException,
                                              PipelineException

      Should be called by the Process which outputs xml as Stream. This function will check the input type of the dependent process or processes and perform the conversion from Stream to DOM/SAX. The function will call setOutputResult as there could be multiple results to be set for multiple inputs.
      Parameters:
      `res` - the process result as a StreamResult object

      `output` - output object to be associated with the result, to be piped to the input of the next process in the pipeline

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md)

      `java.io.IOException`

      [`PipelineException`](PipelineException.md)

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

- **[Prev Class](PipelineProcessor.md)**
- **Next Class**

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
