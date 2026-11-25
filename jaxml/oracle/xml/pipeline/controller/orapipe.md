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

- **[Prev Class](Input.md)**
- **[Next Class](Output.md)**

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

## **Class orapipe**

- **java.lang.Object**

- - **oracle.xml.pipeline.controller.orapipe**

<!-- -->

- **All Implemented Interfaces:**
  **[PipelineConstants](PipelineConstants.md), [PipelineErrorHandler](PipelineErrorHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public class orapipe
      extends java.lang.Object
      implements PipelineErrorHandler, PipelineConstants

  **The orapipe class provides a command-line interface to validate and execute the pipedoc for running connecting xml components together.**
           java oracle.xml.pipeline.controller.orapipe options* <pipedoc>
           -help                    Prints the help message
           -version                 Prints the release version
           -sequential              Executes the pipeline in a sequential mode,
                                    default is parallel
           -validate                Validates the pipedoc with the pipeline schema,
                                    by default does not validate. If 'outparam'
                                    feature is used, then validate will fail with
                                    the current pipeline schema because this is an
                                    additional feature. If you are on a proxy
                                    server set the java property at runtime e.g.
                                    "-DproxySet=true -DproxyHost=www.proxyhost.com
                                    -DproxyPort=80"
           -log <logfile>           Writes the errors/logs to the output
                                    file, by default writes to pipe.log
           -noinfo                  Don't log any info items, turned on by default
           -nowarning               Don't log any warnings, turned on by default
           -force                   Executes pipeline even if target is up-to-date,
                                    by default no force is specified


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
    | `orapipe``()`               |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `error``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`<br>Handle any error thrown by the pipeline           |
    | `void`            | `fatalError``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`<br>Handle an fatal error thrown by the pipeline |
    | `void`            | `info``(java.lang.String msg)`<br>Handle any informational items from the pipeline                                                    |
    | `static void`     | `main``(java.lang.String[] args)`                                                                                                     |
    | `void`            | `warning``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`<br>Handle all warnings thrown by the pipeline      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### orapipe

          public orapipe()

  <!-- -->

  - ### Method Detail

    - #### main

          public static void main(java.lang.String[] args)

    <!-- -->

    - #### error

          public void error(java.lang.String msg,
                            PipelineException e)
                     throws PipelineException

      Handle any error thrown by the pipeline
      Specified by:
      [`error`](PipelineErrorHandler.md) in interface [`PipelineErrorHandler`](PipelineErrorHandler.md)

      Parameters:
      `msg` - - error message

      `e` - - PipelineException

      Throws:
      `java.lang.Exception`

      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### fatalError

          public void fatalError(java.lang.String msg,
                                 PipelineException e)
                          throws PipelineException

      Handle an fatal error thrown by the pipeline
      Specified by:
      [`fatalError`](PipelineErrorHandler.md) in interface [`PipelineErrorHandler`](PipelineErrorHandler.md)

      Parameters:
      `msg` - - error message

      `e` - - PipelineException

      Throws:
      `java.lang.Exception`

      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### warning

          public void warning(java.lang.String msg,
                              PipelineException e)
                       throws PipelineException

      Handle all warnings thrown by the pipeline
      Specified by:
      [`warning`](PipelineErrorHandler.md) in interface [`PipelineErrorHandler`](PipelineErrorHandler.md)

      Parameters:
      `msg` - - error message

      `e` - - PipelineException

      Throws:
      `java.lang.Exception`

      [`PipelineException`](PipelineException.md)

    <!-- -->

    - #### info

          public void info(java.lang.String msg)

      Handle any informational items from the pipeline
      Specified by:
      [`info`](PipelineErrorHandler.md) in interface [`PipelineErrorHandler`](PipelineErrorHandler.md)

      Parameters:
      `msg` -

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

- **[Prev Class](Input.md)**
- **[Next Class](Output.md)**

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
