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

- [Prev Class](ExpressServerException.md)
- [Next Class](TaskInterruptedException.md)

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

## Class ObjectClosedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - java.lang.IllegalStateException

        - - [oracle.olapi.OLAPIIllegalStateException](../olapi/OLAPIIllegalStateException.md)

          - - oracle.express.ObjectClosedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class ObjectClosedException
      extends OLAPIIllegalStateException

  Indicates that you have called an OLAP API method that requires retrieval of information from Oracle OLAP, and that communication is not possible because the resources required for the communication have been freed. For example, an OLAP API method throws this exception if you try to get an object from a `MetadataProvider` but you previously had closed the associated `DataProvider`.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `ObjectClosedException``()`<br>Creates an `ObjectClosedException`.                                                    |
    | `ObjectClosedException``(java.lang.String message)`<br>Creates an `ObjectClosedException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIIllegalStateException](../olapi/OLAPIIllegalStateException.md)

      [`getLocalizedMessage`](../olapi/OLAPIIllegalStateException.md)`, `[`getLocalizedMessage`](../olapi/OLAPIIllegalStateException.md)`, `[`toString`](../olapi/OLAPIIllegalStateException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ObjectClosedException

          public ObjectClosedException()

      Creates an `ObjectClosedException`.

    <!-- -->

    - #### ObjectClosedException

          public ObjectClosedException(java.lang.String message)

      Creates an `ObjectClosedException` with the specified message.
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

- [Prev Class](ExpressServerException.md)
- [Next Class](TaskInterruptedException.md)

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
