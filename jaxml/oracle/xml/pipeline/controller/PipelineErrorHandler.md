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

- **[Prev Class](PipelineDoc.md)**
- **[Next Class](PipelineException.md)**

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

## **Interface PipelineErrorHandler**

- **All Known Implementing Classes:**
  **[orapipe](orapipe.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface PipelineErrorHandler

  **For Pipeline Errors the application calling the Pipeline Processor must implement this interface to handle errors received from the Pipeline Processor. This should be set in the PipelineProcessor. It is up to the application to decide whether to throw an exception for different types of errors.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `void`            | `error``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`       |
    | `void`            | `fatalError``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`  |
    | `void`            | `info``(java.lang.String msg)`                                                         |
    | `void`            | `warning``(java.lang.String msg, `[`PipelineException`](PipelineException.md)` e)`     |

<!-- -->

- - ### Method Detail

    - #### error

          void error(java.lang.String msg,
                     PipelineException e)
              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### fatalError

          void fatalError(java.lang.String msg,
                          PipelineException e)
                   throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### warning

          void warning(java.lang.String msg,
                       PipelineException e)
                throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### info

          void info(java.lang.String msg)

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

- **[Prev Class](PipelineDoc.md)**
- **[Next Class](PipelineException.md)**

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
