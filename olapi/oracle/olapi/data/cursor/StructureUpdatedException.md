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

- [Prev Class](SpecificationUpdateNeededException.md)
- [Next Class](ValueCursor.md)

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

## Class StructureUpdatedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - oracle.olapi.data.cursor.StructureUpdatedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class StructureUpdatedException
      extends java.lang.RuntimeException

  Indicates that the structure of the `Source` associated with a `CursorManager` has changed. The application needs to create a new `CursorInfoSpecification` for the `Source`, update or create a new `CursorManager` using the new `CursorInfoSpecification`, and create new `Cursor` objects.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------|
    | `StructureUpdatedException``()`<br>Creates a `StructureUpdatedException`.                                                    |
    | `StructureUpdatedException``(java.lang.String message)`<br>Creates a `StructureUpdatedException` with the specified message. |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### StructureUpdatedException

          public StructureUpdatedException()

      Creates a `StructureUpdatedException`.

    <!-- -->

    - #### StructureUpdatedException

          public StructureUpdatedException(java.lang.String message)

      Creates a `StructureUpdatedException` with the specified message.
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

- [Prev Class](SpecificationUpdateNeededException.md)
- [Next Class](ValueCursor.md)

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
