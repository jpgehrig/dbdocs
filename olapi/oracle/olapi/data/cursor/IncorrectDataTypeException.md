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

- [Prev Class](CursorManagerUpdateListener.md)
- [Next Class](NoDataAvailableException.md)

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

oracle.olapi.data.cursor

## Class IncorrectDataTypeException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - oracle.olapi.data.cursor.IncorrectDataTypeException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class IncorrectDataTypeException
      extends java.lang.RuntimeException

  Indicates that the data type requested is not the type available or expected. A situation in which this exception is thrown is when an application calls a method that gets the current value from `ValueCursor` and the value is not of the expected data type. For example, if an applications calls the `getCurrentInteger` method and the value at the current position of the `ValueCursor` is not an integer, then this exception is thrown.
  See Also:
  [`ValueCursor`](ValueCursor.md), [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                     |
    |---------------------------------------------------------------------------------------------------------------------------------|
    | `IncorrectDataTypeException``()`<br>Creates an `IncorrectDataTypeException`.                                                    |
    | `IncorrectDataTypeException``(java.lang.String message)`<br>Creates an `IncorrectDataTypeException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### IncorrectDataTypeException

          public IncorrectDataTypeException()

      Creates an `IncorrectDataTypeException`.

    <!-- -->

    - #### IncorrectDataTypeException

          public IncorrectDataTypeException(java.lang.String message)

      Creates an `IncorrectDataTypeException` with the specified message.
      Parameters:
      `message` - The message to associate with the exception.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CursorManagerUpdateListener.md)
- [Next Class](NoDataAvailableException.md)

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
