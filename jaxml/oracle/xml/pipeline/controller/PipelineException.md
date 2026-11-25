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

- **[Prev Class](PipelineErrorHandler.md)**
- **[Next Class](PipelineProcessor.md)**

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

## **Class PipelineException**

- **java.lang.Object**

- - **java.lang.Throwable**

  - - **java.lang.Exception**

    - - **oracle.xml.pipeline.controller.PipelineException**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class PipelineException
      extends java.lang.Exception

  **Represents an exception thrown by a pipeline method.**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                    |
    |--------------------------------------------------------------------------------|
    | `PipelineException``(java.lang.Exception e)`<br>Create a new PipelineException |
    | `PipelineException``(java.lang.String msg)`<br>Create a new PipelineException  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                            |
    |--------------------|-----------------------------------------------------------------------------------|
    | `java.lang.String` | `getExceptionType``()`<br>Get the type of the exception                           |
    | `java.lang.String` | `getProcessId``()`<br>Get the Pipeline Process id where the exception is occuring |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PipelineException

          public PipelineException(java.lang.String msg)

      Create a new PipelineException
      Parameters:
      `msg` - error message

    <!-- -->

    - #### PipelineException

          public PipelineException(java.lang.Exception e)

      Create a new PipelineException
      Parameters:
      `e` - exception embedded in the PipelineException

  <!-- -->

  - ### Method Detail

    - #### getExceptionType

          public java.lang.String getExceptionType()

      Get the type of the exception
      Returns:
      String type of exception, eg. oracle.xml.pipeline.controller.PipelineException

    <!-- -->

    - #### getProcessId

          public java.lang.String getProcessId()

      Get the Pipeline Process id where the exception is occuring
      Returns:
      String process id attribute

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

- **[Prev Class](PipelineErrorHandler.md)**
- **[Next Class](PipelineProcessor.md)**

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
