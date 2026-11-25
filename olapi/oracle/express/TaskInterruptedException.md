Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](ObjectClosedException.md)
- [Next Class](UnexpectedException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.express

## Class TaskInterruptedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

        - - oracle.express.TaskInterruptedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class TaskInterruptedException
      extends OLAPIRuntimeException

  Indicates that the connection to the Oracle Database has been interrupted by Oracle OLAP.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------|
    | `TaskInterruptedException``(java.lang.String message)`<br>Creates a `TaskInterruptedException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getParameters`](../olapi/OLAPIRuntimeException.md)`, `[`toString`](../olapi/OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TaskInterruptedException

          public TaskInterruptedException(java.lang.String message)

      Creates a `TaskInterruptedException` with the specified message.
      Parameters:
      `message` - The message to associate with the exception.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ObjectClosedException.md)
- [Next Class](UnexpectedException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method
