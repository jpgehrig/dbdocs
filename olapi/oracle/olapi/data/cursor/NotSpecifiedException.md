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

- [Prev Class](NoDataAvailableException.md)
- [Next Class](PositionOutOfBoundsException.md)

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

## Class NotSpecifiedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - oracle.olapi.data.cursor.NotSpecifiedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NotSpecifiedException
      extends java.lang.RuntimeException

  Indicates that the operation cannot be performed because the application did not specify that it wanted the information. For example, the `getExtent` method on a `Cursor` throws this exception if an application calls it but the application did not, before it created the `Cursor`, call the `setExtentCalculationSpecified` method of the `CursorSpecification` for that `Cursor`.
  See Also:
  [`Cursor`](Cursor.md), [`CursorSpecification`](../source/CursorSpecification.md), [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------|
    | `NotSpecifiedException``()`<br>Creates a `NotSpecifiedException`.                                                    |
    | `NotSpecifiedException``(java.lang.String message)`<br>Creates a `NotSpecifiedException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NotSpecifiedException

          public NotSpecifiedException()

      Creates a `NotSpecifiedException`.

    <!-- -->

    - #### NotSpecifiedException

          public NotSpecifiedException(java.lang.String message)

      Creates a `NotSpecifiedException` with the specified message.
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

- [Prev Class](NoDataAvailableException.md)
- [Next Class](PositionOutOfBoundsException.md)

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
