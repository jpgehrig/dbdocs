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

- [Prev Class](NotSpecifiedException.md)
- [Next Class](SourceIdentifier.md)

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

## Class PositionOutOfBoundsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - java.lang.IndexOutOfBoundsException

        - - oracle.olapi.data.cursor.PositionOutOfBoundsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class PositionOutOfBoundsException
      extends java.lang.IndexOutOfBoundsException

  Indicates that the specified position is not valid. When an application calls the `setPosition` method of a `Cursor`, Oracle OLAP does not determine whether the specified position is valid until the application attempts some other operation such as calling the `getExtent` or `getCurrentValue` method of the `Cursor`. If the specified position is not valid, then this exception is thrown. If an application catches this exception, then it should set the position to different value and try the operation again.
  See Also:
  [`Cursor`](Cursor.md), [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                        |
    |------------------------------------------------------------------------------------------------------------------------------------|
    | `PositionOutOfBoundsException``()`<br>Creates a `PositionOutOfBoundsException`.                                                    |
    | `PositionOutOfBoundsException``(java.lang.String message)`<br>Creates a `PositionOutOfBoundsException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PositionOutOfBoundsException

          public PositionOutOfBoundsException()

      Creates a `PositionOutOfBoundsException`.

    <!-- -->

    - #### PositionOutOfBoundsException

          public PositionOutOfBoundsException(java.lang.String message)

      Creates a `PositionOutOfBoundsException` with the specified message.
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

- [Prev Class](NotSpecifiedException.md)
- [Next Class](SourceIdentifier.md)

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
