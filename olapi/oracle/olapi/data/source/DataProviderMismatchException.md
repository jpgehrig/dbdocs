Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](DataProvider.md)
- [Next Class](DateParameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Class DataProviderMismatchException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../../OLAPIRuntimeException.md)

        - - oracle.olapi.data.source.DataProviderMismatchException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class DataProviderMismatchException
      extends OLAPIRuntimeException

  Indicates an attempt to combine `Source` objects associated with different `DataProvider` objects. For example, this exception is thrown when `Source` x and `Source` y are associated with different `DataProvider` objects and the `x.join(y)` call is made.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------|
    | `DataProviderMismatchException``()`<br>Creates a `DataProviderMismatchException`.                                                    |
    | `DataProviderMismatchException``(java.lang.String message)`<br>Creates a `DataProviderMismatchException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getParameters`](../../OLAPIRuntimeException.md)`, `[`toString`](../../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DataProviderMismatchException

          public DataProviderMismatchException()

      Creates a `DataProviderMismatchException`.

    <!-- -->

    - #### DataProviderMismatchException

          public DataProviderMismatchException(java.lang.String message)

      Creates a `DataProviderMismatchException` with the specified message.
      Parameters:
      `message` - A `String` that contains a message for this exception.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DataProvider.md)
- [Next Class](DateParameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
